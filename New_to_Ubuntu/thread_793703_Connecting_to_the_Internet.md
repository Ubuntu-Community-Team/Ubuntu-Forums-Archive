---
title: "Connecting to the Internet"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-14
Was able to finally connect my serial dialup after changing permisssions in the etc/ppp/chap-secrets file, but I notice the little dialing window still says "Connecting" and the Networking icon says "No Network Connection". Is there some other configuration I need to make? I've attached a jpeg of the Log screen. Thanks.

---

### Post by Michael.Godawski on 2008-05-14
First here is a general site about dial-up configuration:

[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Can you please post the result of the terminal commands:

```
sudo lshw -C network
iwconfig
```

---

### Post by jacatone on 2008-05-14
Here it is:

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:d0:09:74:73:b2
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
jacatone@eMax:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

---

