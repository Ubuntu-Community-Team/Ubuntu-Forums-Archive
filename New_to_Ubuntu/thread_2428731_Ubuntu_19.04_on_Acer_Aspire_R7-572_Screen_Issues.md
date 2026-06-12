---
title: "Ubuntu 19.04 on Acer Aspire R7-572: Screen Issues"
date: 2019-10-08
forum: New to Ubuntu
---

### Post by dmaysxbrainz on 2019-10-08
Hi all,


I'm experiencing two screen/display issues:


1. The touch screen is unresponsive, but the mouse behaves erratically due to "ghost touches" which typically kick in a couple of minutes post-startup. I've managed this issue by placing # xinput - disable (device #) in the startup commands, but I'd like to be able to use the touch screen. Based on my searches, it seems like folks haven't had trouble with the Aspire R7's touch screen on older (13) versions of Ubuntu.


2. When I minimize a screen, a subtle "ghost" remains on the screen. It's very similar in appearance to the burn-in on OLED screens, but is intermittent and depends on where I last placed a window with a high-contrast edge.


Other than that, the computer hasn't had many issues. There are no screen resolution issues, and I fixed the issue with Wifi by reinstalling the Broadcom driver.


By the way, I've tested a couple of other Linux distros which produced similar issues: Linux Mint, Ubuntu 18, Elementary OS.


Thanks for the help in advance!

---

### Post by cruzer001 on 2019-10-08
I have read this.  Mint has a uncanny ability to work when others have failed.  I have also seen in forums that Mate has a high success rate with touchscreens.  I have yet to own a touch screen so thats all I can input.

---

### Post by dmaysxbrainz on 2019-10-08
Gotcha. Mint was essentially the same experience as Ubuntu. I guess I can try a USB boot for Mate to see how it works. Thanks.

---

### Post by dmaysxbrainz on 2019-10-09
I gave Mate a try, but it made no difference. Xinput finds the N-Trig Duosense Device, but I have to disable it in order for the mouse to work properly. Otherwise, the mouse bounces all over the place and the screen still is unresponsive to touch.

---

