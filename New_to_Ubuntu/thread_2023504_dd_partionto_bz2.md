---
title: "dd partionto bz2"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by lance bermudez on 2012-07-12
I have a computer with 2 partions on 1 hard drive.  I have sda1 for os and sdb1 for backups. Would like to know if I should use .iso or .img and I would also like to know if I have the right commands. Can not use clonezilla for this.

to make backup of sda1
dd if=/dev/sda1 | bzip2 -9 >/media/sdb1/sda1-partion-image.iso.bz2

to restore
bzip2 -cd /media/sdb1/sda1-partion-image.iso.bz2 | dd of=/dev/sda1

---

### Post by O2Blevel on 2012-07-12
Your commands look good to me, but I found bz2 to be considerably slower than gz. I don't know what your requirements are, you may want to perform a quick test for speed, bz2 will give better compression.

---

### Post by mapes12 on 2012-07-13
sda and sdb tells me you have 2 HDD's but your post states 1? If your objective is to make a complete backup of your OS system then take a look at Remastersys.

---

### Post by sudodus on 2012-07-13
> **lance bermudez said:**
> I have a computer with 2 partions on 1 hard drive.  I have sda1 for os and sdb1 for backups. Would like to know if I should use .iso or .img and I would also like to know if I have the right commands. [COLOR="Red"]Can not use clonezilla for this.[/COLOR]

to make backup of sda1
dd if=/dev/sda1 | bzip2 -9 >/media/sdb1/sda1-partion-image.iso.bz2

to restore
bzip2 -cd /media/sdb1/sda1-partion-image.iso.bz2 | dd of=/dev/sda1
Why can't you use Clonezilla for that? Is it necessary to get maximum compression? I think ***Clonezilla*** is much safer than ***dd***. (I use both, but for different tasks.) Clonezilla (the default mode using ***Partclone***) backs up only what is needed (not free space), which makes it much faster than dd. You can combine cloning with Clonezilla and compression with bzip2. See the attached picture (from this link) [[COLOR="Red"]_http://clonezilla.org/clonezilla-live/doc/01_Save_disk_image/advanced/09-advanced-param.php_[/COLOR]]("http://clonezilla.org/clonezilla-live/doc/01_Save_disk_image/advanced/09-advanced-param.php")

It can make clones and or images. And you should use neither dd nor clonezilla to make a  backup/clone/image of a mounted drive (for example the root file system /).

I suggest that you boot from another drive (for example a live CD or USB drive), but it is possible to run from another partition on the same drive (if you have more than one on each drive).

You can use whatever name of the image file that you like, but it helps to use a name (and extension) that helps you remember what file it is.

     -o-

By the way, backup of a data partition is another story, particularly if there are many (well compressed) picture files and video files. It is much more efficient to use ***rsync*** maybe with some graphical user interface.

---

