---
title: "[SOLVED] Wubi hates DNS with a static IP"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Bailywolf on 2008-11-07
I installed Ubuntu (Ibex) via Wubi to get a feel for it before going all-out.

I have a static IP setup, and at first I duplicated the config my XP install uses.  No dice.

I get a good network connection, and can resolve a website if I know the IP address, but it can't handle name resolution for some reason.  It's like it can't find the DNS servers.  

I also tried a different static IP than the XP install uses in case there was some kind of conflict.  Same deal.

Otherwise, the Wubi implementation works just fine... but this static IP thing really sucks.  

-B

---

### Post by Titan8990 on 2008-11-07
How did you configure you static IP? Did you add your router as a DNS server in the Network Config GUI or in /etc/resolv.conf?

---

### Post by Bailywolf on 2008-11-07
> **Titan8990 said:**
> How did you configure you static IP? Did you add your router as a DNS server in the Network Config GUI or in /etc/resolv.conf?

I used the network config, but did *not *add my router as a DNS server.  I put the DNS servers in the spot the N.C. tool asked for them, and the default gateway in that spot.

-B

---

### Post by Titan8990 on 2008-11-07
Use your router's address for your DNS server and see if that works.

---

### Post by Bailywolf on 2008-11-07
> **Titan8990 said:**
> Use your router's address for your DNS server and see if that works.

I'm back to XP land- nope, this didn't help either.  

I used the network tools to ping the address provided in the help docs, and was able to ping it, but in an odd twist, I could not ping the DNS servers.  

Stumped.

-B

---

### Post by Bailywolf on 2008-11-07
I come to you live from inside Ubuntu to report that I AM A COMPLETE MORON.

I had the wrong DNS IP.

Ubuntu is working great so far.

I will go slink off and poke around in Applications now.

-B

---

