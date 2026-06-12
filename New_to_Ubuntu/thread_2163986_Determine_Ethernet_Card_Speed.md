---
title: "Determine Ethernet Card Speed"
date: 2013-07-20
forum: New to Ubuntu
---

### Post by PierreRobiquet on 2013-07-20
Hello,

My ISP recently upgraded me to a 120Mbps connection, at the current time however my router only has 100Mbps ethernet ports giving me only ~90Mbps on a speed test (as I assume due to overhead) as such I'm considering upgrading to a router that supports gigabit speeds, but before I spend the money is there an easy way to tell if my laptops ethernet card supports gigabit speeds?

I've tried Googling around, but it seems that the results are contradictory with some saying it only supports 100Mbps whilst others say it's gigabit compatible. If it helps I have a Lenovo Z560. I'm hoping there's some command I can type into the terminal to give me this information?

---

### Post by Kujua on 2013-07-20
```
sudo ethtool ethX
```
Replace 'X' with your interface's number. Generally eth0 if you have only one ethernet card.
Supported link modes will show *1000baseT* if the card supports Gigabit ethernet.

NOTE: ethtool might not be installed by default. You can get it from repositories.

---

