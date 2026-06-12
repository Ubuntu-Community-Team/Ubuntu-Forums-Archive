---
title: "WiFi not there"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by islnd on 2008-11-07
edit wireless networks shows no network , I have a broadcom PCI card installed and I hope recognised , this from terminal:
island@island-desktop:~$ sudo lshw -C network
[sudo] password for island: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: BCM43XG
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=32

Please advise how I get this connection working?

---

### Post by shifty_powers on 2008-11-07
what version of ubuntu are you using?

---

### Post by islnd on 2008-11-07
> **shifty_powers said:**
> what version of ubuntu are you using?

8.04 lts

---

### Post by shifty_powers on 2008-11-07
have you tried a live cd of the latest 8.10?

they've worked really hard on wireless support, especially the broadcom chips...

---

### Post by islnd on 2008-11-07
> **shifty_powers said:**
> have you tried a live cd of the latest 8.10?

they've worked really hard on wireless support, especially the broadcom chips...

Yeah , and it worked a treat ,but I had several other seemingly unresovlable issues with 8.10 , (graphics especially) so went back to 8.04 .
Not a big problem as I'm using an ethernet , just working my way through my hardware etc...... see what will work .

---

### Post by B34ST1Y on 2008-11-07
you may require the install of the madwifi drivers to make it work

---

