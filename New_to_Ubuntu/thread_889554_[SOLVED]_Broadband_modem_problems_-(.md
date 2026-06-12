---
title: "[SOLVED] Broadband modem problems :-("
date: 2008-08-14
forum: New to Ubuntu
---

### Post by marufaberlin on 2008-08-14
Hi,

I've just got a new broadband internet connection, but I am very disappointed about the modem the company sent me. It is a SIEMENS ADSL C2-010-l.

My network has the following layout:


[LIST]
[*]AVM FRITZ! BOX Router
[LIST]
[*]NETGEAR GIGABIT SWITCH
[LIST]
[*]my computers etc
[*]...
[*]...
[/LIST]
 
[/LIST]
 
[/LIST]
However, the modem (which uses special windows dialling software) needs to be connected ad-hoc to a computer. It has no IP, or whatsoever, so I can't access it in any way.

Is there any way of using it for my whole network (by connecting it to the router, etc...) so that I can use it under linux and on all my machines?

Thanx in advance,

marufaberlin

---

### Post by sharks on 2008-08-14
try sudo pppoeconf

---

### Post by marufaberlin on 2008-08-14
yeah, but the thing is, the Modem doesn't have an IP. Or a MAC address either, as far as I can tell.

---

### Post by sharks on 2008-08-14
is it dynamic ip (dhcp)?

---

### Post by marufaberlin on 2008-08-14
Do you mean my network? Yes.
Do you mean the modem? No.

---

### Post by marufaberlin on 2008-08-15
nobody answering?

---

