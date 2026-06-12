---
title: "Can't get wifi adhoc network to work..."
date: 2011-09-08
forum: New to Ubuntu
---

### Post by PhillyPhil on 2011-09-08
I have two computers (A: 10.04, B: 11.04) and a single 3G dongle in a hotel room.

I want to share the 3G connection between both computers.

I plugged the dongle into computer A, added a new network (on A) (Mode=adhoc, Connect automatically, method=Shared to other computers). Computer A said it was connected to the adhoc network, but it was greyed out and showed zero bars in Network Manager.
Computer B could see the new network, and when attempting to connect the NM icon on B indicated that both computers were trasmitting, but the connection was never established, and eventually would just time out.
I logged out and in again on A, and this time the adhoc network was not greyed out, and had full bars.  Still exactly the same result when trying to connect from B though.

I deleted the adhoc network on A moved the dongle to B, and created a new adhoc network there.
B did not say it was connected to the new network, and A could not see the network.
I logged out/in on B, this time it said it was itself connected to the adhoc network, and A could see it, but when A tried to connect the NM icon on A indicated that B was silent, not replying to anything from A, and so the connection was not established.

Why is something that should be incredibly easy so hard?
Why the inconsistent behaviour (computers/OS versions/sessions)?
"Easy" things that don't go right are so much more annoying that difficult things that don't work, and TBH establishing a wifi connection between 2 devices is something I take for granted these days....

Does anyone know where I went wrong/ how I can get this to work?

---

### Post by PhillyPhil on 2011-09-09
I just managed to successfully connect B to A when A had an unsecured adhoc network (although I failed when I tried the same thing earlier) but there's no way I'm allowing an open AP here.
As soon as I turn security on, B cannot connect.

My phone can see the adhoc network and despite the fact it's secured with WPA2, the phone thinks it's WEP!!  That could explain why B is unable to connect...(the phone is also unable to connect)

This is driving me crazy...

---

### Post by snip3r8 on 2011-09-09
why dont you just try using wep instead of wpa2

---

