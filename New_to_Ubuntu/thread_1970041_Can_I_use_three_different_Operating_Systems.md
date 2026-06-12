---
title: "Can I use three different Operating Systems"
date: 2012-04-30
forum: New to Ubuntu
---

### Post by Electronicman on 2012-04-30
I have a Dell XPS running XP on one HD , and I have installed a second HD where I have UB 11.10. Can I also install the latest and greatest UB 12.4, preferably on the second HD, so that I can boot which one I want?

---

### Post by oldfred on 2012-04-30
I have XP on sda, 10.10 on sdb, and a whole bunch of older installs & test installs, all in 20 to 25GB / (root) partitions. You will have to use manual install to make sure you can choose where to install the grub2 boot loader (sdb) or else it may install to sda.

I prefer to partition in advance so I know exactly where and how large partition will be. Or you can just shrink your 11.10 and let it auto install to the unallocated space, but it may  install grub in sda.

Versions may be different but process is the same.
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?

---

### Post by ammofreak on 2012-04-30
Hi):P: I run Windows 7 (64bit), Windows 7 (32bit) & Ubuntu 10.04 on an Asus G73. As far as I know, one can probably run more...:)

---

### Post by Electronicman on 2012-05-01
Thanks for the advise.

I will try it and report how it went

---

### Post by PeterP24 on 2012-05-01
I hope you didn't gave up on your DVD optical drive to add the second hdd. Since you only use one OS at a time, you might consider a solution I found several years ago when I was still using XP in a dual boot configuration with Ubuntu on my old Dell laptop. 
At that time, I've chosen to buy another hdd - and I installed the Ubuntu OS alone on it. I wanted to have two separate 120 GB hdd (hitachi and toshiba), one for Xp and one for Ubuntu which I would swap depending on my need for one of these OS. The main reason for this was Xp which wasn't very reliable on my Dell Inspiron 1501 back then and every time I reinstalled it would rewrite the grub space - so Ubuntu wouldn't be found at boot times. Each time I reinstalled Xp, I also had to pop the Ubuntu CD and rewrite the boot sector. I also had my part of the guilt - when in Ubuntu I once deleted stuff on Xp partition. 
So I've chosen to buy another hdd and reinstall Ubuntu alone on it - if needed I would preferred to swap the Ubuntu hdd with Xp hdd for several hours than to have both OS side by side in a dual boot (it was very easy on Dell Inspiron 1501 to replace a hdd). 
I found this to be a satisfactory solution - neither OS could affect the other one. I still have the old 120 GB hdd which I used in order to run XP - now I resurrected it as an external hdd with the help of a 2.5" rack because I now run Xp in a virtual machine with Ubuntu as the host OS. But of course the virtual machine solution has its limitations.

---

### Post by Electronicman on 2012-05-01
> **PeterP24 said:**
> I hope you didn't gave up on your DVD optical drive to add the second hdd. Since you only use one OS at a time, you might consider a solution I found several years ago when I was still using XP in a dual boot configuration with Ubuntu on my old Dell laptop. 


Hi Peter,
My Dell XPS desk top was close to the high end of machines at the time, and I had extra slots to add a second drive.

When I got the XPS I had many problems, which after reloading Win XP several times from scratch, I found to be due to the anti virus software which came with the machine. After I tried another anti virus software all was well for many years.

Because of the problems with XP, I was reluctant to mess with the XP drive, and decided to add a second drive for Ubuntu. That too has been working well for several months, but when I tried to upgrade Ubuntu to 10.10 I ran into problems and I had to do a fresh install.

Now Ubuntu 12.04 is available I would like to install this, while keeping 10.10, again I am reluctant to upgrade 10.10 to 12.04, so I thought a triple boot would be a way round it

---

### Post by grahammechanical on 2012-05-01
As others have said, we can boot more than one OS and more than one Ubuntu OS. And many of us think that a fresh install ends up with less issues than an upgrade.

I always install the latest Ubuntu into another partition before changing my existing Ubuntu into the newest Ubuntu, if you see what I mean.

I like to find out if I am going to have any issues setting up the new version the way I like.

Regards.

---

