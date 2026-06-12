---
title: "Html5"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by Autodave on 2012-08-07
So, 2 machine (out of 4) that I have quit playing youtube videos a few days ago.  And, the only thing that keeps reappearing when I ask for help is that youtube no longer uses Flash, but uses HTML5.  Is Firefox capable of viewing HTML5 videos?

---

### Post by asipper10 on 2012-08-07
Youtube only uses html5 if flash isn't installed.  Is flash installed?

---

### Post by Autodave on 2012-08-07
> **asipper10 said:**
> Youtube only uses html5 if flash isn't installed.  Is flash installed?

Yes, but 2 machines w/Flash installed quit showing youtube videos a few days ago.  They both worked fine until then.  I have gone as far as re-installing 12.04 on one machine and then the restricted extras: all with no luck.  I did try youtube right after installation: before installing the restricted extras.  Then after restricted extras.  And then after adding Medibuntu repo.  And then after trying Gnash.  Nothing.

---

### Post by madjr on 2012-08-07
that's weird...

have you tried Chrome ?

---

### Post by Frogs Hair on 2012-08-07
Firefox 14 is listed at this test page for HTML5 support.  [http://html5test.com/results/desktop.html](http://html5test.com/results/desktop.html) Did you get an out dated flash message from Youtube and do all computers have the same Flash version ?

---

### Post by Autodave on 2012-08-07
> **madjr said:**
> that's weird...

have you tried Chrome ?

Chrome will not work on either machine.

---

### Post by Autodave on 2012-08-07
> **Frogs Hair said:**
> Firefox 14 is listed at this test page for HTML5 support.  [http://html5test.com/results/desktop.html](http://html5test.com/results/desktop.html) Did you get an out dated flash message from Youtube and do all computers have the same Flash version ?

All 5 computers have same Flash version.  2 quit working, other are fine.

---

### Post by mcduck on 2012-08-08
> **Autodave said:**
> So, 2 machine (out of 4) that I have quit playing youtube videos a few days ago.  And, the only thing that keeps reappearing when I ask for help is that youtube no longer uses Flash, but uses HTML5.  Is Firefox capable of viewing HTML5 videos?

Yes, it is, but your problem is that there actually is no such format as "HTML5 video". The HTML5 standard only defines how to emabed a video on the web site, not what format it should be encoded in. And as the different companies couldn't agree about the format to use, some browsers support Ogg Theora and others support H.264 encoding.

...and YouTube decided to go for the H.264 encoding, which Firefox can't support as it's a patented and copyrighted format and couldn't be distributed for free with the browser without Mozilla having to pay licence fees for the codec. (Safari, Chrome and IE can support it because the big companies behind those browsers have no problems paying the license fees for H.264)

---

### Post by Steeperton on 2012-08-08
> **mcduck said:**
> 
...and YouTube decided to go for the H.264 encoding, which Firefox can't support as it's a patented and copyrighted format and couldn't be distributed for free with the browser without Mozilla having to pay licence fees for the codec. (Safari, Chrome and IE can support it because the big companies behind those browsers have no problems paying the license fees for H.264)

Nonsense. Youtube uses WebM (and h.264 as a fallback). The clue is who "owns" youtube and WebM (Google)

Firefox and HTML5 youtube works fine for me. Indeed it works better than flash, so I have it permanently set via [http://www.youtube.com/html5](http://www.youtube.com/html5)

---

### Post by madjr on 2012-08-08
> **Autodave said:**
> Chrome will not work on either machine.

well that's certainly something impossible unless there is something wrong with your hardware.

how much free hard drive space you have ?


also you may want to try a distro like mint, which already comes with flash preinstalled and see if it has the same problems:


[http://linuxmint.com/](http://linuxmint.com/)

---

### Post by ads52 on 2012-08-13
> **Steeperton said:**
> Nonsense. Youtube uses WebM (and h.264 as a fallback).

It is a very fine point but when you say WebM you mean VP8 video and Vorbis sound in an extended Matroska container. I guess the fallback is h.264 video and aac sound in an flv or mp4 container. Not much help to the OP I guess :(.

---

