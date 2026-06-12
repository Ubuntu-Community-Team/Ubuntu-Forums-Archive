---
title: "Wireless adaptor for Ubuntu 8.04 64-bit"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by turingcs2005 on 2008-09-02
I just installed Ubuntu 8.04 64-bit operating system and could not get my wireless adaptor (Abit Airpace wi-fi) to work. (I tried ndiswrapper but to no avail)

Is there a wireless adaptor that will work once I plug it in? (be it PCI or USB) My budget is around $50.

Thanks!

---

### Post by Bucky Ball on 2008-09-02
You will find you need the Atheros setup as that card is based on Atheros chipset. You could first try checking in System->Administration->Hardware Drivers and see if the Atheros driver is in there. If it is, tick and see if it works (may ask you to download some other stuff - agree). If it doesn't, make sure you untick and then try this link:

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

---

### Post by ubume2 on 2008-09-02
Did you try it without installing the windows driver for your device?  There is a possibility that 8.04 has your driver already installed.

I don't know anything about yours, but with mine (a Belkin 7050), after toiling with ndiswrapper and installing the windows driver and not getting any joy, that 8.04 already had the required driver.

I did have to manually configure /etc/network/interfaces and rc.local.

Read [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
and
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

---

### Post by Bucky Ball on 2008-09-03
Good point, Ubume. May need to make sure restricted drivers are installed also for this.

---

