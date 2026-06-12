---
title: "Constant Network Activity"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Terry Yaki on 2008-04-24
Hi, I've come across a little problem.

When I check my network history (from System > Administration > System Monitor), it shows that I have been constantly downloading something. I tried closing all my programs, but it still says something is being downloaded. Restarting the computer doesn't stop it either. 

I asked for help previously and was told to check active connections with sudo netstat -tanp, but all it shows is 5788/cupsd. If I run sudo lsof -i -n, I get avahi-daemon, cupsd, and dhclient. 

I normally wouldn't worry about it. But it has reached 5 gigs, and being on campus, I'm limited to 10 gigs of bandwidth. I found this archived thread below, but I thought I'd ask about it anyways to be sure. Thanks.

[http://ubuntuforums.org/archive/index.php/t-8873.html](http://ubuntuforums.org/archive/index.php/t-8873.html)

---

### Post by pytheas22 on 2008-04-24
You can install wireshark (sudo apt-get install wireshark) and then capture the traffic with it.  It will tell you where it's coming from and what's in it.  If it's not legitimate traffic you can blacklist it.

For a faster but less user-friendly traffic monitor, you could also use tcpdump (run as root), which should already be installed.  It's command-line and you have to know what you're doing to use all its features, but it will at least tell you which domains/IP addresses are being contacted.

---

### Post by pytheas22 on 2008-04-24
Also, keep in mind that the activity shown by System Monitor doesn't necessarily represent Internet traffic.  Mine shows constant activity too, but it's just ARP packets and stuff.  So it shouldn't count against your bandwidth limit, because it's only on the local network (or at least, that's how it works at my school).

---

### Post by jarocooke on 2008-04-25
Yeh I have just noticed I am getting the same thing.

I'm connected to a wireless router (broadband) and my network usage show me downloading at 275KB/s pretty much constantly, even with everything like firefox, evolution, etc... closed.

I installed wireshark as suggested, but I don't know enough about network packets to make any sense of it.

Most they seem to be UDP packets where the info column show "Source port: terabase Destination port: complex-main, but every now and again there is a MPEG PES protocol packet.

The internet seems to be quite slow and unresponsive, so I reckon my 275KB/s is genuine network activity (rather than a reporting error).

Anyone got any ideas?

---

### Post by jarocooke on 2008-04-25
Right, I have just run a internet speed test on my computer and it says my download speed is c. 250KB/s.  I then switched off my laptop and used my sisters-in-law's Mac to run the same braodband speed test, it still said c. 250KB/s, so my "downloading" at 275KB/s must be something internal to the LAN if not Hardy Heron (like an incorrectly reported figure).  BTW I ran both tests a few times as those broadband speed tests can be a bit on the unreliable side.

I'd still like to know what it causing it (and how to fix it).

---

### Post by pytheas22 on 2008-04-25
> I installed wireshark as suggested, but I don't know enough about network packets to make any sense of it.

Even if you don't know how to interpret all of the information in Wireshark, the most important thing to look at is which IP addresses your machine is in contact with.  For instance in the screenshot attached below, you can see that my machine is sending stuff to 128.146.13.71 and 66.249.83.19 (I crossed out part of my machine's IP address for privacy reasons).  You can then figure out where these IP addresses are and determine if there's a valid reason for your computer to be in contact with them; if there's not, maybe you should think about blacklisting them.  +200KB/s seems like a lot of traffic--I only have about 15--so if I were you, I'd take a deeper look, especially if you're seeing a lot of MPEG traffic...maybe this means you're hosting p2p files and you don't know it.

---

### Post by jarocooke on 2008-04-25
I'm not sending data out, I'm downloading it!  So not hosting anything.  The IP addresses are 10.x.x.x source to 225.x.x.x.  The 10.x.x.x address is a private one (local network), however the address that my laptop gets from the router is a 192.x.x.x address!  225.x.x.x is outside the range of IPv4 addresses isn't it?  I'm very confused, the activity doesn't affect internet access speed (probably because the traffic isn't coming from outside the LAN), but still.

---

### Post by pytheas22 on 2008-04-25
What's the full 225.x.x.x address?  I thought anything below 256 was valid, although I'm no expert.  And what's your IP address according to a site like [http://whatismyip.com/](http://whatismyip.com/) (or if you don't want to give it out, at least tell us whether it's similar to the 225.x.x.x address or not)?

---

### Post by Monicker on 2008-04-25
225.x.x.x is a multicast address.  It could be a router or something trying to communicate with other devices of the same type.

---

### Post by jarocooke on 2008-04-25
My IP address according to that site is a 79.x.x.x address.

The multicast explanation sounds like a more likely scenario.

You know I think I know what it was (more or less).  The traffic flow has stopped now and the only thing that has changed is that I have turned off the TV which was tuned to a TV channel through Tiscali (UK cable TV / internet provider).  The traffic must have been related to the operation of the TV service (communication from the router to the main Tiscali box).  The box is new (replaced last week) and this is the first time that I have been here since then.  I guess rather than operating the box on the network in a normal way, the router simply multicasts the data to anyone that is listening.

How strange, but interesting.

---

