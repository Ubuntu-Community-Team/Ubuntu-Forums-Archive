---
title: "Backing up DVDs takes 14+ hours"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by mishathegoat on 2008-11-01
Hey everyone,

I'm trying to backup some (legal) DVD Movies and everytime I pop in a DVD to back it up it takes 14 or more hours..

I've tried almost all of the DVD Backup tools.. OGM-Rip, AcidRip etc

I have an Intel Pentium dual-core processor 1.73 GHz 2 GB DDR

---

### Post by bumanie on 2008-11-01
Try k9 copy to shrink and k3b to burn. > sudo apt-get install k9copy > sudo apt-get isntall k3b They are both kde programs, but work fine in gnome.

---

### Post by stmiller on 2008-11-01
Video encoding is very cpu intensive. Handbrake should work faster.  It is the only multithreaded DVD-mpeg4 encoder out there at the moment. This page has a recent snapshot with a link to an Ubuntu .deb:

[http://handbrake.fr/?article=snapshot](http://handbrake.fr/?article=snapshot)

---

### Post by stinger30au on 2008-11-01
install wine from here
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

install dvdfab free 
[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

grab a copy of dvd shrink
[http://www.dvdshrink.org/](http://www.dvdshrink.org/)

intall the programs. rip the dvd in full to the hdd with dvdfab. then run dvdshrink and point it to the files created with dvdfab an it wil compress then to fit on a 4.7 gig dvd

get dvdshrink to save the data to hdd

burn the output files from dvdshrink to dvd with k3b

done

---

### Post by mishathegoat on 2008-11-02
I was actually interested in backing up the DVD to an AVI file . I installed Wine and DVDShrink.. I used DVDShrink to back it up and now I have a bunch of VOB, BUP, and IFO files.

What do I do with these files?

Sorry about the trouble.. Thanks for your help.

---

### Post by bumanie on 2008-11-02
Install devede, it handles nearly any type of video file type and can output to .avi. > sudo apt-get install devede

---

### Post by 3rdalbum on 2008-11-02
The speed of encoding depends on what codec and what settings you use. Fourteen hours is extreme; try using a different codec, a higher bitrate, and no 2-pass encoding.

---

