---
title: "Non-intrusive access to serial CDR status"
date: 2011-02-23
forum: Programming Talk
---

### Post by dsjstc on 2011-02-23
How can I determine whether CDR is high on a serial port, without disturbing any current access to the device?  Any way to tell by looking in /sys or /proc?  I'd prefer to have a non-compiled solution, if possible.

I attempted to use pyserial's serial.getCD().  It works correctly, but the open() call appears to disturb the existing modem connection somehow, even if I don't call close().  I'm not sure why, but I lose the modem link, even though CDR remains high.

Background: I'm sharing two outbound-only modem lines between several virtual machines, and I need to determine whether a modem is in use prior to switching it to the VM that is requesting it.

---

### Post by dsjstc on 2011-03-18
solution: statserial

---

