---
title: "Moving a mount point - someone help me please I'm being slow!"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by django0909 on 2013-01-29
I have a 500gb external hd mounted at /media on an 80gb internal drive. Obviously said internal drive is now full. My fstab looks as follows - can anyone show me how to edit it so the drive mounts as a standalone device? Thanks!

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3b75e9e0-023b-4ed3-97ba-3d0862d604ed /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=45ee0ca5-7ad1-47c8-a8dd-6d9ae7fcc1c0 none            swap    sw              0       0
```

If you need any more info - tell me!

---

### Post by Bucky Ball on 2013-01-29
? The 500Gb partition doesn't mount any information on the 80Gb. It just uses a mount point in /media to be seen. That's all. If your 80Gb partition is almost full you are going to need to remove/move some data from it to the 500Gb.

I'm presuming the 500 mounts when you click on it and is not automatically mounted at boot as it's not in your fstab. If you create an entry for it in fstab you would still be mounting it in /media or /mnt. No diff. 

The partition you have mounting at boot is mounting in /, and nothing else should mount there. Rule of thumb is to mount any other partitions in /media or /mnt, but you would want the external plugged in and switched on whenever you boot if you add it to fstab else you are creating a new problem.

500Gb automatically mounting in /media when you plug it in/switch it on is normal and expected; it's not using any space in the 80Gb ...

---

### Post by django0909 on 2013-01-29
I can't work out what is going on then.

The 500gb (HD-EU) automounts at /media/HD-EU - yet disk usage analyser tells me that it's 99% full at 56.8GB? 

Any ideas?

---

### Post by django0909 on 2013-01-29
Oh and / tells me it's 100% full at 99.1gb - when / should only be 80gb!?

---

### Post by Bucky Ball on 2013-01-29
Hmmm. Something odd. What does Gparted tell you? Perhaps attach a screenshot. Also, with the external in, on and mounted, could you post the output of:

```
sudo blkid
```

---

### Post by django0909 on 2013-01-29
That /dev/sda (80gb internal) is almost full, (3gb free), and that /dev/sdc is nearly empty, (500gb). I do have another 80gb drive mounted at /dev/sdb that is also almost nearly empty. This drive is partitioned twice as sdb1 and sdb2....it's also a bit faulty!

---

### Post by django0909 on 2013-01-29
blkid output:

/dev/sda1: UUID="3b75e9e0-023b-4ed3-97ba-3d0862d604ed" TYPE="ext4" 
/dev/sda5: UUID="45ee0ca5-7ad1-47c8-a8dd-6d9ae7fcc1c0" TYPE="swap" 
/dev/sdc1: LABEL="HD-EU" UUID="FAF8375BF837157B" TYPE="ntfs" 
/dev/sdb2: LABEL="MediaDrive" UUID="E464D98264D9583E" TYPE="ntfs" 
/dev/sdd: LABEL="SchoolDrive" UUID="34446863446829B6" TYPE="ntfs" 


Do you still want a screenshot?

---

### Post by Bucky Ball on 2013-01-29
Then I would start moving some stuff from sda to sdb or sdc. ;)

PS: blkid doesn't seem to correspond with you explanation of the setup. There appears only one partition on sdb and there is an sdd.

---

### Post by SeijiSensei on 2013-01-29
If the root partition fills up, I believe access to mounted devices is also considered full even when they are not.

Why not simply migrate some files from sda to sdb?  You might consider mounting /dev/sdb1 as /home.  That would probably solve a lot of your disk capacity issues for now.

```

# copy /home to /dev/sdb1
sudo mount /dev/sdb1 /mnt
cd /home
sudo rsync -av . /mnt
cd /
sudo umount /mnt

```

Then edit /etc/fstab and repoint the entry for /dev/sdb1 so it mounts as /home.  If everything works as planned, then reboot into "recovery mode" and delete the files from the original /home to gain back the space.

```

mount -o remount,rw /
cd /home
rm -rf *

```

will do the trick.

---

### Post by django0909 on 2013-01-29
This is the thing - I can't tell what's taking up all the room on sda1...

There's definitely another partition on sdb according to gparted - don't know why blkid isn't reporting it?

It looks to me like somehow a copy of information on sdc is being generated again in sda1...not sure how?

Oh, sdd is a usb pen drive :-)

---

### Post by django0909 on 2013-01-29
SeijiSensei - I did that, but moved them to sdc instead of sdb, (bigger drive) - shall I still do the rest of your instructions?

---

### Post by SeijiSensei on 2013-01-29
So now you're mounting /dev/sdcX as /home?  That's fine as long as you don't intend to detach the external drive.  I suggested using /dev/sdb because it is an internal.

If you've rebooted with /dev/sdcX as /home and everything appears intact, then yes, you can take the last step and delete the contents of /home on /dev/sda1.  When you reboot again, your root partition on /dev/sda1 will be much smaller.

---

### Post by django0909 on 2013-01-29
Ah yeah - I would need to remove that drive as I take it to work sometimes..

edit: sda is internal, sdb is external...?

edit 2: Yep, sda is internal, sdb is definitely external. I have two external usb, one is 80gb, one is 500gb and one internal, which is 80gb.

---

