---
title: "Printers stuck on 'processing'"
date: 2013-09-15
forum: New to Ubuntu
---

### Post by Lowcountry on 2013-09-15
I have three printers connected to a ubuntu 13.04 box.  They have been working great on my network.
Since the last few days, they all get stuck on "processing".  I've restarted the printers, the computer, etc.
Everything is up to date.

---

### Post by azmyth on 2013-09-15
Are you using cups? I would look at cups log to see if there are any errors.

---

### Post by radiowave911 on 2013-09-15
I have encountered a similar issue.  I believe mine was caused by HPLPIP status monitor.  Something seems to have been corrupted.  I removed all my printers, removed HPLPIP, and reinstalled the printers.  They all seem to work correctly now (an HP C6280 connected via USB, an HP Laser 4000TN via ethernet and an HP Color Laserjet 3600dn via ethernet).

---

### Post by Lowcountry on 2013-09-26
Thanks for the replies!
Starting to think it may just be my printer...

---

