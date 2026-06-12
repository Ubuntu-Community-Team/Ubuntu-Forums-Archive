---
title: "Fatal error: no such file or directory"
date: 2011-11-01
forum: Programming Talk
---

### Post by ps_arunkumar on 2011-11-01
Hi all,
I have started learning kernel programming. When I started to compile my first program, I am getting error as 

hello.c:1:25: Fatal error:linux/module.h: No such file or directory
compilation terminated.
make:***[hello.o]Error 1

I am using 2.6.38.8 kernel version and running Ubuntu 11.04. I have tried to specify the destination using include and also used those 2 header files directly into make file. Nothing worked.

I have attached program and makefile. Please correct where I am wrong, which will be very much helpful for my career start up.

---

### Post by Bachstelze on 2011-11-01
First, don't post code, especially code that small, as attachment. Paste it in your post with CODE tags, not everyone is going to go through the hassle of downloading and unzipping the attachment.

Second, install the linux-headers package that corresponds to your kernel version.

---

### Post by ps_arunkumar on 2011-11-01
This is my first thread, so i was not aware of it. Thanks for it.

When i tried to install the Linux headers it says Linux header is already newest version

---

### Post by Bachstelze on 2011-11-01
Which package exactly are you trying to install?

---

### Post by ps_arunkumar on 2011-11-01
arun@ubuntu:~$ sudo apt-get install linux-headers-$(uname-r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.38-8-generic is already the newest version.
linux-headers-2.6.38-8-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Bachstelze on 2011-11-01
A quick Google search seems to indicate that your code is wrong. I suggest you use other learning material, because whatever you are using is probably outdated, or just plain wrong.

---

### Post by ps_arunkumar on 2011-11-01
ill be happy if you give me link to materials to learn (if possible)

---

### Post by Bachstelze on 2011-11-01
Sorry but I am not familiar with Linux kernel programming (hence why I had to use Google to find out what was wrong with your code).

---

### Post by SevenMachines on 2011-11-01
The makefile should be 
```
 obj-m += hello.o
```not
```
 obj-m +: hello.o
```But as [Bachstelze]("http://ubuntuforums.org/member.php?u=51114") mentions, there are problems with your code and a good kernel programming guide would be useful, luckily the linux documentation project provides exactly that to get you started
[http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html](http://tldp.org/LDP/lkmpg/2.6/html/lkmpg.html)

---

