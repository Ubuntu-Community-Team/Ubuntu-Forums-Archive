---
title: "Terminal wont open because i change usermod -s /usr/bin/"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by Distlingur on 2013-03-07
Hi hi i was messing arround withouth thanking and changed my  #usermod -s /usr/bin/  to this so everytime i start Terminal now i get this error message

There was an error creating the child process for this terminal
failed to execute child process "/usr/bin/"
any suggestions what i can do to fix it ?

p.s. i have no idea why i did that haha

---

### Post by Cheesemill on 2013-03-07
Boot into recovery mode and drop to a root shell, then remount your root filesystem in rw mode with...
```
mount -o rw,remount /
```
You can then change your shell back again by doing...
```
usermod -s /bin/bash username
```
replacing username with your actual username.
Reboot and all should be OK again.

---

