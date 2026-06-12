---
title: "Anjuta &quot;Hello World&quot; error's"
date: 2006-09-11
forum: Programming Talk
---

### Post by pikeblodd on 2006-09-11
I loaded up Anjuta and after digging around for the dependencies, finally got a project up and running.  I was following the tutorial, which sadly, is a little dated for the latest version, but I followed it as diligently as possible, however, I could not get the file to compile.  Im curious though, as I had to manually add the callbacks.c file into the project, if there were any files I needed to add into pixmap, since that seems to be the source of my errors.  Thanks in advance for any help you guys can offer.  

i put a picture up on photobucket of the compiler errors, hope the link works.

[http://i100.photobucket.com/albums/m38/pikeblodd/Screenshot.png](http://i100.photobucket.com/albums/m38/pikeblodd/Screenshot.png)

---

### Post by scto on 2006-09-11
hmm, need more infos, could you send the hole build output?

regards
scto

---

### Post by dluna on 2006-09-11
I am having the same problem. It seemed to me that the GNU compiler wasnt installed because I was getting 

sh: g++ : command not found. 

Also, If I try to build instead of compile I get 

**(anjuta:6604): WARNING **: Cannot execute command : "make".  

As a last ditch effort I went to the terminal and tried 

g++ hello.cc 

and and I get 

g++ command not found

 All of this would seem to point to not having the GNU compiler not being installed but I went to Synaptic Package Manager and found that I had g++ 2.95, so I went ahead and upgraded to 4.0 to no avail. I am a complete Linux nubie, I have had Ubuntu 6.06 for about 3 days now, but I want to try to use it exclusively as long as I can to speed the lerning curve. I am in a Computer Science class where I have to be able to test my simple C++ programs, and if I cant do it in this os, I will be forced back into bill's arms. Help me, please, help me!

dluna

---

### Post by pikeblodd on 2006-09-11
here is the entire build text

---------------------------------------------
Building the whole Project: HelloWorld ...
make
make  all-recursive
make[1]: Entering directory `/home/n00b/Projects/HelloWorld'
Making all in po
make[2]: Entering directory `/home/n00b/Projects/HelloWorld/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/n00b/Projects/HelloWorld/po'
Making all in src
make[2]: Entering directory `/home/n00b/Projects/HelloWorld/src'
/bin/sh ../libtool --mode=link g++ -Wall         -g -g -O2  -o helloworld  main$g++ -Wall -g -g -O2 -o helloworld main.o callbacks.o -pthread  /usr/lib/libgnom$main.o: In function `main':/home/n00b/Projects/HelloWorld/src/main.c:29: undefi$:/home/n00b/Projects/HelloWorld/src/main.c:36: undefined reference to `create_w$callbacks.o: In function `on_BT_OK_clicked':/home/n00b/Projects/HelloWorld/src/$:/home/n00b/Projects/HelloWorld/src/callbacks.c:22: undefined reference to `GNO$collect2: ld returned 1 exit status
make[2]: *** [helloworld] Error 1
make[2]: Leaving directory `/home/n00b/Projects/HelloWorld/src'
make[1]: *** [all-recursive] Error 1
make: *** [all-recursive-am] Error 2
make[1]: Leaving directory `/home/n00b/Projects/HelloWorld'
Completed ... unsuccessful
Total time taken: 3 secs

--------------------------------------------

p.s. Dluna, i was having the same problem with 'make' errors, sudo apt-get install build-essential fixed it for me

p.p.s. ive been working with Ubuntu for about a week now for almost the same reasons as you have, Dluna, its significantly different than working on windows, but im still optimistic

---

