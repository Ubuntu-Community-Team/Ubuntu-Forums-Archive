---
title: "Need help with removable disk, Hardy 8.04, please."
date: 2008-07-04
forum: New to Ubuntu
---

### Post by L Campbell on 2008-07-04
I have a 4GB removable disk (thumb drive, pen drive) which is 'unreadable'.

Also, root is the owner. 

I'm hoping that if 'I' become the owner I can either open it or reformat it, so as to make it usable.

I have tried the command ' ls -l ' but none of the files that appeared were owned by 'root'.

If someone would point me in the right direction here, I would really appreciate it.

TIA

---

### Post by jombeewoof on 2008-07-04
I had this same problem with my thumbdrive last night.

You need to mount it manually
```
sudo mkdir /thumb
sudo mount /dev/? /thumb
```
where ? is your device. If you need to find that out

```
sudo fdisk -l
```
will show you all of the partitions on all of the devices currently connected to your system.

---

### Post by L Campbell on 2008-07-04
> **jombeewoof said:**
> I had this same problem with my thumbdrive last night.

You need to mount it manually
```
sudo mkdir /thumb
sudo mount /dev/? /thumb
```
where ? is your device. If you need to find that out

```
sudo fdisk -l
```
will show you all of the partitions on all of the devices currently connected to your system.


Thank you.  What I got from 'sudo fdisk -l' is:-

Disk /dev/sdb: 4278 MB, 4278190592 bytes
255 heads, 63 sectors/track, 520 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8ea6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          92      738958+   6  FAT16
/dev/sdb2              93         520     3437910   83  Linux
  
Should this be what I need to do now?

sudo mount /dev/sdb/thumb

Thanks again.

---

### Post by cariboo on 2008-07-04
It looks like you've got a fat-16 partiton and a linux partition. you will have to mount each partition seperately.

```
sudo mount /dev/sdb1 <mnt directory>
sudo mount /dev/sdb2 <mnt directory>
```

<mnt directory> is the directroy you want to mount the partition on.

Jim

---

### Post by jombeewoof on 2008-07-04
> **L Campbell said:**
> 
Should this be what I need to do now?

sudo mount /dev/sdb/thumb

Thanks again.

pretty much, but you have to identify the partition.

/dev/sdb identifies the actual device while 
/dev/sdb1 identifies the partition

sudo mount /dev/sdb1 /thumbfat
sudo mount /dev/sdb2 /thumbext

you will of course have to create the thumbfat and thumbext directories. You might not want to name them thumbfat or thumbext, that is totally up to you. They can also be mounted in subdirectories such as /thumb/fat and thumb/ext
as long as the following rules apply you shouldn't ever run into problems.

1. the directory must exist
2. the directory must be empty

Rule 2 is not necessarily hard and fast, but is always good form.

---

### Post by L Campbell on 2008-07-04
> **jombeewoof said:**
> pretty much, but you have to identify the partition.

/dev/sdb identifies the actual device while 
/dev/sdb1 identifies the partition

sudo mount /dev/sdb1 /thumbfat
sudo mount /dev/sdb2 /thumbext

you will of course have to create the thumbfat and thumbext directories. You might not want to name them thumbfat or thumbext, that is totally up to you. They can also be mounted in subdirectories such as /thumb/fat and thumb/ext
as long as the following rules apply you shouldn't ever run into problems.

1. the directory must exist
2. the directory must be empty

Rule 2 is not necessarily hard and fast, but is always good form.

WOW !  I appreciate your continued interest here but I am in way over my head, now.   :-)

When I create the directory 'thumbfat', should that be on the 'pen drive' itself, or in my 'home folder'?

Kind regards.

---

### Post by L Campbell on 2008-07-05
> **L Campbell said:**
> WOW !  I appreciate your continued interest here but I am in way over my head, now.   :-)

When I create the directory 'thumbfat', should that be on the 'pen drive' itself, or in my 'home folder'?

Kind regards.


I'm still stuck here and hoping someone might have a suggestion for me.

TIA

---

