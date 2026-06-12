---
title: "Dual Monitor Setup"
date: 2013-12-19
forum: New to Ubuntu
---

### Post by youngmalonebrandon on 2013-12-19
Hello, I'm a trying to set my desktop monitor up to my laptop via DVI HMDI port. The main issue is that once I plug in the DVI coord, my screen gets scratchy, or goes black. This is also the case if I boot the laptop with the DVI in. So, I'm unable to post an output of the command xrandr --verbose with the HDMI in, only without, which I assume is pointless.
I'm using an HP Envy M-6 K010DX laptop, with an AMD A10-5745M APU AProccessor with AMD Radeon HD 8610G graphic card. 				
Being new to Linux, I'm not sure how to get around this. I've looked up multiple posts about the issue, but haven't been able to make any progress.
In advance, thanks to anyone who can help.

---

### Post by entw on 2013-12-19
You need to write your [xorg.conf]("https://help.ubuntu.com/community/XineramaHowTo") config. There's no other way I think.

---

### Post by Tristan_Williams on 2013-12-19
Can you run the Xrandr GUI application

---

