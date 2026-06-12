---
title: "where did grub go :(?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by spectre_hfx on 2008-05-04
.

---

### Post by Dark Aspect on 2008-05-04
> **spectre_hfx said:**
> Hi, i have hardy 64 bit.  I had 3 ext3 partitions, and one swap.  I had some space leftover i wanted to use for windows xp for gaming.  One of the ext3 was in an extended partition along with the free space.  I put in the windows cd, and it read all of them, and then i created a partition with the free space.  It wasnt able to install on it for some reason (i guess it doesnt support extended partitions or something?) Anyway. now whenever i turn my comp on, i get a message saying there is no boot media, restart or insert boot media and hit any key. 

so here are my questions:

a) How can i fix this?
b) is there any way to install windows on a 5th partition?
c) Is a swap partition necessary? I have 4 gigs of ram, and if a swap isnt necessary id like to delete it.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

Super Grub should be able to recover your grub loader.As for the swap I would still keep it since it could add stability,though you could probably delete it without much trouble. 

After you load super Grub the windows side may not be listed in your grub menu.You have to add it manually in the /boot/grub/menu.lst.

---

### Post by spectre_hfx on 2008-05-04
.

---

