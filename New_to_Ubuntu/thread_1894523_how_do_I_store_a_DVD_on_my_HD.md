---
title: "how do I store a DVD on my HD?"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-12-12
Hi Ubuntu Community:

I bought a nice DVD ("The Snowman") and want to learn how to store the movie on my computer so that I can play it back when I want without using the DVD disk.

How do I do this?

Thank you!
Phil de Duluthistan GA

---

### Post by jtarin on 2011-12-12
You could copy it as an .iso using GnomeBaker or one of the other CD/DVD burning applications and mount it on a virtual drive using GMountISO.That's one way.

---

### Post by RealityMaster on 2011-12-12
I use Handbrake, it's IMHO the best conversion out there, unless you have lots of extra disk space and want to store the whole ISO, however this also presents problems like watching it on other machines (XBMC, Roku...) 

[http://handbrake.fr/](http://handbrake.fr/)

---

### Post by yetiman64 on 2011-12-12
> **jtarin said:**
> You could copy it as an .iso using GnomeBaker or one of the other CD/DVD burning applications and mount it on a virtual drive using GMountISO.That's one way.
I personally use this method OP (ie using .iso disc images) for storing DVDs, note that some media players, particularly VLC, can play a video dvd straight from the iso and you don't need to mount it as such.

---

### Post by N00b-un-2 on 2011-12-12
there are literally dozens of ways to accomplish what you're after.

To create a video file from the disk:

1)  Use MakeMKV and rip it as a lossless .MKV video file
2)  Use dvdrip to convert it to AVI
3)  Use Thoggen to convert it to OGV
4)  Use Handbrake to rip it as any format
5)  Use VLC to rip it as any format

To create an .iso from the disk:

1) sudo dd if=/dev/cdrom of=/home/usr/snowman.iso
2) K9copy
3) DVD95
4) Gnome Baker
5) Nero Linux

... just to name a few...  My personal preference is to rip any and all movies as .mkv using MakeMKV and then convert the .mkv to .avi using Winff.  That way I always get consistent near DVD quality video files that are in a homogeneous format.

---

### Post by Old Jimma on 2011-12-13
Wow!!!

What terrific answers!!

I liked them all!

Because I'm such an old geezer now, I always go for the easist method... I like reading the .iso using VLC... very, very easy!

Many thanks to my Ubuntu friends!

Sincerely,
Phil de Duluthistan, GA

---

### Post by N00b-un-2 on 2011-12-13
what method did you use to rip the .iso file?  I love using dd because... well, its geekier than using the GUI!

---

