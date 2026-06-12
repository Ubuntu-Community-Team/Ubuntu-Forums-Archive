---
title: "Help: reading and writing external HD"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by lazydesi on 2008-05-09
Hi,

I recently formatted my 160 External HD in ubuntu 8.04 (i am not sure exactly which format i formatted the HD in Ubuntu), but i used Gpartition.

now i am trying to read or copy some files from external HD using VISTA.

It was not showing anything and after searching this forum , i installed Ext2fsd.

after installing Ext2fsd, external HD was showing as RAW hard drive, and no files are showing up
:confused::confused::confused::confused:

---

### Post by hotchkikr on 2008-05-09
you have to add it to your /etc/fstab

you shouldn't need any special drivers for it though

---

### Post by lazydesi on 2008-05-09
> **hotchkikr said:**
> you have to add it to your /etc/fstab

you shouldn't need any special drivers for it though

hey thanks for u r reply.

But how can we add in VISTA, I am currently using VISTA and trying to copy some files from Ubuntu formatted HD

---

### Post by lazydesi on 2008-05-09
still looking for the solution

---

### Post by logos34 on 2008-05-09
> **lazydesi said:**
> (i am not sure exactly which format i formatted the HD in Ubuntu), but i used Gpartition.

maybe you used something other than ext2/3 ?

Or try this:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by HunterThomson on 2008-05-09
It sounds like you formatted it to ext3 not ext2 so if you installed ext2 capability to your vi$ta OS then it would still not be able to read/write to the ext3 formatted Xharddrive.

If you ask me I would back up the data on the XternalHD and then go back into Gparted and ether format it to ext2 or FAT32. FAT32 is a format that both windows and Linux can read/write to. Then you will not have any problems and you will not have to mess around getting windows to work.

EDIT: ya I don't know about if you enabled vi$ta to read ext2 it can also read ext3... FAT32 will work grate for sure:)

---

