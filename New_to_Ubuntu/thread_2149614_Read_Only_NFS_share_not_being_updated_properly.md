---
title: "Read Only NFS share not being updated properly"
date: 2013-05-29
forum: New to Ubuntu
---

### Post by dan08 on 2013-05-29
I have a few read-only NFS shares mounted to an Ubuntu 12.04 server.
This is what the fstab entries look like.

```

234.123.251.49:/Call01 /vrthst/roshare/call01/ nfs ro,intr,sync
234.123.251.49:/DRP /vrthst/roshare/drp/ nfs ro,intr,sync
234.123.251.49:/AyamelStorage /vrthst/roshare/ayamel/ nfs ro,intr,sync

```

The shares are being served from an EMC unisphere that takes regular checkpoints of each share. 
These checkpoint files are hidden but still visible at the mount points.
SOMETIMES
The problem is these checkpoint files do not always show up at the mount points.
The checkpoint from two days ago should get deleted and a checkpoint for today should show up.
But alot of the time the old (deleted) checkpoint sticks around, with a "stale nfs file handle" attached to it, and the new checkpoint does not appear.

Sometimes unmounting and remounting solves this, and sometimes it takes a full server reboot.

I am trying to automate a process to move the checkpoints off the EMC device to separate storage, but this is proving to be a problem because the new checkpoints do not show up regularly.

Does anyone have any idea what could cause this behavior?

---

