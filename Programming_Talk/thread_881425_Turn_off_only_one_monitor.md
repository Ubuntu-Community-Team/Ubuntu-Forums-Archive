---
title: "Turn off only one monitor"
date: 2008-08-06
forum: Programming Talk
---

### Post by HyperHacker on 2008-08-06
I have two monitors connected to a GeForce 6200 (DVI and VGA) using TwinView. I can call "xset dpms force off" to turn off both, but how can I turn off just one? xset doesn't seem to see two different screens, even though most other programs do.

---

### Post by chungy on 2008-08-12
Try xrandr.

Find out what display is called what with plain "xrandr", then use "xrandr --output VGA --off" (example, change "--output VGA" as necessary) to turn that display off.

---

### Post by HyperHacker on 2008-08-12
It just shows one big screen.> Screen 0: minimum 2960 x 1050, current 2960 x 1050, maximum 2960 x 1050
default connected 2960x1050+0+0 0mm x 0mm
   2960x1050      50.0*

---

