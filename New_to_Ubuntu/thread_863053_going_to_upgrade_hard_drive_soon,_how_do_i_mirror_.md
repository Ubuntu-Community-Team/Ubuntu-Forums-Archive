---
title: "going to upgrade hard drive soon, how do i mirror data to new one???"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by stinger30au on 2008-07-18
in the not to distant future i want to upgrade my 80 gig drives with some 250 gig drives.
i have 3 x 80 gig drives.

im quite happy to do one drive at a time and mirror each entire drive to a new 250 gig drive and was hoping there might be a live linux cd that will copy the drive across similar to ghost or true image.

anyone had any experience with this???

---

### Post by hyper_ch on 2008-07-18
well, for the drive containing the boot folder and mbr with grub I'd

start with the livecd and run
```

sudo dd if=/dev/sdX of=/dev/sdY

```
sdX = 80gb drive
sdY = 250gb drive

that should make a 1:1 copy of it. Then try to boot from the 250 gb drive. If that works, use then gparted to enlarge the partition(s).

Once that done, I'd rsync the other two drives onto 250gb one.

---

