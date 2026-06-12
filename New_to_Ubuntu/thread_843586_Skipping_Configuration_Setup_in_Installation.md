---
title: "Skipping Configuration Setup in Installation"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by shoaibi on 2008-06-28
I have ubuntu 8.04LTS server on a machine. I installed ubuntu-dekstop on it, sonme packages like wvdial, bluetooth etc took years while showing:
"Setting up ______"
so i just skipped them by Ctrl+C.

okay, its dpkg --configure -a,
but now my system is stuck at:
udev active, devices will be created in /dev/.static/dev/
 * Starting bluetooth 

again, is there a method i can uninstall bluetooth and continue with rest of reconfigurations?

---

### Post by brian_p on 2008-06-28
> **shoaibi said:**
> I have ubuntu 8.04LTS server on a machine. I installed ubuntu-dekstop on it, sonme packages like wvdial, bluetooth etc took years while showing:
"Setting up ______"
so i just skipped them by Ctrl+C.

okay, its dpkg --configure -a,
but now my system is stuck at:
udev active, devices will be created in /dev/.static/dev/
 * Starting bluetooth 

again, is there a method i can uninstall bluetooth and continue with rest of reconfigurations?

Purge them and reinstall

```
apt-get remove --purge <package>

```
Or

```
dpkg-reconfigure <package>
```

works with some packages.

---

### Post by shoaibi on 2008-06-28
here is what i get:
```

root@madmin:~# dpkg --configure -a
Setting up bluez-utils (3.26-0ubuntu6) ...
Creating device nodes ...
udev active, devices will be created in /dev/.static/dev/
 * Starting bluetooth                                                           
[1]+  Stopped                 dpkg --configure -a
root@madmin:~# rm /var/lib/dpkg/lock 
root@madmin:~# apt-get remove --purge bluez-utils
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@madmin:~# dpkg-reconfigure bluez-utils
/usr/sbin/dpkg-reconfigure: bluez-utils is broken or not fully installed

```

---

