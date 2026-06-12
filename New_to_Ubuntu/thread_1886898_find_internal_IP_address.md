---
title: "find internal IP address?"
date: 2011-11-25
forum: New to Ubuntu
---

### Post by DaimyoKirby on 2011-11-25
Does anyone know how I can find my internal IP address?

---

### Post by trinux_bc on 2011-11-25
In Terminal you can type

ifconfig

Or you can click on the network applet, then click 'connection information.'

trinux_bc

---

### Post by tersogar on 2011-11-25
Check this link.[https://help.ubuntu.com/11.10/ubuntu-help/net-findip.html](https://help.ubuntu.com/11.10/ubuntu-help/net-findip.html)

---

### Post by DaimyoKirby on 2011-11-25
Thanks so much! That article explained it very nicely!

---

### Post by tersogar on 2011-11-25
Your welcome. Please mark the thread as solve.

---

### Post by prakshina on 2013-01-24
> **DaimyoKirby said:**
> Does anyone know how I can find my internal IP address?

To find your internal ip address follow the below steps:

Open the terminal window then type "ifconfig" 
It will display list of network device in your computer.
In that the "lo" denotes local host and it should always be start with 127.x.x
The "inet addr" which starts from 192.168.x.x  that is your internal ip address.
If you want to view your external ip address visit the site [Ip-details.com]("http://www.ip-details.com/")  .

---

