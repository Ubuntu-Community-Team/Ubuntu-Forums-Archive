---
title: "Got Airlink101 AWLC3028 / RTL8185 wireless working"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by brons2 on 2008-06-24
Finally. 

I never could get it to work on Ubuntu 7.1, and for that reason eventually lost interest in the old laptop I was playing with at the time, an old IBM ThinkPad R32.  (What good is a laptop with no wireless networking?)

Now on 8.04, I got it working after reading the advice from several threads here.  Thanks to various threads, I installed ndiswrapper again, but this time from the Synaptic Package Manager.  I installed ndisgtk, ndiswrapper-common and ndiswrapper-utils-1.9.  

Ndisgtk installs a GUI utility under the Administration menu called Windows Wireless Networks.  I then pulled out the CD that came with the card and pointed it at the Windows 98 drivers per the threads I read here on the forums.  As soon as I loaded the driver, bam the card started working!  I'm one happy camper!

Now, maybe I'll take back the shiny new Core2Duo laptop I bought last Friday :-)

(naaah....:D)

Thanks to Kevdog and his ndiswrapper thread!  [http://ubuntuforums.org/showthread.php?t=574501&highlight=rtl+8185](http://ubuntuforums.org/showthread.php?t=574501&highlight=rtl+8185)

---

### Post by mrund on 2009-01-17
Lordy, that was easy! I've got a TP-Link TL-WN353G wifi card, and your method worked perfectly under Ubuntu Hardy.

---

