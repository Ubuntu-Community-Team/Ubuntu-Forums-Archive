---
title: "Upgraded to Hardy - but no sound"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Spoken on 2008-05-29
so after i upgraded to 8.04 from 7.10. i dont have sound anymore. and im not sure what to do. ive tried a lot of suggestions so far,

including following this **[GUIDE]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")**

can anyone help?

---

### Post by cmnorton on 2008-06-02
What's in your logs (/var/log), especially syslog and messages? Is there anything interesting in the output of dmesg?

You may have to play around with this file. Oddly I did not have to do this when I installed Hardy, but when re-installing 7.10, I did have to put this back:

The file name is 

/etc/modprobe.d/alsa-base

I added this line at the end:

options snd-hda-intel model=thinkpad-t61p

This problem could be caused by something else entirely which could be further triaged by your posting anything interesting you find in dmesg or your logs.

Edit:
----------------------------------------------------------------------------
You would need to put your model where thinkpad-t61p is now. I just guessed at model number and kept things lower case.

---

### Post by ZootHornRollo on 2008-06-02
maybe not a great deal of help but i had issues when i installed 8.04 too.

i couldn't get my m-audio 2496 to produce any sound at all.

installed 7.10, works perfectly.

seems to be issues with 8.04 and some soundcards.

---

### Post by almabeck on 2008-06-02
I have a Dell Inspiron 1420. When I upgraded to 8.04, I also lost sound. Nothing I found on these forums worked, but when I did a clean install, everything magically worked again! I did forget to backup one folder, so if you go this route, don't forget to save everything you want to keep (on a disk or some place other than your computer).

---

### Post by sammydadams on 2008-06-04
yeah...check out modprobe.d i have a vaio and had to edit it to get any sound...it initially worked on gutsy, but had no jack sense (which proved to be a royal pain in the butt to fix) but on Hardy, i just put 
options snd-hda-intel model=vaio
into modprobe.d and everything works wonderfully including jack sense and the special volume buttons and everything...

---

