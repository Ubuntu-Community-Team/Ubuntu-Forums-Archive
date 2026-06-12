---
title: "Mencoder set dvd://"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by MrWES on 2008-08-16
Where in the heck do I set the dvd device dvd://?

I tried in .mplayer/config 

dvd_device=/dev/scd0

but it still errors out; device not found.

Thanks,
Bill

---

### Post by mc4man on 2008-08-16
the default for mplayer is /dev/dvd, if your dvd drive has a /dev link of something else then

for the config try dvd-device = /dev/dvd1  or dvd-device = /dev/scd0
ex.
> # Write your default config options here!

 dvd-device = /dev/dvd1

Your drive is probably /dev/scd0 with a link of /dev/dvd1

run > sudo lshw -C disk to check

for playback
for the gui mplayer (gmplayer) open, then r. click on video box -> preferences -> misc and set there.(/dev/dvd or /dev/dvd1, /dev/scd0 or /dev/scd1 ect

for the command line use as such
mplayer -dvd-device /dev/dvd[COLOR="Red"]1[/COLOR] dvd://x[COLOR="Red"][/COLOR] 
 x=title number

Ex. with options
 mplayer -dvd-device /dev/dvd1 dvd://1 -vo xv -ao alsa -fs -aid 128 -channels 6 
(access /dev/dvd1, play title 1, use Xv video output, use alsa audio output, fullscreen, first audio track, 5.1 channel output

Ot. I guess you never did the auto open/ auto connect ipod with amarok, working very well here

---

### Post by MrWES on 2008-08-16
Ok...I see where I went wrong.


The IPOD problem was actually on my son's box, and I haven't had a chance to get over there to fix it. I'll let you know how it goes -- I do thank you for the effort :)

Bill

---

