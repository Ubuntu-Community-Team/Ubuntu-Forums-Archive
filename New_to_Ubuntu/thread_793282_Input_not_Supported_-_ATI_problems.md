---
title: "Input not Supported - ATI problems"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by badbunny42 on 2008-05-13
Good evening.
I'm new to Ubuntu, apart from a brief flirtation with feisty last year, and I am now having a more serious go at making the switch.
My main problem so far is with my display properties.
I have a Club Radeon 9550 graphics card and an Acer AL1714 monitor.
I have tried multiple methods of getting the two to work together, from simply enabling the driver through to using the binary drivers how to/ATI document (plus several hours searching Google), but each time I end up with a blank screen after restart with '**Input not Supported**' displayed.
The only way I can recover is to use the recovery module in start up use xfix.

I Assume that it is something to do with the default display settings, but I admit that I have no idea how to sort it out.
I had no such problems when I tried Feisty (although I did use an AMD64 install instead).

Any advice gratefully received.

Thanks

BB42

---

### Post by mister_pink on 2008-05-13
what exactly are you trying to achieve and what have you got at the moment? 

I assume that the default settings that it picks are working to some extent otherwise xfix wouldn't do much for you? Can you not get the resolution you want, or do you need to enable closed source drivers for 3D?

---

### Post by badbunny42 on 2008-05-14
The default settings give me a maximum of 800*600, with quite a bit of flicker on occasion.
When I try to enable the driver by any of the means I mentioned above, (I also tried the directions on the ATI site) once Ubuntu finishes booting after the required restart, all I can see is a blank screen with a message (from the monitor itself) saying 'input not supported'.



I assume that the display settings are changed on restart to an unsupported resolution. My monitor will take up to 1280 by 1024.

Thanks for responding.

---

### Post by mister_pink on 2008-05-14
Part of the problem could be the fact that you've tried several methods. My last install was working almost perfectly and I tried to install a newer ATI driver and well... everything went a bit wrong. I managed to get it back to a workable state eventually which was good enough to last until hardy came out when I reinstalled.

But I digress! I suggest you try removing as much of what you've done yourself and start again. 
I'd avoid using the ATI website, this seems to cause more trouble than its worth. First thing to try is just enabling the drivers in the hardware drivers dialog. If this fails, turn them off and try using envy, but bear in mind this is unsupported but a lot of people have reported success with it.

---

### Post by badbunny42 on 2008-05-14
Thanks. i'll try that when I get home. I have tried removing what I've done, but if all else fails I can do a complete reinstall.
Any idea if it is possible to change display settings via the terminal? I might give that a try if all else fails.

BB42

---

### Post by ubuntu-freak on 2008-05-14
> **badbunny42 said:**
> Thanks. i'll try that when I get home. I have tried removing what I've done, but if all else fails I can do a complete reinstall.
Any idea if it is possible to change display settings via the terminal? I might give that a try if all else fails.

BB42

 
You should be able to set the resolution with xrandr in recovery mode, as Hardy/Xorg. 7.3 doesn't support dpkg-reconfigure for screens and graphics anymore. 
 
Nathan

---

### Post by badbunny42 on 2008-05-14
Sorry, I'm new to this still, I don't think understand all of that.
I can get to a terminal in recovery, but what is dpkg-reconfigure?

---

### Post by badbunny42 on 2008-05-14
ok, I found out what dpkg-reconfigure is/was. I'll try xrandr. Thanks

BB42

---

