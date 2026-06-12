---
title: "Help With Ubuntu Laptop"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Surion84 on 2008-11-24
I just installed ubuntu on a hp G60-120US laptop.  Everything is working decently though i still believe i am having problems with my Nvidia GeForce 8200m.  though thats not the problem, currently when i try to go to youtube on firefox or use fancast the browser freezes.  Also i love my bittorrent and i was wondering how to get java and Vuze on the ubuntu system.  Then one last problem is that i have sound but the speakers sound muffled or like they aren't as loud as they should be.  

Problems:

1. Firefox freezes when using youtube or fancast

2. How to install java and azureus on my system

3. If there is a way to fix the sound.

If anyone could help me with any of these problems i would be ever so greatful and i am a complete idiot when it comes to using ubuntu or any linux.  This is my first time ever using it

---

### Post by taurus on 2008-11-24
You probably need the ubuntu-restricted-extras package.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by diablo75 on 2008-11-24
> **Surion84 said:**
> 1. Firefox freezes when using youtube or fancast

2. How to install java and azureus on my system

3. If there is a way to fix the sound.


1.  Try installing the restricted extras.  (Click Applications>Add/Remove.  Change the filter to say "All Available Applications" and search for "restricted".  Check off "Ubuntu Restricted Extras")

2.  If I were you, I'd try using Deluge as an alternate bittorrent client.  You can search for "deluge" in the same Add/Remove applet.  Click Apply in the lower right to install the packages you've checked off.

3.  Check the sound levels by clicking on the little speaker icon in the upper right corner on your panel next to the clock.  If you poke around in there, you should be able to show bass and treble controls, as well as additional PCM levels.  (Windows does this to by default, not displaying all your available mixers by default).

---

### Post by ad_267 on 2008-11-24
What version of Ubuntu are you using? 8.10 comes with flash player 10 which is supposed to fix a lot of problems.

To install azureus go to Applications - Add/Remove, search for Azureus and mark it for installation. Or click here: [apt:azureus]("apt:azureus")

---

### Post by Surion84 on 2008-11-24
Thank you so very much! I think i am going to be using ubuntu for a long, long time just from the lack of sarcasm and helpfulness from everyone thank you again.

---

### Post by 2hot6ft2 on 2008-12-12
> **Surion84 said:**
> I just installed ubuntu on a hp G60-120US laptop.  Everything is working decently though i still believe i am having problems with my Nvidia GeForce 8200m.  though thats not the problem, currently when i try to go to youtube on firefox or use fancast the browser freezes.  Also i love my bittorrent and i was wondering how to get java and Vuze on the ubuntu system.  Then one last problem is that i have sound but the speakers sound muffled or like they aren't as loud as they should be.  

Problems:

1. Firefox freezes when using youtube or fancast

2. How to install java and azureus on my system

3. If there is a way to fix the sound.

If anyone could help me with any of these problems i would be ever so greatful and i am a complete idiot when it comes to using ubuntu or any linux.  This is my first time ever using it

For 1. and 2. go here [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

For 3. here [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) which also helps fix #1

I have a G60-125NR which is a lot like yours.

---

