---
title: "Block Port - Won't open in Ubuntu"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by coreyxjessica on 2008-07-27
I opened the ports 6881-6889 in my router's setup and I allowed an inbound rule for bittorrent which opens those ports. I set the source to everyone and I don't know if I should have. No matter what I can't get the port to open. It works fine on XP, no problem at all. I have this problem in Ubuntu and OS X. Don't forward me to another post, I've literally looked through them all. Can anyone help?

---

### Post by neurostu on 2008-07-27
You can try installing Firestarter, then in firestarter you can open the ports you need...

---

### Post by Vivaldi Gloria on 2008-07-27
> **coreyxjessica said:**
> I opened the ports 6881-6889 in my router's setup and I allowed an inbound rule for bittorrent which opens those ports. I set the source to everyone and I don't know if I should have. No matter what I can't get the port to open. It works fine on XP, no problem at all. I have this problem in Ubuntu and OS X. Don't forward me to another post, I've literally looked through them all. Can anyone help?

Different torrent programs use different ports. Have you looked into which ports does it use?

---

### Post by Vivaldi Gloria on 2008-07-27
> **neurostu said:**
> You can try installing Firestarter, then in firestarter you can open the ports you need...

I disagree.

In default ubuntu install firewall is not working and no ports are monitored. It's not needed because there is no program listening to any port.

So he can not open any more ports with firestarter (or ufw) as they are already open.

---

### Post by neurostu on 2008-07-27
> **Vivaldi Gloria said:**
> I disagree.

In default ubuntu install firewall is not working and no ports are monitored. It's not needed because there is no program listening to any port.

So he can not open any more ports with firestarter (or ufw) as they are already open.

I was under the impression that all ports in Ubuntu are closed until a program specifically opens them.

Firestart IS NOT a firewall, it is simply a GUI frontend for the firewall that is installed and running in ubuntu.

---

### Post by Vivaldi Gloria on 2008-07-27
> **neurostu said:**
> I was under the impression that all ports in Ubuntu are closed until a program specifically opens them.

Nope. Every port is open. But it's secure since no program is listening. 

> **neurostu said:**
> Firestart IS NOT a firewall, it is simply a GUI frontend for the firewall that is installed and running in ubuntu.

Sure. Actually ubuntu comes with ufw which is a nice frontend. It's not gui but still very easy to use. See

```
man ufw 
```

for more info. 

For example, I can use amule P2P program and get a high id which shows that the ports it use are open but

```
vivaldi@narval:~$ sudo ufw status
Firewall not loaded
```

So the op has nothing to change with ubuntu settings. It's all about his router port forwarding & router firewall settings for the right ports. Either he's using the wrong ports or making a mistake in one of nat or firewall settings of the router.

---

