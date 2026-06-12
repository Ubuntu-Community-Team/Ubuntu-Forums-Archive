---
title: "Installing Ubuntu tonight. 3 quick questions"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by green_arrow on 2008-06-14
I just made the important decision to switch to Linux. I am sick of looking at AVG and all the antivirus and antispam crap. I am sick of using cygwin to ssh on a school computer together with 10other people when I need to code.

I am very excited about the switch. I hope that you can help me with 3 questions:

1. What compatibility issues should I expect? Will I be able to just  put my backup cds in and open all my Windows files?
2. Does Linux come with GCC?
3. Is every Linux OS actually a GNU/Linux?

Thank you in advance!

---

### Post by FAJALOU on 2008-06-14
Welcome Welcome to Ubuntu :)

One you need to make a new partition for Ubuntu to reside on.  It will install a thing called GRUB, which is like the Linux version of MBR (Microsoft Boot Record).  Off the top, as long as the ntfs partition does pretend to corrupt, you should be able to boot back to Windows (but why would you want to :) ).  You need to make sure that when you do this, you will be able to know what you are doing also, some people come in and accidentally format their Windows Partition, which you may not want, or do.  Its up to you.
  Alot of the compatability issues you will find will be with video cards (particularly closed source like Nvidia, and ATX,), and also many wifi cards can be a pain.  But ethernet normally works easily.

Not sure about GCC, but it should be in the repoes, so it would be easy to find.

And yes I do believe (don't quote me on it though), that all Linux OSes are GNU/Linux.

Welcome again and good luck

---

### Post by alienexplorers on 2008-06-14
1) Ubuntu can read NTFS diredtories and documents.  In order to run windows programs you will need Wine or Cedega.

---

### Post by Rhubarb on 2008-06-14
> 1. What compatibility issues should I expect? Will I be able to just  put my backup cds in and open all my Windows files?
This depends what types of files you wish to open.
For the most part you should be fine. - MS office documents, music, videos, pictures, acrobat, text files etc.
If you wish to execute windows applications, you can use [wine]("http://www.winehq.org/") which will let you run some windows apps.


> 2. Does Linux come with GCC?
The Ubuntu Distribution does not come with GCC by default, however it is trivial to install gcc:
```
sudo aptitude install build-essential
```


> 3. Is every Linux OS actually a GNU/Linux?
Yes.
The GNU tools can also be found with other kernels too, such as Solaris and Mach.


The best way is to try out the live CD before installing it to have a look yourself.

---

### Post by Rhubarb on 2008-06-14
> **FAJALOU said:**
> ... which is like the Linux version of MBR (Microsoft Boot Record). 
MBR stands for Master Boot Record.  Nothing to do with Microsoft.

---

### Post by FAJALOU on 2008-06-14
My bad.

---

### Post by akiratheoni on 2008-06-14
> **green_arrow said:**
> I just made the important decision to switch to Linux. I am sick of looking at AVG and all the antivirus and antispam crap. I am sick of using cygwin to ssh on a school computer together with 10other people when I need to code.

I am very excited about the switch. I hope that you can help me with 3 questions:

1. What compatibility issues should I expect? Will I be able to just  put my backup cds in and open all my Windows files?
2. Does Linux come with GCC?
3. Is every Linux OS actually a GNU/Linux?

Thank you in advance!

1.) Depends on your hardware, use a LiveCD to determine compatibility.
2.) Most versions do, but with Ubuntu, you'll need to use the command:
```
sudo apt-get install build-essential
```
to get it.
3.) Yes, Linux is short for GNU/Linux.

---

### Post by hyper_ch on 2008-06-14
before you alter/shrink your partitions, make a **BACKUP**. Although it's safe to twinker with it, there is always a small chance of a problem and if you encounter one, then you'll lose all your data.

---

### Post by colo on 2008-06-14
Actually, not all distributions of the Linux kernel ship with the GNU userland; there are many (embedded) projects that use busybox and not even the GNU C library, but dietlibc or uclibc instead. However, I don't think any of the other free C compilers (tcc, for example) is able to compile the kernel, so I guess at least the GCC (GNU Compiler Collection) is common amongst all distributions of the Linux kernel.

---

### Post by takumidesh on 2008-06-14
I have noticed a lot of network card compatibility issues with laptops, though so far with 8.04 my lappy has been doing fine with the network card, use the liveCD first and test everything out before you install. Also make sure you make a backup of everything before you make any big decisions

---

### Post by Kronie on 2008-06-14
Not to be an a$$, but,if you cant live without antivirus or antispam software, then i am not sure if linux is right os for you... but on the other hand.. it is an easy OS once you set up everything you need(which can take from 2 hours to couple days..or even weeks) 
after that, the only difference between ubuntu and linux is that..you cant play games the way you could in windows.. i mean there is wine, butit cant play ALL of games out there(but it does play most of 'em)

---

### Post by takumidesh on 2008-06-18
Wine really only works with major games, if you want to play an unknown game, then have fun playing it at 1 fps. Ubuntu is definitely the way to go, much more secure, constantly updated by the community, so many killer apps that are free!

---

### Post by mailtwogopal on 2008-06-18
Hi,

  You can try a live CD to experience it. otherwise u can have dual boot of Windows as well as Ubuntu using Wubi installer with which u can install ubuntu as we install other softwares commonly in windows. as u will be new to linux (probably hope so) u can have both windows and linux in uo box so that sudden migration to linux will not make u feel uncomfortable. then slowly u can fully migrate to linux - Ubuntu.

---

### Post by sailor2001 on 2008-06-18
and always defrag windows before doing anything with it.

---

### Post by takumidesh on 2008-06-18
Always make backups, that is one of the most important things to do, and don't do the install on a business computer do it on the one with the least important documents, take no chances.

---

