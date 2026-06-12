---
title: "Rip a DVD"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by jfbays on 2008-08-20
I have several questions concerning video and Ubuntu (8.04).  But, for now, I will begin with only one question:  Is there a reasonable (Ubuntu) way to rip a DVD/VOB file to the hard drive -- something like what DVDShrink does?  If the answer is yes, and if someone gives me some practical advice, I will move on to other questions later...  

At the moment, I am using "acidrip" to rip and encode a DVD (into an avi file), but, somehow, 275 minutes to rip one (1) DVD/VOB does not seem reasonable.  Is there a better method?

Thanks

---

### Post by cyrille-borne on 2008-08-20
If you want to rip DVD to DVD like dvdshrink, you can use k9copy or dvd95.
If you want to rip DVD to xxx live avi or mkv, you can use OGMRip. 

For 275 minutes you can rip in x264 or increase the mega of the output

---

### Post by Vivaldi Gloria on 2008-08-20
I use dvd::rip because it can rip multithreaded. If you have a core2duo or a quadcore then use it. To enable multithreaded encoding in dvd::rip you need to add a cluster from the settings.

Once in a blue moon, dvd::rip cannot handle a dvd with a weird encryption and I use dvdfab (+ wine) to get rid of the encrption and copy the contents to disk. Then I encode it using dvd::rip.

---

### Post by theilliniguy on 2008-08-21
I'm trying to play ripped DVD (all vob files in a video_ts folder) with VLC and Totem-Xine but cannot get the entire folder to play.  I can open with VLC any of the main vob files and they will play.  None will play with Totem.

Regualr DVD discs (before ripped) play fine in either ap.

What am I missing?

---

### Post by neurostu on 2008-08-21
a great way to copy the DVD to disk is to use:
```

cat /dev/cdrom > filename.iso

```

Its something like that... I use it to rip ISO's of any digital media! its fast and great

note: you might need to adjust /dev/cdrom to whatever your drive is.

I know that this doesn't transcode the video at all... its just a pure ISO rip.

---

### Post by jfbays on 2008-08-22
My solution is to give up trying to do video of any kind (except for watching) with Ubuntu, at least for now.  I'm sure things will eventually get better, but, for now, there are too many good (and free) video tools in the Windows world for me to endure what the Linux/Ubuntu world has to offer at the moment...

---

### Post by dirkjot on 2008-11-03
although there are indeed great video tools for windows, the unix tools are also of very good quality.  just don't expect to use the exact same tool in the 'for unix' flavor, as that doesn't exist.   avidemux is the only tool that I know that is cross-platform, and it cannot rip dvds.  

dvd:rip is very good and easy to use (if you simply click through all kinds of settings that you don't want to know about).

---

### Post by o.besner on 2008-11-03
Have a look at

1) h264enc (not in synaptic, but very powerful and easy. Console script. You answer questions with yes or no). Simply run "h264enc -iso" and it will dump the movie where you want.
2) DVD95 and K9Copy can do simple DVD dumps like you asked for.
3) libdvdcss will decode the DVD on the fly for you if you don't need to dump.
4) OGMrip is easy to use. Might be interesting if you are starting to encode movies.
5) Avidemux is more advanced, but you can do what you want with it.
6) The popular Handbrake ([www.handbrake.fr](www.handbrake.fr)) is also available on Linux. Hard to compile, but if you have a 32-bit install they have a pre-compiled .bin . It's Command-line, but you can compile a graphical user interface if you want. Have a look at this : [http://andrewalliance.wordpress.com/2008/08/29/handbrake-with-gui-ubuntu-linux-how-to/](http://andrewalliance.wordpress.com/2008/08/29/handbrake-with-gui-ubuntu-linux-how-to/)

These are all tools that I've used or use. Linux has excellent DVD ripping tools once you get to know them. Nothing beats MeGUI though... 

Oh yeah, if you really want to speed up encoding, get a decent (as in more recent) version of mplayer/mencoder and x264. Especially if you are not running Intrepid Ibex. Still, mencoder 1.0rc2 is waaay too old.

If you want to compile it yourself : [http://ph.ubuntuforums.com/showthread.php?t=558538](http://ph.ubuntuforums.com/showthread.php?t=558538)

If you want a repository (easier), have a look at : [http://smplayer.berlios.de/forums/viewtopic.php?pid=3466](http://smplayer.berlios.de/forums/viewtopic.php?pid=3466)

---

### Post by billgoldberg on 2008-11-03
> **jfbays said:**
> I have several questions concerning video and Ubuntu (8.04).  But, for now, I will begin with only one question:  Is there a reasonable (Ubuntu) way to rip a DVD/VOB file to the hard drive -- something like what DVDShrink does?  If the answer is yes, and if someone gives me some practical advice, I will move on to other questions later...  

At the moment, I am using "acidrip" to rip and encode a DVD (into an avi file), but, somehow, 275 minutes to rip one (1) DVD/VOB does not seem reasonable.  Is there a better method?

Thanks

I use k9copy and did a little how to on how to use it to rip a video as .avi (xvid).

[http://linuxowns.wordpress.com/2008/10/07/how-to-rip-a-dvd-in-ubuntu-to-avi-the-easy-way/](http://linuxowns.wordpress.com/2008/10/07/how-to-rip-a-dvd-in-ubuntu-to-avi-the-easy-way/)

A 23 minute episode took 30 minutes to rip and encode using k9copy.

---

