---
title: "Some help with partitioning, please?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Thre365ive on 2008-05-29
So I'm confused as **** here.

I'm trying to create 3 partitions with sda1 as root if possible, while retaining the files, sda2 as the data partition.

[Here's a screenshot of GParted.](http://i113.photobucket.com/albums/n240/36fuckin5/Screenshot.png)

Any help is much appreciated.

---

### Post by kk0sse54 on 2008-05-29
little confused at what you are trying to do. What partition are you trying to keep or are you trying to wipe the drive? Also are you using the GParted in the liveCD?

---

### Post by jimv on 2008-05-29
Right click the partition you're trying to delete and click unmount.

---

### Post by mlentink on 2008-05-29
+1 to the confusion...

As far as I can see you're trying to do a lot in an extended partition, but you haven't used your share of primary partitions yet.

Could you describe just what you want to achieve?
We might be able to guide you through it...

---

### Post by kwacka on 2008-05-29
I, too, am confused - do you want a complete new setup with sad2 as /home?

Possibly preferable a simple install with the unallocated space as 

sda1  /
sda2  /swp
sda3  /home

You will the be abled to move the contents of the extended partition to /home (sda3) & then delete the extended partition & resize /home.

---

### Post by drs305 on 2008-05-29
I had him come over from a previous thread. It's a fairly recent install with no windows partitions desired. He just wants a root partition, a data partition (but not a separate home) and the swap partition.

He is looking for the best and easist way of achieving this from what he currently has. Root is currently sda6 and swap is sda7. I did not discuss the benefits of just starting from scratch ;-)

---

### Post by kk0sse54 on 2008-05-29
Correct me if I am wrong but the only partition he needs to delete is sda5 but since sda5 is under an extended partition along with the small unallocated space I didn't think it was possible to merge the free space from the extended partition with the 57GB free space outside the extended partition. So then  he could delete sda5 and then resize his root partition to include the free space under the extended partition and then the free space outside the extended partition he can format as his data partition using ext3 or ntfs or whatever he wants.

---

### Post by drs305 on 2008-05-29
I sent him here because I am not an expert in paritioning. He has cleaned it up a bit since the last time I saw a picture from gparted. As you can see, his root partition is almost full. I wasn't sure how save it would be to expand it to the left. Anyway, as I said, I'm not an expert in this so I'll butt out now... Thanks for your help.

---

### Post by kwacka on 2008-05-29
Thanks for the background, drs305.

Thre365ive what, exactly, do you want?

You have a logical partition containing data - apart from the contents of your /home partition what do you want to keep?

You have unallocated space of 52 GB. Personally (others may disagree) I would use gparted to create 3 partitions:

sda1  label /  possibly 10GB (or smaller)
sda2  label /swap   2GB, for eample
sda3  label /home   remaining 40GB

Do not format sda5/6/7  but label anything you want (e.g. /x, /y, /z.)

Install ubuntu.

Copy data you require from /x, /y, /z to /home.

Delete /x, /y, /z.

Expand sda3 OR create new partition labeled /data

---

### Post by Thre365ive on 2008-05-30
Sorry I took so long, I had a Blind Melon concert to go to.

But what I'm going for here is to just have 1 partition to keep all my necessary Linux files on, a swap partition and one for data. I don't honestly give a damn what they're named as long as I can use them. As it is now, I've got about 20 gigs of space that I'm not even able to use. I was running GParted from the HDD. Now that I think about it, I should have done it from a boot disc.

I'd prefer a way to do it without re-installing Ubuntu if possible. I'm a pretty big n00b at this. I'm pretty sure I just got lucky that my installation went pretty smoothly. This and getting my wireless card working are the only 2 things I couldn't figure out right away.

Wow, I'm drunk and rambling. Sorry, guys. I'll come back tomorrow when I'm all here.

---

