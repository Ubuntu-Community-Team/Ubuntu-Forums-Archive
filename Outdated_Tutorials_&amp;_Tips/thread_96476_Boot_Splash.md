---
title: "Boot Splash"
date: 2005-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by PinkFloyd56 on 2005-11-28
You know how on Ubuntu when it boots up it has a list saying all the stuff is being set up, etc? Well is there a way to put a graphical loader on it? I know some other Linux distro's use it, like SuSe or something.


Jon

---

### Post by amohanty on 2005-11-28
breezy (ubuntu 5.10) comes with usplash that does exactly that, by default too.

AM

---

### Post by PinkFloyd56 on 2005-11-28
Using the update manager, could I update Hoary to Breezy?

---

### Post by amohanty on 2005-11-29
you have to do a dist-upgrade. I would suggest reading up about it in the wiki and the forums before trying it, since its a major change.

AM

---

### Post by PinkFloyd56 on 2005-11-29
But how can I safely do it? Get the installer disc for Breezy then just run it through like i'm reinstalling my system?

---

### Post by amohanty on 2005-11-29
I went that route because my /home is on a separate physical drive and all my config files are in cvs. 

However, I would suggest backing up all your /home contents and any config files you may have modified/installed and then follow the instructions provided here very, very carefully:
[https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgradeNotes?highlight=%28upgrade%29)
and then the instructions here:
[https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28upgrade%29)

HTH
AM

---

### Post by ghosthere on 2005-12-02
So.....can you install usplash in 5.06, maybe a aptget sort of thing or will it just not work without 5.10 installed?

---

### Post by Xian on 2005-12-03
[QUOTE=PinkFloyd56]Using the update manager, could I update Hoary to Breezy?[/QUOTE]
Yes, you can...however, if you are seriously thinking about upgrading an entire system just to get a visual boot screen then IMO you really are nutz. The more reasonable play would be to install [Upower](http://www.nanofreesoft.org/index.php?module=subjects&func=viewpage&pageid=1) on your 5.04 system. There's a thread or two in the forum about this if you'll do a quick search. Or, if you've compiled a kernel before you could just as easily include a bootsplash patch.

[How-To Upgrade To Breezy](https://wiki.ubuntu.com/BreezyUpgrade?).

---

