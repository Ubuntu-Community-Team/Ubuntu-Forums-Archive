---
title: "SSD Upgrade..."
date: 2012-03-14
forum: New to Ubuntu
---

### Post by Jancarel on 2012-03-14
Dear Ubuntu Friends,

I would like to upgrade my computer with a Solid State Disk. My idea is to use CloneZilla to make a disk image of the present harddisk. Then replace the harddisk with a Solid State Disk and restore the disk image back to the new disk. Two questions:

- Will this work...
- Do I need to format the SSD before the restore, or will 
  CloneZilla do this for me...

Thank you for your help,

Jan

---

### Post by howefield on 2012-03-14
No reason why it shouldn't work unless the SSD is smaller than the disk that the image was taken from ?

I believe this is still a limitation of Clonezilla, the destination has to be of at least the same size as the source.

I'd probably be inclined to do a fresh install, just to keep the cruft off the SSD, at least to start with.

---

### Post by Grenage on 2012-03-14
Indeed; you could shrink the partition first with Gparted, if it was indeed bigger than the destination.   I'd perform a fresh install, but the option is there.

---

### Post by Jancarel on 2012-03-14
> **howefield said:**
> No reason why it shouldn't work unless the SSD is smaller than the disk that the image was taken from ?

I believe this is still a limitation of Clonezilla, the destination has to be of at least the same size as the source.

I'd probably be inclined to do a fresh install, just to keep the cruft off the SSD, at least to start with.

I am still using Ubuntu 10.10. This is the latest version which works with my graphic card. With a newer version I could not get my graphic card to work. I am perfectly happy with 10.10. That's why I would like to copy this complete setup to the new SSD...

Jan

---

### Post by howefield on 2012-03-14
> **Jancarel said:**
> I am still using Ubuntu 10.10. This is the latest version which works with my graphic card. With a newer version I could not get my graphic card to work. I am perfectly happy with 10.10. That's why I would like to copy this complete setup to the new SSD...

Jan

Uhmm.. ok but if you mention that as a reason not to do a clean install of 10.10 I'm not sure why that would be the case.

---

### Post by Ghost_Mazal on 2012-03-14
I had this issue a while back and found that the rsync method works flawlessly. It is the fastest and safest way to clone to a smaller drive as you don't need to do any partition resizing and it only copies the data not every sector.
 
I battled with this for more than a week and there is no other way to clone to a smaller drive. 1. Partition resizing and clonezilla (dangerous) , 2. Rsync. (Safer but needs some editing of config files when done)

---

### Post by Grenage on 2012-03-14
That's not a clone, that's just copying files.

---

### Post by Ghost_Mazal on 2012-03-14
> **Grenage said:**
> That's not a clone, that's just copying files.
 
I regularly clone harddrives that way my friend. When done you just install grub , edit fstab , edit grub.cfg and your done. Best and safest way to clone to smaller drive.

---

### Post by Grenage on 2012-03-14
As I said, that's not cloning a drive. ;)

---

### Post by Ghost_Mazal on 2012-03-14
> **Grenage said:**
> As I said, that's not cloning a drive. ;)
 
As it is an exact copy of the original system , yes it is.
 
BUT , if you guys wonna struggle with slow and dangerous partition resizing , knock yourselves out ;)

---

### Post by Grenage on 2012-03-14
> **Ghost_Mazal said:**
> As it is an exact copy of the original system , yes it is.

But it's not!

A [clone]("http://en.wikipedia.org/wiki/Disk_image") is an exact copy, anything else is just transferred files.

---

### Post by Jancarel on 2012-03-14
> **howefield said:**
> Uhmm.. ok but if you mention that as a reason not to do a clean install of 10.10 I'm not sure why that would be the case.

Well, I have installed quite a few programs. With some I had difficulties getting them to work correctly. All this has to be done again if I do a clean install. At the moment my computer works perfectly and I am totally happy with the way it works. An SSD would make it even nicer since it will be faster and quiet...

Jan

---

