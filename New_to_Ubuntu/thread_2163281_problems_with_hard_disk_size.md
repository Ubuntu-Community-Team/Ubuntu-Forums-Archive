---
title: "problems with hard disk size"
date: 2013-07-17
forum: New to Ubuntu
---

### Post by vvhunter on 2013-07-17
Dear ubuntu users:

Today I've received my laptop, an asus k45vd with ubuntu as the OS. My concern is that according to the system, my internal hard drive has only 197 gb. of capacity, whereas the manual and specs indicate it should be 750 gb. Does ubuntu read the size of the disk in a different way? I hope you can help me, thanks in advance

---

### Post by deadflowr on 2013-07-17
You can open up the program "disks", or formerly in older versions "disk utility" and look for your disk in the leftside pane.
Then look at what the partitions are like on the main area.
Post a screenshot if you must.
197 vs 750 is a big difference no matter what.

---

### Post by vvhunter on 2013-07-17
Thanks for the answer. I checked with the tool you mentioned and it showed me the different partitions and the total size (750 gb). The thing I don't understand is that when I click on "system details", it provides the correct info about the processor, the RAM, but it says my disk only has 197 gb available. When I open a terminal and hit the command "df", it shows the same information

---

### Post by deadflowr on 2013-07-17
df shows disk usage for currently mounted partitions.

Try
```
sudo fdisk -l
```
This will show the breakdown of the disks and the disks various partitions/partitions schemes.

---

### Post by DuckHook on 2013-07-17
Hi and welcome to Ubuntu and the forums.

Please describe how you are getting your disk info. It is possible that your disk came already partitioned and only a portion is being used for Ubuntu. The rest may have been left unpartitioned in order to give you the flexibility to use in whichever way you wish.

In addition to @deadflowr's suggestion (and if easier), to see your disk and partition sizes, please bring up a terminal session and post the output of:

```
sudo parted -l
```

edit
late, as usual. @deadflowr has this covered
/edit

---

### Post by vvhunter on 2013-07-17
OK, I entered the command you said and this is the result:

Warning GPT (GUID partition table) detected on ' /dev/sda ' ! the util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sda: 750.2 GB, 
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units= sectors of 1 * 512= 512 bytes 
sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal) : 4096 bytes /4096 bytes

That's most of the information it gives. I have no idea what it means

---

### Post by oldfred on 2013-07-18
With gpt partitioned drives fdisk does not work. There is gdisk but it is not installed by default, but should be for gpt drives.
sudo apt-get install gdisk

 sudo parted -l
or
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

And that is dash el, not one -1, or capital eye -I

---

### Post by vvhunter on 2013-07-18
Thanks for the help. So, if I enter these commands, what will happen to the computer? Which one or in what order should I enter them?

---

### Post by deadflowr on 2013-07-18
> **vvhunter said:**
> Thanks for the help. So, if I enter these commands, what will happen to the computer? Which one or in what order should I enter them?

Are you meaning oldfred's suggested commands?
Then nothing will happen to your computer, except they'll spit out a more accurate description of your partition layout.

You can run any or all the commands, so never mind the order.
The sudo parted -l command is probably the easiest.
From there the output will tell you where the space is divided among the various partitions on the disk.

---

### Post by vvhunter on 2013-07-19
Model: ATA Hitachi HTS54757 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  200GB   200GB   ext4
 3      200GB   208GB   8000MB  linux-swap(v1)

This is what I got when I entered the sudo command. Can you explain to me what it means? Thanks

---

### Post by oldfred on 2013-07-19
You have gpt partitioning, with a fat32 boot which probably means you are booting with UEFI.
Your Ubuntu install is in a 200GB partition and 8GB for swap, but drive is shown as 750GB. 
Not sure if something is confused with the 4k drive as most new partition tools show those correctly.

Is rest of drive unallocated? Run the other command as they show partitions by sector so you can tell what parts of drive are used.

---

### Post by vvhunter on 2013-07-19
vvhunter@vvhunter-K45VD:~$ sudo gdisk -l/dev/sda
[sudo] password for vvhunter: 
sudo: gdisk: command not found
vvhunter@vvhunter-K45VD:~$ 

I don't know if I did something wrong, but whe I ran the last two commands, that is what I got

---

### Post by dannyboy79 on 2013-07-19
you may need to install it first.
```
sudo apt-get install gdisk
```
then run
```
sudo gdisk -l /dev/sda
```

---

### Post by vvhunter on 2013-07-19
Fetched 300 kB in 4s (71.0 kB/s)                     
Selecting previously unselected package gdisk.
(Reading database ... 174249 files and directories currently installed.)
Unpacking gdisk (from .../gdisk_0.8.1-1build1_amd64.deb) ...
Processing triggers for man-db ...
Setting up gdisk (0.8.1-1build1) ...
vvhunter@vvhunter-K45VD:~$ sudo gdisk -l/dev/sda
GPT fdisk (gdisk) version 0.8.1

Problem opening -l/dev/sda for reading! Error is 2.
The specified file does not exist!

 I ran the first command, apparently in installed something and then I ran the second one, that's the result

---

### Post by deadflowr on 2013-07-19
You need a space between the -l and the /dev/sda.
gdisk -l /dev/sda, not gdisk -l/dev/sda.

---

### Post by vvhunter on 2013-07-19
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1465149168 sectors, 698.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 6F6FC056-CF19-417A-AF4A-49AAE4DF0C0E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1465149134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1058707117 sectors (504.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          194559   94.0 MiB    EF00  
   2          194560       390819839   186.3 GiB   0700  
   3       390819840       406444031   7.5 GiB     8200  

Ok, that's what I got now

---

### Post by oldfred on 2013-07-19
You can copy commands and paste into terminal to avoid issues with spaces or characters like l,1 or I which may not display differently depending on font used.

Total free space is 1058707117 sectors (504.8 GiB)

You show you have not used 500GB of your drive. It is just unallocated space.

---

### Post by dannyboy79 on 2013-07-19
looks to me like you have a total of 698.6GB for use. You have a 94MB partition for EFI booting, 186.3GB is your / partition most likely and then 7.5GB I am assuming is you swap partition. 

Basically you have 504.8GB of unallocated space that you can partition into ext4 and mount it whereever you want. I would suggest either /mnt/storage OR /media/storage but it's totally a preference thing.

---

