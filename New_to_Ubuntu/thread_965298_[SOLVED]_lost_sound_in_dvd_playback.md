---
title: "[SOLVED] lost sound in dvd playback"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-31
This rots---put in gparted disk,it went thru a bunch of what_ever eventually saying to remove disk and reboot. Idid and now I have no sound in playback of dvd movies. What can I do to fix this problem?

---

### Post by Daveth on 2008-10-31
though it may not end up having any relevance at all to your problem, it might be useful background to know what you were using the partitioner for. Were you making a separate /home, or extending? Did the process seem to go through OK? Is your playback failure only with movies, or music as well- do you have any sound or just patchy sound?
rather a lot of questions!

---

### Post by johntravis on 2008-10-31
Wanted to partition my hdd. 80gb for 8.0.4 and 80gb for 8.10

---

### Post by Daveth on 2008-10-31
OK, but the playback failure is only with dvds, or is it with cds/mp3/system sounds etc ???

---

### Post by johntravis on 2008-10-31
only with dvd's

---

### Post by LowSky on 2008-10-31
have you tried reloading the libdvdcss2 dvd driver?

sudo apt-get install --reinstall libdvdcss2

maybe you need the codecs too?

sudo apt-get install --reinstall w32codecs

---

### Post by johntravis on 2008-10-31
I loudly clap to all that replied. I used SPIDERMAN as my entry into dvd playback, had problems with getting sound, which have been resolved, but this gparted thing lost playback sound while trying to play the SPIDERMAN movie but reinstalling w32 codes playback is ok with all but SPIDERMAN. i THINK IT DOESN'T LIKE ME

---

