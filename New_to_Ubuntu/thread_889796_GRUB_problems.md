---
title: "GRUB problems"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by marufaberlin on 2008-08-14
Hi,

got a little problem with GRUB, suppose this speaks for itself:

```

# grub-install /dev/sda
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.

```

Any Ideas?

thanx in advance,

marufaberlin

---

### Post by LowSky on 2008-08-14
I can read, but It doesn't speak to me. What are you trying to do, add another OS to grub?

EDIT: [http://www.newlinuxuser.com/adding-other-operating-systems-to-grub/](http://www.newlinuxuser.com/adding-other-operating-systems-to-grub/)

---

### Post by marufaberlin on 2008-08-14
no, re-install grub.

---

### Post by logos34 on 2008-08-14
try this:
> 
Just remove the corrupted files and replacing them with new ones. 
                                       First, save your menu.lst (or grub.conf), to your /home/username folder to get it in a safe place until you are ready to restore it again.  Then remove all those bad files in /boot/grub. Copy back your menu.lst, and reinstall [COLOR=#000000]GRUB[/COLOR]. Here are the commands,
                                       Code:
                                                                                                                                                                           sudo cp /boot/grub/menu.lst .
                                       sudo rm /boot/grub/*
                                       sudo cp menu.lst /boot/grub
                                       sudo grub-install /dev/sda

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)


---

### Post by marufaberlin on 2008-08-14
gives me the same result.

---

### Post by marufaberlin on 2008-08-15
nobody answering?

---

### Post by LowSky on 2008-08-15
[http://www.supergrubdisk.org/index.php](http://www.supergrubdisk.org/index.php)

---

### Post by marufaberlin on 2008-08-15
and what do I do with it?

---

### Post by Sorivenul on 2008-08-15
See [HERE]("http://ubuntuforums.org/showthread.php?t=224351") if you still have your LiveCD.  I've never had this fail, and if the first set of directions don't work, the second set involving the chroot are great as well.  Good luck.

---

### Post by kansasnoob on 2008-08-15
There are a number of ways to reinstall Grub. My preferred method is using the Hardy Alternate Install CD, just because that's what I'm used to:

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

But you can also use the Super Grub Disc:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Use_Super_Grub_Disk)

Or the Ubuntu Live CD:

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

---

### Post by MarkieB on 2008-08-15
no longer participating in ubuntuforums.org

---

### Post by marufaberlin on 2008-08-16
@ sorvenul: Thanks for that link, I do not have the CD anymore, but thanks anyway.
@ kansasnoob: I think the Supergrub method is best for me, so thanks for that link.
@ MarkieB: Yes, I tried that, but it only updates the menu.lst file.

---

### Post by adieb on 2008-08-16
> Yes, I tried that, but it only updates the menu.lst file.
Are you sure?? Actually it should update your master-boot-record with the things, that are written in your menu.lst

At least, I thought it´s like that; I use to do it that way

---

### Post by caljohnsmith on 2008-08-16
> **adieb said:**
> Are you sure?? Actually it should update your master-boot-record with the things, that are written in your menu.lst

At least, I thought it´s like that; I use to do it that way
Actually, all update-grub does is attempt to update your /boot/grub/menu.lst, or it will create a new one if it doesn't exist. It doesn't update the MBR. From the update-grub man page:
> [COLOR="Blue"]update-grub is a program used to generate the menu.lst file used by the grub bootloader[/COLOR].  It works by looking in  /boot  for  all  files  which start  with  "vmlinuz-". They will be treated as kernels, and grub menu entries will be created for each.  It  will  also  create  the  initial menu.lst  if  none  exists, after prompting the user.  It will also add initrd lines for ramdisk images found with the same version as  kernels found.  e.g.  /boot/vmlinuz-2.4.5  and  /boot/initrd-2.4.5 will cause a line of "initrd=/boot/initrd-2.4.5 or similar to be added for the  kernel entry in the menu.lst.

Marufaberlin, how about reinstalling Grub? That might solve the problem. Try the following:
```
sudo apt-get purge grub
sudo apt-get install grub
cp /boot/grub/menu.lst ~/Desktop/.
sudo rm -f /boot/grub/*
cd ~/Desktop
sudo cp menu.lst /boot/grub/.
sudo grub-install /dev/sda

```
If that doesn't work, please copy/paste the exact results you get for all commands from your terminal so we can see what happened.

---

### Post by marufaberlin on 2008-08-26
no, it doesnt.

I tried the supergrub cd, but sadly it gets some settings screwed, it set a root device of (hd0,4) instead of (hd0,5) which it detects and boots correctly.

Still looking for suggestions,

thx in advance,

marufaberlin

---

