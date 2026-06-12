---
title: "Wired network issues"
date: 2016-11-02
forum: New to Ubuntu
---

### Post by dpikerrd on 2016-11-02
I have been scouring the forums for some assistance with setting up wired networking on a fresh Ubuntu 16.04 LTS install. I have set a static IP address because I was not getting anything with DHCP. Connection Information all looks good, and Network Manager says it is connected. But, I have no internet and I can not even ping the gateway (router). I am pretty new to Ubuntu, but I know networking. I see where members post results from commands, but I have no idea how they do it if they have no network in Ubuntu.
Thanks in advance for any assitance.

---

### Post by Odyssey1942 on 2016-11-02
Second computer

---

### Post by cariboo on 2016-11-02
How did you set a static ip address? If you are doing it from /etc/network/interfaces, which should look something like this:

```
cariboo@willy:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet static 
	address	192.168.0.205
	netmask	255.255.255.0
	gateway	192.168.0.1
	dns-nameservers	8.8.8.8 8.8.4.4 
```

Then remove/disable NetworkManager.

If using NetworkManager, make sure Method is set to Manual, and make sure the ip address doesn't conflict with other systems on the network.

---

