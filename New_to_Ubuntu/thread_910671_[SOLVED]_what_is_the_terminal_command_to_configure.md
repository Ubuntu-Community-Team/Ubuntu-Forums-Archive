---
title: "[SOLVED] what is the terminal command to configure the nvidia driver?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Zieg30CT on 2008-09-04
I used EnvyNG to take care of my video driver but I need the command to configure it so I can get some compiz stuff working. Could someone supply the command?

---

### Post by Separ on 2008-09-04
try
```
nvidia-settings
```
or edit the /etc/X11/xorg.conf file (make a backup first.)

---

### Post by SuperSonic4 on 2008-09-04
```
gksudo nvidia-settings
``` since you'll probably need to be root to do some things (like screen config)

---

### Post by Zieg30CT on 2008-09-04
thank you :popcorn:

---

