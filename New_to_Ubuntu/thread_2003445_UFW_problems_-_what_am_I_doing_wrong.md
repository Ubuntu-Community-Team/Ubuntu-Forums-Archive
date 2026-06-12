---
title: "UFW problems - what am I doing wrong?"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by zozza on 2012-06-14
Here are my ufw rules:

sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
128.100.22.22              ALLOW       93.101.128.0/18

93.101.128.0/18            ALLOW OUT   128.100.22.22

128.100.22.22 is my IP

93.101.128.0/18 is the range for my VPN.

My impression is that I am saying: allow from my IP to the VPN range and then allow from the VPN range to my IP.

However, this is obviously not the case because I cannot connect to anything.

See the attachment for how it looks in GUFW.

What am I doing wrong?  Thanks!

---

