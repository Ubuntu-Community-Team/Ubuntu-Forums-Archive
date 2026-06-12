---
title: "Totem .wmv playback poor after gutsy-&gt;hardy"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by jamewill on 2008-06-02
my .wmv files 640 x 480 25 frames per second played fine in gutsy

in hardy totem plays them but skipping bady (about 1 fps)

any ideas

jw

---

### Post by mde123 on 2008-06-03
uh yeah, i can agree,
but try mplayer, because i had the smae problem and mplayer worked better then totem.

---

### Post by PinkFloyd102489 on 2008-06-03
WMV is all around crap on my system, no matter what program I use. VLC does the best job though, but it's still bad.

---

### Post by jamewill on 2008-06-03
hmmmnnn

ok i tried mplayer
(sudo apt-get install mplayer)
but it gave me an error window at video playback start of the following

> Error opening / initialising the selected video_out (-vo) device

I tried starting mplayer from commmandline and found that using option -vo x11 worked

> mplayer -vo x11 video.wmv

Anyone know how to get round this?
Is there an mplayer config file where this can be set and is it a good idea

OK on to VLC player
===================
no dice
displays ok
but playback at approx 1/10 proper speed 
huge digital artifacts everywhere

This is all on a 2 year old laptop with AMD Athlon 4000+ with 1GB RAM running 32 bit hardy

jw

---

### Post by philinux on 2008-06-03
Good how to here.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by jamewill on 2008-06-03
wow thanks for thread but I don't want to do all that!
I just want to sort out video play!
After more testing i have found mplayer -vo x11 still not operating correctly.
Video plays 1/2 speed of audio track...

---

