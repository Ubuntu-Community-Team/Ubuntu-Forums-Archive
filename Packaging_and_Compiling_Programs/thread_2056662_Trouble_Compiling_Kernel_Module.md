---
title: "Trouble Compiling Kernel Module"
date: 2012-09-11
forum: Packaging and Compiling Programs
---

### Post by Runicode on 2012-09-11
Hello,
 
I'm completely new to anything outside of windows and I've run into an issue with my first attempt at compiling a kernel module.
 
I'm working on the latest version of Ubuntu which I downloaded a few nights ago running on a VM.
 
I get the following error when trying to compile with "make".
 
"fatal error: linux/module.h no such file or directory compilation terminated"
 
I'm working off of examples found @ [FONT=Verdana][[COLOR=#0000ff]http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40[/COLOR]]("http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN40") [/FONT]
 
Can anyone point me in the right direction? Does Ubuntu not come with these headers? If not what do I need to do to install them?
 
Thanks for your help!
Runicode

---

### Post by Toz on 2012-09-11
Moved to the Packaging and Compiling Programs forum for better visibility.

---

### Post by steeldriver on 2012-09-11
Hello and welcome

I am no expert in this area but I would think you will need at least the linux-headers package for your kernel

```
sudo apt-get install linux-headers-$(uname -r)
```If you haven't already set up a suitable build environment then the easy way to get everything is the build-essential meta package

```
sudo apt-get install build-essential
```Good luck!

---

### Post by Bucky Ball on 2012-09-11
Just wondering why you are compiling a kernel. This a big leap in for a newcomer. ;)

Using virtualbox you are given a choice and it makes it easy, no compiling required. You can also just burn a disk as per normal, open virtual box and install the guest OS directly from the disk. Good luck whichever way you go but your current path is probably not the easiest for starters. On the other hand, a good way to start the learning curve and you will definitely learn something, as appears to be the case to this point ...

Have you got Win as the host and you are attempting to install Ubuntu as the guest?

---

### Post by einonm on 2012-09-12
I think you need to setup a configuration first, and this can be done in a few ways, usually by typing 'make config' or similar before executing 'make' on the command line. The best way is to take your current kernel config from /boot/config-xxx and putting it at the root of your kernel tree, renaming it to '.config'.

However, you don't provide much detail as to what you have done before typing 'make', and in which directory you are doing it from. More details please!

---

### Post by Runicode on 2012-09-12
I agree this is a big leap for a beginner and is actually for a course I'm taking... no help at all from the professor.
 
I do have build essentials installed. Do I need to execute sudo apt-get install linux-headers-$(uname -r) as well or are the headers included in build essentials?
 
Right now I have the first c hello world program and make file shown at the link I provided. Do they need to be present in a specific directory? Right now I have them in a project folder under documents.
 
Thank you all for your help with this.

---

### Post by steeldriver on 2012-09-12
Well fwiw the hello-1.c example built OK on my Xubuntu 12.04 box using the example Makefile provided at

[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN181](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html#AEN181)

I built it in a directory called ~/src/kernelmod so no I don't think it needs to be anywhere special. I have the latest kernel headers installed i.e. 

```
$ sudo apt-get install linux-headers-$(uname -r)
[sudo] password for steeldriver: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.2.0-27-generic is already the newest version.
The following package was automatically installed and is no longer required:
  libxosd2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
$ 
```
I didn't do anything extra apart from 'make all'

```
~/src/kernelmod$ make all
make -C /lib/modules/3.2.0-27-generic/build M=/home/steeldriver/src/kernelmod modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-27-generic'
  CC [M]  /home/steeldriver/src/kernelmod/hello-1.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/steeldriver/src/kernelmod/hello-1.mod.o
  LD [M]  /home/steeldriver/src/kernelmod/hello-1.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-27-generic'
~/src/kernelmod$ 
~/src/kernelmod$ 
~/src/kernelmod$ ls
hello-1.c  hello-1.ko  hello-1.mod.c  hello-1.mod.o  hello-1.o  Makefile  modules.order  Module.symvers

```

---

### Post by Bucky Ball on 2012-09-12
Please be aware:

> 7. While we are happy to serve as a resource for hints and for asking  questions when you get stuck and need a little help, the Ubuntu Forums  is not a homework service. Please do not post your homework assignments  expecting someone else to do it for you. Any such threads will be taken  offline and warnings or infractions may be issued. ;)

---

### Post by Runicode on 2012-09-12
> **Bucky Ball said:**
> Please be aware:
 
 
 
Approaching the fine line. ;)
 
This isn't a college course. I'm currently an IT Manager going on 12 years now. Just decided I wanted to learn about the unix/linux world and take an online course in it. I guess next time I won't use the word course :)
 
I'll try $ sudo apt-get install linux-headers-$(uname -r) later today and see if that helps.
 
Thanks,
Runicode

---

