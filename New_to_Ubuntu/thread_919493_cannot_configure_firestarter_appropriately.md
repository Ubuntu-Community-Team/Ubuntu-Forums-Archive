---
title: "cannot configure firestarter appropriately"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-14
i need help configuring a firewall. im on public wifi alot and i am growing concerned with the security of my information

---

### Post by mikewhatever on 2008-09-14
> **PatrickMoore said:**
> i need help configuring a firewall. im on public wifi alot and i am growing concerned with the security of my information

If the wifi you use is not encrypted, Firestarter is not going to help, since all the data you send and receive is open to anyone who wants to spy on you. Firestarter can selectively block or open specific ports, however, all ports are closed by default, so that should not be an issue on the desktop.

---

### Post by 1/0 on 2008-09-14
What are you trying to do with the firewall? Stealth some ports or what?

---

### Post by PatrickMoore on 2008-09-14
> **1/0 said:**
> What are you trying to do with the firewall? Stealth some ports or what?

ultimately i just want to secure my system. i use public wifi at school and i use encrypted at home via desktop but considering its xp and no one is really as hardcore as i am in my household about virus protection i just want to make sure no one is going to get into my computer if they happen to get into our wireless

---

### Post by 1/0 on 2008-09-14
I would say the wireless is much less of a problem than WAN. What are the odds of someone sitting and trying to hack your computer at the same time as trying to stay within 50 meters of you...

I think its more likely that worms or people will try to brute force an open port or use a vulnerability in a software to gain access. From WAN they can gain access later on to your computer and do what they want. This however is very very rare. I noticed many brute force attacks on port 21 and 22 so if you're running a ftp or ssh server; consider switching port to one over 10000. 

Check what ports are open and so on with online tools such as [ShieldsUp!](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

