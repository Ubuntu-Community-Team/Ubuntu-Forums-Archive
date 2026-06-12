---
title: "Upgraded to 13.04 Headaches, Probably Easy Fix"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by playing_with_matches on 2013-06-17
I previously had Ubuntu 10.04 installed on my machine and it worked great for years, until they no longer supported it, so I upgraded to 13.04.  I use the GNOME fallback theme (no effects) and have run into some issues:

1.  I accidentally removed one of the menus (that showed you the running applications) and I can't figure out how to get it back!  Now anytime I minimize something, I can't re-open them.  How do I get that menu back?

2.  Ubuntu seems to be running SIGNIFICANTLY slower and laggy compared to 10.04.  I only have a 1gb of memory in my machine (and 256mb is being taken for graphic reasons).  Do I need more memory to run Ubuntu now? 

3. I can't get the flux application to run.  It's in the processes taking up a lot of the CPU, but it's not running.

---

### Post by MidnightGrey on 2013-06-17
> 3. I can't get the flux application to run.  It's in the processes taking up a lot of the CPU, but it's not running.
Note sure if f.lux has improved since, but last time i checked it wasnt very compatible with linux.
There is a linux-alternative called redshift which does basically the same thing, you can find it in the Software Centre.

---

### Post by MidnightGrey on 2013-06-17
> 1.  I accidentally removed one of the menus (that showed you the running  applications) and I can't figure out how to get it back!  Now anytime I  minimize something, I can't re-open them.  How do I get that menu back?
Haven't used GNOME in a while, i had to log back in to figure this one out.
Do you still have the top panel? if so, just hold SUPER+ALT+RIGHT_MOUSE on it and then select Add New Panel to bring back the bottom panel.
Edit: You then need to hold SUPER+ALT + RightMouse on the bottom panel > Add to Panel > Window List

---

### Post by kansasnoob on 2013-06-17
> I previously had Ubuntu 10.04 installed on my machine and it worked great for years, until they no longer supported it, so I upgraded to 13.04. I use the GNOME fallback theme (no effects) and have run into some issues:


Are you sure you upgraded to 13.04?

The normal *upgrade* path would have taken you to 12.04 (aka: Precise) which is supported for 5 years :D

OTOH [the support cycle for none-LTS versions was reduced to 9 months]("https://wiki.ubuntu.com/Releases") beginning with 13.04 :(

> 1. I accidentally removed one of the menus (that showed you the running applications) and I can't figure out how to get it back! Now anytime I minimize something, I can't re-open them. How do I get that menu back?

It sounds to me like you removed "Window List" from the panel:

[ATTACH=CONFIG]243907[/ATTACH]

You may find some of my notes here helpful:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

> 2. Ubuntu seems to be running SIGNIFICANTLY slower and laggy compared to 10.04. I only have a 1gb of memory in my machine (and 256mb is being taken for graphic reasons). Do I need more memory to run Ubuntu now?

3. I can't get the flux application to run. It's in the processes taking up a lot of the CPU, but it's not running. 

I suspect that those two things are related. First of all logout and be certain you're logged into Classic (no effects) - now called Fallback (no effects) in 13.04 - which uses the Metacity window manager. I've found that session to run acceptably well on as little as an 1100 Mhz CPU w/ only 1GB of RAM.

I've never used 'flux' so I'm clueless about that app :confused:

---

### Post by Impavidus on 2013-06-17
13.04 is indeed significantly more resource-hungry than 10.04. Consider using a different desktop environment, like xfce. You can install xubuntu-desktop and select it at login. 1GiB RAM may not be enough for Unity.

---

### Post by NikTh on 2013-06-17
> **Impavidus said:**
> 13.04 is indeed significantly more resource-hungry than 10.04. Consider using a different desktop environment, like xfce. You can install xubuntu-desktop and select it at login. 1GiB RAM may not be enough for Unity.

I don't think that Xubuntu-desktop is lighter than gnome-fallback (**no effects**). Probably the user must disable some startup applications. As XCFE is not using the gnome startup applications, probably it would appear as lighter. 
The truth is that 1GB of ram (and shared with graphics card) is not enough nowadays. 

Regards
 NikTh

---

### Post by playing_with_matches on 2013-06-18
Thanks for all the suggestions guys, I'll check out redshift as a replacement for flux.  In the meantime, I also just got some more RAM, going to upgrade my 1gb to a 4gb, hoping that will help with some of the performance issues.  

As far as a desktop environment goes, I switched to Cinnamon which I like tons better than Unity.  I currently have xfce, cinnamon, gnome, gnome fallback, and unity all installed, and so far surprisingly Cinnamon seems to be the quickest (even quicker than xfce for some strange reason.)

---

