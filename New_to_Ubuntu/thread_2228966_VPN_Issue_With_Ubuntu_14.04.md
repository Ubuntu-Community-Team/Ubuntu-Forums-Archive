---
title: "VPN Issue With Ubuntu 14.04"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by wpwend42 on 2014-06-10
I tried to add my VPN (IPredator) and Ubuntu will not see my certificates for IPredator. There are three files, but it only sees one when I try to add it: [IMG]https://pbs.twimg.com/media/BpyscwOCUAEjQAp.png[/IMG]

Here is the pic [https://pbs.twimg.com/media/BpyscwOCUAEjQAp.png](https://pbs.twimg.com/media/BpyscwOCUAEjQAp.png)

There are definitly all three files in my directory. What am I doing wrong?!

---

### Post by Nobody Nessie on 2014-06-18
It happened to me with I installed network-manager-openvpn. I downloaded again the certificate file directly on an USB stick and then put them in the right folder with Nautilus.   You can make a try ?

---

### Post by nerdtron on 2014-06-19
> There are definitly all three files in my directory. What am I doing wrong?!

Check the permissions on the file. I believe because these are certificates there are restrictions on the read/write access to the files themselves.

---

