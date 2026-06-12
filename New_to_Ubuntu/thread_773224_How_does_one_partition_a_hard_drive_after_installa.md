---
title: "How does one partition a hard drive after installation?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by pjbrown88 on 2008-04-28
While I was setting up Hardy Heron on my desktop, I neglected to partition roughly 100 gigs of free space on one of my hard drives, and I can't seem to find a way to properly partition it.

If anyone has any suggestions on how I might make this free space into a new partition, or even better, find a way that I might be able to use it to extend the NTFS partition I have on that particular drive, that would be great.

---

### Post by Tatty on 2008-04-28
You cant alter your partitions while your hard disk is mounted so boot into a live CD then System->Administration->Partition Editor

:)

---

### Post by elmer_42 on 2008-04-28
I would recommend using the GParted LiveCD. It's like 60MiB and well worth the download. It is the best partitioner I have used.

---

### Post by jlbriggs on 2008-04-28
[gparted]("http://gparted.sourceforge.net/") will do this.

((d'oh! typed too slow...))

---

### Post by pjbrown88 on 2008-04-28
Thanks guys. For whatever reason, my update mirror was down, so I popped in the live CD, ran gParted, and everything's working fine now.

Thanks! :D

---

