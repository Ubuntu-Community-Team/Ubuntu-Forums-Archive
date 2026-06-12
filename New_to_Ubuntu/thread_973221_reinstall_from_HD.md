---
title: "reinstall from HD"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by fredfelter on 2008-11-06
I want to reinstall a fresh copy of Ubuntu 8.04 to my Thinkpad T22 in which I'm using a second HD in place of the CD drive for Linux (so I have no functioning CD drive). I thought that if I copied the Ubuntu install CD to an external usb HD I would be able to do it from there since I would be able to boot from the Ubuntu version already installed that I want to replace. Do I have that right?

So I can access the Ubuntu files on the hard drive but I don't know how to proceed from there. Double clicking on any of them doesn't seem to do anything and the ones I have looked at re: Permission say I'm not the owner so I can't change the execute parameters (maybe that is not necessary).

What I need is for ubuntu install to start running from the HD as if I were autorunning the CD. Since I'm a complete novice I don't what commands to utilize to get there.

Thanks.

---

### Post by lovinglinux on 2008-11-06
You should try [[COLOR="Red"]**Unetbootin**[/COLOR]]("http://unetbootin.sourceforge.net/") to boot from a USB drive or from another partition. It extract the necessary files from the ISO image of the Live Cd to your hard drive/usb and creates a boot entry pointing to these files, so you can run the Live CD without a CD drive.

---

### Post by fredfelter on 2008-11-07
I don't understand what UNetbootin is going to do for me, and this is after reading the web page. Am I going to install it on the existing HD that has the version of Linux on it I want to replace or does it go onto the external drive version that I want to add?

Since this is the beginner's forum maybe I dare ask another really basic question that I've never seen addressed directly. What is different about having the exact same contents of my install CD on a USB connected HD and not being able to install vs. doing it from the CD/CD drive itself? This seems like something every computer should be able to do regardless of capacity - boot from another connected source other than a floppy. How hard can that be?

---

### Post by B34ST1Y on 2008-11-07
you could always try using a disk imaging software, such as Acronis True Image. It costs money, but someone may know of a free alternative.. (an equivalent is Norton Ghost)

---

### Post by Yoke &amp; Chung on 2008-11-07
Unetbootin will create a bootable USB drive containing Ubuntu (or other Linux distros). It is quite easy to use, and will even download Ubuntu for you if you have not done it yet.

Once you have the USB setup, you can boot from it (of course you need to enable this from your computer BIOS), and check whether everything is running. If you like it, there is an "install" icon that will enable a full installation.

You can select which drive you want Ubuntu to install to during the installation process.

---

### Post by lovinglinux on 2008-11-07
> **fredfelter said:**
> I don't understand what UNetbootin is going to do for me, and this is after reading the web page. Am I going to install it on the existing HD that has the version of Linux on it I want to replace or does it go onto the external drive version that I want to add?

Since this is the beginner's forum maybe I dare ask another really basic question that I've never seen addressed directly. What is different about having the exact same contents of my install CD on a USB connected HD and not being able to install vs. doing it from the CD/CD drive itself? This seems like something every computer should be able to do regardless of capacity - boot from another connected source other than a floppy. How hard can that be?


Yoke & Chung already explained what it does, so I will explain how. Unetbootin web page is not very clear. I had to test myself to understand how it works. But it is quite simple, as already stated by Yoke & Chung.

I used the Windows version, but I guess the procedure is similar.

First install Unetbootin on your current installation and save the Ubuntu Live CD ISO file somewhere in your home directory. Then launch Unetbootin, select the ISO option and browse the path to the Ubunbtu ISO file on your home directory. Then, select the USB option and click the button to proceed. Unetbootin will extract the ISO from your home directory into the USB drive and will create a boot option. When the process is finished, reboot and select Unetbootin from the grub menu. It will boot from the Live CD extracted to the USB drive, allowing you to run it as Live CD or to install Ubuntu on the machine. That's it.

---

