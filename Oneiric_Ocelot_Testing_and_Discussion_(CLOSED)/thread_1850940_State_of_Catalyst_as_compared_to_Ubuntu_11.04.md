---
title: "State of Catalyst as compared to Ubuntu 11.04"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kaldor on 2011-09-27
My new PC has an AMD 6450 GPU. I use the stock drivers (11.4? 11.3?) as provided by Jockey in Natty. With compiz there are lag issues, and with compiz disabled there are [_graphical glitches_]("http://ubuntuforums.org/showthread.php?p=11290121"). Apparently some of the newer drivers remedy this problem, but due to the nature of proprietary drivers in Linux I don't want to remove and upgrade drivers via the AMD site. 

Are there any people here using a similar (6000 series) GPU? How has the experience been lately on Oneiric with the provided driver? I know that Natty used an unstable version of Compiz which may have been the reason behind some bugs. I also sometimes have issue with suspend. Sometimes, rebooting will freeze when shutting down. Little niggles like that.

I am assuming that many of the issues I have are related to the fact my GPU is fairly new to market (released February 2011 apparently). Because of this, I assume that over time things will improve since the issues I have seem to be very minor. Most everything works without any flaws. If past experiences are anything to go by, I would suspect that by 12.04 my GPU will work just as well as those on my other setups.

My test machine uses an NVIDIA card, so I can't really discover this on my own. I need a working system on the AMD machine and cannot afford to break something via an Oneiric partition. I know that there are similar topics on this subject, but none are specific to my queries. Since Oneiric is due out shortly, the Catalyst drivers available (11.8?) are likely to be quite indicative of the final product.

---

### Post by el_koraco on 2011-09-27
> **kaldor said:**
> Since Oneiric is due out shortly, the Catalyst drivers available (11.8?) are likely to be quite indicative of the final product.

Catalyst 11.8 is working much better than 11.4, which shipped with Natty. But I'm fairly certain Oneiric will ship with 11.9 or .10, The October driver is supposed to be the first to sort out the bulk of the issues with Gnome Shell, but I can't give any testimony to that.

---

### Post by kaldor on 2011-09-27
> **el_koraco said:**
> Catalyst 11.8 is working much better than 11.4, which shipped with Natty. But I'm fairly certain Oneiric will ship with 11.9 or .10, The October driver is supposed to be the first to sort out the bulk of the issues with Gnome Shell, but I can't give any testimony to that.

Is there a list of changes somewhere for 11.8? I couldn't find one.

---

### Post by cjcj on 2011-09-27
I too have an AMD Radeon 6450 and am using Oneric. The version of catalist is 11.8 and it works fine ON ONE MONITOR. 

Whether it is catalist, fglrx or something else, all attempts I have made to get my second monitor working have been futile. Catalyst recognises the second monitor and automatically offers the set up I want ('as the optimum  desktop size').. but no reconfiguration happens when I press the apply button. 

The system settings 'Desktops' will not allow the second monitor to be placed next to the first monitor, only allowing it to occupy the same screen space. 

I am surprised no-one else is reporting this problem on the forum - perhaps I am uniquely doing something obviously stupid.

Anyone got any suggestions?

---

### Post by kaldor on 2011-09-27
> **cjcj said:**
> I too have an AMD Radeon 6450 and am using Oneric. The version of catalist is 11.8 and it works fine ON ONE MONITOR. 

Whether it is catalist, fglrx or something else, all attempts I have made to get my second monitor working have been futile. Catalyst recognises the second monitor and automatically offers the set up I want ('as the optimum  desktop size').. but no reconfiguration happens when I press the apply button. 

The system settings 'Desktops' will not allow the second monitor to be placed next to the first monitor, only allowing it to occupy the same screen space. 

I am surprised no-one else is reporting this problem on the forum - perhaps I am uniquely doing something obviously stupid.

Anyone got any suggestions?

Do you experience the same problems that I do on Natty? 

Compiz on = Laggy Windows, Laggy scrolling, Laggy 3d games, sometimes black screen on startup.

Compiz off = major screen tearing

---

### Post by alphacrucis2 on 2011-09-27
I update my Catalyst driver every AMD release. IMO the current version 11.8 runs much better with Natty than the repo version. My card is an older model than yours so I can't vouch for how it will work for you. Catalyst 11.9 will be released by AMD tomorrow if they keep to their usual scheme of Wednesday releases and it's the last Wednesay of September so...

---

