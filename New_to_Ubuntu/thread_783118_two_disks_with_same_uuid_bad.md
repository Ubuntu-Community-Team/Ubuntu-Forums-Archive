---
title: "two disks with same uuid bad?"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by -random on 2008-05-05
Is this bad? Should I format one of the two drives?

```
mooooo@hardy32:~$ sudo blkid
/dev/sdb1: TYPE="swap" UUID="91dfa31f-a86b-4731-82ab-5374305579c1" 
/dev/sdb2: UUID="830fe1c8-a4c7-4fb0-a225-5fd2768f847f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="b57766ed-d149-42b8-aca1-76aa4bbe3cf2" TYPE="ext3" 
/dev/sdb4: UUID="10B2D8BA48BDBA9B" TYPE="ntfs"
************
/dev/sdc1: UUID="2A4C7A954C7A5C0F" LABEL="data" TYPE="ntfs" 
/dev/sda1: UUID="2A4C7A954C7A5C0F" LABEL="BACKUP250" TYPE="ntfs"
*************
```

---

### Post by Thingymebob on 2008-05-05
I don't think NTFS supports UUID so this is the default descriptor for NTFS, Ignore it, just don't mount by it

---

### Post by jeffus_il on 2008-05-05
You could use /dev/sdc1 and /dev/sda1 in your /etc/fstab file instead of mounting by UUID. there are ways of fixing the UUID as well.

---

### Post by -random on 2008-05-05
I'm mounting them by /dev/sd... atm thnkx,

i can mount both with ease in gutsy, but not with the hardy gui, and this is definitely bcoz of the uuid (b4 the uuid change i could)..

how do i change a uuid of a ntfs disc without losing the data on it?

---

### Post by Oldsoldier2003 on 2008-05-05
doing some research, i thought i had an answer but its not what I thought...

---

### Post by -random on 2008-05-05
least i know your on top of it :)

love your sig btw!!

---

### Post by Oldsoldier2003 on 2008-05-05
Try the solution posed here.
[http://ubuntuforums.org/showthread.php?t=479047](http://ubuntuforums.org/showthread.php?t=479047)
 its not exactly the situation you are in but it shows how to change the UUID of a disk without formatting and also covers fixing the fstab and grub (if required) to reflect the changes

---

### Post by linfidel on 2008-05-05
> **-random said:**
> I'm mounting them by /dev/sd... atm thnkx,

i can mount both with ease in gutsy, but not with the hardy gui, and this is definitely bcoz of the uuid (b4 the uuid change i could)..

how do i change a uuid of a ntfs disc without losing the data on it?
I had duplicate UUIDs at one time, but not with NTFS.  I used "tune2fs -U random device" to generate a new random UUID for one of the drives, and that worked fine.  You could try it with the NTFS drive.  Or, you could change the other one, and update the new UUID where it's referenced, like fstab, etc.

I'm not at my system, so this is from memory - I think I wrote it down in my notebook at home.  I won't swear that I didn't use mk2fs, as the above referenced article stated, but I can't even find anything about that command anywhere.

---

### Post by -random on 2008-05-05
wjhaaaaa!

```
zzz@64BiTuBuNtU:~$ mk2fs
bash: mk2fs: command not found
zzz@64BiTuBuNtU:~$ mk2fs -U random /dev/sda1
bash: mk2fs: command not found
zzz@64BiTuBuNtU:~$ man mk2fs
No manual entry for mk2fs
****
zzz@64BiTuBuNtU:~$ mke2fs -U random /dev/sda1
mke2fs: invalid option -- U
Usage: mke2fs [-c|-t|-l filename] [-b block-size] [-f fragment-size]
        [-i bytes-per-inode] [-I inode-size] [-j] [-J journal-options]
        [-N number-of-inodes] [-m reserved-blocks-percentage] [-o creator-os]
        [-g blocks-per-group] [-L volume-label] [-M last-mounted-directory]
        [-O feature[,...]] [-r fs-revision] [-R options] [-qvSV]
        device [blocks-count]
***
zzz@64BiTuBuNtU:~$ sudo tune2fs -U hello_kittyBACKUP250 /dev/sda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
zzz@64BiTuBuNtU:~$ sudo tune2fs -U random /dev/sda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.


```



how now brown cow?

also looked for in in synaptic, to no avail.

---

### Post by vanadium on 2008-05-05
If you do not succeed in changing the UUID of the ntfs drive, you might instead use the volume label to mount the disk. Obviously then, you must make sure that no other disk has the same label.

---

### Post by linfidel on 2008-05-05
> **-random said:**
> wjhaaaaa!

```
zzz@64BiTuBuNtU:~$ mk2fs
bash: mk2fs: command not found
zzz@64BiTuBuNtU:~$ mk2fs -U random /dev/sda1
bash: mk2fs: command not found
zzz@64BiTuBuNtU:~$ man mk2fs
No manual entry for mk2fs
****
zzz@64BiTuBuNtU:~$ mke2fs -U random /dev/sda1
mke2fs: invalid option -- U
Usage: mke2fs [-c|-t|-l filename] [-b block-size] [-f fragment-size]
        [-i bytes-per-inode] [-I inode-size] [-j] [-J journal-options]
        [-N number-of-inodes] [-m reserved-blocks-percentage] [-o creator-os]
        [-g blocks-per-group] [-L volume-label] [-M last-mounted-directory]
        [-O feature[,...]] [-r fs-revision] [-R options] [-qvSV]
        device [blocks-count]
***
zzz@64BiTuBuNtU:~$ sudo tune2fs -U hello_kittyBACKUP250 /dev/sda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
zzz@64BiTuBuNtU:~$ sudo tune2fs -U random /dev/sda1
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.


```

how now brown cow?

also looked for in in synaptic, to no avail.
Are you really sure you can't mount it using the /dev/sda1 type of notation?  Seems like I have mounts in Hardy that still work without using the UUID.  I won't swear I've checked them since upgrading, but I think I have.

---

### Post by -random on 2008-05-06
I'm in gutsy now.. but i'll check asap!

I think i only have problem mounting both graphically, but ye I can mount both in the terminal so it's kewl.

> **vanadium said:**
> If you do not succeed in changing the UUID of the ntfs drive, you might instead use the volume label to mount the disk. Obviously then, you must make sure that no other disk has the same label.

do i just do it like this in /etc/fstab:

```
LABEL="backup_disk" /media/sdb2 ntfs defaults 0 2
```

?

---

### Post by vanadium on 2008-05-06
You can mount using either one of the tree methods: device name, UUID or label. The issue with device names is that with (modern) hardware, device names are not guaranteed to be the same on each boot. UUIDs and LABELS have the benefit of being persistent identifiers for a partition. UUIDS have the additional benefit of being highly unique: the chance of having the same UUID on two partitions is virtually zero (at least for ext3 volumes), except of course if you cloned a partition.

---

### Post by -random on 2008-05-06
sweeet. I'll mount my ntfs hdd's according 2 labels now.

consider this thread solved!! (someone plz? i'ts not in thread tools, has the policy changed or am i looking in the wrong places.. but how do you mark a thread solved?)

---

