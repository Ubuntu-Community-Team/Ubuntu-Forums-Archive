---
title: "Xbox networking and internet via Laptop"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by gladstone on 2008-08-10
I have my xbox networked as so:

Crossover cable to/from laptop/xbox
xbox network settings as:
```

address 192.168.2.2
netmask 255.255.255.0
gateway 192.168.2.1

```
Network settings on the Laptop are as follows:
```
#Wired (Setup for XBOX share)
auto eth0
iface eth0 inet static
address 192.168.2.1
netmask 255.255.255.0
gateway 192.168.1.2

#Wireless
auto eth1
iface eth1 inet static
address 192.168.1.2
gateway 192.168.1.1
netmask 255.255.255.0
```

FTP/SAMBA works fine, but I was wondering if there is a way of giving internet access to the xbox from this setup? I have tried setting the gateway of the xbox to 192.168.1.1 (my router) and have experimented with network bridging (on Linux) but didn't get very far.

---

### Post by nicedude on 2008-08-11
I would recommend getting a $40 netgear or linksys router then plugging both up to it and go from there, maybe you already have one ( not sure but you are obviously using Wifi for internet, but heck that could be your neighbors router :-) ) If you do have one just use wire from Xbox to router and Laptop to router via wire or wifi and you would be networked and allow for Xbox internet. 

Otherwise my guess is you will have to figure out if you can bridge it. 

I have an old xbox I keep meaning to do up myself, but just haven't sat down to do it yet. I am gonna use the hardware rewrite the firmware method so it takes a couple solder connections and some chip flashing but gives you a pure linux xbox and you can then use any hard drive or even 2 hard drives :-) .


nicedude

---

### Post by gladstone on 2008-08-11
Hey there,

Sorry, I should have been a bit more specific. Yes, I do have a wireless router that I use for internet on my laptop.

I have, as you rightly say, used a wire from the Xbox to the router and connected to the internet/networked fine from it. This is how I'm currently updating XBMC.

My router is in another part of the house and for convienance, I'd like to be able to connect the Xbox up to my laptop with internet wirelessly, rather than having a long ethernet cable trawled across the house :)

Yeah, I agree bridging is probably the way to do it, but I didn't find any n00b guides for Linux bridging ;)

You should really have a go at modding your xbox - it's well worth it! I went the *cheap* way out and softmodded mine (you can actually have a read about it on [my blog](http://h2oz7v.shockv2.com/consoles/xbox-modding/) if you like!) and haven't looked back since! XBMC is a brilliant bit of engineering.

---

### Post by CGorman68 on 2008-08-31
A little off topic...  Thought you guys might be able to help anyway.

I'm connected to the internet through a usb wireless network adapter and, in Windows, had always used a crossover cable to connect to XBMC.

Now when I plug in the crossover cable I lose my wireless connection and am unable to access the internet.  

Any tips on how to use both the crossover cable and my wireless connection?  Very new to Ubuntu (about two hours!), any help would be greatly appreciated.

---

### Post by CGorman68 on 2008-08-31
Obligatory bump ;)

---

### Post by PriceChild on 2008-08-31
Found [http://www.linux.com/feature/133849](http://www.linux.com/feature/133849) a while ago which might be helpful.

---

### Post by gladstone on 2008-09-01
Thanks PriceChild, that does look useful. @CGorman68: Let us know if you get anywhere with this as it sounds like your after the same thing as me.

---

### Post by billgoldberg on 2008-09-01
Can't the xbox go wireless with some sort of adapter?

[flamebait]My PS3 does that out of the box. [/flamebait]

---

