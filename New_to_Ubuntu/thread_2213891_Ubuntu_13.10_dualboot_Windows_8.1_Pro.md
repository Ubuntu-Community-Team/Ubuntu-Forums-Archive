---
title: "Ubuntu 13.10 dualboot Windows 8.1 Pro"
date: 2014-03-29
forum: New to Ubuntu
---

### Post by Delta_Unit_117 on 2014-03-29
Hello

So, I would like to install Ubuntu 13.10 on my computer, but I am confused how I should install it. I have a ASUS B85M-G motherboard, which has UEFI. I have tried to find for the exact correct methode how you have to install it, but I don't know which methode I have to choose.
Note: Windows 8.1 Pro hasn't been preinstalled on my system. My computer is a custom build one. 

PS: Is the Nvidia GeForce GT 640 supported on Ubuntu ?

Thanks already for respoding and helping :D
**Delta Unit 117**

---

### Post by Lancro on 2014-03-29
I have windows 8.1 pro, ubuntu 13.10 and centos 6.5, and they boot perfectly, but you have to know how to install it.

In the partitioning menu of the installation of ubuntu you have to choose the last option, "more options" I think its in english (im a spanish user), first you will need unallocated space, do it shrinking your windows partition, you can do that from windows, or, executing gparted in the live usb choosing try ubuntu without installing, its safest in windows, because windows will never delete itself.

Once you hace unallocated space, you have to asign it, you click on create and you create a partition of about 10 GB ext4 with mount point "/", and the rest of the unallocated space you create an ext4 partition with mount point "/home", and then you continue with installation, be carefull not to delete the windows partition, the NTFS one, and thats it.

Grub will detect your windows installation at the end of the process, and at booting it will display a menu to let you choose between windows and ubuntu.

---

### Post by Delta_Unit_117 on 2014-03-29
Hi

Thanks for responding. I'll try this methode out as soon as possible.
By the way, is this the only way I have to do to install Ubuntu aside with Windows 8.1 without any issues ? Because I rather don't want to break my system already.

---

### Post by Vladlenin5000 on 2014-03-29
> **Delta_Unit_117 said:**
> By the way, is this the only way I have to do to install Ubuntu aside with Windows 8.1 without any issues ? Because I rather don't want to break my system already.

No. Actually there are a few bad advices in that post. 
First of all, DON'T use Linux tools to manage Windows partitions. Prepare your system for dual-boot by shrinking the Windows partitions (NTFS) with Windows 8.1 own partition tools, reboot and let it do the 'chkdsk' to correct logical errors and for safety do it one more time. Then - and only then - you can safely install Ubuntu in that new free space. The partitioning suggestion is very good but please understand you don't need a separated /home partition but it's advisable to do so - it'll keep your user settings and data if you later decide to reinstall Ubuntu.
The most important thing you should keep in mind - unfortunately not mentioned before - is that your system has uEFI, secure boot and stuff like that which is typical of new hardware made for/shipped with Windows 8 and later. Please read the following document at least TWICE from top to bottom and only proceed when you're sure you've understood what's in stake here and what you need to do in order to properly install Ubuntu in dual-boot and keep your Windows intact: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Delta_Unit_117 on 2014-03-29
> **Vladlenin5000 said:**
> 
The most important thing you should keep in mind - unfortunately not mentioned before - is that your system has uEFI, secure boot and stuff like that which is typical of new hardware made for/shipped with Windows 8 and later. Please read the following document at least TWICE from top to bottom and only proceed when you're sure you've understood what's in stake here and what you need to do in order to properly install Ubuntu in dual-boot and keep your Windows intact: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Hello

About the UEFI, my secure boot appeared to be disabled or something like that, and as I mentioned before, Windows 8 wasn't preinstalled on the computer. This is a custom build computer.

EDIT: I just realised my BIOS-Mode appeared to be 'old'. (According to the system information) And I discovered my OS is running on Legacy BIOS. This is confusing me, because I have a UEFI motherboard and I expected that my OS is running on UEFI. But I guess the installation is more simple now.

---

### Post by monkeybrain20122 on 2014-03-29
> **Delta_Unit_117 said:**
> Hello
I just realised my BIOS-Mode appeared to be 'old'. (According to the system information) And I discovered my OS is running on Legacy BIOS. This is confusing me, because I have a UEFI motherboard and I expected that my OS is running on UEFI. But I guess the installation is more simple now.

Well why do you want UEFI in the first place? To me it just makes my linux installs not portable and makes cloning partitions impossible, that sucks.  If you put win8 on yourself you can boot it in BIOS as you have found out.

