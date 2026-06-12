---
title: "Setting static IP with a Linksys WRT54GS router"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Linux_noob616 on 2008-11-30
I'm having trouble setting up a static IP.

That is. I have no idea how to do it haha:)

I got all the information on aMSN from portforward.com

But i've no idea how to set up a static IP at all (let alone Ubuntu..)

So could someone please explain to me how to get this working?

If it means anything i use AT&T DSL that uses PPPoE (only mentioning because it's not DHCP. i don't think anyway)

---

### Post by Gannon8 on 2008-11-30
There are some tutorials online that I followed and got working... Let me see if I can dig one up.
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

---

### Post by Linux_noob616 on 2008-11-30
I'd like to do it the GUI way if i could.

But do i just use this information?

```
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

---

### Post by newbee70 on 2008-11-30
> **Linux_noob616 said:**
> I'm having trouble setting up a static IP.

That is. I have no idea how to do it haha:)

I got all the information on aMSN from portforward.com

But i've no idea how to set up a static IP at all (let alone Ubuntu..)

So could someone please explain to me how to get this working?

If it means anything i use AT&T DSL that uses PPPoE (only mentioning because it's not DHCP. i don't think anyway)


make sure you get your ip address, gateway, subnet mask, dns primary and secondary, from your isp.

in firefox type in 192.168.1.1 in the address bar, and hit enter. this will bring up your router: use the user name and password for your router.

do not do this wireless use a cable if your on a laptop.


the wgrt54G series is menu setup friendly.

why not setup your router as dhcp and your computer as dhcp. then the oly spot you have to worry about is your router.

---

### Post by Gannon8 on 2008-11-30
Most of it should be OK except the address. Change it to something lower than 100 (but not 0 or 1). I have mine on 5.

---

### Post by Linux_noob616 on 2008-11-30
Alright so i need to call my ISP. thats were i was getting confused.

Alright. Probably costs for a static IP doesn't it?

---

### Post by Linux_noob616 on 2008-11-30
> **Gannon8 said:**
> Most of it should be OK except the address. Change it to something lower than 100 (but not 0 or 1). I have mine on 5.

On my router it says my starting IP address is 100 though

---

### Post by newbee70 on 2008-11-30
> **Linux_noob616 said:**
> Alright so i need to call my ISP. thats were i was getting confused.

Alright. Probably costs for a static IP doesn't it?

I pay extra for a static address, but then I'm out in the sticks. in the cities they may give you a dedicated ip.

can you connect to the internet through you dsl modem without the router in line?

---

### Post by Linux_noob616 on 2008-11-30
Yes i can, I can connect with the router, But aMSN and P2P programs are as slow as dirt

---

### Post by newbee70 on 2008-11-30
> **Linux_noob616 said:**
> Yes i can, I can connect with the router, But aMSN and P2P programs are as slow as dirt

if you leave the router out, and go straight through th modem are the programs still slow?

---

### Post by Linux_noob616 on 2008-11-30
Nope.

I know my issue is port forwarding, But i believe i need a static IP for that.

Cause when i set it up otherwise i still get "You're firewalled"

---

### Post by newbee70 on 2008-11-30
> **Linux_noob616 said:**
> Nope.

I know my issue is port forwarding, But i believe i need a static IP for that.

Cause when i set it up otherwise i still get "You're firewalled"

it has been years since I set my router up but I believe you can port forward on a dhcp system Just tell the router what software you want forwarded. "I think that is the way it was". look at your routers menu's
it will tell you.

but don't hold me to that,

---

### Post by Linux_noob616 on 2008-11-30
Well thats what i thought. But unless i'm putting the wrong three digit number at the end for IP. it should be working =/

---

### Post by newbee70 on 2008-11-30
> **Gannon8 said:**
> There are some tutorials online that I followed and got working... Let me see if I can dig one up.
[http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

if you right click on your network interface icon "upper right on upper toolbar. and then click on the information icon. what does it tell you?

---

### Post by chrisod on 2008-11-30
You shouldn't need a static IP address to port forward for games. The router should keep track of which machine it forwards to. If not, it is simple to set up a single static IP address for your game machine. This has nothing to do with your ISP. The game sever will get your public IP address every time you connect. It does not matter if it changes. 

Log into your router. Somewhere in the menu you'll see an option to exclude an address from the DHCP pool. Pick one within the range (that isn't already assigned to another machine on your network) and exclude it. Then go into the network set up on on the game machine and configure it for a static IP with the IP address that you just excluded from the IP pool.

Click System, the Preferences, then Network. Select the network, enter your root password, deselect "enable roaming mode" if necessary, and edit the properties of the connection. Change it to a static IP address, and enter the IP address. You may also need to enter to DNS servers and gateway server from your network set up.

That should do it.

---

