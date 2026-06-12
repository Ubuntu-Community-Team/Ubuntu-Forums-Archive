---
title: "[SOLVED] Partition not auto mounting on reboot."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by rabidninjawombat on 2008-05-28
Title explains it.. every time i reboot i have to manually remount the partition that i want auto mounting. (the one i set to mount to /mnt/multimedia.

Here is my /etc/fstab , its the last one on the list..i think everything is set up properly. 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=f52792a5-0355-4ae2-b53c-0cc12d7d3a77 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=604144a8-65b7-44e2-9150-43c209f1f493 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda1       /mnt/multimedia  ext3   default,devgid=100   0   0
```

---

### Post by spiderbatdad on 2008-05-28
I think you need a uid in there to mount it during your user session, and I'm not sure about devgid. Maybe try the following.

/dev/sda1       /mnt/multimedia  ext3   default,uid=1000,gid=100   0   0

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by rabidninjawombat on 2008-05-28
> **spiderbatdad said:**
> I think you need a uid in there to mount it during your user session, and I'm not sure about devgid. Maybe try the following.

/dev/sda1       /mnt/multimedia  ext3   default,uid=1000,gid=100   0   0

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ok, just restarted.. and no its still not mounting automatically.

---

### Post by Oldsoldier2003 on 2008-05-28
> **rabidninjawombat said:**
> Ok, just restarted.. and no its still not mounting automatically.
this is what i would try.
```
/dev/sda1 /mnt/multimedia ext3 nodev nosuid
```

---

### Post by rabidninjawombat on 2008-05-28
Then i assume i would edit the permissions on the mount point to ensure i can read/write to the drive?  something like 

```
chmod 777 /mnt/multimedia
```
?

---

### Post by rabidninjawombat on 2008-05-28
> **Oldsoldier2003 said:**
> this is what i would try.
```
/dev/sda1 /mnt/multimedia ext3 nodev nosuid
```

still no luck... :(  

mounted it and unmounted it manually just to make sure , and its fine there. just not automounting on reboot.

---

### Post by Oldsoldier2003 on 2008-05-28
> **rabidninjawombat said:**
> still no luck... :(  

mounted it and unmounted it manually just to make sure , and its fine there. just not automounting on reboot.

thats odd did you chown the mount point and chmod it?
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by rabidninjawombat on 2008-05-28
> **Oldsoldier2003 said:**
> thats odd did you chown the mount point and chmod it?
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)


I did indeed. Not sure whats up.

---

### Post by Michaelg14 on 2008-05-28
Have you created a multimedia directory in /mnt?

Sorry, rereading, it seems like you have.

---

### Post by rabidninjawombat on 2008-05-28
> **Michaelg14 said:**
> Have you created a multimedia directory in /mnt?

Oh yea. :) ahead of ya there.  And a symbolic link in the home directory (/home/USERNAME/multimedia)  

When i manually mount the partition it works just fine the issue seems to just be automounting upon rebooting.

---

### Post by rabidninjawombat on 2008-05-28
any other idea? :) help so far is greatly appreciated

---

