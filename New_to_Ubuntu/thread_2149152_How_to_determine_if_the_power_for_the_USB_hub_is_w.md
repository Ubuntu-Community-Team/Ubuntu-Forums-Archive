---
title: "How to determine if the power for the USB hub is working?"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-05-27
I have plugged a 5 volt 2.2 amp wall adapter power supply into a 4 port usb hub. Is there a Linux command or sequence that will show whether the device is "seeing" the 5 volts? FYI, the 1 gig thumb drive is "seen" on my desktop. It can be mounted, opened and unmounted. But is the hub powered up?

---

### Post by squakie on 2013-05-28
Isn't there an status led for power?  Every externally powered USB hub I have had always had a led that lit when the power adapter was plugged in.  If you have the correct ac adapter (proper voltage, ampherage and tip polarity) you can just put a volt meter across tip and shield a ngd see what the voltage shows.  If it shows correctly then it should be working unless there is an internal problem in your hub.

Just remember that if the hub does not have an external power source then the total load for all ports on the hub cannot exceed the load for the host USB port - I'm not positive on it, but I think it's something like 500 milliamps in total.

Oh, and a dumb question - this is true power adapter and not one with a USB plug on it, right?  If you don't know you can't take something like a charging adapter and  Usb cab[SIZE=2]le like used on a lot of tablets, etc., into the hub.[/SIZE]

---

### Post by sanderj on 2013-05-28
> **squakie said:**
> 
Oh, and a dumb question - this is true power adapter and not one with a USB plug on it, right?  If you don't know you can't take something like a charging adapter and  Usb cab[SIZE=2]le like used on a lot of tablets, etc., into the hub.[/SIZE]

I would say that's the most important question. If the hub isn't meant for an external power adapter, the OP is connecting two power sources (from the PC and from the power adapter) to eachother, which is a big no-no. Electrical engineers call this a ... short circuit. You will get a lot of power dissipation in the different USB powers and/or within the USB hub. That's bad.

---

### Post by squakie on 2013-05-28
yeah - that's why i decided to ask - sometimes people do bad things out of  ignorance.  in this case, depending on the hub - damage to the host usb port is possible as well.  shorting a 5 to 10 dollar hub can be really  bad. ; )

---

### Post by Paqman on 2013-05-28
If you've got it plugged into a computer it'll be getting 5VDC from the motherboard. What is it you're worried about? Do you want to plug a lot of devices into the hub and have the little power supply keep the voltage up? Best way to find that out is to try it tbh. While it's plugged into the mobo you're always going to see 5VDC on the appropriate pin, the only way to test its response under load is to, well, put a load on it.

---

### Post by sanderj on 2013-05-28
OK: the OP is not reacting, so I'm unsubscribing from this thread.

---

### Post by Paqman on 2013-05-28
> **sanderj said:**
> If the hub isn't meant for an external power adapter, the OP is connecting two power sources (from the PC and from the power adapter) to eachother, which is a big no-no. Electrical engineers call this a ... short circuit.

A short circuit is different, what you're doing here is applying a couple of voltages in parallel. Not a great idea, but easily fixed by cutting the 5VDC pin/wire from the cable going to the computer. If your little power supply is working then you'd have made your own powered hub.

If you're at all unsure what you're doing, just go buy a powered hub. They aren't expensive, you can get em on Ebay for peanuts.

---

### Post by Mark_in_Hollywood on 2013-05-28
From Squakie:

"Isn't there an status led for power? Every externally powered USB hub I have had always had a led that lit when the power adapter was plugged in." [COLOR="#FF0000"]Yes, the hub has an LED. But that LED is lit as the hub is plugged into the 'puter (motherboard) via the 'puter's USB port.[/COLOR]

From sanderj:

"call this a ... short circuit." - [COLOR="#FF0000"]No sir, it's two power sources in parallel.[/COLOR]

From Paqman:

"the only way to test its response under load is to, well, put a load on it." -[COLOR="#FF0000"] So in answer to my question (OP), there is no Linux command or app which shows loads on various devices.[/COLOR]

From Paqman:

". . . voltages in parallel. Not a great idea, but easily fixed by cutting the 5VDC pin/wire from the cable going to the computer." [COLOR="#FF0000"]- What I expected here, at this post (my thread) is whether there is a Linux/Unix app or command (like: lsusb) that shows whether a device is seeing it's designed volts/amps. Your idea about cutting cables, etc. defeats the whole purpose. It may have it's spec'd power, but so what? if the 'puter as a whole cannot "see" it.[/COLOR]

---

### Post by Paqman on 2013-05-28
> **Mark_in_Hollywood said:**
> 
[COLOR="#FF0000"] So in answer to my question (OP), there is no Linux command or app which shows loads on various devices.[/COLOR]


Not AFAIK. Devices do have to report their maximum power to the USB hub they're attached to, but this doesn't tell you how much they're actually drawing at any particular time. However, if a bus-powered device powers up and you can see it when you do lsusb then you can be sure it is seeing the 5VDC.

---

### Post by squakie on 2013-05-28
If all you want is that single answer, then the vote is no - you're out of luck.  And next time be aware we are trying to help and don't want you to mess up your computer.  There's no reason to get a little snippy, and future help may not be forthcoming.

---

### Post by squakie on 2013-05-28
And I should add - if the adapter is not working, do not put a total load on the hub ports greater than what the host port can support - like I said I think it's 500 milliamps.

---

### Post by squakie on 2013-05-28
Also - what happens if you have no USB cables - including the host - plugged into the hub and the plug in the adapter?  Hopefully the led should come on when you plug in the power supply - this would indicate the hub is getting external power since nothing else is plugged into the hub.  Remove everything from the hub then plug in the power supply.

---

### Post by Mark_in_Hollywood on 2013-05-29
Well, if I could withdraw this post, I would. Now I have seen that without the external wall adapter plugged into the hub that the hub's LED stays on, even when the computer is shutdown. Go Figure! and when the wall adapter is plugged into the hub and the computer is off, then the hub's LED is off. Go Figure!

So, gents, please, it's time to quit this and if I could mark this as "solved" I would. By the bye: as there are linux commands to show the various processes, e.g., top and iotop, I find it passing strange that there is no way to know how much current is coursing through a hub. But as I said above, mox-nix.

---

