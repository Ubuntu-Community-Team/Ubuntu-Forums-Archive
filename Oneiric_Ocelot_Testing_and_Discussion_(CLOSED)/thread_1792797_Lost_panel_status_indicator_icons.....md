---
title: "Lost panel status indicator icons...."
date: 2011-06-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-06-28
.... and the global menus.

This from an install from yesterday's daily-live and updated about half an hour ago. A fairly hefty update too, including the 3.0.2 kernel. After rebooting all I have left in the panel is the Ubuntu button and the application window title.

Anyone else seeing this? Or rather, not seeing these?

---

### Post by Framli on 2011-06-28
Same here. You get them back if you reinstall indicator-*-gtk2 packages. I don't know if those packages were supposed to be uninstalled so early.

---

### Post by georgelab on 2011-06-28
Reinstalling indicators package worked for my netbook.

---

### Post by coffeecat on 2011-06-28
> **Framli said:**
> Same here. You get them back if you reinstall indicator-*-gtk2 packages. I don't know if those packages were supposed to be uninstalled so early.

Thanks for that. Curiously, of the seven that are listed as (suggested) dependencies of Unity (appmenu, application, sound, datetime, messages, me and session) only datetime and sound were missing from my system. But installing those two brought everything back, including the global menus.

They must be the seven musketeers - "All for one; one for all." :wink:

---

### Post by P-I H on 2011-06-28
The indicators are gone.
The upper panel is green, the desktop background is black, alert messages are red and nothing is visible in application windows.

---

### Post by PhantmKllr on 2011-06-28
Well, the indicators are back now (after update ;) ), and there's now a "Post to Twitter" box in the Me menu. Awesomeness?

---

### Post by PhantmKllr on 2011-06-28
OMG. The new Twitter box actually works! FTW!

---

### Post by jerrrys on 2011-06-28
just finished update on Xubuntu and no longer have a bottom panel, but thats ok with me :)

---

### Post by Framli on 2011-06-28
> OMG. The new Twitter box actually works! FTW!
Enjoy it while it's still here. The Me Menu is going away in favor of a better Messaging Menu [https://wiki.ubuntu.com/MeMenu](https://wiki.ubuntu.com/MeMenu) | [https://wiki.ubuntu.com/MessagingMenu](https://wiki.ubuntu.com/MessagingMenu) (specs have been updated yesterday).

---

### Post by PhantmKllr on 2011-06-28
> **Framli said:**
> Enjoy it while it's still here. The Me Menu is going away in favor of a better Messaging Menu...
Aww, MAN! Sadness. :(

---

### Post by castrojo on 2011-06-29
Updating today should fix the indicators.

---

### Post by P-I H on 2011-06-29
> **Framli said:**
> Same here. You get them back if you reinstall indicator-*-gtk2 packages. I don't know if those packages were supposed to be uninstalled so early.

After installation of the 29/6 daily build and installation of all the gtk2 indicators, it is possible to use the system again.

---

### Post by jerrylamos on 2011-06-29
> **castrojo said:**
> Updating today should fix the indicators.

29 June daily build - updating didn't, I had to manually get the indicators going.  

Only things showing are an envelope, GMT time, and power indicator.  BTW, restart didn't, I gave up looking at a blank screen and physically powered off/on.

Network applet is still missing.  I had to fuss around with apps a few times to get wireless going for this netbook.

Currently gives the appearance of being up and running.  I do use casper-rw which works so I'm not starting from zero on every reboot.

Usual lightdm crashes and _usr_lib_gnome-settings-daemon_gnome-settings-daemon.999.crash.

Wonder how close this is to the June 30 Alpha 2.

Jerry

---

### Post by cariboo on 2011-06-29
ALpha 2 won't be released until July 7th. Check the updated [release schedule]("http://ubuntuforums.org/showthread.php?t=1747647").

---

### Post by jppr on 2011-06-30
Ha-Haa :p system works again. Just did latest upgrades and Ubuntu with Nvidia-current driver works fine

---

