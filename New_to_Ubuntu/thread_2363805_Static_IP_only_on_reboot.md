---
title: "Static IP only on reboot"
date: 2017-06-14
forum: New to Ubuntu
---

### Post by hvu86 on 2017-06-14
Hey guys

I'm new to the linux world, just installed ubuntu 16.04.2 today. My task is to set a static IP address, I do so by going into vi editor and saving it. After that I restart the network interface using sudo if down -a and sudo if up -a. My problem is when saving the new IP address I run the ifconfig command and it is still set on the old IP address. Now I found a solution which is kind of annoying, I have to reboot the system in order for the static IP to take place. Is that normal? Am I missing a step  or is that the only way for the static IP to take place. #-o

---

### Post by cariboo on 2017-06-14
Which file are you editing to set a static ip address?  If you are running a gui, NetworkManager overrides any static ip address settings, so use it to set an ip address. If you are running the server version, /etc/network/interfaces should look similar to this:

```
cariboo@willy:/etc/network$ cat interfaces
# This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp2s0
iface enp2s0 inet static 
	address	192.168.0.3
	netmask	255.255.255.0
	gateway	192.168.0.1
	dns-nameservers	8.8.8.8 8.8.4.4 
```

---

### Post by HermanAB on 2017-06-15
Log into your router and set the address there, linked to your computer's MAC address.

---

