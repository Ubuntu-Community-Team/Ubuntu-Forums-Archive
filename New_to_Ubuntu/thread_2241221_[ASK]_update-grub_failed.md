---
title: "[ASK] update-grub failed"
date: 2014-08-25
forum: New to Ubuntu
---

### Post by syaiful2 on 2014-08-25
[IMG]https://mail.google.com/mail/u/0/images/cleardot.gif[/IMG]
help me, please ? my notebook with triple booting os,

i've just re-install my ubuntu, but it won't start normally

why this message shown when ubuntu not yet finish installed ?
[IMG]http://s1.postimg.org/4tenxd25r/DSC_0911_1.jpg[/IMG]
[http://postimg.org/image/g5r9f5auj/](http://postimg.org/image/g5r9f5auj/)

not possible install bootloader
[IMG]http://s27.postimg.org/dh4ymfx6b/DSC_0914_1.jpg[/IMG]
[http://postimg.org/image/azt7f6d9r/](http://postimg.org/image/azt7f6d9r/)

install without bootloader
[IMG]http://s17.postimg.org/66opozzzz/DSC_0918_1.jpg[/IMG]
[http://postimg.org/image/vph220jjv/](http://postimg.org/image/vph220jjv/)

now my ubuntu can't start normally
[IMG]http://s17.postimg.org/mya17r08v/DSC_0920_1.jpg[/IMG]
[http://postimg.org/image/701bhm60r/](http://postimg.org/image/701bhm60r/)

sory i'm not good in english
thanks for your help...

---

### Post by sandyd on 2014-08-25
I have moved your post to the New To Ubuntu forums where you will get better help

edit: fixing pics...

---

### Post by yancek on 2014-08-25
Did you accept the default to install the bootloader to /dev/sda?  Or to its partition?
What other operating systems do you have?

---

### Post by grahammechanical on 2014-08-25
In Linux/Ubuntu we need a boot loader because the Windows boot loader is not programmed to recognise any operating system other than Microsoft operating systems. In Ubuntu our boot loader is called Grub. It means GRand Unified Boot loader. It will recognise not only Linux operating systems but also Microsoft operating systems as well as others.

Grub has to be installed on to the hard disk as part of the installation process of Ubuntu. Grub  is always installed towards the end of the installation process. It usually installs by default into the MBR of the first hard disk (called sda in Linux. Sata Drive a). The process called update-grub creates the configuration files that make up the boot menu and inform the menu where the operating system is located on the hard disk and which file to run to load the operating system.

In your case the process of updating the Grub configuration files failed. and it could be that the location to install Grub was incorrect. Did you allow the installer to install Grub into sda or did you change the direction to somewhere else?

My advice to you would be to re-install Ubuntu. I cannot give more advice as you do not give us information about your machine, the partitions on the hard disk or even if there is another operating system on it. We do know it is Ubuntu 14.04 that you are trying to install. We know that from the image in the first photograph.

Regards.

---

### Post by syaiful2 on 2014-08-25
@yancek : 
i have xp, 7 and ubuntu on my notebook

@grahammechanical : 
   I have 3 OS, the first xp, 7 and ubuntu, the hard drive is partitioned into 5 parts. 
I've installed ubuntu root on partition that I installed by default. 
by the way, I have checked my hard drive using hd tune, many blocks are broken there? does it affect? 



thank you so much

---

