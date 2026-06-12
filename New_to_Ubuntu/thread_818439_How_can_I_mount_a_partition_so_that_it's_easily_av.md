---
title: "How can I mount a partition so that it's easily available?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by icouldntfindausername on 2008-06-04
I've dedicated a 320 gb hard drive for Ubuntu alone. I therefore created some partitions:

30 gb mounted as /
2 gb as swap
38 gb mounted as /home
250 gb mounted as /downloads

Does that look about right? The partition mounted as /downloads would I like to use for downloads, obviously. And where do all the installed programs go? And the games I install using Wine?

Anyhow, the partition mounted as /downloads would I like to have easily available under the "Places" menu at the start line. Right now I have to go to Places>computer>filesystem>downloads to access the partition. How can I make this appear under "Places" just like the Home folder?


Thanks.

---

### Post by Duck2006 on 2008-06-04
For mounting linux drives.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

For windows drives.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by sayakb on 2008-06-04
Can you post the output of:
```
df -l
```

---

### Post by sayakb on 2008-06-04
I don't know how you have made the /download mountpoint :)
Anyway, if you don't know the path, open the location in Nautilus and click on the Text toggle button towards the left of the location bar. Copy the location and create a Launcher for it on the desktop. Specify the Launcher type as Location, and enter Location as shown by Nautilus location bar and whatever name you want.

---

