---
title: "Cannot figure out how to download amd graphics card drivers"
date: 2015-04-04
forum: New to Ubuntu
---

### Post by anthony58 on 2015-04-04
I just downloaded Ubuntu and I am new to Linux.  I am running the latest version of Ubuntu that I updated to in the Ubuntu updater.  I know I have to download or enable or do something for graphics card drivers for videos and games to run better.  My graphics card is an amd radeon hd 7750.  I would like to know how to install the correct and/or best drivers for my graphics card and maybe how to update the drivers if I ever have to in the future.

---

### Post by monkeybrain20122 on 2015-04-04
Search for Software&Update in the dash, open it and go to the additional driver tab and choose the one and it will do it automatically.

---

### Post by Mark Phelps on 2015-04-04
>  I would like to know how to install the correct and/or best drivers for my graphics card

The correct drivers are already installed.  That is done as part of initial installation.  IF you didn't already have the correct drivers, you would not be able to see a desktop. You should be able to see videos with the default drivers, just fine.

The "restricted" drivers are proprietary drivers offered by AMD.  These are only needed if you are doing high-end 3D gaming -- and NOT trying to run Windows games.  If you're not doing this gaming, you don't need the restricted drivers.

---

### Post by rishav2 on 2015-04-04
> **Mark Phelps said:**
> The correct drivers are already installed.  That is done as part of initial installation.  IF you didn't already have the correct drivers, you would not be able to see a desktop. You should be able to see videos with the default drivers, just fine.

The "restricted" drivers are proprietary drivers offered by AMD.  These are only needed if you are doing high-end 3D gaming -- and NOT trying to run Windows games.  If you're not doing this gaming, you don't need the restricted drivers.

Quite unrelated, I know, but you wouldn't happen to be the same Mark Phelps who helped me out [here]("http://www.eightforums.com/installation-setup/63951-dual-booting-windows-8-1-ubuntu-14-room-expand.html#post490533"), would you?

---

### Post by trag on 2015-04-05
Further to proprietary drivers supplied by AMD,It has been my experience they do not seem to perform as well as those provided by Ubuntu team, but mileage may vary by user.

---

### Post by Mark Phelps on 2015-04-05
> **rishav2 said:**
> Quite unrelated, I know, but you wouldn't happen to be the same Mark Phelps who helped me out [here]("http://www.eightforums.com/installation-setup/63951-dual-booting-windows-8-1-ubuntu-14-room-expand.html#post490533"), would you?
Yes ...

---

### Post by Mark Phelps on 2015-04-05
> **trag said:**
> Further to proprietary drivers supplied by AMD,It has been my experience they do not seem to perform as well as those provided by Ubuntu team, but mileage may vary by user.

This depends entirely on usage.  If you're just doing typical 2D graphics (web browsing, 2D gaming), the default Radeon drivers are quite sufficient.  I regularly switch between them and the AMD drivers just to see if the latter make any difference, and from the visual perspective, I don't see any difference.

However, if you do intense 3D gaming and need to overclock the GPU(s) and/or adjust video features specific to gamine, then the restricted drivers are essential.  The Radeon drivers don't offer the degree of hardware acceleration or feature customizing.

---

### Post by MartyBuntu on 2015-04-05
> **Mark Phelps said:**
> These are only needed if you are doing high-end 3D gaming -- and NOT trying to run Windows games. 


...or power saving...

...or CPU frequency scaling, occasionally.

---

