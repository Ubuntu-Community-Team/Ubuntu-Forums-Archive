---
title: "Problems with desktop on first login after boot/reboot"
date: 2012-09-19
forum: New to Ubuntu
---

### Post by JamieKG on 2012-09-19
Hi When I log on into Ubuntu the desktop can become unresponsive lets say I open a Nautilus window I cant move it or make it maximize or minimize if I open another one some times I can only click the bar to raise one of the windows but still not move the dock can also become unresponsive

this only happens on the first login of a boot as soon as I log out then back in every thing is perfect

Thanks JamieKG

---

### Post by daslinkard on 2012-09-21
Try this sudo command and then reboot the machine and see if resetting unity fixes the issue.

```
unity --reset
```

Hopefully this fixes the issue.

---

