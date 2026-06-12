---
title: "Mounting a Windows NAS Permanently"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by kc5hwb on 2013-04-08
I have searched this forum and I am actually able to mount my NAS using Gigolo.  It seems to work fine, the only "issue" is that is won't let me rename the link that appears on my Desktop.  I am a bit ADHD on that and I would like to have the link named something that makes sense instead of "volume_1 on 192.168.x.x"

Thanks Morbius1 for this thread:
[http://ubuntuforums.org/showthread.php?t=1590825&p=9941016#post9941016]("http://ubuntuforums.org/showthread.php?t=1590825&p=9941016#post9941016")

The other way I would like to know how to do it, just for my own knowledge, is with adding the line to the /etc/fstab file.  My NAS is a DLINK 2-drive setup, which is currently RAIDed as Mirrored (RAID1) with 2-1.5TB drives.  It doesn't require a password to access the share.  I could set one up in the GUI of the NAS itself, but I don't intend to do this, so the idea of having my password written in my /etc/fstab file isn't an issue to me.  Plus if I mount the NAS folder into a folder that I create in my /home directory, everything will be all in the same place, nice and pretty.

Thanks for the help.

---

### Post by Habanero101 on 2013-04-08
Hi, I did something similar to this about a month ago. The difference was my windows backup drive is in the same PC as Ubuntu, so I'm not sure if that'll make any difference. These 2 threads helped me out a lot; if you need any more help with this, just ask.

I did exactly what you are asking about, adding lines to fstab.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
check Manual Setup Help

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
contains some good examples under Manual Configuration

---

### Post by Morbius1 on 2013-04-09
You can give this example a shot:

First, make sure the following package is installed:
```
sudo apt-get install cifs-utils
```

Create a mount point in your home directory:
```
mkdir /home/kc5hwb/NAS
```
Add the following line to your fstab:
```
//192.168.x.x/volume_1 /home/kc5hwb/NAS cifs guest,uid=1000,nounix,iocharset=utf8,file_mode=0666,dir_mode=0777 0 0
```
Then run the following command to see if it mounts the way you want it to mount:
```
sudo mount -a
```

*[COLOR=#0000cd]**Note**[/COLOR]*: Using Gigolo to automount shares does have one advantage over the fstab method however. If the NAS is not up and running when you boot, fstab will find nothing to mount on the NAS and it never goes back to try it again. Gigolo will try to mount the share every 60 seconds ( user adjustable ) until mounting is successful.

---

### Post by kc5hwb on 2013-04-09
> **Morbius1 said:**
> 

*[COLOR=#0000cd]**Note**[/COLOR]*: Using Gigolo to automount shares does have one advantage over the fstab method however. If the NAS is not up and running when you boot, fstab will find nothing to mount on the NAS and it never goes back to try it again. Gigolo will try to mount the share every 60 seconds ( user adjustable ) until mounting is successful.

I like using Gigolo, for sure.  I just wish it would name the mountpoint folder on my Desktop to something more standard.

---

