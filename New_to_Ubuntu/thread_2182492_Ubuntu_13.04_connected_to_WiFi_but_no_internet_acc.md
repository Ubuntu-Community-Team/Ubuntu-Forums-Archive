---
title: "Ubuntu 13.04 connected to WiFi but no internet access"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by pritx1990 on 2013-10-21
I upgraded to Ubuntu 13.04 from 12.10 a few days back. internet was working fine with 12.04. however it stopped as soon as I upgraded. the toolbar shows that connection to WiFi is established. but I can not access the internet through the browser. the router is working fine as I vcan access internet through other devices. please help!!!

---

### Post by dankojoffrey on 2013-10-21
Is the gate (probably router address) and DNS set correctly...???

---

### Post by newb85 on 2013-10-21
To see if it's DNS related, 

```
 ping 8.8.8.8 
```

After a few seconds,  ctrl+c to stop it.   See whether packets came back.

---

### Post by dankojoffrey on 2013-10-21
and also ping router address to determine if there is a problem between PC and router...

---

### Post by Hadaka on 2013-10-21
Hi, Let's take a peek and see if the driver got clobbered
in the upgrade...please post the output of..
```
lspci -nnk | grep-iA3 net
lsmod
rfkill list all
```
thanks.

---

