---
title: "compiling C++ from Terminal"
date: 2006-05-21
forum: Programming Talk
---

### Post by Phil_McCrackin on 2006-05-21
I am new to compiling from command (and really like it for some reason I can't pinpoint). I have managed to figure it out using java, but C and C++ are my native languages and I haven't been able to find anything beginner definitive here in the forum. I am a month old noob to linux and Ubuntu.
If anyone can point me in the right direction, I would be eternally grateful.

Thanks in advance, 
-Phil

---

### Post by Zdravko on 2006-05-21
Assume that we have a "sample.cpp" file. We go with "cd" to that directory that contains it. Then we type "make sample". This will invoke the g++ compiler and an executable will be created - with name "sample". You can start it by typing "./sample".
This was the simplest case. In general I work with makefiles.

---

### Post by tonyr on 2006-05-21
The compilers are not installed by default.  Install package **build-essential**,
a dummy package that pulls in all the **gcc/g++** compile related packages. 
Then go off and look for **gcc/g++** references.

---

### Post by tonyr on 2006-05-21
[QUOTE=Zdravko]Assume that we have a "sample.cpp" file. We go with "cd" to that directory that contains it. Then we type "make sample". This will invoke the g++ compiler and an executable will be created - with name "sample". You can start it by typing "./sample".
This was the simplest case. In general I work with makefiles.[/QUOTE]

This feature of **make** is really nice, and something I hadn't known about before
a couple of weeks ago.  In some other *nixen, **gcc** and **g++**, the
GNU C and C++ compilers, are/were effectively synonymous, and invoking
either one would "do the right thing", recognize all reasonable  file extensions and
choose the appropriate processes, syntax front-end-wise and link-step wise. 

Not so in the current **gcc/g++** generation, at least in Ubuntu (maybe
every GNU-**gcc/g++**-where?), but **make** figures it all out just
fine.

---

### Post by Harleen on 2006-05-21
Make does only work if you have a Makefile. I doubt, that Phil_McCrackin has written one for his project.
So he will have to call g++ directly.

```
g++ sample.cpp -o sample
```

This will call the C++ compiler and generate an executable named "sample". You can also pass multiple cpp files. For further options look at the man page of g++.

---

### Post by tonyr on 2006-05-21
[QUOTE=Harleen]Make does only work if you have a Makefile. [/QUOTE]

I believe that this is not entirely true.  It may, however, be related to the version
of **make** being used.  You should try it and see.  Complex projects with many
files and subdirectories definitely need to be organized with **makefiles**.

Here is a sample from my login session:

```

playroom:~/src/c++> **ls -l**
[COLOR="SeaGreen"]total 12
-rw-r--r-- 1 tonyr tonyr 86 2006-05-10 07:54 ex1.cc
-rw-r--r-- 1 tonyr tonyr 60 2006-05-09 14:27 ex2.c
-rw-r--r-- 1 tonyr tonyr 86 2006-05-21 16:14 ex3.cpp[/COLOR]
playroom:~/src/c++>
playroom:~/src/c++>
playroom:~/src/c++> **make -v**
[COLOR="SeaGreen"]GNU Make 3.81beta4
Copyright (C) 2003  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu[/COLOR]
playroom:~/src/c++>
playroom:~/src/c++>
playroom:~/src/c++> **make ex1**
[COLOR="SeaGreen"]g++     ex1.cc   -o ex1[/COLOR]
playroom:~/src/c++>
playroom:~/src/c++>
playroom:~/src/c++> **make ex2**
[COLOR="SeaGreen"]cc     ex2.c   -o ex2[/COLOR]
playroom:~/src/c++>
playroom:~/src/c++>
playroom:~/src/c++> **make ex3**
[COLOR="SeaGreen"]g++     ex3.cpp   -o ex3[/COLOR]
playroom:~/src/c++>
playroom:~/src/c++> **which cc**
[COLOR="SeaGreen"]/usr/bin/cc[/COLOR]
playroom:~/src/c++> **ls -l /usr/bin/cc**
[COLOR="SeaGreen"]lrwxrwxrwx 1 root root 20 2006-04-15 15:32 /usr/bin/cc -> /etc/alternatives/cc[/COLOR]
playroom:~/src/c++> **ls -l /etc/alternatives/cc**
[COLOR="SeaGreen"]lrwxrwxrwx 1 root root 12 2006-04-15 15:32 /etc/alternatives/cc -> /usr/bin/gcc[/COLOR]
playroom:~/src/c++>


```

EDIT:  Missed some lines in my first copy/paste

---

### Post by Phil_McCrackin on 2006-05-21
Sweet action... We have executable! I haven't tried putting a project together this way, but now that I have the basics (and I know some of the commands), I'm certain I can get the rest. Seems I need to learn a bit of DOS. Thank you all very much for your help. I'm actually not currently working on a project (I've mostly been trying to acquaint myself with java since I have no formal education with it), but most of my classes require code done in C++ and at OSU the instructors compile in Linux. I have been told that compiling this way requires more attention to detail as the compilers are a bit pickier. I've even heard stories of assignment failures because the instructor could not get a pgm to compile on his linux box that compiled fine in an IDE in Windows. I will be prepared ;)

Thanks a million!

---

### Post by bieber on 2006-05-21
lol.  You don't wanna touch DOS.  What you're using now is Bash.

---

### Post by Phil_McCrackin on 2006-05-21
Really...wow I'm a doofus. Well, I've never known anything about either until the last few weeks and quite a few of the commands are the same. 
Just did a book search...Wow so many. Can anyone recommend one? I'm a total noob, but I'm a quick study.

---

### Post by tonyr on 2006-05-21
There is plenty of stuff online. Here is one page that looks like a reasonable
place to start.
[http://librenix.com/?inode=4052]("http://librenix.com/?inode=4052")

---

### Post by Phil_McCrackin on 2006-05-21
Great, thank you! The Ubuntu wiki also has a good command line how-to. I will probably eventually try to find a book. I like to have that hard reference. I'm OCD like that (Especially since it looks like I'm going to be sticking with linux). The goal for me is to be completely unreliant on Windows. I'm not there yet.

---

### Post by bieber on 2006-05-21
[http://www.linuxcommand.org](http://www.linuxcommand.org)

Awesome Bash tutorial, goes into basic commands and then scripting.

---

### Post by Steveire on 2006-05-22
[QUOTE=bieber][http://www.linuxcommand.org](http://www.linuxcommand.org)

Awesome Bash tutorial, goes into basic commands and then scripting.[/QUOTE]
I like the constant references to 'the legacy operating system'. Very comprehensive tutorial.

---

