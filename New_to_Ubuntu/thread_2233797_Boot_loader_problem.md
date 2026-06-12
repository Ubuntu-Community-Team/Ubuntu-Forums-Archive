---
title: "Boot loader problem"
date: 2014-07-10
forum: New to Ubuntu
---

### Post by Neil_Walker on 2014-07-10
Hi I am a complete noob to linux so please be gentle!

I am having problems booting to Windows after trying to dual boot. My windows recovery is on sda1 but I cannot boot in to this and windows fails to start as possibly the sda is visable?

I have used Boot Repair without success. The generated URL is [http://paste2.org/zgJ9HaZy](http://paste2.org/zgJ9HaZy)

Any help would be gratefully recieved.

---

### Post by oldfred on 2014-07-11
Have you tried directly booting Windows from UEFI menu.

It looks like you have used grub customizer as all the scripts with proxy in the name are the revised grub scripts from grub customizer. 
But it has creates BIOS type boot entries that will not work with UEFI. You have to chain to the efi partition not to each install.

And you have a grub installed in the MBR. Is that from Mint installed in BIOS mode?

And the boot files for recovery are in sda3 which are efi based. There are two recovery partitions. One is Windows recovery or repair and the other is the vendor recovery which is an image of hard drive as purchased. 
Best to always fully backup efi partition(s) and Windows main install.

You cannot dual boot from grub menu unless systems are installed in same boot mode, either UEFI or BIOS. Only from UEFI menu can you choose systems not installed in the same boot mode. And some require you to turn on or off the UEFI or BIOS/CSM flag in UEFI to correctly boot. Others do auto switch or have a UEFI and BIOS option.

If thinking of reinstalling anything, please back up and read the very important message in my link below.

---

### Post by Neil_Walker on 2014-07-11
How do i directly boot windows from uefi?

---

### Post by Neil_Walker on 2014-07-11
I think I've tried launching Windows from UEFI. But only get an error saying windows failed to start. 

File \BCD 
Status Oxc0000098 
Info: Boot configuration data file doesn't contain valid information for an operation system

---

### Post by oldfred on 2014-07-11
Did you boot with UEFI on and either with or without secure boot on?

Did you change BCD? That cannot be fixed from Linux.

You may do better on fixing Windows from a Windows site.
       [http://www.eightforums.com/](http://www.eightforums.com/)

If you can get to repair console (f8) or made the Windows repair CD or flash drive you can run this:

 BootRec.exe /RebuildBcd

      
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by Neil_Walker on 2014-07-15
Thanks for all the help. I ended up downloading a paid for recovery disk which repaired the windows Boot loader.

---

