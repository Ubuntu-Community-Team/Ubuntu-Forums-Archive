---
title: "[SOLVED] I have just downloaded and installed the new ubuntu"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by keith071482 on 2008-11-20
I am having to issues when checking hardware my wireless internet card is supported and green, but i have a touch button to turn my wireless internet on and it wont let me turn it on??? any thoughts...

Second I am still in hardware and I can't get my graphics card lite to go supported, the graphics card is an ati radeon HD3200 , please help 

thank you all so much.

---

### Post by nhasian on 2008-11-20
what kind of wifi adaptor do you have?

in a terminal type:

```
lshw -C network
```

also please post the output of:

```
iwconfig
```

---

### Post by nhasian on 2008-11-21
according to your private message, you have:

> description: Ethernet controller
product: AR242x 802.11abg Wireless PCI Express Adapter
vendor: Atheros Communications Inc.

please follow my instructions in this post to get your wifi adaptor to work in Ubuntu 8.10:

[http://ubuntuforums.org/showpost.php?p=6059353&postcount=15](http://ubuntuforums.org/showpost.php?p=6059353&postcount=15)

---

