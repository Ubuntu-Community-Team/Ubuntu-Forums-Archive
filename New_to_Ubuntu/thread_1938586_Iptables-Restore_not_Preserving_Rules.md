---
title: "Iptables-Restore not Preserving Rules"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by WinterStove on 2012-03-09
Iptables-restore does not retain iptables rules after reboot (10.04).

Used root terminal for following:

Put firewall in bash shell and ran shell in terminal. 
Gave /root rwx permissions.
Used iptables-save to create /root/ipt.save.
Gave ipt.save rwx permissions.
Ran: cat /root/ipt.save | iptables-restore

If I flush firewall rules, running iptables-restore reinstalls rules.
But after reboot, iptables rules are not preserved.
My understanding is that iptables-restore loads rules into kernel, and doesn't need to be rerun after rebooting.

Anybody have any ideas>

---

### Post by Toz on 2012-03-10
Hello and welcome to the forums.

> **WinterStove said:**
> My understanding is that iptables-restore loads rules into kernel, and doesn't need to be rerun after rebooting.
Actually, iptables-restore needs to be run after reboot (it is not persistent). 

One option, is to add your command to the end of **/etc/rc.local** above the *exit 0* command so that they are loaded automatically on start. 

A better option is to load them before the network interface comes up. I believe the proper location for this file would be /**etc/network/if-pre-up.d**.

---

### Post by Doug S on 2012-03-10
you can also add a script execution via the pre-up directive added directly to /etc/network/interfaces.
see the method 3 segment here: [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)
After seeing the above referenced thread, I changed from the rc method, my interfaces file is below:```
# Smythies 2011.11.15 Can I execute my firewall script from here
#          instead of /etc/rc2.d? Add it.
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
[COLOR=red]pre-up /home/doug/init/doug_firewall[/COLOR]
# The primary interface (d-link PCI card)
auto eth1
iface eth1 inet dhcp
# Local network interface (uses built in ethernet port)
auto eth0
iface eth0 inet static
  address 192.168.111.1
  network 192.168.111.0
  netmask 255.255.255.0
  broadcast 192.168.111.255
```

---

### Post by WinterStove on 2012-03-11
Thanks Toz and Doug for showing me how to set things up!

---

