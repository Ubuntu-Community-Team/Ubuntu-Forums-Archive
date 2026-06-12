---
title: "grub rescue question"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by MickeyPilgrim on 2012-04-27
I dual boot with XP. My Ubuntu partition had failed installs of 10.04 and 11.04, so for a clean install, I used Gparted to clear everything that wasn't on the sad1 partition - let me rephrase that- I deleated sda 4 5 6 7 8, and now have a untouched sda1 with XP and an empty sda2.
 When I rebooted there was no option of going into XP, just a message to do a grub rescue. But I am now downloading 12.04. Won't installing 12.04 install everything I need in the cleaned out partition sda2?

---

### Post by carl4926 on 2012-04-27
Because you deleted the partitions, you deleted part of grub you needed.

Assuming you can create a boot cd OK
Use it and install Ubuntu to sda2, yes.

FYI: Supergrubdisk should be able to boot windows in your current situation

---

### Post by garvinrick4 on 2012-04-27
Grub is installed in first few sectors of drive and then looks for boot files in your file system in partition used
to install grub into said first few sectors (mbr). 
Since you had no install in partition with boot files you cannot boot into anything. Still have Grub in those first few sectors just need to reinstall with active partition. Will accomplish when you install new Operating system of Ubuntu. 

With Windows XP cd can install windows boot files with link below.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 

Here is link for installing grub2 (grub-pc) when and if you need to from Live CD (ubuntu install CD using Try Ubuntu)
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

Many ways nowadays to fix grub with GUI apps if more comfortable with just google will find links.

---

