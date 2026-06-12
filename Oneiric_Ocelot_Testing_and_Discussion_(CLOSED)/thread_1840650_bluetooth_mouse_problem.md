---
title: "bluetooth mouse problem"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xurwxj on 2011-09-07
when in 11.04,my bluetooth mouse works.failed in 11.10 after upgrade,syslog get following errors:

Sep  8 11:18:54 victor-ThinkPad-T500 bluetoothd[1990]: Refusing input device connect: No such file or directory (2)
Sep  8 11:19:34 victor-ThinkPad-T500 bluetoothd[1990]: HUP or ERR on socket
Sep  8 11:19:34 victor-ThinkPad-T500 bluetoothd[1990]: 00:60:D1:00:2A:06: error updating services: Connection timed out (110)
Sep  8 11:19:36 victor-ThinkPad-T500 bluetoothd[1990]: Refusing input device connect: No such file or directory (2)
Sep  8 11:20:17 victor-ThinkPad-T500 bluetoothd[1990]: 00:60:D1:00:2A:06: error updating services: Connection refused (111)
Sep  8 11:20:17 victor-ThinkPad-T500 bluetoothd[1990]: HUP or ERR on socket

how to fix it?
thanks a lot.

---

### Post by rapiertg on 2011-09-08
I just bought a new bt mouse and it is working great. I just needed to pair it. I was impressed and surprised it went so smooth.

Have you tried deleting mouse and pairing it again?

---

### Post by xurwxj on 2011-09-23
how to delete bt mouse?i can not find any message about the mouse except above errors from log.

---

### Post by rapiertg on 2011-09-23
Click bluetooth icon, open settings, click mouse and a minus that is below. Than click plus and try to add it again.

---

