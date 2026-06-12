---
title: "Why are Ubuntu and Zenwalk so easy to ping?"
date: 2008-11-11
forum: Other OS Talk
---

### Post by Antman on 2008-11-11
I have a question:
With Ubuntu and Zenwalk, as soon as I install them on my machines they can ping each other via their computer names (e.g: *computername.local*) without me needing to know their IP addresses (DHCP assigned). 
However, distros like Fedora, sidux, etc., do not have that functionality out-of-the-box. 

So what services/packages are installed in Ubuntu/Zenwalk that enables them to do it so easily? Is that Avahi or something else?

Thanks,

Ant

---

### Post by Antman on 2008-11-11
Hmmm... looks like I may be able to add this functionality to sidux and or Debian Sid with:```
apt-get install avahi-daemon avahi-discover libnss-mdns
```
Gotta test this out.:guitar:

---

