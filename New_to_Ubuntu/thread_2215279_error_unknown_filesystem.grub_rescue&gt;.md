---
title: "error: unknown filesystem.grub rescue&gt;"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by Dawrees on 2014-04-05
I installed Ubuntu over XP and deleted the partition ..so only Ubuntu was my OS.  I don't have a network connection at this time and working with wireless only...
Anyways...after installing Ubuntu I have no wireless...looks good but wireless option is shaded...
I have Ubuntu recovery DVD. 
So now I figured maybe I should put windows XP back so I did recovery and it said recovery complete restart your computer..so After I restart I get the message...error: unknown filesystem.grub rescue message..
If I can get either of the issues fixed whichever is easier...but at this moment windows is on just can't get to it..Any support would be greatly appreciated...I am new to Ubuntu but wouldn't mind having dual boot..thank in advance..

---

### Post by oldfred on 2014-04-05
To boot Windows you need a Windows boot loader in the MBR, assuming the rest of Windows is correct.
From a Windows repairCD or install DVD you can run fixMBR command.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Or you can just run Boot-Repair. It cannot make major fixes to Windows but can add a Windows type boot loader to the MBR to boot Windows.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Grub just has a boot loader in the MBR and need the rest of grub that is in Linux partition to boot.
Ubuntu really installs much better with a wired network connection. Not all wireless drivers are on install DVD, and you may have to download wireless driver.

---

