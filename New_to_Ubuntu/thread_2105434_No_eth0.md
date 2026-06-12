---
title: "No eth0"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by TheTardis on 2013-01-16
After my friends computer kept crashing on windows, I decided to install ubuntu 12.04 on it as he only needs it for basic Internet connection. However, I can not get the computer to detect the ethernet cable. I have the same install on my computer, and it detects the cable and will automatically connect to the internet just fine.

I did some searching on google for similiar problems and found out that it is not even detecting the ethernet port as when I try the command **ifconfig -a** the results are only:

lo                  Link encap:Local Loopback
                      inet addr:127.0.0.1 Mask:255.0.0.0
                      inet6 addr:  : : 1/128 Scope:Host
                      UP LOOPBACK RUNNING  MTU:16436  Metric:1
                      RX packets:176 errors:0 dropped:0 overrunes;0 frame:0
                      TX packets:176 errors:0 dropped:0 overrunes:0 carrier:0
                      collisions:0 txqueuelen:0
                      RX bytes:14144 (14.1 KB)  TX bytes:14144 (14.1 KB)



From what I can determine from google, this means that the network card is not recognized by Linux, but I dont know how to determine what the network card and as such I dont know how to find out if there is a driver available for it. For all I know that may not even be the issue. Any help is appreciated.

---

### Post by deadflowr on 2013-01-16
Try:

```
lspci | grep Ethernet
```

And probably post back your results, if any.

---

### Post by TheTardis on 2013-01-16
No results, just goes straight to the next line :neutral:

---

### Post by von Corax on 2013-01-16
If you still have some way of booting Windows you could check the Device Manager to see how it recognizes your NIC.

---

### Post by audiomick on 2013-01-16
You could try
```
sudo lshw -c network
```

and see if that finds anything, but I don't know if that will do any better than lspci.

---

