---
title: "Bash easy backup script"
date: 2009-12-08
forum: Programming Talk
---

### Post by carlinuxlearner on 2009-12-08
What I'm trying to do: Create a script that finds a 500GB external hard drive, mounts it, creates a image of the main hard drive and places it on the external one.

My current script:
```

#!/bin/bash
command1=`sudo fdisk -l | grep 500.1`
command2=`cut -c 6-13 .asdfgh`
echo $command1 > .asdfgh
sudo umount $command2"1"
sudo mkdir /tmp/backup/
sudo mount $command2"1" /tmp/backup
sudo dd_rescue /dev/sda /tmp/backup/full_backup_`date +%m-%d-%y`.img
sudo umount $command2"1"
#rm .asdfgh

```

Problems with my current script: 

1. I have to create a file so I can get the part of the string I want. *"echo $command1 > .asdfgh"*

2. My *"rm .asdfgh"* breaks the script unless I comment it out. (and I really don't know why)

3. Over all I believe it's rather sloppy coding, and there is probably a much better why to do most of it.


So, what I'm asking for is this:
1. Advice on cleaning up the code/better ways to do it.
2. How I can take the output of a command and put it in a variable, or just how I can use *"cut"* to read a variable instead of a file.

---

### Post by scragar on 2009-12-08
OK, few quick points, if your disk has a label you can greatly reduce this work, since you can mount the disk by it's label, rather than size(which is risky).
You can probably reduce your code to just a few lines.
Things are easier with pipes.

For a partition called BACKUP we get:
```
#!/bin/bash

DEV=/dev/disk/by-label/BACKUP
TMP=/tmp/backup

sudo umount "$DEV"
sudo mkdir "$TMP"
sudo mount "$DEV" "$TMP"
sudo dd_rescue /dev/sda "$TMP/full_backup_$(date +%m-%d-%y).img"
sudo umount "$DEV"

```

EDITS:
Your writing to and using the file are in the wrong order, that's why deleting the file causing problems, because the file doesn't exist next time you try to read it.

Cut only works on files, it's not needed though, awk is probably much more powerful for your selection method.

If you don't want, or can't use labels for your partitions then by all means use UUIDs, they're harder to understand but just as easy to use.
```
DEV=/dev/disk/by-uuid/3b3df30f-2262-447f-ac7b-d1472ec5ebbe

```

---

### Post by carlinuxlearner on 2009-12-08
Well I don't think I can use the uuid, but maybe the label... because the application of this is going to be for a Live disk, to be used on multiple computers and multiple 500GB external drives. So I just give them a disk, they pop it in, click the backup script and it goes and finds their 500GB drive and backs up the main drive to it. I also plan on making it so (by passing some parameters) you can specify what it searches for, what drive to backup and the drive where the backup is to go.

so I guess I'm now going to look into awk. (thanks for the suggestion! :D)

---

### Post by scragar on 2009-12-08
OK, since you might not be able to use labels etc I thought up this edit:
```
DEV=$(sudo fdisk -l | awk '/500\.1/ { print $2 }' | tr -d ':' | head -n 1)
```
It's pretty simple, first fdisk runs like you've been using it, that's then piped into awk, which get's just the line with 500 on it, and returns the second space seperated value on the line(the device name with a colon), then I finally pipe this into tr in order to delete( -d ) any colons.
Just to be on the safe side I then further pipe this into head to return only the first line of the results, in case multiple partitions are selected.

---

