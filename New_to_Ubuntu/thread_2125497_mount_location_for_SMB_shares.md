---
title: "mount location for SMB shares"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by stevebond001 on 2013-03-14
Hi
I have installed a backup tool (lucky backup) which seems to do what I want (I have tried backing up from folder to folder locally)
I now want to backup my files to a SMB share on my NAS.
I can access the SMB shares across the network no problem.  However, when I try to configure the backup tool to point to my SMB share I can't find the mount point.
I have looked in ~/.gfs, /media and /mnt folders, but I can't find it.  I've also come across a post which states that they may be in the ~/.cache/gvfs/ instead, but it's not there either.

Does anyone know where I need to look please? (running Ubuntu 12.10)

Many thanks in advance

---

### Post by Paqman on 2013-03-14
If you mounted them through the Nautilus file browser they should be in ~/.gvfs. You know that location is hidden by default, yes?

---

### Post by stevebond001 on 2013-03-14
> **Paqman said:**
> If you mounted them through the Nautilus file browser they should be in ~/.gvfs. You know that location is hidden by default, yes?

Hi
Thanks for the reply.
Yes I know that the location is hidden (I am showing hidden files)

I think I've found the location - it's /run/usr/"user name"/.gvfs.  When I go there in nemo I see an entry for the mounted share.

However, when I try and input this path into the backup program it won't access the gvfs folder, which is a PITA. :(

All I want to do it backup files from a folder to a share (and run periodically to backup any new files).  How hard can it be to do this??  There must be an easier way:(:(

Can anyone recommend a decent backup tool which backs up file (not zips them up - actually backs the files up).  I can acheive what I want in the windows world with synctoy, cobian backup, etc - is there an alternative in linux?

Thanks very much

---

### Post by steeldriver on 2013-03-14
If you want to run periodic (unattended) backups then imho it's not a good idea to rely on a gvfs (userland) mount - you would be better off mounting the share to a permanent mount point via your fstab file

---

### Post by stevebond001 on 2013-03-14
> **steeldriver said:**
> If you want to run periodic (unattended) backups then imho it's not a good idea to rely on a gvfs (userland) mount - you would be better off mounting the share to a permanent mount point via your fstab file

I agree.  However, as I'm at my PC regularly it's no problem to mount my share manually.  The issue I have is finding a suitable backup tool which will allow backing up to SMB shares

---

### Post by steeldriver on 2013-03-14
Well gvfs/fuse mounts have funny permissions (for example root can't even read them by default) which may be what's causing your issues, especially if you are running the backup tool as root

FWIW on my 12.04 system the nautilus SMB shares go in ~/.gvfs:

```

$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
.
.
.
**gvfs-fuse-daemon on /home/steeldriver/.gvfs** type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=steeldriver)

```

```

$ ls -l ~/.gvfs
total 0
drwx------ 1 steeldriver steeldriver 0 Aug 24  2012 public on alice

```

---

