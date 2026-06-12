---
title: "White screen at games startup"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by jack_harper2007 on 2008-09-16
Every time i try to start a game like, lincity, open arena, etc... my screen turns black and then slowly becomes white lol
The strange thing is that some times this doesn't happen, the game just starts normally, and i just have to change the video settings to he proper resolution (in my case 1440 x 900) and the white screen doesn't appear any more if i start that game.
I'm having this problem since i installed Ubuntu and i still couldn't solve it. I've been searching the web for solutions but still couldn't find any :(
Can someone give me a step by step way on how to solve this? I would be very grateful :)

Thank's in advance and sorry for my bad english :)

My graphic card is ATI Mobility Radeon x600.

---

### Post by Orange_and_Green on 2008-09-16
Hello jack_harper2007.

I was wondering what kind of driver you are using.

ATI cards are often a pain in the back in my experience, as on the one hand, there are two open source drivers called "ati" and "radeon" (if you didn't install any extra drivers, you are probably using one of those) but they seldom reach top performance because until very recently ATI would not release hardware specifications for their products.

On the other hand, there's always ATI's proprietary driver fglrx (at least ATI is one of the "enlightened" maufacturers who do provide their own drivers for linux), you can find the 32-bit version [here]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") and the 64-bit version [here]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html").

I have made mostly good experiences with the proprietary driver, but also a few very bad ones (like strange polygons flashing on the screen, freezes, crashes...:frown:) 

The installer that comes with the downloads is a little troublesome (it makes it hard to uninstall the driver for example) so before actually installing you might find [this link]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") of interest...
At least, if you don't like it, this way you can remove it...

Good luck:KS

P.S. I find your English very good... which means that either it really is, or that mine is terrible too#-o

---

