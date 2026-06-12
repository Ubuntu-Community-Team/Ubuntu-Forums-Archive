---
title: "i want to see the header files of my c++ compiler"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by dilanka007 on 2008-07-26
guys i am really new to Ubuntu..
but i have completely left windows at home now.
can somebody help me with the file structure here.
if i want t see my c++ compiler folder and if i want to check the header files hw do i do that, to which folder should i go in to.
same with java.
pls give me a step by step support.
and normally when u install an application how it is stored in ubuntu.

sorry guys some may sound stupid to you..

thanks in advance

---

### Post by RiceMonster on 2008-07-26
If you want to know where any application is stored type this into a terminal:

```
whereis program
```

Most executables will be stored in /usr/bin/.

Oh, and your questions are not stupid at all. I actually don't know the answer about the c++ compiler, so I don't think it's a stupid question.

---

### Post by iaculallad on 2008-07-26
For the GCC header files, try browsing the directories below:

> /usr/local/include
/usr/include
/usr/lib/gcc-lib

Depending on your version installed:

> /usr/include/glib-2.0

or if you can't find them in there, try using the locate command instead.

```
locate *.h
```

Output will surely overflow in your screen, so it's much better to pipe the output to a file for you to review:

```
locate *.h > headerfiles.txt
```

---

### Post by dilanka007 on 2008-07-26
hey thnaks..

i could browse all the direcrories as you said.
and i could se all the header files.
but the problem is i want to know why all these header files are everywhere in 3 directories such as
> /usr/local/include
/usr/include
/usr/lib/gcc-lib 
/usr/include/glib-2.0
and how do i know which type of a compiler i use(ok i guess its gcc)
and how do i know which header files in these folders are excactly can be used when programming in c++.
actually i need to work with mysql++.
so for that i need to put those mysqlpp.h files in to the proper folders.
this is where i get confused.
if it is in windows u know where to put headers exactly.
here i am kinda lost.
pls do help.
thank you in advance

---

### Post by dilanka007 on 2008-07-26
and this is what i get when i try to see where is gcc..
> dilanka@dilanka-laptop:~$ whereis gcc
gcc: /usr/bin/gcc /usr/lib/gcc /usr/share/man/man1/gcc.1.gz

so this is where i get confused where to put my header files where i can use it forever

---

