---
title: "How to increase my parition?"
date: 2015-01-19
forum: New to Ubuntu
---

### Post by anbu-s on 2015-01-19
I'm trying to resize my /dev/sda1 using gparted utility - I need to extend it by 4GB which is available in /dev/sda6. How do I do this? Since the /dev/sda2 is in the middle i'm unable to increase /dev/sda1.

I'm willing to lose the data thats in /dev/sda6 as it contains only a trial install of ubuntu which i did as a try.

---

### Post by fantab on 2015-01-19
It would be simple if you could delete partitions 6, 5 & 2.
After this you'd have lost your SWAP... merge your 4gb in /dev/sda1 and create a 4gb SWAP, /dev/sda2.

Since we recreated SWAP its UUID will change. After booting Ubuntu run the following in  Terminal:
```
sudo blkid
```

Note down (copy) the new UUID of the swap partition or /dev/sda2.

Now edit /etc/fstab file and replace the old UUID with the new:
```
sudo gedit /etc/fstab
```
and save the file.

---

### Post by anbu-s on 2015-01-19
> **fantab said:**
> It would be simple if you could delete partitions 6, 5 & 2.
After this you'd have lost your SWAP... merge your 4gb in /dev/sda1 and create a 4gb SWAP, /dev/sda2.

Since we recreated SWAP its UUID will change. After booting Ubuntu run the following in  Terminal:
```
sudo blkid
```

Note down (copy) the new UUID of the swap partition or /dev/sda2.

Now edit /etc/fstab file and replace the old UUID with the new:
```
sudo gedit /etc/fstab
```
and save the file.

Thanks for your reply. Just before doing this, I'm trying to understand this:

Without doing anything I ran this command sudo blkid
Got this

/dev/sda1: UUID="5e722b05-afc4-4da0-bd85-483f3689068a" TYPE="ext4" 
/dev/sda5: UUID="617f48cf-9e47-476d-b9da-e314459fc98c" TYPE="swap" 
/dev/sda6: UUID="40535afd-c30b-426f-8df2-8facc8edeb78" TYPE="ext4" 

When i looked at /etc/fstab command, i was expecting to see the swap UUID

But this is what I see 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
# swap was on /dev/sda5 during installation
#UUID=4b6a4e05-3a5e-4927-a274-6e7a572f8ff6 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=5e722b05-afc4-4da0-bd85-483f3689068a / ext4 errors=remount-ro 0 1

why is the UUID still the ext4 not SWAP?

---

### Post by fantab on 2015-01-19
You seem have an encrypted swap...

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=5e722b05-afc4-4da0-bd85-483f3689068a / ext4 errors=remount-ro 0 1
[COLOR=#006400]# swap was on /dev/sda5 during installation
#UUID=4b6a4e05-3a5e-4927-a274-6e7a572f8ff6 none            swap    sw              0       0
[/COLOR][COLOR=#b22222]/dev/mapper/cryptswap1 none swap sw 0 0[/COLOR]

```

I have placed the ext4 uuid at it appropriate place... (it make not difference).
When editing /etc/fstab after following my steps, delete the entry in red; remove the # in front of the Swap UUID, edit the UUID value.

---

### Post by anbu-s on 2015-01-19
Just before I do this, I wanted to confirm this - don't want to screw this up!!

In gparted, this is what i have as pending actions..is this correct?
The new partion I created shows up only as New Partition #1 - not sure whether this is correct
You can see the operations I did in the bottom window

---

### Post by Impavidus on 2015-01-19
Almost correct, that screenshot, but you have to unmount sda1 before you can change it. You can't unmount as long as you run the system that's installed on it, so you have to boot from a live disk and run gparted from there.

And did somebody already tell you that you have to make sure you have reliable backups of all important files on sda1? You should have them anyway. It's not likely anything goes wrong, but that may happen during partitioning.

---

### Post by anbu-s on 2015-01-19
How do i rename the new parition #1 to something like /dev/sda2?

---

### Post by fantab on 2015-01-19
You don't have to name it /dev/sda2, the second partition of your first HDD is always /dev/sda2 in linux.
[Gparted tutorial]("http://www.dedoimedo.com/computers/gparted.html").

---

### Post by anbu-s on 2015-01-19
de
Even to resize /dev/sda1 on my laptop (where i have the OS installed), do I have to do this with boot live DVD only? I thought i could do this on the fly??

---

### Post by yancek on 2015-01-19
> Even to resize /dev/sda1 on my laptop (where i have the OS installed),  do I have to do this with boot live DVD only? I thought i could do this  on the fly?? 		

You can't modify a partition on which you are running the partitioner, in this case GParted so yes, you need to do it from a CD/DVD with GParted.

---

### Post by kevdog on 2015-01-20
Partitions can't be mounted when you resize them, so hence you can't use the /dev/sda1 partition when you are trying to resize it.  Please back up everything prior to do this. Honestly what I found the easiest for me doing this would be to copy everything each partition to a back up media, such as an additional hard drive or something.  I usually do this with the dd command, however I suppose you could use something else. 

I then just started deleting partitions until reaching /sda1 -- I then resized it, and formatting, and then recreated the old partitions. I then copied each partition back onto the disk.  Please be aware as mentioned above the UUIDs will change after doing this, so you are going to have to modify your /etc/fstab file after doing this, unless you plan on mounting the partitions manually during the boot process.

---

