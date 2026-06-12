---
title: "Windows XP Ubuntu dual boot problems"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by echris1 on 2008-05-07
I have been running a Ubuntu/XP Dual boot system for the last week or so and everything has been fine.  I recently followed some instructions for how to get NTFS drives to automount once ubuntu starts up, and since then there has been a problem.  When I reboot and select Windows XP from the grub menu, the screen goes black and the machine reboots itself.  Same thing for safe made with windows.  I tried restoring the old fstab, which was fstab-pre-ntfs-config, but the only thing that did is create the same folders in /media/ with underscores after them (I now have Storage and Storage_, but Storage won't let me access it)

Is there a way to clean up the /media/ folder and more importantly, what do I need to do to get my XP to boot up again?

Thanks,
echris1

---

### Post by tjwoosta on 2008-05-07
could you post a link to the instructions you were folowing ?

---

### Post by echris1 on 2008-05-07
[http://ubuntuforums.org/showthread.php?t=778702](http://ubuntuforums.org/showthread.php?t=778702)

I installed ntfs-config and used it to automount the ntfs drives, including the windows partition.  Before the windows partition didn't have a name, just showed up as 98.8GB Media or something like that, but when I used ntfs-config it made me name it so I named it windows.  Is it possible that this is causing the problem?

---

### Post by tjwoosta on 2008-05-08
its possible i suppose..

sry but i dont really know how to help you here 
(the way that i use to automount my windows partition is a bit different, it involved manually editing my fstab file)

have you checked your /boot/grub/menu.lst to make sure it is still pointing to the right partition?

theres gotta be someone here that can help you

---

