---
title: "Broadcom B43 wireless - Dell 1501"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by XulluX on 2008-11-01
I did an update a few days ago, and I have been unable to connect to my wireless network.  I can connect to the network with all my other workstations (a mac mini, a server with windows 2003, 3 macbook pro's and a Vista box). All the mac's are connected via wireless. 

The machine that I'm having a problem with is a Dell 1501 when I first started to have the problem I was running 8.04 but have since then updated 8.10.  Its running off the restricted Broadcom B43 wireless driver. I can authenticate with the router but for some reason it will not remain connected.  If I check my router for the IP address that access the router I find my system.  So I know my card is somewhat functioning, but I will not remain connected. 

Any Ideas?

---

### Post by Bölvaður on 2008-11-01
this sounds very strange. Btw was this working on 8.04? If so you might be able to upgrate/downgrate to that kernel.

---

### Post by saskchi on 2008-11-02
Here is what I did to fix the wireless issue in 1501

First install any updates using the update manager or command line

1. Connect your laptop to the Internet using your Ethernet port
2. Click System-> Administration-> Hardware Drivers
3. Let it search for the Broadcom drivers
4. Activated drivers
5. Once installed, click the network icon and choose connect to hidden network
6. The rest is self explanatory

Hope this helps

---

