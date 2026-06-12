---
title: "Ubuntu 8.10 installation problem"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by J03y on 2008-11-27
Hello, yesterday at night I upgraded from 8.04 to 8.10 and the computer restarted and everything, but then at the login screen when I typed the user name and the password the screen suddenly became all blank and couldn't see and do anything. Then I restarted the computer again and since I had made a dual boot it showed an option to enter recovery mode and then I followed all the steps but it didn't work. Is there anyway to fix this?

---

### Post by Peter09 on 2008-11-27
Boot into recovery mode and select 'xfix' from the menu, this may resolve.

If not try typing ```
startx
``` at the command prompt.

Can you post the output of the shell command to confirm the driver that you are using.
```
lshw -C display
```

---

### Post by bodhi.zazen on 2008-11-27
If that fails, what videocard do you have. 

@Peter09 : yes that information is helpful, but it may be easier to work in windows (ie beginners will find it difficult to post the output without X or interpret those commands).

---

### Post by mapes12 on 2008-11-27
If you can boot the system in recovery mode and access a Terminal try ```
sudo apt-get install ubuntu-desktop
``` which should reinstall the desktop environment and all dependencies.

---

