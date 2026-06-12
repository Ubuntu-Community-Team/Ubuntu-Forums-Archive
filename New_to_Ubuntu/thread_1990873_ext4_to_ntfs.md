---
title: "ext4 to ntfs"
date: 2012-05-30
forum: New to Ubuntu
---

### Post by glacierjean on 2012-05-30
i installed ubuntu 12lts(latest distribution) and i setup the partition it's on as ext4 journaling file system, but i need to erase ubuntu and install windows on it but on the windows installation page it says cant install on that partition because its unknown..so is there anyone who can help me learn how to change the ext4 partition back to ntfs

---

### Post by gamblor01 on 2012-05-30
You should be able to delete partitions in the Windows installer.  I forget exactly how it works but I'm pretty sure you just select the partition that you wish to install to and then use the D key to delete that partition.  It will have you confirm that (with the L key if I remember correctly) and after that it should just show up as free space.

If that doesn't suit you then you could always use a graphical tool like gparted, or go command line style (place the live CD in, boot up, and then use cfdisk to delete the partition).  If you wish to use one of these tools we'll need to know a little more about your disk layout, so boot into Ubuntu or use a live CD and run this command:

```
sudo fdisk -l
```

But really you shouldn't need any of this...why on earth would anyone want to remove Linux and install Windows?!??!!  :p

If you need any further help just ask.

---

### Post by wilee-nilee on 2012-05-30
Windows 7 has a custom and advanced, from there you can make a ntfs any size you want. XP  and vista also have custom install choices as well. Delete the ext4 and make the ntfs from this section of the install.

[ATTACH]218941[/ATTACH]

---

### Post by oklokl on 2012-05-30
sudo apt-get install gparted

UI
Windows key > gparted 

ext4 system > Editing Partitions
First, please back up your files.
Notices will lose data.




How to format a partition

 sudo parted -l
 Partition view

 ex> 
To format the partition.
 Data is erased.
Elsewhere
Copy important documents.

 / dev/sdcX1 => ext4  (Want to change the partition)
 test @ test> 
sudo mkfs.ntfs -f / dev/sdXy


If you try to change it back to ext4.
sudo mkfs.ext4 /dev/sdXy

---

### Post by Elfy on 2012-05-30
If you are going to post information about partitioning it is much better to either use the information already in the post or use something to represent partition numbering - for example

sudo mkfs.ntfs -f / dev/sdXy

---

### Post by oklokl on 2012-05-30
ok
Thank you good answer.
/dev/sdXy

I'll make sure it won't happen again 
n,.n

---

### Post by oklokl on 2012-05-30
Data will be copied.
ext4 -> ntfs
In the Windows system to use ext4

[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

---

### Post by wilee-nilee on 2012-05-30
> **oklokl said:**
> Data will be copied.
ext4 -> ntfs
In the Windows system to use ext4

[http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)

The user just wants to install windows, windows can delete the ext4.

---

### Post by oklokl on 2012-05-30
If the data is assumed to remain
/home

Users folder, the file data
 Important Documents

---

### Post by wilee-nilee on 2012-05-30
> **oklokl said:**
> If the data is assumed to remain
/home

Users folder, the file data
 Important Documents

I think that is a fair concern on your part. :)

It would be helpful though if you used sentences addressing this, cryptic messages are open for interpretation, and can be misinterpreted, and defeat the purpose of helping here.

If you look through the forums you will notice that most people use a standard form of addressing the other user.

---

### Post by soumoks on 2012-05-30
If u really want to remove ubuntu,within windows,delete the ubuntu partitions i.e the main large partition and the swap partition created by ubuntu,then reformat the partitions into NTFS using the default disk management tool available within windows,to delete the ubuntu partitions,right click on them and say delete volume,now u will have free space left which u can reclaim by formatting it into NTFS..hope this helps..

---

### Post by oklokl on 2012-05-30
wilee-nilee
 Answers to
know your stuff


I do not enjoy a copy.
I'm really sorry.
I'll try to come up with some ideas to solve the problem

---

