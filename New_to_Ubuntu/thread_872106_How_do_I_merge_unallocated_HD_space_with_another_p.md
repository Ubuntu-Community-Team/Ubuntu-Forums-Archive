---
title: "How do I merge unallocated HD space with another partition with Gparted?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by erans on 2008-07-27
I tried doing this booting from the Ubuntu live CD but couldn't find an option w/ Gparted to merge unallocated space with my NTFS partition. Anyone know the procedure?

---

### Post by lisati on 2008-07-27
If the NTFS partition is next to the free space, the "resize" option will probably be the easiest.

---

### Post by erans on 2008-07-27
I don't think the unallocated space is next to the NTFS partition, nor could I find a resize option.

---

### Post by zipperback on 2008-07-27
> **erans said:**
> I don't think the unallocated space is next to the NTFS partition, nor could I find a resize option.


The unallocated freespace must be next to the partition you wish to resize.

If you don't have gparted installed you can install it with:

```

sudo apt-get update && sudo apt-get install gparted

```


Once it is installed you can access it with:


```


System -> Administration -> Partition Editor


```

[IMG]http://i257.photobucket.com/albums/hh216/zipperback1234/Screenshot-Desktop.png[/IMG]




In gparted, just click on the partition you want to resize or move and then **Partition -> Resize/Move** should allow you to move it. You cannot resize or move a partition which is currently mounted.



- zipperback

---

### Post by pi.boy.travis on 2008-07-27
I believe that when you resize a partition, the UUID changes.

BTW Learned that the hard way first time resized my swap.

---

