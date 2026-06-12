---
title: "What's my ip address?"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by mkornig on 2011-10-29
Hi there!

Under Windows there is the command *ipconfig* to find out my own ip address. Is there something simiular under Linux?

---

### Post by CharlesA on 2011-10-29
ifconfig will show your what your ip address is.

Run it in a terminal:

```
ifconfig
```

---

### Post by roger_1960 on 2011-10-29
Hi

For your local IP address click on the network icon and select "connection information"

For external IP (of your router) go to whatismyip.com

---

### Post by BillyBoa on 2011-10-29
Right click on your connection icon, move downwards up to connection information. It's there. simpler impossible

---

### Post by mkornig on 2011-10-29
Thanks to all of you. That was quick.

*(1) ifconfig* and (2) *right clicking on the network icon *give the same result.

But strangely enough (3) whatismyip.com gives a totaly different address. Which I guess is wrong?

---

### Post by blackbird34 on 2011-10-29
look at his post :

> **roger_1960 said:**
> Hi

For your local IP address click on the network icon and select "connection information"

For external IP (of your router) go to whatismyip.com

that explains it :popcorn:

---

### Post by haqking on 2011-10-29
> **mkornig said:**
> Thanks to all of you. That was quick.

*(1) ifconfig* and (2) *right clicking on the network icon *givethe same result.

But strangely enough (3) whatismyip.com gives a totaly different address. Which I guess is wrong?

you have a LAN (local) IP address used for you local network, seen when using ifconfig etc.

Whatismyisp.com shows your WAN address, the one assigned to your external interface from your ISP, this is your address on the internet and packets are usually delivered to this which is probably a router or modem and them sent to your LAN IP address.

---

### Post by mkornig on 2011-10-29
Oh, I see.

The "external" IP address is the address of some router. NOT the IP address of my computer?

Thanks everybody.
Martin

---

### Post by haqking on 2011-10-29
> **mkornig said:**
> Oh, I see.

The "external" IP address is the address of some router. NOT the IP address of my computer.

Thanks everybody.
Martin

It is the address of your router, modem or whatever device connects you to the internet.

---

### Post by roger_1960 on 2011-10-29
Hi again

The router(or modem) sits between your computer and the internet.  It gives one address to your computer (internal LAN address) and a different one to the outside world (internet).  The outside world sees just the one address which applies to your network.  

Within your network (if you have more than one computer) your router will allocate different IP addresses to each computer, one of which is your LAN address.

---

### Post by mkornig on 2011-10-29
I'm still a bit confused.

Say someone on the Internet (outside the LAN) would like to ping my computer to see if I'm connected to the Internet. Which IP address would he need? The local or the external one? Or maybe either one could be used?

---

### Post by haqking on 2011-10-29
> **mkornig said:**
> I'm still a bit confused.

Say someone on the Internet (outside the LAN) would like to ping my computer to see if I'm connected to the Internet. Which IP address would he need? The local or the external one? Or maybe either one could be used?

They would ping your WAN IP, your LAN IP is likely to be a non-routable address using NAT something like 192.168.x.x or similar and so cant be pinged from external

---

### Post by roger_1960 on 2011-10-29
They need the external one.  Millions of computers have the same LAN addresses because most makes of router use the same limited ranges of addresses.

If you ever need to set up a web server you would need your ISP to allocate a fixed external address to your router so that it could always be found at the same address.  Normally, routers will obtain a new external address from your ISP each time they are rebooted.

If you are interested, its worth googling IPV6 to see where this is all going as the old system, IPV4 is running out of unique addresses very quickly.

---

### Post by haqking on 2011-10-29
> **roger_1960 said:**
> They need the external one.  Millions of computers have the same LAN addresses because most makes of router use the same limited ranges of addresses.

If you ever need to set up a web server you would need your ISP to allocate a fixed external address to your router so that it could always be found at the same address.  Normally, routers will obtain a new external address from your ISP each time they are rebooted.

If you are interested, its worth googling IPV6 to see where this is all going as the old system, IPV4 is running out of unique addresses very quickly.

IANA and RIR APNIC have already run out

---

### Post by mkornig on 2011-10-29
Okay. What if there were several computers in my LAN. Then each of them would have a different external (or WAN) IP address? And on each of these computers I would get a different answer from whatismyip.com?

If that's true the external IP adress given by whatismyip.com is NOT the address of some router (as somebody said earlier).

---

### Post by haqking on 2011-10-29
> **mkornig said:**
> Okay. What if there were several computers in my LAN. Then each of them would have a different external (or WAN) IP address? And on each of these computers I would get a different answer from whatismyip.com?

If that's true the external IP adress given by whatismyip.com is NOT the address of some router (as somebody said earlier).

no as stated, your LAN machines have their own addresses, your external interface has one address, the WAN address seen on whatismyisp.com

That address will change though as is it likely to be dynamic from your ISP.

yoru WAN address should be the same from all your LAN machines unless it has changed dynamically already, depends on the lease time

---

### Post by roger_1960 on 2011-10-29
Hi again

Each computer on your LAN has the same external IP address (using IPV4 - this will change when IPV6 comes in). The address given by whatsmyip is the external address of your router.  Generally you can only ping servers which have fixed external IP addresses.(or routers)

When you go on the internet via your router, it knows which PC on your LAN a packet came from (by using the LAN IP address which it allocated) and routes the reply from the web back to the same one.

