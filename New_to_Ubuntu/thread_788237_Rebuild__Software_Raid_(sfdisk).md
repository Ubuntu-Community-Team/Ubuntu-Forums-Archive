---
title: "Rebuild  Software Raid (sfdisk)"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by rgotten on 2008-05-09
I am testing my raid with my 3 hard drives, and have eliminated (zero) one of the har drives, i have two raid 1, one for the boot, one for the swap, and 2 raid 5 one for the system and one for home. The boot has the grub on each one of the har drive. I have tested disconecting each one of the hard drive and having always two conected and the RAID works degraded. Today i decided to go one step further and did a quick zero of one of the hard drives, and was able to boot in degraded way. This is my question: Reading to rebuild the RAID i found that i have to do a copy with sfdisk doing sfdisk –d /dev/sdb | sfdisk /dev/sda i am getting /dev/sda: "Permission denied" and then i get sfdisk: cannot open /dev/sda read-write

Can somebody help with this

Thanks

rgotten

---

### Post by arkitek on 2009-01-12
sorry to ask the obvious:

have you tried running the command as root? (sudo sfdisk ...) and also try changing the drive order so sda(f) is sdb and the good sdb is then sda. also when you do: cat /proc/mdstat does sda (failed) appear in the output. if so you need to mdadm --fail /dev/mdX /dev/sdaY (X = media from mdstat command, Y = partition tag from mdstat command) all the failed sda raid partitions. even good partitions, then use mdadm --remove /dev/mdX /dev/sdaY. 0 disk and then sudo sfdisk -d ... then reboot. 

then when mdadm --add the partions it should rebuild them.
 
Sorry if I stated the obvious ....

A

---

### Post by sc3 on 2011-03-08
A bit late, but in case anyone runs across this, you've go to type:

sudo sfdisk –d /dev/sdb | sudo sfdisk /dev/sda

Don't forget the sudo after the pipe (|).

---

### Post by mucho_maze on 2011-10-16
> **sc3 said:**
> A bit late, but in case anyone runs across this, you've go to type:

sudo sfdisk –d /dev/sdb | sudo sfdisk /dev/sda

Don't forget the sudo after the pipe (|).

Thanks! This was exactly what I did wrong! Now I can easily copy partition tables between my raid devices

---

### Post by electronico_nc on 2011-11-27
Hi all,
Just for records, I had to (considering copy table partition from /dev/sdb to /dev/sda) :
```
sudo sfdisk -d /dev/sdb | sudo sfdisk --force /dev/sda
```Hope this will help some :).

---

