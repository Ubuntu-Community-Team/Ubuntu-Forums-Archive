---
title: "swap file goes off"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Mosaab on 2008-04-30
when I installed ubuntu i didnt know anything about linux so I used 7 MB only as swap partition.

I want now to make a swap file , and I did it and it works fine when I run free -m, it shows.

but when I restart my system it goes again ... when I run free -m it shows me that the swap is only 7 MB as before ... 

is there something to do to make it permanent?

---

### Post by Monicker on 2008-04-30
Do you have an entry in /etc/fstab for the swap?  Did you enable it using the swapon command?

---

### Post by Mosaab on 2008-05-01
yes I did the swapon command .. and it worked ... but it doesnt when I restart ..
and there is only one entry for the swap in the fstab file but i dont know if its the swap file or the swap partition. 

this is the entry:
UUID=83a5d8bf-3e8b-4575-ba82-e18db57e9de6 none            swap    sw

---

### Post by Mosaab on 2008-05-04
should there be an entry for the new swap file ?
how can I add it ?

---

### Post by Mosaab on 2008-05-07
any one has any suggestion ?

---

### Post by philinux on 2008-05-07
you need to run the live cd and run gparted to shrink maybe home and enlarge the swap partition. 

But, it depends. How much ram have you got?

---

### Post by Mosaab on 2008-05-07
what if I want a swapfile !! 
I followed the steps of creating a swapfile carefuly.

ok . does it help if I put the command "swapon swapfile" ?
if yes where will I put it ? in what file?

---

### Post by philinux on 2008-05-07
> **Mosaab said:**
> what if I want a swapfile !! 
I followed the steps of creating a swapfile carefuly.

ok . does it help if I put the command "swapon swapfile" ?
if yes where will I put it ? in what file?

Sorry missed your sig. I've 2 gig of ram and I gave it 1 gig for swap. however the system mostly does not need it or use it. The only time it did was when i ran alien-arena and goolge-earth at the same time.


Like i said the only way to increase it is with gparted from the live cd

---

### Post by Delever on 2008-05-07
You need to modify your fstab file entry for swap file. You changed it, so probably it's UUID changed too. To find out UUID of swap partition:

1. Run gparted.
2. Note swap partition device name (for exaple, /dev/sdb5)
3. Start terminal
4. type 
sudo vol_id -u /dev/sdb5

it will show you UUID
5. open fstab
sudo gedit /etc/fstab

change swap file UUID to new one (if it is not the same)

(sorry, I thought you resized your partition, never mind this post)

---

### Post by lswest on 2008-05-07
the above method would work, but here's how i'd do it (no need for a liveCD):
```
sudo blkid
``` then find the UUID of your swap partition, then add it to your fstab file by copying the old swap file entry, and pasting it just below it, and edit the UUID to the new one.  That should be fine, reboot and it should start automatically.  Unless you created a swapfile, then i'm not sure, it should start at boot i believe.

---

### Post by Mosaab on 2008-05-07
Iam sorry guys but you are confusing me alittle cause I am new to linux.

this is how my fstab file looks like:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=d64e8e5d-78cb-4088-a3ab-a4f6d7a92bff /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=CA30B8AD30B8A1BD /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=83a5d8bf-3e8b-4575-ba82-e18db57e9de6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

..........................
My swap PARTITION is sda6.

I already have a swap parition but its too small .. its 7 MB ONLY.
I want to add a swap file ... and I did ... and I named it "swapfile", and I did the swapon command and every thing.

now, What should I add to the fstab? how can I get th UUID ?

I am sorry again for my ignorance ..

---

### Post by Mosaab on 2008-05-07
I fount the solution,
if you want to make the swapfile permenant all you have to do is to add this line in fstab:

/mnt/swapfile swap swap defaults 0 0

where /mnt/swapfile is the swapfile you created..

I did that and restared the system and ran free -m and found that the swap size increased indeed.

Thank you any way :)

---

### Post by prshah on 2008-05-07
> **philinux said:**
> you need to run the live cd and run gparted to shrink maybe home and enlarge the swap partition. 


> **philinux said:**
> 
Like i said the only way to increase it is with gparted from the live cd

> **Delever said:**
> You changed it, so probably it's UUID changed too. To find out UUID of swap partition:


> **lswest said:**
> 
```
sudo blkid
``` then find the UUID of your swap partition, then add it to your fstab file by copying the old swap file entry, 

He wants a swap FILE, not a swap partition so resizing is not the answer; as long as the swap file is setup in the /etc/fstab, all you need to do is ```
sudo swapon -a
```. If you use the mkswap command to make the swap, it will automatically add it to the /etc/fstab. further, you must use the "dd" command to create a file suitable for use as swap. From your posts, I assume you have done all this, and just want to know how to "auto-activate" it.

{Edit} Just saw page 2; that makes this post irrelevant.

---

