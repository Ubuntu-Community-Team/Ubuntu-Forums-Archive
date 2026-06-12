---
title: "Need some hand-holding with new LTSP setup"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by doctorbighands on 2011-10-15
I'm not new to Ubuntu, but it's my first time trying to set up an LTSP cluster. To put it mildly, things aren't going well. I'm hoping someone can step me through what I'm doing wrong, because I'm completely lost.

MY SETUP

Server: 1u Dell 1435, 8GB RAM, 2 dual-core Opterons, 2 onboard gigabit NICs, Ubuntu 11.04 x64
Clients: 6, all PXE-capable
Network Topology: "Internet -> Router -> eth0 on server", and "server eth1 -> 24-port HP Procurve switch -> clients"

I installed the OS on my server according to [these instructions]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall"), using the "Installing from CD" section. I installed from a USB stick, but same thing. The install went fine - I'm typing this message from the server right now.

Once the installation finished, I went into a terminal and entered
```
sudo ltsp-build-client --arch i386
```
because my server is 64-bit, and my clients are all 32-bit.

Tried to connect to server from client. Received error message: PXE-E51: No DHCP or proxyDHCP offers were received.

It turned out my server wouldn't connect to the switch, and I couldn't figure out why not, so I played with Network Manager until I discovered the option called "Method: Share With Other Computers" under the IPv4 tab. Now server and switch are talking, but now I get a new error from the clients at boot: PXE-E53: No boot filename received

I haven't messed with any conf files. I haven't done anything except hook up hardware, install a vanilla OS, rebuild the LTSP client image for x86 arch, and connect my server to my switch.

What am I missing?

ADDITIONAL INFO

On the instruction page I referenced above, there's a line that says this:
```
Configure your spare interface for the thin clients to have the IP 192.168.0.1 (and make sure it is up and running).
```
I have no idea what this means, or what it's asking me to do. I'm thinking this is my problem, but I just have no idea.

Please help a lost, frustrated soul. Thank you.

---

