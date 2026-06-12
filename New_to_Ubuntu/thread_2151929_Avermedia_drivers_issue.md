---
title: "Avermedia drivers issue"
date: 2013-06-06
forum: New to Ubuntu
---

### Post by Squalo71 on 2013-06-06
Hello, the situation is:
Ubuntu server 12.04 64bit, kernel 3.2.0-45 (if I'm not wrong, I'm not at the machine now).
I installed tvheadend with no problems.
I then installed drivers for Avermedia USB DVB-T tuner (Sky digital key) A867 model.
Everything worked fine.
Then I installed drivers for DVB-S2 TBS5922, and somehow avermedia drivers "broke".
That is what happens:
```
modprobe a867
FATAL: Error inserting a867 (/lib/modules/3.2.0-44-generic/kernel/drivers/media/dvb/a867/a867.ko): Invalid argument

```
and:
```
dmesg|grep dvb
[   13.418792] a867: disagrees about version of symbol dvb_usb_device_init
[   13.418798] a867: Unknown symbol dvb_usb_device_init (err -22)
```
I have tried to go back to kernel 3.2.0-44 (and uninstalled 3.2.0-45), where was installed only avermedia, and it worked.
After installing TBS drivers on 3.2.0-44, again avermedia drivers broke.
How can I resolve the incompatibility between the drivers (or at least repair the avermedia drivers, givin up in installing tbs card)?

Thanks in advance.

EDIT: Confirmed kernel versions.

---

### Post by Squalo71 on 2013-06-07
I solved in repairing avermedia drivers.
Trying to understand what in tbs drivers breaks avermedia ones.
BTW, 106 views and no answer...

---

### Post by Squalo71 on 2014-02-17
Is there anyone who can help me?
I've searched for solutions, but with no luck.

---

