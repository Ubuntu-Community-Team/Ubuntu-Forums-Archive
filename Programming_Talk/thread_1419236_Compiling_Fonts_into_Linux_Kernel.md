---
title: "Compiling Fonts into Linux Kernel"
date: 2010-03-01
forum: Programming Talk
---

### Post by Gwasanaethau on 2010-03-01
I don't know if this is strictly programming, but I thought I'd ask here anyway.

I'm compiling the kernel from scratch and would like to change the font that the kernel uses when its spewing out its reports. I know you can use **setfont**, but that only has an effect once the kernel has passed control to init. I was able to compile a keymap into the kernel using the following command:
```
loadkeys -m /usr/share/kbd/keymaps/i386/qwerty/uk.map.gz > drivers/char/defkeymap.c
```
Is there something similar that can be done for compiling in a console font? I have a font situated at **/usr/share/kbd/consolefonts/Lat2-Terminus16.psfu.gz** that'll be ideal.

Just throwing it out there…

Gwasanaethau.

---

### Post by falconindy on 2010-03-01
You might be interested in this article:

[http://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt](http://www.mjmwired.net/kernel/Documentation/fb/fbcon.txt)

---

### Post by Gwasanaethau on 2010-03-05
Thanks for posting. I actually stumbled across that article myself before I posted, and I think part of it will certainly be useful down the line – namely how to select the font at boot time. But it appears that the font still needs to be compiled into the kernel first…unless I missed something. ;)

Thanks for the suggestion!

---

