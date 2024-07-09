# Sprint III - Curso de Pós-graduação em Engenharia de Software - MVP

## Descrição
Este é o componente C do MVP, uma API responsável pelo autenticação do usuário
no sistema.


## Stack
A API foi feita em Django 4.0, utilizando Django Rest Framework. A persistência
dos dados é feita através do PostgreSQL.

## Técnicas utilizadas
### Login
O sistema de login nativo do Django foi sobrescrito, para demonstrar o conhecimento na criação de rotas
e na elaboração de modelos de dados. Foi escolhido o modelo de autenticação por token, devido a média
complexidade: nem tão fácil quanto uma Session nem tão complexo quanto um JWT.
Foram desenvolvidas cinco rotas.

### TDD e Linting
O trabalho foi todo desenvolvido utilizando o modelo Test Driven Development, onde foram desenvolvidos
cerca de 20 testes, que englobaram desde modificações feitas no Django Admin até testes de modelagem de dados.
Todos os testes foram desenvolvidos antes da funcionalidade. Foi adicionada uma funcionalidade de linting, com o
Flake8. A escolha de técnica é para tentar uns pontinhos a mais no exame :).

### Herança e Mixins
Foram alteradas e herdadas algumas propriedades de classes do Django e do DRF, para demonstrar
o conhecimento de herança e polimorfismo. As principais ocorrências podem ser percebidas no Django Admin
e nos serializadores.

### Docker
No comando RUN do docker todos os comandos de criação do servidor foram
colocados em uma única linha (uso do &&). Essa técnica abre mão da capacida de 
criação de camadas do Docker em benefício do tamanho do arquivo. 
Foi utilizado um comando para encerrar o problema de database racing, já que a aplicação espere que o db
fique pronto, uma vez que o comando 'depends_on'
possui limitações, já que o banco até inicia mas até estar disponível leva alguns
segundos.

## Como instalar
Na pasta do projeto, digite:

`$ docker-compose build`
`$ docker-compose up`

## Testes e Linting
Uma vez que a aplicação esteja instalada, digite:

`docker-compose run --rm app sh -c "python manage.py test && python manage.py flake8`

## Rodando a API
Tudo verificado, hora de rodar a aplicação:

`docker-compose up`

## Documentação
A documentação poderá ser acessada através da rota `http://127.0.0.1:8000/api/docs/`. A
biblioteca de documentação escolhida foi a DRFSpectacular.

## Administração
O módulo de administração da API foi modificado. Caso desejem verificar as mudanças, acessem
`http://127.0.0.1:8000/admin/`. Para criar um superusuário capaz de acessar as funcionalidades
digite:

`$ docker-compose run --rm app sh -c "python manage.py createsuperuser"`

## CI/CD
Foi incluída uma solução de teste contínuo no Github Actions, caso desejem basta 
acessar no meu github o repositório 'xihu-app-api', que é meu projeto de livro de receitas para estudar deployment.

