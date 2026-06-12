---
title: "fatal error: sys/cdefs.h: No such file or directory|"
date: 2014-05-22
forum: Packaging and Compiling Programs
---

### Post by mandar2 on 2014-05-22
Hi all,


It has been weeks that i am trying to use Code::Blocks IDE to  program Atmega16, however, i am hindered by the following error while  compiling/building the program in C::B

  /usr/include/features.h|374|fatal error: sys/cdefs.h: No such file or directory|

  i have read following thread.


  [http://stackoverflow.com/questions/9303037/cannot-compile-simple-c-program-in-ubuntu](http://stackoverflow.com/questions/9303037/cannot-compile-simple-c-program-in-ubuntu)

From the thread above i have tried to purge libc6-dev and ran into trouble  by removing the dependencies. From previous experience i knew that there  is a huge probability to get into broken pipe error. i tackled it by  installing the lost dependencies.

 
now still i have the same error.

Experts, please guide me. 

what should i do? I use Ubuntu 14.04 LTS

---

### Post by kadir6 on 2014-06-19
Try these:
sudo apt-get purge libc6-dev
sudo apt-get install libc6-dev

In case of -m32:
sudo apt-get install libc6-dev-i386

---