### Post by icouldntfindausername on 2008-06-04
> **LinuxIsInnovation said:**
> Can you post the output of:
```
df -l
```
Ok, here you go:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             29293564   2532128  26761436   9% /
varrun                 2027240       104   2027136   1% /var/run
varlock                2027240         0   2027240   0% /var/lock
udev                   2027240        80   2027160   1% /dev
devshm                 2027240        36   2027204   1% /dev/shm
lrm                    2027240     43044   1984196   3% /lib/modules/2.6.24-16-generic/volatile
/dev/sda5            244132256     32840 244099416   1% /downloads
/dev/sda4             37133068    341468  36791600   1% /home
/dev/sdb2            511999996 323300444 188699552  64% /media/DOWNLOADS
tmpfs                  2027240     43040   1984200   3% /lib/modules/2.6.24-18-generic/volatile
gvfs-fuse-daemon      29293564   2532128  26761436   9% /home/<user>/.gvfs
```

> **LinuxIsInnovation said:**
> I don't know how you have made the /download mountpoint :)
Anyway, if you don't know the path, open the location in Nautilus and click on the Text toggle button towards the left of the location bar. Copy the location and create a Launcher for it on the desktop. Specify the Launcher type as Location, and enter Location as shown by Nautilus location bar and whatever name you want.

I really have no idea how I made that either, I just wrote it during setup (without having any idea what it meant :) ). But it doesn't seem to work, I can't copy anything to it.

I tried following the guide over here. However, I can't quite figure out what to do with the /etc/fstab file. Here's how it looks like now, what should I edit?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=d7028417-79e6-42c6-8d62-56baadbe4cde /               reiserfs notail,relatime 0       1
# /dev/sdb5
UUID=554a6db4-20ca-4014-a8c4-e5baa754bfbd /downloads      reiserfs relatime        0       2
# /dev/sdb4
UUID=5d727bfc-d4ff-419f-94db-a4c6408aec0c /home           reiserfs relatime        0       2
# /dev/sdb2
UUID=823ebb81-137d-4b97-a75f-f19d9720dde3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by icouldntfindausername on 2008-06-04
Ok, I actually managed to make it work now :D . I mounted the /downloads partition successfully and I made a launcher for it at the desktop. However, I still want to have a shortcut at the start line under "Places" along with Music, Pictures, Documents etc. How do I do that?

---

### Post by Duck2006 on 2008-06-04
Use the mount point under 

/Media/mount point

I think that should put it there.

---

### Post by icouldntfindausername on 2008-06-04
> **Duck2006 said:**
> Use the mount point under 

/Media/mount point

I think that should put it there.

Where should I put this mount point? In a terminal? :confused:

---

### Post by sayakb on 2008-06-04
> **icouldntfindausername said:**
> Ok, I actually managed to make it work now :D . I mounted the /downloads partition successfully and I made a launcher for it at the desktop. However, I still want to have a shortcut at the start line under "Places" along with Music, Pictures, Documents etc. How do I do that?
Just open the /downloads folder and Press Ctrl+D
It should appear in the Places then.

---

### Post by icouldntfindausername on 2008-06-04
Thanks, that worked well :)

I might just be a bit much of a perfectionist now, but I would like to give it a different name under the menu "Places". Is there any way I could do that without changing the name of the actual mount point?

---

### Post by sayakb on 2008-06-04
Yes, open a Nautilus Window. Goto Bookmarks->Edit Bookmarks.
Select that one and change the name!

---

### Post by icouldntfindausername on 2008-06-04
Aha, thank you :KS

I've got only one last question now. I've got some NTFS partitions that have been automatically mounted by ubuntu. I can access these through "Places". However, once I open one of them a shortcut appears at my desktop. These are rather annoying, and they are gone after a reboot. Is there any way to stop it from creating these shortcuts every time??

---

### Post by sayakb on 2008-06-04
Yes: Open gconf (Press Alt+F2 and type gconf-editor)
Navigate to /apps/nautilus/desktop and **uncheck** volumes_visible

---

### Post by icouldntfindausername on 2008-06-04
Thanks for quick replies, that worked like a charm!

Turns out though I have one more question. How can I make the NTFS partitions automatically mount on boot up? Because if they don't my shortcuts under "Places" will not appear, unless I open the partitions myself after boot up. After that they appear normally.

---

### Post by sayakb on 2008-06-04
Sorry for the late reply! Add this to your fstab:
```
/dev/sda5 /downloads ntfs users,gid=users,ro,umask=0222,utf8=true 0 0 
```
Assuming that /downloads is NTFS.

---

### Post by icouldntfindausername on 2008-06-05
Ok, that seemed to do the trick, but I seem to have the weirdest problems... Here's the problem:

I've got two hdds, one IDE (320 GB) and one SATA (750 GB). I've got 5 linux partitions on the IDE drive, and 3 NTFS partitions on the SATA drive. one drive is recognised as sda and the other one as sdb. However, they seem to switch on every other bootup where suddenly the other drive is sda and the other one is sdb. This causes a problem, obviously. I add this to my fstab file:
```
/dev/sdb2 /media/DOWNLOADS ntfs users,gid=users,ro,umask=0222,utf8=true 0 0
```
But on the next bootup the sdb hdd suddenly has change to sda. :confused: Why does that happen? Because of that the line I added will not work every time.

---

### Post by Duck2006 on 2008-06-05
> **icouldntfindausername said:**
> Ok, that seemed to do the trick, but I seem to have the weirdest problems... Here's the problem:

I've got two hdds, one IDE (320 GB) and one SATA (750 GB). I've got 5 linux partitions on the IDE drive, and 3 NTFS partitions on the SATA drive. one drive is recognised as sda and the other one as sdb. However, they seem to switch on every other bootup where suddenly the other drive is sda and the other one is sdb. This causes a problem, obviously. I add this to my fstab file:
```
/dev/sdb2 /media/DOWNLOADS ntfs users,gid=users,ro,umask=0222,utf8=true 0 0
```
But on the next bootup the sdb hdd suddenly has change to sda. :confused: Why does that happen? Because of that the line I added will not work every time.

Try

/dev/sdb2 /media/DOWNLOADS ntfs nls=utf8,umask=0222 0 0

---

### Post by icouldntfindausername on 2008-06-05
Wow, that actually worked. Thanks! Now my 750 gb disk is always sda and the 320 gb always sdb and all the partitions automount at startup :guitar:

---

