---
title: "[SOLVED] Change default user on  live session"
date: 2008-10-26
forum: Other OS Talk
---

### Post by Nonno Bassotto on 2008-10-26
I'm trying to create a customized version of ubuntu. The last thing missing is to remove all occurrences of the name ubuntu, at least in the user interface.

I'm trying to find out how to rename the default user of the live session, which for now is called ubuntu@ubuntu. I've been not able to find where this name comes from. Does anyone know?

---

### Post by init1 on 2008-10-27
The host name (it's the first "ubuntu" in "ubuntu@ubuntu") can be changed by editing /etc/hostname.

---

### Post by Nonno Bassotto on 2008-10-27
Unfortunately the user is created during boot for the live session, so the default name is stored somewhere else. It seems that it should be under /etc/casper.conf, at least from what I could understand of the boot scripts for the live cd. But unfortunately changing the appropriate lines there didn't work :(

---

### Post by chris4585 on 2008-10-27
I have a similar problem (ok the same problem) but I think I know where to look

/etc/casper.conf <-- never worked for me

another place is

/usr/share/initramfs-tools/scripts

Thats all I can say since I actually haven't had success in editing the casper file in that folder, maybe you might who knows

---

### Post by Nonno Bassotto on 2008-10-28
I solved this. You just need to edit /etc/casper.conf and then rebuild initrd.gz using mkinitramfs and copy the resulting image on the cd.

---

### Post by chris4585 on 2008-10-28
I'll try that, thanks

---

### Post by feenana on 2008-10-30
[img]http://www.top1gaming.com/cosplay/Goddess-16.jpg[/img]See more pics [[color=#800080]click here[/color]](http://www.top1gaming.com/coscontent-45-16.html).  Want to see more [[color=#800080]cosplayer[/color]](http://www.top1gaming.com/cosplayer.php) ? Show yourself on our forum [[color=#800080]click here [/color]](http://www.top1gaming.com/forum/forumdisplay.php?fid=29).**Recommend : **[[color=#0000ff]Chrono Trigger's Ayla [/color]](http://www.top1gaming.com/coscontent-130.html)   [[color=#0000ff]Legend of Zelda cosplay[/color]](http://www.top1gaming.com/coscontent-51.html)

---

