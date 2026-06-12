---
title: "[SOLVED] automount 2nd linux drive in xubuntu"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by worlestone on 2008-10-27
I've just installed xubuntu, I'd been using ubuntu previously.  I have a 2nd drive using ext3 which does not automount.  I've tried following the instuctions at [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) but cannot seem to get it to work.  Could someone please help me out, thanks.

Adrian

---

### Post by Xiong Chiamiov on 2008-10-28
Post the results of:
```

sudo fdisk -l

```
and your /etc/fstab.

---

### Post by worlestone on 2008-10-28
Hi thanks,

It's:

root@adrian-desktop:/home/adrian# sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37f1a851

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30214   242693923+  83  Linux
/dev/sda2           30215       30401     1502077+   5  Extended
/dev/sda5           30215       30401     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x37f1a851

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161   83  Linux
root@adrian-desktop:/home/adrian#

---

### Post by Elfy on 2008-10-28
Making the assumption that you have started to work through the page can you also post

```
cat /etc/fstab
sudo blkid
```

---

### Post by worlestone on 2008-10-28
Gives the following....

root@adrian-desktop:/home/adrian# cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2a8c5c03-a85f-464f-bc9e-bfc9ae6eb5e6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=dea0e89a-e373-4e57-87ab-7f0e8ce42036 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#my changes
# /dev/sdb
/dev/sdb   /media/backup_disk  ext3   defaults  0 0
root@adrian-desktop:/home/adrian# sudo blkid

---

### Post by worlestone on 2008-10-28
Oops... and...

root@adrian-desktop:/home/adrian# sudo blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="2a8c5c03-a85f-464f-bc9e-bfc9ae6eb5e6" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="dea0e89a-e373-4e57-87ab-7f0e8ce42036" 
/dev/sdb1: UUID="6af51ff0-d642-4884-9b36-d974027f89b1" TYPE="ext2" 
root@adrian-desktop:/home/adrian#

---

### Post by Elfy on 2008-10-28
change the last line - you have /dev/sdb - it needs to be /dev/_sdb1_ or you can get the UUID from blkid and use that instead

UUID=6af51ff0-d642-4884-9b36-d974027f89b1 /media/backup_disk ext3 defaults 0 0

at the moment it won't check the drive for errors either, to do so

UUID=6af51ff0-d642-4884-9b36-d974027f89b1 /media/backup_disk ext3 defaults 0 2

---

### Post by worlestone on 2008-10-28
Thanks.  Just tried that, still not visible after a reboot - assume that I should be able to see the drive in 'Places'?

Adrian

---

### Post by worlestone on 2008-10-28
Oops, sorry, found it in Media.  I was hoping to see this along with filesystem, wastebin etc in 'Places'

Thanks for the help.

Adrian

---

### Post by Elfy on 2008-10-28
Open a terminal and run

```
sudo mount -a
```

post the error please

---

### Post by Elfy on 2008-10-28
Ok, you can drag from the right panel in naultilus to the places on the left panerl and it will make a shortcut for you

---

### Post by worlestone on 2008-10-28
no errors, in fact nothing, just returns to the prompt.  Rebooted, nothing new, tried terminal again and sudo mount -a, still nothing.

---

### Post by worlestone on 2008-10-28
Ah, just caught up with your last post.  How simple is that, I'd just not thought it could be so simple!

Thanks for the help :)

---

### Post by Elfy on 2008-10-28
heh - posting at the same time can cause confusion :)

can you mark thread solved please

---

