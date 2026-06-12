---
title: "VLC Media Player leaves image on screen if paused."
date: 2016-05-13
forum: New to Ubuntu
---

### Post by erich5 on 2016-05-13
Hey everyone, I'm very new here and excited to be part of this community. My experience with Ubuntu has only been through scriptcoin mining. Anyway, I am taking it slow as I bought a System76 laptop and don't wanna mess it up. So I installed VLC Media Player and started to watch a movie, I had to go to the bathroom so I paused it. Then I got bored of the movie and exited VLC Media Player. After I closed VLC the paused image was up on my screen and I had to hard reboot to get it to go away. 

Is there a better alternative?
Is there a fix or is this common?

If there are some better alternatives I will more than likely need help installing them unless they are from the Ubuntu Software page. I'm not very familiar with the command line but plan to become familiar with it.

Intel® Core&#8482; i7-6500U CPU @ 2.50GHz × 4 

Intel® HD Graphics 520 (Skylake GT2)

---

### Post by mc4man on 2016-05-13
Maybe it was an anomaly, I'd see if it happens again.

As far as vlc, it has 2 settings that by default are set to Automatic,  video out &  hardware decoding. However at times & with some hardware vlc isn't too good at picking the correct ones.

Maybe try > open vlc > Tools > Preferences
Under the Input/Codecs tab for Hardware-accelerated  decoding either disable or set to VA-API via x11 as seen in screen 1
Under the Video tab set Ouput to OpenGl as in 2nd screen
Save changes then see if vlc is better behaved

---

### Post by erich5 on 2016-05-13
> **mc4man said:**
> Maybe it was an anomaly, I'd see if it happens again.

As far as vlc, it has 2 settings that by default are set to Automatic,  video out &  hardware decoding. However at times & with some hardware vlc isn't too good at picking the correct ones.

Maybe try > open vlc > Tools > Preferences
Under the Input/Codecs tab for Hardware-accelerated  decoding either disable or set to VA-API via x11 as seen in screen 1
Under the Video tab set Ouput to OpenGl as in 2nd screen
Save changes then see if vlc is better behaved

This worked! Thank you so much

---

