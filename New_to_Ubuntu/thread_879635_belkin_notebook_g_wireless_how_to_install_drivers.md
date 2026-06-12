---
title: "belkin notebook g wireless how to install drivers"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by hazman on 2008-08-04
hi have all the tools i think to get the card going as its a fresh install just mind gone a blank on how to get wireless again

---

### Post by northern lights on 2008-08-04
Can you please post the output of ```
sudo lshw -C network
```Thank you.

---

### Post by bobnutfield on 2008-08-04
Many (not all) Belkin PCMIA cards use a Ralink chipset and are supported with the RL2500 module right out of the box.  If it is a USB dongle, there are five different versions which use different chipsets, and not all will work natively with Linux.  Some will, while others will require the use of ndiswrapper.  If it is a natively supported chipset, you can simply click on the network icon in the right side of your panel, and a network (if one is available within range) will be listed.  If you know you are in range of a network and you see none when clicking the icon, you will have to do some setting up with third party drivers (usually, some exceptions).

---

