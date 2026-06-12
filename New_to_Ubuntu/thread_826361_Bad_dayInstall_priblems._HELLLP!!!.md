---
title: "Bad day/Install priblems. HELLLP!!!"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Terran on 2008-06-11
So my Vista laptop died last night while installing an update. So now my Vista install is totally screwed. So what i would like to do is install a dual boot with Vista, take all the files off the other partition, burn them on CD then reinstall Ubuntu on a full partiton over the original installations then bring the old files back on.

BUT

The Ubuntu installer errors out when it trys to partition. And i can't get the harddrive to unmount in the live-CD so i can get the files that way. 

HELLLLLP!

---

### Post by Duck2006 on 2008-06-11
> The Ubuntu installer errors out when it trys to partition. And i can't get the harddrive to unmount in the live-CD so i can get the files that way.

To copy the files of the old partition, the partition must be mounted. You then can copy then to a usb stick or a DVD/CD

---

### Post by Sef on 2008-06-11
> The Ubuntu installer errors out when it trys to partition.

What errors are you getting?

> And i can't get the harddrive to unmount in the live-CD so i can get the files that way.


If you boot up from the Live CD, the hard drive should not be mounted at all.  

Is your computer still under warranty?

---

### Post by Terran on 2008-06-11
> **Sef said:**
> What errors are you getting?



If you boot up from the Live CD, the hard drive should not be mounted at all.  

Is your computer still under warranty?

It just won't partition, it says it encountered an ERROR and it takes me to another table of the two partitions and asks which to format. 

Is it under warranty? i'm not sure, i've had it about 4 or 5 months and i don't think Compaq offers any warranty on the software side.

---

### Post by Terran on 2008-06-11
I've been able to force a mount of the primary drive from the live CD, but I'm still don't think the partitioner will work when I restart to install even if I'm doing a full partition.

---

### Post by st33med on 2008-06-11
No, it should work. Nothing changes with the LiveCD; it is a permanent, unwritable disk when it is being used. Just go ahead and restart.

---

### Post by Terran on 2008-06-11
The dual boot partition did not work.

---

### Post by Terran on 2008-06-11
If I do a full install, will I be able to port the current music files from vista to ubuntu?

---

### Post by Het Irv on 2008-06-11
Not unless you have them saved eleswhere.  Do you have either a Usb drive or something like that.  If not you might want to look into DamnSmall Linux.  DSL can be booted into RAM, freeing up your CD drive to burn your data to disk.

---

### Post by cariboo on 2008-06-11
You are probably not setting a mount point for your new partition. It is probably set your /media/disk or something. You will have to change it to / and then it will continue on.

Jim

---

### Post by jimrz on 2008-06-11
for copying your files - you may have better luck using the knoppix live cd as it will auto-mount your drives

for partitioning - try downloading the gparted live cd, seems to be better than the version on our live cd

---

