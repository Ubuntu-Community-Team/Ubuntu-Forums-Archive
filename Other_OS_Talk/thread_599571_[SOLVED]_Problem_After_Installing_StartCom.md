---
title: "[SOLVED] Problem After Installing StartCom"
date: 2007-11-01
forum: Other OS Talk
---

### Post by kshane on 2007-11-01
I'm hoping there's a simple fix for this...

I installed a new Linux OS this morning: StartCom. It's supposed to be really great for doing multimedia stuff. Well, first, when I rebooted, there was no option for Ubuntu, so I used Super Grub and fixed it so that Ubuntu would boot. Then I couldn't boot to StartCom, so I went to the grub menu that it wrote and copied the entry for StartCom and put it in the Ubuntu grub menu.lst. Now they both boot, but I get an fsck error each time I boot to Ubuntu. I looked at the log file it wrote and I am lost. The entry is below:
```

Log of fsck -C -R -A -a 
Thu Nov  1 09:28:03 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda4: clean, 2551/6979584 files, 5538669/13952452 blocks (check in 4 mounts)
fsck.ext3: Unable to resolve 'UUID=278672a9-9db7-40db-96f4-9691b3874fa4'

fsck died with exit status 8

Thu Nov  1 09:28:04 2007
----------------

```
The referenced partition is the one I installed StartCom on. It's not a new partition, I just hadn't been using it. Below is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c1dd7906-ecf3-403c-8348-9701b828e691 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=7198D00F73629629 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda4
UUID=5e70c11b-d4a5-4cd6-9c1a-4a81e11ecffe /media/sda4     ext3    defaults        0       2
# /dev/sda5
UUID=278672a9-9db7-40db-96f4-9691b3874fa4 /media/sda5     ext3    defaults        0       2
# /dev/sda6
UUID=ebf9e319-ccac-4b71-b585-88c0cea88134 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```
The only REAL problem now is that when booting to Ubuntu the login screen doesn't come up. I get a grub command line. If I exit it, them the Gnome login screen comes up and everything is pretty much fine, except that Ubuntu seems a little "jerky", like it's hesitating a split second before executing any commands. That I guess I can figure out and smooth over on my own. I would just like to clean up the error that's stopping a smooth transition from cold boot to login.

Any ideas, folks?

Thanks in advance!

Kevin

---

### Post by kshane on 2007-11-01
problem solved...

---

