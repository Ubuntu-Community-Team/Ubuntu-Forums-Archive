---
title: "Partition &amp; Installtion 8.04"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by yo_pandabear on 2008-06-06
What I wanted was the OS on a 12 gb partition, my Home folder/files on the 194 gb, and the 40 gb for ISO backups & other backups.

Have partition 250 gb IDE as follows: (Only Ubuntu on this 250 gb drive.  No duel boot. All were partition & formated in order listed below.

12 gb   ext3 primary       root  install Ubuntu OS here
4 gb  swap file
40 gb   ext3 primary         (for backup's of OS, data, etc.)
194 gb  ext3 primary         Home, my documents


The OS & everything went to the 40 gb partition.  How do I direct or force this.  

A much better HD partition scheme would be appreciated.

This is the 2nd hard drive I have loaded Ubuntu on.  This stuff is great.

Can someone help a newbie.       Thanks.

---

### Post by spiderbatdad on 2008-06-06
I think a good idea is separate partitions for
/
/home
/tmp
/var
You can then set mount rules in fstab to protect your file system. This will require some research to do properly, but ultimately you would end up with a much more secure file system, and have greater control over access to that file system.

You can also look into the file: /etc/security/limits.conf

---

### Post by Duck2006 on 2008-06-06
You can use parted magic, or gparted, to may your partition be for you install. Then in the instal,l part4 of 7 use manual partition, and make your mount points to the partitions that you have made. If you got the system installed you can use one of the partitions tools, to move the partition as you want them (a lot of work).

---

### Post by yo_pandabear on 2008-06-06
> **spiderbatdad said:**
> I think a good idea is separate partitions for
/
/home
/tmp
/var
You can then set mount rules in fstab to protect your file system. This will require some research to do properly, but ultimately you would end up with a much more secure file system, and have greater control over access to that file system.

You can also look into the file: /etc/security/limits.conf

What size for root, home, tmp, var,

Thanks.

---

### Post by yo_pandabear on 2008-06-06
> **Duck2006 said:**
> You can use parted magic, or gparted, to may your partition be for you install. Then in the instal,l part4 of 7 use manual partition, and make your mount points to the partitions that you have made. If you got the system installed you can use one of the partitions tools, to move the partition as you want them (a lot of work).


Thanks, I will try this.

---

### Post by Duck2006 on 2008-06-06
/ 7Gb
/home 10Gb
the others i use the default one.
/ linux swap 1Gb

---

