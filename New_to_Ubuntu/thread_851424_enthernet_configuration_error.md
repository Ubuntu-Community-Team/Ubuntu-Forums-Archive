---
title: "enthernet configuration error"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Matt26 on 2008-07-06
i just replaced my motherboard and everything seems to have loaded fine when i start ubuntu (v8.04) now, except when i go into System/Administration/Network Tools, choose my network adapter (which comes up as eth1 now- i thought i always used to be eth0) and click on the Configure button i get the following error message:

The interface does not exist

Check that it is correctly typed and that it is correctly supported by your system.

any ideas on how i can resolve this issue?  am i correct that the interface should be eth0 instead of eth1?

thanks.

---

### Post by quantumstitch on 2008-07-06
What's the output of:
```

more /etc/network/interfaces

```

---

### Post by Matt26 on 2008-07-06
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.158
netmask 255.255.255.0
gateway 192.168.0.1





auto eth0

iface eth1 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1

---

### Post by Matt26 on 2008-07-07
after reviewing a sample interfaces file i have modified my interfaces file as follows:

auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1


i rebooted my machine but the interface is still showing as eth1 under Network Tools and when i try to view the configuration of the interface it is still giving me the error message 'the interface does not exist...'

also, when i look at the Network option i see that my Ethernet connection has the Roaming option ticked- even though i have a static IP config in the interfaces file...

any ideas?

---

### Post by Matt26 on 2008-07-09
how do i edit the information that is provided when using the command **ifconfig -a**?

my ethernet adapter is coming up as eth1 and it should be eth0- if i try to restart my networking services using [B]sudo /etc/init.d/networking restart
[/B] i get the following error message:
[B] * Reconfiguring network interfaces...                                          eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
[/B]

my /etc/network/interfaces file is setup as:
auto lo
iface lo inet loopback


auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

thanks.

---

### Post by cariboo on 2008-07-09
What happens when you change the interface to eth1?

---

### Post by bab1 on 2008-07-09
read```
man interfaces
```

This explains how to to reconfigure the NIC (eth*[COLOR="Red"]n[/COLOR]*)
Including how to disable (down) and enable (up) the interface

---

### Post by Matt26 on 2008-07-09
when i run ifconfig my ethernet adapter shows up as eth1- is there a way i can update or change this entry to be eth0?

---

### Post by Matt26 on 2008-07-11
i just ran the ubuntu 8.04 live cd and went to Network Tools under System/Administration and this time my ehternet adapter shows up as eth0- instead of eth1 ... i still can't into the Configure button though- same error message as below... anyone know why the difference from eth1 to eth0 when using the live cd?

thanks.

---

### Post by plucky on 2008-07-11
Try this ```
cat /etc/udev/rules.d/70-persistent-net.rules
```
will show your ethernet interfaces associated with mac hardware addresses.

You can either edit the file to reflect the new mac address for eth0 or delete it and let the system create a new one.


Good Luck

---

### Post by Matt26 on 2008-07-12
> **plucky said:**
> Try this ```
cat /etc/udev/rules.d/70-persistent-net.rules
```
will show your ethernet interfaces associated with mac hardware addresses.

You can either edit the file to reflect the new mac address for eth0 or delete it and let the system create a new one.


Good Luck

thanks, that allowed me to get my interfaces matched up and configured properly again!  i now have the correct static IP setup for my ethernet adapter, eth0 showing up when i run ifconfig -a and under network tools- but i still can't sue the Configure button- still says the interface doesn't exist... could this still be a problem with the /etc/udev/rules.d/70-persistent-net.rules file?

---

