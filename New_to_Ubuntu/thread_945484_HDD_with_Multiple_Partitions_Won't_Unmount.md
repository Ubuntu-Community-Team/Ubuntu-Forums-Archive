---
title: "HDD with Multiple Partitions Won't Unmount"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by punong_bisyonaryo on 2008-10-12
I'm running Xubuntu (I just installed xubuntu-desktop from Ubuntu, if that helps). When I plug in an HDD with 2 partitions, it mounts no problem. But when I unmount it, it unmounts for a second and comes back and gives an error. Along with that, it opens 2 windows of each partition, same behavior as when mounting. Is there a workaround for this?

I also want to report this as a bug, if one doesn't exist yet. But I'm not sure, is this a gnome bug or what?

PS. I used to have this problem in Ubuntu Edgy and earlier I think. But it has since been resolved by newer Ubuntu versions.

---

### Post by Delvien on 2008-10-12
> **punong_bisyonaryo said:**
> I'm running Xubuntu (I just installed xubuntu-desktop from Ubuntu, if that helps). When I plug in an HDD with 2 partitions, it mounts no problem. But when I unmount it, it unmounts for a second and comes back and gives an error. Along with that, it opens 2 windows of each partition, same behavior as when mounting. Is there a workaround for this?

I also want to report this as a bug, if one doesn't exist yet. But I'm not sure, is this a gnome bug or what?

PS. I used to have this problem in Ubuntu Edgy and earlier I think. But it has since been resolved by newer Ubuntu versions.

partitions are tough, try unmounting them manually.

Command is "sudo umount /path/to/folder" (doesnt have to be /dev/hardware)

---

### Post by punong_bisyonaryo on 2008-10-12
Well... sudo umount didn't give any errors, but the drives didn't unmount either. Hmm...

---

