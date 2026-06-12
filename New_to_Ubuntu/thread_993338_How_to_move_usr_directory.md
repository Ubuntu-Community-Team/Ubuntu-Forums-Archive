---
title: "How to move /usr directory"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by tmwsr3 on 2008-11-25
I would like to move my /usr directory onto another drive. How would I do that and keep all the links and permissions?

---

### Post by Nycticorax on 2008-11-25
Can you explain why you need to do it? Otherwise I think people are going to worry that they're giving you advice which is going to lead to (serious) problems for you.

---

### Post by mbsullivan on 2008-11-25
Are you filling up your drive, and you figure this will give you more room? Nycticorax's right, this is treading on dangerous ground.

Mike

---

### Post by tmwsr3 on 2008-11-25
> **mbsullivan said:**
> Are you filling up your drive, and you figure this will give you more room? Nycticorax's right, this is treading on dangerous ground.

Mike
yes i am filling my drive. i have a sd card and would like to move it to there. i bought the dell mini and with only the updates and gnomesword i have 87 mb left and would like to have more room.

---

### Post by redseventyseven on 2008-11-25
With Great Difficulty.

If there's another option for freeing up space I would recommend that.

---

### Post by Sorivenul on 2008-11-25
Since you appear to have downloaded some things try:
```
sudo apt-get clean
```
This should clear out unneeded, old .deb files from your apt cache, and give you a bit more room.

---

### Post by mbsullivan on 2008-11-25
> i bought the dell mini

Cool!

> yes i am filling my drive. i have a sd card and would like to move it to there. i bought the dell mini and with only the updates and gnomesword i have 87 mb left and would like to have more room.

Do you already have your /home/ directory on another drive? It should be easier to move than /usr/.

The basic procedure for moving either is as follows:

(1) Mount the new drive (let's say to /mnt/disk)

(2) Move all files to the new drive

```
sudo cp -a /home/ /mnt/disk/
```

(3) Make sure the files are there (you could compare sizes for one way)

```
du -sm /mnt/disk/home/; du -sm /home/
```

(4) Delete the old home directory

```
sudo rm -rf [home directory]
```

(5) Re-mount the drive as your home directory. Set the mount point in /etc/fstab. Let me know if you want more information on how to do this.

... and that's it! It should work with your /home directory, and *perhaps* with /usr, but in that case you might want to boot to a LiveCD before doing the operation.

In the future, it might behoove you to use [LVM2]("http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux)") with that computer. It will let you transparently stripe your storage over multiple drives and move things much more easily. Unfortunately, it doesn't appear to be as easy to get it working under Ubuntu as most things.

Mike

PS: You can also easily move your swap space onto the SD card to save space on your drive.

PPS: Moving /opt/ to the new drive should work pretty easily, too.

PPPS: Moving /usr/ onto the SD card will probably make programs slow to load and run, anyway. There's a lot of program data in those directories.

---

### Post by scorp123 on 2008-11-26
> **tmwsr3 said:**
> yes i am filling my drive. i have a sd card and would like to move it to there.  I don't think that this would work. For SD cards to work certain drivers need to be loaded ... and the utilities required for loading drivers just happen to underneath "/usr" as well ... You can move /usr to another disk, yes, "armed" with a live CD this shouldn't be too hard. Just don't forget to adjust /etc/fstab and to configure your new /usr location in there .... But SD card? Nope, I don't think that this will work.

Besides ... why SD card?? Would be slow as hell anyway, IMHO.

---

### Post by mbsullivan on 2008-11-26
> For SD cards to work certain drivers need to be loaded ... and the utilities required for loading drivers just happen to underneath "/usr" as well

I don't know... SD Card drivers should be built into the kernel. The sdhci, mmc_block, mmc_core, etc. are all in /lib/modules/..., and modprobe, etc. are @ /sbin/. 

It might be possible to move /usr/ to an SD card, but I certainly wouldn't advise trying on a whim :)

Mike

---

### Post by yldouright on 2008-12-16
I'm in a similar situation. My /(root) was built on a 4GB partition and it is now being choked off. I added a 192GB raid 5 partition successfully and made /Data the mount point. I would like to reconfigure my partitions so that everything except my /boot partition mounts on the raid 5 partition. Is this possible? Can I rename a mount point on an array or must it be empty and stopped to do this?

---

