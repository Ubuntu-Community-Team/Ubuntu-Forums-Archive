---
title: "[SOLVED] Need to change or link /home to another mounted partition"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by bumanie on 2008-07-04
I need to change /home on /dev/sdb1 to /media/home on sdb2 (already mounted in /etc/fstab). I am running virtualbox from the /home on sdb1 and the virtual hdd's are taking up too much room. Am happy to mv virtualbox only if someone knows how.

---

### Post by Elfy on 2008-07-04
You can clone your harddrive images, I've never done it myself but it is documented in the vbox manual - I've had a quick look at my one and it looks simple enough. The new cloned drive can then be used by vbox - I gues you could try it out and make sure before you use the new and delete the old - that sounds a bit rtfm, but I really don't mean it too :) . If you aren't too sure - I can try with mine for you as mine's not critical - let me know.

Last year I used the psychocat page on moving my /home without problems - it is for a new /home but you can just change it to suit your situation I assume.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by bumanie on 2008-07-04
> Last year I used the psychocat page on moving my /home without problems - it is for a new /home but you can just change it to suit your situation I assume. I know of that tutorial - my issue was adapting it to my needs. Unfortunately I don't have enough room on /home to backup and that seems to rely on backing up /home, within /home that is later copied to the new /home and then once everything works removing the copy- guess I could back up else where (ie external drive) and go from there. I'll have a bit more of a think about it all before proceeding with anything.

---

### Post by jw5801 on 2008-07-04
If you just want to copy the virtual box images, you could copy the .VirtualBox folder from your home directory to the other partition and then symlink it back.
```
mv ~/.VirtualBox /media/home/VirtualBox
#you can call it whatever you'd like, I've made it not hidden here, but it's up to you
ln -sv /media/home/VirtualBox ~/.VirtualBox
```

---

### Post by bumanie on 2008-07-04
jw5801 thanks for that. I can't try it just now as I am a friend's house, but I was thinking about a symlink, but didn't know the commands adequately enough. I'll let you know how it goes later, but I think a symlink is the way to go.

---

### Post by Elfy on 2008-07-04
I'm not too convinced that copying the drive is such a good idea - I could be wrong but this what the manual has to say - 

> Note: Do not simply make copies of virtual disk images. If you import such
a second copy into a virtual machine, VirtualBox will complain with an error,
since VirtualBox assigns a unique identifier (UUID) to each disk image to
make sure it is only used once. See chapter 5.3, Cloning disk images, page 65 for instructions on this matter.

> You can duplicate hard disk image files on the same host to quickly produce a second virtual machine with the same operating system setup. However, you should only make copies of virtual disk images using the utility supplied with VirtualBox; see chapter 8.14, VBoxManage clonevdi, page 110. This is because VirtualBox assigns a unique identity number (UUID) to each disk image, which is also stored inside the image, and
VirtualBox will refuse to work with two images that use the same number. If you do accidentally try to reimport a disk image which you copied normally, you can make a second copy using VirtualBox&#8217;s utility and import that instead.
   Note that newer Linux distributions identify the boot hard disk from the ID of the drive. The ID VirtualBox reports for a drive is determined from the UUID of the virtual disk image. So if you clone a disk image and try to boot the copied image the guest might not be able to determine its own boot disk as the UUID changed. In this case you have to adapt the disk ID in your boot loader script (for example /boot/grub/menu.lst). The disk ID looks like
scsi-SATA_VBOX_HARDDISK_VB5cfdb1e2-c251e503.

The ID for the copied
image can be determined with 
hdparm -i /dev/sda


Finally the clonevdi

> This command duplicates a registered virtual hard disk image to a new image file with a new unique identifier (UUID). The new image can be transferred to another host system or imported into VirtualBox again using the Virtual Disk Manager; see chapter
3.5, The Virtual Disk Manager, page 39 and chapter 5.3, Cloning disk images, page 65.

---

### Post by jw5801 on 2008-07-04
> **forestpixie said:**
> I'm not too convinced that copying the drive is such a good idea - I could be wrong but this what the manual has to say

I don't think it'll be an issue. After all we're copying the disk image, not the drive itself. Something akin to removing a physical hard drive and shifting it to a new location, as opposed to copying a filesystem from one location to another. It's still going to remain exactly the same file. That manual entry is actually warning against precisely the opposite thing, in that if you make a copy of the image, it will be exactly the same (have the same UUID), so if you attempt to then import the copy of the drive into VirtualBox, it will see two drives with the same UUID, hence erroring. Moving the virtual drive to a new location shouldn't cause any problems.

---

### Post by Elfy on 2008-07-04
Yea - bumanie pm'd me as well - as I'm not too sure about the whole symlink thing I just put that there as a 'make sure' really.

Better to have too much than not enough some times, as it is bumanie had already done so previously :)

---

### Post by bumanie on 2008-07-04
That worked a treat. Thanks again jw5801. There was actually about 13g on virtualbox. I tested it; works fine and now /home on sdb1 has heaps of room. I made an ample / partition for testing on vbox. Didn't realise it would take up so much room.
I had a suspicion that mv and symlink may work - almost got the mv right, but had no idea about the symlink syntax - jw5801, you must teach me sometime!

---

### Post by cariboo on 2008-07-04
Open up a terminal and enter:

```
man symlink
```

and

```
man ln
```

Jim

---