### Post by glotz on 2008-11-07
[QUOTE=B34ST1Y]you could always try using a disk imaging software, such as Acronis True Image. It costs money, but someone may know of a free alternative.. (an equivalent is Norton Ghost)[/QUOTE]
[http://www.partimage.org/](http://www.partimage.org/) (GPL)

---

### Post by lovinglinux on 2008-11-07
> **ilkolinux said:**
> that's a very nice idea, i will try it today and see how it works for me since im still trying to find which linux distro i want to use.

Please notice that this is for those who want to test or install a distro from an USB drive or from another partition on the hard drive, like fredfelter. If you have a working CD drive, you can just burn the Live CD and boot from it.

---

### Post by Liviu-Theodor on 2008-11-07
Maybe the [How to mirror drives]("http://ubuntuforums.org/showthread.php?t=940426") thread will help you? Perhaps you will find better to keep your installation and settings by mirroring your actual drive to a new one.

---

### Post by lovinglinux on 2008-11-07
> **B34ST1Y said:**
> you could always try using a disk imaging software, such as Acronis True Image. It costs money, but someone may know of a free alternative.. (an equivalent is Norton Ghost)

> **Liviu-Theodor said:**
> Maybe the [How to mirror drives]("http://ubuntuforums.org/showthread.php?t=940426") thread will help you? Perhaps you will find better to keep your installation and settings by mirroring your actual drive to a new one.

I think you guys are missing the point here. He wants to install Ubuntu, but he doesn't have a working CD drive. So what he needs is a way to boot the Live CD from an USB device or from another disk/partition. This is exactly what Unetbootin does. 

@fredfelter

My explanation on how to use Unetbootin is in the post [[COLOR="Red"]**#6**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6122371&postcount=6").

---

### Post by fredfelter on 2008-11-07
> **Yoke & Chung said:**
> Unetbootin will create a bootable USB drive containing Ubuntu (or other Linux distros). It is quite easy to use, and will even download Ubuntu for you if you have not done it yet.

Once you have the USB setup, you can boot from it (of course you need to enable this from your computer BIOS), and check whether everything is running. If you like it, there is an "install" icon that will enable a full installation.

You can select which drive you want Ubuntu to install to during the installation process.

Thanks Yoke & Chung but I see a problem - my older Thinkpad doesn't have a USB boot option in BIOS. That means UNetbootin won't work for me, right?

---

### Post by fredfelter on 2008-11-07
> **lovinglinux said:**
> I think you guys are missing the point here. He wants to install Ubuntu, but he doesn't have a working CD drive. So what he needs is a way to boot the Live CD from an USB device or from another disk/partition. This is exactly what Unetbootin does. 

@fredfelter

My explanation on how to use Unetbootin is in the post [[COLOR="Red"]**#6**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6122371&postcount=6").

Thanks for you replies LovinLinux. Your explanation on how to use UNetbootin is very clear.
And you are correct by saying I don't have a working CD. Not only that I have no USB boot option. And I do NOT want to clone my present Ubuntu program; in fact I want to get rid of it and replace it with a fresh one since I've mucked it up badly with various app installs and removals.

---

### Post by lovinglinux on 2008-11-07
> **fredfelter said:**
> Thanks for you replies LovinLinux. Your explanation on how to use UNetbootin is very clear.
And you are correct by saying I don't have a working CD. Not only that I have no USB boot option. And I do NOT want to clone my present Ubuntu program; in fact I want to get rid of it and replace it with a fresh one since I've mucked it up badly with various app installs and removals.

Since you don't have an USB boot option you could boot from the hard drive.

This is a little bit more complicated. Basically you need a spare partition in the machine hd where you will install a fresh Ubuntu. Since you don't have a working CD or USB boot option, Unetbootin will boot the Live CD content from the same hard drive partition where you have the current Ubuntu installed, so you can install it on the spare partition. Here is what you have to do.

1 -Shrink your current partitions using gparted (you must install it first) to make room for the new Ubuntu installation, creating an empty spare partition. I guess there are plenty of gparted tutorials in the forums.

2 - Follow my previous instructions about Unetbootin, but instead of using the USB option, use the hard drive option. Unetbootin will then extract the ISO to your current installation HD (not the empty partition) and create a boot option to launch the Live CD from it. Then boot using Unetbootin option in the boot menu. It will launch the Live CD from your hard drive (not the empty partition) so you can install Ubuntu to the empty spare partition. Once completed this process you will have two Ubuntu options in the boot menu. One of them will be your current Ubuntu installation and the other will be the new Ubuntu installation.

3 - Once you have your new Ubuntu installed you will be able to remove the old one from the boot menu, delete the old partitions and merge the free space with the new Ubuntu partition.

---

### Post by bodhi.zazen on 2008-11-07
Try [uhelp]community/Installation[/uhelp]

[indent]There is a section on no CD ...[/indent]

---

### Post by johanzebin on 2009-01-01
> **lovinglinux said:**
> 
Since you don't have a working CD or USB boot option, Unetbootin will boot the Live CD content from the same hard drive partition where you have the current Ubuntu installed, so you can install it on the spare partition.



Hi I had the same problem, and had basically the same idea.. however I encountered a serious problem:
If you boot the (intrepid, xubuntu desktop version) live-cd from a partition prepared by Unetbootin and try to install, not a single partition from that same harddrive appears when it comes to choosing where to install the system to!
I tried both mounted and unmounted, since I don't know what's right...
Anybody an idea?

---

### Post by fredfelter on 2009-01-01
I don´t know if your situation is the same as mine (2nd HD in carrier where CD/DVD drive also goes) so I finally physically removed the primary HD #1, moved HD #2 to its slot, put CD/DVD drive back in, installed Ubuntu from the CD using the appropriate startup BIOS settings then replaced the 2 HDs to their proper respective locations. Now I have a sweet Thinkpad that has a Windows OS on one HD and Ubuntu on the other. When I turn on the computer I can access either one thru the BIOS > Startup menu which takes only a few seconds longer than normal.Otherwise the computer self boots to the last OS configuration without doing anything. It´s like having 2 complete and independent computers in one box.

---

