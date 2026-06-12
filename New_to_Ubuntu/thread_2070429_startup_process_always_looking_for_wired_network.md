---
title: "startup process always looking for wired network"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by herbert tamayo on 2012-10-12
Hi, I've recently installed ubuntu precise, the installation and update process was done using my wired network connection; after config my wireless card, eveytime i start my pc if the wired connection is not plugged I get I message "looking for network connection..." this process delays up to 4 minutes, then i boot into the X manager and after logon I get network connection through my wireless card. so my question is:

how can I deactivate the looking for process of wired connection everytime I boot ubuntu precise?

regards

---

### Post by NikTh on 2012-10-12
Hi,
Boot in to Ubuntu and then open a terminal with [Ctrl]+[Alt]+[t] keys combo. 
Copy-paste from here bellow command and give the results*****
```
cat /etc/network/interfaces
```

*****Put the results between the brackets [noparse]```
Here
```[/noparse]

Thanks

---

### Post by herbert tamayo on 2012-10-15
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

---

