---
title: "[SOLVED] merge ntfs and ext3"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by new Student on 2008-09-11
i need to merge two partitions one partition is ext3

and the other is NTFS 

can i do this ?

will it harm my beloved ubuntu ?

---

### Post by jerome1232 on 2008-09-11
Well first whenever you play with partitions backup data, in case something gets screwed up.

You would have to delete the ntfs partition (losing all data on it) and grow the ext3 partition into the now free space. Partitions can only be grown towards the end of the drive so if the ext3 partition was after the ntfs partition you would have to move the ext3 partition to the begining of the drive then grow it.

---

### Post by new Student on 2008-09-11
well i should have asked how i can do this ?

thanx

and now u mention something that look great 

how i can move the "\" partition to the begining of the drive ?

---

### Post by kjohansen on 2008-09-11
you will need to use gparted.  you can only use gparted on drives that are unmounted, so if this is your booting harddrive you are talking about you will need to boot from the liveCD.

To run gparted

```

sudo gparted

```

To reiterate the previous advice BACKUP EVERYTHING before playing with partitions.

---

