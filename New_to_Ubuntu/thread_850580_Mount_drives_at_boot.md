---
title: "Mount drives at boot"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Check3check on 2008-07-05
How do I set all drives to mount at boot?
I have an additional drive running XP and one for only media that don't mount at boot, so every time I start up my PC I have to re-add everything to Amarok and my background reverts to the default background :/

Help?

---

### Post by Cypher on 2008-07-05
You can add entries to the /etc/fstab file to cause those directories to be automatically mounted at boo-time.

Once you figure out which partitions you want to mount, run the command
```

sudo vol_id <partition>

```
Look for the ID_FS_UUID value which you will use in the /etc/fstab to specify a particular partition. Now just mimic the existing entries and create your own. For the WinXP partition you'll want to use NTFS as opposed to EXT3 for the partition type, the same goes for your media partition...

---

### Post by alienexplorers on 2008-07-05
Generate the UUID using:
> sudo vol_id /dev/s???

```
terminator@terminator-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2eed7dda-3209-456c-8867-a36d3716088c /               ext3    relatime,errors=remount-ro,commit=300 0       1
# /dev/sda2
UUID=64af1f59-71ab-4fc5-b463-092ab5fa4dea /home           ext3    relatime,commit=300        0       2
# /dev/sda3
UUID=F884-CCF8				  /windows        vfat    iocharset=utf8,umask=000	0	0
# /dev/sda4
UUID==56af67af-7b95-43a3-831c-8e778637e77a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
terminator@terminator-desktop:~$ 
```

---

### Post by kuja on 2008-07-05
I would:

[Mount](http://www.tuxfiles.org/linuxhelp/mounting.html) the partitions in question (seeing as there are more than one, I'd do this one at a time to simplify things)
Then I'd add them to the [/etc/fstab file](http://www.tuxfiles.org/linuxhelp/fstab.html)

If you do it one at a time as I suggested, you can use this command: ```
sudo bash -c "tail -1 /etc/mtab >> /etc/fstab"
``` to add the line to the file, therefore you don't have to edit the /etc/fstab file by hand at all, all you have to manage to do is mount the partition :)

---

### Post by Troll_the_Great on 2008-07-05
There is an easier way.Install ntfs-config and it will auto mount them (I suppose that your windows partition is NTFS)
```
sudo apt-get install ntfs-config
```
Have a look here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
Hope this helps.
Cheers!

---

### Post by Check3check on 2008-07-05
> **Troll_the_Great said:**
> There is an easier way.Install ntfs-config and it will auto mount them (I suppose that your windows partition is NTFS)
```
sudo apt-get install ntfs-config
```
Have a look here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
Hope this helps.
Cheers!

You're a beast, thanks bro. worked.

---

