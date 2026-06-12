---
title: "green screen"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by jonathan21 on 2008-06-13
when ever I try to play videos where the video should be playing it goes green this happens in mplayer,totem and vlc.

---

### Post by k33bz on 2008-06-13
I have that  same problem with my laptop, except it is a blue screen. But it dont bother me much since I use the exteranl vga port for my monitor and do it that way. However I will be watching this thread closely.

---

### Post by melrom on 2008-06-13
What's the graphics card?

---

### Post by jonathan21 on 2008-06-13
description: VGA compatible controller
                product: UniChrome Pro IGP [VIA P4M890 Chipset]
                vendor: VIA Technologies, Inc.

---

### Post by melrom on 2008-06-13
are you sure you have the correct codecs??

i.e. [http://osdir.com/ml/linux.suse.multimedia/2003-02/msg00004.html](http://osdir.com/ml/linux.suse.multimedia/2003-02/msg00004.html)

Also, have you tried turning off compiz while viewing movies? If you haven't gotten the proper codecs, this website is helpful for the proprietary stuff: [http://www.seafriends.org.nz/linux/dvd_css.htm](http://www.seafriends.org.nz/linux/dvd_css.htm) .

---

### Post by 3rdalbum on 2008-06-13
In VLC and Mplayer, try fiddling with the "Video Output Device". Change it to different things.

I had the same problem when Nvidia released a new version of their drivers. I had to change all my video players to use "X" as the output device.

---

### Post by jonathan21 on 2008-06-17
sorry please explain more what you did with vlc I thinh it might be vga related too thanks for the help by the way

---

### Post by Inxsible on 2008-06-17
Extending 3rdalbum's reply 
1)Open VLC. 
2)Go to Settings>>Preferences. 
3)Select Video>>Output modules
4)Check mark the box for Advanced options (lower right hand corner)
5)From the drop down above, select X11 Video output
6)Start your video

---

### Post by Inxsible on 2008-06-17
For mplayer,
1) Click on the spanner on the left.
2) Go to the Video tab
3) Select x11 X11(Ximage/Shm)
4) Click ok, start the video

---

