---
title: "fdisk  ubuntu 12.04"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by noobb2 on 2014-03-06
The command fdisk -b 4096 /dev/sda  will 'format' sda? including the file system?

---

### Post by nunecas123 on 2014-03-06
Here are the commands for your help. It seems you want to edit the disklabel, which doesn't seem to format the disk. For that, you should delete the partition by using fdisk -d and adding it again by using fdisk -n. That will erase everything, including the filesystem. If you want to get a filesystem, you must do fdisk -t.

[IMG]http://cdn.howtogeek.com/wp-content/uploads/2012/02/Screenshot-at-2012-02-25-04_06_44.png[/IMG]

Here's a great tutorial: [LINK]("http://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/")

What do you want to do, basically?

---

### Post by noobb2 on 2014-03-06
> **nunecas123 said:**
> Here are the commands for your help. It seems you want to edit the disklabel, which doesn't seem to format the disk. For that, you should delete the partition by using fdisk -d and adding it again by using fdisk -n. That will erase everything, including the filesystem. If you want to get a filesystem, you must do fdisk -t.

[IMG]http://cdn.howtogeek.com/wp-content/uploads/2012/02/Screenshot-at-2012-02-25-04_06_44.png[/IMG]

Here's a great tutorial: [LINK]("http://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/")

What do you want to do, basically?

I'm trying to change the sector size from 512 to  4096 bytes, but i want to do this when install ubuntu server 12.04( to 2 hdd sda and sdb) but i assuming i can't enter in the command mode when i install ubuntu, so on the hdd (with the system) after i install the system i can't change this because like you said that will erase everything.

---

