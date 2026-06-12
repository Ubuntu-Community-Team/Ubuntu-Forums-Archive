---
title: "[SOLVED] RAID Help"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by talking_walnut on 2008-05-26
Hi,

I'm looking for some help in setting up 2 hard drives I got in a RAID0 array. I made an attempt at it already and it worked fine to begin with but after a while it got corrupted. Here's what I did so far (drives /dev/sdd /dev/sdc):

Created the new array with:

```
sudo mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sdc /dev/sdd

```

And assembled it with:

```
sudo mdadm --assemble /dev/md0 /dev/sdc /dev/sdd
```

Finally I formated the new partition (JFS) with :

```
sudo mkfs.jfs /dev/md0
```

As I said this worked for a while then failed. Now when I try and mount it i get a "mount: wrong fs type, bad option, bad superblock on /dev/md0," error. 

Anybody know how to fix it?

---

### Post by quelx on 2008-05-26
You need to create partitions on the drives of type Linux RAID autodetect (fd). **This will wipe out whatever is there already**

First stop the array

```
sudo mdadm -S /dev/md0
```

```
sudo fdisk /dev/sdc
```
**n** > **p** > **1** > **ENTER ENTER** > **t** > **fd** > **w**

Then recreate the array using the partitions not the entire drive, i.e.

```
sudo mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdd1
```

and start it with the like.

---

### Post by talking_walnut on 2008-05-26
I try that and get as far as the final step of creating the arrays. When I try it with 
```
sudo mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdd1
```

I get "No such file or directory. And when I try it with 
```
sudo mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sdc /dev/sdd
```

I get "Device or resource busy".

Anybody know what's going on? :(

---

### Post by quelx on 2008-05-26
what does ```
cat /proc/mdstat
``` show?

---

### Post by talking_walnut on 2008-05-26
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid0 sdb[0] sdc[1]
      976772992 blocks 4k chunks
      
unused devices: <none>

```

Should I be using sdb0 instead??

---

### Post by quelx on 2008-05-26
No, the 0 is the device number.  Your array is still active you need to stop the array ```
sudo mdadm -S /dev/md0
``` then ```
cat /proc/mdstat
``` to make sure it is actually stopped.

then do the fdisk bit above for both drives, creating **sdb1** and **sdc1**

Make sure the drives you are running **fdisk** on are the drives you want in the array ```
sudo fdisk -l /dev/sd{b,c,d}
```

After that create the array using the partition **sdc1** not the drive **sdc**

---

### Post by talking_walnut on 2008-05-26
I've created the partitions like you said (drives are sdc and sdd, I was wrong in my first post). I'm getting a "Device or resource busy" error :( Here's what I'm entering 
```
sudo mdadm --create /dev/md0 --chunk=4 --level=0 --raid-devices=2 /dev/sdc1 /dev/sdb1
mdadm: Cannot open /dev/sdc1: Device or resource busy
mdadm: Cannot open /dev/sdb1: Device or resource busy
mdadm: create aborted

```

Any ideas why this is? 
Thanks for taking the time to help so far

---

### Post by quelx on 2008-05-26
Make sure those drives are not mounted (don't know how Ubuntu would have mounted them, but...)

```
sudo umount /dev/sdb1
sudo umount /dev/sdc1
```

Just read [http://ubuntuforums.org/archive/index.php/t-129498.html](http://ubuntuforums.org/archive/index.php/t-129498.html)

so you may need to ```
sudo mdadm -S /dev/md0
``` again after fdisk because mdadm is auto detecting the drives and adding them to an array.

---

### Post by talking_walnut on 2008-05-26
Thanks a million!!

That seems to have worked. Hopefully it'll stay working :)

One quick question for anyone that knows. I want to upgrade to 8.04 and want to do a fresh install. What do I need to do to setup this RAID again after the reinstall without loosing all my data?

---

### Post by quelx on 2008-05-26
After you install mdadm again (assuming you do the fresh install) the drives *should* bind to md0 after you reboot.  mdadm is setup to detect arrays by checking for drives with the **fd** Linux RAID Autodetect format and seeing if they belong to the same array.

---

### Post by talking_walnut on 2008-05-26
Thanks again quelx. You're a lifesaver!! :)

---

