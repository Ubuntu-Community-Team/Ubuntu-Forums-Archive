---
title: "Format and partiton USB flash drive???"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Dissident85 on 2008-06-18
Hi all, i am trying to format and repartition my flash drive. but i am having quite a bit of trouble doing so... 

i am using a cheep 512mb one i had lying around for testing, what i am trying to do is create a 10mb partition, and a the remainder to be another partition.

i have never used fdisk in linux before but when i type in the command 
```
fisk /media/disk
```
i get the fallowing error
```
last_lab(): I don't know how to handle files with mode 40700
You will not be able to write the partition table.

Unable to read disk
```

any ideas on what this could be?

---

### Post by KingTermite on 2008-06-18
You are using the directory there, not the device.

do this command:

**sudo fdisk -l**

That should give you list of devices and you can figure out which one your thumb drive is (like sdb0 or something like that).

Then you can use that name like:

**sudo fdisk sdb0**

once in fdisk, I think you can type "help" to get commands. Also google, probably dozens of tutorials. Just don't forget to issue "w" command last to WRITE the partition table.

---

### Post by steve101101 on 2008-06-18
remember to be careful when formatting as you will erase all data on the selected drive.

---

