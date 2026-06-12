---
title: "ubuntu not showing in GNU GRUB Boot menu"
date: 2012-07-26
forum: New to Ubuntu
---

### Post by Jays2Kings on 2012-07-26
I recently applied some updates on Ubuntu and when I restarted I booted up windows first then rebooted to Ubuntu. Now the boot menu only shows windows 7 and recovery environment options but no Ubuntu or other Linux options. What can I do to boot into Ubuntu again or get the options back?

---

### Post by drs305 on 2012-07-26
Jays2Kings,

Welcome to the Ubuntu Forums!

First, you could try editing the Recovery option in the GRUB menu. Press 'e' to edit the menu. Cursor to the end of the 'linux' line and remove "recovery" or "single" and press F10 to boot. If it boots, let us know. If not:

Boot an Ubuntu LiveCD, install Boot Repair, and click the "Recommended Repair" button. That is probably the easiest solution. If it doesn't work, run the info script and post the contents of RESULTS.txt or the link to it provided by Boot Repair.

Link to Boot Repair in my signature line.

---

