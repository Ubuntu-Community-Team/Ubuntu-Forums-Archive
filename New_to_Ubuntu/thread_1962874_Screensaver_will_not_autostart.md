---
title: "Screensaver will not autostart"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-04-21
KDE Screensaver (any) worked fine for a week, but now won't auto start.  This problem happens no matter what screensaver I use. They all ru fine in Test mode. Have searched KDE forums, KDE documentation & Ubuntu Community, but cannot find any answers. There is no item listed in /.kde/share/config/kscreensaverrc for a timer setting - listed are:
 [ScreenSaver]
 ActionBottomLeft=0
 ActionBottomRight=0
 ActionTopLeft=0
 ActionTopRight=0
 Lock=false
 LockGrace=4000
 PlasmaEnabled=false
 Priority=0
 Saver=koceansaver.desktop
 Timeout=60
 
 Renamed ~/.kde/share/config/kscreensaverrc to old, rebooted, still no change.
 Would you know where to edit screensaver timer listing?
 There are some errors listed in the KDE logs, which doesn't mean anything to me, but which I could paste here if you can identify specific log & error type listing.

---

### Post by rotave on 2012-04-21
the timer setting is the timeout field. at the moment you have the screensaver to come on after 60 seconds of inactivity. having said that though, not sure why it isn't working for you.

---

### Post by critin on 2012-04-21
I don't know KDE, but ubuntu doesn't have settings for seconds, only minutes.

> Timeout=60

Could this be minutes instead of seconds?

---

### Post by whatthefunk on 2012-04-21
You can configure your screensaver in System Settings > Hardware > Display and Monitor

The Timout entry is in seconds, not minutes.

As for the problem, Im stumped.  Ive set my screensaver up to test it and it works fine.  Well see if mine breaks too.

---

