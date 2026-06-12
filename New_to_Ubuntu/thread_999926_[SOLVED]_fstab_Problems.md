---
title: "[SOLVED] fstab Problems"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by markwaypoint on 2008-12-02
Hi everyone,

I am quite new to Linux at all.

I screwed around with my fstab conf trying to get my second HD to mount on bootup. (For the next time I know to backup config files.)

Both my CD and 2nd HD wont mount...

Here is what my fstab reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71938af6-77ca-48ff-bd1d-ad391d700121 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0e4b8799-6fd9-4d9c-99d2-37a5cc466477 none           swap    sw              0       0
# /dev/sdb1
UUID=f6a74353-6d94-46c8-8e5a-f66a5d76a173 /media/disk ext2 defaults 0 0
/dev/scd0
       /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0       0


any ideas on whats wrong here?

Let me know if you need more info.

Lars

---

### Post by taurus on 2008-12-02
> **markwaypoint said:**
> Hi everyone,

I am quite new to Linux at all.

I screwed around with my fstab conf trying to get my second HD to mount on bootup. (For the next time I know to backup config files.)

Both my CD and 2nd HD wont mount...

Here is what my fstab reads:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71938af6-77ca-48ff-bd1d-ad391d700121 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0e4b8799-6fd9-4d9c-99d2-37a5cc466477 none           swap    sw              0       0
# /dev/sdb1
UUID=f6a74353-6d94-46c8-8e5a-f66a5d76a173 /media/disk ext2 defaults 0 0
[B][COLOR="Blue"]/dev/scd0
       /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0       0
[/COLOR][/B]

any ideas on whats wrong here?

Let me know if you need more info.

Lars

Shouldn't the lines in blue be on the same line in /etc/fstab?  Also, do you have /media/dislk, the mount point for your /dev/sdb1?

---

### Post by markwaypoint on 2008-12-02
Like this? - What do I need to do to have sdb1 mounted on my desktop (on bootup) like it did on double click before...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71938af6-77ca-48ff-bd1d-ad391d700121 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0e4b8799-6fd9-4d9c-99d2-37a5cc466477 none           swap    sw              0       0
# /dev/sdb1
UUID=f6a74353-6d94-46c8-8e5a-f66a5d76a173 / ext2 defaults 0 0
# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0       0

Edit: CDrom mount works, thanks

Lars

---

### Post by mikewhatever on 2008-12-02
Here is what I have for cdrom, it's all in one line and no hash (#) sign in the beginning.
> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
As for the second HDD, simply delete all mention of it from fstab and mount it on demand from Places.

---

### Post by Idefix82 on 2008-12-02
Firstly, Taurus meant that mounting the cd rom should be done in one line. Instead of collapsing two lines into one you have just commented out the first bit.
Secondly, you certainly don't want to mount two partitions under the same mount point. Leave /media/disk as it was but make sure that this directory exists. You create it with
```
sudo mkdir /media/disk
```
In summary, your fstab should look like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71938af6-77ca-48ff-bd1d-ad391d700121 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0e4b8799-6fd9-4d9c-99d2-37a5cc466477 none           swap    sw              0       0
# /dev/sdb1
UUID=f6a74353-6d94-46c8-8e5a-f66a5d76a173 /media/disk ext2 defaults 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by taurus on 2008-12-02
> **markwaypoint said:**
> Like this? - What do I need to do to have sdb1 mounted on my desktop (on bootup) like it did on double click before...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=71938af6-77ca-48ff-bd1d-ad391d700121 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0e4b8799-6fd9-4d9c-99d2-37a5cc466477 none           swap    sw              0       0
# /dev/sdb1
**[COLOR="Red"]UUID=f6a74353-6d94-46c8-8e5a-f66a5d76a173 / ext2 defaults 0 0[/COLOR]**
# /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0       0

Edit: CDrom mount works, thanks

Lars

You better NOT use that /etc/fstab or you won't be able to boot into Ubuntu again.  If you want to mount /dev/sdb1, change the entry in /etc/fstab to this.

```

UUID=f6a74353-6d94-46c8-8e5a-f66a5d76a173   /media/sdb1   ext2   defaults   0   0
```
Save it.  Then, create a new mount and mount it.

```
mkdir sudo /media/sdb1
sudo mount -a
```

---

### Post by markwaypoint on 2008-12-02
thanks, I am back to "quite normal" state

Lars

---

