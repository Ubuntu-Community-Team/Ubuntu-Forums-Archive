---
title: "accidentally installed ubuntu-touch on my dell inspiron i7 touch screen"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by geovannylc on 2014-01-26
accidentally installed ubuntu-touch on my dell notebook i7 touch screen, pythons and removed files from my ubuntu library, now I try to reinstall the removed files and can not find all packages. I was wondering how do to lower the standard library of packages already installed Ubuntu 13.10 Unity.

Never smoke in galley one messing updates! : ~

Acidentalmente instalei ubuntu-touch no meu notebook dell i7 touch screen, e removi arquivos pythons da biblioteca do meu ubuntu, agora tento reinstalar os arquivos que removi e não consigo achar todos os pacotes. Eu queria saber como faço pra baixar a biblioteca padrão dos pacotes já instalados o Ubuntu 13.10 Unity. 



Que maconha forte é essa que eu escrevi essa p*em inglês?

---

### Post by Bashing-om on 2014-01-26
geovannylc; Hi Welcome to the forum.

As a 1st approximation:
terminal codes:
```

sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get install -f

```
Now if the package manager can not work it out, and you know or have found out the packages in question:
Go to:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
and download the package and try to install:
```

sudo dpkg -i <package_name>

```
It is difficult but,
[INDENT][INDENT][INDENT]it can be done
[/INDENT][/INDENT][/INDENT]

---

