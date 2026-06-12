---
title: "Realtek RTL8188CU Wireless LAN 802.11n USB 2.0 Network Adaptor"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by fleamour on 2012-01-02
Hi

Anyone know how to get the above working in Xubuntu 10.04 LTS?  It is not automatically detected so I guess there is no driver for it in kernel.  Installing a external driver (not in kernel) would require a reinstall each kernel upgrade, right?  That would not be ideal but a work around.

My brother bought it of eBay, & it says Linux compatible on packaging.  will it be backwards compatible with USB 1.1?  I plug it in & it is not recognized.

:confused: :( :confused:

---

### Post by fleamour on 2012-01-02
Seems this is the answer:

[http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux&p=46859#post46859](http://www.solwiseforum.co.uk/showthread.php?9849-NET-WL-UMD-606N-and-Linux&p=46859#post46859)

Bit complex, may stick to my trusty PCMCIA card.

---

### Post by Locke_99GS on 2012-01-02
The RTL8188CU uses the same driver as the RTL8192CU. This driver (along with others of that pedigree) was added to staging for kernel for 2.9.31 (or .32?). Since Ubuntu uses the same kernel configuration for any particular version of Ubuntu, regardless of the actual kernel being used, any kernel upgrade offered by Ubuntu (regular upgrades or new mainline builds) will be configured the same way as it was in April of 2010 - without these modules enabled.

Building a newer kernel with 8192CE and 80211 as modules is, in my opinion, the best way to do this. Alternatively, building the module separately for every kernel will work just as well.

---

