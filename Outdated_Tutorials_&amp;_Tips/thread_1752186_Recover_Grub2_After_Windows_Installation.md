---
title: "Recover Grub2 After Windows Installation"
date: 2011-05-07
forum: Outdated Tutorials &amp; Tips
---

### Post by ubume2 on 2011-05-07
I use this guide frequently for my multiple boot system when I have installed a new Linux Distro on my drive, but want to keep or change the grub boot menu on a different partition.

I downloaded this piece from a web site that no longer exists, and use it repeatedly.  It is thorough for the purpose it was intended, but simple.  It is an excellent piece and deserves preserving. Very useful for beginners like me. It works in Ubuntu installations up to 11.10. ** Edit: 12.04 LTS seems to require an additional cli entry mentioned in the edit section below, dated 4/27/12.**
 
This procedure can  also be done without CD if you have a different Ubuntu or Linux version on another partition on the same HD. It can also be used with a USB flash drive. 

Original source: formerly **[http://www.ubuntu-inside.me/2009/06/...r-windows.html](http://www.ubuntu-inside.me/2009/06/...r-windows.html)** by binbash.


At the end of this post are urls to complete guides to grub recovery and customizations.


> Howto Recover Grub2 After Windows Installation
Posted by Binbash on Jun 21, 2009
Labels: grub2, Howto, jackalope, jaunty, karmic, koala, linux, recover, ubuntu, windows

Today i destroyed my Grub2 via installing windows on my notebook which i write blog posts.(I quit smoking , so i have to play some games : ) No rush). It may be hard to recover it since there are not much (i did not find anything) howtos around the net about recovering Grub2.Here is the step by step guide to recover it :

You will need a LIVE cd if you are going to recover an Ubuntu Box.Download Ubuntu Jaunty, Karmic whatever you want.Open the system with Live CD (I assume you are using Ubuntu Live CD).Press Alt+F2 and enter gnome-terminal command.And continue by entering :

$sudo fdisk -l

This will show your partition table.Here is my table to understand it better :

/dev/sda1 29 8369 66999082+ 83 Linux
/dev/sda2 * 8370 13995 45190845 7 HPFS/NTFS
/dev/sda3 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris

Now i will mount Linux (sda1 here), i have no external boot partition as you can see.(IF YOU HAVE external one, do not forget to mount it! )

$sudo mount /dev/sda1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc

The following command is optional (it copies resolv.conf)

$sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

Now chroot into the enviroment we made :

sudo chroot /mnt

After chrooting, you do not need to add sudo before your commands because from now, you will run commands as root.

You may want to edit /etc/default/grub file to fit your system (timeout options etc)

#nano -w /etc/default/grub

Play with the options if you want.(But do not forget to give grub-update command if you saved it ;) )

Now install/recover Grub2 via :

#grub-install /dev/sda

command.However you may get errors with that code like me.If so please use this command :

#grub-install --recheck /dev/sda
#update-grub

Now you can exit the chroot, umount the system and reboot your box :

#exit

$sudo umount /mnt/dev
$sudo umount /mnt/proc
$sudo umount /mnt
$sudo reboot

**Edit: 4/27/12 Beginning with 12.04LTS** this procedure now requires a mount of the /sys.


So the order would be:
```

$sudo mount /dev/sda1 /mnt
$sudo mount --bind /dev /mnt/dev
$sudo mount --bind /proc /mnt/proc
$sudo mount --bind /sys  /mnt/sys

```

then:
```

$sudo chroot /mnt
#grub-install /dev/sda
#update-grub
#exit

```

Then unmount:
```

$sudo umount /mnt/sys
$sudo umount /mnt/proc
$sudo umount /mnt/dev
$sudo umount /mnt

$sudo reboot

```




For detailed explanation of grub, see:
**Purge and Reinstall grub2** [ubuntuforums.org/showthread.php?t=1581099](ubuntuforums.org/showthread.php?t=1581099)

**How to Tweak/Customize Grub2** [http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

---

