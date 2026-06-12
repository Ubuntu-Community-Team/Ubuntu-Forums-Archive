---
title: "Don't use the guest login from lightdm."
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by JRV on 2011-07-30
I tried it, everything seemed to work.
I logged out and logged in as myself.
Most of my custom settings were gone.
All my custom launchers were gone from the launcher bar.
  (They just have to be replaced, they were not deleted.)
The launcher bar was re-set to the default applications.
Global menus returned, and windows had no boarders.

---

### Post by cpatrick08 on 2011-07-31
> **JRV said:**
> I tried it, everything seemed to work.
I logged out and logged in as myself.
Most of my custom settings were gone.
All my custom launchers were gone from the launcher bar.
  (They just have to be replaced, they were not deleted.)
The launcher bar was re-set to the default applications.
Global menus returned, and windows had no boarders.
sounds like a bug you should report the bug at [https://bugs.launchpad.net/lightdm/+filebug](https://bugs.launchpad.net/lightdm/+filebug) if you had not already

---

### Post by drs305 on 2011-07-31
I decided to take one for the team and tried logging in to the Guest account. Here is what happened:

Cold boot and selected 'Guest'.
Taken to purple screen, where it remained for about 30 seconds ( almost rebooted at this point).
It finally logged in as Guest and had the default setup/launchers.
Logged out and logged in as myself.
To my relief, my customizations were intact.

I am using the daily build from yesterday, AMD64, Nvidia card.

I'll try to contribute something to this thread, even though I can't confirm the original problem.

To save your launchers:
```
gsettings get com.canonical.Unity.Launcher favorites > /path/filename
```
You can also, after installing dconf-tools, open dconf-editor and go to Desktop > Unity > launcher and manually save the entry.

To restore:
```
gsettings set com.canonical.Unity.Launcher favorites '[.....]'
```
I don't know if you can import a file directly, so you may just have to paste the saved content between ' '.

---

### Post by JRV on 2011-08-03
After many tries I could not get the problem to repeat.

---

