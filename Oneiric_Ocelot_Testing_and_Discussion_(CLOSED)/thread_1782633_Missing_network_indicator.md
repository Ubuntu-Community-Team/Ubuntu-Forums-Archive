---
title: "Missing network indicator"
date: 2011-06-14
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-06-14
After the last update of network-manager I am missing my network indicator. I installed the notification-daemon as it is listed as Recommends but still do not have a indicator. Any ideas?

Bill

---

### Post by nm_geo on 2011-06-14
I have the same issue after today's updates.  The indicator is missing but wireless is functioning normally. Looking into it but I have found no fix. Have you filed a bug report?

I went ahead and reported it Oneiric has been almost bug free on this end compared to Natty.  So a little breakage is news Bug #797495

---

### Post by Harry33 on 2011-06-14
> **sparker256 said:**
> After the last update of network-manager I am missing my network indicator. I installed the notification-daemon as it is listed as Recommends but still do not have a indicator. Any ideas?

Bill

The package network-manager-gnome contains a systray applet for GNOME's notification area and it also works for other desktop environments which provide a systray like KDE
or Xfce.

But in Gnome-shell and Gnome-panel (GTK+3) you do not need this package at all. The indicator applet is in panel automatically.

---

### Post by sparker256 on 2011-06-15
With the latest updates today it is back. Will mark as solved.

Bill

---

### Post by VinDSL on 2011-06-16
Interesting!

This morning, my network and volume applets were missing from the tray.

Tonight, I performed an update, and they were back.  However...

When I rebooted, Unity puked, with the following error message:

```

Failed to load session "Ubuntu"

```

The only option (button) was "Log Out".

Soooo, not [SOLVED] for me...  :D

---

### Post by nm_geo on 2011-06-16
My updates went well today and my network-indicator is back.  They sure fixed this problem quickly Bug #797498 looks like it is history now. However there may be future breakage to look forward to.  :)

---

