---
title: "[SOLVED] Basic network help"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by laffinet on 2008-11-06
I'm after some really basic networking help. I think I lack some basic understanding somewhere.

I'm trying to connect two Ubuntu machines, both are running 8.10 (one Ubuntu, one Mythbuntu).

Both are connected via wireless to a router (OPEN824RLW which is a rebadged Billion 7404VGP) with DHCP

The router's IP is 192.168.1.254, one machine is 192.168.1.103, the other one 192.168.1.100.

At the moment I can't even get ping between the machines to work, let alone sharing folders or VNC. 

Do I need to setup static IPs ? If so how ? Do I need to change anything on router ? I'm really lost here so any help is appreciated.

Thanks.

---

### Post by hictio on 2008-11-06
> 
Do I need to setup static IPs ? If so how ? Do I need to change anything on router ? I'm really lost here so any help is appreciated.


Not at all, in the scenario you describe.
Let's do some basic test first...

- Both of the Ubuntu's boxes' NICs are working right?
On each one can you ping localhost (ping 127.0.0.1), can you ping the same IP address of each of the boxes from themselves?

- Both of the Ubuntu boxes see the WiFi router?
Can you ping it from each of them?

- Both of the Ubuntu boxes are on the same subnet?
That is, have you checked that they network settings are Ok?


If the NICs are working Ok, the network settings idem, you have to get a ping reply from the Ubuntu boxes, even if enabled, the built in firewall does not block pings.

---

### Post by kerpow on 2008-11-06
There is no need for static IPs, as long as you know the IPs at a given point in time, and seeing as you are on a small network they *may* never change.

Can you can ping the router from both machines?
Can you reach the Internet via the router on both machines?

Let us know.

---

### Post by handydan918 on 2008-11-06
> **kerpow said:**
> There is no need for static IPs, as long as you know the IPs at a given point in time, and seeing as you are on a small network they *may* never change.


Indeed, many routers are able to "reserve" a dhcp address to a particular MAC address so that the ip NEVER changes.

---

### Post by B34ST1Y on 2008-11-06
> **laffinet said:**
> I'm after some really basic networking help. I think I lack some basic understanding somewhere.

I'm trying to connect two Ubuntu machines, both are running 8.10 (one Ubuntu, one Mythbuntu).

Both are connected via wireless to a router (OPEN824RLW which is a rebadged Billion 7404VGP) with DHCP

The router's IP is 192.168.1.254, one machine is 192.168.1.103, the other one 192.168.1.100.

At the moment I can't even get ping between the machines to work, let alone sharing folders or VNC. 

Do I need to setup static IPs ? If so how ? Do I need to change anything on router ? I'm really lost here so any help is appreciated.

Thanks.

some things you may want to consider checking into - 

1. make sure you can at least ping the router. If you cant even do that, you may have a bigger problem. 

2. are both hosts (computers) on the same subnet? (for example, 255.255.255.0 ) 

3. do you have any special firewall configurations?

---

### Post by laffinet on 2008-11-06
I can ping the router from both machines.

I have an internet connection on both machines.

I think both machines are on the same subnet (how can I check ?)

I'm not aware of any special firewall settings (again, how can I check ?)

Thanks.

Edit: Just checked, firewall on router is disabled.

---

### Post by B34ST1Y on 2008-11-06
typing in "ifconfig" to your terminal will reveal the ip address, and subnet for each respective interface. If you cannot ping the computers from one another, it is possible that you have a firewall blocking it. Or perhaps SNMP (ping) is set to ignore as a safety measure.

---

### Post by B34ST1Y on 2008-11-06
> **laffinet said:**
> I can ping the router from both machines.

I have an internet connection on both machines.

I think both machines are on the same subnet (how can I check ?)

I'm not aware of any special firewall settings (again, how can I check ?)

Thanks.

Edit: Just checked, firewall on router is disabled.

random question - are you trying to VNC into your box via your WAN (internet) ip address, or the local private address?

---

### Post by hictio on 2008-11-06
> **laffinet said:**
> I can ping the router from both machines.

I have an internet connection on both machines.

I think both machines are on the same subnet (how can I check ?)

I'm not aware of any special firewall settings (again, how can I check ?)

