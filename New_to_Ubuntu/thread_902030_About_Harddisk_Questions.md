---
title: "About Harddisk Questions"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Anjue on 2008-08-26
when I just installed new hard disk in the systems. 
I want to know which HDDs are belong to /dev/sd* or /dev/hd*.

Any script ,commands, or any usually methods about it?

---

### Post by tamoneya on 2008-08-26
im not exactly sure what you are asking since it was phrased a little odd so this is a stab in the dark.  Try these commands and see if you get the info you want:```
sudo fdisk -l
mount
```

---

### Post by wolfen69 on 2008-08-26
i'm also not quite sure about the real question here, but i'll chime in with this: if you are adding a hardrive formatted as ntfs or fat32, they will be automatically mounted and user will be the owner of it. but if it is an linux formatted drive (ext3, ext2, jfs, zfs, reiser fs, etc) you will have to create a mount point and edit fstab. you will also have to get ownership of it. hope this helps.

---

### Post by Anjue on 2008-08-27
sorry guys,

It's my fault. I edited my questions right now. Thank you.

---

### Post by mcduck on 2008-08-27
> **Anjue said:**
> when I just installed new hard disk in the systems. 
I want to know which HDDs are belong to /dev/sd* or /dev/hd*.

Any script ,commands, or any usually methods about it?

Most likely they are _all_ named as /dev/sd*, since the same driver is now being used for both PATA & SATA/SCSI drives..

But yeah, "sudo fdisk -l" will give you the answer. :)

---

### Post by tamoneya on 2008-08-27
> **Anjue said:**
> sorry guys,

It's my fault. I edited my questions right now. Thank you.

Im still a little confused but post the output of the commands I listed earlier and we can tell you what they mean then hopefully we will come to a conclusion.

---

### Post by knattlhuber on 2008-08-27
If you prefer a GUI, you can used GParted, the Gnome Partition Editor. Can't remember if it's pre-installed. You would find it under System > Administration > Partition Editor or in the repos.
GParted has a drop-down menu in the right top corner that allows you to choose the device you are interested in.

---

