---
title: "[SOLVED] I crashed my machine using fsck command"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Vishal Agarwal on 2008-09-08
I was trying to check the hard disk for errors and accidentally run this command. My boot loader all every thing is crashed. System is not booting. I had a dual boot system. 

How can I recover my previous partitions and installation. I had ubuntu 8.04 LTS Desktop edition (64 bit) CD. with that I have booted my system now.

Pls help, what do i do ?

---

### Post by sancho panza on 2008-09-08
Are you able to access/mount all your drives via the ubuntu CD? If so, first backup all your personal files (/home/username/). Try any recovery only after that. As a start, I might try using [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html#introduction") to see if I can fix grub.

---

### Post by Vishal Agarwal on 2008-09-09
help needed.

when I boot my system, it shows Error No 17.

---

### Post by Vishal Agarwal on 2008-09-09
Help Needed

---

### Post by amo-ej1 on 2008-09-09
Get a livecd and try to boot your system from that cd, then see if you can still access your harddrives  and your partitions ? 

What command did you execute ? What how are your drives partitioned ?

---

### Post by Bucky Ball on 2008-09-09
As mentioned, but you missed it. Try supergrubdisk. Download, burn, boot from the disk.

[www.supergrubdisk.org](www.supergrubdisk.org)

Grub error 17 is common. Supergrubdisk will probably fix.

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by Vishal Agarwal on 2008-09-09
Thanks to all replies.

---

