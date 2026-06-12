---
title: "port 80 and 22 problem"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by jeff1234567890 on 2008-10-16
hi, i am trying to run a server but my no-ip is not working, i did port forward with port 43594 80 and 22 but port 80 and 22 are still blocked and searching on google i found that u absobuletly need port 80 and 22 to run ur server so i searched on how to open the port but the only way i found was with no-ip and its cost like 25$ so if someone know how to do it for free it would be really appreciated to have an answer:)

---

### Post by spiderbatdad on 2008-10-16
do you think your isp has blocked the ports?
Try this to see if you have opened the ports locally:```
telnet 127.0.0.1 22
```If you get connection refused, you have not set the rules for your firewall. If you can connect, then the next step is to configure your router (if you have one) to forward requests on those ports to your computer.

---

### Post by jeff1234567890 on 2008-10-16
im new at this lol where am i suppose to put this code?:confused:

---

