---
title: "squashfs on a 7gb eee pc"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Madwida on 2008-09-13
Hi

I am running Ubuntu eee on my 701 4gb eee pc.  I have two, perhaps related, concerns/questions.

First, in an effort to save some space I tried to use squashfs according to the instructions here [http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/#leave_comment](http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/#leave_comment).  Initially, when I did it would not finish compressing b/c I ran out of space; it would only compress about 50% and then stop.  Then I tried again yesterday and got this (it's followed by the output from df and df -h).  

The second problem: You will note that there are two 3.5 gb files allegedly running; but I only have a 4gb eee.  When I run the disk usage analyzer I am also told that I have 7gb. I have included a screenshot below.  

Many, many thanks! 

Here's the output: 

christian@christian-laptop:~$ sudo mkdir -p /.filesystems/usr/overlay
[sudo] password for christian: 
christian@christian-laptop:~$ mksquashfs /usr /.filesystems/usr/usr.sqfs
Could not create destination file: Permission denied
christian@christian-laptop:~$ sudo mksquashfs /usr /.filesystems/usr/usr.sqfs
Parallel mksquashfs: Using 1 processor
Creating little endian 3.1 filesystem on /.filesystems/usr/usr.sqfs, block size 131072.
[========================================================= ] 108018/109010  99%
Exportable Little endian filesystem, data block size 131072, compressed data, compressed metadata, compressed fragments, duplicates are removed
Filesystem size 663029.00 Kbytes (647.49 Mbytes)
	38.56% of uncompressed filesystem size (1719656.11 Kbytes)
Inode table size 1282868 bytes (1252.80 Kbytes)
	27.41% of uncompressed inode table size (4679879 bytes)
Directory table size 1322535 bytes (1291.54 Kbytes)
	48.53% of uncompressed directory table size (2724918 bytes)
Number of duplicate files found 37948
Number of inodes 137666
Number of files 107565
Number of fragments 5320
Number of symbolic links  15554
Number of device nodes 0
Number of fifo nodes 0
Number of socket nodes 0
Number of directories 14547
Number of uids 4
	root (0)
	daemon (1)
	libuuid (100)
	christian (1000)
Number of gids 13
	tty (5)
	shadow (42)
	crontab (110)
	lpadmin (109)
	mlocate (111)
	utmp (43)
	ssh (112)
	messagebus (119)
	polkituser (122)
	staff (50)
	dip (30)
	libuuid (101)
	src (40)
christian@christian-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              3649788   3539648         0 100% /
varrun                  513432       104    513328   1% /var/run
varlock                 513432         0    513432   0% /var/lock
udev                    513432        48    513384   1% /dev
devshm                  513432        28    513404   1% /dev/shm
gvfs-fuse-daemon       3649788   3539648         0 100% /home/christian/.gvfs
christian@christian-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.5G  3.4G     0 100% /
varrun                502M  104K  502M   1% /var/run
varlock               502M     0  502M   0% /var/lock
udev                  502M   48K  502M   1% /dev
devshm                502M   28K  502M   1% /dev/shm
gvfs-fuse-daemon      3.5G  3.4G     0 100% /home/christian/.gvfs
christian@christian-laptop:~$

---

### Post by Madwida on 2008-09-14
bump, please

---

### Post by synss on 2008-09-22
The thing is that none of
```
 
varrun 502M 104K 502M 1% /var/run
varlock 502M 0 502M 0% /var/lock
udev 502M 48K 502M 1% /dev
devshm 502M 28K 502M 1% /dev/shm
gvfs-fuse-daemon 3.5G 3.4G 0 100% /home/christian/.gvfs

```
are on disk. varrun, varock, udev and devshm are in RAM, gvfs-fuse-daemon is from gnome, look for gvfs or gnomevfs on google if you want details, [here is a link]("http://library.gnome.org/misc/release-notes/2.22/#sect:gvfs-gio").

---

