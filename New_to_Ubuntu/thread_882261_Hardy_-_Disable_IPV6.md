---
title: "Hardy - Disable IPV6?"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Slim Backwater on 2008-08-06
Any idea on how to really really disable IPV6 in Hardy?
I've search and found references to this several year old thread

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

where I've done the usual alias net-pf-10 off and alias ipv6 off to /etc/modprobe.d/aliases but it doesn't seem to work, lsmod | grep ipv6 is still showing that the module is loading, and `ip a` shows that I have inet6 addresses on my interfaces.

My guess is that ipv6 is being loaded during the initrd part of the boot, and I have no idea how to hack that.

FWIW, I don't have a good reason to do this, I just want to.

Thanks,

._.

---

### Post by Oldsoldier2003 on 2008-08-06
> **Slim Backwater said:**
> Any idea on how to really really disable IPV6 in Hardy?
I've search and found references to this several year old thread

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)

where I've done the usual alias mod-pf-10 off and alias ipv6 off to /etc/modprobe.conf/alias but it doesn't seem to work, lsmod | grep ipv6 is still showing that the module is loading, and `ip a` shows that I have inet6 addresses on my interfaces.

FWIW, I don't have a good reason to do this, I just want to.

Thanks,

._.
you also need to edit /etc/modprobe.d/blacklist 

add this line:
```
blacklist ipv6
```

---

### Post by drs305 on 2008-08-06
To late, follow Oldsoldier2003

---

