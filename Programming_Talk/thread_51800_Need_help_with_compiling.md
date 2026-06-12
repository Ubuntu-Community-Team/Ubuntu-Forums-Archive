---
title: "Need help with compiling"
date: 2005-07-25
forum: Programming Talk
---

### Post by JPatrick on 2005-07-25
I can write the code by I can't compile any of it... :(

I using KDevelop.

I just need a way, any way, to compile the code..

Thanks

---

### Post by DJ_Max on 2005-07-25
[QUOTE=JPatrick]I can write the code by I can't compile any of it... :(

I using KDevelop.

I just need a way, any way, to compile the code..

Thanks[/QUOTE]
 hrmm, any errors? Can't really help if I don't know your problem.

---

### Post by JPatrick on 2005-07-25
I don't know where to start compiling...

---

### Post by thumper on 2005-07-25
[QUOTE=JPatrick]I don't know where to start compiling...[/QUOTE]
You could try the command line.

What language are you using?

---

### Post by JPatrick on 2005-07-25
C++. I was thinking about the command line...

Don't know the command.

---

### Post by thumper on 2005-07-25
[QUOTE=JPatrick]C++. I was thinking about the command line...

Don't know the command.[/QUOTE]
If you are compiling a single file test.cpp then the command line is:
```
g++ -o test test.cpp
```
This will create an executable file in the current directory called test.
Execute it by
```
./test
```
and you are off an running.

You can pass multiple source files to g++ on the command line, but once you get past two or three it is time to start looking a makefiles.

---

### Post by JPatrick on 2005-07-25
Excellent it works!! :D

Cheers!

---

