---
title: "eric help"
date: 2008-12-30
forum: Programming Talk
---

### Post by perlsyntax on 2008-12-30
How do i install the eric  useing the tar file?I just want to update to the new one that it and could you give me a step by step for installing eric please or i just install the one from apt-get tool.:P

---

### Post by Ahadiel on 2008-12-30
Could you provide a link to what eric is?

---

### Post by pmasiar on 2008-12-30
If you don't know how to install a package from tar files, it's a hint you should not do it (and inadvertently wreck your system). Use the version  provided in repositories. Even if it is not bleeding edge new, it is stable and it works.

Eric is Python IDE - obvious play on IDLE, the default IDE. [http://en.wikipedia.org/wiki/Eric_Idle](http://en.wikipedia.org/wiki/Eric_Idle) of Monty Python of course :-)

---

### Post by NathanB on 2008-12-30
Ignore the post attempting to scare you into passing-up a learning opportunity.  The process is simple to follow:

[php]
$ tar -xvzf eric4-4.2.4a.tar.gz
$ cd eric4-4.2.4a
$ sudo ./configure
$ sudo make
$ sudo make install
[/php]

---

