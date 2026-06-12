---
title: "Dual Boot Problem"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-23
Currently, there is XP and Ubuntu installed on my wife's computer. Now she supposed to upgrade XP to Seven. How can it be done?
Just install Seven over XP or what?
Thank you.

PS:
In the most articles all over the web, I read Windows should be installed first. Before Ubuntu.

---

### Post by unibroker on 2012-06-23
I have read that as well.  I had Win XP on my desktop first and then added Ubuntu afterwards and have had no problems.  I would perform all of my Windows operations first.

---

### Post by Frogs Hair on 2012-06-23
There may be boot loader issues and you can find help here if need be .

---

### Post by anewguy on 2012-06-23
I'm not sure how Windows 7 works, but I think you should be able to leave Ubuntu there.  Here's is what will happen, and there are EASY fixes after you've done it, so we can go from there:

The master boot record currently points to the Ubuntu partition (assuming, of course, your Ubuntu isn't a wubi install) in order to find the grub menu, etc..  When you install Windows after Ubuntu, Windows will overwrite the mbr so that it is pointing to Windows - no Ubuntu will show.  BUT, this isn't that big of deal - after you done that, we can walk you through the simple process of updating grub so the it is back in the mbr.

Your other choice, of course, is to blow everything away.  You'll need to watch partitioning:  if you, for example, let Windows 7 (and this what I'm not sure of) take the entire disk, Windows 7's disk management MUST be used to repartition the disk, and you want to be sure they are not created as dynamic partitions.

---

### Post by oldfred on 2012-06-23
Windows on a bare drive uses two partitions, one a hidden 100MB boot/repair and the other the main install. But it also overinstalls to a NTFS formated partition with the boot flag (active partition in Windows). Then it will only use one partition. The separate was supposed if you wanted to encrypt the main install as the boot/repair partition could not be encrypted.

So it should just install, will overwrite the MBR as mentioned above and you will have to use your Ubuntu liveCD or USB to reinstall grub2's boot loader. With the new Ubuntu & grub you need to use the same version to reinstall. So if you have upgraded in place be sure to download a new liveCD first.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If you prefer a gui to reinstall grub2 to the MBR:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

