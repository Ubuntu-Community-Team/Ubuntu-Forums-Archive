---
title: "Wireless problem"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by subash_patel on 2008-06-05
Hardware:  Acer Aspire 4520
            AMD Athlon 1.9GHZ X 2, 2GB DDR2, NVIDIA GeForce 7000M
OS:
            Ubuntu 7.04 (Feisty), WinXP

I tried dual booting with both XP and Feisty. All the drivers correctly install on the XP. But ubuntu doesnt detect the NVIDIA wireless hardware. I did a PCI walk and also lot of trouble shooting methods mentioned in other threads. I also tried downloading and installing the driver package using Synaptic. Nothing works out.

First and foremost, how to find if the hardware is detected?
Second, how to find exact driver? 

Broadcom 802.3 and bluetooth works.
NVIDIA - Basic graphics only, No WiFi(802.11 b/g)
--------------------------- END ---------------------------------
Problem 2:

I have an age old PIII system for which I added a cheap network card from TECHCOM recently. It is also uses the RTL8139 chipset. But fiesty doesnt detect at all. I tried porting the 2.4 driver provided by the manufacturer to 2.6 (since I know little bit of driver programming) following driver porting guidelines found somewhere. It didnt work either. Any idea what might be the reason, since the same card is detected on Windows and RHL flavours.

---

### Post by bhavi on 2008-06-06
Hello 

Please paste the output of:

```
lspci
```

or

```
sudo lshw -C wifi
```

---

