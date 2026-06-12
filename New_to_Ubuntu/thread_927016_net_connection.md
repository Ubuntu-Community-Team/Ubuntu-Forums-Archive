---
title: "net connection"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by maruf10 on 2008-09-22
hello everyone.....

--->System\Administration\Network
--->Wired connection
--->properties
--->ip address 
--->dns
--->default gateway
--->save in /media/filesysten
--->restart

i have done the above procedure

when i write ping <my ip address> in terminal it shows that data receiving....but i can't browse....where is the problem???

---

### Post by jbrown96 on 2008-09-22
Have you tried to ping an outside address? Try pinging google two different ways. 
```
ping -c 10 72.14.207.99
``` and ```
ping -c 10 google.com
``` If the first one works and the second fails, there is a DNS problem. If they both fail there is some sort of connection problem. See if you are getting a valid IP address with ```
ifconfig
```

---

### Post by willca on 2008-09-23
what does this give ya?

$ nslookup [www.ubuntu.com](www.ubuntu.com)
 or
$ ping [www.ubuntu.com](www.ubuntu.com)

---

