---
title: "M-audio soundcard... How? (sound issues)"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by light_without_heat on 2008-06-12
Hey guys.  So I'm completely new to this whole Ubuntu thing.  My brother is a huge advocate of it and my last system (windows) crashed and died. 

I don't know a whole lot about computers; I took programming in high school and like to fiddle around but I'm not too well versed in this stuff.  Anyways onto the meat of it...

I'm trying to use my soundcard (M-Audio Delta) with Ubuntu but it doesn't play out of the rca outputs that I want to use... The headphone jack is the only output that works right now... Ubuntu sees the soundcard and I try to select it or use ALSA for all sounds but no go on the RCA outputs. So ... A little help?!

Thanks to all.

---

### Post by light_without_heat on 2008-06-13
Shameless bump

---

### Post by ZootHornRollo on 2008-06-13
hi,

what model of card is it and what version of Ubuntu?

i have an m-audio audiophile 2496 and had a major headache trying to get this card working in Ubuntu 8.04.  Same problems as yourself, no audio through the rca's but everything else said the card awas working.

I installed Ubuntu 7.10 it worked straight away.

So my adice would be to try 7.10.

CHeers.

---

### Post by Nepherte on 2008-06-13
Try following these steps to troubleshout:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and post the issues you get here.

---

### Post by light_without_heat on 2008-06-13
> **ZootHornRollo said:**
> hi,

what model of card is it and what version of Ubuntu?

i have an m-audio audiophile 2496 ...

So my adice would be to try 7.10.

CHeers.

Well it's the same card as yours and I'm running Ubuntu 7.10 ... Is there some sort of driver for it that I need to download?

Thanks again to all and I'm going to try some of that stuff from the other thread about sound issues too so we'll see what's what pretty soon hopefully.  :confused:

---

### Post by ZootHornRollo on 2008-06-14
are you connecting the rca leads to the outputs? (the two middle rca's)

i did it wrong when i first set the card up because looking at the back of the card, it looks like the two middle rca's are for midi.  noticed my mistake after it wouldn't work and i consulted the instructions :oops: (still didn't sort it as i was using 8.04 at the time)

---

### Post by ZootHornRollo on 2008-06-14
if you have onboard sound have you disabled it in the bios?

the card worked right away when i installed 7.10.  no need to download drivers etc (works with the alsa drivers)  you may need to un-mute it in the alsa mixer.

---

### Post by ZootHornRollo on 2008-06-17
Did you get it working?

i remember reading somewhere there is a problem with revision E cards of this particular model.  they are not supported in alsa.

mine is a rev b card and works fine.  might be worth checking your card and looking a bit further into this if it is a rev E card.

---

