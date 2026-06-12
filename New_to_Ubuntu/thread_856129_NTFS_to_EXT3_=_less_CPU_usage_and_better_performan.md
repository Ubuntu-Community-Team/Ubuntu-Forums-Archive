---
title: "NTFS to EXT3 = less CPU usage and better performance??"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Thee_Baron_ on 2008-07-11
Hello, when playing about with conky I noticed high CPU usage with a thing called mount.NTFS - which doesnt appear in gnome-system-monitor (or whatever its called)

So would converting my "data-only" harddrives to ext3 give better system performance? 

Thanks!

---

### Post by hyper_ch on 2008-07-11
I think it would

---

### Post by tjwoosta on 2008-07-11
me too

---

### Post by MasterProg on 2008-07-11
I heard that XFS and RaiserFS are a way faster than EXT3. If you want even better performance, try one of them.

---

### Post by hyper_ch on 2008-07-11
as ext3 is a native linux fs and ntfs isn't...

> **MasterProg said:**
> I heard that XFS and RaiserFS are a way faster than EXT3. If you want even better performance, try one of them.
It pretty much depends on what yuo want to do... each fs has it's strengths and weaknesses...

---

### Post by Thee_Baron_ on 2008-07-11
:) So should I use GParted or is there something better? I need to be able to use the free space then transfer the files from the NTFS partition to EXT3 partition and resize the EXT3 partition to the full size of the HDD

---

### Post by hyper_ch on 2008-07-11
gparted is fine for that :) is the ntfs made with vista? If so, use the vista parttiioner to resize that partition.

Btw, here's a comparision between different linux fs: [http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388)

---

### Post by Canis familiaris on 2008-07-11
> **hyper_ch said:**
> gparted is fine for that :) is the ntfs made with vista? If so, use the vista parttiioner to resize that partition.

What is the difference b/w NTFS for XP and Vista?

---

### Post by hyper_ch on 2008-07-11
dunno ;) never used vista - but everywhere it is recommended to use the vista partitioner for vista ntfs partitions... well, it may mean to use vista's partitioner to resize the partition upon which vista is installed...

---

### Post by Thee_Baron_ on 2008-07-11
Its a XP NTFS partition. I think I'm going to go for XFS, seem the best overall.

---

### Post by hyper_ch on 2008-07-11
then use gparted - but remember to make a backup first of your important data... although resizing works very, very, very often there's still a small chance you can hose it...

---

