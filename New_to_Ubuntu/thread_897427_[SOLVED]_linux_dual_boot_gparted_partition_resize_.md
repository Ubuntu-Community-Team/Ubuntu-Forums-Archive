---
title: "[SOLVED] linux dual boot gparted partition resize question"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by LTFC2020 on 2008-08-22
hi
I am dual booting ubuntu and mint and want to increase the size of the mint partition
I inserted the ubuntu live CD and used that to shrink the ubuntu partition /dev/sda1
So far so good....
I was then left with and unallocated partition and my original mint partition (plus swap partitions)
The mint partition /dev/sda6 (I think its this one) is part of the /dev/sda2 partition and swap partitions.
As you can see from the screen shot these are all locked (except /dev/sda5) - I tried both the ubuntu and mint live cds but they are locked with both
So my question is how do I remove the unallocated partition and replace it with an extended mint partition?
and
Can I safely reduce the size of the /dev/sda5 linux swap partition? (although this is a secondary importance)
thanks for any input

---

### Post by Elfy on 2008-08-22
Boot the disc again - unmount swap - there is maybe an option if you right click the swap partition in the bottom pane if not do it from a terminal

```
sudo swapoff -a
```

---

### Post by Paqman on 2008-08-22
Yeah, the LiveCD does grab any swap partitions it finds, which is locking your extended partition. Gparted will let you "swapoff" from a right click, and you'll be good to go.

Btw, you don't need two swap partitions unless you're using hibernation, so you could take this opportunity to ditch one.

---

