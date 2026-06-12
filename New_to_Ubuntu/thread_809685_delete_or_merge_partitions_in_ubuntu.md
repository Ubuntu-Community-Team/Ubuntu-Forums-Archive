---
title: "delete or merge partitions in ubuntu"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by roflatlife on 2008-05-27
hey guys
im running ubuntu 8.04 now and i installed windows xp on virtualbox and it works like a charm.
im dualbooting between ubuntu and windows vista and i want to get rid of windows vista. is there anyway to format my vista partition in ubuntu and then merge it with my ubuntu partition?
thanks =D

---

### Post by eriqjaffe on 2008-05-27
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You can also do it from the Ubuntu LiveCD, but I don't see the point in booting an entire Desktop OS for one task.  ;)

---

### Post by sayakb on 2008-05-27
No need for the gparted liveCD. Just install gparted in Ubuntu
```
sudo apt-get install gparted
```
And delete the Vista partition. Do not create a new one, and select "Extend" with the Ubuntu partition.
Also, edit the /boot/grub/menu.lst file to remove the "Vista/Longhorn loader" entry.

---

### Post by civillian on 2008-05-27
My advice would just be to use the ubuntu liveCD, since you already have one since youre using ubuntu and doesnt require any extra downloading!
Although it would take longer to boot, i think the pros outweigh the one con ;)

---

### Post by fluffman86 on 2008-05-27
the gparted download is less than 50mb, and it's pretty much guarenteed to work.  I've had trouble resizing partitions with the ubuntu cd, especially on older systems.  gparted seems faster, too.

---

### Post by forestpixie on 2008-05-27
> select "Extend" with the Ubuntu partition.That is only possible if you can unmount the partition you wish to extend - if the op wants to extend the existing ubuntu partition they will have to be unmounted - hence the need for the livecd in one form or another - (or even to use partedmagic instead)

I have had problems with some gparted versions.

Edit - > the gparted download is less than 50mb... 

+1

---

### Post by sayakb on 2008-05-27
> **forestpixie said:**
> That is only possible if you can unmount the partition you wish to extend - if the op wants to extend the existing ubuntu partition they will have to be unmounted - hence the need for the livecd in one form or another - (or even to use partedmagic instead)

Okay.. right.. got it! ;)

---

### Post by Duck2006 on 2008-05-27
Or you can use parted magic to do it with.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Some reading on partitioning.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)

---

### Post by forestpixie on 2008-05-27
> **Duck2006 said:**
> Or you can use parted magic to do it with.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Some reading on partitioning.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted)

I've been using that - I like being able to use firefox when in there

---

