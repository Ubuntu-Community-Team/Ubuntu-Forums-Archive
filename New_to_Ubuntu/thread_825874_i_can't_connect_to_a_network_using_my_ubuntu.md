---
title: "i can't connect to a network using my ubuntu"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by nnamdi on 2008-06-11
good day all i cant connect to the internet in my office wth my ubuntu. the network is on auto detect IP address and the windows systems are working fine. i can see the network but i cant browse the net what do i do 
```

ip 10.0.0.206
subnet 255.255.255.0
default gateway 10.0.0.254

primary dns 10.0.0.254
secondary 0.0.0.0

```
when i try pingin my gateway i get no reply


the computer i used to send this mail is on this network too. it is a windows system this is the information

```

Connection-specific DNS Suffix  . : qkon.com
Description . . . . . . . . . . . : Intel(R) PRO/1000 MT Network Connect

Physical Address. . . . . . . . . : 00-0B-DB-C6-B0-4D
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 10.0.0.208
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 10.0.0.254
DHCP Server . . . . . . . . . . . : 10.0.0.254
DNS Servers . . . . . . . . . . . : 10.0.0.254
Lease Obtained. . . . . . . . . . : Wednesday, June 11, 2008 2:42:11 PM
Lease Expires . . . . . . . . . . : Wednesday, June 11, 2008 8:42:11 PM


```

---

### Post by wil313 on 2008-06-11
What ubuntu version are you using?

---

### Post by Het Irv on 2008-06-11
Have you tried resetting everything? Starting with the modem and finishing with the computer.  Sometime that will help solve problems like this.

---

### Post by alexandremrj on 2008-06-11
nnamdi, i will assume that when you mean "auto detect IP address" you are using DHCP automatic configuration?

If that is the case there are some networks that don't do well with it. I recomend you put network manager in static ip adress and insert the values you have just to see if it works

---

### Post by nnamdi on 2008-06-11
yes i mean dhcp

---

### Post by nnamdi on 2008-06-11
am usin ubuntu gusty gibbon ver 7.10 and i meant dhcp network
i.e it get ip automatically

---

### Post by compiledkernel on 2008-06-11
External DNS might not be a bad idea either. There are many public DNS servers that can be used.

---

### Post by Het Irv on 2008-06-11
I am worried about the fact that nnamdi cannot ping the Gateway.  The gateway should be the first set when you are going anywhere, if you cannot reach that, then anything else is pointless.

Oh, one more thing, check your cables, something may have come loose or it stayed in long enough just to get the IP address.  Its worth a shot.

---

