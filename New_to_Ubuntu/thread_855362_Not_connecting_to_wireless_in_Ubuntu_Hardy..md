---
title: "Not connecting to wireless in Ubuntu Hardy."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by ElTesorillo on 2008-07-10
I am been having big troubles with my wireless after a smooth switch to Ubuntu from xp. I was told that WICD would fix my problems but it can connect to my wifi signal in my house. It seems to read the signal but cant connect. Now I have neither wicd or network manager installed. How can I connect to my wifi? It is driver me a little crazy! Thanks.

---

### Post by phidia on 2008-07-10
Open a terminal and copy/paste this into it> lspci -v
We need to know what network device your computer is using.

---

### Post by fatality_uk on 2008-07-10
Do you know what type of wireless card chip you have?
If not, type > lsusbinto a terminal and post the results back here.
If it's Atheros or Broadcom, there are ways to solve that quite quickly.

---

### Post by ElTesorillo on 2008-07-10
Umm.. I cant really post it into here since I am not on my ubuntu partition but I will try to copy some stuff by hand..

The lsci -v came up and the network controller is Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

The lsusb came up as Bus 007 Device 002: OmniVision Technologies INC.
Bus 006, 005 and 003 is Broadcom Corp.

I hope that helps.

---

### Post by ElTesorillo on 2008-07-10
> **fatality_uk said:**
> Do you know what type of wireless card chip you have?
If not, type into a terminal and post the results back here.
If it's Atheros or Broadcom, there are ways to solve that quite quickly.

I hope that this can work well. Sorry that I didn't get to paste the code in.

---

