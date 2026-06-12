---
title: "Flash video issues"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by clevercasey on 2008-10-28
I am relatively new to Ubuntu...I have recently been switching back and forth between this and Windows Vista. After playing around and playing with things to find what I like...I am ready to make the switch for good. However there is one issue regarding flash videos that is driving me crazy to no end. 

Everything plays fine...no stuttering, sound issues, etc. However, I notice videos start to tear or look like someone took some scissors to them when there is a lot of movement going on in the videos. Horizontal lines going through the video. I never noticed this problem with flash videos running under Windows before. I have tested this on multiple flash video sites. Youtube, Hulu, and quite a few more. I am wondering if this is normal or some weird problem only I have.

I have searched around endlessly trying to figure out what could be causing this but so far have had no luck. I have even tried disabling hardware acceleration in the flash settings. My system shouldn't be having any issues...

Intel Core Duo 2x1.73 GHz
3GB Ram (it's 4 but 32 bit limitation makes it 3)
Intel 945 Integrated Video

Currently running the 8.10 Intrepid release candidate. 

Any advice or suggestions would be very much appreciated. Thank you.

---

### Post by quibbler on 2008-10-28
Do you have the latest flash 10? you can read about it here:

[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

regards quibbler

---

### Post by philinux on 2008-10-28
If he's running Intrepid then he has flash 10.

---

### Post by vivichrist on 2009-11-17
is one cpu at 100% ?

---

### Post by ArinSky on 2009-11-18
sometimes its a problem with gnash of swfdec taking over as default, you can test by right clicking on the flash video that isn't running and clicking preferences. If it's swfdec or gnash it will say that instead of flash in the window that pops up. If that is the case, run these commands to get rid of them. I find that they don't work often, and when they do they are slow and jumpy, as well as the problem you described.

```
sudo apt-get remove flashplugin-* --purge
 sudo apt-get remove --purge swfdec-mozilla swfdec-gnome mozilla-plugin-gnash gnash
 sudo apt-get install flashplugin-nonfree
```

---

### Post by nunovi on 2009-11-21
Hi,

It's a well known problem that flash on Linux performs horribly slow, especially on Atom-based system as the GPU is not used. I don't want to discourage you but there is really no solution other than Adobe to fix Flash on Linux.

If we make this issue big enough, we can gain a higher priority for Adobe to solve this issue. Please go to [https://bugs.adobe.com/jira/browse/FP-1692](https://bugs.adobe.com/jira/browse/FP-1692), register and vote for this issue. If we all take 5 minutes to do this, I'm sure we can reach a very high number of votes and let Adobe know Linux is an important community to take into consideration.

Nuno

---

### Post by ibuclaw on 2009-11-21
Old Thread - Closing.

If you are having this issue, raise a new support question.

Regards
Iain

---

