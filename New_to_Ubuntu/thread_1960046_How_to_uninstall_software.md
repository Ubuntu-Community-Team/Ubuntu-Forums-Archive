---
title: "How to uninstall software"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by paulv1 on 2012-04-16
thanks i used this to uninstall avast after it tried to update and crashed thereafter. whilst uninstalling it told me libxssl had been installed alongside and was no longer needed. i tried to uninstall with apt-get autoremove libxssl to get the message
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
 what does this mean? is it ok to leave?
im very new to ubuntu but loving it. any help is  much! appreciated 
thanks in advance

---

### Post by oldos2er on 2012-04-16
Post moved to its own thread. In the future please start a new thread rather than posting in an old one.

You need to use "sudo" with your command, ala ```
sudo apt-get autoremove
```

---

