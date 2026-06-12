---
title: "restart fstab"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by mt85m on 2008-07-08
Hello all, I am wanting to know a way to restart the drive mountings. When I edit the fstab file I have to reboot for the changes to take effect?

Is there a command to restart the drive mounting process?

P.S: i think if i do sudo mount -a, this will should do the trick, however, when i did this it gave me an error message saying, permission denied"[tcp] operations:/var/log/ehds/combinedServerLogs: Permission denied"
all the permissions for the mount folders are set to true.  

Thanks

---

### Post by Rocket2DMn on 2008-07-08
Can you please post your fstab file?  If you have login/pw info stored for a remote connection, please cover that up
```
cat /etc/fstab
```
Also please post:
```
sudo fdisk -l
mount
sudo blkid
```

---

### Post by mt85m on 2008-07-09
# Device                Mountpoint      FStype  Options         Dump    Pass#
/dev/da0s1b             none            swap    sw              0       0
/dev/da0s1a             /               ufs     rw              1       1
/dev/da0s1d             /var            ufs     rw              2       2
/dev/da1s1d             /clients        ufs     rw              3       3
/dev/acd0               /cdrom          cd9660  ro,noauto       0       0
# {NFS}-->Operations /usr/{src,ports} [HH] 20071204    
operations:/usr/guests/src      /usr/src        nfs     rw,tcp              0       0
operations:/usr/ports    /usr/ports      nfs     rw,tcp               0       0
operations:/var/log/ehds/combinedServerLogs      /var/log/ehds/combinedServerLogs       nfs     rw,tcp  0       0

---

### Post by mt85m on 2008-07-09
here is the other info that you requested

usage: fdisk [-BIaipstu] [-b bootcode] [-1234] [disk]
       fdisk -f configfile [-itv] [disk]

------------------------------------------------------
/dev/da0s1a on / (ufs, local)
devfs on /dev (devfs, local)
/dev/da0s1d on /var (ufs, local, soft-updates)
operations:/usr/guests/src on /usr/src (nfs)
/dev/da1s1d on /clients (ufs, local, soft-updates)
operations:/usr/ports on /usr/ports (nfs)
------------------------------------------------------
the blkid command does not work in my bash shell:
i have an abunto machine but these commands are being executed on a FreeBSD server.  sorry that i did not mention this before.

---

### Post by Rocket2DMn on 2008-07-09
Yeah, those commands don't look much like normal output on Ubuntu machines.  If you need help with FreeBSD, you need to post in Other OS Talk area of the forum, in the BSD section - [http://ubuntuforums.org/forumdisplay.php?f=171](http://ubuntuforums.org/forumdisplay.php?f=171)

Good luck.

---

### Post by mt85m on 2008-07-15
I know that abuntu is little different than FreeBSD but when i do mount -a it works for all the commands in the file exept the command that i entered, it gives me a mesaage: Permission Denied.  so its kindaof working but iam missing something and i can figure out WHAT THE HECK IT IS!!!

---