We are all trying to explain the same thing here!!

---

### Post by mkornig on 2011-10-29
Just one more question: 

If my computer is on a LAN (together with one or two others). Is there a way for someone out on the internet to find out (using ping or some other tool) whether or not my computer is connected to the Internet at a given time?

---

### Post by haqking on 2011-10-29
> **mkornig said:**
> Just one more question: 

If my computer is on a LAN (together with one or two others). Is there a way for someone out on the internet to find out (using ping or some other tool) whether or not my computer is connected to the Internet at a given time?

100's of different ways.

But not from pinging your LAN IP.

I suggest you read the following links such relating to malware, firewalls and services such as Tor

No system is 100% secure when on a network or sharing data, security is best in a layered approach and with ongoing vigilence and awareness, the main security flaw in any system is PEBKAP = Problem Exists Between Keyboard And Person

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSRF, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

See below for Bodhi.Zazen's overview of Linux Security

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Then these stickies:
security stickies (5 stickies)
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

Also see about sudo and why root account is disabled by default in Ubuntu:

rootsudo (make sure you read this if you only read one thing)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are typically taken care of by your home router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here: 

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and their privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


Have fun

Regards

haqking

---

### Post by mkornig on 2011-10-30
Let me try to sum this up a little (before I declare this thread "solved"). You want to distinguish the following two:
[B]
1. LAN IP address[/B]

In a local area network (LAN) there may be one or several machines connected to a router which provides access to the Internet. Each of these machines has its own LAN IP address (aka local IP addess).

Once logged on onto one of these machines you have (at least) two ways to find out about this address:

[LIST]
[*]*ifconfig* (command to be typed in a terminal)
[*]right click on the *connection icon *(on my screen it's at the very top), then click on *connection information*
[/LIST]

[B]2. WAN IP address
[/B]
The LAN's router is identified by other machines on the Internet by its WAN IP address (aka external IP address,  WAN=wide area network). This address is different from the LAN IP addresses mentioned above. To find out about the router's WAN IP address:

[LIST]
[*]a user logged on onto a local machine may want to visit the site *whatismyip.com* (using a browser).
[/LIST]

---

### Post by haqking on 2011-10-30
> **mkornig said:**
> Let me try to sum this up a little (before I declare this thread "solved"). You want to distinguish the following two:
[B]
1. LAN IP address[/B]

In a local area network (LAN) there may be one or several machines connected to a router which provides access to the Internet. Each of these machines has its own LAN IP address (aka local IP addess).

Once logged on onto one of these machines you have (at least) two ways to find out about this address:

[LIST]
[*]*ifconfig* (command to be typed in a terminal)
[*]right click on the *connection icon *(on my screen it's at the very top), then click on *connection information*
[/LIST]

[B]2. WAN IP address
[/B]
The LAN's router is identified by other machines on the Internet by its WAN IP address (aka external IP address,  WAN=wide area network). This address is different from the LAN IP addresses mentioned above. To find out about the router's WAN IP address:

[LIST]
[*]a user logged on onto a local machine may want to visit the site *whatismyip.com* (using a browser).
[/LIST]

yes correct.

There are also other methods to obtain both LAN and WAN addresses other than the ones you mention for example you could just login into the router to see the WAN address, but yes it is correct

---

### Post by The Cog on 2011-10-30
Nobody has mentioned the expression Network Address Translation (NAT). This is the function your router is performing to convert your internal address to your publicly visible IP address. This has to be done because your ISP only assigns you one IP address and you have the possibility of many internal computers.

You router maintains a NAT translation table that tracks which internal address/port it is converting to which external address/port so that it can convert the incoming packets relating to existing connections back and forward them to the correct internal computer.

This leaves the question of what to do with incoming packets that are not associated with an existing connection? Generally they will be dropped. This means that a NAT router acts rather like a firewall, preventing incoming connections. So if you want to run a pubic server internally, a web server for instance, you have to explicitly configure the router to forward incoming web connections (port 80 for http) to a particular internal address. This is known as port forwarding.

---

### Post by haqking on 2011-10-30
> **The Cog said:**
> Nobody has mentioned the expression Network Address Translation (NAT). This is the function your router is performing to convert your internal address to your publicly visible IP address. This has to be done because your ISP only assigns you one IP address and you have the possibility of many internal computers.

You router maintains a NAT translation table that tracks which internal address/port it is converting to which external address/port so that it can convert the incoming packets relating to existing connections back and forward them to the correct internal computer.

This leaves the question of what to do with incoming packets that are not associated with an existing connection? Generally they will be dropped. This means that a NAT router acts rather like a firewall, preventing incoming connections. So if you want to run a pubic server internally, a web server for instance, you have to explicitly configure the router to forward incoming web connections (port 80 for http) to a particular internal address. This is known as port forwarding.

I touched on it in my post #12 ;-)
[http://ubuntuforums.org/showpost.php?p=11406264&postcount=12](http://ubuntuforums.org/showpost.php?p=11406264&postcount=12)

---

### Post by The Cog on 2011-10-30
Yes you did. Sorry, half my mind on the formula1 race.

Actually, wikipedia has a ling explanation for anyone wanting to learn more.
[http://en.wikipedia.org/wiki/Network_address_translation](http://en.wikipedia.org/wiki/Network_address_translation)

---

