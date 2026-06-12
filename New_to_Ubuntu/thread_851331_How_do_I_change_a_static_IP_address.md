---
title: "How do I change a static IP address?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by smithwk2 on 2008-07-06
Could someone point me to the command where I can change the static IP address for an Ubuntu 8.04 implentation?  Thanks in advance for any help.

Wayne

---

### Post by Troll_the_Great on 2008-07-06
Not sure what you mean...You want to change your network address?

---

### Post by smithwk2 on 2008-07-06
Yes, I need to change the network address from 1.192.168.55 to 1.192.168.60.  Thanks.

Wayne

---

### Post by Xerp on 2008-07-06
You can use the Network Manager applet icon and change it from there. If you want the command to change the IP address for a NIC, it is ifconfig. Here is an example:

```
sudo ifconfig eth0 10.88.77.66 netmask 255.255.255.0
```

---

### Post by unutbu on 2008-07-06
If you are configuring a home network,
your IP address will start with 192.168.*.* not 1.192.168.*. You might want to double check that.

---

### Post by steveneddy on 2008-07-06
I think you want to do that in the router.

---

### Post by AndyCooll on 2008-07-06
You can do it from the router (the method I use). You can also click on the network applet (near to the clock) and select the "Manual configuration" option.

:cool:

---

