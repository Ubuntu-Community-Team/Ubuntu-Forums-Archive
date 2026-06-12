---
title: "best wifi hardware ?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-10-20
im going to be buying a wireless router & a usb 2.0 wifi adapter for my laptop soon. can you recommend any decent ones that will work "out of the box" or with not much configuration needed ?

---

### Post by Xiong Chiamiov on 2008-10-26
The router doesn't matter a bit.  I've had success with Edimax cards, as they use the Ralink chipset, whose driver is built in to the kernel now.

---

### Post by d_skillz on 2008-10-26
> **Xiong Chiamiov said:**
> The router doesn't matter a bit.  I've had success with Edimax cards, as they use the Ralink chipset, whose driver is built in to the kernel now.

cant go wrong here

---

### Post by alecjw on 2008-10-26
Ralink and intel chipsets seem to work quite well for me

Ralink do open source drivers

IDK about intel, but they work

Best try and avoid broadcom, they dont give a fcuk about us linux users, and only provide closed source windows drivers. Having said that, there is some level of reverse-engineered broadcom support for linux.

---

### Post by ugm6hr on 2008-10-27
> **Xiong Chiamiov said:**
> The router doesn't matter a bit.  I've had success with Edimax cards, as they use the Ralink chipset, whose driver is built in to the kernel now.

If you are set on USB, Edimax cards are generally the best bet (due to Ralink chipset).

Nevertheless, I had to use the serialmonkey driver to get it to work, and replace NetworkManager with Wicd.

Not sure why - it is *supposed* to work out-of-the-box.

---

### Post by maestrobwh1 on 2008-10-27
USB... awesome luck with the Airlink 101

Uses the ZyDAS chip and works out of the box.  Shows significantly stronger signal than internal adapters.

---

### Post by Keen101 on 2008-10-27
Yeah whatever you do stay away from broadcom. Intel mostly seem to work fine. Zydas if your cheap (ebay).

---

### Post by Crafty Kisses on 2008-10-27
> **smooth3006 said:**
> im going to be buying a wireless router & a usb 2.0 wifi adapter for my laptop soon. can you recommend any decent ones that will work "out of the box" or with not much configuration needed ?

Nice avatar. :lolflag: You might want to checkout this link > [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

