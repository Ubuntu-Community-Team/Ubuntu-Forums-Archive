---
title: "Shell script change ip"
date: 2010-01-14
forum: Programming Talk
---

### Post by slax2009 on 2010-01-14
Hi
 
I have trouble with this script. I try to change ip (network/interfaces)
 
> # An example ethernet card setup: (broadcast and gateway are optional)
#
# auto eth0
# iface eth0 inet static
# address 192.168.1.25
# network 192.168.1.0
# netmask 255.255.255.0
# broadcast 192.168.1.255
# gateway 192.168.1.1
```

#!/bin/sh
echo "Configure your network interfaces"
echo "Please enter your old IP address: (eg 192.168.1.25)"
read NIC_OLD_IP
echo "Enter new IP address:"
read NIC_NEW_IP
echo "Please enter your old gateway address: (eg 192.168.1.1)"
read NIC_OLD_GATE
echo "Enter new gateway address:"
read NIC_NEW_GATE
echo "Please enter your old network address: (eg 192.168.1.0)"
read NIC_OLD_NET
echo "Enter new network address:"
read NIC_NEW_NET
echo "Please enter your old broadcast address: (eg 192.168.1.255)"
read NIC_OLD_BROADCAST
echo "Enter new network address:"
read NIC_NEW_BROADCAST
 
 
 
#
echo
echo Is this information correct? [Y/N] Default is [Y]
read ANS
case $ANS in
YES|[Yy]es|[Yy]|"")
    echo OK, we will continue...
    ;;
NO|[Nn]o|[Nn])
    echo Lets start over...
    sleep 3;clear;./ipchange;exit 
    ;;
*)
esac
#
cp -p /etc/network/interfaces /etc/network/interfaces.orig
sed -e s/${NIC_OLD_IP}/${NIC_NEW_IP}/g /etc/network/interfaces
sed -e s/${NIC_OLD_GATE}/${NIC_NEW_GATE}/g /etc/network/interfaces
sed -e s/${NIC_OLD_NET}/${NIC_NEW_NET}/g /etc/network/interfaces
sed -e s/${NIC_OLD_BROADCAST}/${NIC_NEW_BROADCAST}/g /etc/network/interfaces
 
 
 
# 
sleep 2 
echo 
echo Done....
fi 
host#

```Is there other way to just enter (NIC_NEW_IP), and will auto enter the gateway, broadcast and network address.
 
Like just enter: 192.168.1.25, and it assign to $xxx
 
adresss 192.168.1.25 
network xxx.xxx.xxx.0
broadcast xxx.xxx.xxx.255
gateway xxx.xxx.xxx.1 
 
where $xxx is 192.168.1
 
Thanks in advanced

---

### Post by lavinog on 2010-01-15
```

NIC_IP_PREFIX=$(echo "$NIC_NEW_IP"|cut -d '.' -f 1-3)
NIC_NEW_GATE="${NIC_IP_PREFIX}.1"
NIC_NEW_NET="${NIC_IP_PREFIX}.0"
NIC_NEW_BROADCAST="${NIC_IP_PREFIX}.255"

```

---

### Post by slakkie on 2010-01-15
> **lavinog said:**
> ```

NIC_IP_PREFIX=$(echo "$NIC_NEW_IP"|cut -d '.' -f 1-3)
NIC_NEW_GATE="${NIC_IP_PREFIX}.1"
NIC_NEW_NET="${NIC_IP_PREFIX}.0"
NIC_NEW_BROADCAST="${NIC_IP_PREFIX}.255"

```

Yes, that works only for /24 networks. What if I have a /28?

Perhaps use ipcalc to determine the network/broadcast/gateway address:

sudo aptitude install ipcalc

ipcalc 192.168.0.0/28 

and parse that output?

---

