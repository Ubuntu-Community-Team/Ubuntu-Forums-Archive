---
title: "cannot compile and install ospfd"
date: 2009-03-05
forum: Packaging and Compiling Programs
---

### Post by chuyinsu on 2009-03-05
I downloaded the source code here:
www dot ospf dot org-->Release 2.0-->gzipped tar format

and there're errors when I run "make install".

I noticed that I might have to install some packages first:
gcc
g++
glibc
glibc-devel
libstdc++-devel
make
Tcl

some of above I managed to install(like gcc) but some I cannot find via "apt-get". e.g. I cannot find glibc and glibc-devel and libstdc++-devel using "sudo apt-get install (package name)" or "sudo aptitude install (package name)". So do some packages have other names in Ubuntu?

and when I unzipped the package:
sudo tar xvzf ***.tar.gz
and went into the directory
cd ospfd/linux
then:
make install
it failed.
I figured that this is an formal&fixed release so there shouldn't be something wrong in the source code. Maybe I made some mistakes without realizing them.

I'd be very appriciated if someone can told how to install this...

P.S. error messages:

cys@cys-laptop:~/temp/ospfd/linux$ sudo make install

g++ -MD -O -g -Wall -Woverloaded-virtual -Wcast-qual -Wuninitialized -I. -I../src -I/usr/local/include -c linux.C
In file included from ../src/ospfinc.h:24,
from linux.C:33:
./machdep.h:93: [error]&#65306; C [function]‘char* strptime(char*, const char*, const tm*)’[declaration]
/usr/include/time.h:210: [error]&#65306; conflict with the previous declaration ‘char* strptime(const char*, const char*, tm*)’
make: *** [linux.o] [error] 1
cys@cys-laptop:~/temp/ospfd/linux$

the words with [] like [error], [function] are in Chinese originally and I translated them into English.
I tried to change the function in machdep.h, which is
char* strptime(char*, const char*, const tm*)
into:
char* strptime(const char*, const char*, tm*)
and there is another error:
../src/dbage.C:117: [error]&#65306; ‘GetNextAdj’[is not declared in dbage.C]

very confused.
I'm using Ubuntu 8.10
thanks!

---

### Post by moma on 2009-03-05
Hello,

Gcc and g++ are part of the "build-essential" meta package.
[COLOR="DarkGreen"]sudo apt-get install build-essential[/COLOR]

I studied the source code and it seems to have several errors when compiling on Ubuntu (or any other Linux distro). Notice that the files in the source package (xxx.tar.gz) are marked read-only, so you must change the permissions before you can alter the files.

Linux has propably ready-made packages for ospf. **Eg. try [quagga...]("http://packages.ubuntu.com/intrepid/quagga").** (See also: [http://www.quagga.net/resources.php](http://www.quagga.net/resources.php) )
[COLOR="DarkGreen"]aptitude search quagga[/COLOR]

---

### Post by chuyinsu on 2009-03-06
Thanks for your reply.

Actually I've already installed quagga and it works. However I need to install OSPFD in order to study the source code on the book which takes this OSPFD as an example. And OSPFD has more functions like Multiple OSPF, etc.

I've tried with Fedora 10, and the same error message occurred. In the book I noticed that the linux kernel under which the OSPFD programme was developed was 2.0.**(Red Hat Linux 5.*), so it's kind of old...-_-;;;

I think I'll try to change the permissions of the files, install "build-essential" first. If it doesn't work, maybe I have to change the Linux distribution to an old one.

---

