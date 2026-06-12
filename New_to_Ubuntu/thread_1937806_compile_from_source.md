---
title: "compile from source"
date: 2012-03-08
forum: New to Ubuntu
---

### Post by natman on 2012-03-08
Hello,
I want to install the following program ( it has a L.c and MakeFile in its tar ball ) i have NO idea what i do after i download the tarball.
The program is here:
[http://2n1.org/opengl/proj0/bin/](http://2n1.org/opengl/proj0/bin/)

Could someone please give me some terminal commands that will get the above installed?
Btw i have a 64 Kubuntu if that makes any difference.

---

### Post by winh8r on 2012-03-08
post retracted

---

### Post by natman on 2012-03-08
Thanks but i am unable to run ./configure
natman@swan:~/Desktop/proj0src$ cd
natman@swan:~$ cd Desktop//proj0src/
natman@swan:~/Desktop/proj0src$ ls
L.c  Makefile
natman@swan:~/Desktop/proj0src$ ./configure
bash: ./configure: No such file or directory
natman@swan:~/Desktop/proj0src$ 

( i have extracted the folder correctly, there was only the two files inside it )

---

### Post by Simian Man on 2012-03-08
winh8r's instructions will only work for programs that use autotools, this is not one of those programs, so I don't know why he posted that.

When I extract the archive you posted, I only get a 32-bit executable called "L".  This is not source, but a compiled program.  You may have to install some 32-bit libraries to get it to run, but I don't want to try running some random EXE to help you with that.

---

