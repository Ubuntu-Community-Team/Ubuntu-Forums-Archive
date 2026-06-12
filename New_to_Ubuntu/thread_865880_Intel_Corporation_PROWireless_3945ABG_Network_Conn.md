---
title: "Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by sameer.india on 2008-07-21
Can someone tell me where to find the drivers

---

### Post by JagDragon on 2008-07-21
The drivers are in the kernel already. Open a Terminal (Applications -> Accessories -> Terminal) and type```
sudo modprobe iwl3945
```

If that works, enable them at startup by opening the modules file ```
sudo gedit /etc/modules
``` and adding the line```
iwl3945
```

---

### Post by Graeme2804 on 2009-04-13
Hi,

I can't get my wireless to work and I have this wireless card.

modprobe iwl3945 didn't return anything in the terminal and my wireless does not work after adding that to the file and rebooting.

any further suggestions?

see [http://ubuntuforums.org/showthread.php?p=7042414#post7042414](http://ubuntuforums.org/showthread.php?p=7042414#post7042414) for my full story

---

### Post by Graeme2804 on 2009-04-17
Hi,

Can anyone assist me with this problem please?

---

### Post by Graeme2804 on 2009-04-28
Hi,

I have now upgraded to Ubuntu 9.04 and it says Wireless Disabled when I right click network connections and doesn't give me the option to enable.

Any ideas on what I can do to resolve this?  I really don't want to do a clean install.

---

### Post by Sealbhach on 2009-04-28
Try the steps here:

[http://geekygospel.wordpress.com/2008/10/30/getting-wifi-to-work-on-intel-prowireless-3945abg-in-ubuntu-hardy/](http://geekygospel.wordpress.com/2008/10/30/getting-wifi-to-work-on-intel-prowireless-3945abg-in-ubuntu-hardy/)

Or you could try using wicd.

[https://bugs.launchpad.net/ubuntu/+bug/223304](https://bugs.launchpad.net/ubuntu/+bug/223304)

If you install wicd, it uninstall network Manager.

.

---

