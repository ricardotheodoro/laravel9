
# Setup Docker Para Projetos Laravel

### Passo a passo Laravel 9 básico
Clone Repositório
```sh
git clone https://github.com/ricardotheodoro/laravel9.git my-project
```
```sh
cd my-project/
```


Alterne para a branch laravel de sua preferência

Laravel 9 com Docker
```sh
git checkout laravel-com-docker
```


Remova o versionamento (opcional)
```sh
rm -rf .git/
```


Crie o Arquivo .env
```sh
cp .env.example .env
```


Atualize as variáveis de ambiente do arquivo .env
```dosini
APP_NAME="MyProject"
APP_URL=http://localhost:8989

DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=nome_que_desejar_db
DB_USERNAME=root
DB_PASSWORD=root

CACHE_DRIVER=redis
QUEUE_CONNECTION=redis
SESSION_DRIVER=redis

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379
```


Suba os containers do projeto
```sh
docker-compose up -d
```


Acesse o container app com o bash
```sh
docker-compose exec app bash
```


Instale as dependências do projeto
```sh
composer install
```


Gere a key do projeto Laravel
```sh
php artisan key:generate
```


Acesse o projeto
[http://localhost:8989](http://localhost:8989)


### Adicionando JetStream

Documentação JetStream
[Laravel JetStream](https://jetstream.laravel.com/2.x/introduction.html)

Acesse o container app com o bash
```sh
docker-compose exec app bash
```

Instalar dependencia laravel/jetstream
```sh
composer require laravel/jetstream
```

Instalar Jetstream com Livewire
```sh
php artisan jetstream:install livewire
```

Ou, Instalar Jetstream com Inertia
```sh
php artisan jetstream:install inertia
```

O container app não contém o NPM instalado
É recomendado que a máquina local possuia a aplicação para a execução dos próximos comandos

Para instalar o NPM, [Clique Aqui](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

Com as dependencias devidamente instaladas, devemos instalar e buildar as dependências do NPM
```sh
npm install
```

```sh
npm run build
```

Retornar para o bash do container app
```sh
docker-compose exec app bash
```


Por fim, gerar as tabelas no banco de dados
```sh
php artisan migrate
```

#### ATENÇÃO

Para versionar sua aplicação com o banco de dados não esqueça de remover a pasta do MySQL (.docker/*
) do gitignore