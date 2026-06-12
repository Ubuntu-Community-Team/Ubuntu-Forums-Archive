---
title: "Firestarter still allows ping"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-06-01
Hello Everybody,

I recently installed Firestarter for when I have to log onto public hotspots at airports etc and I ran a Shields Up test before and after. Before, the ports could be seen but were closed and after they could not be seen at all. All as it should be. 

However, what worried me was that the page said that my computer had failed the test because they could still ping it. The site said that this is a security hole. Can I close this? I can't any mention of it in the documentation.

Also, is file sharing automatically on in Ubuntu?

Many thanks, as always,

Charlie

---

### Post by sayakb on 2008-06-01
Ubuntu does not share file with Windows networks unless equipped with Samba. Also, reconfigure firestarter. Open preferences and enable ICMP filtering.

---

### Post by Charlie Chick on 2008-06-01
Thanks for the advice. I'll test it out next week.

Charlie

---

### Post by durand on 2008-06-01
Aren't all networked computers supposed to be pingable?

---

### Post by mcduck on 2008-06-01
> **durand said:**
> Aren't all networked computers supposed to be pingable?

By network standards, yes.

Blocking ICMP ping is breaking standards, and not necessarily even very useful. But some people prefer hiding their computers instead of simply keeping all ports closed. This way possible attackers might think that there is no computer in your IP address (unless they happen to already know that there is one, in which case hiding the machine probably only makes them even more interested in gaining access..)

The only real benefit you might gain from blocking ICMP is that ICMP messages (and ping) can be used for DoS-attacks, so if you need to protect your machine from such risks blocking ping is the easy way. Of course there are better ways to do it as well..

---

### Post by durand on 2008-06-01
Do people really get DoSed at airports? :S

---

### Post by sayakb on 2008-06-01
> **durand said:**
> Do people really get DoSed at airports? :S

Not quite, I guess :) 
There is not much of a reason to use Firestarter here. I use it since I use my computer within a local area network, and I wan't to stop data sending to Packet capture apps (WinPCap) apps..

---

### Post by durand on 2008-06-01
Oh right, that makes more sense :D

---

