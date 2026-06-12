---
title: "Adding to NTFS"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-08-12
well guys i deleted my GRUB and i deleted my ubuntu partion

so how do i add back to my NTFS partion because when i deleted ubuntu that partion just says 268 gigs of free space and if i write click my NTFS partion there is: open, explore, change drive letter and paths, shrink volume, properties, and help options what one should i use?

---

### Post by null byte on 2008-08-12
> **mr-Kirch said:**
> well guys i deleted my GRUB and i deleted my ubuntu partion

so how do i add back to my NTFS partion because when i deleted ubuntu that partion just says 268 gigs of free space and if i write click my NTFS partion there is: open, explore, change drive letter and paths, shrink volume, properties, and help options what one should i use?
Use Partition Magic 8 to resize it. Make sure to make a backup!

---

### Post by mr-Kirch on 2008-08-12
is there a way without spending 
$69.95

---

### Post by sandysandy on 2008-08-12
use gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

here is a link to gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by mr-Kirch on 2008-08-12
> **sandysandy said:**
> use gparted

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

here is a link to gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

does gparted come on ubuntu live cd?

---

### Post by sandysandy on 2008-08-12
> **mr-Kirch said:**
> does gparted come on ubuntu live cd?

it does.

---

### Post by mr-Kirch on 2008-08-12
> **sandysandy said:**
> it does.

k

---

### Post by LowSky on 2008-08-12
I assume you have Windows on that NTFS patition, if you do Right click on My Computer icon, go to manage disk drives. You can add, delete, and resize partions from there. People always assume Windows doesn't have any of these tools.

---

### Post by mr-Kirch on 2008-08-12
how do i get to gparted on the live cd?

---

### Post by mlentink on 2008-08-12
> **mr-Kirch said:**
> how do i get to gparted on the live cd?

Please see also LowSky's remark.
GParted is under System>Administration>Partition Editor
Not sure about the exact name, since I use a localized version, but it should be something like that

---

### Post by mr-Kirch on 2008-08-12
[http://s276.photobucket.com/albums/kk36/teh_leetzor/?action=view&current=Screenshot--dev-sda-GParted.png](http://s276.photobucket.com/albums/kk36/teh_leetzor/?action=view&current=Screenshot--dev-sda-GParted.png)

wont let me do anything with my free space

---

### Post by mr-Kirch on 2008-08-12
well i officially am done but i cant get crap in my c: drive i just have an extra drive (f drive) and it has 200 something gigs is that gonna work?

---

### Post by bumanie on 2008-08-12
The problem you are having with the unallocated space is that it is contained within a logical partition (the light blue rectangle). If you remove the logical partition you will then be able to format the space to ntfs and add it to vista if you  wish, or leave it as a dedicated storage area.

---

### Post by mlentink on 2008-08-12
Also, please make sure that any partition you are performing operations on (like shrinking or enlarging) ***must not currently be mounted***. Please unmount all those partitions first, otherwise GParted will not let you do anything with them

You can also safely delete the remaining linux-swap partition, as it will not do anything further for you

---

