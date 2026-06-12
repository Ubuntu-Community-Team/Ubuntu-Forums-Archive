---
title: "mono WinForms designer installation"
date: 2009-06-07
forum: Programming Talk
---

### Post by kruno3 on 2009-06-07
Hi,
I have installed mono2.0 and the Windows.Forms libs. I found the Winforms-designer
[http://mono-project.com/WinForms_Designer](http://mono-project.com/WinForms_Designer)
 but i can't install it.
There is no mwf-designer in ubuntus packet manager.
In mono-develop i still can create only gtk+ projects but no Windows.Forms project.
Can someone help me?

---

### Post by directhex on 2009-06-07
You need to check out from SVN and compile it yourself.

---

### Post by kruno3 on 2009-06-08
I got that and i have installed the SVN and check out the mwf-designer but I cant compile it.
In the readme is just "make && make run", but how do i call make?
I tryed with "make mwf-designer" but the result was something like "there is no rule to compile the mwf-designer".
I do it for the first time this way.

---

### Post by matmatmat on 2009-06-08
All you have to do is cd into the directory:
```

$cd mwf-designer
$make && make run

```

---

### Post by kruno3 on 2009-06-08
Hi
I finally got the compiling and Output was :"Compilation succeeded - 1 warning(s)"
but i have no luck with make run:
Laptop:~/mwf-designer$ make run
mkdir -p build
cp deps/*.dll build
cp deps/*.mdb build
cp: Aufruf von stat für &#8222;deps/*.mdb&#8220; nicht möglich: No such file or directory
make: *** [run] Fehler 1

---

### Post by matmatmat on 2009-06-08
I got the same thing

---

### Post by kruno3 on 2009-06-08
I got it with "make mono-design && make run".
This compiles all WinForms classes and runs MWF-designer.
The environment looks strange and it's not that good as the mono-develop.
Anyway, how can i install it?

---

### Post by Bufke on 2009-06-08
sudo make install

I've played with it before, it's not stable enough to do any real work in it.

I usually make winforms in sharpdevelop on windows ):  Then just hand edit the files in MonoDevelop afterwards.

---

### Post by directhex on 2009-06-08
Out of interest, what's the attraction of WinForms? It's a truly horrible API

---

### Post by kruno3 on 2009-06-09
I have much experience with it, many projects and libraries i can use.
And I would like to run my software on both OS-s (without learning Java and start again from 0).

---

### Post by directhex on 2009-06-09
GTK# runs on both too (as long as you have GTK#-for-ms.net installed on Windows). But the experience argument may be compelling

---

