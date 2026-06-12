---
title: "Compile from source."
date: 2008-05-25
forum: New to Ubuntu
---

### Post by ethoxyethaan on 2008-05-25
i want to install bwiimote-0.4 from source because the once in ubuntu respo's are outdated.

this is what i did:

```
$ sudo su
$ mv '/home/ethox/Desktop/libwiimote-0.4.tgz' '/usr/local/src'
$ cd /usr/local/src
$ tar -zxvf '/usr/local/src/libwiimote-0.4.tgz'

(files unpack so im still doing well)

$ ls

(output is libwiimote-0.4 so...)

$ cd libwiimote-0.4
$ ls
output:
AUTHORS  config.mk.in  COPYING     lib          NEWS    src   TODO
bin      configure.in  install-sh  Makefile.in  README  test

i read README:
INSTALL

Make sure you have BlueZ installed. Type make in the toplevel directory to
build the library and sample applications. After the build is complete the
library can be found in the lib directory.

USAGE

In the test directory there are a couple of test applications that illustrate
how to use this library."

```

root@mm:/usr/local/src/libwiimote-0.4# more INSTALL
INSTALL: No such file or directory

root@mm:/usr/local/src/libwiimote-0.4# make
make: *** No targets specified and no makefile found.  Stop.

root@mm:/usr/local/src/libwiimote-0.4# ./configure
bash: ./configure: No such file or directory

is the world coming to a end or what :D?

help appriciated. sorry for the long post.

---

### Post by &amp;wP*!) on 2008-05-25
**./configure** won't help, because there is no such file in the directory. **make** also not. Look at the README again. Follow the things there.

I think you must use **install-sh** in that directory, not configure/gmake.

---

### Post by ethoxyethaan on 2008-05-25
> LIBWIIMOTE - NINTENDO WIIMOTE LIBRARY FOR LINUX
===============================================

Copyright (C) 2007  Joel Andersson <bja@kth.se>

INSTALL

Make sure you have BlueZ installed. Type make in the toplevel directory to
build the library and sample applications. After the build is complete the
library can be found in the lib directory.

USAGE

In the test directory there are a couple of test applications that illustrate
how to use this library.

thanks for the reply but none of that worked :(

---

### Post by joshsmith on 2008-05-25
you want to type ./install-sh in the correct directory

btw, unless you have had specific advice telling you to do so, it seems like quite a bad idea to copy the source code into /usr. just compile it in your home directory, and it then running something like sudo make install with put it into the right folder

i guess you want
./install-sh
make
sudo make install

(but as you are in a system folder you will need sudo permissions for all)

./install-sh means run the program install-sh in the folder you are currently in

(post the output of anything you do)

---

### Post by ethoxyethaan on 2008-05-26
> **joshsmith said:**
> you want to type ./install-sh in the correct directory

btw, unless you have had specific advice telling you to do so, it seems like quite a bad idea to copy the source code into /usr. just compile it in your home directory, and it then running something like sudo make install with put it into the right folder

i guess you want
./install-sh
make
sudo make install

(but as you are in a system folder you will need sudo permissions for all)

./install-sh means run the program install-sh in the folder you are currently in

(post the output of anything you do)
```

root@mm:/usr/local/src/libwiimote-0.4# ls
AUTHORS  config.mk.in  COPYING     lib          NEWS    src   TODO
bin      configure.in  install-sh  Makefile.in  README  test
root@mm:/usr/local/src/libwiimote-0.4# ./install
bash: ./install: No such file or directory
root@mm:/usr/local/src/libwiimote-0.4# ./install-sh
./install-sh: no input file specified.
root@mm:/usr/local/src/libwiimote-0.4# make
make: *** No targets specified and no makefile found.  Stop.
root@mm:/usr/local/src/libwiimote-0.4# make install
make: *** No rule to make target `install'.  Stop.
root@mm:/usr/local/src/libwiimote-0.4#
```

i just did (sudo su) to stay root permanent so i don't need to keep typing sudo sudo sudo.

ill try to compile it from the home directory.... but i always keep it in this directory to keep a backup of the origenal install files...

---

### Post by &amp;wP*!) on 2008-05-27
> **ethoxyethaan said:**
> ```

root@mm:/usr/local/src/libwiimote-0.4# ls
AUTHORS  config.mk.in  COPYING     lib          NEWS    src   TODO
bin      configure.in  install-sh  Makefile.in  README  test
root@mm:/usr/local/src/libwiimote-0.4# ./install
bash: ./install: No such file or directory
root@mm:/usr/local/src/libwiimote-0.4# ./install-sh
./install-sh: no input file specified.
root@mm:/usr/local/src/libwiimote-0.4# make
make: *** No targets specified and no makefile found.  Stop.
root@mm:/usr/local/src/libwiimote-0.4# make install
make: *** No rule to make target `install'.  Stop.
root@mm:/usr/local/src/libwiimote-0.4#
```

i just did (sudo su) to stay root permanent so i don't need to keep typing sudo sudo sudo.

ill try to compile it from the home directory.... but i always keep it in this directory to keep a backup of the origenal install files...
As suspected, it seems that **./install-sh** is the thing to go but it expects an argument from the user. In the docs it must be stated what argument you must give. Maybe a directory name? Take a look at the **install-sh**. This is an installation script it must include information inside what option you have to give. Probably a directory name.

---

