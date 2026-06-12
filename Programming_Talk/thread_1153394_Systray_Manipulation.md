---
title: "Systray Manipulation"
date: 2009-05-08
forum: Programming Talk
---

### Post by dael99 on 2009-05-08
Is there any way to manipulate system tray icons...

I mean replacing the contextual menus of the icons in the system tray with something else... inherit those icons, and replacing the tray.

(this is related to a personal idea respecting the contextual menu of dockbarX)

---

### Post by SKLP on 2009-05-08
You can create your own notification area (tray) icons using the Gtk.StatusIcon class (available in many programming languages).
If you wan't to modify existing icons the best way would probably to get the source code of the application providing the icon in question(since most are open source).

---

### Post by dael99 on 2009-05-12
> **SKLP said:**
> You can create your own notification area (tray) icons using the Gtk.StatusIcon class (available in many programming languages).
If you wan't to modify existing icons the best way would probably to get the source code of the application providing the icon in question(since most are open source).

thanks, but i thinks you have misunderstood. What i want is to manipulate the existing applications in the systray, including network manager)

I think we shouln't have icons in the systray, because they are only there toshow extra menu actions that should be attached to the ricght click of the app in the taskbar.

Is there a way to access the data of the systray??

---

### Post by SKLP on 2009-05-13
The way the systray works is that you start a process (an application) and the app that wants to display an icon "talks" to the systray. So if you want to manipulate the icons, modifying the applications which provide them should be the most obvious way to do that.

---

### Post by dael99 on 2009-05-15
> **SKLP said:**
> The way the systray works is that you start a process (an application) and the app that wants to display an icon "talks" to the systray. So if you want to manipulate the icons, modifying the applications which provide them should be the most obvious way to do that.

no no no.

I want to make a replacement for the systray...
A new way to show notifications icons (no to modify an icon)

well, in fact, i want to replace the systray with something else.

[https://blueprints.launchpad.net/ubuntu/+spec/replace+taskbar+and+systray](https://blueprints.launchpad.net/ubuntu/+spec/replace+taskbar+and+systray)

---

