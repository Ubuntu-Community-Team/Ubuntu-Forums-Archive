---
title: "Ubuntu 12.04 Internet does not work well"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by ravikanth1988 on 2012-06-24
Hey,
I have a dual boot of Windows 7 and ubuntu 12.04(upgraded from 10.04 yesterday). The internet connection I have works very well on windows 7. On ubuntu it works on and off. I have no idea what to do about it. i don't even understand why it works sometimes and why it does not work at other times. Can you help me solve this problem?

By the way I faced similar issues even with 10.04 before upgrading.

Lastly though I was a bit wary of the Unity talks. I love it :)

---

### Post by firekage on 2012-06-24
In fact some people here have similar problem with network/internet. I don't get it at all, cable on wired is plugged but there is no internet/network but as soon as i boot up at the same machine but with 11.10 there is right after boot wired network/internet.

Somebody give me an tips, you can try:

```
sudo nano /etc/resolve.conf
```

and add there:

```
nameserver 8.8.8.8
```

but i don't know if it will help you.

---

### Post by sudodus on 2012-06-24
What kind of internet connection is it, wired or wireless?

---

### Post by ravikanth1988 on 2012-06-24
It is wired net

---

### Post by d_t_nguyen on 2012-08-16
I have same problem with you. Could somebody help us?

---

### Post by DisturbedDragon on 2012-08-16
Sort out what chipset your LAN is using and ensure proper driver is being used.  If necessary download and compile driver yourself.  

I had issues with slow speed on my Realtek PCIe Gb NIC until I compiled the driver and replaced incorrect but somewhat working driver chosen by the system.

---

### Post by ravikanth1988 on 2012-08-16
@Disturbed dragon
I have spent over 100 hours trying to fix this problem by posting on forums and getting help over IRC channel of ubuntu. Here is the solution.

1. Copy the IP settings, DNS, subnet mask etc and use them on ubuntu. I did this and it started working immediately. 

2. I just got a Cisco router and its working much much better.

Ravi
[www.helloravi.com](www.helloravi.com)

---

