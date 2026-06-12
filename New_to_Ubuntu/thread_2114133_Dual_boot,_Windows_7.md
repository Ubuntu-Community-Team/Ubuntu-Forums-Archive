---
title: "Dual boot, Windows 7"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by dragonbat13 on 2013-02-09
Hi, first post.
 
What I have done:
I built a computer for my mother out of a HP Slimline, completely updated, and installed Ubuntu 12.04.  Its the only OS on the computer, and so far she likes it.  I still have to refine the install for her sake.  Mainly install Wine so I can set up her router the way she wants.
 
What I have and intend on doing.
I am building my own completely new computer.  It will be a i7 3770K, 8G DDR3, and SSD for operating system and programs.  Pretty normal setup.
 
My intentions are to run Windows 7 along with Ubuntu studio 12.10 on a single 256G Samsung 840 SSD.  I want the Ubuntu studio for music recording since I am a guitarist and recording musician.  I like the idea of a open source recording setup, and I also like having the recording operating system seperate from the Windows operating system.
 
My questions are, should I go with the single 256G SSD for everything, or setup two 128G drives, one for each OS?  I also intend on using a single 1T (or possibly2T) WD black HDD for file storage.  The HDD will store files for both operating systems.  
 
The computer will also do some gaming, although that is a second though over the other two requirements.  All in all the I want the computer to do File Conversions through Windows and Ubuntu (whichever I like using the best).  Lots of video converting.  I want it to be able to use the most out of Ubuntu Studio, and some gaming.\
 
So one 256 or two 128 SSD?  What about 1T HDD, 2x1THDD, or single 2T HDD?
 
Thanks for the help!!

---

### Post by sudodus on 2013-02-09
> **dragonbat13 said:**
> 
What I have and intend on doing.
I am building my own completely new computer.  It will be a i7 3770K, 8G DDR3, and SSD for operating system and programs.  Pretty normal setup.
 
My intentions are to run Windows 7 along with Ubuntu studio 12.10 on a single 256G Samsung 840 SSD.  I want the Ubuntu studio for music recording since I am a guitarist and recording musician.  I like the idea of a open source recording setup, and I also like having the recording operating system seperate from the Windows operating system.
 
My questions are, should I go with the single 256G SSD for everything, or setup two 128G drives, one for each OS?  I also intend on using a single 1T (or possibly2T) WD black HDD for file storage.  The HDD will store files for both operating systems.  
 
The computer will also do some gaming, although that is a second though over the other two requirements.  All in all the I want the computer to do File Conversions through Windows and Ubuntu (whichever I like using the best).  Lots of video converting.  I want it to be able to use the most out of Ubuntu Studio, and some gaming.\
 
So one 256 or two 128 SSD?  What about 1T HDD, 2x1THDD, or single 2T HDD?
 
Thanks for the help!!
Welcome to the Ubuntu Forums :-)

Since you will be installing Windows and Ubuntu Studio yourself, it should be straight-forward, and I would say, that it is OK (and maybe simpler) to use only one SSD for dual boot. I have done such installations with XP, Vista, 7 and 8 (developer's preview) along with various Ubuntu versions and flavours including Ubuntu Studio.

It would be a different story with a new Windows, that is already installed with UEFI. Then it might be a good idea to install on two drives, and avoid tampering with the Windows drive at all.

I suggest you have one HDD for storage (internal) and one or two HDD(s) for backup (external via USB3 or eSATA), and that you set up some nice and reliable backup system. Don't take the risk to lose your recordings because of a disk failure!

*Edit*: Rememeber to install the least intelligent system first (Windows), otherwise you will have to repair the boot sector to boot Ubuntu!

---

### Post by dragonbat13 on 2013-02-09
Boy that was quick!
 
Thanks for confirming what I was thinking.  I really wanted to use the single SSD for simplicitys sake.
 
I got a 750G External also.  Gonna set that up for backup use.
 
Sure appreciate the help.
 
Now all I got to do is think about partitions and such, but thats for another day and thread.  Gotta get the computer built.  Only good thing about tax time is I get a new toy each year!

---

### Post by sudodus on 2013-02-09
Good luck :-)

---

### Post by Mark Phelps on 2013-02-09
Furthermore, 40GB should be enough (60GB, if you want) for Win7 -- since you will be using Ubuntu for most of your work.

---

### Post by clive littlewood on 2013-02-09
Hi

I would recommend that you install windows first. Then install Ubuntu and you will then be given the choise to let ubuntu decide the partion sizes or you can tweak them yourself.

Come back nearer the time if you require further info.

Good luck and welcome to the wonderful world of Linux.

Clive

---

### Post by oldfred on 2013-02-09
On your Mom's system, you should not need wine to set up router. I just installed a new router and yes they provide a CD that only runs under Windows to do auto configuration. But you should just be able to use Firefox or any browser and sign into it and manually set all parameters, wifi names, security etc.
[http://192.168.0.1/](http://192.168.0.1/)
or 
[http://192.168.1.1/](http://192.168.1.1/)
Or something similar.

I know eventually hard drives fail, so I want a operating system on every hard drive even if it is just a data drive. With very large drives now a 10 or 20GB for a system that you know will boot is worth the extra space.

I also like separating Windows & Ubuntu. But many dual boot from one drive so it is your call.

But with the very new systems, you will have the added complication of UEFI or BIOS. All the new systems are UEFI but have a fallback of BIOS/Legacy/CSM or some way to work the old fashioned BIOS with MBR partitioning. 

Windows only boots with UEFI when you partition with gpt. Ubuntu will boot from a gpt partition drive in either UEFI or BIOS.

But to dual boot you have to install both Windows and Ubuntu in either UEFI or BIOS whether one drive or several.

If you do UEFI install:
       GPT Advantages (older but still valid)  srs5694 post #@:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

    
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

