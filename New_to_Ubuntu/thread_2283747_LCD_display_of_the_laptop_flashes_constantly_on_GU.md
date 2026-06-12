---
title: "LCD display of the laptop flashes constantly on GUI"
date: 2015-06-24
forum: New to Ubuntu
---

### Post by simba4 on 2015-06-24
Hello there,

Four days old Ubunto-64bit on Dell XPS1730;  8GB RAM; nVidia 8700GT.
Another 19" external display attached as well.

The SSD is connected as the 2nd drive, so I  have to press F12 for boot menu and then choose the 2nd drive (the 1st drive is with vista). 

When booting, the laptop's LCD display first shows the textual purple screen of boot options, but then, when the GUI kicks in, the LCD display of the laptop start to flash with all king of full screen colors, Blue, Red, Purple, Black, Green etc. Each time a full scren with te same color (no mixing)

All this, while the other 19" display is fully readable with the GUI.
I got into the display setting where I can set each screen with its own resolution and position, but it seems that  no resolution is good enough for the LCD laptop display that keep flashing its colors.

BTW, on the Vista, the two screen working fine together as multi display set.

Simba

---

### Post by dino99 on 2015-06-24
there are a few possible reasons for a such trouble:
- hardware does not like condensation: cold/hot transition, wet place
- some other hardwares are spreading electromagnetic disturbances around (often external psu weirdly protected)
- graphic card/cord/receiver plug not working friendly together (frequencies compatibilities)
- possible not calibrated LCD or worst failing to do its job (see brand support)

---

### Post by simba4 on 2015-06-24
Thanks for the swift reply.
Pay attention that the pair (displays) are working fine when loading Windows Vista.

Therefore, to my humble opinion, neither of the possibilities that you mention seem as the true reasons.

I thinking more in the direction of the display driver.
I looked and found a nVidia driver **'NVIDIA-Linux-x86_64-340.76.run'**.
This driver should be suitable for my old 8700M.

I just don't know how to install it.
Is it just a simple replace or should I remove the current driver first?

Is there a 'device manager' equivalent for Ubunto?

How should I install the new driver?  what is the procidure?

Simba

---

### Post by Vladlenin5000 on 2015-06-24
You can and should install nvidia drivers at System Settings > Software & Updates. Open the rightmost tab, Additional drivers, a choose accordingly.

---

