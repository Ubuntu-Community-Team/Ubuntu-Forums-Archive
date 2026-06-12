---
title: "[SOLVED] hardy won't recognize wired connection"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by bmann11 on 2008-08-06
I can't connect to evolution or ff using a wired connection even though it works fine on my windows partition, which I'm using right now.  Everything appears to be working and connected, but it just ain't working.

---

### Post by hyby on 2008-08-06
I had this same problem, can I get your specs first? 

You have to play around with the network connection, turn off roaming mode and enable DHCP or set your IP details.

---

### Post by bmann11 on 2008-08-07
How do I get IP details and what kind of specs would be helpful?

I'm using an older Dell laptop latitude D600 with a pentium 1.6 mghz processor.  As I mentioned earlier, I'm running 8.04

---

### Post by zvacet on 2008-08-07
> How do I get IP details and what kind of specs would be helpful?

You can find them in Windows under network connections.You should know your nameservers witch you will put under network>DNS tab in Ubuntu.In short your spec should be the same as in Windows(obviously).

---

### Post by bmann11 on 2008-08-07
I got the specs from windows and checked them with the specs in the DNS tab, and they were not the same.  I attempted to enter the IP, Gateway specs manually while in ubuntu, but I still couldn't connect.  At this point, I'm lost.

I should also mention that I usually connect wirelessly at my home in the US and don't have any trouble.  I've been in Brazil for the past 6 weeks and haven't had much trouble up until the past 24 hours.

---

### Post by zvacet on 2008-08-07
On the upper right side of panel clcik on network manager icon>manual configuration>select your modem (don´t check box just click on your modem)>properties>select yout type of connection (dhcp or static)>in upper left corner uncheck roaming mode>close>DNS tab>you will find address there and if you use router leave it and if you don´t delete it>put your nameservers>general tab> check box on your modem>close.That should be it.

---

### Post by bmann11 on 2008-08-07
are the nameservers the IP, subnet mask, and default gateway?  If not, what is the nameserver and how do I access it?  Thanks and forgive my computer retardedness.

Edit:  By the way, I understand all of the directions except the nameserver piece.

---

### Post by zvacet on 2008-08-08
> what is the nameserver and how do I access it?

Nameserver is your ISP address.For example if you use OpenDNS namesever will be 208.67.222.222 and 208.67.220.220.If you can not find it in Windows settings ask your ISP provider for address.Or you can use one from OpenDNS.

---

### Post by bmann11 on 2008-08-08
It started working again as randomly as it stopped.  Thanks for the help.  I'm a bit more educated now, if nothing else.

---

