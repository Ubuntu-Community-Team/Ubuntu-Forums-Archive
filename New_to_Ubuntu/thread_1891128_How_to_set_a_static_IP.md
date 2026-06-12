---
title: "How to set a static IP?"
date: 2011-12-04
forum: New to Ubuntu
---

### Post by burnsmicro on 2011-12-04
There are a ton of postings on this topic. But it seems to be evolving.

I used "[Make **Ubuntu** Server 11.04 use a **static IP** address | parabing!]("http://parabing.com/2011/05/07/make-ubuntu-server-11-04-use-a-static-ip-address/")["]("http://parabing.com/2011/05/07/make-ubuntu-server-11-04-use-a-static-ip-address/") as a reference. It all seems quite straight forward. Except I cannot get it to work.

When I go to stop and start eth0, my Ubuntu-11.10 PC cannot recognize eth0:

```
~$ sudo ifdown eth0
ifdown: interface eth0 not configured

```Yet eth0 shows up with ifconfig:

```
~$ sudo ifconfig
**[COLOR=Red]eth0[/COLOR]**      Link encap:Ethernet  HWaddr 14:da:e9:ef:47:5c  
          inet addr:192.168.2.103  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::16da:e9ff:feef:475c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11759 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3174879 (3.1 MB)  TX bytes:501480 (501.4 KB)
          Interrupt:41 Base address:0xa000 

lo        Link encap:Local Loopback
             :

```What am I missing?

Thanks,

RF

---

### Post by N00b-un-2 on 2011-12-04
In my experience, it's almost impossible to get a static IP address configured on the computer's side of things.  You can do it, but you'll run into issues with not having internet access and such.  You're best bet (assuming that you're behind a router) is to assign a static IP address to your NIC's mac address via your router's DHCP settings menu.  The details vary from router to router, but the concept is the same.
However, if you are NOT behind a router and you're trying to grab a static IP address from your modem you're pretty much SOL.  You would have to lease the static IP from your ISP which costs $$$.

---

### Post by burnsmicro on 2011-12-04
Right on!

After wasting hours failing to set a static IP on the PC, I did it in minutes on the router.

Thanks

RF

---

### Post by docbop on 2011-12-05
Do you have the Network Tools install you could do it with that interface.  If you want to manually do it a little google shows.

[dhcp-to-a-static-ip-address]("http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html")

---

### Post by Dennis N on 2011-12-05
Setting a static IP can be also done in Network Manager by editing the IPv4 connection method and then entering your desired static IP, netmask and gateway address, but looks like you have found another way.

---

### Post by realstarman on 2011-12-05
Settng it in the router has the advantage of setting things correctly and consistently at one single spot.

It is also possible to set the static IP address in your PC, but then you need to make sure that you set the network mask, gateway and dns server correctly as well. Also, make sure that the address you assign matches with the address and network mask set on the router.
The easiest way is to have everything set dynamically, then check the settings with ifconfig and then set things manually the same way.

In addition, you should set a range for dynamic adresses on the router and use an address outside this range for your static one.
Example:
Network mask is 255.255.255.0. 
Router has an address of 192.168.0.1, range for dynamic IP addresse starts with 192.168.0.100.
Use a static IP address within 192.168.0.2 and 192.168.0.99.

---

### Post by mastablasta on 2011-12-05
interesting... i thought the ISP had to asign the static address. 

I had dynamic one and had to make a request to their tech support. sure enough in a couple of hours i had a static IP.

---

### Post by N00b-un-2 on 2011-12-05
I am not disagreeing with anyone here.  It is very easy to manually set a static IP address on Ubuntu, both via the terminal or by using the nm-applet or wicd or any other manner of configuring your network connection.  

**However...**

That being said, in my experience in the past many routers are computer agnostic devices that are relatively inflexible and assume that all incoming connections are DHCP connections.  Typically what will happen on a small home network behind a route when you assign the static IP address on the computer itself will behave properly.  It will use all local services like samba, nfs, ssh, vnc, you name it... everything will work fine.  However, the router will not properly dynamically assign external services (read: internet connection) because it can not "see" the computer.  Mileage may vary from one network to the next depending on the router, but in my experience when setting up a home network, if you want to assign static IPs to devices, the best practice is to do so using the router.

The only thing that I do not like about using the router is that especially when we're talking about a wireless router, it does create a potential security threat, but in all honesty how likely is it that someone is going to hack into your home network, and if they do they're probably just going to use your wifi to download torrents, and not bother trying to hack into your files (assuming you're smart enough to password protect your computers).

Truth be told, I can pick up roughly a dozen wireless signals from my neighbors and I am dumbfounded to find that half of them don't even have a secured wireless network.  So how likely is it that you're going to encounter another Linux hacker ON YOUR STREET?

---

### Post by N00b-un-2 on 2011-12-05
> **mastablasta said:**
> interesting... i thought the ISP had to asign the static address. 

I had dynamic one and had to make a request to their tech support. sure enough in a couple of hours i had a static IP.

You are correct, your ISP does need to assign your global IP address.  He's talking about setting a static IP for a home network for things like file sharing (lots of other reasons why but that is very common).  
You're very lucky that they were willing to just give you a static IP.  My ISP charges quite a bit extra to lease the static IP address, because they know that anyone using  static IP address is likely doing one of two things
A) hosting a web server
B) hosting a game server
and they charge a premium for the substantial increase in bandwidth usage.

