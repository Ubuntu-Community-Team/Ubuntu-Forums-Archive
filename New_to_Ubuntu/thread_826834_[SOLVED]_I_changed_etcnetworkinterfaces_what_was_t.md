---
title: "[SOLVED] I changed /etc/network/interfaces what was the original file?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by hopelessone on 2008-06-12
Hi,

How can i find out what was the original file?

Thanks...

---

### Post by _sphinx_ on 2008-06-12
Mine is this
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
#iface eth1 inet dhcp

iface eth1 inet static
address <ip of eth1>
netmask <subnet mask>

iface eth0 inet dhcp
netmask <subnet mask>
auto eth0

```

Fill the <> with your network configuration

---

### Post by issih on 2008-06-12
Linux typically saves backups as filename~, so try looking for /etc/network/interfaces~. Generally that will only be the last time you saved though, so it may not be enough if you've been making a lot of changes.

Chances are the only entry you had originally was the stanza concerning the interface lo. Which is the loopback interface.

Everything else can be handled by network manager with the interfaces in roaming mode.

---

### Post by aktiwers on 2008-06-12
Mine only has this:
> auto lo
iface lo inet loopback


---

### Post by kpkeerthi on 2008-06-12
> **hopelessone said:**
> Hi,

How can i find out what was the original file?

Thanks...

I'm not in front of ubuntu right now. But you should be able to restore the file by reconfiguring the package that installed the file:

1. Find the package that installed /etc/network/interfaces
```
dpkg --search /etc/network/interfaces
```

2. Reconfigure the <package> printed by the above command
```
sudo dpkg-reconfigure <package>
```

-----------------------------------------------

Another option is to boot with Ubuntu Live CD and then use the content available in /etc/network/interface

---

### Post by hopelessone on 2008-06-12
Thanks Everyone...!!

---

### Post by |Porsche on 2009-03-30
ooops.

---

