---
title: "Help unable to access ubuntu files, boot-repair not working"
date: 2020-10-06
forum: New to Ubuntu
---

### Post by oneala on 2020-10-06
Starting a new thread, cause I feel this problem has not been addressed using techniques mentioned so far.

                        Hello,
 Disclaimer: I am really a novice when it comes to OS and programs, and software in general. My motivation for using Ubuntu is because of its ease of use, core principles, and my curiosity in general. Excuse me if I am not clear enough, and please feel free to correct, be blunt, and ask for clarification if I’m not clear enough
 
 
 PC system : Asus TUF GAMING (FX705DT-AU092T)
 OS: came preinstalled with Windows 10. I installed Ubuntu 20.04 in dual boot mode. The PC on starting boots into ubuntu (first option)
 
 
 Issue:  
 Incorrect system shutdown (my best guess).
 After which  a black screen with the following message appears:
 
 
 GNU GRUB 2
 minimal bash like line editing is supported. For the first word TAB lists possible command completions. Anywhere else, TAB lists possible device or file completions.
 
 
 > grub_
 
 
 on typing exit,  
 
 
 I boot into Windows.
 
 
 While in Windows,
 
 
 I have tried to access my linux files using WLS , but faced some difficulty in doing that, so I did not try it out fully.
 I saw some files present, that I was not authorized to open, so I chose not to do so.  
 
 
 **Accessing Ubuntu files from windows seemed risky and challenging so did not proceed.**

 
 
 Additionally, I saw a tutorial (link below), and followed the steps.
 [https://www.geeksforgeeks.org/how-to-fix-minimal-bash-like-line-editing-is-supported-grub-error-in-linux/](https://www.geeksforgeeks.org/how-to-fix-minimal-bash-like-line-editing-is-supported-grub-error-in-linux/)
 
 
 It didn’t work. After typing:  
 grub > normal_  
 
 
 nothing changed. I  still couldn’t access Linux OS, to update GRUB.
 
 
 
 
 2) Live Boot using Ubuntu
 I had the Ubuntu 20 iso on my windows partition, so I burned it onto a USB. Following the tutorial below:
 [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#4-boot-selection-and-partition-scheme](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#4-boot-selection-and-partition-scheme)
 
 
 Proceeded to live boot using USB.
 
 
                           Using the information on the link below,
 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
 
 
 Since I was unsure of the (START and END),
 
 
 I followed this tutorial ([https://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](https://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)). 
 Got the response below:
 --------------------------------------------------------------------------------------------------------------------------------------------------------------------------  

 ubuntu@ubuntu:~$ sudo /bin/bash
 root@ubuntu:/home/ubuntu# fdisk -l
 Disk /dev/loop0: 1.93 GiB, 2049204224 bytes, 4002352 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop1: 27.9 MiB, 28405760 bytes, 55480 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop2: 54.97 MiB, 57614336 bytes, 112528 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop3: 240.82 MiB, 252493824 bytes, 493152 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop4: 62.9 MiB, 65105920 bytes, 127160 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop5: 49.8 MiB, 52203520 bytes, 101960 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/nvme0n1: 476.96 GiB, 512110190592 bytes, 1000215216 sectors
 Disk model: INTEL SSDPEKNW512G8                      
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: gpt
 Disk identifier: 656736E6-5B64-4990-A27F-E384657634BC
 
 
 Device             Start        End   Sectors   Size Type
 /dev/nvme0n1p1      2048     534527    532480   260M EFI System
 /dev/nvme0n1p2    534528     567295     32768    16M Microsoft reserved
 /dev/nvme0n1p3    567296  499667598 499100303   238G Microsoft basic data
 /dev/nvme0n1p4 998473728 1000214527   1740800   850M Windows recovery environmen
 /dev/nvme0n1p5 499668992  998473727 498804736 237.9G Linux filesystem
 
 
 Partition table entries are not in disk order.
 
 
 
 
 Disk /dev/sda: 14.6 GiB, 15664676864 bytes, 30595072 sectors
 Disk model: Cruzer Blade     
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x0066d5ed
 
 
 Device     Boot Start      End  Sectors  Size Id Type
 /dev/sda1  *     2048 30595071 30593024 14.6G  c W95 FAT32 (LBA)
 root@ubuntu:/home/ubuntu# exit
 
 
 exit
 ubuntu@ubuntu:~$ sudo swapoff -a  
 ubuntu@ubuntu:~$ sudo parted /dev/nvme0n1p5
 GNU Parted 3.3
 Using /dev/nvme0n1p5
 Welcome to GNU Parted! Type 'help' to view a list of commands.
 (parted) help                                                              
   align-check TYPE N                       check partition N for TYPE(min|opt)
         alignment
   help [COMMAND]                           print general help, or help on
         COMMAND
   mklabel,mktable LABEL-TYPE               create a new disklabel (partition
         table)
   mkpart PART-TYPE [FS-TYPE] START END     make a partition
   name NUMBER NAME                         name partition NUMBER as NAME
   print [devices|free|list,all|NUMBER]     display the partition table,
         available devices, free space, all found partitions, or a particular
         partition
   quit                                     exit program
   rescue START END                         rescue a lost partition near START
         and END
   resizepart NUMBER END                    resize partition NUMBER
   rm NUMBER                                delete partition NUMBER
   select DEVICE                            choose the device to edit
   disk_set FLAG STATE                      change the FLAG on selected device
   disk_toggle [FLAG]                       toggle the state of FLAG on selected
         device
   set NUMBER FLAG STATE                    change the FLAG on partition NUMBER
   toggle [NUMBER [FLAG]]                   toggle the state of FLAG on partition
         NUMBER
   unit UNIT                                set the default unit to UNIT
   version                                  display the version number and
         copyright information of GNU Parted
 (parted) rescue 499668992  998473727                                       
 Error: /dev/nvme0n1p5: unrecognised disk label
 (parted) rescue 499668992  998473727 and END                               

 Error: /dev/nvme0n1p5: unrecognised disk label

 (parted)                                                                   
 --------------------------------------------------------------------------------------------------------------------------------------------------------------------------  

 [B]I also was unable to install testdisk, or Ddrescue, mentioned in [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[/B]

 
 tried mounting, as per this tutorial (with a minor variation, since I don’t know file type) [https://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](https://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/) 
 
 
 [https://www.thegeekstuff.com/2013/01/mount-umount-examples/](https://www.thegeekstuff.com/2013/01/mount-umount-examples/)

 
 
 [https://unix.stackexchange.com/questions/315063/mount-wrong-fs-type-bad-option-bad-superblock](https://unix.stackexchange.com/questions/315063/mount-wrong-fs-type-bad-option-bad-superblock)

 
**The above also did not work. I can send the terminal output if needed. I also ran fsck. the output is below.**


**--------------------------------------------------------------------------------------------------------------------------------------------------------------------------**                        

 root@ubuntu:~# fsck /dev/nvme0n1p5

 fsck from util-linux 2.34

 e2fsck 1.45.5 (07-Jan-2020)

 ext2fs_open2: Bad magic number in super-block

 fsck.ext2: Superblock invalid, trying backup blocks...
 Superblock has an invalid journal (inode 8).
 Clear<y>? cancelled!
 Journal superblock is corrupt.

 Fix<y>? cancelled!
 fsck.ext2: The journal superblock is corrupt while checking journal for /dev/nvme0n1p5

 e2fsck: Cannot proceed with file system check

 
 
 /dev/nvme0n1p5: ***** FILE SYSTEM WAS MODIFIED *****

 
 
 /dev/nvme0n1p5: ********** WARNING: Filesystem still has errors **********
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

  
(I chickened out, last minute).

Also tried boot repair, (I could not do the ‘recommended boot option’) 

 But when I did, The only option was to generate a report and write down a url which I did, but I am not even sure what to do with that. (I could not do the ‘recommended boot option’).  
 
 
 Any help on this matter will be really appreciated, I really want to :
 
 
 Recover as much as data possible.
 
 
 Format everything, and do a fresh install of Ubuntu, that is relatively noob proof, by some means of having regular backups. I heard that using a virtual machine also helps. I am trying to learn Python for data management, and have lot of dependencies to install, that I would rather prefer to have in a small ‘sub – environment’ if that makes sense.  
 
 
 Thank you for all the help!

---

### Post by ActionParsnip on 2020-10-06
Is the data backed up? If not, why not?

---

### Post by oneala on 2020-10-06
The backup I have is a month old (Before Installing Focal Fossa). I sadly do not have a backup of this week, which is most crucial. :( 
It is due to my utter stupidity, and carelessness, that I severely underestimated the fact that crashes can happen without warning. That is on me.

---

### Post by tea for one on 2020-10-06
> 2) Live Boot using Ubuntu
I had the Ubuntu 20 iso on my windows partition, so I burned it onto a USB. Following the tutorial below:
[https://ubuntu.com/tutorials/create-...rtition-scheme](https://ubuntu.com/tutorials/create-...rtition-scheme)

Proceeded to live boot using USB.


Boot into the [COLOR="#0000FF"]live[/COLOR] session and, instead of trying to repair grub or your file system, back up all your data.

---

### Post by oneala on 2020-10-06
Thanks, but pardon my ignorance, I am not sure how to backup all my data. 
Cannot even view my folders (some folders have a red cross)

I will try to use gddrescue to copy everything.

Am still concerned, about what will happen because the super block is corrupted

---

### Post by ActionParsnip on 2020-10-06
You can use a different superblock. The superblock is important so just use a different one when you use fsck

---

### Post by tea for one on 2020-10-06
> **oneala said:**
> Thanks, but pardon my ignorance, I am not sure how to backup all my data. 
Cannot even view my folders (some folders have a red cross)

I am only referring to your personal data in your home directory.

As long as your data is securely backed up, you can always re-install Ubuntu if superblock repairs fail.

When you boot a live session, can you identify your user directory?

If you can, then copy it to an external usb stick/drive.

I assume that your Windows OS and data therein is OK and accessible?

---

### Post by oneala on 2020-10-06
Yes ! I am in the process of copying the data. My windows OS is Ok and accessible.

---

### Post by tea for one on 2020-10-06
When your back-up is complete, then you can then decide to fix the superblocks or re-install.

I would suggest a re-install, because it is good practice to become confident with installer software (Ubiquity in Ubuntu's case), partitions, file systems etc.

Also, good practice to restore your personal data files from a back-up.

---

### Post by oneala on 2020-10-10
Did as suggested, worked like a charm :)
Thanks.

---

