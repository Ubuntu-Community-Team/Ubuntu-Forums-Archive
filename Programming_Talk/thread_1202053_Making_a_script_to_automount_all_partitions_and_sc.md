---
title: "Making a script to automount all partitions and scan them (with linux antivirus)"
date: 2009-07-01
forum: Programming Talk
---

### Post by pythonscript on 2009-07-01
I'm making a custom ubuntu 9.04 live cd with three antivirus programs built in (clamav, avg, and bitdefender). Overkill, I'm sure, but I'm experimenting with this. I want to make a shell script that integrates the scanning from all three of these programs into one script, and my question is thus:  How can I make a shell script that will mount every partition on the main computer (not the live cd) into /mnt? For example, if the computer has two hard disks, with two partitions each, the script will mount them as /mnt/sda1, /mnt/sda2, /mnt/sdb1, /mnt/sdb2, etc. Thanks in advance!

---

### Post by Idefix82 on 2009-07-02
The command for mounting a device is
```
mount
```

You need to create the folder where you want to mount the device before you can mount it there. So for example if sda1 is formatted as ext3 then you can do
```
sudo mkdir /mnt/sda1
mount -t ext3 /dev/sda1 /mnt/sda1
```

See
```
man mount
```
for more options.

---

### Post by pythonscript on 2009-07-02
I'm familiar with the commands to mount a partition, but the mount documentation doesn't really give me any idea as how to iterate through all the partitions on a system, regardless of the number of disks, etc. The disks/partitions I talked about earlier were just an example; this is a live CD, so it could be run on a computer with a wide variety of disks and partitions.

---

### Post by decoherence on 2009-07-02
So basically, you want to see what drives/partitions are attached to the system, mount each one, scan it, unmount it, mount the next, scan it, etc.?

First you need a list of recognized partitions. I've never had to do this before for a script, and there might be a better way, but the following seems like it might do the trick

```
awk '{print $4}' /proc/partitions | sed -e '/name/d' -e '/^$/d' -e '/[1-9]/!d'
```

You'd take the output of that and use it in a for loop. Here is some code that absolutely will not work, but serves as a skeleton.

```
#!/bin/bash

TARGET_PARTITIONS=$(awk '{print $4}' /proc/partitions | sed -e '/name/d' -e '/^$/d' -e '/[1-9]/!d')

for i in $TARGET_PARTITIONS
do mount /dev/$i /mnt && echo "successfully mounted $i!"
echo "Virus scanning happens now." && sleep 2
umount /mnt && echo "unmounted!"
done

```

By running this code you can see that you'd have to put in exception handling for swap and any currently mounted filesystems (which would be the ones on your liveCD.... probably always starts with "sda" so easy to filter out) and any filesystems whose type can't be recognized.

hth

---

