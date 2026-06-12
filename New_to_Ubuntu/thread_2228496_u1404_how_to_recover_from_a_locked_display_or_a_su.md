---
title: "u1404 how to recover from a locked display or a suspend without rebooting"
date: 2014-06-07
forum: New to Ubuntu
---

### Post by nu2u904 on 2014-06-07
Running u1404 live session from key drive, display blanked and locked after a few moments idle.  i  could only recover by rebooting. I subsequently found that the display lock screen was set for 15 minutes. I reset the value to never and the display remained unlocked. If the display is locked or the system suspended how do I unlock the display or recover from a suspend.

nu2904

---

### Post by nu2u904 on 2014-06-22
U14.04 has a  lock screen bug. When locked the screen is blanked and even though the response to a key stroke may be present on the screen it is invisible and no unlock action can be taken. My workaround is to set the lock delay to never. This should work for suspend too.

Users should be warned to set lock to never or they be forced as I was to power down and risk file corruuption instead of initiating a smooth shutdown. Ctrl-Alt-Delete is received but is not sent to the kernal and thus is useless. Is the bug being worked on?

Donald

---

### Post by nu2u904 on 2014-06-22
> **nu2u904 said:**
> Running u1404 live session from key drive, display blanked and locked after a few moments idle.  i  could only recover by rebooting. I subsequently found that the display lock screen was set for 15 minutes. I reset the value to never and the display remained unlocked. If the display is locked or the system suspended how do I unlock the display or recover from a suspend.

nu2904

u14.04 on HP Z400 w/s  After a lock display or suspend screen goes black ; pressing any keys does not display any box to enter my password to unlock screen  and  continue or do  a normal shutdown. Only recourse is to power off. My work around is to set time out to never and lock off. Still cannot recover from suspend.

---

