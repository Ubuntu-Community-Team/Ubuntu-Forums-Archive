---
title: "Wireless card install?"
date: 2012-10-02
forum: New to Ubuntu
---

### Post by BuzzStPoint on 2012-10-02
Trying to install a network card, 
Bear with me, I'm a novice at linux configuring. 

On the network icon the enable wireless is greyed out. So I can't check it. 
Here's what I have so far.

```

$ lspci | grep etwork
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

```

This is a fresh install of Kubuntu 12.04 64 bit.  Nothing else has been installed.

Edit: Compaq Cq50 Laptop.

---

### Post by daslinkard on 2012-10-02
> **BuzzStPoint said:**
> Trying to install a network card, 
Bear with me, I'm a novice at linux configuring. 

On the network icon the enable wireless is greyed out. So I can't check it. 
Here's what I have so far.

```

$ lspci | grep etwork
07:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)

```This is a fresh install of Kubuntu 12.04 64 bit.  Nothing else has been installed.

Edit: Compaq Cq50 Laptop.

With it being greyed out....is there a button on the front of the machine or on the side to enable wireless?  Or possibly a key combination of FN + F2 <----combination for my wireless?

---

### Post by BuzzStPoint on 2012-10-02
There is a wireless button, But it was lit up blue upon start up.
I've tried pressing and even holding the button with no results.

I notice that if I disconnect the wired, it will display "Wireless Disabled by hardware"

---

### Post by BuzzStPoint on 2012-10-02
Found a forum post on a Fedora forum... 

Here's what fixed my issue.

[B]The solution is to have it running under Windows and:

1. Under device manager choose the Atheros AR9285 Wirless LAN
2. Under Power Management, disable the "Allow Windows to switch off deivice for power saving[/B]

rebooted to Kubuntu, wireless is up and running.

---

### Post by daslinkard on 2012-10-02
Awesome, glad it is solved for you!  Thank you for posting the work around!

---

