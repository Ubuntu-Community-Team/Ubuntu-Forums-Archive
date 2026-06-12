---
title: "Scanning wireless network"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by lakersforce on 2008-11-14
How do I scan for wireless networks (access points) and obtain the ip-adresses? (command-line prefered)

---

### Post by kaptengu on 2008-11-14
You can only obtain the IP address from AP:s with very weak security. I think kismet is a good program to scan for AP:s. Install with:
```
sudo apt-get install kismet
```
After that you first need to edit this part:
```
source=sourcetype,interface,name[,initialchannel]
```
in:
```
/etc/kismet/kismet.conf
```

---

### Post by lakersforce on 2008-11-14
> **kaptengu said:**
> 
```
source=sourcetype,interface,name[,initialchannel]
```


What would that be on a Linksys wap54g crap 2?

...or how may I find it?

---