Thanks.

Subnet:
- Type:
```

ifconfig (ENTER)

```
on a terminal on each one of the Ubuntu boxes.

You'll see something like this:
```

wlan0     Link encap:Ethernet  HWaddr 00:1f:3a:4a:43:3a  
          inet addr:10.120.10.4  Bcast:10.120.10.7  Mask:255.255.255.248
          inet6 addr: fe80::21f:3aff:fe4a:433a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15186 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13964936 (13.9 MB)  TX bytes:3007890 (3.0 MB)

```

Look for the 'Mask:' setting.

Firewall:
- Type on the terminal of each one:
```

sudo ufw status (ENTER)

```

It will ask your password.

---

### Post by laffinet on 2008-11-06
Machine 1:

inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

Machine 2:

inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0


> it is possible that you have a firewall blocking it. Or perhaps SNMP (ping) is set to ignore as a safety measure. 

How do I check this ?

> random question - are you trying to VNC into your box via your WAN (internet) ip address, or the local private address? 

I haven't gotten to the level of VNC yet, only trying to ping at the moment to see if the machines can see each other. For that I had been using the addresses as listed above, ie from machine 1 ping 192.168.1.103

---

### Post by laffinet on 2008-11-07
> sudo ufw status

not loaded

---

### Post by hictio on 2008-11-07
> **B34ST1Y said:**
> typing in "ifconfig" to your terminal will reveal the ip address, and subnet for each respective interface. If you cannot ping the computers from one another, it is possible that you have a firewall blocking it. Or perhaps SNMP (ping) is set to ignore as a safety measure.

AFAIK, the Ubuntu firewall does not do that, unless you really go "bellow the hood", check here:

[ufw disable ping / icmp](http://ubuntuforums.org/archive/index.php/t-773485.html)

---

### Post by laffinet on 2008-11-07
Any more suggestions ?

---

### Post by shazbut on 2008-11-07
I have almost the exact same setup with a similar problem, same OPEN824RLW.  Intermittent 'no route to host' error on pings between hosts, all on the same subnet, but other times it works fine.  Only really started happening since I swapped to this router, so maybe I should start by looking there.

---

### Post by laffinet on 2008-11-07
This is what I get from ping:

PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
From 192.168.1.103 icmp_seq=1 Destination Host Unreachable

---

### Post by B34ST1Y on 2008-11-07
I would recommend setting up your vnc server. See if you can connect to it. Are you using special firmware on your router, by chance? Anything out of the ordinary that we should know about

---

### Post by laffinet on 2008-11-07
I swear I didn't change a thing but when I tried ping a moment ago it worked, from both machines.

Then, without changing anything, it stopped working again.

I'm stumped. 

No idea.

---

### Post by kerpow on 2008-11-07
Connect your router with the bin and start again. :)

---

### Post by shazbut on 2008-11-07
Hey, Laffinet, that's my exact symptoms too. Right now I can ping between 2 wired static IP hosts, but not to a DHCP host on wireless, all in the same subnet.  Trying to work out if it's the router now.

Edit: Might not be the router. Something funny is going on with the arp table. If I type 'arp' in the terminal there is an entry like this:
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.101                    (incomplete)                              eth0

If I add the proper hardware address with:
 sudo  arp -s 192.168.1.101 00:00:00:00:00:00
(where 00:00:00:00:00:00 is the mac address of the wireless adapter in 192.168.1.101)
I can now ping it. And the arp table looks right:
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.101            ether   00:01:81:91:B1:21   CM                    eth0
Still have no clue why it's happening though...I'd still like to know why the MAC address of the adapter is getting mangled.

---

### Post by B34ST1Y on 2008-11-07
o.O randomly working, then not working? If you really didn't change anything, you may have defective hardware.

---

### Post by laffinet on 2008-11-07
Alright, I've done some more testing and it's definitively the wireless connection that's causing the problem:

Two machines on router with wired connection: no problem
One machine wired, one wireless: intermittend success with ping

Questions now: why ? And how can I solve this ?

