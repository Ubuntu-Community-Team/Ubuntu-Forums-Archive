---
title: "[SOLVED] Mic doesn't work on Notebook or headset"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-05-30
I'm running Ubuntu 7.10 on a Sony VGN-FE780G. I am able to hear the volume fine from the speakers & USB headset. However, I am unable to transmit through the mic on either. Any Ideas ?

---

### Post by bluefrog on 2008-05-30
open applications/eccessories/terminal and run
alsamixer

go to to the mic "section" and see if you have mic1 and mic2 (click on your keyboard arrow up/down)

and try your mike when you change.

---

### Post by CoCoKnots on 2008-05-30
What command do I use to 'Run' Alsamixer on the terminal ?

---

### Post by Mjölner on 2008-05-30
Just type in

> alsamixer

sometimes some of the chanels are muted. so if you go left or right arrow to the channel and then toggle mute/unmute with the > m key. Up and down arrow will change the volume

---

### Post by CoCoKnots on 2008-05-30
Thanks... I was able to see control difference in sound, But no change in Mic.

---

### Post by Mjölner on 2008-05-30
are you sure its not muted?

In the attached screenshot you can see that the light green 00's are unmuted channels and that the dark green MM's are muted channels.

---

### Post by CoCoKnots on 2008-05-30
Correct... They are mot muted. However, I only have 2 bars up showing a reading of 90. It looks like you have possibly 16 bars. Am I looking at the wrong thing ?

---

### Post by Mjölner on 2008-05-30
:confused:  I don't know.

sorry

make a screenshot

---

### Post by CoCoKnots on 2008-05-30
Here is a screen shot. I'm not sure what to look for next.

---

### Post by Mjölner on 2008-05-30
I can see no capture channels in you screenshot.

try this:
in the terminal type

> alsamixer -V all


and see if it gives you the capture channels


If it doesn't, then with my level of GNU/Linux, I cant help you:(

Mjölner

---

### Post by CoCoKnots on 2008-05-30
Thanks, This looks a little different. Line & Capture are not showing any reading...

---

### Post by Mjölner on 2008-05-30
First I must say that this is beyond my knowledge, but open up the mixer with

> alsamixer -V all 


and go to either the mic or capture column, and hit the space bar. this should enable recording for that channel.

Otherwise there is loads of documentation:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") is one example.

You could try posting in the Multimedia & Video section with a link to this post.

---

