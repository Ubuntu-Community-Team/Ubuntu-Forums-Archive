---
title: "hd4000 graphical error"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by avgudar2 on 2014-03-26
[https://bugs.freedesktop.org/show_bug.cgi?id=68410](https://bugs.freedesktop.org/show_bug.cgi?id=68410)

I get the same as described in this thread.
As per the thread I can reproduce it by goign to wikipedia and scrolling up and down a few times.

screenshot
[http://s28.postimg.org/hxwhnt3f0/image.jpg](http://s28.postimg.org/hxwhnt3f0/image.jpg)

---

### Post by ajgreeny on 2014-03-26
I have tried to get this to show on my machine with i5-3570K using HD4000 graphics and have had no luck (actually, no bad luck, I suppose) as I can not reproduce these symptoms in any way.

How quickly does it appear and doers it matter how you scroll the long page? I went to [http://en.wikipedia.org/wiki/Linux](http://en.wikipedia.org/wiki/Linux) and scrolled up and down many times over several minutes using the mouse wheel, cursor arrow keys and Page Up/Down keys but the graphic rendering is still first class with no artifacts of any kind showing.

I am using a desktop machine with cpu as mentioned, ASUS® P8H61-MX USB3/SI: motherboard, 8GB DUAL-DDR3 1600MHz (2 X 4GB) ram and a Hanns-G monitor attached with DVI cable.  Could the problem be related to some incompatibility of the HD4000 with some other part of the setup, or perhaps the version of firefox and the scrolling preferences set in that?

---

### Post by avgudar2 on 2014-03-26
I am using a laptop with an external Asus monitor hooked up via HDMI, the artifacts CAN appear on both monitors but since the other monitor was used for skype and they didn't appear on the other monitor at the time of the screenshot I didn't feel the need to include it. It shall be noted that the problem is not just occuring in Firefox, but also on the desktop on rare occations and in other programs such as audacity or linux multimedia studio. I fell this is not a problem related to firefox even though firefox has got the worst case of the bug, perhaps due to it being used so much and because it is constantly in motion (scrolling). The black boxes do seem to appear as you scroll/something on screen is moving or updating. For the above screenshot i used the arrow keys but they tend to appear no matter how you scroll only in lesser numbers.

The main screen hooked up via HDMI is 1920x1080 in resolution and the built in laptop screen is 1366x768.

Under system details the Graphics driver says "Unknown" and experience says "standard"

---

### Post by avgudar2 on 2014-03-27
Well, I installed KDE and the problem is gone. Now instead of black boxes I get white bars. Lmao.

---

