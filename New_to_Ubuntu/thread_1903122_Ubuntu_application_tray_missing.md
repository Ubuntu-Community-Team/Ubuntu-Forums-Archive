---
title: "Ubuntu application tray missing"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by jhayward_ct on 2012-01-01
I'm a novice with Ubuntu which my son loaded on my wife's Sony VAIO laptop over a year ago when she had issues with Windows Vista and has been working fine until recently.

About a month ago Ubuntu started requesting Wireless Network Authorization with each login when it did not in the past. Two days ago the authentication request would appear during the session.

Yesterday, it accept the key but the application tray on right wold not respond even when I click the Windows key. Today Wireless Authentication process does not accept the key.

I would like to reload the Ubuntu application but can't get the tray with applications icon to appear on right. Even the top Icons for Shut Down, Wireless and Sound are missing.

Is there a way to reset the Ubuntu dashboard/desktop back to normal?:(

---

### Post by LinuxFan999 on 2012-01-01
Which version of Ubuntu is on your wife's laptop?

---

### Post by wildmanne39 on 2012-01-01
Hi, if you are using unity which it sounds like you are you can do it this way if something changed in compiz that caused it
```
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
rm ~/.compiz-1/session/*
rm ~/.config/compiz-1/compizconfig/config
```
I just had to do that to mine a couple of hours ago then log out and back in.
Thanks

---

