---
title: "Device Mount over IP"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Androssi on 2008-06-11
I set up the OS so I could mount a device over a LAN using:

$ <device name>-mount

The IP address of the device has a long lease, but cannot be set to static.  The IP address has changed.

Is there an easy way to change the IP address that Ubuntu (8.04) looks to when I type:

$ <device name>-mount

Thank you.

---

### Post by cariboo on 2008-06-11
How are you mounting the device? Samba NFS or some other protocol?

Why not add the ip address to the /etc/hosts file and then when the ip address changes all you have to do is change the ip address eg:

```
127.0.0.1	localhost 
192.168.1.200	willy
192.168.1.1 	router
127.0.0.1	intrepid
```

In this example when I want to connect to 192.169.1.200 i just enter the name associated to the  ip address eg:

```
http://willy
ftp://willy
smbclient -L willy -U user -P passwrod
```

Jim

---

