---
title: "Compiz edge flipping again"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by monkeybrain20122 on 2014-01-06
In one of my Ubuntu 13.10 install I experience this strange situation. When moving a file from one folder to another by dragging from one opening nautilus tab to another (or one instance of nautilus window to another) edge flip stops working and need to re-enable through ccsm. So does moving icon from dash to Unity launcher. I can reproduce it 100% of the time.

This is quite strange as it only happens with one 13.10 but not the other. The configurations are pretty much the same execpt the problematic one uses the Nvidia driver while the good one uses noveau (as far as I am aware of in terms of configurations) They both boot off the same machine (noveau on external drive)

Reference [http://ubuntuforums.org/showthread.php?t=2156531](http://ubuntuforums.org/showthread.php?t=2156531) Basically I have disabled automatic plugin sortings in ccsm and put wall in the end, and also put wall in the end  in gcof-editor appa > compizconfig-1 > profiles > unity > general > screen0 > options > list of active plugins.

Thanks for any advice.

---

### Post by monkeybrain20122 on 2014-01-06
Ok this may be relevant. On this installation I have also installed gnome-flashback (or whatever it is called) just to check it out. Maybe it messes up something? Will try removing it tonight..

---

### Post by mc4man on 2014-01-06
Haven't seen any issue here on 14.04 with edge flipping (though still disable auto plugin sorting after initial setup.
This install is about 2 months old

Whether being 14.04 matters not sure,  for the most part there has been little change so far in unity & compiz as compared to 13.10
Noting  that here use rotate & don't use grid, though again not likely a factor. 
Also am using a modded unity & compiz but can't see that the changes would make any difference here.

At the end of the day 13.10 doesn't really matter as it has a short life, here see no reason to use it, 14.04 is fine with only a few issues, mainly related to new gtk

---

### Post by monkeybrain20122 on 2014-01-06
> **mc4man said:**
> 

Whether being 14.04 matters not sure,  for the most part there has been little change so far in unity & compiz as compared to 13.10



Just out of curioisty, do you know if 14.04 will get Compiz 0.9.11? Will 0.9.11 ever be released, or is it just a mythical milestone?

---

### Post by monkeybrain20122 on 2014-01-06
> **mc4man said:**
> 
At the end of the day 13.10 doesn't really matter as it has a short life, here see no reason to use it, 14.04 is fine with only a few issues, mainly related to new gtk

Well except for this one little annoyance 13.10 is really nice, it is fast and smooth (much better than 12.04) and I set it up exactly the way I want, get all the up to date software... So no, no update to 14.04  for me til July, thank you very much. :)  By then I am probably getting a new computer.

---

### Post by monkeybrain20122 on 2014-01-06
Removed gnome-session-flashback and rebooted. Still the same, dragging a file from Nautilus to desktop kills edge flip instantly. So either gnome-session-flashback has nothing to do with it or that I have already messed up some configuration somewhere by installing it in the first place..

---

### Post by mc4man on 2014-01-06
compiz in 14.04 is basically  0.9.11,  don't think they'll be much but some bug fixes

---

### Post by monkeybrain20122 on 2014-01-06
Ok, this is not a big issue but it does bother me. Just move some files from Nautilus to desktop and back in the other 13.10 install and edge flip still works.

I will try to copy the compiz configuration from the one where edge flip is not broken to the other one, just wonder where does compiz store its configuration other than .config/compiz-1 and .compiz/session(which is empty) ..

---

