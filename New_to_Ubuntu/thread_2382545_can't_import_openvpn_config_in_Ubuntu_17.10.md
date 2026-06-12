---
title: "can't import openvpn config in Ubuntu 17.10"
date: 2018-01-14
forum: New to Ubuntu
---

### Post by borg101 on 2018-01-14
When I go to Network Connections and click add VPN, the only options I have are pptp and import from a file.  OpenVPN is installed.  I even uninstalled and reinstalled it.  If I choose an ovpn config it tells me it can't read the information.  I previously had no issues doing this with Ubuntu 16.04, 16.10, nor 17.04.  Any ideas on what the issue may be?

---

### Post by joebeasley on 2018-01-16
Install network-manager-openvpn.

---

### Post by borg101 on 2018-01-19
> **joebeasley said:**
> Install network-manager-openvpn.
That was the first thing I checked.  Just triple checked it....already installed.  All I see is PPTP and import file.

---

### Post by roger_1960 on 2018-01-21
I think you may need:

> sudo apt-get install network-manager-openvpn-gnome

---

