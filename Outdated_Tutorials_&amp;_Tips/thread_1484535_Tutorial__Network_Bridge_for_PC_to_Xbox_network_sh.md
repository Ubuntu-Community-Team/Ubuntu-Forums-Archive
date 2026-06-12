---
title: "Tutorial:  Network Bridge for PC to Xbox network sharing."
date: 2010-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Beelzebud on 2010-05-15
I struggled with getting this setup to work properly for a few months of on-again-off-again attempts.   I finally found a solution, and I'm posting it here in case it will help someone else trying to do something similar. 

The hardware I was using was a PC with an Asus A78X-E motherboard.   It has two network ports on it.   The line to the router was in one of the ports, and a line to my Xbox (original Xbox modded and running XBMC) was going to the other.  This was all done using wired connections, because I do not have wireless.   I'm not sure if it would work correctly for wireless or not.   

I found a few sloppy solutions that involved manually bringing up the bridge any time I wanted to use it, but this wasn't a satisfying solution for me.   Internet connection sharing with Firestarter didn't work correctly because it didn't assign an IP address to the Xbox.   With this config it will make both network interfaces bridge, and each get their own IP address from a router's DHCP server.  

Basically I wanted the machine to act as a switch so the Xbox could still get its own IP from DHCP.   Many configurations were tried, and none of them worked well.   Given that XBMC uses Samba sharing, the machine needed its own IP address to be able to both browse the internet if needed, and use SMB shares on the network.  

This is what I ended up with, and it works fine for giving the 2nd machine an internal IP address, just as if it were plugged in to the router itself.   It works with my Xbox, a laptop running Puppy Linux, and I'm sure it would share a connection properly with an Xbox360, PS3, or anything else you wanted to share the connection with.

This was all done in Ubuntu 10.04 LTS, but I'm sure it will work in older versions, as the bridge utility hasn't changed at all.  

Start off by installing the network bridge utilities by opening your Terminal and entering in:  >  sudo apt-get install bridge-utilsAdd the following config to /etc/network/interfaces
(For those of you that are really new, open the Terminal and type > sudo gedit /etc/network/interfaces> auto lo
iface lo inet loopback

auto eth0
auto br0

iface eth1 inet dhcp

iface br0 inet dhcp
bridge_ports eth0 eth1Now this isn't universal.   If your setup is similar but you have things plugged in opposite ports than I did, all you'll have to do is just swap the 'eth0' entries with the 'eth1' entries.

Reboot the machine, and you should have a network bridge that will grab an IP from the DHCP server even if the 2nd device is started after the Ubuntu machine.   I've been using this config for a couple of weeks now with no problems at all.   Network shares work, internet works, and I've seen no negative side effects.   It just acts like both machines are plugged in to the router.   

I hope this helps anyone out there trying to get network sharing to work on either a game console, or even another PC.   This should work fine for either scenario.

---

### Post by micheledm on 2010-05-20
This is interesting, I was using NM-applet for bridging the two connections but the X-Box takes the IP from my laptop instead from the router, while it would be nice to have the same ip class for both. I want to try this out but bridging wlan0 and eth0, i assume that eth0 in your config goes to the router and eth1 to the xbox. Is there anything else to modify? Is easily reversible in case  i want to connect my laptop through eth port when i'm away from home?

---

