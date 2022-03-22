<h2 align="center">
    SENAI
</h2>
<h3 align="center">
    Programador Full Stack  -  Versionamento
</h3>

Comandos que utilizei para trabalhar com versionamento.

### Repositório Local

Configurando nome de usuário e e-mail:

```bash
$ git config --global user.email wesleycarvalho.dev@outlook.com

$ git config --global user.name "wbc-code"
```

### Criar a chave SSH para autenticar usuario local

```bash
$ ssh-keygen -t ed25519 -C "wesleycarvalho.dev@outlook.com"
```

```bash
> Generating public/private algorithm key pair.
```

Quando aparecer a solicitação "Enter a file in which to save the key", pressione Enter para salvar a chave no local padrão do arquivo.

```bash
> Enter a file in which to save the key (/home/you/.ssh/algorithm): [Press enter]
```

Digite uma senha no terminal e pressione Enter é Opcional.

```bash
> Enter passphrase (empty for no passphrase): [Type a passphrase]

> Enter same passphrase again: [Type passphrase again]
``` 

### Adicionar a chave privada no GitHub - ssh-agent

Abrir o terminal e executar o comando:

```bash
cat ~/.ssh/id_ed25519.pub
```
Cópiar a chave pública gerada no terminal.

### Adicionar chave no Github

Cópiei a chave gerada no terminal, abrir o setting no github, no canto superior direito, cliquei em SSH and GPG Keys, no campo titulo, adicionei um rótulo para nova chave "Personal Ubuntu 21", colei a chave pública na área de transferência no campo e cliquei em Add SSH Key, e pronto!

Criei um repositório na pasta **senai-versoes-colaboracoes** utilizando a opção `-b` do comando `init` para setar o nome do *trunk* para **main** conforme comando abaixo:

```bash
$ git init -b "main" --initial-branch="main"
```

Fiz desta forma porque o *trunk* no GitHub "nasce" com o nome de **main** e eu não sabia alterar lá. Então, consultei a documentação do git disponível no link [Git - Reference (git-scm.com)](https://git-scm.com/docs) e cheguei na opção `-b`. Posteriormente, aprendi como alterar o nome do *trunk* no GitHub também, nas configurações do repositório.

Criei o arquivo **versoes.txt** e usei os comandos abaixo para adicioná-lo ao repositório local:

```bash
$ git add versoes.txt

$ git commit -m "Meu primeiro commit"
```

Experimentei fazer alterações neste arquivo e novamente executei estes comandos para atualizá-lo no repositório.

### **Repositório remoto**

Criei um repositório no site do GitHub chamado **senai-versoes-colaboracoes** e utilizei o comando abaixo para fazer a ligação entre o repositório local e o repositório remoto:

```bash
$ git remote add origin git@github.com:wbc-code/senai-versoes-colaboracoes.git
```

Executei o comando a seguir para enviar o conteúdo sob versionamento no repositório local para o repositório remoto:

```bash
$ git push -u origin main
```

Com relação às branches, preferi utilizar a nomenclatura **dev1** e **dev2** e fiz o merge no **main**; utilizei os comandos abaixo:

```bash
$ git checkout -b dev1
```

Alterei o **readme.md** e publiquei suas alterações:

```bash
$ git add .

$ git commit -m "subindo o readme na dev1"

$ git push origin dev1
```

Fiz o mesmo na **dev2**:

```bash
$ git checkout -b dev2

$ git add .

$ git commit -m "subindo o readme na dev2"

$ git push origin dev2
```

Voltei para o *main* com o comando abaixo e fiz um *merge* do **readme.md** e **versoes.txt** da **main** com as **dev1** e **dev2**, atualizando o repositório local em seguida:

```bash
$ git checkout main

$ git merge dev1

$ git add .

$ git commit -m "resolvendo os conflitos"

$ git merge dev2

$ git add .

$ git commit -m "resolvendo os conflitos"
```

Eu havia feito previamente um *merge* sem efetuar o *commit* e o arquivo ficou só com a última alteração. Entendi meu erro e fiz novamente com os devidos *commit* conforme demonstrei no quadro anterior.

Por fim, enviei o conteúdo atualizado ao repositório remoto:

```bash
$ git push origin
```
