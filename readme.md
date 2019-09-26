# Hive
O **Hive** é um sistema de gestão focado em pequenas empresas, com o principal intuito de descomplicar a gestão empresarial bem como as rotinas diárias. Desenvolvido com *framework* Laravel e linguagem PHP, é um sistema **modular**, onde podemos escolher os principais recursos para cada empresa. O **Composer** gerencia todas as dependências necessárias para o pacote. **O Hive é um diretório privado**, portando é necessário que você possua permissões e uma **key** configurada.

## Como instalar?
Para instalar o Hive, clone este repositório em seu ambiente.

```
git clone https://github.com/pedroroccon/hive-core.git
```

Instale todas as dependências com o comando:
```
composer install
```

## Dependências privadas
Após a instalação, pode ser necessário **fornecedor o seu token** para instalar os pacotes privados (basicamente todos os pacotes do ecossistema Hive). Para gerar um novo **token**, vá até o **Github, acesse sua conta e procure pelo menu superior direito**. Entre na opção **Settings**, **Developer Settings**, **Personal access tokens**, **Generate new token**. Você deve gerar um token com as permissões **repo**, **admin:public_key**, **admin:repo_hook**. Faça o update dos repositório com o comando:

```
composer update
```

Quando solicitado o *token*, utilize o *token* gerado no seu **painel do Github**. O *token* é invisível e você não conseguirá visualizar ele, mesmo após colando no seu SSH.

## Configurações iniciais
Agora precisamos configurar o arquivo **.env** em seu repositório. Este arquivo define em qual ambiente iremos trabalhar, bem como as configurações de **base de dados, e-mails, logs, integrações, etc...**. Faça uma cópia do arquivo **.env.example** (arquivo de exemplo).

```
cp .env.example .env
```

## Definindo a *app key*
Defina a sua **app key**, chave única de acesso (utilizada para criptografar os arquivos e senhas). **Nunca divulgue esta chave**.

```
php artisan key:generate
```

## Configurando a base de dados
Para configurar a base de dados, você deve editar o arquivo **.env**, indicando qual a base de dados que você irá utilizar, bem como o *host*, usuário e senha. O arquivo **.env.example** possui um exemplo de uma conexão via **MySQL**.

Caso você opte por utilizar a base de dados **sqlite** (recomendado apenas em ambiente de desenvolvimento), crie o arquivo database.sqlite:  **database/database.sqlite**

```
touch database/database.sqlite
```

Após configurar a base de dados e o arquivo **.env**, execute o instalador do Hive.

```
php artisan hello:install
```

O instalador é responsável por
* Executar as migrações;
* Publicar as *views* (opcional)
* Publicar as traduções (opcional)
* Criar os usuários padrões

## Permissões
Para que o Hive funcione, algumas pastas precisam de permissões de leitura/escrita. Caso a aplicação não possua as permissões, necessárias, este evento poderá acarretar em um **erro 500**.

```
chmod 0777 -R storage bootstrap database
```

## Pacote de estilos
O Hive precisa de um pacote de estilos responsável por toda a sua *interface* gráfica.
Para instalar, simplesmente clone o repositório [https://github.com/pedroroccon/hive-assets](https://github.com/pedroroccon/hive-assets.git) dentro da sua pasta /public.

## Criando a pasta storage (pública)
O Hive é capaz de realizar *uploads* de vários arquivos. Alguns destes arquivos são restritos, outros devem ficar disponíveis para os usuários. Por este motivo, precisamos *linkar* a nossa pasta pública dentro do diretório **storage** da nossa aplicação.

```
php artisan storage:link
```

## Tudo pronto, vamos utilizar!
**Tudo pronto, você pode acessar sua aplicação**
