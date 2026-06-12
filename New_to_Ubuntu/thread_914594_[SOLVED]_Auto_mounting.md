---
title: "[SOLVED] Auto mounting"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by masterofthemelee on 2008-09-09
I tried searching for fifteen minutes and couldn't find anything on the forums.  I found something on Ubuntu's community documentation but I'm not sure if its for Ubuntu 8.04 or not.

I have two NTFS partitions and a FAT32 partition, how do I get them to mount on their own when I startup?  How do I get them to not appear on the desktop?

---

### Post by alienexplorers on 2008-09-09
Read this page:
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by graben3 on 2008-09-09
Open a terminal and type :
sudo apt-get install ntfs-3g

Then type this :

sudo fdisk -l

That will tell you what hard drive match what device IE /dev/sd_something like sda1, etc.

Then run :

sudo gedit /etc/fstab

then add this to that file at the end just before CDROM entry (this is an example) :

```
/dev/sda1 /media/MyMountFolder ntfs-3g defaults,nls=utf8,umask=000,gid=46 0 1
```

Save file.

In the example line for FSTAB :

Replace sda1 by the device listed by fdisk -l that match the hard drive you want automounted

Replace /media/MyMountFolder by the folder you created to mount your hard drive in...

Replace gid=46 by :
Go into System -> Administration -> Users and groups
Then click on the unlock button, enter password. Click on Manage groups and doubleclick on the group that match your username.

You will see your group ID, replace 46 by that or any number lower will do it too. The lower the number, the more your HD is accessible to everyone.

Reboot !
That does it all the time for me...hope this helps !

That did it for me !

---

### Post by masterofthemelee on 2008-09-09
Okay, so how do I automount the FAT32 partition?

EDIT:  Nevermind, figured it out.

---

