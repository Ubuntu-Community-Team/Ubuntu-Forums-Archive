---
title: "Tweaking guide for video card?"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by andy_blah on 2012-12-28
These are my current specs:

[IMG]http://i.imgur.com/fBAQm.png[/IMG]

I know that this card is on a slow chipset/port, but I noticed that the card usually performs really badly in most games, not getting past 25-30FPS, and it really irritates my eyes when I play for too long. Is there any way to speed it's processing time, like overclocking the card's GPU, or changing voltage, update firmware or something? Also can somebody guide me on doing those things? Would it make any difference? Also I was a bit heasitant to overclock the GPU since I can't find it's temperature, and I wouldn't want to burn it, since this PC is quite old and I can't find replacement/alternative cards anymore.

What I've tried so far on speeding things up is to increase the AGP aperture size and enabling Fast Write in the BIOS, but so far no improvement.

Thanks in advance~

---

### Post by gordintoronto on 2012-12-28
My rule of thumb is that computer technology is good for seven years. I'm not sure where you are located, but in Toronto I can buy an off-lease computer for $160, which would be much, much faster than what you have.

If the card has temperature sensors, you can run Nvidia X Server Settings, and click on Thermal Settings to see the temperature.

It never hurts to include what version of Ubuntu you are using.

---

### Post by cariboo on 2012-12-28
Unfortunately the FX-5500 is no longer supported by Nvidia. Have you tried the nouveau driver, as it may work better with that graphics adapter than the legacy driver provided by the manufacturer.

---

