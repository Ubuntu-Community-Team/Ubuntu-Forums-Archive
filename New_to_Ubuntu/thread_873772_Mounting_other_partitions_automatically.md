---
title: "Mounting other partitions automatically"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by pzs on 2008-07-29
How do I do this in Ubuntu? I just want to mount a different ubuntu install I have on another partition. I thought this would probably just be a /etc/fstab job, but it looks rather confusing:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=449b7567-56ec-4acf-9ef5-a32dd5485712 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=421b7680-f28d-45bd-843a-f849efb75ae5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by hyper_ch on 2008-07-29
you have to add them to /etc/fstab

What does look confusing about it?

---

### Post by pzs on 2008-07-29
I thought I needed to use those big UID numbers. As it turns out I don't.

Shouldn't there be a wizard for this? Maybe I'm just getting lazy.

---

### Post by hyper_ch on 2008-07-29
I think KDE has a wizard for it.... and UUID is nice if you keep changing the disks around (or if the system does this, like for me sda and sdc get switched upon every reboot.. no clue why...)

---

### Post by drs305 on 2008-07-29
I've just written a tutorial about a program that edits fstab for you. You might be interested in the "3 Minute Guide" Section.

It's in the tutorials section here: [GUI Fstab Editing with PySDM]("http://http://ubuntuforums.org/showthread.php?t=872197")

---

