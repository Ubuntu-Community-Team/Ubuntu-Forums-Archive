---
title: "Determing use of partition and shrinking same"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-13
I have set my /home to sda3. I have all the files of /home on /sda3. At the time that /home was moved from sda1 to sda3 /home was about 30 gig. Once /home was moved, I tried to delete /home from sda1. 

Can I do

cd /sda1 ?

or how can I remove the /home left behind on sda1.

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9711    78003576   83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda3            9712       38536   231536812+  83  Linux
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

---

### Post by taurus on 2008-11-13
Did you mount /dev/sda3 to /home in /etc/fstab?

```
cat /etc/fstab
```

---

### Post by Mark_in_Hollywood on 2008-11-13
> **taurus said:**
> Did you mount /dev/sda3 to /home in /etc/fstab?

```
cat /etc/fstab
```

I don't believe so, I did the create sda3 and move of /home according to Psychocats page: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


mark@Lexington-19:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62e29314-59b3-4ead-95d0-92763420a111 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=755a36f6-c291-4ba2-b502-9304af3be671 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid,relatime 0 2 UUID=b137b9c0-cdce-43a7-917a-3cd4ee90cf22 /media/marks80 ext3 defaults,user 0 0

---

### Post by taurus on 2008-11-13
So, did you remember to remove the /home_backup?

```
ls -la /
```

---

### Post by Mark_in_Hollywood on 2008-11-13
> **taurus said:**
> So, did you remember to remove the /home_backup?

```
ls -la /
```

Following Psycho's page, I did:

sudo rm -rf /home_backup


mark@Lexington-19:~$ ls -la /
total 108
drwxrwxrwx  21 root root  4096 2008-10-23 20:33 .
drwxrwxrwx  21 root root  4096 2008-10-23 20:33 ..
drwxr-xr-x   2 root root  4096 2008-10-30 09:06 bin
drwxr-xr-x   3 root root  4096 2008-11-10 09:12 boot
lrwxrwxrwx   1 root root    11 2008-05-17 06:48 cdrom -> media/cdrom
drwxr-xr-x  14 root root 14180 2008-11-13 10:13 dev
drwxr-xr-x 148 root root 12288 2008-11-13 10:18 etc
drwxr-xr-x   5 mark mark  4096 2008-11-04 08:21 home
drwxr-xr-x   2 root root  4096 2008-04-22 10:48 initrd
lrwxrwxrwx   1 root root    32 2008-10-24 11:57 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root 12288 2008-11-13 08:17 lib
drwx------   2 root root 16384 2008-05-17 06:48 lost+found
drwxr-xr-x   9 root root  4096 2008-11-13 10:14 media
drwxr-xr-x   2 root root  4096 2008-04-14 22:53 mnt
drwxr-xr-x   6 root root  4096 2008-10-30 08:54 opt
dr-xr-xr-x 132 root root     0 2008-11-13 10:12 proc
drwxr-xr-x  22 root root  4096 2008-11-07 11:20 root
drwxr-xr-x   2 root root  4096 2008-11-13 08:17 sbin
drwxr-xr-x   2 root root  4096 2008-04-22 10:48 srv
drwxr-xr-x  12 root root     0 2008-11-13 10:12 sys
drwxrwxrwt  16 root root 12288 2008-11-13 10:52 tmp
drwxr-xr-x  14 root root  4096 2008-10-24 11:32 usr
drwxr-xr-x  15 root root  4096 2008-04-22 11:07 var
lrwxrwxrwx   1 root root    29 2008-10-24 11:57 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

---

### Post by taurus on 2008-11-13
You should be good then.  This command will tell you about your disk space usage.

```
df -h
```

---

### Post by Mark_in_Hollywood on 2008-11-13
> **taurus said:**
> You should be good then.  This command will tell you about your disk space usage.

```
df -h
```

mark@Lexington-19:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              74G   70G  1.7G  98% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  240K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  684K  504M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda3             220G   33G  176G  16% /home
/dev/sdb1             246M   42M  205M  17% /media/UDISK 28X

The /dev/sda1 is what I'm trying to "fix". Note that of the 74 gig, 70 are in use. I want to "shrink" /dev/sda1 to a more reasonable size: 20 gig. Then expand sda3 to absorb the 50 odd gig difference. In LiveCD under GParted, I cannot shrink sda1.

---

### Post by taurus on 2008-11-13
You cannot shrink /dev/sda1 because you don't have a whole lot of space there, only 1.7GB left.  What do you install on your machine that takes up the whole 70GB anyway?  Unless you clean out some space on /, gparted will not do any shrinking for you.

Looks in /var and /tmp to make sure you don't have any large files in there, taking up a big chunk of your space.

```
sudo du -h /tmp
sudo du -h /var
```

---

### Post by Mark_in_Hollywood on 2008-11-13
> **taurus said:**
> You cannot shrink /dev/sda1 because you don't have a whole lot of space there, only 1.7GB left.  What do you install on your machine that takes up the whole 70GB anyway?  Unless you clean out some space on /, gparted will not do any shrinking for you.

Looks in /var and /tmp to make sure you don't have any large files in there, taking up a big chunk of your space.

```
sudo du -h /tmp
sudo du -h /var
```

The 70 gig should have mostly been /home. Now that /home is on it's own partition and the old_home has been deleted, I thought I could recover 30 to 50 gig.

mark@Lexington-19:~$ sudo du -h /tmp
[sudo] password for mark: 
4.0K	/tmp/plugtmp
4.0K	/tmp/seahorse-bhfbJ7
4.0K	/tmp/.ICE-unix
4.0K	/tmp/.exchange-mark
4.0K	/tmp/gdl/log
8.0K	/tmp/gdl
4.0K	/tmp/.X11-unix
8.0K	/tmp/orbit-mark
4.0K	/tmp/.esd-1000
4.0K	/tmp/.winbindd
8.0K	/tmp/pulse-mark
4.0K	/tmp/.wine-1000/server-803-18405
8.0K	/tmp/.wine-1000
4.0K	/tmp/keyring-NluCNP
4.0K	/tmp/Tracker-mark.5908/Attachments
24K	/tmp/Tracker-mark.5908
4.0K	/tmp/virtual-mark.ko9DXr
112K	/tmp

so nothing there

/var is another story
mark@Lexington-19:~$ sudo du -h /var

[lines and lines of files, mostly in the kb size and some in mb size

363M	/var

I did do a permanent delete of the /.trash, it had a few gig in it, but I'm looking for 30 to 50 gig.

---

