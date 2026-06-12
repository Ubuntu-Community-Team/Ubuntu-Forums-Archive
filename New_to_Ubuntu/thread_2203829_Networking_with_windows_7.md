---
title: "Networking with windows 7"
date: 2014-02-05
forum: New to Ubuntu
---

### Post by mr best buy on 2014-02-05
When I click on network from windows I cannot see my Ubunutu Machine. When I click on networking in Ubunutu I cannot see my windows machine. Is there a simple probram that will allow this?  They are connected through a router

---

### Post by Ubi_one_2014 on 2014-02-05
are both machines in 'WORKGROUP'

---

### Post by vitz_3 on 2014-02-05
It might be a simple network problem and not a software thing. Are both computers on the same subnet? Perhaps the router is blocking the traffic or the Windows machine doesn't have sharing enabled.

I'm going to assume you're trying to share files in this instance, please correct me if I'm wrong.

What you could do is simply try to connect directly to the system's IP and bypass the whole WORKGROUP broadcast stuff all together.

From the nautilus file explorer (the folder icon) you can press ctrl+L and enter:
```
smb://[IP_ADDRESS_OF_WINDOWS_MACHINE]
```
to try and connect.

Let us know if you have any issues with this.

I'm going to assume since both computers are on the same router there wouldn't be a subnet issue but it's worth checking.

Do you mind posting the IP addresses and Subnet mask (the number starting with 255) of both the Windows and Linux machines? If you're cautious about doing that it's safe to do so when the addresses start with 192.168 , 10 or 172.16 since these are [private addresses]("http://en.wikipedia.org/wiki/Private_network") that are not globally assigned.

Cheers

---

