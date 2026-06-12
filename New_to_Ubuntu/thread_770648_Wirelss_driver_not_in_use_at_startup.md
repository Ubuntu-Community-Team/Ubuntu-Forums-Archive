---
title: "Wirelss driver not in use at startup"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by mogwins on 2008-04-27
Thanks to help on this forum I've got my Broadcom wireless device working in Ubuntu (8.03). I now have another issue: When I restart Ubuntu, the wirelss is "not in use." If I go to the Hardware Drivers GUI, it states Broadcom B43 Wireless Device is enabled, but not in use. If I disable and re-enable it, everything's fine, however, I'm guessing there's a way around this?

Thanks in advance, M.

---

### Post by furtypajohn on 2011-07-01
Give this a try:

When you log in and your wireless isn't working try running the following command:

```
sudo modprobe b43
```If that works then you'll want to add it to your /etc/modules file (all you have to do is add b43 to the bottom of the file, then reboot) so that it is automatically added when you boot.

---

