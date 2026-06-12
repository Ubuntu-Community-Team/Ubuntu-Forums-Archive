---
title: "Install Ubuntu as secondary OS"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by jammedubu on 2013-03-16
Hello there.

I've been an ubuntu user for a while on media systems. However, i'd li ke to use it in dual boot now too (the platform has matured a lot lately and I think it's time to start doing it). However, how can I install Ubuntu without having Grub boot into Ubuntu on startup? I want to start Windows automatically within x seconds (When installing Ubuntu with standard settings, Grub automatically puts Ubuntu on top of the list).

Basically my question is how can I install ubuntu as an optional secondary OS while still being able to boot in to Windows automatically?

---

### Post by Mark Phelps on 2013-03-16
One way to do that is to install it like usual and then install Grub-Customizer and set it to boot into Windows by default.  You can also set a timer using the same app.

---

### Post by jammedubu on 2013-03-16
And what would be the usual way of installing it as to make sure my Windows files are untouched :D ? And is it an ubuntu app or a windows app ?

---

### Post by fantab on 2013-03-16
I am assuming that you only have one HDD on your machine. When you install Ubuntu you have to install Grub, otherwise you cant boot into Ubuntu. And when Grub is installed it WILL overwrite Windows Boot Loader. (AFAIK Windows Boot Loader does not recoginize Linux OS and will not boot it, on the other hand Grub will flawlessly boot Windows).

Now to answer your original question:
[QUOTE=jammedubu]...how can I install ubuntu as an optional secondary OS while still being able to boot in to Windows automatically?[/QUOTE]

Grub, by default, will boot Ubuntu. However, you can easily change your default OS to boot. To do this you have to edit /etc/default/grub and change the default OS.

After Installing Ubuntu do this from Ubuntu - Terminal:

```
$ gksu gedit /etc/default/grub
```

... and edit the line GRUB_DEFAULT=0 to **GRUB_DEFAULT=x** (where "x" is the Windows' Grub menu entry Number. It will most likely be 2 or 3). You can change and verify what entry is selected at Grub-Menu by default and adjust accordingly.

After you have edited, save the file and close gedit. Then from Terminal:

```
$ sudo update-grub
```

If editing the file is difficult for you then install and use [Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183") as suggested in the earlier post. However, personally, I would discourage you to do so.

For more info on Dual-Booting **[Read Here]("http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/")**.

I hope I was clear.

---

### Post by jammedubu on 2013-03-16
> **fantab said:**
> I am assuming that you only have one HDD on your machine. When you install Ubuntu you have to install Grub, otherwise you cant boot into Ubuntu. And when Grub is installed it WILL overwrite Windows Boot Loader. (AFAIK Windows Boot Loader does not recoginize Linux OS and will not boot it, on the other hand Grub will flawlessly boot Windows).

Now to answer your original question:


Grub, by default, will boot Ubuntu. However, you can easily change your default OS to boot. To do this you have to edit /etc/default/grub and change the default OS.

After Installing Ubuntu do this from Ubuntu - Terminal:

```
$ gksu gedit /etc/default/grub
```

... and edit the line GRUB_DEFAULT=0 to **GRUB_DEFAULT=x** (where "x" is the Windows' Grub menu entry Number. It will most likely be 2 or 3). You can change and verify what entry is selected at Grub-Menu by default and adjust accordingly.

After you have edited, save the file and close gedit. Then from Terminal:

```
$ sudo update-grub
```

If editing the file is difficult for you then install and use [Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183") as suggested in the earlier post. However, personally, I would discourage you to do so.

For more info on Dual-Booting **[Read Here]("http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/")**.

I hope I was clear.

You are a true hero. To install Ubuntu next to Windows I just create a new partition with a swap and linux file system which I create during installation?

Edit: I see it's in the last link. Thanks !

---

### Post by fantab on 2013-03-16
There is plenty of information available on dual booting Windows and Ubuntu on www. Just google for it and read until you are satisfied. 

Good Luck....

---

### Post by verymadpip on 2013-03-16
Hi there.
[I]Please do not shrink your Windows partition with anything other than the Windows disk management tool.
[/I] You risk ruining your Windows installation by doing so.

Personally, I'd also defrag Windows a time or two before proceeding. I also suggest making backups of anything important to be on the safe side.
Good luck - it'll be fine :D

---

### Post by orb9220 on 2013-03-16
The way I approached dual booting. I didn't want the mbr touched at all. So made sure during the install that the grub installed where / root is. In my case sda5 was root / so had the installer install grub there also. Then using free program EasyBCD on my windows 7 just add the linux to my mbr menu on startup. Adjust time to 3 seconds for booting and assign default OS on boot.

Know as chain loading you end up with two boot menus during the process and that is fine with me. 
I prefer this method as if my grub gets trashed still have a bootable machine.
.

---

### Post by jammedubu on 2013-03-16
And how did you do that ?

---

### Post by orb9220 on 2013-03-16
LiveCD choose Install during install dialog where to install choose something else.
Select your unused partitions for / and make a swap partiton. 
At bottom shows where to install grub default is always first partition sda1.
Change it to match root partition.

Boot up into windows and find download program easyBCD install it and run it and add linux grub to the entry and save.
.

---

### Post by fantab on 2013-03-17
> **verymadpip said:**
> Personally, I'd also defrag Windows a time or two before proceeding. I also suggest making backups of anything important to be on the safe side.

Running "Disk Defragmentation" from Windows on your HDD before you begin partitioning is a very good idea.

---

### Post by squakie on 2013-03-17
A couple of notes here:

[LIST]
[*]as mentioned DO RUN the Windows defrag of the disk - twice would be best
[*]AFTER the defrag, THEN run the Windows disk management to shrink the partition to make room for Linux
[*]if this is a Windows 8 system, or if you have an EFI enabled BIOS, you will want to search the forums for information regarding UEFI enabled PC's and dual-boot.  There is quite a bit of information you should read first, as the installation is different.  If by chance it is a laptop with UEFI and Windows 8 came preinstalled, please do not attempt installation before posting here first.  There is a certain brand of laptop that can actually be bricked by attempting this.  I just went through this process on a new laptop and had a lot of interaction with user "oldfred" who got me around my problems.  I would seriously scan for his posts if this applies to you.
[/LIST]

---

### Post by Mark Phelps on 2013-03-17
If you're really intent on setting up a dual-boot system, then read through the details below BEFORE you do that ...

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by jammedubu on 2013-03-23
I did run partitioning tools, but found out why I could not shrink the hard drive. The hibernation file was placed at the end of the hard drive's memory. Deleting that made partitioning a breeze. I'd recommend it to anyone.

---

