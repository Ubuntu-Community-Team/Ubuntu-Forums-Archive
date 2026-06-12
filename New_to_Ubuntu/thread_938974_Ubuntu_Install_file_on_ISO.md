---
title: "Ubuntu Install file on ISO"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by jiminy82 on 2008-10-05
I downloaded the Ubuntu ISO from the website. I believe it is the new 8.1 BETA version. When I looked in the ISO I found an exe file which was weird cause I didn't think Linux used exe's.

When I clicked it, it gave me a menu asking for a username/password to install. My question is...if I install Ubuntu this way, will it allow me to partition my C: drive and keep my current windows installation? Or will it automatically format my drive and put it in a Linux format?

I want to keep both OS's and I don't want to lose what I have, so I need to know if I need to partition the space before I click on that exe. Oh and if I don't need to partition before hand, will it create the boot sequence for choosing which OS to go into when I boot up?

Thanks

---

### Post by halitech on 2008-10-05
I believe the exe file you found is for WUBI which is what is being used to install Ubuntu from within windows for those who want to try it out without actually formatting their hard drive or partition it. You should be able to set up a dual boot by setting the slider to the amount of space you want to give Ubuntu

---

### Post by Gutt on 2008-10-05
> **jiminy82 said:**
> 
I want to keep both OS's and I don't want to lose what I have, so I need to know if I need to partition the space before I click on that exe. Oh and if I don't need to partition before hand, will it create the boot sequence for choosing which OS to go into when I boot up?

Thanks

To dual boot, you need at least two partitions (one with Windows and one with Ubuntu), you can't put Ubuntu and Windows on the same partition.

For the boot sequence, during Ubuntu's installation, it'll install Grub 1.5 so you don't need to worry about that.

---

### Post by jiminy82 on 2008-10-05
Thanks for the quick responses guys. I guess what I am getting at is, will the WUBI install file allow me to partition within that install or do I need to partition beforehand?

---

### Post by halitech on 2008-10-05
I haven't used WUBI so I'm not sure but from what I understand, WUBI actually installs Ubuntu in a virtual partition (ie its a single file that holds all the Ubuntu files and folders) so it doesn't actually partition anything and to get rid of Ubuntu, you simply remove it from Windows Add/Remove programs.

---

### Post by Gutt on 2008-10-05
Wubi is to use Ubuntu like a Windows exe file if I remember well (never used it).

From their site

> You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. It works just like any other application. Wubi is spyware and malware free, and being open source, anyone can verify that.

---

### Post by jiminy82 on 2008-10-05
So to install the real Ubuntu I have to burn it and partition my drive. I was hoping that I could save the step of burning it.

Thanks for your help guys.

---

### Post by Gutt on 2008-10-05
There is no other way of really installing any distribution (I think :P ). Anyways good luck installing Ubuntu !

---

### Post by jiminy82 on 2008-10-05
Thanks, I am sure I will be back when I start installing stuff. :D

---

### Post by halitech on 2008-10-05
if you want to avoid burning a cd, there is LUBI ( [http://lubi.sourceforge.net/lubi.html](http://lubi.sourceforge.net/lubi.html) ) which runs from within windows and allows the creation of a true linux partition and it will download the ISO as well for you

---

