---
title: "dd if= : Device mounted or device unmounted?."
date: 2016-02-28
forum: New to Ubuntu
---

### Post by gwein on 2016-02-28
Hi; I would like to back up my drive and I m going to use this command: 

dd if=/dev/sda of=/media/path/to/myexternaldrive/backup.img bs=256k conv=noerror


I got clear that my external drive has to be mounted, cause it is receiving the data and backing up  the img file, but what about the origin, my sda I want to backup into a binary file?.

I ve been told that: 

"You don't need to mount the disk you are copying from, in fact you probably should not do that". 

So would like to know for sure if the origin must be mounted or not, and if someone knows the reasons why mounted or why unmounted?. 

Thanks in advance to those who could say something back. Kind Regards!.

---

### Post by sudodus on 2016-02-28
Welcome to the Ubuntu Forums :-)

When you read from or write to a block device (in this case a mass storage device), no partitions on the source and/or target device should be mounted. In your case check that no partition on the source device is mounted.

I should warn you that ***dd*** is very powerful but also very dangerous. It does what you tell it to do without any questions: A small mistake, and you overwrite the family pictures or other valuable data. So is is nick-named 'disk destroyer'.

What is the file system on your external drive (where you want to write the image file)?

[hr][/hr]
Please consider using ***Clonezilla*** instead of dd.

Finally, never rely on a backup, that is not tested. In your case you should restore it to a 'third drive' and check that it really works.

---

### Post by gwein on 2016-02-28
my external drive is  1TB new and empty by the way and it is NTFS formated with just one partition: The source drive is a SSD 60GB with MBR, ubuntu OS partition and swap partition.

dd if=/dev/sda of=/media/path/to/myexternaldrive/backup.img bs=256k conv=noerror

and sda MUST be unmounted. and the external drive that stores the backup created with this command MUST be mounted for this concrete example. is that right?. 

I already know the dangers of dd if, I ll try with TimeShift my backup [https://www.youtube.com/watch?v=RoS4MHo20oA](https://www.youtube.com/watch?v=RoS4MHo20oA) instead :) . Thanks for advice, and for answering back:  that's why I created this post in fact. Did not feel like in the mood for learning from my own experience :).

---

### Post by sudodus on 2016-02-28
> ***All partitions on*** sda MUST be unmounted. and ***the partition on*** the external drive that stores the backup image file created with this command MUST be mounted for this concrete example. is that right?. 

Yes!

NTFS and ext4 are good file systems for storing huge files. (FAT32 has a file size limit of 4 GB.)

Good luck :-)

---

