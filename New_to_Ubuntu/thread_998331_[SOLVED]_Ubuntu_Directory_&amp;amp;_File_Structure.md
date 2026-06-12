---
title: "[SOLVED] Ubuntu Directory &amp;amp; File Structure"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2008-11-30
I’m new to the linux operating system and to Ubuntu. I have my SAMBA SERVER SYSTEM setup using an Athlon 1800+ on a ASUS A7N266-C motherboard. The system hard drive is an 80G hard drive and is now sda1.

I plan to add 3 additional IDE hard drives to this system.
[LIST]
[*] sda1 – ubuntu8.04 Server Edition -- 80g
[*] sdb1 - Music   -- 250g
[*] sdb2 - Photos   -- 250g
[*] sdc1 – Movies -   750g
[*] sdd1 – TV Recordings - 500g
[/LIST]

Looking at this article:

[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)

[LIST]
[*]  /media - mounted (or loaded) devices such as cdroms, digital cameras, etc. 
[*]  /mnt - mounted file systems
[/LIST]

It seems to me that it will be adequate to mount these new drives in either* /mnt *or* /media*, but* /mnt *would be my preferred directory.  Anyone with a similar setup care to comment on their setup. The sole purpose of the server is to stream music, photos and movies throughout the house.

DOES THIS SOUND LIKE A GOOD PLAN?

CarolinaGuy

---

### Post by jgoguen on 2008-12-01
That seems somewhat wrong to me.  I believe Ubuntu follows the filesystem hierarchy standard, where /mnt is for temporarily mounted file systems and  /media is for mounting removable media.  For what you want to do, following the FHS, I would say everything should be mounted under /srv.  I prefer to have subdirectories under /srv denote services provided (ftp, www, smb, etc.) but there's no standard for that.  You could probably do /srv/photos/, /srv/music/, etc.

That's of course if you want to follow the standard.  Nothing prevents you from making new directories under /media or /mnt and mounting everything there.  I admit to breaking the standard by forcing my USB key to mount in a directory inside my home directory :)

---

### Post by louieb on 2008-12-01
Sounds fine to me. Stuff mounted in /media gets a shortcut automatically  added to the desktop. Not sure about /mnt. Guess I should try it.  anyway as jgoguen says Ubuntu more or less follows the [Filesystem Hierarchy Standard]("http://www.pathname.com/fhs/pub/fhs-2.3.html")

---

### Post by hyper_ch on 2008-12-01
you can mount it wherever you want :) however I would put it all into /media :)

---

### Post by CarolinaGuy on 2008-12-02
Jgoguen, louieb and hyper_ch

THANK YOU for your replies and comments. I’m new to this and wasn’t aware yet of the Filesystem Hierarchy System. Another thanks to louieb for that suggestion. I will read it and ponder each suggestion.

I haven’t looked at UBUNTU STUDIO, anyone using Ubuntu Studio care to comment on what directory they used to stored and mount their movies, TV shows, photos and music. 


THANKS again.

CarolinaGuy

---

