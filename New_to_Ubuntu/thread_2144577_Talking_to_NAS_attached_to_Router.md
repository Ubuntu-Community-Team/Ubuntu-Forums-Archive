---
title: "Talking to NAS attached to Router"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by AlanPee on 2013-05-12
Hi,

My first post.

I have Ubuntu 13.04 on a dual boot (Windows 7) laptop which talks wirelessly to my router. Attached to the router is a Synology NAS (and attached to that is a USB hard drive). Windows talks fine to the NAS and its USB drive, but I can't communicate with them with Ubuntu. I'd appreciate help.


Solved : In Nautilus, go to System Tray, choose Files, then Connect to Server and enter smb://synology/

AP

---

### Post by sanderj on 2013-05-13
> **AlanPee said:**
> Hi,

My first post.

I have Ubuntu 13.04 on a dual boot (Windows 7) laptop which talks wirelessly to my router. Attached to the router is a Synology NAS (and attached to that is a USB hard drive). Windows talks fine to the NAS and its USB drive, but I can't communicate with them with Ubuntu. I'd appreciate help.

Is your Ubuntu succesfully connected to the LAN and Internet?

If so: start up Nautilus, en go to Network. Do you see the NAS there?

---

### Post by AlanPee on 2013-05-13
> **sanderj said:**
> Is your Ubuntu succesfully connected to the LAN and Internet?

If so: start up Nautilus, en go to Network. Do you see the NAS there?

Internet connection is fine. Nautilus shows "Windows Network" under "Browse Network". Under that is simply "HOME" which Nautilus cannot access.

AP

---

