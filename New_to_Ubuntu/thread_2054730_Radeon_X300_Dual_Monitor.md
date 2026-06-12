---
title: "Radeon X300 Dual Monitor"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by Martwana on 2012-09-07
Hi there. I'm totally new to Linux, but I'm determined to stick with it.

So far I've managed to get Ubuntu 12.04.1 LTS installed fine alongside Windows 7 and also installed BURG for some clean  bootscreens. 

I only have one more issue now, I cannot figure out how to get my dual monitors working. I've got 2 17" del monitors running off a radon x300 card. I know it's a crap card but I do not game or do many graphics intensive things so it does fine, plus it fits snug in my optiplex SFF box. Anyway, currently, my displays are mirrored. That's just annoying. 

When I go to displays and uncheck the box for Mirrored displays and click apply, I get a message telling me theat my card can't display a 2560 x 1080 resolution. It works fine in win 7. After reading about, I seen a lot of talk about xorg.conf and fglrx and radeon driver, but couldn't find anything specific to my card and problem, it was all different OS versions and different gfx cards.

Could someone explain what my problem is, and what the resolution is? Please lol. I don't wanna fork out for new hardware, but on the same note, I do wanna move to Linux. 

As I've seen it on other threads, I have typed lspci -v | grep VGA and I get a message along the lines of VGA supported RV370 (x300), so thought I may as well post that too.

Cheers
Martin

---

### Post by 2F4U on 2012-09-08
What graphics driver are you using, the open source or the proprietary ATI drivers? If you use the proprietary drivers, the AMD control center should take care of this.

[http://askubuntu.com/questions/71457/how-can-i-set-up-dual-monitor-display-with-ati-driver](http://askubuntu.com/questions/71457/how-can-i-set-up-dual-monitor-display-with-ati-driver)
[http://ubuntuforums.org/showthread.php?t=1855750](http://ubuntuforums.org/showthread.php?t=1855750)

---

### Post by Martwana on 2012-09-08
I have no idea what ones I'm currently using, but when I installed amdcccle and ran it, it said there was no AMD drivers found. What do I do now?

---

### Post by newb85 on 2012-09-08
In the dash, search for and run "Additional Drivers".  See whether ATI drivers are listed, and whether one of them is enabled.

---

### Post by Martwana on 2012-09-08
Ive tried that, when i open additional drivers, there is nothing displayed at all in the box.

---

