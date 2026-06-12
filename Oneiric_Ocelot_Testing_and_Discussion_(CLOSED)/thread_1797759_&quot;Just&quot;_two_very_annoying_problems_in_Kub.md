---
title: "&quot;Just&quot; two very annoying problems in Kubuntu Daily ..."
date: 2011-07-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xeizo on 2011-07-05
1. Neither mouse nor keyboard works at the KDM-screen, but if both is USB-devices I can remove and insert them again in which case they work. Keyboard always work perfect in CLI. I can't use a non-USB keyboard at all.

2. I ALWAYS get the "dummy output" for sound after a reboot, I've tried numerous fixes and workarounds but none is persistent after a reboot. The most simple fix at the moment is to do sudo alsa force-reload after every login.

All this happened yesterday and I obviously haven't been able to fix it, but as "almost" everything else works fine except virtualbox having slow harddisk throughput I'm not overly amused by doing a full reinstall with all necessary post-install tweaks having to be repeated.

ANY idea what to do?  :)

---

### Post by PaulW2U on 2011-07-05
> **xeizo said:**
> 1. Neither mouse nor keyboard works at the KDM-screen, but if both is USB-devices I can remove and insert them again in which case they work. Keyboard always work perfect in CLI. I can't use a non-USB keyboard at all.

2. I ALWAYS get the "dummy output" for sound after a reboot, I've tried numerous fixes and workarounds but none is persistent after a reboot. The most simple fix at the moment is to do sudo alsa force-reload after every login.

I'm not seeing either of those problems but my recent installation from a daily build has produced these two minor issues:

1) There's no notification when my USB hard drive is connected. This works in Natty and I'm sure that the settings are the same.

2) The Krusader icon is missing from the menus and task bar and no amount of fiddling has brought about its return.

I've not had time to look for bug reports but at this stage Oneiric is very stable, not one crash, perhaps KDE 4.7 will change that when the time comes. ;)

*[COLOR="DarkRed"]Edit: Krusader icon brought back by changing icon theme and back again, so just the USB problem now[/COLOR]*

---

