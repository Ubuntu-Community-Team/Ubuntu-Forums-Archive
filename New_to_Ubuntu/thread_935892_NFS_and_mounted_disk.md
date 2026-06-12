---
title: "NFS and mounted disk"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by .nedberg on 2008-10-02
I am using NFS to share a folder from my server to some clients (all are Hardy).

My /etc/exports is something like this:
```

/mnt/media/ 192.168.2.*(rw,no_root_squash,async,all_squash,anonuid=1000,anongid=1000)

```

Under /mnt/media there is a folder, mediafiles. On the server I mount another disk at /mnt/media/mediafiles.

The problem is that the old files from /mnt/media/mediafiles are shown on the clients, not the new files from the other disk. On the server ls /mnt/media/mediafiles gives the desired output.

Is there a way to make it export the mounted disk or do I have to make another line in /etc/exports and mount it on the clients? I have rebooted the server and restarted nfs.

---

### Post by .nedberg on 2008-10-02
After digging around for a while I found something indicating that what I wanted could not be done with the nfs-kernel-server. With the nfs-user-server it was default behaviour, but it didn't have that good performance.

I therfore "solved" this problem by simply mounting my new disk on the server outside of the old export, added the new mountpoint to /etc/exports and mounted this where I wanted it on the clients. This was not optimal as I now had to change /etc/fstab on every client.

Anyhow, it is now working as it should do!

---

