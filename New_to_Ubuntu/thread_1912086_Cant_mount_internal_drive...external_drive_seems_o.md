---
title: "Cant mount internal drive...external drive seems ok"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by wherbjr35 on 2012-01-20
Greetings forumers,

I am running Ubuntu server 10.04.3 and am having trouble mounting an internal drive. I believe part of the problem is that I may have several copies of fstab file and am not sure they are in sync. It was not my intention to create multiple copies, but i used a restore command at one point b/c i was confused ;-()   

Here is the output from fdisk:

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/htwm--mediasvr-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=fd39d4a9-2ec0-4aa7-8866-a20637dc3c2b /boot           ext2    defaults        0       2
/dev/mapper/htwm--mediasvr-swap_1 none            swap    sw              0       0
/dev/sdc1 /media ntfs-3g rw,auto,user,exec,sync 0

```

I added the last line for /dev/sdc1, which seems to be working.  

Once I get this internal drive mounted, I have a flash drive that wont show up either.  I am hoping the process used to mount one will be similar for the other. 

Thanks for the assistance. 

wherbjr35

---

### Post by wherbjr35 on 2012-01-20
I ended up going with this.

```

sudo blkid

```

Which produced this output

```

 sudo blkid
/dev/sda1: UUID="fd39d4a9-2ec0-4aa7-8866-a20637dc3c2b" TYPE="ext2"
/dev/sda5: UUID="gyXzZK-b5TB-mj0Y-LoyA-34ee-ozNd-5MtOXO" TYPE="LVM2_member"
/dev/sdb1: LABEL="^A" UUID="271F-13E9" TYPE="vfat"
/dev/mapper/htwm--mediasvr-root: UUID="65c9092a-c9e1-49f0-b9be-163ee925affe" TYPE="ext4"
/dev/mapper/htwm--mediasvr-swap_1: UUID="3594f72c-7f8b-4e42-b356-5cd42d82ba5c" TYPE="swap"
/dev/sdc1: LABEL="NTFS40GBUSB" UUID="4466243B6624305A" TYPE="ntfs"

```

Then added this to my fstab file...

```

#80GB - data only
UUID=271F-... /mnt/primaryHD vfat rw 0
#40GB - music only
LABEL=NTFS... /media ntfs rw 0

```

Does anything look out of place? After saving changes, I was able to browse to mount points.

Thanks,
wherbjr35

---

