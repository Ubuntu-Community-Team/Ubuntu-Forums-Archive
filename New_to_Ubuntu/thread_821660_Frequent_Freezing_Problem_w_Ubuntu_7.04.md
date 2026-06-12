---
title: "Frequent Freezing Problem w/ Ubuntu 7.04"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Cooper87 on 2008-06-07
hello everyone.  I'm new to the ubuntu forums but since I've switched from Windows XP, I've had nothing but issues.  At this point, I've eliminated numerous problems and all I've got left to do is download the rest of the 576 updates that will complete my Feisty Fawn update package.  Unfortunately, ubuntu freezes and locks up very frequently and it is taking me days to upload it simply because I've had to reboot and restart the download *so many times.* Now it's freezing even without me starting the update process again.  I'm good with computers, but I'm just not familiar with linux and ubuntu just yet.  Does anyone have any ideas? Any help or helpful links would be greatly appreciated.

---

### Post by quelx on 2008-06-07
If you have a wired connection on this system try upgrading from the console.

**CTRL-ALT-F1** and login as your normal user and try these

```
sudo /etc/init.d/gdm stop
sudo apt-get update
sudo apt-get upgrade
```

When it completes then ```
sudo reboot
```

---

