---
title: "Ubuntu 12.04 compatibility with Acer Netbook"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-04-05
Does anyone have experience with 12.04 setting up the wireless on an  Acer Netbook Aspire D250-1165? 

Our only remaining computer to switch from XP to Ubuntu is this one and my wife needs it on a daily basis so I would prefer to not have it down for a long time trying to figure out how to get the wireless working.

The build sheet that came with it:

CPU: Intle Atom processor N270
Wireless: 802.11 b/g WLAN
WWAN: NO

From Device Manager:

Atheros AR 5007EG Wireless Device Manager
Atheros AR 8132 PCI-E Fast Ethernet Adapter

Also, this may be relevant, I already tried to boot from the 12.04 USB ISO that I used on three other computers and it would not work on the Acer because of "the wrong processor."

---

### Post by Double.J on 2014-04-05
> **riverguy99 said:**
> Atheros AR 5007EG Wireless Device Manager
Atheros AR 8132 PCI-E Fast Ethernet Adapter

Also, this may be relevant, I already tried to boot from the 12.04 USB ISO that I used on three other computers and it would not work on the Acer because of "the wrong processor."

Hi there! 

I've installed quite a few netbooks now. Generally atheros wifi is supported out the box on ubuntu and derivatives and not supported otb on fedora and suse, but is usually easy to get the drivers after install.

as for the processor message, it's just that the processor in that netbook is an N270 which is 32bit. If you downloaded the recommended installer from the ubuntu website it's the 64 bit system. 32 bit can run on 64 bit hardware, but 64bit systems cannot run on 32 bit chips.

for future reference, all N2* and Z5* atom chips are 32 bit, all others are 64 bit enabled (although their mother boards may not support it) 

Jj

---

### Post by riverguy99 on 2014-04-05
> **gnu/mirow said:**
> Hi there! 

I've installed quite a few netbooks now. Generally atheros wifi is supported out the box on ubuntu and derivatives and not supported otb on fedora and suse, but is usually easy to get the drivers after install.

as for the processor message, it's just that the processor in that netbook is an N270 which is 32bit. If you downloaded the recommended installer from the ubuntu website it's the 64 bit system. 32 bit can run on 64 bit hardware, but 64bit systems cannot run on 32 bit chips.

for future reference, all N2* and Z5* atom chips are 32 bit, all others are 64 bit enabled (although their mother boards may not support it) 

Jj

Thank you so much for the quick (and encouraging) response!

---

