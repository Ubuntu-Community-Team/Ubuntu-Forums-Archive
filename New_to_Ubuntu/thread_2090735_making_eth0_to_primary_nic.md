---
title: "making eth0 to primary nic"
date: 2012-12-03
forum: New to Ubuntu
---

### Post by kanjah on 2012-12-03
hi there, ave installed ubuntu 12 server, with 2 NIC cards, choose eth0 to be primary during installation, for squid3 proxy. Nw internet only works with eth1 not eth0 which is the primary. due to this i cant configure the iptables and lan. running  sudo nano /etc/network/interfaces
shows 

#the primary network interface

auto eth0 inet static
       address 81.25.128.x
       netmask 255.255.255.x
       gateway 81.25.128.x
       #dns -xoptions are implemented by the resolvconf package,
       dns-nameservers 91.x.x.x 91.x.x.x

iface eth1 inet static
       address 81.25.128.x
       netmask 255.255.255.x
       brodcast 81.25.128.x


any advice?
thanks

---

### Post by Cheesehead on 2012-12-03
Check your persistent-net.rules file under /etc/udev/rules.d/

Both NICs should be there - the rule tells which MAC address should be which eth#. Perhaps they've been switched? If so, fix them and reboot to see if that fixes the problem.

If udev rules are correct but you still have the problem, next look at the boot log using [FONT="Courier New"]dmesg | grep eth[/FONT] . Look for mesages about interfaces coming up, going down, or getting renamed. Post them here.

---

### Post by kanjah on 2012-12-03
thanks for the reply, run /etc/udev/rules.d/ and this is the output

#PCI device 0x14e4:/sys/devices/pci0000:00/0000:1c.2/0000:02:00.0(tg3)
SUBSYSTEM=="net", ACTION=="add",DRIVERS=="?*", ATTR{address}=="d0:67:e5:23:88:0f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

#PCI device 0x1106:/sys/devices/pci0000:00/0000:1e.0/0000:03:01.0(via-rhine)
SUBSYSTEM=="net", ACTION=="add",DRIVERS=="?*", ATTR{address}=="14:d6:4d:54:4d:8c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

i dont understand these, eth0 is inbuilt, whilst eth1 is pci

---

### Post by kanjah on 2012-12-04
hi there, ave installed ubuntu 12 server, with 2 NIC cards, choose eth0 to be primary during installation, for squid3 proxy. Nw internet only works with eth1 not eth0 which is the primary. due to this i cant configure the iptables and lan. running sudo nano /etc/network/interfaces
shows 

#the primary network interface

auto eth0 inet static
address 81.25.128.x
netmask 255.255.255.x
gateway 81.25.128.x
#dns -xoptions are implemented by the resolvconf package,
dns-nameservers 91.x.x.x 91.x.x.x

iface eth1 inet static
address 81.25.128.x
netmask 255.255.255.x
brodcast 81.25.128.x

and running /etc/udev/rules.d/

#PCI device 0x14e4:/sys/devices/pci0000:00/0000:1c.2/0000:02:00.0(tg3)
SUBSYSTEM=="net", ACTION=="add",DRIVERS=="?*", ATTR{address}=="d0:67:e5:23:88:0f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

#PCI device 0x1106:/sys/devices/pci0000:00/0000:1e.0/0000:03:01.0(via-rhine)
SUBSYSTEM=="net", ACTION=="add",DRIVERS=="?*", ATTR{address}=="14:d6:4d:54:4d:8c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

anyone please help me....

---

### Post by ahallubuntu on 2012-12-04
You're close.  Edit the file /etc/udev/rules.d/70-persistent-net.rules and swap eth0 and eth1 and reboot.  That will swap eth0 and eth1.  Change the interfaces file too, of course.

---

### Post by kanjah on 2012-12-04
thank you, it works

---

### Post by kanjah on 2012-12-04
thank you

---

### Post by coffeecat on 2012-12-05
Threads merged. Please do not create duplicate threads. This dilutes community effort.

---

