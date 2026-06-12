---
title: "[SOLVED] Firefox 3.0 Work Offline. Default or bug?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Gyrotwister on 2008-06-14
Every time I open the first instance of Firefox 3.0 in Hardy it comes up in Offline mode.  This never used to happen with Firefox 2 in Dapper.  

I want Firefox open on line, and go straight to my homepage.  
Is there a way to fix this?

---

### Post by SQuark on 2008-06-14
I had the same problem and found a solution in this thread: [http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179)

---

### Post by Gyrotwister on 2008-06-15
Thanks for the link.  Seems it's due to a bug in network-manager.  

I use GNOME PPP with an external dial up modem, so I'm wondering if I can just ditch network-manager.  
 
Can I use Synaptic to uninstall network-manager without breaking anything?

---

### Post by SQuark on 2008-06-15
Sure, shouldn't be a problem.

(And if it is, just reinstall it :p)

---

### Post by Gyrotwister on 2008-06-17
Well there you go!  
It seems network-manager can't manage an external dialup modem.  
I'm better off without it.

---

### Post by jkohler2 on 2008-11-03
> **Gyrotwister said:**
> Well there you go!  
It seems network-manager can't manage an external dialup modem.  
I'm better off without it.
The usb modem (zoom 3095) is all I have for dial-up and I need it.  I will live with
placing the firefox offline to the correct setting as long as it requires that.

John

---

### Post by jkohler2 on 2009-05-08
A new version of Ubntu is out now, with many updates in addition to the
kernel.  I loaded them all.  FireFox still gets active with my Zoom
usb 3095 dialup modem with the "Work offline" box checked, which I have
to un check, each time.  Oh, for a DSL connection!:(

---

