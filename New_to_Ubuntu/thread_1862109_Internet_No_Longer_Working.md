---
title: "Internet No Longer Working"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by Inhopeless on 2011-10-16
This is a recent problem. Up until a few days ago, Ubuntu 11.04 recognised my adapater, chosen network, and I could get reasonable  access to the internet. 

However, one day I failed to get a connection to the internet.

My adapter is recognised, and the home network I use is connected to.

However, whenever I load a page in Firefox, Chromium, or use any application that needs an internet connection, I get no data coming into my computer.

The internet works fine on my Windows partition, however.

---

### Post by grahammechanical on 2011-10-16
Hi

My broadband connection has been working fine since I got it a couple of years ago but for the last couple of days the connection has been dropping (just a few times).

Ubuntu is still connected to the router but the router has dropped the connection to the ISP as confirmed by the led on the router marked Internet being red and not green.

In the news there were reports that there was an outage at BT servers. I do not use BT by many ISP get their connections through BT.

To get a connection again I switched the router off and on. And then when I got the green light I opened the web browser. It seemed as if the web browser was stuck remembering that It could not access the Internet.

Regards.

---

### Post by sadaruwan12 on 2011-10-16
First one do this and verify your Wi-Fi data is going through.

```
ping <your router IP>
```

Second (grahammechanical) you try deleting your history of the browser and see if it works.

---

### Post by Inhopeless on 2011-10-17
This is the result I got (My IP address has been omitted for safety reasons).

> PING <IP ADDRESS> (<IP ADDRESS>) 56(84) bytes of data.
64 bytes from <IP ADDRESS>: icmp_req=1 ttl=64 time=0.039 ms
64 bytes from <IP ADDRESS>: icmp_req=2 ttl=64 time=0.043 ms
64 bytes from <IP ADDRESS>: icmp_req=3 ttl=64 time=0.043 ms
64 bytes from <IP ADDRESS>: icmp_req=4 ttl=64 time=0.046 ms
64 bytes from <IP ADDRESS>: icmp_req=5 ttl=64 time=0.044 ms
64 bytes from <IP ADDRESS>: icmp_req=6 ttl=64 time=0.042 ms
64 bytes from <IP ADDRESS>: icmp_req=7 ttl=64 time=0.049 ms
64 bytes from <IP ADDRESS>: icmp_req=8 ttl=64 time=0.043 ms
64 bytes from <IP ADDRESS>: icmp_req=9 ttl=64 time=0.042 ms
64 bytes from <IP ADDRESS>: icmp_req=10 ttl=64 time=0.041 ms
64 bytes from <IP ADDRESS>: icmp_req=11 ttl=64 time=0.048 ms
64 bytes from <IP ADDRESS>: icmp_req=12 ttl=64 time=0.043 ms
64 bytes from <IP ADDRESS>: icmp_req=13 ttl=64 time=0.042 ms
64 bytes from <IP ADDRESS>: icmp_req=14 ttl=64 time=0.041 ms
64 bytes from <IP ADDRESS>: icmp_req=15 ttl=64 time=0.043 ms
64 bytes from <IP ADDRESS>: icmp_req=16 ttl=64 time=0.061 ms
64 bytes from <IP ADDRESS>: icmp_req=17 ttl=64 time=0.043 ms
64 bytes from <IP ADDRESS>: icmp_req=18 ttl=64 time=0.041 ms
64 bytes from <IP ADDRESS>: icmp_req=19 ttl=64 time=0.043 ms
64 bytes from <IP ADDRESS>: icmp_req=20 ttl=64 time=0.041 ms

---

