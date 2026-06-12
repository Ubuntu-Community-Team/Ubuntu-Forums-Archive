---
title: "[SOLVED] Local SubDomains Question"
date: 2007-11-13
forum: Philippine Team
---

### Post by md5hash on 2007-11-13
how can i make my local sub domains accessible to other computer in my network?

reference: [https://help.ubuntu.com/community/LocalhostSubdomain](https://help.ubuntu.com/community/LocalhostSubdomain)

---

### Post by pinoyskull on 2007-11-15
> **md5hash said:**
> how can i make my local sub domains accessible to other computer in my network?

reference: [https://help.ubuntu.com/community/LocalhostSubdomain](https://help.ubuntu.com/community/LocalhostSubdomain)

put it in /etc/hosts if you're using linux
put it in c:/windows/system32/drivers/etc/hosts

format is:
ipaddress [space] subdomain name
192.168.0.23   subdomain.example.com

---

### Post by md5hash on 2007-11-16
do i still need to add a dns record for each subdomains?

thanks, Mabuhay..

---

### Post by pinoyskull on 2007-11-16
I dont think its needed since it is only for local access

---

### Post by md5hash on 2007-11-16
Socket error sya pre pag sa ibang pc sa network eh..

---

### Post by md5hash on 2007-11-16
SOLVED :guitar:

---

