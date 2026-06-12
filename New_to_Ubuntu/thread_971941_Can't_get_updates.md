---
title: "Can't get updates"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by cartisdm on 2008-11-05
Last week or so I got the little notification in the system tray saying that there are new updates available.  When I tried to complete the updates I get this "Partial Upgrade" thing.  Check out the screenshots, that basically sums it up.

---

### Post by jbrown96 on 2008-11-05
try running the updates through a terminal ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by brandoncolorado on 2008-11-05
> **cartisdm said:**
> Last week or so I got the little notification in the system tray saying that there are new updates available.  When I tried to complete the updates I get this "Partial Upgrade" thing.  Check out the screenshots, that basically sums it up.

Finish the partial upgrade, restart, then run updates again to finish the rest.

---

### Post by cartisdm on 2008-11-05
> **brandoncolorado said:**
> Finish the partial upgrade, restart, then run updates again to finish the rest.

It wont let me finish the partial upgrade, when I click it the "Partial Upgrade" from screenshot_1, I get a progress bar then go straight to  screenshot_2


I will try running them through the terminal as soon as I reboot out of Windowz

---

### Post by brandoncolorado on 2008-11-05
> **cartisdm said:**
> It wont let me finish the partial upgrade, when I click it the "Partial Upgrade" from screenshot_1, I get a progress bar then go straight to  screenshot_2


I will try running them through the terminal as soon as I reboot out of Windowz

Whoops, sorry I didn't see the second screenshot.

If you continue having trouble, disable some of the non-standard repositories.  You can post your sources.list if you would like help with that.

---

### Post by cartisdm on 2008-11-08
weird, I ran it through the terminal and everything went smoothly.  Thanks for the tip!

---

