---
title: "GNM = gmake not make ???"
date: 2006-11-21
forum: Packaging and Compiling Programs
---

### Post by offbyte on 2006-11-21
hi everybody,

my first thread start... so sorry for anything wrong

i was trying to install postgresql from source, like any starter following the step by step install

./configure

#lot's of msg's, good continue...

gmake

### kabum!!!###
root@carlos-laptop:/usr/share/postgresql-8.1.5# gmake
bash: gmake: command not found

i don't have gmake so I tryed with make

### kabum againg!!!###
root@carlos-laptop:/usr/share/postgresql-8.1.5# make
You need to run the 'configure' program first. See the file
'INSTALL' for installation instructions.
make: *** [all] Error 1

now what do I do?

thanx in advance

---

### Post by loell on 2006-11-21
how about the postgresql in the repository?

---

### Post by adamkane on 2006-11-21
xampp has a postgresql addon:
[http://addons.xampp.org/cgi-bin/search.pl?pid=21](http://addons.xampp.org/cgi-bin/search.pl?pid=21)

---

### Post by offbyte on 2006-11-25
> **loell said:**
> how about the postgresql in the repository?

i managed to install using the repository
that resolves my problem with postgres.

gmake still not found... but i don't need anymore since I opted for the synaptics instalation

thanks

---

### Post by shining on 2006-11-25
> **offbyte said:**
> 
gmake still not found... but i don't need anymore since I opted for the synaptics instalation


make on BSD system is not like GNU one, so they also provide GNU make as gmake for the programs that require it.
On Linux, make is already the GNU one, so it doesn't make sense to also have gmake. But you could just do a symlink from gmake to make, and it would work:
ln -s make /usr/bin/gmake

---

### Post by offbyte on 2006-11-29
> **shining said:**
> make on BSD system is not like GNU one, so they also provide GNU make as gmake for the programs that require it.
On Linux, make is already the GNU one, so it doesn't make sense to also have gmake. But you could just do a symlink from gmake to make, and it would work:
ln -s make /usr/bin/gmake

I'm using linux (ubuntu) not BSD

the symlink worked =) thanx

another happy ubuntu user

---

