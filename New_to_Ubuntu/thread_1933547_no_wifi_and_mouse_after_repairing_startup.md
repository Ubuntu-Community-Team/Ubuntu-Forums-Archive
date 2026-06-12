---
title: "no wifi and mouse after repairing startup"
date: 2012-02-29
forum: New to Ubuntu
---

### Post by zabih on 2012-02-29
I have 3 problems after fixing my startup problem which was caused by start up Manager on Ubuntu 11.10

Mouse doesn't work on Ubuntu
can't connext to wifi

Because of startup manager problem once I fixed it, in my windows 7 I cannot see the texts onbuttons for example ok or accept or no and many more  when running a program and even on shutting Down menu. I uninstalled my graphics, reinstalled after reboot still no luck.

---

### Post by cariboo on 2012-03-01
Are you mouse and wifi device detected on boot, check:

```
lsusb
```

for the mouse, it should look something like this:

> Bus 002 Device 003: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0

depending on the mouse your output of the above command may look different, and for you wireless device:

```
lshw -C network
```

should list your network devices.

---

