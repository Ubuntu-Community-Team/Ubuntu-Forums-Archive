---
title: "HOWTO: HD (X264) Playback on Slow CPU"
date: 2007-12-02
forum: Outdated Tutorials &amp; Tips
---

### Post by nlindblad on 2007-12-02
After some experimenting I finally got a 1080p video working on my system (Pentium 4 3.4GHz 1GiB RAM nVidia GeForce 6800). I thought some people could possibly be interested in reading how I solved the audio-latency/heavy CPU-usage problems.

Mplayer insisted that my system was too slow so I took its advice and tried to lower the settings. I have now found a functional setup that gives me a decent CPU-load and acceptable quality.

**[SIZE="4"]Step 1[/SIZE]**
[SIZE="2"]**Create the file */usr/local/bin/mplayer-x264***[/SIZE]

```
sudo -e /usr/local/bin/mplayer-x264
```

```
#!/bin/bash
nice -n 0 mplayer -vfm ffmpeg -lavdopts lowres=2:fast:skiploopfilter=all:threads=8 "${1}"
```

**[SIZE="4"]Step 2[/SIZE]**
[SIZE="2"]**Make it executable**[/SIZE]

```
sudo chmod +x /usr/local/bin/mplayer-x264
```

**[SIZE="4"]Step 3[/SIZE]**
[SIZE="2"]**Play your video**[/SIZE]

```
mplayer-x264 *.mkv
```

**[SIZE="4"]Newer systems (try this)[/SIZE]**
[LIST]
[*] Lower the ***lowres*** option to **1** or **0**
[/LIST]

---

### Post by Regenpak on 2008-01-02
*My* Pentipruttel is even slower at 2.8 GHz. I tried overclocking the thing but it didn't help much. This fix improved things significantly but didn't completely solve it. 720p is acceptable but 1080p is still out of my league. Guess I *really* need a faster box...

Anyway, as I wanted to use my desktop and not the command line to start my movies I created a new launcher. In the "name" box I entered "Mplayer x264", in the "Command" field "nice" then clicked OK. Then I brought up properties, and in the "Launcher" tab entered in the "Command" field ```
nice -n 0 gmplayer -vfm ffmpeg -lavdopts lowres=2:fast:skiploopfilter=all:threads=8
```
Note that I used gmplayer to get the Mplayer UI on my desktop and do not pass a filename to it. I will just open it from Mplayer and browse like I always did.

In the desktop launcher file (in ~/Desktop) I added somewhere ```
Icon=mplayer.xpm
``` as the Mplayer icon is not available in the pick list.

TJ

---

### Post by Gaxnys on 2009-12-31
Sry for late post, but I've got the same problem, and almost found a solution to it.

Try -autosync 30 (start mplayer from terminal, of course). Greatly improved the performance om my P4 (2,62Ghz) system when playing 1080p. Still, after a short time of playback, mplayer complains about too many video packets in the buffer. I, for some reason, then tried to add the flag -nosound, and what do you know, almost perfect playback.

---

### Post by mkw87 on 2010-01-01
Thanks for the tip, worked great to get my old P4 2.4 GHz to play a 720p file.

---

