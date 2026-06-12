---
title: "[SOLVED] GUI vs. CLI"
date: 2008-01-10
forum: Packaging and Compiling Programs
---

### Post by buccaneere on 2008-01-10
When I open MPlayer Movie Player through GUI, I get 2 windows open: 1 for the player's screen, and another for the control console. But, I cannot open a particular file.

When I use CLI to open the player, and include the file name, I get the window that plays the file (playing the file properly), but I get no control console window.

Bug? I don't know. Bug reporting process is too convoluted.

How do I open the executing file, to see the differences in what is going on, such that I can try to modify it myself, and get the control console window to open in sync with the player window???

Thanks..............

---

### Post by philinux on 2008-01-10
I've installed smplayer which is the front end gui for mplayer. I think its better and there's only one window.

---

### Post by stani on 2008-01-11
> **philinux said:**
> I've installed smplayer which is the front end gui for mplayer. I think its better and there's only one window.

smplayer is qt based and is better suitable for kubuntu. For ubuntu you can:
> sudo apt-get install gnome-mplayer

---

### Post by buccaneere on 2008-01-11
> **stani said:**
> smplayer is qt based and is better suitable for kubuntu. For ubuntu you can:

What's the difference between gnome-mplayer, and MPlayer movie player?

---

### Post by rvm4000 on 2008-01-12
> **buccaneere said:**
> When I open MPlayer Movie Player through GUI, I get 2 windows open: 1 for the player's screen, and another for the control console. But, I cannot open a particular file.

When I use CLI to open the player, and include the file name, I get the window that plays the file (playing the file properly), but I get no control console window.

Bug? I don't know. Bug reporting process is too convoluted.

I think it's not a bug. I think when you open "MPlayer Movie Player", probably by clicking on a icon in the desktop or in the menus, you're calling gmplayer, which is mplayer with a GUI. That provides two windows: the video window and the control.

When you type on a console:
```

mplayer movie.avi

```

you're calling mplayer without GUI. That's only the video window.

If you typed:
```

gmplayer movie.avi

```

you'd got the control too.

By the way, *mplayer -gui file* is the same as *gmplayer file*.

> **buccaneere said:**
> What's the difference between gnome-mplayer, and MPlayer movie player?

gnome-player, as well as smplayer, kmplayer... are frontends for mplayer. They actually don't know how to play a file, they run and control mplayer to do it.

---

### Post by buccaneere on 2008-01-12
No joy.

[HTML]chucknb@chucknb-desktop:~$ gmplayer -fs /media/E/HaM.tsp
MPlayer 2:1.0~rc1-0ubuntu9.2 (C) 2000-2006 MPlayer Team
CPU: AMD Sempron(tm (Family: 6, Model: 8, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /media/E/HaM.tsp.
TS file format detected.
VIDEO MPEG2(pid=6690) AUDIO MPA(pid=6691) NO SUBS (yet)!  PROGRAM N. 0
VIDEO:  MPEG2  544x480  (aspect 2)  29.970 fps  15000.0 kbps (1875.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.


Exiting... (Quit)[/HTML]

Thanks for tryin' tho', rvm4...

Anybody else?

---

### Post by rvm4000 on 2008-01-12
Try adding "-vo xv" or "-vo x11".

---

### Post by buccaneere on 2008-01-12
Hi rvm4...

Where in the code string to enter those items?

[HTML]gmplayer -fs /media/E/HaM.tsp[/HTML]

---

### Post by rvm4000 on 2008-01-12
```
gmplayer -fs /media/E/HaM.tsp -vo xv
```

If xv doesn't work, try with x11.

---

### Post by buccaneere on 2008-01-12
> **rvm4000 said:**
> ```
gmplayer -fs /media/E/HaM.tsp -vo xv
```



This one worked; opened file, WITH control console. Thanks!

Exactly what does -vo xv mean in code???

---

### Post by rvm4000 on 2008-01-12
-vo selects the video output driver you want to use. xv is the faster.

Type *mplayer -vo help* to see a list of all video output drivers available.

In the [mplayer manpage](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html) you can find more details.

---

### Post by buccaneere on 2008-01-13
well, not completely solved...

I got .tsp's (mpeg format) playing in MPlayer.

Video is great. Audio changes to at least 3 channels. One channel was good audio, but included a 'narrarative' of the action. Then, a commercial - played good audio only. Then, the movie, and a third channel, with a continuous prompt for language selection of the playing device.

I think this is a codec problem...

What do I need to do?

(the file plays properly in 'Media Player Classic' when Windows is booted)

---

### Post by buccaneere on 2008-01-14
> **buccaneere said:**
> well, not completely solved...

I got .tsp's (mpeg format) playing in MPlayer.

Video is great. Audio changes to at least 3 channels. One channel was good audio, but included a 'narrarative' of the action. Then, a commercial - played good audio only. Then, the movie, and a third channel, with a continuous prompt for language selection of the playing device.

I think this is a codec problem...

What do I need to do?

(the file plays properly in 'Media Player Classic' when Windows is booted)

bumpintodatopagain..........

---

### Post by rvm4000 on 2008-01-14
I don't know much gmplayer (I guess you have to select an audio track).

Have you tried to play the file in smplayer?

---

### Post by buccaneere on 2008-01-17
> **rvm4000 said:**
> I don't know much gmplayer (I guess you have to select an audio track).

Have you tried to play the file in smplayer?

Thanks again there rvm...

You know more than anybody else who chimed in - that's all that matters to me!

Yeah, I've tried about 5 different media players. All will play the file, but with one or another problem - no control console, multiple audio channels playin', etc.

Could be the player, could be codecs, could be playin through ntfs-3g (all 3 'secondary' HDD's with the vids are ntfs formatted, although they ARE mounted properly), could be a combo of the two.

It's time to read the Ubuntu book:-|. In the meantime, we just gonna' have to keep an MS load on one of these boxes, and use Media Player Classic. Wost thing is nothin' has been learned:(

Thanks again..............

---