In terms of my setup long term I could possibly get away with one wired and one wireless (although that wasn't really the idea), but I can't do both wired.

Any further suggestions ?

---

### Post by laffinet on 2008-11-07
I've done some more testing and am now pretty sure it's not a hardware problem:

Setup 1: Windows machine wireless on router, Ubuntu machine wired on router: no problems, ping consistently working, both ways

Setup 2: Windows machine wireless on router, Ubuntu machine wireless on router: ping not/sometimes working

So it seems Ubuntu has a problem with the wireless connection. What I'm confused about is that the wireless is working alright for internet etc., only when I try to reach another machine on the router is it that I have problems. 

Any ideas ?

---

### Post by handydan918 on 2008-11-07
I'd start by verifying the ip address of any machine using wireless, just to make sure it is actually on your lan. 
I sent a print job to my neighbors HP one day...

---

### Post by B34ST1Y on 2008-11-07
laffinet, if you router is intermittently not allowing the passage of packets to the computers....then its probably defective. Your computers would either successfully ping each other, or they wouldn't. intermittent behaviour leads me to believe its a defective router. Can you try a diff router?

---

### Post by laffinet on 2008-11-07
> **B34ST1Y said:**
> laffinet, if you router is intermittently not allowing the passage of packets to the computers....then its probably defective. Your computers would either successfully ping each other, or they wouldn't. intermittent behaviour leads me to believe its a defective router. Can you try a diff router?

I don't think it's my router. Have a look at my latest post, wireless windows to wired Ubuntu works consistently, which makes me think it's not a router problem but an Ubuntu problem.

---

### Post by shazbut on 2008-11-07
It's not the router.  The ARP table entry for the wireless host is correct on my router, but on the wired Ubuntu host it is listed as (incomplete).  Manually adding the correct entry corrects the problem, and I suspect flushing the ARP cache would too, which is probably why the problem is intermittent.  Going to do a capture with wireshark when I get a minute later to see what's going on...

---

### Post by laffinet on 2008-11-07
Thanks shazbut.

I am not experienced enough to understand half of your post but I am more than grateful for any help you can offer :D

---

### Post by handydan918 on 2008-11-07
> **shazbut said:**
> It's not the router.  The ARP table entry for the wireless host is correct on my router, but on the wired Ubuntu host it is listed as (incomplete).  Manually adding the correct entry corrects the problem, and I suspect flushing the ARP cache would too, which is probably why the problem is intermittent.  Going to do a capture with wireshark when I get a minute later to see what's going on...

hmm. Good thought. Still might be router related, tho. Most NAT routers have some RIP functionality options you can play with. Seems like that might mess with the routing table, no?

---

### Post by shazbut on 2008-11-07
Shouldn't be any routing happening within the same subnet though, this is purely layer 2 stuff.  RIP and other routing protocols are turned off, only a static route from LAN -> WAN.

---

### Post by B34ST1Y on 2008-11-07
try using a crossover cable. Connect the two wired NIC cards together, and statically assign IP addresses. Ping each other and see if you get continuity.

---

### Post by shazbut on 2008-11-08
Bugger ,can't get mine to fail now.  Here's some commands to try in the terminal when it fails for you, laffinet:
```
arp
```
Shows the current arp table, matches IP addresses to ethernet MAC addresses. Look for an entry for the IP/hostname you cannot ping.

```
sudo arp -d <hostname_or_ip_address>
```
Deletes the specified host or IP from the arp table.  Use it to remove an entry showing as (incomplete), then try pinging it again to refresh the table.

```
sudo arp -s x.x.x.x yy:yy:yy:yy:yy:yy
```
Sets a static arp table entry for IP address x.x.x.x to hardware address yy:yy:yy:yy:yy:yy.  You can find out the hardware address by looking at the output of ifconfig, or by logging into the web interface of the router and going to status -> arp table.

Hope one of these helps.

---

### Post by laffinet on 2008-11-08
I'm beginning to suspect that the wireless from my mythbox is not working properly.

Just now I tried all the steps you described and ping still did not work. On top I couldn't even ping the router from the mythbox. Hm.

---

### Post by laffinet on 2008-11-08
Is it possible that the two wireless connections interfere with each other (physically) ?

If so, is it possible to have them transmit on slightly different frequencies ? Might that help ?

It almost seems that I can see the quality on machine going down as the other one is active on the network. Or maybe I'm just imagining things...8-)

---

### Post by shazbut on 2008-11-08
Yes, 2 clients on the same router are using the same frequency, it's set on the router (configuration -> LAN -> wireless -> channel ID on the web admin page of the open824rlw).  Can't set them to different channels on the same router.  Unless both machines are trying to max out the connection you shouldn't see too much degradation though.  Try the scan channel usage option if you suspect you might be overlapping with a neighbour's channel.

---

### Post by laffinet on 2008-11-08
After some more playing around it looks like the wireless connection from my mythbox is just not stable enough. I noticed that the signal strength was going up and down and sometimes even lost connection. 
So I wired it to the router and now I can ping easily and even got a ssh -X to work.
Haven't been able to set up folder sharing via nfs yet, but I guess that's another problem...

Is there any way to boost a wireless connection ? Like an amplifier/active antenna you can fit to the wireless card or the router ? Or is my only chance to go wired or move the router closer to the mythbox ?

---

### Post by laffinet on 2008-11-08
Success !!!

I moved my router, got a better wireless connection (that doesn't drop out all the time, which I first didn't notice) and I can now consistently establish a connection from my laptop via wireless to the wireless mythbox.

So far I managed to rdesktop into the mythbox, right now I'm trying to share folders which I'm still having trouble with. But I've already got another thread going for that.

Thanks everyone.

---

### Post by shazbut on 2008-11-10
Glad to see you got it resolved.  I had the problem happen again yesterday and mesing with ARP did nothing, so I'm starting to suspect a flaky wireless connection too.  Must be a reason why one laptop gets 30% signal and another gets 85%.  I have to pull the laptop apart anyway (heat issues) so I'll make sure the antenna connector is not loose/broken.

---

### Post by laffinet on 2008-11-10
Yeah, in the end it came down to just a dodgy wireless connection, once that was sorted everything worked fine and I got the NFS shared folders working as well.
It was hard to detect since the wireless worked good enough for internet etc. but at one stage I noticed the quality fluctuating a lot.

I'm having a new problem with one of my other laptops now. It sees the network, but does not connect to it (ubuntu and windows). I suspect that it's a faulty wireless card, might have to open it too or try a USB adapter.

---

### Post by laffinet on 2008-11-15
Back to square one !

I had to reset my router to the factory defaults (after fiddling with it to get the whole network thing working I couldn't connect with the one windows machine I have and couldn't figure out what to change so I went full reset) and now I'm back to where I started: ping sometimes works but that's about it.

arp only produced this:

```
 arp
Address                  HWtype  HWaddress           Flags Mask            Iface
home.gateway             ether   00:04:ed:24:d2:60   C                     wlan0

```

Shouldn't it at least show the machine I'm on as well ?

This is the arp table from the router interface:

```
IP Address 	MAC Address 	Interface 	Static
192.168.1.100	00:21:91:89:c6:22	iplan	no
192.168.1.101	00:1c:bf:c6:0e:4b	iplan	no
192.168.1.102	00:0c:f1:19:47:29	iplan	no
```

And the DHCP table from the router:

```
IP Address 	MAC Address 	Client Host Name 	Expiry
192.168.1.102	00:0c:f1:19:47:29	benq-11wch2lwoc	11 hours
192.168.1.101	00:1c:bf:c6:0e:4b	laffi-laptop	11 hours
192.168.1.100	00:21:91:89:c6:22	laffi-mythbox	10 hours
```

Ping to those other two machines works sometimes (more not than it does).

Wireless connections are pretty good for all machines (>70%).

Any ideas ?

---

### Post by shazbut on 2008-11-16
I'm out of ideas.  On the plus side, I did get my own wireless working a bit better.  Someone had plugged in the antenna cables to the mini pci card the wrong way around, instant 15% signal improvement once I fixed that.

---

### Post by laffinet on 2008-11-18
Bump

---

### Post by laffinet on 2008-11-21
Anyone ?

---

### Post by laffinet on 2008-11-22
Okay, I've got it working, it's not lightning fast but I guess that was expected.

I've changed this on my router to get it to work:

1. Changed the wireless channel, although I've got no idea if this made any difference because at the same time I
2. Added all machines to the wireless client filter.

---

