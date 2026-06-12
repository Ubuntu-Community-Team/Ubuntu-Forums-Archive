---
title: "Compiling qmail Trouble, Can yoy help me???"
date: 2005-12-10
forum: Packaging and Compiling Programs
---

### Post by jguerra1977 on 2005-12-10
I want compile qmail in my sever in ubuntu 5.10 in the first step i don´t have GCC runing in the server, the first step did install the package in the server but after that when i try to make the make setup check , i receive a error.

This the mesage than i receive

root@ubuntu:/usr/local/src/qmail/qmail-1.03# make setup check
./load auto-str substdio.a error.a str.a 
substdio.a(substdo.o): En la funciÃ³n `allwrite':
substdo.c:(.text+0x36): referencia a `errno' sin definir
collect2: ld devolviÃ³ el estado de salida 1
make: *** [auto-str] Error 1
root@ubuntu:/usr/local/src/qmail/qmail-1.03#

---

### Post by gord on 2005-12-10
its kinda hard to tell seing as its in a diffirent language but i would suggest doing

```

sudo apt-get install build-essential

```

---

### Post by RHAnthony on 2008-04-29
> **gord said:**
> its kinda hard to tell seing as its in a diffirent language but i would suggest doing

```

sudo apt-get install build-essential

```

I've already done this, and still get this error.
Any other thoughts?

---