---

### Post by The Cog on 2011-12-05
> **burnsmicro said:**
> 
I used "[Make **Ubuntu** Server 11.04 use a **static IP** address | parabing!]("http://parabing.com/2011/05/07/make-ubuntu-server-11-04-use-a-static-ip-address/")["]("http://parabing.com/2011/05/07/make-ubuntu-server-11-04-use-a-static-ip-address/") as a reference. It all seems quite straight forward. Except I cannot get it to work.

Those instructions look tight to me. At least, the configuration files look right. And your ifconfig shows that the intereface is configured. I'm not sure if ifdown and ifup will work with that config though (although the instructions say they will) and I'm not near a machine I can try it on at the moment.

Have you actually tried the networking? 
If it's not working, you can try these things:

Try to ping the router - you don't say what address that is.

Check that your default route is installed. Look at the output of the command **route -n** .

Check that you can reach the internet - ping 8.8.8.8 should work.

---

### Post by oldfred on 2011-12-05
You were using this:

> inet addr:192.168.2.103

And that is almost always inside the range of dynamic address already allocated.
You cannot use one of those.

---

### Post by Zill on 2011-12-05
I always use static IPs for my LAN eth0 connections.  It is simply a matter of configuring one file... /etc/network/interfaces.

The instructions given in the OP's link seem fine to me.  You can also tweak your DNS settings if necessary as described in the link.

---

### Post by burnsmicro on 2011-12-11
> **oldfred said:**
> You were using this:
[INDENT] 192.168.2.103
[/INDENT]And that is almost always inside the range of dynamic address already allocated.
You cannot use one of those.

The problem is my router will not allow me to allocate a static IP outside the range specified for the allocation of IPs.

The result is the router does allocate the static IP and all PCs can access the Ubu-11 PC on the network. But, the Ubu-11 PC cannot access shared files or printers on Windows PCs on the network.

---

### Post by Zill on 2011-12-11
burnsmicro:  In my experience most routers are highly configurable and you should be able to change most parameters.  All you need to know is how? ;-)

The instruction manual you received with the router should explain this but if it doesn't contain everything then it should be possible to download a full version from the manufacturer's website.

BTW, which make/model of router do you have?  What is the "gateway" IP address for your router and what is your preferred static IP address for the Ubuntu PC?  Do you have any other PCs connected via DHCP and, if so, what range of IP addresses is currently defined in the router?

---

