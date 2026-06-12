---
title: "mysql++ + g++ (wow lots of +s)"
date: 2007-12-15
forum: Programming Talk
---

### Post by t3hi3x on 2007-12-15
I am experimenting programming c++ applications with mysql apis. the one seeming to be the best is mysql++....

i have some sample cpp files to play with it, but i cannot figure out how to link the libaries. i have looked anywhere and everywhere for such. does anyone know the compile commands for it?

(i have the packages from synaptic installed) i just dont know the flags for g++ to compile it....

Does anyone here know them?

---

### Post by dumbsnake on 2007-12-15
You need the -l flag (that is a lowercase L for library).  Look in /usr/lib for libmysql*.so* probably something like libmysql++.so will be what you want.

If it is that, then you compile by adding "-lmysql++ -lmysqlclient" since you also need the client library probably as well.

I'm assuming you have included the proper headers.  If you get compile error saying that things are undefined then you don't have those.  If you get linker errors saying things are undefined then you are missing libraries.

Goodluck...  Also, you might look into PostGreSQL for databasing especially if you ever plan to sell your C++ code.  Since technically that is against MySql's license.  Also, PostgreSQL is way faster and has tons more features and you can compile C++ code into it and stuff like that much more easily.

---

### Post by t3hi3x on 2007-12-15
well....lol this is kinda complicated. the package that i installed from apt installed the headers to /usr/include/mysql++

the .so file is libmysqlpp

anyway. i had to have -I function to include the headers for it work:

```
g++ -I/usr/include/mysql -I/usr/include/mysql++ -c simple1.cpp -o simple1
```

that did it. weird, but it did it. i'm not sure why above didnt work. 

i figured it out by dissecting the make file included with documentation.

btw i am learning all of this because i and a friend are working on a project called teraTunes. It is a music management system and i need to learn how to compile multiple libraries (for now sql and taglib)

the project has a page on sf and launchpad

thanks a billion for the help, and i hope above helps someone

---

