---
title: "Dual boot With Two Hard Drives"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by tentel on 2008-08-10
Hello, 


I currently have Vista installed on one of my drives, and I'd like to install Ubuntu on my second drive.


What I would like is to keep grub on the Ubuntu drive and the windows boot loader on the Windows drive.

I would like to use the Windows boot loader, but have the option to pass the reigns over to grub when I want to use Ubuntu.



How exactly would I go about setting something like this up, if it is even possible?



Thanks,

Tim

---

### Post by Tteddo on 2008-08-10
> **tentel said:**
> Hello, 


I currently have Vista installed on one of my drives, and I'd like to install Ubuntu on my second drive.


What I would like is to keep grub on the Ubuntu drive and the windows boot loader on the Windows drive.

I would like to use the Windows boot loader, but have the option to pass the reigns over to grub when I want to use Ubuntu.



How exactly would I go about setting something like this up, if it is even possible?



Thanks,

Tim

I do exactly this with 2 SATA drives, except I use grub as the default loader. Check out how I remap the drives for Windows at the end. I would install Ubuntu on the standalone drive then manually add the Vista drive to grub after you hook up the Vista drive again. This is my menu.lst in the /boot directory. I also mount my Windows drive in the fstab file so I can access it from Linux. You can find out the UUID of a drive with the blkid command.

> ## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=22fe38f4-dd6a-451a-a394-09bcfb1932ae ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=22fe38f4-dd6a-451a-a394-09bcfb1932ae ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22fe38f4-dd6a-451a-a394-09bcfb1932ae ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=22fe38f4-dd6a-451a-a394-09bcfb1932ae ro single
initrd		/boot/initrd.img-2.6.24-19-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Windows 2000 Bork Bork
rootnoverify	(hd1,0)
makeactive
map		(hd0,0) (hd1,0)
map		(hd1,0) (hd0,0)
chainloader	+1

---

### Post by bpowell2005 on 2008-08-10
I've had Windows on drive A and Ubuntu on drive B, but I had to install Grub on the Windows drive. I don't think the windows boot-loader can handle anything besides Windows...Grub can handle both.

---

### Post by tentel on 2008-08-10
Thanks guys!

I'll just use grub then.
it isn't that big of a deal.



So, what I should do is unhook my vista drive and just do a normal install of Ubuntu on the second drive.  Afterwards, I should hook up the Vista drive and then go into Ubuntu and set grub to load vista on default?

The question is, how do I make grub do that?



Thanks
-Tim

---

### Post by bpowell2005 on 2008-08-10
> **tentel said:**
> Thanks guys!

I'll just use grub then.
it isn't that big of a deal.



So, what I should do is unhook my vista drive and just do a normal install of Ubuntu on the second drive.  Afterwards, I should hook up the Vista drive and then go into Ubuntu and set grub to load vista on default?

The question is, how do I make grub do that?



Thanks
-Tim

Well, from personal experience...and based on XP, not Vista...

Don't unhook the drive. Just hook up your new drive, put the Ubuntu CD in, and tell it to install Ubuntu...when asked what drive to install on, just select the new drive...when asked about where to put Grub, put it on the Windows drive. Everything worked like a champ for me!

---

### Post by Bodsda on 2008-08-10
I would suggest you detach the windows hard drive then install ubuntu. Then you can reattach the windows hard drive. In your system bios you will have to tell it to boot the windows hard drive first. This will then use the windows boot loader, however you will have to add ubuntu to this by hand.

Hope this helps

Bodsda

---

### Post by caljohnsmith on 2008-08-10
Tim, if you keep your internal HDD with Windows on it connected when you install Ubuntu, then when you get to the part about installing Grub, most likely Ubuntu will by default install Grub to the MBR of your Windows drive (hd0). That means though that you will always have to have your external drive (Ubuntu) connected to boot any OS, because if you disconnect your Ubuntu HDD, then even though Grub is installed on your internal HDD's MBR, Grub needs its configuration files in the Ubuntu partition on the second HDD to boot. That may be OK for you if you don't intend on disconnecting your second HDD.

Another option would be to install Grub to the MBR of your second HDD, and then go into your BIOS and set it so your second HDD comes before your internal HDD in the boot order. That way you don't touch your internal HDD, and you won't have any problems booting Windows if you disconnect your second HDD. To do this, when you get to the part about installing Grub in the Ubuntu installer, hit the "advanced" button and tell Grub to install to (hd1) instead of (hd0). 

Anyway, just some thoughts, hope it helps.

---

### Post by ntu on 2008-08-10
I have used this method:

[http://www.pperry.f2s.com/linux-dualboot-2hd.htm](http://www.pperry.f2s.com/linux-dualboot-2hd.htm)

and it works very well.

---

### Post by Tteddo on 2008-08-10
> **caljohnsmith said:**
> Tim, if you keep your internal HDD with Windows on it connected when you install Ubuntu, then when you get to the part about installing Grub, most likely Ubuntu will by default install Grub to the MBR of your Windows drive (hd0). That means though that you will always have to have your external drive (Ubuntu) connected to boot any OS, because if you disconnect your Ubuntu HDD, then even though Grub is installed on your internal HDD's MBR, Grub needs its configuration files in the Ubuntu partition on the second HDD to boot. That may be OK for you if you don't intend on disconnecting your second HDD.

Another option would be to install Grub to the MBR of your second HDD, and then go into your BIOS and set it so your second HDD comes before your internal HDD in the boot order. That way you don't touch your internal HDD, and you won't have any problems booting Windows if you disconnect your second HDD. To do this, when you get to the part about installing Grub in the Ubuntu installer, hit the "advanced" button and tell Grub to install to (hd1) instead of (hd0). 

Anyway, just some thoughts, hope it helps.

I always wanted mine to be able to single boot to the windows drive if I had too, and this articulates why I did what I did better than I did!

---

