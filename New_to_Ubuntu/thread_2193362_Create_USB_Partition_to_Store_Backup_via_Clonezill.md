---
title: "Create USB Partition to Store Backup via Clonezilla"
date: 2013-12-12
forum: New to Ubuntu
---

### Post by rafiqcmnet on 2013-12-12
Hi colleagues, re: OS - Ubuntu 12.04

1. I have one unallocated partition in my USB drive.

2. I plan to 'create volume' to the above using Gparted for the purpose of storing backups using Clonezilla.

My questions are:

3.1 In Gparted, what partitioning format should I use?

3.2 For backups, is it adequate if I backup partition sda1 only, instead of the whole disk?

Thank you in advance

---

### Post by rafiqcmnet on 2013-12-12
If I choose Primary Partition, the options are: ext2 ext3 ext4 fat16 fat32 linux-swap ntfs unformatted

IF I choose Extended Partition, hence no options available.

---

### Post by sudodus on 2013-12-12
Welcome to the Ubuntu Forums :-)

I suggest that you use the linux file system ***ext4***. It works well with Clonezilla, which itself is run on top of linux.

-o-

What partitions are there on your HDD/SSD to be backed up? Only /dev/sda?

I suggest that you make one first backup image of the whole drive (including the bootloader and the partition table). Then you can make 'smaller' backups of single partitions.

I use a ***multimedia*** partition, where there are mainly already compressed picture-, music- and video-files. It is a waste of time to back it up with Clonezilla. It is better to back up or synchronize the files. You can use ***Unison*** or the command line tool ***rsync***.

---

### Post by rafiqcmnet on 2013-12-12
Thank you. My pleasure to be here.

Appreciate the additional information you imparted. Will put to good use.

Using Gparted, I see

/dev/sda 12.29 GiB, broken down:

1) /dev/sda1 9.33 GiB, of which 3.73 is used

2) /dev/sda5 2.95GiB

I have no clue what data resides where but will educate myself in a day or two.

---

### Post by sudodus on 2013-12-12
I'm not sure, but I would guess that /dev/sda1 contains the root file system of Ubuntu and /dev/sda5 contains a swap partition.

You can get more information about that, if you run the terminal window commands and read the output carefully. You can copy and paste the text from each of the command lines into a terminal window and press the Enter key to launch the command.

Post the output here (within code tags) if you are not sure how to interpret it.

```

sudo fdisk -lu
sudo parted -l
sudo blkid

```

---

### Post by rafiqcmnet on 2013-12-12
I will implement your suggestions at a later stage.

At the moment I am still at base 1.

I use Gparted to format a 74.05 GiB USB partition. After partitioning I found that 1.34 GiB has been used! 

On top of that, right-clicking, I cannot create any folder or documents. 

Something is not right.

---

### Post by rafiqcmnet on 2013-12-12
Sorry I forgot to

sudo chmod 777 /media/< usb label >

It's fine now. I can write and delete. However why it takes 1.34 GiB before using?

---

### Post by sudodus on 2013-12-12
I think it is the journaling (file system metadata), that makes it possible to recover from many file system errors.

---

### Post by rafiqcmnet on 2013-12-12
TQ for the tips and all.

This my first time using Clonezilla. I did a disk backup and restored it thereafter. All went fine.

I can now proceed using Ubuntu with greater piece of mind. :)

---

### Post by sudodus on 2013-12-13
You are welcome,

When you feel that your problem is solved, please click on **Thread Tools** at the top of this page and mark this thread as SOLVED :-)

---

