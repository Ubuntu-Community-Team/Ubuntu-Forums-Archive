---
title: "Log in loop, Ubuntu 18.04.3 LTS"
date: 2020-07-26
forum: New to Ubuntu
---

### Post by juliagreek on 2020-07-26
Hello, 

I have not been using my computer for a couple of weeks, turned it on today and am suddenly stuck in a login loop. 

In the terminal I ran command startx and it tells me:

Fatal server error:
Cannot move old log file "home/username/.local/share/xorg/Xorg.0.log" to "home/username/.local/share/xorg/Xorg.0.log.old"
xinit: giving up
xinit unable to connect to X server: Connection refused
xinit: server error


How do I fix this? I am not very good with the programming of Ubuntu, I have searched the forums and tried different commands I found. If someone can help with my specific problem, I would be very grateful. Thanks!

---

### Post by ActionParsnip on 2020-07-27
Do you have free space on the system? If you drop to root recovery mode and run:
```

df -h

```
It should show you. You can also run:
```

mount -o remount,rw /
apt-get clean
reboot

```
Which may help too

---

### Post by monkeybrain20122 on 2020-07-27
Sounds like a permission issue. [https://bbs.archlinux.org/viewtopic.php?id=205219](https://bbs.archlinux.org/viewtopic.php?id=205219)

---

