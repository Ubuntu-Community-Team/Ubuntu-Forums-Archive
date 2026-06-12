---
title: "4 GB flash drive shows up as 884 MB volume"
date: 2016-06-27
forum: New to Ubuntu
---

### Post by rdb3 on 2016-06-27
Ubuntu 16.04 here.

Is there a way that I can restore this flash drive back to its full 4 GB capacity?

When I do Disks and click on 4.0 GB Thumb Drive, it shows:

Partition 1
884 MB FAT   and     Free Space 3.1 GB

I don't know what to do next to make this a 4 GB volume.

Please help.

---

### Post by X-RED_Tech on 2016-06-27
What about removing that partition and creating a new one using all the space?
PS - The drive shows exactly what it has, a 884MB partition and the remaining space free (unallocated).

---

### Post by rdb3 on 2016-06-27
Thank you.  That's just what I did using gparted.  Then I did a format on the flash drive as FAT 32.

What I actually did was:

Unmount Partition 1 > re-sized it to max > click check mark & apply > format to FAT 32 > Restart the pc.

---

