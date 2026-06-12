---
title: "Cannot dual boot win8 and Ubuntu. Sony VAIO SVE1513M1EW e series. UEFI Secure Boot."
date: 2013-06-03
forum: New to Ubuntu
---

### Post by scrypt on 2013-06-03
hello folks.

im having a bit of nightmare atm.

I cannot for the life of me seem to be able to get Windows 8 and Ubuntu 12.04 to play well together, and its not from lack of trying.
I bought a sony VAIO Model Name: SVE1513M1EW e series laptop a short while back
and i'm trying to get windows 8 and ubuntu 12.04 to dual boot. but i'm not able to do it.

When I boot up using my ubuntu 12.04 usb, ubuntu recognises my newly created 100GB partition,
but it wont let me easily install ubuntu next to windows 8. The only way it seems I can install ubuntu is to choose the something else option,  and I then would have to create my own ubuntu partitions. I must admit i'm a bit daunted by this because I do not want to loose windows 8 after making any mistakes.

My BIOS firmware is UEFI although can choose legacy boot, but win 8 will not boot this way. I also have secure boot enabled. Am I right in thinking that this is okay?. I thought Conical paid microsofts ransom. So that ubuntu can now be installed alongside windows 8 UEFI secure boot. and I will be able to install ubuntu along side win 8 with these options enabled. To dual boot successfully this way. or not ?

I would appreciate some help on this.  
If anybody could tell me in layman's terms how I can successfully dual boot win8 and ubuntu without messing up my existing win8 installation.
That would be massively appreciated!

I know there are similar posts on this forum about similar issues, but i don't understand them. I'm hoping someone could explain it to a still relative newbie to ubuntu.

i look forward to any help.

---

### Post by fantab on 2013-06-03
> **scrypt said:**
> ...
When I boot up using my ubuntu 12.04 usb, ubuntu recognises my newly created 100GB partition,
but it wont let me easily install ubuntu next to windows 8. The only way it seems I can install ubuntu is to choose the something else option,  and I then would have to create my own ubuntu partitions. I must admit i'm a bit daunted by this because I do not want to loose windows 8 after making any mistakes.

My BIOS firmware is UEFI although can choose legacy boot, but win 8 will not boot this way. I also have secure boot enabled. Am I right in thinking that this is okay?. I thought Conical paid microsofts ransom. So that ubuntu can now be installed alongside windows 8 UEFI secure boot. and I will be able to install ubuntu along side win 8 with these options enabled. To dual boot successfully this way. or not ?

...

How did you create 100GB Partition? Did you use Windows tool or did you use Gparted? How is it formatted, NTFS or Ext4? Post the output of:
```
sudo parted -l
```
after booting from Ubuntu LiveUSB and "Try Ubuntu".

If an OS is installed in UEFI/EFI mode then it will only boot in that mode. When dual booting if one OS is already installed in UEFI mode then then other OS HAS to be installed in UEFI mode.
Yes since Ubuntu version 12.04.2 we can install Ubuntu alongside Windows8 with secure boot 'enabled'. However, you MUST [disable 'fast Startup']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"), and you must also disable Fast Boot/Quick Boot from UEFI/BIOS setup. Also look in UEFI/BIOS if you have something called 'Intel SRT', you have to disable it as well to dual boot.

---

### Post by Eersfanpilot on 2013-06-04
I had similar problems using a LiveUSB trying to install anything Linux dual boot with Windows 8. I changed over to a bootable DVD and have not had any issues getting them to install. On my machine (Lenovo Z585) I have Windows 8 with Ubuntu 13.04 dual boot and EFI still enabled.

---

### Post by scrypt on 2013-06-04
hello thanks for your replies...

fantab... 
i created the 100GB partition using EaseUS partition manager. it is marked as Unallocated.
this is the way i created the partition i am going to install ubuntu on every time i have dual booted win and ubuntu in the past.
thanks for your clear advice i will check those options in my BIOS right away.

I will live boot into ubuntu and post the

 sudo parted -l

output here ::

---

### Post by scrypt on 2013-06-28
Hello guys

Apologies for my delay in replying to my thread.
I'm back able to continue to try to successfully dual boot windows 8 and Ubuntu 13.04.
I'm also pretty sure im gonna need some more help so ill spark up my Ubuntu 13.04 Live DVD and post back here if i need any assistance.

Cheers for now

---

### Post by scrypt on 2013-06-28
Im on Ubuntu 13.04 Live DVD atm

im about to once again try to install ubuntu alongside win8. secure boot is enabled and my bos is UEFI.
Ubuntu is also 64bit!

Here is my sudo parted -l output ::

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  316MB  315MB  ntfs         Basi  hidden
 2      316MB   420MB  105MB  fat32        EFI   boot
 3      420MB   555MB  134MB               Micr  msftres
 4      555MB   806GB  805GB  ntfs


Model: Kingston DataTraveler SE9 (scsi)
Disk /dev/sdb: 7803MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7799MB  7798MB  primary  fat32        boot
=====================================================


Im also using this site as a guide :

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Acording to it  my HDD is GPT.
and I need to create an extra BIOS boot partition. 
So in total i need 3 Partitions, is this correct?
should it be simular to this:


BIOS-boot or EFI partiton (parition 1)
	
swap partition : size of RAM (partition 2)

/   partition: the rest of the disk (partition 3) 

Should i create a BIOS Boot or an EFI partition ??
and what isze should this partitoin be ?

I must admitim concerned about wrecking my existing windows instalation. id like to get this preceedure correct as possible
hence all my questions.

i look forward to any replies.

what size I crete the BIOS of EFI partition

---

### Post by oldfred on 2013-06-28
If booting in UEFI mode, you do not need bios_grub partition, that is only for BIOS/CSM/Legacy boot. And if you install Ubuntu in BIOS mode it is difficult but not impossible to dual boot. You have to go into UEFI/BIOS and turn UEFI on to boot Window and go into UEFI/BIOS and turn on CSM to boot Ubuntu. When CSM is on, secure boot is off.
 Compatibility Support Module (CSM), which emulates a BIOS mode 

Does your Windows boot with secure boot off, but still in UEFI mode. Some will boot with secure boot off, others only boot with it on. But Microsoft does specify that a user can turn secure boot off, but does not seem to specify whether Windows will still work. Some vendors are better than others.

Ubuntu will work in 3 different modes, UEFI, UEFI with secure boot, and BIOS mode. How you boot install media is how it installs, but some systems will not boot flash drive or DVD in secure boot mode. And a few will only let you boot in BIOS mode. If you have to install in BIOS mode, Boot-Repair will convert to UEFI or convert to UEFI with secure boot and signed kernels. 

Users with Sony have installed, but some have even manually moved files around. I generally suggest Boot-Repair as it also does backups.

 Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
 Sony SVE15125CXS Notebook  Only could Install in BIOS mode, Boot-Repair to UEFI dual boot works
[http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570](http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony - Manually copied but still some issues.
[http://ubuntuforums.org/showthread.php?t=2093415](http://ubuntuforums.org/showthread.php?t=2093415)
EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 on Sony Vaio S dual SSD
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)
Sony VAIO with Insyde H2O EFI bios Ubuntu 12.04 Dual Boot 
[http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html](http://www.linuxrelease.com/2012/07/sony-vaio-with-insyde-h2o-efi-bios.html)
sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time installed 12.10, then  booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

---

