---
title: "videos on apple.com don't work."
date: 2008-09-26
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-09-26
how do i get them to work properly?

---

### Post by Crafty Kisses on 2008-09-26
Have you tried installing this package?
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by andrewwg94 on 2008-09-27
wait, i just realized that they don't even work on firefox under windows with quicktime installed. i guess this is just a firefox problem. any solutions?

---

### Post by SunnyRabbiera on 2008-09-27
They work for me, unless you are trying to use the high def videos and such.
I know the Mac vs PC adds work

---

### Post by mc4100 on 2008-09-27
It depends, for example this doesn't work, at all:
[http://www.apple.com/ipodnano/gallery/ads/small.html](http://www.apple.com/ipodnano/gallery/ads/small.html)
Yet this works flawlessly:
[http://www.apple.com/trailers/miramax/blindness/medium.html](http://www.apple.com/trailers/miramax/blindness/medium.html)

---

### Post by nowshining on 2008-09-27
> **SunnyRabbiera said:**
> They work for me, unless you are trying to use the high def videos and such.
I know the Mac vs PC adds work

those are probably flash - i'm taking adds - ads :)

---

### Post by SunnyRabbiera on 2008-09-27
> **mc4100 said:**
> It depends, for example this doesn't work, at all:
[http://www.apple.com/ipodnano/gallery/ads/small.html](http://www.apple.com/ipodnano/gallery/ads/small.html)
Yet this works flawlessly:
[http://www.apple.com/trailers/miramax/blindness/medium.html](http://www.apple.com/trailers/miramax/blindness/medium.html)

Both work fine for me.
Though the one for blindness does need to be played around with.

---

### Post by nowshining on 2008-09-27
> **andrewwg94 said:**
> how do i get them to work properly?

sudo apt-get install mozilla-mplayer


then

do a symbolinc link with all files in /usr/lib/mozilla/plugins/ to /home/username/.mozilla/plugins or copy and paste a copy from the lib folder - do a restart of Firefox...

edit: do u have noscript - if so enable apple.com to use javascript and if it doesn't auto refresh press F5 or since it doesn't work for me either

try to install libquicktime and symbo link all quicktime files:

/usr/lib/libquicktime.so.1.0.0
/usr/lib/libquicktime1
/usr/lib/libquicktime1/lqt_audiocodec.so
/usr/lib/libquicktime1/lqt_mjpeg.so
/usr/lib/libquicktime1/lqt_ffmpeg.so
/usr/lib/libquicktime1/lqt_videocodec.so
/usr/lib/libquicktime1/lqt_rtjpeg.so
/usr/lib/libquicktime1/lqt_vorbis.so
/usr/lib/libquicktime1/lqt_dv.so
/usr/lib/libquicktime1/lqt_png.so

to ur .mozilla plugins folder in ur home folder like i'm going to try and restart FF..


edit: 2: the above didn't work for me :/

---

### Post by mc4100 on 2008-09-27
> **SunnyRabbiera said:**
> Both work fine for me.
Though the one for blindness does need to be played around with.
Hmmm, it's odd, the first link just gives me an utterly unusable page -- been trying to get Apple stuff to work for a while -- and the second (Trailers, which have always played fine) plays almost instantly, and gives smooth playback.

---

### Post by SunnyRabbiera on 2008-09-27
> **mc4100 said:**
> Hmmm, it's odd, the first link just gives me an utterly unusable page -- been trying to get Apple stuff to work for a while -- and the second (Trailers, which have always played fine) plays almost instantly, and gives smooth playback.

I have all the codecs so that might explain my fortunes.

---

### Post by andrewwg94 on 2008-09-27
> **mc4100 said:**
> Hmmm, it's odd, the first link just gives me an utterly unusable page -- been trying to get Apple stuff to work for a while -- and the second (Trailers, which have always played fine) plays almost instantly, and gives smooth playback.

same here

---

### Post by mc4100 on 2008-09-27
> **SunnyRabbiera said:**
> I have all the codecs so that might explain my fortunes.

Usually I'd say the same things: But I've PPA's and Repo's with codecs coming out of my ears, and every possible gstreamer plugin imaginable, and then variants still. And yet, no Apple Ads ... maybe it's a sign. Also, I've tried going with a different browser, scripting on, scripting off ... nothing.

---

### Post by terry_gardener on 2008-09-27
i have found a workaround that works with some of the videos on apple.com. 

quidedtour videos i have not got working. 

watch ads and trailers seems to work. 

trailers section. 

open the trailer you want to watch and when you see the small medium large options in the top right of the page right click the option you want and click open in new tab it will buffer and then stop click the play button and it plays. 

watch ads section [http://www.apple.com/getamac/ads/](http://www.apple.com/getamac/ads/)

you will get a window saying get latest quicktime, under this there is list of adverts right click the advert you want to watch and open in new tab, again it will buffer and stop, just click play and it plays fine.

hope this helps a little. 

dont know why apple.com doesn't work normally i can watch quicktime videos on other websites.

---

