---
title: "[SOLVED] Wicd Broke For No Reason"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by KevinD_Atl on 2008-06-15
[FONT="Tahoma"]Ubuntu 7.10

So I have been using Wicd in liue of the Network Manager/Wi-Fi Radar and it was working great for the last month.  Yesterday, I tried to launch and it does nothing.  I have a read around, but no real answers.  One direction was to check Python2.4 instead of the 2.5 but not sure how to check that, or to even find the logs when it errors out.[/FONT]

---

### Post by imdano on 2008-06-15
Try deleting /opt/wicd/data/wired-settings.conf, then restart the daemon with ```
sudo /etc/init.d/wicd start
```Then try starting up the tray/gui again.

---

### Post by KevinD_Atl on 2008-06-15
Booya, you the man.  I should have also noted that it happened when I plugged in my wired connection, then it just froze for a minute and closed.

---