### Post by kwacka on 2008-05-30
1. Insert install CD
2. when you get to partitioning, select 'manual'
3. create partition in unused space, about 10 GB should be enough. label  ' /'. (obviously without the " ' ")
4. create partition in unused space, about 2 GB label '/swap'
5. create partition in unused space, use remainder of free space, label '/home'.
6. Install, restart.
7. Use nautilus to find any files you want in the partitions inside the logical partition, and copy to /home/user.
8. install & run gparted```
sudo apt-get install gparted
sudo gparted
```9. Delete partitions inside logical partition. Resize if you wish
10. Create extended partitions inside logical partition, any size you want, any name you want (except ones that are already in use by base system, e.g. boot, home, opt, usr) e.g. data1, or data1 & data2, or data1......

---

### Post by Thre365ive on 2008-05-30
Thanks, but I've got it all sorted out now. I just backed everything up to CD, reformatted the entire HDD and reinstalled.

I've got it set up so that I've got Linux on sda1 - ext3 (I'm assuming this is what you meant by a home partition?) I've got 2.86 gigs of swap space on sda2 and I've got 65.69 gigs of space for data on sda3 - Fat32. 

The only thing now is that when I transfer my music over to sda3, it tells me that I don't have the proper permissions to write to it in ext2 or ext3. I can format it as Fat32 and it'll work, but I've heard that it's better to have ext2 or ext3 (would anyone care to explain why?). From what I've read, an ext3 would be best if I could get it running right, am I correct? I can format it over to ext3 no problem, but how do I make sure I'll have permission to read from/write to it?

---

### Post by Thre365ive on 2008-05-30
Bump.

---

### Post by drs305 on 2008-05-30
Reformat sda3 to ext3 (assuming you haven't put any data on it yet).

Make a mount point for the partition (name it what you want, data is just an example):
```
sudo mkdir /media/data
```

Backup fstab (this format makes it fstab-2008-05-30):
```
sudo cp /etc/fstab /etc/fstab-`date %F`
```

Open /etc/fstab:
```
sudo gedit /etc/fstab
```

Make (or alter if /dev/sda3 exists) the line in fstab for sda3:
```

# /dev/sda3
/dev/sda3 /media/data ext3 defaults 0 0

```

Save fstab.

Mount the partition:
```
sudo mount -a
```

Make yourself the owner of the mountpoint and subfolders and set permissions:
```
sudo chown -R username:groupname /media/data
sudo chmod -R 755 /media/data

```

Followup:
You can replace the /dev/sda3 with a uuid if you want. To find the uuid:
```
 sudo blkid | grep sda3
```

You can label the partition using e2label (replace 'data' with any name):
```
sudo e2label /dev/sda3 data
```

Once everything is done, if you make adjustments to fstab, you can check the results by running:
```

sudo umount -a
sudu mount -a

```

---

### Post by kwacka on 2008-05-31
> **Thre365ive said:**
> 
I've got it set up so that I've got Linux on sda1 - ext3 (I'm assuming this is what you meant by a home partition?) I've got 2.86 gigs of swap space on sda2 and I've got 65.69 gigs of space for data on sda3 - Fat32.


As it looks from your earlier posts like you have an 80GB drive and have allocated 65GB to sda3 you are likely to be running out of space on sda1 (which contains, amongst the linux system files in /bin, config files in /etc and users files in /home) pretty quickly unless you repeatedly transfer data from sda1 to sda3, i.e. you are back where you started.

I would suggest you re-install again.

This time, when you get to Step 5 (partitioning) choose either guided to use full disk, which will give you 2 partition:
partition a. about 78GB labelled '/'
partition b. about 2 GB labelled /swap

OR choose manual 
a. create a new partition about 12GB, ext3 (if you wish) with mount point '/'
b. create another new partition, 2GB formatted as swap, label '/swap/ 
c. create another new partition, using the remainder of the drive, formatted as e.g. ext3, label/mount point '/home'.

You should have no problem copy your CDs to your /home/user directory, whether its on /home/username at sda1 or on its own partition at sda3.

---

