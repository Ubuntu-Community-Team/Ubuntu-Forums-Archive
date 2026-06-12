---
title: "Where is source code is color setting? (indicator applet)"
date: 2011-07-01
forum: Programming Talk
---

### Post by Moozillaaa on 2011-07-01
After the initial update of fresh 10.04 install, my indicator applet for logout/switch user/shutdown was red. Pretty cool.

But the next day, it was pasty default white again.

So I found the page with applet code, but I don't know where to look for this control...
[http://bazaar.launchpad.net/~indicator-applet-developers/indicator-applet/applet/files]("http://bazaar.launchpad.net/%7Eindicator-applet-developers/indicator-applet/applet/files")

Help?

edit:
And how might I change the image from the power symbol, to a burning-candle .gif image??? If I can find the image in the code file, I should be able to swap it easy enough. But where to look???

And the wireless icon ---> some Indians sending smoke signals?

---

### Post by megabytemonster on 2011-07-01
It goes red to indicate a reboot is needed, in case you didn't know that.

The images for the different icon themes are in /usr/share/icons

You can replace selected ones in your currently selected icon theme to achieve the effect you're after.

---

### Post by Moozillaaa on 2011-07-01
Thanks...............

---

