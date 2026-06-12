---
title: "View network devices?"
date: 2012-10-14
forum: New to Ubuntu
---

### Post by Deniz343 on 2012-10-14
Hi,

I want to see which computers connected to my local network. And how can I connect to a windows computer and access to the files. I want to do all of this with terminal.

Sorry for my bad English. 

Best Regards

---

### Post by Cheesemill on 2012-10-14
You can use nmap to scan for all devices on your network and see which services they are running:
```
nmap 192.168.1.0/24
```
(Obviously change the network declaration if you are not on a 192.168.1.* network).

---

### Post by Deniz343 on 2012-10-15
> **Cheesemill said:**
> You can use nmap to scan for all devices on your network and see which services they are running:
```
nmap 192.168.1.0/24
```
(Obviously change the network declaration if you are not on a 192.168.1.* network).

Thanks for your quick reply. And how about second question ?

Best Regards

---

