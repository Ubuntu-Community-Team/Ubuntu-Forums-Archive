---
title: "Time in Wine"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by cooljeff3000 on 2008-11-11
I have installed shareware in wine and the timer ran out and i was wondering if there was a way to set the time back a few years for just a single application

---

### Post by gandaran on 2008-11-11
if you haven't any other important applications installed, just delete the hidden home .wine (home/'user'/.wine) folder and install the same program again

---

### Post by Kellemora on 2008-11-11
Hi Cool Jeff

There is actually an easier way!
If Wine is installed in your user directory.

To to System Administration Users & Groups

Create a New User named something like ShareGames

Install WINE in your new User ShareGames Directory.

Before you install the game, if you want to take the trouble to go through every single file in wine and then find the one this particular game writes it's expiration data into, you can just delete that file each time it expires.  Unless it's in a system file.

If not, then just uninstall wine from that directory and reinstall it and you can use the game again.  Usually!

Now don't you wish you knew that before you installed it to your home/user directory, hi hi........

TTUL
Gary

---

