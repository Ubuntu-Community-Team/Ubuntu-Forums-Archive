---
title: "Help; no networking"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by ant2ne on 2008-05-18
VMs have networking but host doesn't 

I'm posting this with my VM. My host Ubuntu OS cant even http into my router. I can ping the router though. What setting did I screw up, and how do I fix it?

[http://ubuntuforums.org/showthread.php?p=4990025#post4990025](http://ubuntuforums.org/showthread.php?p=4990025#post4990025)

---

### Post by ant2ne on 2008-05-18
I found the solution here.
[http://ubuntuforums.org/showthread.php?t=148508](http://ubuntuforums.org/showthread.php?t=148508)

```
sudo gedit etc/networks/interfaces
``` added
```
# The primary network interface
iface eth0 inet dhcp
```
GUI tools were not working.

Then restarted.

---

