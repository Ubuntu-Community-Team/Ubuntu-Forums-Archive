---
title: "TL-WN321G...wireless disconnects every so often, bad wifi adapter to blame?"
date: 2012-06-15
forum: New to Ubuntu
---

### Post by venom104 on 2012-06-15
I am using a TL-WN321G wireless adapter...

This is my wireless driver 

```

Bus 001 Device 006: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

```

Every 5 boots or so, my device will NOT see my network's ESSID on the network list, I have to manually connect to it (ESSID is on; I've checked). Then recently my wireless connection just cuts off after a while or so...

Here is the /var/log/messages output...

[http://pastebin.com/F4Yrvcj0](http://pastebin.com/F4Yrvcj0)

Please note I had to unplug my device and reconnect it for it to get me back online.

I've also noticed that when I unplug and and replug my wireless adapter in, it is VERY hot.

Is my wireless adapter dying?

---

### Post by MG&amp;TL on 2012-06-16
> **venom104 said:**
> 
I've also noticed that when I unplug and and replug my wireless adapter in, it is VERY hot.

Is my wireless adapter dying?

I have one of those, a little white stick, right?

Without looking at the messages, my stick doesn't exhibit that behaviour, and it's never got hot. It might be worth running it on a different machine and seeing hat happens there.

---

### Post by venom104 on 2012-06-16
> **MG&TL said:**
> I have one of those, a little white stick, right?

Without looking at the messages, my stick doesn't exhibit that behaviour, and it's never got hot. It might be worth running it on a different machine and seeing hat happens there.


Well actually I believe the white stick is the version 4 model. I think I have a version 1. I've exchanged wifi adapters with my brother to see if the problem is the wireless device. I'll re comment back, but please offer more suggestions to try!

---

### Post by MG&amp;TL on 2012-06-16
> **venom104 said:**
> Well actually I believe the white stick is the version 4 model. I think I have a version 1. I've exchanged wifi adapters with my brother to see if the problem is the wireless device. I'll re comment back, but please offer more suggestions to try!

Hmm...don't suppose you could post a photo? I don't still have the packet, but I seem to recall mine being v. 1.

---

### Post by venom104 on 2012-06-16
> **MG&TL said:**
> Hmm...don't suppose you could post a photo? I don't still have the packet, but I seem to recall mine being v. 1.


I'm sorry but that isn't possible. I don't have a camera phone and I am kind of in the red this month (school started). My device is completely black, my brothers which is a version 4, is a white stick.

---

### Post by venom104 on 2012-06-19
I think I figured out the problem. Using deductive reasoning, gave my brother my wireless adapter and switched out with his. He is running windows 7, and I downloaded the driver on his computer and installed it for him. 

He was experiencing a high amount of disconnects on his network; this was isolated to the computer, nothing else in the house on the network was having a problem.

So it seems that the problem is that my wireless device just went bad. As I stated before, it gets terribly hot, so I'm guessing some integrated circuit probably blew out, and as a result, the thing overheats and loses the network connection.

I am not having a problem with his device.

---

### Post by MG&amp;TL on 2012-06-20
> **venom104 said:**
> I think I figured out the problem. Using deductive reasoning, gave my brother my wireless adapter and switched out with his. He is running windows 7, and I downloaded the driver on his computer and installed it for him. 

He was experiencing a high amount of disconnects on his network; this was isolated to the computer, nothing else in the house on the network was having a problem.

So it seems that the problem is that my wireless device just went bad. As I stated before, it gets terribly hot, so I'm guessing some integrated circuit probably blew out, and as a result, the thing overheats and loses the network connection.

I am not having a problem with his device.

Cool. Oh well, at least we know it's not Ubuntu, right? ;)

---

