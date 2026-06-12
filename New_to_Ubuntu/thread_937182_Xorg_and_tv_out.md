---
title: "Xorg and tv out"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by natman on 2008-10-03
Hi,
I have a tv out on my laptop and am using a cable to hook it up to my tv, all works ok but the right hand side of the screen is always missing on the tv. The TV is a HD tv and am using svideo to connect. I have played around with the overscan and res settings in Nvida control panel but nothing ever gives me the whole screen on the TV - is there any way to fix this.
I dont have a VGA on the TV or a dvi / hdmi on the laptop so am stuck with svideo cable.

---

### Post by phidia on 2008-10-03
You may need to edit your xorg.conf with the specific modelines that the HDTV uses.

There are sites online that will help you generate those modelines. 
[This link]("http://do.whileloop.org/soft/tricks/htpc-nvidia.php") is old but does cover the basics of how to go about that.

You can also play around with xvidtune (available from terminal) but that never did much for me with HDTV set up. 
Including the make & model plus # of the tv may get you better help too.

---

