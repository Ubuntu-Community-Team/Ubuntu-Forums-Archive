---
title: "[SOLVED] No more space left on / after simple backup"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2008-09-20
So I was running simple backup, trying to do a backup to my external hard drive. It looks like nothing was put onto my external but I just looked and now I have 0 bytes free on "/". This is really strange since I'm sure I had a few gigs (3-4) left on it before I tried backing up.

Is there any way I can fix this? Like seeing if it made a backup on my "/" partition and deleting it? Does simple backup save backups as an iso? I forsee this being a problem in the near future ._.

Thanks,
SMRT

---

### Post by BattousaiX on 2008-09-20
This happens sometimes with our servers I don't know why.  For some reason, whatever the cause (I have yet to find anything within the logs), though /backup becomes unmounted.

I would do the following

- move all files that do not belong in / to /home as you should have some space there. (move to /backup after remounting)

- remount your backup drive to /backup

- make sure /etc/fstab contains the /backup line, if not, you may need to use man fstab for configuration.

- once this is done, you may want to run the backup.


How do you perform your backups?

You can make an ISO with dd.

dd if=/path/to/input/file of=/path/to/output/file.iso

It's been a while but I believe that's how I used to make my ISOs.

---

### Post by frank002 on 2008-09-20
Simple backup creates a backup directory in /var/backup. Check there to see if you can delete older backups and free space. A while back a reader posted  that Simple backup had eaten up most of his drive. If you have an external drive, just copy your important stuff to it.

---

### Post by I[AM]SMRT on 2008-09-20
> **BattousaiX said:**
> - move all files that do not belong in / to /home as you should have some space there. (move to /backup after remounting)
I would've done this but I'm not too familiar with what belongs there and what doesn't ._.

> **frank002 said:**
> Simple backup creates a backup directory in /var/backup. Check there to see if you can delete older backups and free space. A while back a reader posted  that Simple backup had eaten up most of his drive. If you have an external drive, just copy your important stuff to it.
I deleted the backup in /var/backup using root but it didn't clear up any space =/.

---

### Post by bumanie on 2008-09-20
To try and free up some space > sudo apt-get autoclean> sudo apt-get install localepurgemay help also.

---

### Post by lswb on 2008-09-20
It sounds like your external drive was not mounted or perhaps was not mounted where you thought it was. What is the mountpoint (directory path) that the external drive uses? With the external drive disconnected, try ls /path/to/extdrive/mountpoint and see if the files are there.

---

### Post by I[AM]SMRT on 2008-09-20
> **bumanie said:**
> To try and free up some space may help also.
Autoclean didn't do anything ;(

What does localepurge do exactly? I'm not sure what language codes to select and whatnot. I'm also not sure how to select a language code ._.

```
localepurge: Disk space freed in /usr/share/locale: 33468K
localepurge: Disk space freed in /usr/share/man: 3432K

Total disk space freed by localepurge: 36900K

```

/ is still full.

> **lswb said:**
> It sounds like your external drive was not mounted or perhaps was not mounted where you thought it was. What is the mountpoint (directory path) that the external drive uses? With the external drive disconnected, try ls /path/to/extdrive/mountpoint and see if the files are there.
There's nothing at the mount point with it disconnected ._.

/media/WD Passport is the mountpoint

When I select everything in my home folder (minus /home) and right click, it says all the files add up to 3.8 gb ;(.

---

### Post by I[AM]SMRT on 2008-09-22
> When I select everything in my home folder (minus /home) and right click, it says all the files add up to 3.8 gb ;(.
This is so strange, I have no idea what to do =/. Hate to bump threads but I still need help.

Here's some output:

```
brian@brian-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.7G  9.5G     0 100% /
varrun                755M  108K  755M   1% /var/run
varlock               755M     0  755M   0% /var/lock
udev                  755M   68K  755M   1% /dev
devshm                755M  200K  755M   1% /dev/shm
lrm                   755M   39M  717M   6% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              63G   16G   44G  28% /home
overflow              1.0M   40K  984K   4% /tmp
gvfs-fuse-daemon      9.7G  9.5G     0 100% /home/brian/.gvfs



brian@brian-laptop:~$ sudo du -sh /*
5.2M	/bin
38M	/boot
0	/cdrom
280K	/dev
46M	/etc
du: cannot access `/home/brian/.gvfs': Permission denied
16G	/home
4.0K	/initrd
0	/initrd.img
0	/initrd.img.old
284M	/lib
16K	/lost+found
8.0K	/media
4.0K	/mnt
4.0K	/opt
du: cannot access `/proc/10899/task/10899/fd/4': No such file or directory
du: cannot access `/proc/10899/task/10899/fdinfo/4': No such file or directory
du: cannot access `/proc/10899/fd/4': No such file or directory
du: cannot access `/proc/10899/fdinfo/4': No such file or directory
0	/proc
6.5G	/root
6.9M	/sbin
4.0K	/srv
0	/sys
40K	/tmp
2.2G	/usr
263M	/var
0	/vmlinuz
0	/vmlinuz.old



brian@brian-laptop:~$ mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
overflow on /tmp type tmpfs (rw,size=1048576,mode=1777)
gvfs-fuse-daemon on /home/brian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brian)

```

---

### Post by I[AM]SMRT on 2008-09-22
I found the problem, it was that backup, it's 6.5 gb in "/root/.local/share/Trash/files"

But when I try to delete it it just goes right back to the trash, even when I open nautilus as root. What can I do to delete this file? ;(

---

### Post by maybeway36 on 2008-09-22
```
sudo rm -rv /root/.local/share/Trash
```
This will get rid of the backup for good.

---

### Post by I[AM]SMRT on 2008-09-22
> **maybeway36 said:**
> ```
sudo rm -rv /root/.local/share/Trash
```
This will get rid of the backup for good.
Yea I figured it out, woo! Thanks.

---

