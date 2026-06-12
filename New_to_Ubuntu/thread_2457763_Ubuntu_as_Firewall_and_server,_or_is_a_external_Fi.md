---
title: "Ubuntu as Firewall and server, or is a external Firewall reccomended?"
date: 2021-02-08
forum: New to Ubuntu
---

### Post by erdur on 2021-02-08
I want to build a (a bit more) complicated server at home.

It should have services which are reachable from the inside and outside (e.g. linuxgsm).
But i also want some services to only be reachable from the inside.

As i understand it i can set the firewall rules to distinguish if a service can be reached by either Ethernet port.

But can i also set up the Firewall (with NAT) in the server, or is it recommended to get a external firewall (like a zyxel or baracuda)?

---

### Post by rsteinmetz70112 on 2021-02-08
As usual the answer is it depends.

Most people would generally recommend a separate firewall/router rather that having a server do that as well as other things. Rather than a specialized device just about any spare computer could be configured as a router/firewall. 
However depending on your plans you might be able to get by at home with a server alone, depending on what your ISP supplies, the services you need and the devices connected to your home network.

---

### Post by erdur on 2021-02-08
At my current plan the ISP would be in Bridge/Modem mode.

So one of the devices in my network should run the usual services, Firewall / DHCP, maybe even some UPnP. (UPnP odds with security, but some devices can make problems if they don't get that one.).

The main reason to get it is as a game server (linuxgsm), for other things i was thinking about adding a KODI (internal only, my NAS has problems with some avi files) or play around with some web services.
(e.g. Cataloging my Recopies, indexing my books & movies.)

The advice from one of my friends would be use different servers for everything (internal server, external server and one a smal Z-Box for DHCP and DNS).
Another one has the opinion, just use one and visualize everything.
And i don't want to many boxes in my living-room, but i want the setup to be as save as needed.

---

### Post by rsteinmetz70112 on 2021-02-08
Virtualization is a pretty good option as long as you have enough horsepower to run all of the VM you want.
I'd still think about having a separate router/firewall.

---

### Post by erdur on 2021-02-08
Thanks,i will go with a seperate Firewall then.

I plan to use Containers instead of full VM for some of the systems since it appears to be "save enough".

---

### Post by TheFu on 2021-02-08
+1 on having a separate WAN router and firewall.  Don't want a misconfigration destroying your LAN security.
+1 for using virtualization too. LAN only services need to be placed on a different subnet than internet-facing services.  Security architecture is important.

VM overhead isn't really THAT much.  I ran 15 VMs on an early core2 duo w/ 16GB ram, easily.  Separate VMs for services that aren't closely related will make your life easier. Another option is to use Linux containers for services that aren't so risky and for LAN stuff only.

Just because something CAN be done, that doesn't mean it is a good idea.

Most computers are too noisy to be in a den, imho. For media playback, use a cheap, silent, streaming device. I use 2 raspberry pis, fanless. my media server is on the network elsewhere. An old laptop might work for a quiet media playback device too.  I don't use wifi.

---

### Post by erdur on 2021-02-08
So at least one VM for the game-server, another one when i decide to run some (external) web-services and so on.
Seems like good advice. (I will probably try QEMU for the server.)

I have some pis lying around, so i an test that one.

Since i haven't worked with long term running systems i am not sure how much the fans will produce, but i can only put thy system in the room where the internet enters.
(Else i would have to add a VLAN switch or find a way to add a Lan cable in my wall.)

---

### Post by TheFu on 2021-02-08
QEMU is slow because it only uses software to emulate the other CPUs. Use KVM instead. It uses the VT-x or AMD-v CPU extensions for much improved VM performance. May I suggest using virt-manager, libvirt, and KVM with normal Linux bridging to connect the different VMs to the different network LANs? Setting up a bridge for VM use isn't hard. By default, VM networking is NAT and slow. A manually created bridge can provide fantastic performance.  For VM-to-VM transfers, I see 25+ Gbps on the same system. Obviously, the performance of the storage is the limiting factor for those transfers.

Power-line ethernet does work. I bridge 2 floors of my home using that.  I have COAX for CATV throughout the house too. Today, I'd probably use MoAc 2.5Gbps networking rather than powerline.  Wifi is a mess in most environments. I designed thousands of wifi deployments at an old job for the local people install. Two nearly identical buildings would have very different success or failures with wifi. For streaming video, wifi is a mess. I only use wifi for android devices that don't support wired connections.  If you live in a multi-tenant building, wifi will be a mess almost always.

A r-pi v2 can handle 720p videos easily and specific 1080p video if the correct codecs are used.
A r-pi v3 can handle more codecs and 1080p resolution.
A r-pi v4 can handle 4K video, I understand. I don't have this model, yet.  Our projector is only 1080p, so I don't see the point. We don't have any TVs.

---

### Post by erdur on 2021-02-08
> virt-manager I will try that one tomorrow. (ok, with my timezone its today, but after i slept.)
I think i will also have a look into "cockpit".

Notwork-structure - For my home i have one room where the modem resides, and one line into every other room (and a separate line for where i want to place my Consoles).
So i would put the Firewall next to the Modem, and the "Server" (Workstation hardware) next to it. One LAN connected to the Firewall directly, the other one one to the inside switch.

> A r-pi v3 can handle more codecs and 1080p resolution. I definitely have to try that one, my NAS has a media center,but problems playing some formats to my tv.
(And i have one lying around, if i can figure out which one is the 3 ...)

---

### Post by TheFu on 2021-02-08
TV video players usually are limited to h.264/aac/mp4 and similar content.  Some media servers will transcode to whatever format is needed by each client on-the-fly.  If you hook up a r-pi v3 running OSMC, then the ability to view almost any content (except h.265 which is a CPU hog) will probably work.

What is a "Consoles?"  If you have networking to other rooms, then the "server can be placed anywhere you like.  A real router can manage firewall rules and vlans. It doesn't need to be too expensive. I've seen $60 GigE routers with this capability.  Of course, they don't have wifi. Wifi needs to be a separate consideration anyways.  Routers should last 10+ yrs, get vendor patches for at least that long, while wifi standards change is large ways about every 5 yrs. Best to keep wifi-AP and routing separate, IMHO.

---

### Post by erdur on 2021-02-09
Wouldent V-Lans neccesetate vlan-capable switches in the corresponding room?
```

Modem<---> router <-+-> vlan <---> switch (vlan) <-+-> Server (Vlan resolved inside?)
                    |                              +-> other devices in the room (would be my PC in this setup)
                    +-> Lan to other rooms

```

"Consoles": Gaming-Consoles: PS4, Switch, ...

"Transcoding": Is part of the specs of the NAS, but its smart-tv-app ffails with some formats.
(The TV source menu plays it with some artifacts on the start, when transcoding is enabled.)

---

