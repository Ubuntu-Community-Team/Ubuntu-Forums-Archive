---
title: "Appropriate commands to remove thunderbird and Gwibber."
date: 2013-01-19
forum: New to Ubuntu
---

### Post by arroy_0209 on 2013-01-19
I do not use thunderbird and Gwibber in Ubuntu12.04 but auto updates for these keep coming. I want to remove these completely so that I do not get notifications for related updates. However I am confused which command(s) I should use: for thunderbird:
1. sudo apt-get remove thunderbird
2. sudo apt-get remove thunderbird-gnome-support
3. sudo apt-get remove thunderbird-globalmenu

for Gwibber:
1.  sudo apt-get remove gwibber
2.  sudo apt-get remove gwibber-service
3.  sudo apt-get remove gwibber-service-facebook
4.  sudo apt-get remove gwibber-service-identica
5.  sudo apt-get remove gwibber-service-twitter

Also will it be better to replace "remove" by some other stronger command (e.g. "purge") in above cases?

---

### Post by GordThompson on 2013-01-19
If you haven't used either app then it would make very little difference whether you used "remove" or "purge". However, why mess around on the command line when you can just launch the Ubuntu Software Centre, find Thunderbird, and then click the "Remove" button?

---

### Post by ajgreeny on 2013-01-19
I've not tried this myself, but if you do it you may find that **ubuntu-desktop** package is also removed.

This is not as much of a disaster as it may sound as that package is nothing more than information for the system (a metapackage) and its removal will not hurt day to day running.  If you tried to do a distro version update from, say 12.04 to 12.10, you would find that the ubuntu-desktop package is definitely needed to ensure everything is updated properly.

---

### Post by Paqman on 2013-01-19
```
sudo apt-get remove thunderbird gwibber && sudo apt-get autoremove
```

Following the removal of the main packages with apt-get autoremove will make sure that any dependencies that were installed for gwibber and thunderbird will get removed too.

The issue with removing Gwibber taking ubuntu-desktop with it has been fixed on Precise (12.04) or later versions.

---

