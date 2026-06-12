---
title: "Partitioning in HDD"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-06-13
Hi all,

  I installed ubuntu 8.04 in my box a week before, after installing windows xp and while installing windows i partitioned my 80GB HDD into four partitions namely C: D: E: F:. i used wubi installer to install ubuntu in my box in E drive. in C: windows installed by default.

 i was reading mounting partitions (when u read this) in ubuntu forums - beginners talk. i found the command "sudo fdisk -l". so i used it in my machine and following is the output.

home@home-desktop:~$ sudo fdisk -l and i entered passwd.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9e3f9e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9728    57657285    f  W95 Ext'd (LBA)
/dev/sda5            2551        5100    20482843+   b  W95 FAT32
/dev/sda6            5101        7650    20482843+   b  W95 FAT32
/dev/sda7            7651        9728    16691503+   b  W95 FAT32

What all the above things saying. am not getting these. Moreover i could see in forums when they were using this command they got **"/dev/hda1"** etc whereas am gettng as above **"/dev/sda1"** wht is the difference. how can i associate my entire disk (except C drive) to store and manage files in D and F etc. if i mount using anything as mentioned in forums, will i get my windows xp deleted or files associated with it deleted. I am totally confused. kindly help me. Thanks in advance.

---

### Post by gr4nf on 2008-06-13
/dev/sda1? That's a known bug. If you have a SATA hard drive, the OS recognizes it a SCSI. sda represents SCSI, whereas hda is supposed to represent most else.

---

### Post by gr4nf on 2008-06-13
to mount a disk, use:
```

sudo mount

```
followed my the path to the partition, and the mount point, i.e.:
```

sudo mount /dev/sda3 /mnt

```
this should allow you to put files in any partition while booted into any other partition (xp excepted).

---

### Post by rabidninjawombat on 2008-06-13
As for the diffrences between hd vs. sd, i was under the impression that hd usually indicated a IDE based drive, were sd was usually SCSI or SATA based drives, though i imagine this could be wrong :) cause my IDE drives are also identifyed as sda, sdb, etc,  (im by no means an expert)

As for managing you windows files in linux, and vice versa, you can manage your windows files under ubuntu,  (you obviosly dont wanna go messing with and changing your c:\windows folders or anything like that) but you can access and edit your media, and documents just fine.  

As for managing your linux files under windows,  as far as i know windows will no normally read an ext3 filessystem. without some outside help.  Ive used this program here 

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Ext2ifs,  it will allow you to have read/write access to your linux partition under windows.. again the same thing goes here. you have to be careful with what you edit, :)

not sure if this answered your question.. more of general information :P

---

### Post by mailtwogopal on 2008-06-13
> **gr4nf said:**
> to mount a disk, use:
```

sudo mount

```
followed my the path to the partition, and the mount point, i.e.:
```

sudo mount /dev/sda3 /mnt

```
this should allow you to put files in any partition while booted into any other partition (xp excepted).

  hi gr4nf,

   am not clear yet, plz tell me how do i recognize in the "/dev/sdaX" (which one in the list i posted as a result of o/p due to sudo fdisk -l command) belongs to D and F drive which are free.i don wanna combine or goin to access files from windows to linux or vice versa. in that case shall i have to execute the command "sudo mount /dev/XXX/mnt" by replacing "XXX" as "sda1 or sda2 or sda5 or sda6" etc. Please help me as i am bewildered a lot.

---

### Post by mailtwogopal on 2008-06-13
Hi all,

  i have mounted the drives /dev/sda7, sda6, sda5 from the above list when i posted previously. can i feel the difference after mounting these items after mounting. any way to recognize it. may be this is out of my ignorance am asking. kindly bear with me if am illogical. please explain guys.

Thanks in advance.

---

### Post by stchman on 2008-06-13
> **gr4nf said:**
> /dev/sda1? That's a known bug. If you have a SATA hard drive, the OS recognizes it a SCSI. sda represents SCSI, whereas hda is supposed to represent most else.

sd is for SCSI and SATA

hd is for IDE

Hardy recognizes my IDE hdd as sd rather than hd, no biggie though.

---

### Post by mailtwogopal on 2008-06-13
Hi all,

  i open computer in places menu in top panel of ubuntu. i already mentioned i have 4 partitions C: with windows, E: with ubuntu, D & F drive are free space. but in computer - file browser i could see only 3 partitions and a CD-ROM drive, please refer attached screenshot for the same. can u please help guys.

Clarification in this is really appreciable. can u tell what is all about and also i can see file type unknown. why is it so?

---

