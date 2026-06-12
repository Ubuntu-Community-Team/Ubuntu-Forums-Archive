---
title: "[SOLVED] rdesktop update"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by CyberDean on 2008-09-19
On my Ubuntu server 8.04, I received 1 update, "rdesktop" RDP client for Windows NT/2000 Terminal Server (Size: 142 KB).

What is the purpose for this update on a Ubuntu server?

---

### Post by acidsolution on 2008-09-19
well i think ubuntu shows the update of all the package available either installed or not in your computer.

---

### Post by Kevbert on 2008-09-19
See [[COLOR="Red"]this...[/COLOR]]("http://www.rdesktop.org/")  It's built into the kernel so better safe than sorry to upgrade it.

---

### Post by iaculallad on 2008-09-19
I just got my update a while ago. Below is an excerpt from [Launchpad]("https://launchpad.net/ubuntu/hardy/+source/rdesktop/1.5.0-3+cvs20071006ubuntu0.1").

> Changelog

rdesktop (1.5.0-3+cvs20071006ubuntu0.1) hardy-security; urgency=low

  * SECURITY UPDATE: fix integer overflow in iso.c that could cause denial
    of service or possibly remote code execution
  * SECURITY UPDATE: fix buffer overflow in rdp.c that could cause allow
    remote code execution via redirect requests
  * SECURITY UPDATE: fix integer signedness error that may allow remote
    code execution via heap-based overflow
  * References
    CVE-2008-1801
    CVE-2008-1802
    CVE-2008-1803
    LP: #228193

---

### Post by CyberDean on 2008-09-19
Thanks to all, was not sure what it was about and I try to understand any updates.

Thanks again.

---

