---
title: "is it possible to send the data packets wirelessly using static ip"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by kavi123 on 2012-07-23
hi,

      I have a doubt like, are there any ways to send the data packets using static IP, after the successful association of client and access point.


Thanks

---

### Post by Ms. Daisy on 2012-07-24
I can't see why it wouldn't work. Are you having problems?

---

### Post by Grenage on 2012-07-24
Once the connection is established, it should be (ostensibly) the same as using a wired connection.

---

### Post by kavi123 on 2012-07-25
yeah, u are correct , but instead of connecting automatically i have established the connection with the access point through user space program, i mean without the intervention of driver, since driver did not involve in establishing the connection, it is not allowing to ping the access point also.

since whether the connection is established either by the support of driver or user space program it makes no difference at the access point side.

since access point still shows the station's MAC in the associated client list, which is achieved through user space program,,,,

but after this connection establishment if i ping using static ip it is giving 
connect: network host unreachable...

kindly help me


Thanks

---

### Post by HiImTye on 2012-07-25
have the host skip the DHCP server and manually assign itself an IP

---

### Post by kavi123 on 2012-07-25
yeah wanted to skip the DHCP part, since driver is not involved in the connection establishment hence, i will have to prepare the DHCP request to get the dynamic IP assigned, so not sending any DHCP request.

Hence wanted to skip this part, after establishing the connection i'm assigning and pinging the access point, to test the connection, but it is not happening..

---

### Post by kavi123 on 2012-07-25
If the connection is established through the driver then even static IP works well, since I have used user space program to establish connection with the access point, hence ping is not possible using static IP address.

As soon as established connection if i ping it is giving
From 192.168.xx.xx icmp_seq=50 Destination Host Unreachable
From 192.168.xx.xx icmp_seq=51 Destination Host Unreachable

192.168.xx.xx is the static ip assigned to the interface.

---

