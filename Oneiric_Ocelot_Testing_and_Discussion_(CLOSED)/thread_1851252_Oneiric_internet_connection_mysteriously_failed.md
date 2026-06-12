---
title: "Oneiric internet connection mysteriously failed"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by seanlano on 2011-09-27
I've been using the testing releases of Oneiric for a while now, with very few problems, but just this morning I installed some updates and some graphics software from a Natty PPA (since it doesn't have an Oneiric one yet) and now the Internet connection flatly refuses to work. I can still ping devices on my LAN, but I can't connect to the "outside world". I have no idea why. The Internet still works fine on the Lucid partition of the same system, it's just Oneiric that won't work.

---

### Post by garvinrick4 on 2011-09-28
What build of network manager are you using? just curious.

---

### Post by cariboo on 2011-09-28
It sounds more like a DNS problem, than a network-manager problem. Can you ping by number eg:

```
ping 173.194.33.16
```

if that works try by name:

```
ping www.google.com
```

I always setup static ip addresses for systems with a wired connection, you can easily do this in network-manager, use your isp's DNS server for the DNS settings.

---

### Post by seanlano on 2011-09-29
Yeah, setting Network Manager to use "DHCP (Addresses Only)" and manually setting the DNS to use OpenDNS has fixed the issue. So then it's an issue with my crappy router not doing DNS properly (which is also set to use OpenDNS, but it doesn't seem to pass that on to clients). 
I guess something in one of the updates may I have reset Network Manager. I'm not sure how to find the version of Network Manager.

---

### Post by cariboo on 2011-09-29
If you haven't run:

```
apt-get clean
```

recently, you can use:

```
apt-cache showpkg network-manager
```

to list what version of network manager installed.

---

