---
title: "Linux boot process?"
date: 2013-04-17
forum: New to Ubuntu
---

### Post by vailixi on 2013-04-17
What all has to happen when I boot up my computer to load ubuntu? Grub, kernel, x, etc? What's some good reading on the subject. Yes I'll read a 700 page manual to find out all this stuff. :KS

---

### Post by audiomick on 2013-04-17
In short:

The computer has some memory that tells it that it is a computer. That is generally the BIOS, or EFI. What is in there tells it where to look for the first intructions. These are generally on a hard drive, and are likely to be a boot loader. In the case of a Linux system, that might be GRUB. The boot loader provides the opportunity to choose between whatever operating systems are installed. If there is only one, it is accessed automatically. The chosen operating system is loaded, and in the process, things like the x-server are started to provide the desktop environment.

I don't really know of any resources to tell much more than this, but the Wikipedia is a good starting point.
[http://en.wikipedia.org/wiki/Booting]("http://en.wikipedia.org/wiki/Booting")

---

### Post by Bashing-om on 2013-04-17
vailixi; Hi !

Here are some links you will find of interest ....
[http://duartes.org/gustavo/blog/post/kernel-boot-process](http://duartes.org/gustavo/blog/post/kernel-boot-process)
[http://www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/](http://www.expertslogin.com/linux-administration/boot-process-of-linux-in-detail/)
And one doesn't have a clue till one looks at upstart:
[help.ubuntu.com/community/UbuntuBootupHowto]("http://help.ubuntu.com/community/UbuntuBootupHowto")
[INDENT]Happy trails to you

[/INDENT]

---

### Post by DuckHook on 2013-04-17
> **vailixi said:**
> ...I'll read a 700 page manual to find out all this stuff. :KS

You're a braver man than I, Gunga Din.

---

### Post by oldfred on 2013-04-18
This is about Vista, but all the older BIOS/MBR computers boot similarly. Grub does not use PBR or partition boot sector like Windows, but syslinux and lilo boot loaders do use PBR. At end is some discussion of grub legacy, but grub2 now is different.
       
Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

    
Vendor info:
       Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

---

