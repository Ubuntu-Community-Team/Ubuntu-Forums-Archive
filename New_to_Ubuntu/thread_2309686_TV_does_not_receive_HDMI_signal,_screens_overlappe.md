---
title: "TV does not receive HDMI signal, screens overlapped in latop"
date: 2016-01-12
forum: New to Ubuntu
---

### Post by compa2 on 2016-01-12
I'm new to linux, I've been a windows user for as long as I can remember but I decided to revive an old laptop through Xubuntu.
Everything seems to work fine and the distro is quite fast, which I am liking a lot! I decided to use that laptop for Netflix and Chill purposes and connect it to my tv via HDMI cable... the problem: 
The TV is not receiving any signal. I am positive the HDMI port is working because Xubuntu does detect the display, but the TV is only showing "No signal detected". Also, when I press "Identify" in the Config-> Display, **both labels seem to be one on top of another in my laptop's display**
I installed arandr but it shows one display next to the other, contrary to what the labels say when I press "Identify".

I am really confused, mainly because I am extremely ignorant regarding Linux. I tried drag and drop the TV's label but that didn't work. I modified arandr display position and nothing happened. I am 100% the display is enabled (I checked the checkbox to in the display settings to enable it)

Any clues as to what might be happening and how to solve it??

---

### Post by tea for one on 2016-01-13
> **compa2 said:**
> 
The TV is not receiving any signal. I am positive the HDMI port is working because Xubuntu does detect the display, but the TV is only showing "No signal detected".

"No signal detected" on a TV often indicates that the intended source is not correct.

Have you changed the input source on your TV to HDMI 1 or HDMI 2 etc?

Kind regards

---

### Post by DuckHook on 2016-01-13
Hello compa2 and welcome to Linux and the forums.

Your Config>Display is working properly. What it is telling you is that the TV will mirror the image on your monitor. Because the resolutions are likely different, the display and monitor will not align, so one will show a smaller image than the other, but since they are both showing the same "space" they are layered over top of each other. If you turn off mirroring, then they will be shown side-by-side and you will be able to drag one screen around to any four sides of the other. However, this will then mean that your effective desktop space is larger and your mouse will travel from one screen to the next, which may not be what you want.

As for the missing input, *tea for one*'s suggestion is excellent: look for your TV being set to the wrong input. If it has more than one HDMI port, it needs to be set to the correct one before it will receive the signal.

---

