---
title: "Realtek sound question"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by RierdenGazer on 2012-05-29
I am new to Linux, and recently installed Ubuntu 12.04 32bit on my Lenovo Idea Center k220. So far I have been able to get just about everything I want out of it, except one thing. I can not figure out how to get my surround sound set up. I have stero, that is all. In the Unity sound settings (right click on speaker in upper right corner) it has slider bars for balance, fade, and sub. But fade and sub are shaded out and i can not adjust them. AlsaMixer does not show anything about surround sound. I know that this sound card, A Realtek ALC662 rev 1, remaps the jacks to accommodates my surround sound setup. It was an easy thing to do in Windows Vista. Am I simply missing something? Everything I find in the forums about surround not working is for HDMI sound. This is 3 two channel phono jacks. Anyone have any ideas? I am LOVING this OS. I just want all my speakers working.

---

### Post by mastablasta on 2012-05-30
it seems HD sound and surroud sound doens't work. in my casse every now and then sound even dissapers (i.e. sometimes it doesn't even load the card drivers and shows it as dummy card). so i consider it good that it can at least run stereo. this should really get fixed as these realtek cards seem quite common.

---

### Post by RierdenGazer on 2012-05-30
Well that is just tragic. Is this just a problem with 12.04? i found a youtube vid that supposedly shows how to fix it, but all it shows is the guy setting it from 2 to 6 channels in AlsaMixer. but alsa says he has the exact same card as me. the only 2 comments on the vid are praising him for the easy fix. But I do not even have the same options in Alsa that he did. I suppose that I can just deal with stereo sound until a fix is released, I am just a bit of an audiophile and my music does not sound "right" to me without my sub working...

---

### Post by mastablasta on 2012-05-31
for me (i have a similar card but i don't think it's exactly the same model) it hasn't been working nicely since 10.04. 10.10 made it work most of the time...
12.04 sometimes still does not recognise it on boot, but it does most of the time (90%+). and it only works on stereo mode.
 
i think it's a bug with medium priority.
 
you could try adding ALSA development PPA and see if that works any better.
 
edit: i think my card is Intel but has realtek chip inside.

---

