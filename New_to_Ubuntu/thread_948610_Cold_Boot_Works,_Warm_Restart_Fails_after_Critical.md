---
title: "Cold Boot Works, Warm Restart Fails after Critical Updates"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by lawtech on 2008-10-15
System has been working fine. Just took today's updates, mostly about dbus. Now system will not warm reboot. It hangs right after shutting down the firewall. A power off, power on, cold reboot works. What's going on? Any ideas how to get it restarting again, or even what to check?

$ cat /etc/issue
Ubuntu 8.04.1 \n \l

$ uname -a
Linux black-host 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

---

### Post by melrokz on 2008-10-15
try this:

sudo apt-get clean
sudo apt-get check

---

### Post by melrokz on 2008-10-15
try this:

```
sudo apt-get clean
sudo apt-get check
```

---

### Post by lawtech on 2008-10-15
> **melrokz said:**
> try this:

sudo apt-get clean
sudo apt-get check

$ sudo -s
# sudo apt-get clean
# apt-get clean
# apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
#

---

### Post by lawtech on 2008-10-20
Reinstalled 8.04.1. Took all updates. Everything works now. (Deep fsck found no disk problems.)

---

