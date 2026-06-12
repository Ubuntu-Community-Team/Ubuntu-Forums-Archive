---
title: "Include NTFS drives in updatedb"
date: 2005-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by zukakog on 2005-08-18
Yes I have searched the forums.

When I run updatedb, it doesn't seem to be indexing my mounted ntfs drives.  I've checked the /etc/updatedb.conf and it doesn't say anything about ntfs being included or excluded.  Any ideas?

my updatedb.conf
```
# This file sets environment variables which are used by updatedb

# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs afs proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs sysfs"
export PRUNEFS
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs"
export PRUNEPATHS
# netpaths which are added
NETPATHS=""
export NETPATHS
# run find as this user
LOCALUSER="nobody"
export LOCALUSER
# cron.daily/find: run at this priority -- higher number means lower priority
# (this is relative to the default which cron sets, which is usually +5)
NICE=10
export NICE
```

---

### Post by dabear on 2005-08-18
[QUOTE=zukakog]Yes I have searched the forums.

When I run updatedb, it doesn't seem to be indexing my mounted ntfs drives.  I've checked the /etc/updatedb.conf and it doesn't say anything about ntfs being included or excluded.  Any ideas?

my updatedb.conf
```
# This file sets environment variables which are used by updatedb

# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs afs proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs sysfs"
export PRUNEFS
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs"
export PRUNEPATHS
# netpaths which are added
NETPATHS=""
export NETPATHS
# run find as this user
LOCALUSER="nobody"
export LOCALUSER
# cron.daily/find: run at this priority -- higher number means lower priority
# (this is relative to the default which cron sets, which is usually +5)
NICE=10
export NICE
```[/QUOTE]
 Hi and welcome. You should note the following thread, and ask in another subforum.
READ: [http://ubuntuforums.org/showthread.php?t=22348](http://ubuntuforums.org/showthread.php?t=22348)

---

