---
title: "how to keep computer from logging out"
date: 2021-09-30
forum: New to Ubuntu
---

### Post by barochia on 2021-09-30
Hi!   How can I keep my computer (with Ubuntu 20.10) recently installed - from logging off, every time it goes to sleep?  I am not a business - I just use my computer at home.    Thanks!

---

### Post by guiverc on 2021-09-30
Ubuntu 20.10 (*along with all flavors*) is [B]End-of-Life

[/B]- [https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/](https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/)

- [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

If it was only *recently* installed; I'd suggest starting with a supported release of Ubuntu/Lubuntu; being aware that 20.10 means the 2020-October release; which had 9 months of *supported life, *thus 10 (or October) + 9 months = 2021-July for EOL.  Only LTS or *long term releases* come with longer lives (ie. Ubuntu 20.04 LTS comes with 5 years of support; Lubuntu 20.04 LTS *being a flavor* comes with 3 years of *supported life*.

As for *locking*, look at [URL="https://manual.lubuntu.me/stable/3/3.2/3.2.20/screensaver.html"]https://manual.lubuntu.me/stable/3/3.2/3.2.20/screensaver.html
[/URL]
(*where the manual page I provided is the stable release, ie. currently 21.04*)

though please note - the screenlock is a different routine to what you get when you initially login, so if you're being returned to `sddm` or the greeter (ie. actually being logged out), that won't be your issue (*xscreensaver's lock screen is very different to the greeter*)

---

### Post by T6&amp;sfpER35% on 2021-09-30
i go to screensaver and disable the lock screen

---

### Post by poorguy on 2021-09-30
[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

---

### Post by GhX6GZMB on 2021-09-30
The easiest way is to kill the screensaver:
"Preferences -> LXQt settings -> Session settings", select "Autostart" and untick XScreensaver.

---

