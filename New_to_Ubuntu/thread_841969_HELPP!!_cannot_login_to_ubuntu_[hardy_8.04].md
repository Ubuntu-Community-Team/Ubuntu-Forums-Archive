---
title: "HELPP!! cannot login to ubuntu [hardy 8.04]"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Lenz on 2008-06-26
[toshiba a200 laptop dual boot vista 32 and ubuntu hardy 8.04] okay heres the deal so im fairly new to linux. been using ubuntu for 3 weeks. long story short, i pretty much uninstalled everything that has to deal with alsa because i was trying to fix the sound problems i have(realtek soundcard ALC 861VD) i went to a forum that says to do this and that since when i plug in my headphones i hear sound coming out from both speakers and headphones at the same time...so i reboot after, tried xmms and no sound comin out. also tried vlc, it was perfectly fine. i got pissed so i uninstalled everything that has to do anything with alsa. :confused: next thing i know i can't login. grub's still working but i cant get to the login [splash?] screen...enter ubuntu and a black screen pops out and asks for my password and that how far it goes. i know this is long...help anyone?

---

### Post by tamoneya on 2008-06-26
try logging in in terminal and then run the follow command.  Then reboot:```
sudo dpkg-reconfigure ubuntu-desktop
```This is assuming you are using ubuntu as opposed to kubuntu or xubuntu.  The package changes.  I believe it is kubuntu-desktop and xubuntu-desktop but I am not 100% positive because I dont use those distros personally

---

