---
title: "Trying to nstall Vpython"
date: 2007-07-23
forum: Programming Talk
---

### Post by eldara5 on 2007-07-23
I'm trying to install Vpython but i get this error:-

configure: error: A suitable python interpreter was found, but you do not have the header files required for building C/C++ extensions to python, or another problem was encoutered when compiling a program that uses Python.h.

Through googling it seems i need to install some packages but there is no referece to what ones and where to get them, has anyone else had this problem if so how is it solved?

Thanks in advance,
Eldara

---

### Post by cdenley on 2007-07-23
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=Python.h&searchmode=searchfiles&case=insensitive&version=feisty&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=Python.h&searchmode=searchfiles&case=insensitive&version=feisty&arch=i386)

You need python2.5-dev, assuming you have python 2.5. When you compile software yourself, you usually need the ...-dev package for all the dependencies. When you're missing a file, just search the contents of packages for that file at [http://packages.ubuntu.com/](http://packages.ubuntu.com/), and install the needed package.

---

### Post by eldara5 on 2007-07-23
Thanks for the reply, will check it out now, hope it works

Eldara

---

### Post by eldara5 on 2007-07-23
Got the package fixed my problem Thanks, XD now o find GTK+

---

