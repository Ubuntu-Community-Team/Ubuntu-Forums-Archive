---
title: "gnome ppp trouble unable to run /usr/sbin/pppd"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by gigi1234 on 2012-11-21
Hi! I am hitting the wall on this problem. I have tried reading the howto for dialups and none of the suggestions seem to work.

I am running 10.04 LTS on a Dell XPS m1330.
I want to set up a dialup connection.
I installed the driver for the modem and it works great.
I can dialup successfully using gksudo gnome-ppp.

However, if gnome-ppp is launched without sudo permission, then I get this error: unable to run /usr/sbin/pppd

I have tried adding myself as a user to dip and dialout. That didn't help. 

What else should I try? I am lost.

Thanks!**[B]**[/B]

---

### Post by steeldriver on 2012-11-21
Did you log out and back in after adding yourself to the 'dip' group? the new group membership doesn't take effect until that iirc

---

### Post by gigi1234 on 2012-11-21
No I didn't know that! But I think that was it. Thanks!!!

It seems to be working now...I think.

---

