---
title: "Network problems"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by stlcity on 2008-12-01
Hi. this is my first post and I am new to Linux. Here is my problem:

I recently put together an HTPC with ASUS M3A78-EM AM2+/AM2 AMD 780G HDMI Micro ATX motherboard and AMD Athlon X2 4850e 2.5GHz Socket AM2 45W Dual-Core Processor. I installed both XP(blueray playback) and ubuntu(**Hardy**) with the latter being the default OS on boot. I have a home network with Belking wireless G router. I installed this PCI adapter for connecting to the net as the reviews said that it was complaint with linux.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041](http://www.newegg.com/Product/Product.aspx?Item=N82E16833315041)

The problem is that I was able to connect to the internet thru both the OS for about 2 days. Yesterday when I was browsing the net in Ubuntu the connection dropped and I have not been able to connect to the net in Ubuntu since. 

But I can boot into XP and connect to the net wirelessly without problems. I was wondering if anybody out there has any ideas and can help me. THanks in advance

---

### Post by superprash2003 on 2008-12-01
post output of the following commands from the terminal
1)lshw -C network
2)iwconfig

---

### Post by stlcity on 2008-12-01
> **superprash2003 said:**
> post output of the following commands from the terminal
1)lshw -C network
2)iwconfig

will do so this evening. I am at work now.

---

### Post by mapes12 on 2008-12-01
You could also try WICD instead of Network Manager. Here's a success thread: [http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

---

