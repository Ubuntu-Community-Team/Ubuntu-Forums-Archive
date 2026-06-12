---
title: "Problem with the system settings in Ubuntu 12.04"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by SenK on 2012-05-10
Hi,

I am new user of Ubuntu OS. I had installed Ubuntu 12.04. Unfortunately 'System Settings' option got disappeared. If I click on the 'System Settings' at the right corner (above) of the desktop, it does not open. That's why I installed 'system settings' from the ubuntu software center. But it's KDE based. Also the screen shot is completely different from the default 'system settings'. I want to get back the default system settings option. Pls help me.

---

### Post by 3rdalbum on 2012-05-10
It's called "gnome-control-center". If you have removed it by mistake, you can install it again from Ubuntu Software Center or type this into the terminal:

```
sudo apt-get install gnome-control-center
```

Also, everything in Gnome Control Center can be launched from the Dash anyway regardless of whether GCC is installed or not.

---

### Post by SenK on 2012-05-10
Many thanks to you. It worked. Thanks once again...

---

### Post by 3rdalbum on 2012-05-11
Glad it helped!

---

