---
title: "Using Ubuntu as a OpenVPN client?"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by riahc3 on 2012-10-01
Im trying to use a Ubuntu box as a OpenVPN client.

It reads correctly the three files needed (after installing the Network Managaer plugin) but fails. Whats wrong? Where can I see some type of log file?

---

### Post by shreepads on 2012-10-01
Look in /var/log/syslog for entries made by Network Manager..

Alternatively, run from the command line to see error messages..

---

### Post by Bufeu on 2012-10-01
If you are trying to install and start OpenVPN, just follow these steps:

[LIST=1]
[*]Install OpenVPN and resolvconf (sudo apt-get   install openvpn resolvconf)
[*]Extract the configuration   files into /etc/openvpn/
[*]Start with sudo /etc/init.d/openvpn start (Or install network-manager-openvpn and use the network manager menu)
[/LIST]

If you are trying to install and configure an OpenVPN-server, check these links:
[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
[http://ubuntuguide.org/wiki/OpenVPN_server](http://ubuntuguide.org/wiki/OpenVPN_server)
[http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)
[https://www.septimius.net/linux-howto-setup-openvpn-server/](https://www.septimius.net/linux-howto-setup-openvpn-server/)

---

