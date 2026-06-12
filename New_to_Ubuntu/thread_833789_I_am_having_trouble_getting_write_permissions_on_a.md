---
title: "I am having trouble getting write permissions on a hard drive"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by simpleclosure on 2008-06-18
I'm having trouble just mounting the drive... i'm not so worried about the permissions ... yet.  When I go to open it, i get an error: 'unable to mount location' 'cannot mount file'
any ideas why?

---

### Post by iaculallad on 2008-06-18
Is the drive you're trying to mount included in your fstab file? Post any error that displays when you issue the command below on your terminal:

```
sudo mount -a
```

---

### Post by cdtech on 2008-06-18
Create a directory (/mnt/devicename). Then issue the command:
sudo mount -t ext3 /dev/sda1 /mnt/devicename

The sda1 is the dev/partition your trying to mount (which can be found using sudo fdisk -l). The -t is the file system type (ext3 for Linux - ntfs or vfat for windows).

Hope this helps.......

---

### Post by bodhi.zazen on 2008-06-18
> **simpleclosure said:**
> I'm having trouble just mounting the drive... i'm not so worried about the permissions ... yet.  When I go to open it, i get an error: 'unable to mount location' 'cannot mount file'
any ideas why?

can you post the exact command you used please ?

Otherwise we are just guessing.

---

