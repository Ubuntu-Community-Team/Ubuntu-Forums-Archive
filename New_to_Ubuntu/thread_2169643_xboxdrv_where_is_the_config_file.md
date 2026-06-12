---
title: "xboxdrv where is the config file?"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by hopelessone on 2013-08-22
Hi All,
I have 3 controllers and only 1 appears to be working, i was reading [https://wiki.archlinux.org/index.php/Joystick#Xbox_360_Controllers](https://wiki.archlinux.org/index.php/Joystick#Xbox_360_Controllers)

where you need to enable second controller:
xboxdrv with two controllers
xboxdrv supports a multitude of controllers, but it works only in daemon mode. The simplest way is launch xboxdrv as service in daemon mode:
```
ExecStart = /usr/bin/xboxdrv -D -c /etc/conf.d/xboxdrv
```

And add support of the second controller in config file:
 ```
[xboxdrv]
 silent = true
 next-controller = true
 [xboxdrv-daemon]
 dbus = disabled
```

ExecStart doesnt work and cant find the config file to enable the second controller..

Can someone help me through this?
Thanks,

---

