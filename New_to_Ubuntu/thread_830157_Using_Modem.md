---
title: "Using Modem"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by shoaibi on 2008-06-15
I have HP Compaq 6720s Laptop. And i want to be able to use its 56K modem to connect to internet whenever required.

This link contains the complete specs:
[http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-89315-3442832.html](http://h10010.www1.hp.com/wwpc/us/en/sm/WF06a/321957-321957-64295-321838-89315-3442832.html)

Info from the above link:
```

Modem
56K V.92 modem

```

Something i got from a device mapper on windows:
```

Agere Systems HDA Modem

	Driver Vender: Agere

	PnpID: hdaudio\func_02&ven_11c1&dev_1040&subsys_103c1378

```

---

### Post by shoaibi on 2008-06-17
anyone on this topic?

---

### Post by editrix on 2008-06-17
> **shoaibi said:**
> I have HP Compaq 6720s Laptop. And i want to be able to use its 56K modem to connect to internet whenever required.

```

Modem
56K V.92 modem

```

Actually, that says nothing. You have to know the chipset.

Check on the dialup link in my signature, and also [www.linmodems.org](www.linmodems.org)

I don't know how Linux-savvy you are, but another place to try is [http://tldp.org/HOWTO/Modem-HOWTO.html](http://tldp.org/HOWTO/Modem-HOWTO.html) and [http://tldp.org/HOWTO/Modem-HOWTO-2.html](http://tldp.org/HOWTO/Modem-HOWTO-2.html)

and, of course the Sticky: Setting up your dialup modem (aka winmodem) which is at the top of the Networking and Wireless forum.

---

### Post by housam on 2008-06-17
As stated above , visit the link given to you [[COLOR="Red"]_http://www.linmodems.org/_[/COLOR]]("http://www.linmodems.org/") and scan your modem using the [COLOR="RoyalBlue"]scanModem[/COLOR] tool in this link to know the driver needed to activate your modem. then download/install it. the driver package will have the installation instructions.

---

