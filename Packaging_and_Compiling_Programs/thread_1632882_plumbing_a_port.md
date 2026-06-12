---
title: "plumbing a port"
date: 2010-11-28
forum: Packaging and Compiling Programs
---

### Post by qmqmqm on 2010-11-28
Hi

I often hear the phrase "plumbing a port". I searched on Google but couldn't find what it means. Could someone explain what it means?

Thanks.

Tom

---

### Post by duanedesign on 2010-12-02
I've heard this used In Solaris circles.

An interface must be plumbed before it can pass traffic between the system and the network. The first step in bringing up an interface is "plumbing" the interface. This sets up the streams needed for TCP/IP to use the device.

```
ifconfig elxl0 plumb
```

This sets up the streams needed for TCP/IP to use the device but does not configure the stack. You would then need to configure the TCP/IP stack. Adding the IP address, netmask, and telling the device it is up.

```
ifconfig elxl0 192.168.1.132 netmask 255.255.255.0 up
```

hope this helps,
duanedesign

---

### Post by qmqmqm on 2010-12-05
Thank you Duanedesign!

---

