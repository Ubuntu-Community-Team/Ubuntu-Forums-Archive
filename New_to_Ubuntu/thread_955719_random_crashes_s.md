---
title: "random crashes :s"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by fallen seraph on 2008-10-22
I'm running heron on a dell d630 laptop and I'm experiencing random crashes where the laptop just become totally unresponsive, the capslock and scrolllock lights start flashing on and off and I have to pull out the battery to shut the laptop off :(

The crashes don't appear to me to be occurring in any pattern. like they've happened while booting, just after logging in and after having been using the laptop for 2 hours continuously :s

I've no idea where to start to tackle this problem, but any help would be greatly appreciated. This feels like windows 98 :(

---

### Post by egalvan on 2008-10-22
It may be hardwsare-related.

You can run a memory check from the LiveCD
It shows on the initial screen, usually the last option.

Let it run several hours, even better 48 hours.

---

### Post by Crandom on 2008-10-22
i agree, sounds like a memory problem. Run memtest86+ from your grub boot menu. If you don't see a menu, press Esc on startup many times, then select memtest86+. 48 hours of testing seems a bit extreme :(

---

### Post by DrMega on 2008-10-22
> **fallen seraph said:**
> I'm running heron on a dell d630 laptop and I'm experiencing random crashes where the laptop just become totally unresponsive, the capslock and scrolllock lights start flashing on and off and I have to pull out the battery to shut the laptop off :(

The crashes don't appear to me to be occurring in any pattern. like they've happened while booting, just after logging in and after having been using the laptop for 2 hours continuously :s

I've no idea where to start to tackle this problem, but any help would be greatly appreciated. This feels like windows 98 :(

Sounds like you're one of the unlucky ones that is hit by the old Hardy Freeze bug:

[http://ubuntuforums.org/showthread.php?t=765510]("http://ubuntuforums.org/showthread.php?t=765510")

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239021]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239021")

---

