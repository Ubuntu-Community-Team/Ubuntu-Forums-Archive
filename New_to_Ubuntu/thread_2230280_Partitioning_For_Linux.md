---
title: "Partitioning For Linux"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by john_smith14 on 2014-06-18
Hi,


I have the following set-up:


SSD 64GB
HDD1 1TB
HDD2 3TB
Ram 16GB
I've decided to use GPT for all along with UEFI and dual boot Windows 7 64 bit on the HDD.
Since i want Linux as my main system i've was thinking of the following split:
#ssd
/boot 300-500 mb
/ 20GB
/var 15GB #not sure if it's the right place for var but i think the SSD will survive
/home rest of the ssd
#Probably Ext4 for all tho i don't why some choose ext3 for boot, do i need a COW FS?
#No need for swap as far as i can see
#Not sure but do i need to have /usr in a separate partition?
#hdd1
C:\ NTFS 200-300GB
D:\ (/data on linux) NTFS rest of the HDD to be shared as Downloads etc.
#hdd2
Backup Drive - Weekly backup of /Home


I'm also considering pushing /tmp /var/spool /var/tmp and /var/log to Ram(tmpfs).
Since i'm still new at this what do think? I'm planning to run a few vm's and is mainly for personal\code development machine..


Thanks.

---

### Post by TheFu on 2014-06-18
Don't make this so hard.

/ - boot, var, programs (everything but home+swap)
/home - having this separate is important.
swap - you NEED some swap partition so the system gets slow before RAM is gone. 2G is the recommended amount. Put it on spinning disk.

I think you'll want more EXT4 storage.  If this is a Linux machine - why have ANY NTFS at all?   Oops - as Oldfred points out below.  OTOH, as a Linux lover "why have any NTFS at all?"  ;)

---

### Post by oldfred on 2014-06-18
He does mention dual boot Windows 7 on hard drive.

Windows 7 default install is BIOS with MBR partitions. You have to copy DVD to flash drive and make some updates to convert it to a UEFI installer.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

This is how I partitioned my 64GB SSD, but I only have BIOS now and planned to move it to UEFI. Now it is 2 years old, so may just get a new larger one. I have several installs of trusty on hard drive and all data & swap on hard drive. I currently still boot 12.04 as my working system and just about have 14.04 configured the same, but may not fully convert until first point release.

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sdd
[sudo] password for fred: 
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3645 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    8300  Precise
   4        58925056       117229743   27.8 GiB    8300  TrustySSD


