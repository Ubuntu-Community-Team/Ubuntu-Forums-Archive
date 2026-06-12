---
title: "Still getting phantom blank disc icon"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Jonga on 2008-07-31
Hi all, I've been trying to beet this problem for a while, my benq dvd drive worked fine in 7.10 but ever since upgrading to 8.4 I've had a phantom blank disc icon on my desktop and my cd/dvd drive doesn't function at all on ubuntu but works fine on windows so I'm pretty sure it ain't the hardware.  I've only seen reports on this in a couple of other threads,([http://ubuntuforums.org/showthread.php?t=740143](http://ubuntuforums.org/showthread.php?t=740143)) and their problems were fixed by the updates, I've installed all the updates on mine to no avail.
  Anyways, here's my fstab file, any help would be greatly appreciated.

[PHP]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a20a59cd-6f1f-4a65-a39b-3c657199b6da /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=07ccda61-a0dc-4e21-93b8-c3c1cd30f5cd none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
jonga@jonga-desktop:~$ 

[/PHP]

Thanks,
Jonga

---

### Post by bobnutfield on 2008-07-31
Have you tried to mount it on the command line?  Try this:

> sudo mount -t iso9660 /dev/hdc /mnt

The change to the /mnt directory and check if it is mounted.  If it is not, the mount command will give you an error message that will help us track down the problem.

---

### Post by Jonga on 2008-07-31
Just did that and got this

[PHP]
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/PHP]

I'm afraid I know next to nothing of command line as I'm very new to the world of linux.

---

### Post by Jonga on 2008-07-31
Bah, I've been reading around and it seems a lot of folks have still been having issues making their dvd/cd drives work with the 8.04 and I'm not enough of a geek to know how to debug my own stuff so screw it.  I'm throwing in the ubuntu towel until next release, my eyes are sore because I've been looking on forums for so long trying to find a fix.

/end rant

:-({|=

---

### Post by Jonga on 2008-08-02
You know what? I feel kind of stupid now, I put that earlier command in today
[PHP]sudo mount -t iso9660 /dev/hdc /mnt [/PHP] and my dvd drive actually started working, it reads but it still won't record with any of my burning programs except cd/dvd creator.  And when I take a disc out of it and put another one in, it'll show them both as still being on my desktop.  When I restart my computer the drive goes totally back to the way it was before, not functioning and registering a blank disc on my desktop.  I guess I'll keep ubuntu on this partition, I just like it too much to give it up now, and I'll just have to resort to my windows partition whenever I need to burn an audio disc or dvd.

---

### Post by Rocket2DMn on 2008-08-02
When you boot the computer, is there a cd or dvd in the drive that you later unmount/eject?  If so, this is a known bug - [https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/94605](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/94605)

---

### Post by Jonga on 2008-08-02
When I start the computer with any media in the dvd drive it doesn't even register it as being in there, but instead gives me a blank disc icon on the desktop.
When I run this in terminal like bob suggested:
> sudo mount -t iso9660 /dev/hdc /mnt 

I'm able to read the disc, but it'll still say the disc is still in there if I eject it and put another one in, It'll also register the new one on my desktop.  I also noticed while I can read the disc that's in the dvd drive, I can't burn discs with any of my regular programs that I could in 7.10 except cd/dvd creator.

---

### Post by Rocket2DMn on 2008-08-02
Is any output appearing in dmesg for the drive?
```
dmesg
```
Because of the bug when booting the computer with a disc in the drive, try to avoid doing that.  Does the problem still exist if the computer boots normally without a disc in the drive?  Also, because of the writing problem, there may either be a problem with the hardware or a lack of complete support for your drive in linux.

---

