---
title: "Huawei USB Modem"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by jabiru on 2008-11-23
Hello everyone i'm getting crazy tryin' to configure Vodafone internet key aka Huawei E172!
Is it possible? i don't want change my OS to Wi****
Thx 
jabiru

---

### Post by sharke on 2008-11-24
> **jabiru said:**
> Hello everyone i'm getting crazy tryin' to configure Vodafone internet key aka Huawei E172!
Is it possible? i don't want change my OS to Wi****
Thx 
jabiru

Jabiru
Which version of ubuntu are you using if hardy or older you need to install thh latest network manager and it should work.
Regards
Sharke

---

### Post by Rhubarb on 2008-11-24
Ubuntu 8.10 runs nicely with huawei based 3G modems.
I'm currently using a 3 E160G Huawei modem, the new network manager is great for configuring it.

Oh, and hi there sharke, you helped me get Telstra 3G working in Ubuntu 7.10 :)

---

### Post by anet on 2009-04-04
> **sharke said:**
> Jabiru
Which version of ubuntu are you using if hardy or older you need to install thh latest network manager and it should work.
Regards
Sharke

Hi, Sharke,
I'm a unbuntu Noob, have Ubuntu Hardy 8.04 in a partition on my laptop, and have a Huawei EC325 modem, IP is Citycell in Bangladesh. Modem works fine with the softward cd it came with on my Windows. But I can't install that software on Ubuntu. And when I plug in my modem, Ubuntu doesn't seem to recognize it. Or at least, I have no idea where to look if it does. But then, how to make it work...

I've been reading and copy/pasting stuff from other threads and posting questions on them too...but your post brings me to this question:

It sounds like people who've upgraded to ubuntu 8.10 have the tools necessary to connect this kind of modem. But you mention "installing the latest network manager"...how do I do that for my verison of hardy? 

Thanks in advance for any help!!

---

### Post by sharke on 2009-04-05
> **anet said:**
> Hi, Sharke,
I'm a unbuntu Noob, have Ubuntu Hardy 8.04 in a partition on my laptop, and have a Huawei EC325 modem, IP is Citycell in Bangladesh. Modem works fine with the softward cd it came with on my Windows. But I can't install that software on Ubuntu. And when I plug in my modem, Ubuntu doesn't seem to recognize it. Or at least, I have no idea where to look if it does. But then, how to make it work...

I've been reading and copy/pasting stuff from other threads and posting questions on them too...but your post brings me to this question:

It sounds like people who've upgraded to ubuntu 8.10 have the tools necessary to connect this kind of modem. But you mention "installing the latest network manager"...how do I do that for my verison of hardy? 

Thanks in advance for any help!!

We dont need network manager to get this working.
Please have modem plugged in before entering the lsusb command.
In a terminal enter lsusb
we are lookig for the vendor & product id,s for the modem you should see something like
P: Vendor=12d1 ProdID=1001 Rev= 0.00
S: Manufacturer=Huawei Technologies
S: Product=Huawei Mobile
Post back the id,s and we should be able to get you connected with wvdial
Regards
Sharke

---

