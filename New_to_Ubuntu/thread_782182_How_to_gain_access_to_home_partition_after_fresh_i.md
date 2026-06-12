---
title: "How to gain access to /home partition after fresh install of 7.10"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by tuyuyu68 on 2008-05-04
Hi, I have just reinstalled Gutsy 7.10 and as recommended in several posts had /home under separate partition. After doing clean install though found /home partition under /media/lost+found, thought that by just changing owner and permissions would be able to move all files under the new /home directory? I don't have access to any of the files and understand that I need to mount this under /.
Below please find output of /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=27838135-2c4a-4b8f-9d3f-9edb810a5590 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=3a99517b-f876-4845-9e9b-37ffa30e2ff8 /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=f720ef8e-3b8c-4cfa-92e8-6d3d08571e84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Could someone please help I need some guidance on how to mount /home (sda3) under / and gain access to my files.

Thanks

---

### Post by raul_ on 2008-05-04
change

UUID=3a99517b-f876-4845-9e9b-37ffa30e2ff8 /media/sda3 ext3 defaults 0 2

to 

UUID=3a99517b-f876-4845-9e9b-37ffa30e2ff8 /home ext3 defaults 0 1

i suggest 0  2 to 0 1 because that's how I have it

---

### Post by bodhi.zazen on 2008-05-04
> **tuyuyu68 said:**
> Hi, I have just reinstalled Gutsy 7.10 and as recommended in several posts had /home under separate partition. After doing clean install though found /home partition under /media/lost+found, thought that by just changing owner and permissions would be able to move all files under the new /home directory? I don't have access to any of the files and understand that I need to mount this under /.
Below please find output of /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=27838135-2c4a-4b8f-9d3f-9edb810a5590 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=3a99517b-f876-4845-9e9b-37ffa30e2ff8 /media/sda3     ext3    defaults        0       2
# /dev/sda5
UUID=f720ef8e-3b8c-4cfa-92e8-6d3d08571e84 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Could someone please help I need some guidance on how to mount /home (sda3) under / and gain access to my files.

Thanks

What did you do to move your home partition ?

From fstab is looks as if you did not set any partition as /home, so right now /home is on root , / , > # /dev/sda1
UUID=27838135-2c4a-4b8f-9d3f-9edb810a5590 /               ext3    defaults,errors=remount-ro 0       1

So you look like you have two issues. One is to establish home on a separate partition. Best follow a guide for this :

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Also, when installing, to use a partition for /home you need to use manual parititioning.


Second problem is then data recovery. Hope it goes will.

Last piece of advice, go for a separate /data partition rather then a /home.

> **raul_ said:**
> change

UUID=3a99517b-f876-4845-9e9b-37ffa30e2ff8 /media/sda3 ext3 defaults 0 2

to 

UUID=3a99517b-f876-4845-9e9b-37ffa30e2ff8 /home ext3 defaults 0 1

i suggest 0  2 to 0 1 because that's how I have it

No that will not work. The last digit in fstab indicates if the file system should be checked at the time of booting. 0 = do not check. 1= check first and is used for the root partition. 2 = used for all else, check after root.

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by raul_ on 2008-05-04
Thank you then :) I guess it's the default behaviour with Arch

---

