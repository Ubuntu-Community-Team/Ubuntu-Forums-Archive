---
title: "Basic Hardware Requirement"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by nikhilgoyal on 2008-05-05
Hello everyone:KS
I want to practice networking and system security at my home using at least 3-4 computers. 

What I want to know is what should be the basic system requirement   in terms of memory, processor type, motherboard etc that should have enough power to run all the available Linux flavors and also windows Xp.

Please also tell about any type of routers or any other networking equipment required. (I am just a starter, so don't know much)

Is there any other way I can practice with minimum investment.

---

### Post by phr0ze on 2008-05-05
For a router: get the linksys WRT-54GL, then load a 3rd party firmware on it such as tomato or dd-wrt.

For a system, I'd get 2 GB of ram, although 1GB would work and I would make sure you have a large drive to fit all the OSs. Install XP first, then your other distros. 

CPU isn't as important, but I prefer the Core2Duos.
Use nvidia geforce for a gfx card.

for more fun, make sure you get 2 network ports in it. You can buy an extra for $10-$20.

---

### Post by Xiong Chiamiov on 2008-05-05
When you say "all the available Linux flavors", do you realize just how much that spans?

If you get computers that meet [the minimum reqs of XP]("http://support.microsoft.com/kb/314865"), then you'll be able to run all the common "modern" distros just fine.  If you're just wanting to be able to run Linux, well, let me tell you that I'm buying an old Toshiba laptop from a guy off Craigslist with 8 megs of RAM and a 90MHz Pentium to run Damn Small Linux, DeLi Linux or NetBSD off of.  There are some people who would say that if you've got 64 megs of RAM, you're more than comfortable.

EDIT: I'm amused greatly at recommending 2 gigs of RAM for Linux.  What the hell is that about?  Oh, and thumbs up to DD-WRT on a Linksys WRT54-GL.  Make sure you get the GL model, not the G.

---

### Post by zvbxrpl on 2008-05-05
If you're buying a lot of new kit and you're planning a (part-)wireless network, you might want to get hold of a wireless ethernet bridge, like this one:

[http://www.buffalo-technology.com/pr...net-converter/](http://www.buffalo-technology.com/pr...net-converter/)

What this device does is to convert your wired ethernet connection into a wireless one. It's configured via a web interface, so it doesn't matter which OS you use. I own one of these and they're great - you can plug up to 4 computers into them. The signal is much more powerful as well.

Wireless adapters are the bain of Ubuntu and Linux generally, and a wireless bridge is by far and away the easiest solution.  Incidentally, if you are looking for a router, the WRT54GL is OK but is getting a bit old now.  The Buffalo WHR-HP-G54DD is a lot more powerful, and you can even buy a unit with DD-WRT preinstalled, saving you the hassle of having to flash the firmware yourself:

[http://www.buffalo-technology.com/products/wireless/wireless-g-mimo-performance/wireless-g-mimo-performance-router-with-dd-wrt/](http://www.buffalo-technology.com/products/wireless/wireless-g-mimo-performance/wireless-g-mimo-performance-router-with-dd-wrt/)

If you really do want to buy a wireless adapter (e.g. PCI or USB) instead of a bridge though, avoid Buffalo as they tend to use Broadcom chipsets which are poorly supported in Linux.  Try here for Linux-friendly wireless adapters (a UK site, but you should be able to find the same devices elsewhere):

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

Good luck!

---

### Post by Xiong Chiamiov on 2008-05-05
Your first link got cut off; [here]("http://www.buffalo-technology.com/products/wireless/wireless-g-mimo-performance/wireless-g-mimo-performance-ethernet-converter/") is what I think you were trying to link to.

The 3rd link has great wireless products for Linux.  If you're in the US, I'd recommend buying them from Newegg.

---

### Post by nikhilgoyal on 2008-05-05
First of all I would like to thank everyone for such a fast reply.:lolflag:

By all linux flavors I meant the common one like Ubuntu, fedora, dsl, red hat, slax and all that, I know there are a hell lot of different flavors I cannot even imagine.

Then if I purchase some hardware for linux only, will it not be compatible with winxp or vice-versa.

Right now I have one pc ---> P4, 512MB ram, 80GG HDD,onboard sound and video(64MB), 4 usb, no lan card/Ethernet card (my router's connected via usb)
Please recommend any changes in this config.

As for routers I'm still confused like how many will I need for a part wireless network, or I'll still be needing any other equipment to support my network for 4-5 computers.

---

### Post by nikhilgoyal on 2008-05-05
someone please help ....

---

### Post by thisiam on 2008-05-05
> **nikhilgoyal said:**
> Hello everyone:KS
I want to practice networking and system security
 

> **nikhilgoyal said:**
> Is there any other way I can practice with minimum investment.


Get a laptop and go sit at a coffee shop for while, practicing network security would be fun there.

---

### Post by nikhilgoyal on 2008-05-06
but how can I practise with only one laptop ???
there are no networks..

---

### Post by subzero316 on 2008-05-06
the pc you have is enough get a few more of simliar configs.

For networking 
1) Wifi router(Linksys Wrg***)
2)ADSL modem(for ur internet connection)
now a days wifi routers come with built in adsl modem get that
3)from wired connections u get built in Nic cards now a days if not get for each system
4)cables(crossover and straight through)

---

### Post by nikhilgoyal on 2008-05-06
> **subzero316 said:**
> the pc you have is enough get a few more of simliar configs.

For networking 
1) Wifi router(Linksys Wrg***)
2)ADSL modem(for ur internet connection)
now a days wifi routers come with built in adsl modem get that
3)from wired connections u get built in Nic cards now a days if not get for each system
4)cables(crossover and straight through)

I have a adsl modem, my isp provided it, but its simple one  and has no extra features.
Do I need lan/ethernet card for all my systems.
can you give some more information on Nic cards.

---

### Post by subzero316 on 2008-05-06
> **nikhilgoyal said:**
> I have a adsl modem, my isp provided it, but its simple one  and has no extra features.
Do I need lan/ethernet card for all my systems.
can you give some more information on Nic cards.


Nic cards are Ethernet cards (diff name thats it). yes youll need ethernet card for every system. Dont worry all the pc`s or laptops come with them now a days.

Since you have a ADSL modem(simple one is gud enough you wont have to do anyting with it) jus get a Linksys Wifi Router.

---

### Post by Xiong Chiamiov on 2008-05-06
> **thisiam said:**
> Get a laptop and go sit at a coffee shop for while, practicing network security would be fun there.

> **nikhilgoyal said:**
> but how can I practise with only one laptop ???
there are no networks..

What he was trying to say was that you should go to a coffee shop that has a wireless hotspot and cut your teeth on snooping into other people's traffic.

---

### Post by nikhilgoyal on 2008-05-06
> **Xiong Chiamiov said:**
> What he was trying to say was that you should go to a coffee shop that has a wireless hotspot and cut your teeth on snooping into other people's traffic.

Now I get it...
:)

---

