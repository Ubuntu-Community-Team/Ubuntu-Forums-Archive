---
title: "how to find the ip of a device connected to ethernet?"
date: 2016-05-23
forum: New to Ubuntu
---

### Post by hach75 on 2016-05-23
Hi, 

I have an external hard drive connected directly to my laptop trough Ethernet. I need to access this drive with SSH because if fails to mount but i don’t know its IP. 

Any ideas?

Thank you

---

### Post by CantankRus on 2016-05-23
Log into your router and look at the DHCP client list or Attached Devices list.

---

### Post by hach75 on 2016-05-23
Thanks for your reply CantankRus, 

The drive is connected Directly to my laptop not the router and I need terminal access to it. 

Thank you

---

### Post by CantankRus on 2016-05-23
Maybe arp-scan?
```
sudo apt-get install arp-scan
```
```
sudo  arp-scan -l
```

---

### Post by hach75 on 2016-05-23
Thanks again for your reply CantankRus, 

Thats what i was looking for. Thank you

---

