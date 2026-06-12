---
title: "Ubuntu 13.10 has errors on start up"
date: 2014-01-13
forum: New to Ubuntu
---

### Post by com3 on 2014-01-13
One of which is "System Program Problem Detected" and the other being "Ubuntu has experienced an internal error"

The System Program error lists in details this:

Action: com.ubuntu.apport-gtk-root
Vendor: Apport

Internal error lists (cherry picking what I think is important I can't copy from window)

ExecutablePath
/usr/share/apport/apportcheckresume

Problem Type
KernelOops


What can I do to solve this?

---

### Post by hoopia on 2014-01-13
What did you do to cause this change? Updates and reboot? Any kernel changes?

On boot, see if you can get into a shell and disable Apport for just the session:

[B]sudo service apport stop

[/B]

---

