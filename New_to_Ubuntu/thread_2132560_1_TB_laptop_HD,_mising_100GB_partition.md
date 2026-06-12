---
title: "1 TB laptop HD, mising 100GB partition"
date: 2013-04-05
forum: New to Ubuntu
---

### Post by 00dram on 2013-04-05
I just bought a 1TB drive for my laptop and had Windows 7 on the 1st 100 GB partition.  Windows installed a smaller (~2GB?) recovery partition.  Both were primary partitions and the remaining ~900 GB is unallocated.  I was using gparted to set up partitions for Ubuntu 12.10 install.  

I decided that I didn't like my initial partition structure AND mistakenly deleted the 2 Windows partitions when I tried to start over.  Now gparted only shows the unallocated 931.51GiB partition.  I'd like to regain the missing disk space on the windows partition.  Data isn't important.  I'll do a fresh install of both windows and Ubuntu.

sudo fdisk -l shows the full drive.

Disk /dev/sada: 1000.2 GB

What do I need to do to get the missing  partition back?

---

### Post by fantab on 2013-04-05
First of all, when the manufacturer says your HDD is 1TB it will be less than that. So you wouldn't have lost exactly 100gb.
Does your machine has UEFI?

You can try [FIXPARTS]("http://www.rodsbooks.com/fixparts/") for Ubuntu LiveDVD/CD/USB and see if it helps...

---

### Post by Lembritt on 2013-04-05
That´s becuase gparted shows your unallocated space in GiB and fdisk shows it in GB

[http://wintelguy.com/gb2gib.html](http://wintelguy.com/gb2gib.html)

---

### Post by 00dram on 2013-04-05
Thanks to both of you.  That explains the size discrepancy - it was only in my misunderstanding.  Test disk found the partitions.  I'll let it finish then live with the recovery or start fresh depending on how well recovery works.

---

