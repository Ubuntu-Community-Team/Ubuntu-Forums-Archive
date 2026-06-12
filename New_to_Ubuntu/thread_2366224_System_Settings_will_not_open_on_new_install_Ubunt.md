---
title: "System Settings will not open on new install Ubuntu"
date: 2017-07-15
forum: New to Ubuntu
---

### Post by cloake on 2017-07-15
Hello there!

I've been playing around with Ubuntu 17.04 for the past few days and fell in love. Since I hadn't had much invested into my install yet (data-wise), I decided to install it fresh on my new SSD. I've noticed that on this install, I am unable to open System Settings. I've been searching around on the internet for a little while, and haven't been able to find the solution to this particular error. I already attempted to uninstall and reinstall using ```
sudo apt-get remove unity-control-center
sudo apt autoremove
sudo apt-get install unity-control-center
``` and the same commands for the "ubuntu-system-settings" package.

The error title is "system-settings crashes with SIGABRT in QMessageLogger::fatal()"

Update: Another reinstall solved the issue.

---

