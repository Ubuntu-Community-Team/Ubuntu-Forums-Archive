---
title: "confused by fstab"
date: 2016-02-09
forum: New to Ubuntu
---

### Post by claude9 on 2016-02-09
Hi all

i'm trying to share a NTFS partition in a HD attached to a PC running Ubuntu (14.04 I think..)

I've created a /media/claude/partage mount point,and in order to mount automatically, I have written my /etc/fstab

/dev/sdc6       /media/claude/partage  ntfs-3g -o rw,uid=1000, gid=1000, utf8, umask=0022 0   1

From what I understand, partage shld have, due to umask  the following rights rwxr-xr-x
BUT , once the HD mounted ( sdc6 partition ) , partage belongs to root, root with rwxrwxrwx rights....
and more than that, il I type a simple mount , I'm getting 

/dev/sdc6 on /media/claude/partage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

How come, what I wrote in my /etc/fstab is not taken into consideration? are where that fuseblk come from..

A bit of clarification would be greatly needed and greatly appreciated...
Thks in advance

---

### Post by SeijiSensei on 2016-02-09
Don't include "-o" before the options and remove the spaces from the list.  You should just use "ntfs" as the filesystem type and probably include "defaults" in the list of options as well.
```
/dev/sdc6 /media/claude/partage ntfs defaults,rw,uid=1000,gid=1000,utf8,umask=0022 0 1
```

For comparison, my NTFS partition is mounted with the following entry:
```
UUID=D054464154462A94 /media/BigNTFS  ntfs    defaults,umask=007,gid=46 0 0
```
(I'm using a UUID rather than "/dev/sdb2".)  This configuration mounts the device with root as the owner and group "plugdev" (46).  At installation, my user was added to that group by default.  The mounted device has full permissions for root and group plugdev and blocks access from everyone else.

---

### Post by claude9 on 2016-02-09
Done what u suggested...thks
but same stuff, I have the feeling that the way it is mounted ( what I see after a "mount" command)  differs from what sits in my fstab...
Don't know why...and don't know if it is that important - but i'd like to have the ideas clear...if possible lol

---

### Post by sandyd on 2016-02-09
Does that still happen when running
```

sudo umount /dev/sdc6
sudo mount -a
```

Note that unless you create a usermap file or add the *permissions* option, a mounted NTFS partition will not support setting access permissions set through chmod

---

### Post by SeijiSensei on 2016-02-09
> **sandyd said:**
> Note that unless you create a usermap file or add the *permissions* option, a mounted NTFS partition will not support permissions.
If you mount the NTFS filesystem with the options I gave above, all the files and directories are owned by root and group plugdev with full permissions to both.  Of course, that doesn't mean that user bill can create a file that only bill owns.  It will be owned by [noparse]root:plugdev[/noparse].

---

### Post by sandyd on 2016-02-09
> **SeijiSensei said:**
> If you mount the NTFS filesystem with the options I gave above, all the files and directories are owned by root and group plugdev with full permissions to both.  Of course, that doesn't mean that user bill can create a file that only bill owns.  It will be owned by [noparse]root:plugdev[/noparse].

Should have been "setting access permissions using chmod" above for clarity - fixed

---

### Post by claude9 on 2016-02-10
@Seijiensei/Sandyd
I've checked the umoun/mount sequence you suggested...same stuff "mount" gives me something different from what sits in my fstab
i've checked...I have no usermap so that's why chmoding is useless !!! Thks for clarification 

Plugdev...I don't know how to assign a client to this group because the client ( a Smart TV...trying to access the shared partition) has no name
This client is under Android 5.1.1 and I have no access to the internals..
I'll stay with my current config...which seems to work fine even if I don't fully understand why
Thks again to you both

---

### Post by Morbius1 on 2016-02-10
> /dev/sdc6 /media/claude/partage ntfs-3g -o rw,uid=1000, gid=1000, utf8, umask=0022 0 1
That line was likely ignored for the reasons SeijiSensei has given.
> il I type a simple mount , I'm getting

/dev/sdc6 on /media/claude/partage type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
Even if you corrected your fstab line and ran mount you will still get that output.

Linux mounts ntfs by creating a "view" of that partition that gives it the appearance that it has Linux permissions when in fact ntfs has no linux permissions. It does that using "fuse" which is why you see "fuseblk" in mount. It will obey the options listed in fstab/

Please ignore the following suggestion if you interpreted it as such:
> Note that unless you create a usermap file or add the permissions option, a mounted NTFS partition will not support setting access permissions set through chmod 

No one should ever do that to an NTFS partition in Linux. It will just make a mess of things.

---

### Post by claude9 on 2016-02-12
@Morbius1
Thks...its clear now !!

---

