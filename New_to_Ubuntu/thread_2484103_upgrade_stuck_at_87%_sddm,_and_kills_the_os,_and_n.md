---
title: "upgrade stuck at 87% sddm, and kills the os, and needs to be reinstalled."
date: 2023-02-17
forum: New to Ubuntu
---

### Post by magnoliafan2000 on 2023-02-17
APT Upgrade FROZEN at  "preparing configuration of sddm"

When I close the window and reset, Lubuntu is unable to start-up again, and I have to delete the partition from Windows, Extend the WINDOWS partition specifically because lubuntu will not install on another partition already set aside and unformatted just for it, then re-install Lubuntu from a USB again. What in tarnation is going on?

---

### Post by #&amp;thj^% on 2023-02-17
First kill the hung command:
```
sudo killall -9 aptd
```
Then try:
```
sudo dpkg --configure -a && sudo apt update && sudo apt full-upgrade
```

This will finish the incomplete installation, then apply any new updates.
This was a bug on Lubuntu 20.04 and Older. but reported as fixed in 22.04

---

### Post by magnoliafan2000 on 2023-02-18
Thank-you! Very much!

---