```

---

### Post by john_smith14 on 2014-06-19
> **oldfred said:**
> He does mention dual boot Windows 7 on hard drive.

Windows 7 default install is BIOS with MBR partitions. You have to copy DVD to flash drive and make some updates to convert it to a UEFI installer.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

This is how I partitioned my 64GB SSD, but I only have BIOS now and planned to move it to UEFI. Now it is 2 years old, so may just get a new larger one. I have several installs of trusty on hard drive and all data & swap on hard drive. I currently still boot 12.04 as my working system and just about have 14.04 configured the same, but may not fully convert until first point release.

```
fred@fred-Precise:~$ sudo gdisk -l /dev/sdd
[sudo] password for fred: 
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdd: 117231408 sectors, 55.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 85A657E7-D379-4592-B060-E8EA09953D80
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 117231374
Partitions will be aligned on 2048-sector boundaries
Total free space is 3645 sectors (1.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          616447   300.0 MiB   EF00  
   2          616448          618495   1024.0 KiB  EF02  
   3          618496        58925055   27.8 GiB    8300  Precise
   4        58925056       117229743   27.8 GiB    8300  TrustySSD


```

Thanks for the Win 7 UEFI guides will definitely come in handy :)
Can you explain both 27.8 GiB partitions? i didn't get which one is which... i'm guessing one is /.
Also Isn't suspend enough? why do i need swap for? and where do you keep your /var?

> **TheFu said:**
> Don't make this so hard.

/ - boot, var, programs (everything but home+swap)
/home - having this separate is important.
swap - you NEED some swap partition so the system gets slow before RAM is gone. 2G is the recommended amount. Put it on spinning disk.

I think you'll want more EXT4 storage. If this is a Linux machine - why have ANY NTFS at all? Oops - as Oldfred points out below. OTOH, as a Linux lover "why have any NTFS at all?" ;)


Ok so:
1. i'm pretty sure i want a seperate boot or ESP as i might want to encrypt some stuff
2. i'm still not sure if it's a good idea to have /var on a 2y old SSD
3. i'm also not sure about swap as mentioned in my response to oldfred

To answer the NTFS\WINDOWS question i would say "Gaming" Currently there is more support for windows so i must keep my windows as well and since games do take a lot of space it's not an entirely bad idea to have a rather large NTFS partition.

---

### Post by oldfred on 2014-06-19
My SSD is smaller, but I still have two / (root) partitions. One is my current main Precise 12.04 install in sdd3 and the other is my trusty 14.04 install, soon be be my working install. I have other trusty test installs on my hard drive so I labelled it trustySSD so I know which is which.

All my system partitions are in my / partition including /home and total is 11GB (edit, up now to 12) out of the 27.8GB. All my data is in /mnt/shared & /mnt/data which have folders that I link into /home to replace all the default folders like Documents, Music, Video etc. I also move some hidden folders like the Firefox & Thunderbird profiles to my shared partition. Both data partitions are mounted in all my installs so all my data is the same in every install. As you can see I do not have lots of data. Almost no videos, a few Music CDs I have ripped and mostly text, spreadsheets and misc data that is not large.

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G   12G   15G  43% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           396M  1.1M  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  132K  2.0G   1% /run/shm
/dev/sdc2       100G   42G   59G  42% /mnt/shared
/dev/sdc6        97G   60G   32G  66% /mnt/data
/dev/sdd4        28G  7.9G   19G  31% /media/trustySSD


```

---

### Post by john_smith14 on 2014-06-23
> **oldfred said:**
> My SSD is smaller, but I still have two / (root) partitions. One is my current main Precise 12.04 install in sdd3 and the other is my trusty 14.04 install, soon be be my working install. I have other trusty test installs on my hard drive so I labelled it trustySSD so I know which is which.

All my system partitions are in my / partition including /home and total is 11GB (edit, up now to 12) out of the 27.8GB. All my data is in /mnt/shared & /mnt/data which have folders that I link into /home to replace all the default folders like Documents, Music, Video etc. I also move some hidden folders like the Firefox & Thunderbird profiles to my shared partition. Both data partitions are mounted in all my installs so all my data is the same in every install. As you can see I do not have lots of data. Almost no videos, a few Music CDs I have ripped and mostly text, spreadsheets and misc data that is not large.

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G   12G   15G  43% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           396M  1.1M  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  132K  2.0G   1% /run/shm
/dev/sdc2       100G   42G   59G  42% /mnt/shared
/dev/sdc6        97G   60G   32G  66% /mnt/data
/dev/sdd4        28G  7.9G   19G  31% /media/trustySSD


```

OK So eventually i've decided to go with:

#SSD
1 mega for grub2
/boot +ESP 1GB
/ 20GB
/home what's left of the SSD

and the HDD will be 2 NTFS partitions.

Now the only question is should i install linux then windows or the other way around and should i perform SSD optimization before or after installation.

---

### Post by oldfred on 2014-06-23
Grub2 only needs the 1MB bios_grub if booting in BIOS mode. Some want the flexibility to do either, so optional.
You do not need a separate /boot, but do need the efi partition for UEFI boot, the efi partition should be first on drive.

I do not know of any SSD settings you can do before install. The are part of settings you change after install.

I would disconnect drive not used so each install is purely on the one drive. Otherwise installers may use the other drive for efi files or Windows may put a boot partition on another drive if in BIOS mode (and just overwrite what is there).

       Only 64 bit Windows supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)


 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by john_smith14 on 2014-07-06
Thanks For all the help!

---

