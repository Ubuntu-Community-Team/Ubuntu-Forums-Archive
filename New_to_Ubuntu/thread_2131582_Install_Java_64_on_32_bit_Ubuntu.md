---
title: "Install Java 64 on 32 bit Ubuntu?"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by caleb12134 on 2013-04-02
I have  64 bit machine and when i got it it had 32 bit ubuntu?? and now my minecraft server cannot use more than 2 gigs ram and its gettin really popular. i could use a VM or something. i also have multiple hard drives so could i like have another install of ubuntu on the machine?? please help and if possible i would choose a route that keeps me from having to uninstall ubuntu server!

---

### Post by Cheesemill on 2013-04-02
I'm afraid there is no way of running 64-bit applications on a 32-bit OS or upgrading a 32-bit OS to a 64-bit OS.

You're going to have to install the 64-bit version of Ubuntu Server and set up everything from scratch, though this shouldn't take more than an hour or so.

---

### Post by caleb12134 on 2013-04-02
No. there has to be another way. :( how can i allocate it more ram

---

### Post by ManamiVixen on 2013-04-02
Sorry, but Java32 is maxed at 2GB. If you need more, YOU HAVE TO install the 64bit Ubuntu to get Java64 and more than 2GB. It's a physical limitation of the 32Bit Arch.
Also be aware 64bit requires twice the ram to do the same thing. So if you allocate 4GB to Java64, it is the same amount of space as compared to giving 2GB to Java32. That is because 64bits take up twice the space as 32bit in memory.  So you need at least 6-8GB of ram in your computer to run Java64 at a level that secedes Java32 in terms of more memory, preferably 12GB or more gives best performance.

---

### Post by caleb12134 on 2013-04-02
k. how can i install over the current install??? and will the IP of the machine change. i need it to stay at 192.168.1.8! and external 71.191.206.154?? Thanks

---

### Post by ManamiVixen on 2013-04-02
Yes you can install over and yes the IP should stay the same. Each household gets an IP and is unique to that house so all computers will keep the same IP. But if you move somewhere else, your IP changes.

---

### Post by Cheesemill on 2013-04-02
> **ManamiVixen said:**
> Also be aware 64bit requires twice the ram to do the same thing. So if you allocate 4GB to Java64, it is the same amount of space as compared to giving 2GB to Java32. That is because 64bits take up twice the space as 32bit in memory.

Where did you get that idea from?

A 64-bit application will use slighly more memory than its 32-bit version, but nowhere near double.
The actual amount will vary from application to application but a good estimate is probably around the 10% mark.

This is due to some of the memory addressing pointers in the application being 64-bits rather than 32-bits wide, but this by no way means that a 64-bit application will use double the RAM.

---

### Post by Horbo on 2013-04-02
> **ManamiVixen said:**
> Sorry, but Java32 is maxed at 2GB. If you need more, YOU HAVE TO install the 64bit Ubuntu to get Java64 and more than 2GB. It's a physical limitation of the 32Bit Arch.
Also be aware 64bit requires twice the ram to do the same thing. So if you allocate 4GB to Java64, it is the same amount of space as compared to giving 2GB to Java32. That is because 64bits take up twice the space as 32bit in memory.  So you need at least 6-8GB of ram in your computer to run Java64 at a level that secedes Java32 in terms of more memory, preferably 12GB or more gives best performance.
Whoa, this is dead wrong, and horribly misleading for newbs who don't know better.


OP, if you have 64 bit hardware (almost a certainty) then unless you have a VERY good reason for doing so, you shouldn't have installed 32 bit Ubuntu in the first place.  Install 64 bit Ubuntu.

---

### Post by Cheesemill on 2013-04-02
> **caleb12134 said:**
> and will the IP of the machine change. i need it to stay at 192.168.1.8! and external 71.191.206.154?? Thanks

That depends.

How did you set up the static internal IP on your server in the first place?
If you did it using an address reservation in your routers DHCP settings then it should stay the same, as the MAC address of your server won't have changed.
If your server doesn't use DHCP and instead you edited the network configuration files to give it it's static IP you'll have to do the same again.

As to your external IP, does your ISP provide you with a fixed IP address (most ISPs will charge extra for this)?
If you have a fixed external IP address then it will never change, but if your ISP provides you with a DHCP assigned address then this can change at any time whether you reinstall your server or not.

---

### Post by Paqman on 2013-04-02
> **ManamiVixen said:**
> Yes you can install over and yes the IP should stay the same. Each household gets an IP and is unique to that house so all computers will keep the same IP. But if you move somewhere else, your IP changes.

Er, what? You can't be certain of that at all. Static IPs are pretty unusual for home broadband subscriptions. 

The internal address (192.168.1.8) is assigned by your own router, if that's using dhcp it'll probably change whenever you disconnect. If it's been reserved then it'll always be the same unless the MAC address changes (eg: you change your network card).

The external IP address (71.191.206.154) can also either be static or dynamic. Most ISPs dynamically assign IPs to subscribers, so your IP could change at any time. You'd need to contact your ISP to see if you had been given a static IP. You may need to pay extra for one, but if you're hosting a server it's not a bad idea.

---

### Post by ManamiVixen on 2013-04-02
Paqman, yeah mine is static. Never thought it was strange.

Also, as for the 64Bit thing, I've seen articles all over the Internet about that. that 64Bit needs about twice as much ram to get a job done.

---

### Post by Paqman on 2013-04-02
> **ManamiVixen said:**
> 
Also, as for the 64Bit thing, I've seen articles all over the Internet about that. that 64Bit needs about twice as much ram to get a job done.

Well, whoever wrote that article was wrong. As Cheesemill mentions above, 64-bit uses slightly more RAM, but nothing like twice as much.

---

