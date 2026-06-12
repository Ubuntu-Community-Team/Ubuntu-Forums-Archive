---
title: "[SOLVED] when i play mplayer, pidgin sounds stop"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by NAWSE on 2008-11-24
so lots of my IMs are going unnoticed, as i always watch movies. i messed with sounds and switched to alsa, pulse and all- both on my laptop and in pidgin sound preferences- but none of the combinations seem to work.

---

### Post by nhasian on 2008-11-24
follow this guide to fix your audio problem:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by NAWSE on 2008-11-24
when i gave

 mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/

i got this error

cp: cannot stat `/home/rahul/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory

---

### Post by NAWSE on 2008-11-24
when i gave

 mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/

i got this error

cp: cannot stat `/home/rahul/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory

---

### Post by nhasian on 2008-11-24
like the instructions say, that is okay.  continue with the rest of the instructions :)

---

