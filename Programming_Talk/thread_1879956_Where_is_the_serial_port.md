---
title: "Where is the serial port?"
date: 2011-11-12
forum: Programming Talk
---

### Post by jackj on 2011-11-12
Using Ubuntu 10.04

In Windows, you go to device manager to tell you which port the device is connected to.  Where do you go in Ubuntu to get this info?

---

### Post by Bachstelze on 2011-11-12
The serial ports are /dev/ttyS*. Try polling /dev/ttyS0 and see if the device responds (if it doesn't, try /dev/ttyS1, etc.).

---

### Post by jackj on 2011-11-12
Good idea.  I'll do that.  Thanks.

---

