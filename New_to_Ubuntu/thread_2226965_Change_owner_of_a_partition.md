---
title: "Change owner of a partition"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by Bob_Younkin on 2014-05-29
I have a Toshiba Laptop running 32 bit Ubuntu 13.10 that I want to upgrade to 64 bit 14.04.  I have a terbyte WD ext drive(/dev/sdc) that is partitioned into 4 partitions sdc 1, 2, 5, 6. sdc5 is about a 490 gig ext4 that I cannot write to.  I wanted to back up the hdd, install 14.04 and restore.  The file manager tells me that the owner of the partition is "root" and that I don't have permission.  I am the owner of partitions 1 and 2 but they are full.  I have enabled root on this machine but haven't figured out a way to run a gui from root.

Any suggestions?

Bob

---

### Post by Bashing-om on 2014-05-29
Bob_Younkin; Hi !

In simplest terms, you can change the ownership of the mountpoint away from root.
see: with terminal command 
```

man chown

``` For the format family of 'buntu - for other families other means must be employed.

For additional guidance, provide the means you are mounting sdc5 and where the device is mounted onto the file system.
BY the FIle System TABble; /etc/fstab ?
By automount through /media/Younkin ?
What is the format of the device ? - ext4, NTFS ?


[INDENT][INDENT]it's ubunt[/INDENT][/INDENT]

---

### Post by hyperreal on 2014-05-29
You can run a GUI partition program from root with the following command:  gksu gparted.

Make sure to have the gparted program installed:  sudo apt-get install gparted

---

### Post by aysiu on 2014-05-29
Open up a terminal and paste in ```
sudo chown -R *bob:bob* /dev/sdc5
``` assuming *bob* is your username in Ubuntu. This let's you take ownership of the Ext4 partition on that drive.

---

