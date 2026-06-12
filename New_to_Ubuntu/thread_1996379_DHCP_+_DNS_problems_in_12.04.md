---
title: "DHCP + DNS problems in 12.04"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by getut on 2012-06-04
Sorry for the crosspost. I waited around 2 days and never got an answer in the networking specific forum.

I just installed our first 12.04 machine in our network and am having problems with DNS. I have already read about the changes to the DNS system in 12.04, but I need to know how to fix the after effects.

The first one is definitely a problem, but number 2 may just be a display issue.

1) My DHCP server assigns search domains with option 135 "domain suffix search order". It seems to not be working on 12.04. How can I get this option to work without have to manually assign this on my machines?

2) nm-tool is only reporting the system as having 1 assigned DNS server when we have many. What is going on here?

---

### Post by sandyd on 2012-06-04
> **getut said:**
> Sorry for the crosspost. I waited around 2 days and never got an answer in the networking specific forum.

I just installed our first 12.04 machine in our network and am having problems with DNS. I have already read about the changes to the DNS system in 12.04, but I need to know how to fix the after effects.

The first one is definitely a problem, but number 2 may just be a display issue.

1) My DHCP server assigns search domains with option 135 "domain suffix search order". It seems to not be working on 12.04. How can I get this option to work without have to manually assign this on my machines?

2) nm-tool is only reporting the system as having 1 assigned DNS server when we have many. What is going on here?
Dnsmasq, oh dnsmasq...
Run
```
gksudo gedit /etc/NetworkManager/NetworkManager.conf
```
Stick a "#" (without quotes) to make the line 
```
dns=dnsmasq
```
look like
```
#dns=dnsmasq
```

save.

```

sudo restart network-manager
```
The second problem will be fixed by the change as well - all dns requests are routed through dnsmasq, which makes it appear as if there is one dns server.

---

