---
title: "Ubuntu 64-bit and Windows installer?"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by Nathan Brazil on 2012-07-20
Hi,

I'm looking into giving Ubuntu 12 a try, and noted the Windows Installer method. But, if I use this, and specify the install HDD as other than C, will that still work? Also, how do I go  about getting the 64-bit version to install via Windows Installer method?

Is there a better way of doing this, where I end up with a dual booting system, with Windows 7 64-bit on my C: drive and Ubuntu on another HDD?

Thanks,


Nathan

---

### Post by Gone fishing on 2012-07-20
If you have a spare Hard drive you can install on that and yes it will be better than Wubi in my opinion. When you install you will need to specify that you want to install on this drive. 

If you removed the partitions from this drive and create free space you could tell the installer to install into the largest free space. Windows disk manager will remove the partitions on the spare drive or partition editor on the Ubuntu live CD.

---

### Post by Nathan Brazil on 2012-07-20
> **Gone fishing said:**
> If you removed the partitions from this drive and create free space you could tell the installer to install into the largest free space.

The spare drive is bare and formatted, no additional partitions to worry about.

So it's an Ubuntu live CD I need for installing this way and in 64-bit?

Oh, just noticed that the 64-bit version appears to be for AMD CPU's only. I'm using an i7. So am I right in thinking that I should use the X86 Ubuntu version, and therefore there is no 64-bit version for Intel based PC's?

Thanks,


Nathan

---

### Post by maniandram on 2012-07-20
@Nathan, no you are wrong
i7 is an 64-bit processor - you should install 64 bit Ubuntu for best performance.
AMD 64 is a standard for 64-bit processors.
Just because the name has AMD doesn't mean 64 bit is only for AMD processors.
Intel adopted the standard in all processors since the Core family.
Thanks,
Best luck with Ubuntu
PS:Once you install Ubuntu, check out Kubuntu (at [http://kubuntu.org](http://kubuntu.org))

---

### Post by Nathan Brazil on 2012-07-20
> **maniandram said:**
> @Nathan, no you are wrong
i7 is an 64-bit processor - you should install 64 bit Ubuntu for best performance.

Okay, thanks for putting me straight. Will get to work installing once I have ironed out the latest hideous kink in Windows 7 64-bit. Microsoft: Making Like Just A Little More Difficult For US All. :)

---

### Post by oldfred on 2012-07-20
If you install to any second drive you should use the manual install or Something Else. Otherwise grub2's boot loader will install to sda which usually is the Windows drive. Best to keep Windows boot loader in sda and install grub2's boot loader to sdb. Then change BIOS to boot sdb. From grub you can boot either Ubuntu or Windows and if issues with sdb then you can still directly boot Windows from sda.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by QIII on 2012-07-20
To add to oldfred:  I would suggest going so far as to disconnect the physical drive on which Windows is installed before installing Ubuntu on the other.  This will entirely avoid the risk of a frustrating and potentially costly accident.

When you plug the Windows drive back in and change your boot priority to the Ubuntu disk, simply update GRUB to add Windows to the selections.

---

### Post by Gone fishing on 2012-07-20
Its as long as it is short if you let Ubuntu install into largest free space then the boot loader will be put on sda (the windows drive) mbr and at boot you can choose Windows or Ubuntu. That's what I would do. 

If you disconnect the Windows drive or manually partition and put the grub bootloader on sdb (the spare drive) then in order to start Ubuntu you will need to tell the system BIOS to boot from that drive usually by pressing F11 or similar on boot.

You choose what suits you best - if you put the bootloader on sda (The Windows drive) it is trivially easy to remove it.

Post edit

QIII's solution also works well for me - safe and sensible - update grub with sudo update-grub.

---

### Post by LordEager on 2012-07-20
I think that all these suggestions are good, but not suitable for a new user that looked to me a bit confused about linux world... I always suggest to try a linux distro from live CD (or live DVD ) if you wanna see "what it's all about" then, if you like it, the best thing to do, is to make a free partition with a partition manager (partition wizard for example is great because you can write the iso on a cd and use it by booting from Cd drive) and make a clean install of the distro on the partition just created. I' ve never liked wubi and for experience i have always encountered issues in the past with wubi's grub... i don't wanna scare anyone, but it happened to me that wubi almost messed up my win system in the past... Following my way you have no risk and best results, if you don't like the distro you can always format the partition and your win partition will be left untouched... 
There are several step-by-step guides for preparing a partition for linux, it's just enough to create a partition formatted in ext(x) and a partition formatted for swap, and that's it...
Same obviously applies to different HDDs instead of different partitions.

---

### Post by Nathan Brazil on 2012-07-21
Okie-cokie, thanks to all who replied. Will have a bash at this in the coming days and report back. :)

---

