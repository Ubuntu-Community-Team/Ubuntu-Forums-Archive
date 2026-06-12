---
title: "Dual Boot Windows 8 and Ubuntu: help for partitioning"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by federicodemaria on 2013-10-18
I've just bought a Lenovo B590 (Core i3 2348M; RAM 4BG; 500 GB hard disk; HD3000; 15.6"/W8) which supposedly is certified for Ubuntu. 
[http://www.ubuntu.com/certification/.../201208-11535/](http://www.ubuntu.com/certification/.../201208-11535/)

I first had a problem (laptop was not loading Ubuntu from CD) but I've now solved it. 
[http://ubuntuforums.org/showthread.php?t=2181292&p=12819476#post12819476](http://ubuntuforums.org/showthread.php?t=2181292&p=12819476#post12819476)

I've tried it and it seems to work fine. So I now would like to install it. I've done it other times, but I wanna ask advice for manual partitioning. 
I know I can do it with partition magic, GParted or during the installation process (less advisable, I understand). 

I always use Ubuntu, but very rarely also access to Windows to run some programs i can't have on Ubuntu. 
I would like a good partition for Windows, an excellent one for Ubuntu and then probably a shared one for data (NTFS?)
What partitioning would you suggest?  
I propose one below from what I've learned online (I paste here the two links), but please adive me as I don't really understand the technicalities. 
[http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

Tot 500 gb 

Windows 8 system partition - 1GB (sda1)
Extended partition - 99GB (sda2)
Windows partition (Windows files) - 20GB (sda5)
Windows data partition (user files) - 60GB (sda6); you can share it in Linux
Linux root - 10GB (sda7)
Linux swap - RAM size, 4GB (sda8)
Linux home - remaining space, 300 GB (sda9)


Thank you very much 

Best, 
f

---

### Post by westie457 on 2013-10-18
Hello federicodemaria
Out of the links you posted use the second one for guidance. It is IMHO it is the better one. You might also want to look at this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
If the HDD has a GPT partition table you will not need to create an extended partition for Ubuntu.

To check which you have run ```
sudo fdisk -l
``` in a terminal.
The l is a lower-case L.

---

### Post by fantab on 2013-10-18
When managing Windows Partitions ALWAYS use Windows Tools and only Linux tools for managing Linux Partitions.

Lets see how you have your existing partitions... Boot with Ubuntu DVD/USB, "Try ubuntu without installing", open Terminal [Ctrl+Alt+T], type the following command and Post its output here:

```
sudo parted -l
```

---

### Post by spiral2 on 2013-10-18
I am new to ubuntu, and computers generally, before I installed ubuntu form a disc, I went into windows & reduced the size it occupies on the HDD (restart it a few times before doing any thing else) then I went into bios F2 and changed it to boot from CD / DVD.

Then I restarted it with the ubuntu DVD in and it installed perfectly into the space left by the reduced windows.

---

### Post by fantab on 2013-10-18
@spiral2: Its all good if you are satisfied... Glad you successfully installed Ubuntu.

However, to want more control over your partioning and Install the Manual ('Something Else') option is recommended.

---

### Post by adnan_amin on 2013-10-18
Hi,
Your statement "[COLOR=#000000]I always use Ubuntu, but very rarely also access to Windows to run some programs i can't have on Ubuntu. "[/COLOR]
Other friends already adviced you different methods but i would say if you wanna windows only for few programs so first try to run these programs using wine 1.7. if could work fine so i think there is no need of dual operating system. if you can compromise on a little bit slowness then create virtual machine with windows operating system as guest on  host ubuntu for running your required programs.

---

### Post by federicodemaria on 2013-10-19
This is the current partition

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA HGST HTS545050A7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs                                       hidden, diag
 2      1050MB  1322MB  273MB   fat32        EFI system partition          boot
 3      1322MB  1456MB  134MB                Microsoft reserved partition  msftres
 4      1456MB  487GB   485GB   ntfs         Basic data partition          msftdata
 5      487GB   500GB   13.5GB  ntfs                                       hidden, diag


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

> **adnan_amin said:**
> Hi,
Your statement "[COLOR=#000000]I always use Ubuntu, but very rarely also access to Windows to run some programs i can't have on Ubuntu. "[/COLOR]
Other friends already adviced you different methods but i would say if you wanna windows only for few programs so first try to run these programs using wine 1.7. if could work fine so i think there is no need of dual operating system. if you can compromise on a little bit slowness then create virtual machine with windows operating system as guest on  host ubuntu for running your required programs.

I had tried before the virtual machine (wine 1.7) to run Office, which is the only Windows program I sometimes need to work, but I have always failed. 
I now have Ubuntu 11.04. 

jhonny@jhonny-DELL:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

> **westie457 said:**
> Hello federicodemaria
Out of the links you posted use the second one for guidance. It is IMHO it is the better one. You might also want to look at this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
If the HDD has a GPT partition table you will not need to create an extended partition for Ubuntu.

To check which you have run ```
sudo fdisk -l
``` in a terminal.
The l is a lower-case L.

Thanks. Here is what I get, not sure what it means. 

ubuntu@ubuntu:~$ sudo fdisk -l 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted. 


Disk /dev/sda: 500.1 GB, 500107862016 bytes 
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0xb0dcdfdd 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1  4294967295  2147483647+  ee  GPT 
Partition 1 does not start on physical sector boundary. 
ubuntu@ubuntu:~$

---

### Post by fantab on 2013-10-19
Your HDD has GUID Partition Table [GPT], with GPT you don't need any Extended Partition. You can have more than 100 Primary partitions. Extended Partition is used with 'DOS Partition Table' which has only 4 Primary Partition Limit.    

Your Windows Boots with UEFI/EFI. Which means you'll have to install Ubuntu in EFI mode only. To do this you'll have to boot your Ubuntu DVD/USB in EFI mode; from the boot menu you will get the choice to boot in either PMAP or EFI when using USB. You MUST boot in EFI mode only. 
If you successfully boot your Ubuntu in EFI mode then you will get a black screen with options, if not then you will see a regular ubuntu colors. Read  [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)    

But first you will have to SHRINK one of your Windows Partitions to create Space for Ubuntu, after Shrinking leave the space as 'unallocated', don't create partitions with Windows. Read  [http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/](http://www.tweakhound.com/2013/01/02/how-to-resize-your-windows-8-partition/)    

During Ubuntu installation you can create partitons manually using Gparted. If you use Gparted to create partitions for Ubuntu then during install choose "SOMETHING ELSE' option at 'installation Type' dialog.  If NOT then just tell the installer to use the Unallocated Space and install alongside windows. 

 After installing Ubuntu if your computer boots to Windows8 then you will need BOOT-REPAIR utility... 'Recommended Repair' is all you need.  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)    

Clear all your Doubts before you actually install.

---

### Post by Mark Phelps on 2013-10-19
Wine doesn't run MS Office very well.  An older version of Office (2010) can be tweaked with considerable effort to run Word and Excel OK, but the other Office components won't work well or at all.  Office 2013 does not run in Wine.

To use Office regularly, you're better off keeping Windows around.

---

### Post by adnan_amin on 2013-10-20
Using wine 1.7, office 2013 will not work and i hope very soon the developers will resolve this issue as well but office 2010 is absolutely work. i will suggest you that install virtualbox (open source free) and install windows whenever a program you need which work on windows so use virtualbox. in this case host operating system will be ubuntu and windows will be consider guest or just service. if you need steps i can share with you. during creating virtual machine, choose dynamic partition size that means "how much space you will utilize that much will be occupy only" if you will create dual book so it will take fix size of partition and you cannot easily switch from running one operating system to another while in virtual machine you will be able to do that.

---

