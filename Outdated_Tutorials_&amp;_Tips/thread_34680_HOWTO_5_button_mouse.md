---
title: "HOWTO: 5 button mouse"
date: 2005-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Oblivious Hazard on 2005-05-15
type in: sudo gedit /etc/X11/xorg.conf

and scroll down to the mouse and replace the last 3 lines with this:

Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"

---

### Post by pdk001 on 2005-05-25
i've got a cordless mouse(logitech) now the side botton is work fine as well
thank you

---

### Post by Spike on 2005-06-02
I asked this in another thread, but hopefully you can answer me...

Any idea how I can...
* Have my scroll-wheel scroll a page at a time...
* Have pressing my scroll-wheel initiate a double-click...

Thank you in advance.

---

### Post by mrbass on 2005-06-02
Anyone know a way to map 4th or 5th or 6th or 7th mouse button to kompose or skippy (mac os x Expose for linux).  I'm kinda addicted to doing that on mac.

---

