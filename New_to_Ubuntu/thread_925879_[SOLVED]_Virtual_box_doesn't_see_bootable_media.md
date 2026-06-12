---
title: "[SOLVED] Virtual box doesn't see bootable media"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by eru777 on 2008-09-21
Im having a problem with virtual box and it says it does not see the bootable media . I have the original windows XP disc on the drive but I guess something is wrong.

After reading the FAQ i saw this

You will need to install the following packages on your Linux system before starting the installation (some systems will do this for you automatically when you install VirtualBox):
Qt 4.3.0 or higher;
SDL 1.2.7 or higher (this graphics library is typically called libsdl or similar).

Maybe that's the problem ?
So, I guess virtual box is free, but these
[http://trolltech.com/downloads/commercial](http://trolltech.com/downloads/commercial)
aren't?
:confused:
Anyway, can anyone tell me of any thoughts on how to solve this problem and use virtual box? Thanks

---

### Post by eru777 on 2008-09-21
Oh anyway I fixed it. I just had to press F12 to boot the disc.

Sorry :(

---

### Post by DGortze380 on 2008-09-21
> **eru777 said:**
> Im having a problem with virtual box and it says it does not see the bootable media . I have the original windows XP disc on the drive but I guess something is wrong.

After reading the FAQ i saw this

You will need to install the following packages on your Linux system before starting the installation (some systems will do this for you automatically when you install VirtualBox):
Qt 4.3.0 or higher;
SDL 1.2.7 or higher (this graphics library is typically called libsdl or similar).

Maybe that's the problem ?
So, I guess virtual box is free, but these
[http://trolltech.com/downloads/commercial](http://trolltech.com/downloads/commercial)
aren't?
:confused:
Anyway, can anyone tell me of any thoughts on how to solve this problem and use virtual box? Thanks

Assuming you've already clicked on "New" and create a virtual machine, VDI etc.. etc.. and want to install from a cd or dvd...

highlight the machine you want to install to, click settings, highlight CD/DVD ROM, Select Mount CD/DVD-ROM, select Host CD/DVD-ROM.

You may also need to change the boot order, located in:
Settings>General>Advanced

---

### Post by eru777 on 2008-09-21
> **DGortze380 said:**
> Assuming you've already clicked on "New" and create a virtual machine, VDI etc.. etc.. and want to install from a cd or dvd...

highlight the machine you want to install to, click settings, highlight CD/DVD ROM, Select Mount CD/DVD-ROM, select Host CD/DVD-ROM.

You may also need to change the boot order, located in:
Settings>General>Advanced

Thanks anyway I fixed it. It was that simple problem. If I encounter any new ones I 'll be sure to check in here.

---

