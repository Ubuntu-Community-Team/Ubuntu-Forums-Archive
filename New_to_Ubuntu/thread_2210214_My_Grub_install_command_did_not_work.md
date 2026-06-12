---
title: "My Grub install command did not work ?"
date: 2014-03-09
forum: New to Ubuntu
---

### Post by hebdave on 2014-03-09
[SIZE=3]Hi I **removed** my grub successfully on my good spec laptop with windows 7 and Ubuntu. I also was able to reinstall the grub back easily by doing this in the terminal - [/SIZE]

[SIZE=3][FONT=Source Sans Pro][COLOR=#141412]sudo grub-install /dev/sda via live cd or supergrub[/COLOR][/FONT]

[FONT=Source Sans Pro][COLOR=#141412]I have exactly the same set up on my desktop mesh (different computer) which instead has XP alongside Ubuntu. I uninstalled the grub in the same way as before [/COLOR][/FONT][https://sites.google.com/site/easylinuxtipsproject/grub#TOC-With-an-USB-memory-stick](https://sites.google.com/site/easylinuxtipsproject/grub#TOC-With-an-USB-memory-stick)[/SIZE][FONT=Source Sans Pro][COLOR=#141412][SIZE=3] and then tried to reinstall it with the above command in the same way as well. It did not work this time though for some reason. My Ubuntu version is the same too. The only difference is the default operating system is XP as described and it is a desktop this time.

I have looked on Google but get mixed messages and would prefer to ask here first rather than make an error with installing. Can I perhaps run a simple command in the terminal where it would tell you something about my Xp desktop set up ?

I am seeking to place grub back again with my current working windows and a 12.04 Ubnuntu. It needs a multi-boot grub install as normal.

Please I could do with your help - many thanks! [/SIZE]
 [/COLOR][/FONT]

---

### Post by Bashing-om on 2014-03-09
hebdave; Hi !

Show us what you are working with:
Post back the output - between code tags - of terminal commands:
```

lsb_release -a
uname -a
sudo fdisk -lu

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And we see about installing grub properly.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-03-09
If booted with Supergrub you are in your install and the reinstall to the MBR should work.
[SIZE=3][FONT=Source Sans Pro][COLOR=#141412]sudo grub-install /dev/sda

But if you have booted with Live installer you need to mount partition with / (root) (also /boot if separate partition)

[/COLOR][/FONT][/SIZE]        #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

    

Or use Boot-Repair which really just runs those commands.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by hebdave on 2014-03-10
Hi so I take it my first port of call after checking the partition for Ubuntu is [COLOR=#000000]sudo mount /dev/sda5 /mnt[/COLOR]
[COLOR=#000000]sudo grub-install --root-directory=/mnt/ /dev/sda . Then use the boot command one if necessary. I say this as when I use supergrub via usb , installed with yumi , the code [/COLOR][COLOR=#141412][FONT=Source Sans Pro]sudo grub-install /dev/sda does not work as you asked me[/FONT][/COLOR][COLOR=#000000]. It sounds like its not playing ball ? 

[/COLOR]```

root@it:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
root@it:~# uname -a
Linux it 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 athlon i386 GNU/Linux
root@it:~# sudo fdisk -lu


Disk /dev/sda: 8032 MB, 8032092160 bytes
5 heads, 32 sectors/track, 98048 cylinders, total 15687680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24642463


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        8064    15687679     7839808    b  W95 FAT32


Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4a0fe34


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   195915040    97957489    7  HPFS/NTFS/exFAT
/dev/sdb2       195915774   390721535    97402881    5  Extended
/dev/sdb5       195915776   384563199    94323712   83  Linux
/dev/sdb6       384565248   390721535     3078144   82  Linux swap / Solaris


Disk /dev/sdc: 31.2 GB, 31214010368 bytes
64 heads, 32 sectors/track, 29768 cylinders, total 60964864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7cdb7cd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    60964863    30482416    c  W95 FAT32 (LBA)
root@it:~# 

```

Is this code correct ? I had to press return one more time to access a new part of it. I am using a partition manager distribution which has a terminal that starts with the words root@it:
                    See boxed commands above to confirm this as I might need to omit something in my command lines now?!. My graphics goes nutty using the normal live cd so I am using this to sort it.

Thanks much appreciated.:D

---

### Post by hebdave on 2014-03-10
See the above post sorry it took a while to edit. Many thanks !

---

### Post by grahammechanical on 2014-03-10
Do you have two hard disks? If so which one is Ubuntu installed on? Which one has the boot priority? Is it the hard disk that you installed Grub to?

If you are installing Grub to sda but have sdb with the boot priority then Grub will never load.

Regards.

---

### Post by oldfred on 2014-03-10
If sda, is just your flash drive, you must install grub to sdb, so system will boot when flash drive is removed. 

It would still boot only if flash drive still plugged in, if you install grub to sda, and then flash drive will not work as live installer as it just has grub.

---

### Post by hebdave on 2014-03-10
High on reading through my log above I am touch confused myself. I had two flash drives in at the time. I did not need to have both in so I have now removed the one that was not being used for boot purposes. The new log is below just in case you need it.

```

root@it:~# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise
root@it:~# uname -a
Linux it 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 athlon i386 GNU/Linux
root@it:~# sudo fdisk -lu


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4a0fe34


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195915040    97957489    7  HPFS/NTFS/exFAT
/dev/sda2       195915774   390721535    97402881    5  Extended
/dev/sda5       195915776   384563199    94323712   83  Linux
/dev/sda6       384565248   390721535     3078144   82  Linux swap / Solaris


Disk /dev/sdb: 31.2 GB, 31214010368 bytes
64 heads, 32 sectors/track, 29768 cylinders, total 60964864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb7cdb7cd


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    60964863    30482416    c  W95 FAT32 (LBA)
root@it:~# 

```

As you can see alot has changed even with removing the one device. Being new to Ubuntu and new to partitioning I am struggling but probably understand enough with prior reading. Basically /dev/ sda 1 is currently my windows c partition and this is the boot priority. It boots into windows which was the only partition I had before I installed Ubuntu using the default partitioning . In the current log the /dev/sdb1  is just my booted live cd as I cannot boot my computer without the multiboot grub. So this is not where I want the grub to be of course. Instead I want it on the normal c drive that comes with the computer or just before it replacing the bootloader. My computer is the most basic state that beginners use with installing Ubuntu from the live cd.

There is now just one flash drive plugged in for this in the new log. Note the boot command in this live cd does start with the word root@it:~# and I wondered if this might effect anything I do next. I could remove my flash drive and boot into windows and use there command prompt to give you a log if you want that instead. Once flash drives are removed there is nothing else attached to my PC other than a mouse and it boots right into windows c.

I am sorry if my information is still lacking I will do my best to understand your next answers from my level of knowledge. Can you bare with me and still tell me how to proceed ? I did not want to confuse you further by leaping to conclusions so I kept it simple. I do have slightly more knowledge than what I have written but its limited and may be wrong.

Thank you.

---

### Post by oldfred on 2014-03-10
Now your drive is sda. This is why you need to run fdisk or parted to see drive order as with different devices plugged in BIOS may show them in different order to system. Even live installer may show devices differently than after install.

If you use Supergrub to boot into your install, you can directly install grub2's boot loader into the MBR of sda.

If you use live installer to boot you have to mount sda5 to correctly install grub to MBR. 
Or you can use Boot-Repair which automates the process.
Boot-flag is only used by Windows, grub does not use that.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by hebdave on 2014-03-11
Thanks it turned out I had to leave a one space gap between sudo-install and /dev/grub or that I typed install as instal when I used the Supergrub program. So I was on the right track from the start. However I am incredibly grateful for your help and am sorry about that ! Thread is marked as complete.

---

