---
title: "Slow computer after graphics driver change"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by flyingsolo on 2008-06-23
I recently got help fixing a resolution problem on my laptop (Dell 6400; ATI x1400; 2 G ram) but now everything is slow.

[my earlier thread about screen resolution]("http://ubuntuforums.org/showthread.php?t=834274")

Example, if I type text, there is a visible delay between key entry and characters showing on screen.  If I open Amarok, it takes a long time to write the playlist to the screen.  If I open some photos, it takes time to switch to next photo in collection and you can see the image being painted in blocks.  If I click on the date at upper right to see map and to do list, nothing happens and usually the panels (top & bottom) freeze!

So this is all very frustrating & any suggestions would be appreciated.  The resolution of the screen is fixed and properly rendered now from the earlier thread.  Using Hardy Heron.
Thanks.

---

### Post by angryfirelord on 2008-06-23
Is the driver enabled properly? Run this command and post what appears:
```
fglrxinfo
```
Also, how did you install the ATI driver? Did you use it from Ubuntu's repos or did you use the one from ATI's site?

---

### Post by flyingsolo on 2008-06-24
Sorry--missed your reply as I had to sleep!
From fglrxinfo I get:

> ~$ fglrxinfo
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.3)

I used Envy to install drivers.

---

### Post by angryfirelord on 2008-06-24
Yeah, I wouldn't touch Envy. It usually ends up creating more problems.

If it says "Mesa", then the driver didn't install right. If Envy has an uninstall option, remove the driver and then follow this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29")

Just read it carefully and follow everything step-by-step. Some of the stuff you can ignore if you're not running 64-bit or no errors are appearing. When you get to point where it says to modify your xorg.conf, don't. Just run the next command below it. (sudo aticonfig --initial -f) That'll add the necessary things to your xorg.conf.

---

### Post by flyingsolo on 2008-07-15
OK--had to take a break for work but need to still work on this.  I did follow the last suggestion to remove mesa drivers & it looks successful b/c now fglrxinfo gives:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release

But I still have a really serious problem with the whole system being slow and other oddities.  For instance, if I click on the panel date/calendar app, the whole system freezes and I need to do a hard shutdown (shutdown button or CTRl/alt/del won't work)  I've seen a few mentions of similar problems in other posts but no solutions and I'm not sure it relates to my changing video drivers--maybe it just coincidentally started then.  Very frustrating so any suggestions/help would be appreciated.

Extra information--I really think my original video driver issues are fixed but yet I have this new problem which perhaps warrants its own posting so I'll proceed with that.

---

### Post by markbuntu on 2008-07-16
maybe you x is a little confused, try this:

sudo dpkg-reconfigure -phigh xserver-xorg

It will reconfigure the x server

You can also try turning off your desktop visual effects to see if compiz is causing the problem. If it is, try

compiz --replace.

You could also try logging in in gnome safe mode and see if the problem goes away. If it does then the problem is with you particular session setup.

Actually you should try these things in reverse order from how I wrote them, easy to less easy.

---

