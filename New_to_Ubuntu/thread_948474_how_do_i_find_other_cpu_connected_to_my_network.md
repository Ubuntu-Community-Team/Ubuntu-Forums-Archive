---
title: "how do i find other cpu connected to my network"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by duquer on 2008-10-15
how do i find other cpu connected to my network so that i may be able to file share?

---

### Post by cmnorton on 2008-10-15
nmap is quite interesting, and easily installable.

sudo apt-get install nmap

---

### Post by LowSky on 2008-10-15
You will need Samba if its a Windows machine

---

### Post by Paul41 on 2008-10-15
If it's just a small home network you can just get the ip address from the computer then use it without needing to search from one computer to the other.

---

### Post by gjoellee on 2008-10-15
it should not be harder then getting your IP and set the IP Address into the web-browser. 

NOTE: It is not dangerous if you have a worry. Only computers connected to your network or maybe only computer connected with cable have access to the router via IP address.

---

### Post by tarps87 on 2008-10-15
If its a windows machine you will need samba ```
sudo apt-get install samba
```
the try ```
smbtree
```
Usually you can just browse the network by going to Places->Network*
*I think it's called network, I will check when I get home

---

### Post by Sarmacid on 2008-10-15
nmap should do the trick. Just run it like this

```
nmap -sP 192.168.0.0-255
```

And change the ip according to your network.

---

### Post by duquer on 2008-10-15
how do you use samba?

---

### Post by Paul41 on 2008-10-15
> **duquer said:**
> how do you use samba?

Here is a good place to start.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

---

### Post by tarps87 on 2008-10-15
In addition to the link you may want to install a program called samba, not to be confused by the samba protocol. It can be fine by searching in 'add program'. This is a small GUI that will allow you to configure samba.
Also try ```
ping *ipAddress*
``` *ipAddress* is the ip address of the PC you are trying to browse, this will check you are correctly connected

---

### Post by jdong on 2008-10-15
Recent versions of Ubuntu and most versions of OS X and some versions of Windows broadcast Zeroconf DNS too, so something like "ping hostname.local" will reveal where computer at hostname is. Avahi/ZeroConf has been a lifesaver on my networks.

---

