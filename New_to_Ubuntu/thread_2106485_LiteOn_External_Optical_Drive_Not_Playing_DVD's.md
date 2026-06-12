---
title: "LiteOn External Optical Drive Not Playing DVD's"
date: 2013-01-19
forum: New to Ubuntu
---

### Post by Bombesly45 on 2013-01-19
HI there, 

got this dvd/cd rewritable external drive from Life-on eSAU108. I'm running Ubuntu 12.04 with kde and I'm having problems with it. 

After looking around for a wile I've enabled the dvd reading function and installed new packages for it. At the beginning it read fine I managed to watch few dvds however I got an indication error saying that an internal crash occurred. I was a bit surprised but everything was still working fine except the dvd isn't recognized any more. I checked and the bus and it is detected that way but not in the device window.

I looked for a thread with the same problem but it looks like at least the dvd is detected, not for me through. 

Any one got an idea?

---

### Post by overdrank on 2013-01-19
Hi and welcome, I have moved your post to it's own thread. No need to revive a three year old thread. :)

---

### Post by audiomick on 2013-01-19
Have you restarted the machine since the crash? If not, try that. It might find everything again.

---

### Post by Bombesly45 on 2013-01-19
Thanks for that :)

yep I tried that a few times but nothing. Don't know what else to do.

---

### Post by mapes12 on 2013-01-19
Did the crash occur with Movie Player? That happens to me. Try VLC instead. It's in Software Centre.

---

### Post by Bombesly45 on 2013-01-19
was using vlc, before it happened I had to go into vlc and into the open dialogue box at which point the dvd would start spinning and I had access. But I'm just not able to see the device any more.

---

### Post by mapes12 on 2013-01-19
A solved problem as yours here:

[http://ubuntuforums.org/showthread.php?t=1302449](http://ubuntuforums.org/showthread.php?t=1302449)

and try Googling > ubuntu dvd codecs

---

### Post by Bombesly45 on 2013-01-19
Thanks, I had a look at that but the problems on the thread you are proposing all include the fact that the device mount. 

Mine doesn't show as mounted, although it is present on the bus when requested via the terminal.

After keying sudo lshw -short: the result show as followed:


/0/2/0.0.0             /dev/cdrom  disk        eSAU108   2

Wich means that it is there but cant access it trough kde gui,

Sly.

---

### Post by Bombesly45 on 2013-01-24
Hi there well am out of the woods, the dvd is finaly reconized. I've done nothing extra. Not sure what happend, thanks to all involved.

---

