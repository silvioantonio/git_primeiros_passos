# Git e GitHub

O Git é um sistema de controle de versão e organização de código fonte. Foi inicialmente desenvolvido por Linus Torvalds para para gerir as versões do código fonte do Linux.

## Instalação

**Linux**

Para usuários Linux a instalação do git pode ser feita via terminal através do comando:

````bash
$ sudo apt-get install git
````

**Mac**

Para usuários de Mac o download do pacote de instalação pode ser feito através do site oficial do [git](https://git-scm.com/download/mac).

**Windows**

Em máquinas windows faça o download do instalador de acordo com o sistema operacional através da página oficial do [git](https://git-scm.com/download/win). Nesse instalador para sistemas windows já vem integrado o gitBash, um interpretador de código do git que roda em sistemas micrisoft.

## 1. Configurações Iniciais

> **Meta do capítulo: **
>
> 1 - Verificar se o git está instalado
>
> 2 - Identificar o usuário que irá utilizar o git

### Verificando o Git

Para verificar se o git foi instalado corretamente utilize o seguinte comando no terminal do linux/mac ou no gitBash para computadores windows.

```bash
$ git --version
```



### Identificando o Usuário

> Essa identificação irá servir para que o git identifique qual usuário está fazendo as alterações nos arquivos.

Para identificar o usuário que irá utilizar o git iremos preencher as variáveis globais `user.name` e `user.email`.

```bash
$ git config --global user.name "Thiago Guimarães Tavares"
$ git config --global user.email "thiagogmta@gmail.com"
```

Para verificar a configuração utilize o comando:

```bash
$ git config --list
```



## 2. Um Repositório no Git (criar, verificar e excluir)

> **Meta do capítulo: **
>
> 1 - Aprender a criar e a excluir um repositório

> O ato de iniciar um repositório no Git consiste em informar que aquele diretório criado para armazenar o projeto deve ser monitorado.

Para armazenar nossos arquivos do projeto (seja código fonte ou outro tipo de documento), normalmente criamos um diretório no computador e inserimos os arquivos ali dentro. O ato de iniciar um repositório no Git consiste em informar que aquele diretório criado deve ser monitorado.

### Iniciando um Repositório

Para tanto utilizamos o comando 

```bash
$ git init
```

Dentro do diretório a ser monitorado.

Esse guia por exemplo está sendo escrito em MarkDown e como exemplo foi iniciado um repositório no Git dentro do diretório que armazena esse projeto.

ao executar o comando `git init` dentro do diretório a seguinte mensagem foi exibida:

```bash
$ Initialized empty Git repository in C:/Users/thiago/Dropbox/PENSAMENTOS/Guia de Estudos - Front-end/.git/
```

Nesse caso _Guia de Estudos - Front-end_ é o diretório que armazena o projeto. Note também que ao final da linha é exibido a informação `.git` que é um diretório criado pelo git com as informações do repositório. Esse diretório mantem-se oculto no sistema de arquivos.

### Verificando o Status do repositório

Podemos verificar a situação do nosso diretório através de um comando específico. Dentro do diretório do projeto execute o comando:

```bash
$ git status
```

Para este ambiente de testes temos o seguinte retorno:

```bash
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Git e GitHub.md
        Guia de estudo_ Front-end.md
        Registro de Estudo Front-end.md

nothing added to commit but untracked files present (use "git add" to track)
```

O retorno do comando informa que existem arquivos que não estão sendo monitorados `untracked files:`[^1] e que não foi feito nenhum `commit`[^2] no nosso projeto.

### Excluindo um Repositório

Caso não seja mais necessário o acompanhamento desse projeto (ou de qualquer outro) por parte do Git podemos desfazer o repositório apagando seus arquivos com o comando:

```bash
$ rm -f .git
```



[^1]: Definir o git add
[^2]: Definir o git commit



## 3. Manipulando arquivos no git

> **Meta do capítulo: **
>
> 1 - Aprender a adicionar e remover arquivos do rasteramento do git
>
> 2 - Aprender a gravar as alterações realizadas

Como vimos no tópico anterior, conseguimos criar o repositório, entretanto o git nos informou que naquele diretório exisitiam arquivos que não estavam sendo monitorados. Cada arquivo inserido no diretório deve ser informado ao git, para que seja monitorado.

### Adicionando Arquivos: $ git add

**Adicionando individualmente:**

Podemos adicionar arquivos individualmente com:

```bash
$ git add <nome_do_arquivo>
```

**Adicionando todos os arquivos:**

ou adicionar todos os arquivos do repositório com:

```bash
$ git add .
```

Após adicionar os arquivos do repositório e novamente utilizar o comando `git status` temos um retorno diferente:

```bash
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   Git e GitHub.md
        new file:   Guia de estudo_ Front-end.md
        new file:   Registro de Estudo Front-end.md
```

Nesse retorno o git informa que existem mudanças para serem "comitadas" e que novos arquivos (três para ser mais preciso) foram adicionados.

### Removendo Arquivos: $ git rm

Caso algum (ou vários) arquivos tenham sido adicionados por engano, podemos remove-los do monitoramento do git.

**Removendo individualmente:**

Nesse repositório de exemplo tenho três arquivos que foram adicionados, caso seja necessário remover o arquivo _Git e GitHub.md_ basta executar o comando:

```bash
$ git rm --cached Git e GitHub.md
```

Para verificarmos, utilizaremos `git status` novamente:

```bash
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   Guia de estudo_ Front-end.md
        new file:   Registro de Estudo Front-end.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Git e GitHub.md
```

Podemos verificar que existem dois novos arquivos adicionados (new file) e um arquivo não monitorado (Git e GitHub.md).

**Removendo todos os arquivos:**

Para remover todos os arquivos utilizaremos o comando:

```bash
$ git rm --cached . -r
```

Para esse exemplo irei manter todos os arquivos adicionados no git (`$git add .`)!

### Gravando... : $ git commit

> o $ git commit atua como o seu ctrl+s do seu editor de código.

Até então fizemos os seguintes procedimentos:

1. Criamos um diretório

2. Iniciamos o repositório ($ git init)

3. Adicionamos os arquivos a serem monitorados ($git add)

O próximo passo consiste em gravar as alterações que foram feitas. Para esse procedimento vamos utilizar o comando:

```bash
$ git commit -m "Vai teia! Voa! Para o alto e avante teia! Shazam!? Vai vai vai vai teia vai!"
```

O `$git commit` aplica as alterações realizadas ou em outras palavras informa ao git que você quer gravar um registo de suas atividades naquele momento. A instrução `-m` do exemplo indica que você irá inserir uma informação que servirá de registro para aquele commit.

O comentário desse exemplo foi uma mera brincadeira. É extremamente importante que seus comentários sejam relevantes para o projeto. Pois ao consultar o log de atividades os comentários irão te auxiliar a indentificar a versão desejada.

**Dica:**

- O comando: `$ git commit` está para o **git** como o `ctrl+s` está para o **VisualStudio Code**.
- Quando usar: Sempre que necessitar criar um registro de atividade.
- O comentário: Procure criar comentários condizente com as atividades que quer registrar.

### Verificando o Log de Atividades



git log

## 4. Resumo dos comandos

$ git init

$ git status

$ git add <nome_do_arquivo>

$ git add .

$ git rm --cached <nome_do_arquivo>

$ git rm --cached . -r

$ git commit

$ git log