---
title: "Restrict LiveCD resolution"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by ralphz on 2008-07-24
Hi

How can I make my XUbuntu (or Ubuntu) live CD to start by default in 1024x768 mode.

The reason is I'll be using live CDs to run as a kiosks and I need them all to start in 1024x768 no matter what.

Thanks
Ralph
__________________
Ralph
[http://www.TheOrangeIT.org](http://www.TheOrangeIT.org)

---

### Post by phidia on 2008-07-24
[Here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers") is a table of video modes I think you want 773
So if you press F4 from the livecd boot menu you would enter vga=773
Hope that helps.

---

### Post by ralphz on 2008-07-24
Hi

That's only during a boot. Then X is taking over and uses something called DDC to query monitor for supported modes. In my case it defaults to 1280×1024 even if I ask it otherwise in my xorg.conf. 

I modified /usr/bin/dexconf script on the Live CD to put my configuration in the xorg.conf that LiveCD's X will use. 

When I start LiveCD my xorg.conf like in attached file.


But it's still starting in 1280×1024 instead of desired 1024x768.

I could add: Option "NoDDC" in Screen section but then I run into issues with vertical refresh. LiveCD boots to 1024x768 but the screen is shifted left 1/3 of the way.

I would appreciate any help.

---

### Post by phidia on 2008-07-24
I guess you probably know about this:
> Note: As of Ubuntu 8.04 and Xorg 7.3, the setup and configuration of /etc/X11/xorg.conf has changed. Please see the [Xorg in Ubuntu 8.04]("https://help.ubuntu.com/community/XORGHardy") for more information.

For additional troubleshooting resources, please also see the Ubuntu [X Team wiki]("https://wiki.ubuntu.com/X")
Which is from the Community Docs on video configuration [here]("https://help.ubuntu.com/community/Video").

Just including that in case you aren't aware of all the changes.

---

