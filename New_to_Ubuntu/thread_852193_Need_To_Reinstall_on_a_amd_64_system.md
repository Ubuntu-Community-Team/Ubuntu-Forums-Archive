---
title: "Need To Reinstall on a amd 64 system"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Majorflam on 2008-07-07
Hi,

I am using Ubuntu and loving it. The problem is that I installed the amd 64bit version and it gives problems. I can't use skype, and the support for flash on Opera or Firefox is dismall, causing crashes galore.

I want to totally reformat my hard drive and install an alternative version to amd64 that will remedy these problems. I have a dual boot allowing me to use Windows XP alongside Ubuntu and I'd like to keep Windows XP, but I could live without it if it'd be a hassle to keep it.

How would I do all this?

---

### Post by phidia on 2008-07-07
You already have a partition for the 64 bit install so you can use that-just install over it. Maybe you will want to use the alternative x386 iso but you could use the desktop cd too. 
If you run into problems you can use cfdisk from a livecd terminal and just delete the partition that your current install is on.

---

### Post by Majorflam on 2008-07-07
> **phidia said:**
> You already have a partition for the 64 bit install so you can use that-just install over it. Maybe you will want to use the alternative x386 iso but you could use the desktop cd too. 
If you run into problems you can use cfdisk from a livecd terminal and just delete the partition that your current install is on.

Hi,

Which version of ubuntu would I download to do this, and how would I install over the current partition?

---

### Post by Sbarton on 2008-07-07
Sorry to see you have difficulty with Opera. I have AMD64 version installed with the latest ver.of Opera 
Version
9.51
Build
2061
Platform
Linux
System
x86_64, 2.6.24-19-generic
Qt library
3.3.8b
Java
Java Runtime Environment installed
and it all seems to run ok!
regards

---

### Post by Majorflam on 2008-07-07
OK, on the download page - [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) -  I'm assuming I should select the "standard personal computer" version, even 'though I have amd64?

---

### Post by starcannon on 2008-07-07
Majorflam:

Yes, you can install the standard or 32bit version on your 64bit hardware, its how I do it here in fact. If you don't have more than 3gb of ram you won't see any difference, and for now 32bit is much easier to administer, especially if your new to the linux operating system.

GL

---

### Post by Majorflam on 2008-07-07
I've reached the install point and selected the partition that has ubuntu 64bit on it. I've deleted the partition and then told ubuntu to install on the free space. However, I keep getting an error that no root partition has been found!!?

---

### Post by starcannon on 2008-07-07
If your using the partition editor to define your partition yourself, you should set aside say 10~20gb for / (root), >= the amount of ram in your machine for /swap, and the rest to /home.

otherwise if you don't want to be bothered you can just rerun the installer and tell it to use the entire partition you want Ubuntu on, it will take care of the rest, though you won't have a seperate /home partition that way; I recommend having /home on a seperate partition my self.

---

