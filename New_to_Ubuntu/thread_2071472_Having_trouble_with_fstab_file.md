---
title: "Having trouble with fstab file"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by weatherscomputers on 2012-10-15
Hello I'm a noob linux user and am currently trying to learn through various books & tutorials. Problem I'm having is in a tutorial and forums search everyones fstab comes out nice and clean 

for me after running $ less /etc/fstab i get the following:

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
UUID=c1f74c8a-b4d3-4a04-93fd-bc2c96475b02 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=212582e5-fabb-416c-b803-7868fe45ce05 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
fstab (END)
```Do I have to read it like this everytime I want to check my fstab? or is the a way to align and also I can't tell if i'm getting errors here or not. Thanks in advance!

---

### Post by oldfred on 2012-10-15
Welcome to the forums.

You can also just list it:

 sudo cat /etc/fstab

Or you can open it 

gedit /etc/fstab

Or open for editing

gksu gedit /etc/fstab

If editing you may want to backup first.

sudo cp /etc/fstab /etc/fstab.backup

And if you have edited it and want to make sure it is ok before rebooting.

sudo mount -a

If it just returns then it is good, otherwise it will report errors.

---

### Post by weatherscomputers on 2012-10-15
Thanks for fast reply, I'm gonna go ahead and edit it, the huge UUID numbers I think that were throwing me off because the tutorials and other's posts fstab were showing up as dev/sda1

---

### Post by oldfred on 2012-10-15
That must be old info. 

UUIDs are used now as they change less or rarely. Where just installing another drive or having BIOS load a flash drive before the hard drive can change the drive numbering and make sda1 become sdb1 and booting fails.

---

### Post by weatherscomputers on 2012-10-15
Ahh yeah I just researched that. Thanks again for all the info!

---

