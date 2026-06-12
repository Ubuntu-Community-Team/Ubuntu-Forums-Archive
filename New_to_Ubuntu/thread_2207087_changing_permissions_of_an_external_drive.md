---
title: "changing permissions of an external drive"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by beelzebufo on 2014-02-22
I am not sure how I did it, but I seem to have changed my external to read only.. and now I am not sure how to get it back to read/write.  I am sure it's something simple and I just haven't been reading the posts I have seen on this correctly, but any help would be appreciated.

thanks in advance
beelze

edit: nevermind, I think I got it, I just had to do a chmod 777 /home/media/me/external

---

### Post by Habitual on 2014-02-24
until the next reboot or mount?

See [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by beelzebufo on 2014-02-24
I think it's working.. is 777 a temporary or a windows only argument?  it's a fat 32 partition, so the ntfs quarrels shouldn't be an issue.  anyway, thanks for the response.

---

### Post by Habitual on 2014-02-25
See [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

You'll need to mount via /etc/fstab using some switches that will preserve your intended Linux permissions for it to be persistent.

as root (I use another OS, so YMMV) I made a mount using (with the unit **un**mounted)...
```
sudo mkdir /home/media/me/external
```
then I plug the unit in an then we have to manually mount it as root to "see" which options we'll need in /etc/fstab...

See the section titled "Mount the Drive" at above link.
If you're super-lucky, then
```
sudo mount -t vfat /dev/**[COLOR=#ff0000]sdb1[/COLOR]** /home/media/me/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
``` will give you the correct permissions.

where **[COLOR=#ff0000]sdb1[/COLOR]**[COLOR=#000000] could be, may be...possibly ***is*** different.
[/COLOR]```
sudo fdisk -l
```

if it IS sdb1 and the command with the fmask in it works, then your /etc/fstab could be
```
/dev/sdb1 /home/media/me/external vfat rw,uid=1000,gid=1000,utf8,dmask=027,fmask=137 0 0
```

But don't try these blindly, wait for someone else to insert something I missed.
Lately, I read that UUID is **the way to go**, see [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

See also [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Let us know...

---