---

### Post by Delta_Unit_117 on 2014-03-29
Well... I am not sure what you mean what you're saying, but I know that UEFI is better then the legacy at some point.

---

### Post by monkeybrain20122 on 2014-03-29
> **Delta_Unit_117 said:**
> Well... I am not sure what you mean what you're saying, but I know that UEFI is better then the legacy at some point.

Yeah I am curious to find out in what way it is better. So far from what I gathered it just makes things a lot less flexible, e.g gpt prevents cloning of partitions so you have to clone the whole drive with something like clonezilla instead. I would like to hear it from knowledgeable people.

---

### Post by Delta_Unit_117 on 2014-03-30
'bumping up thread'.

Well, I am still a bit confused and worried if I will do something wrong when installing Ubuntu. According on Windows, it says Secure boot is unsupported and that I am running on legacy. On my BIOS settings, it says that Secure boot is enabled.

---

### Post by oldfred on 2014-03-31
You cannot enable secure boot with BIOS, it is only an option with UEFI. And it is usually better not to use secure boot anyway. Grub also has a bug where it will not let you boot Windows 8.1 with secure boot on currently.

Current UEFI normally has CSM.
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
Eventually the new systems will eliminate the extra BIOS chip and then be Class 3 UEFI and only boot with UEFI.

Currently it is not critical whether you use BIOS or UEFI, but UEFI is the future. Some new hardware may not have BIOS drivers later. So if you add hardware later on, it may not work in BIOS in the future. Microsoft wanted vendors not to even write Windows 7 drivers for all new hardware, so users could not down grade, but most current systems seem to run Windows 7 just fine in BIOS or UEFI.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
And yes you cannot clone gpt partitions as they have internal data that must not be duplicated. But that really was true with MBR(msdos) partitions also. You had to change UUIDs to avoid issues. But you can easily use rsync to copy a gpt partition's data.

      
 Dual-Boot Windows 8 and Ubuntu 12.10 (BIOS)
[http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM)
Some info on UEFI:
Legacy BIOS and  UEFI AMI AptioMar 2012 -  20 MIn
[http://www.youtube.com/watch?v=dRMIvY7BiL4](http://www.youtube.com/watch?v=dRMIvY7BiL4)

---

### Post by monkeybrain20122 on 2014-03-31
> **oldfred said:**
> 
And yes you cannot clone gpt partitions as they have internal data that must not be duplicated. But that really was true with MBR(msdos) partitions also. You had to change UUIDs to avoid issues. But you can easily use rsync to copy a gpt partition's data.


Yes you can, I do it all the time with fsarchiver. You need to change uuid only if you try to boot the clone off the same computer where the original is still there. It is not hard to change uuid anyway, I have one setup like that, I have a clone of my running system in an external drive which I use as a portable, but I also boot it off the same machine for testing and updates. 

One nice thing about being able to do this instead of using clumsy tools like clonezilla to clone the whole drive is that I can easily repartition drive and then restore only partitions that are affected. Doing it this way I  can avoid slow and sometimes risky gparted operations like move/resize, just delete/reformat partitions then restore, a lot faster and safer.

Also I don't need to clone the /home partition  if I just want to guard against potential risky updates or installations (I backup data/files using other methods). The / partition is typically small and it takes maybe 5 minutes to clone and restore, but not the whole drive with a lot of data on it. For example I can keep changing and testing graphic drivers until I find a right one without having to go through perhaps hours or even days of messy trouble shootings and reinstallation.

rysnc doesn't do it as I am not interested in copying data, there are plenty of ways to copy data.

IMO none of the supposed advantages of gpt offsets this flexibility.

---

### Post by Delta_Unit_117 on 2014-03-31
I think I have the correct information now how I have to install Ubuntu properly. Only thing what I am still worried is that I will do something wrong, but I'll probably do it alright.

Thanks for the information and the help.

---

### Post by oldfred on 2014-03-31
@monkeybrain20122

You can copy gpt partitions, just cannot clone and keep on same drive. And you can clone entire drives, but cannot keep it in same computer unless you change GUIDs with sdgdisk:

[http://askubuntu.com/questions/57908/how-can-i-quickly-copy-a-gpt-partition-scheme-from-one-hard-drive-to-another](http://askubuntu.com/questions/57908/how-can-i-quickly-copy-a-gpt-partition-scheme-from-one-hard-drive-to-another)

If clone is really just a backup then their should be no issue restoring to same partition.
The main issue is using something like dd that does an exact image and does not change the internal GUIDs as well as UUIDs.

---

