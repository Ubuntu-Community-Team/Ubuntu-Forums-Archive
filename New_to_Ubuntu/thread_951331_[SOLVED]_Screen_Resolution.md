---
title: "[SOLVED] Screen Resolution"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by JoHenning on 2008-10-18
Hi

i just installed ubuntu like 2 hours ago, i have never worked on it before or on any other linux based machine, the terminal is just like reading chinese to me.

I would like to change my screen resolution right now it's 800x600 and thats the highest i can choose under system preferences -> screen resolution, i would like to have 1024x768 i tried doing it using instructions i found through google but i just dont figure it out.

How do i do it? As simple as possible :)

Henning:)

---

### Post by eternalnewbee on 2008-10-18
> **JoHenning said:**
> Hi

i just installed ubuntu like 2 hours ago, i have never worked on it before or on any other linux based machine, the terminal is just like reading chinese to me.

I would like to change my screen resolution right now it's 800x600 and thats the highest i would like to have 1024x768.

How do i do it?

Henning:)

Go to Main Menu > System > Preferences > Sreen Resolution and change it from there.

---

### Post by Bucky Ball on 2008-10-18
What machine are you using and specifically, what graphics card?

To find the graphics card, open a terminal (breath and stay relaxed, it's not that bad) and paste this in:

```
**lspci**
```

Hit return, have a look and find your graphics card then let us know. You may need to load the appropriate drivers for it. :)

---

### Post by eternalnewbee on 2008-10-18
Btw, welcome to Ubuntu.
It would also be handy to mention your system specifications.
Mine are:
Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

### Post by eternalnewbee on 2008-10-18
You can find more extensive info about your system in Main Menu > System Tools > Sysinfo.
If you don't have Sysinfo, you can install it via Main Menu > Add/Remove and search for it, tick, and apply.
Good luck.

---

### Post by JoHenning on 2008-10-18
i have an AMD Athlon 2800
memory: 439.9mb

my graphics card is nvidia nForce2 igp2

my screen is a SyncMaster 701n by Samsung

:guitar:



by the way i don't have internet onmy ubuntu computer yet 
im using another com right now

---

### Post by niccholaspage on 2008-10-18
Go to System>Administration>Hardware Drivers. Enable any that are not checked. Reboot and this should be fixed.

---

### Post by Bucky Ball on 2008-10-18
> **niccholaspage said:**
> Go to System>Administration>Hardware Drivers. Enable any that are not checked. Reboot and this should be fixed.

If all updates and ubuntu-restricted-extras aren't installed, and they won't be as there is no internet connection, the nvidia restricted driver will probably not be there. But yes, that is the fix. Plus installing nvidia-settings to tweak the card from Synaptics. :)

---

### Post by JoHenning on 2008-10-18
Ok so basically as soon as i have my Internet connecting it should work.

Thanks everyone

---

