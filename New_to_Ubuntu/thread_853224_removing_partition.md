---
title: "removing partition"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by carrarin on 2008-07-08
removing partition from a usb drive? how do i do it. 
there is nothing on the drive

---

### Post by bumanie on 2008-07-08
In terminal > sudo apt-get install gpartedUnmount the usb drive, then open the partition editor (System --> Administration --> Partition Editor) From there locate usb drive and delete old partitions and use the slider to extend one partition over the whole drive (if you don't want partitions) and then format to which format you want.

---

