---
title: "ubuntu server network autoconfiguration failed(using a 'guest' version wifi)"
date: 2017-08-22
forum: New to Ubuntu
---

### Post by hiomachi on 2017-08-22
i've tried googling without fail and this issue has been a literal WALL to me. Hope some can shed a little light on this.
[FONT=inherit]I've been trying to install an Ubuntu server on a virtual machine(VirtualBox) but everytime i reach the network configuration installation step, autoconfig sewith DHCP seems to fail:[/FONT]
[FONT=inherit]"Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or the network hardware not working properly".[/FONT]
[FONT=inherit]Now i'm a little confused here, being a newbie in technical jargon so could someone explain the error? I am indeed connected to the internet albeit a guest wifi of sorts so i assume the wifi comes with some connection restrictions which could be the reason for this?[/FONT]
[FONT=inherit]I read online that manual config can help but the whole nature of using the guest wifi is stumping me such that i have no idea what ip address to even input.[/FONT]
[FONT=inherit]A quick check on ipconfig in cmd yielded this:[/FONT]
[FONT=inherit]Wireless LAN adapter WiFi:[/FONT]
[FONT=inherit]IPv4 Address. . . . . . . . . . . : 10.255.74.4[/FONT]
[FONT=inherit]Subnet Mask . . . . . . . . . . . : 255.255.254.0[/FONT]
[FONT=inherit]Default Gateway . . . . . . . . . : 10.255.74.1[/FONT]
[FONT=inherit]But a quick search on whatsmyip yielded a very different ip address.[/FONT]

Isnt the default IP add supposed to start with 192.168.0....?

---

### Post by SeijiSensei on 2017-08-23
VirtualBox has a variety of different networking modes (see Settings > Network), the most common of which are "NAT" and "bridged."  In NAT mode, the default, the virtual machine gets an address starting with 10.0.8, and the VM itself is not visible from other machines on the network.  It is "hidden" behind the host computer, all its network traffic is forwarded through the host.

That's not the best solution if you want to set up a VM as a server that other machines on the network can use.  For that, you should choose "bridged."  Then the VM will appear to be on the same physical network as the host machine and will get an address in the same subnet as the host.

If you're using "bridged" already, but the VM cannot see a DHCP server, perhaps you actually do not have one?  Most people using wifi routers already have a DHCP server built into the router itself.  That way you can simply log into the wifi device, or plug in an Ethernet cable, and get an IP address.  If you do not have a router handing out addresses with DHCP, or another server on your network that provides the DHCP service, then you should give the VM guest a static IP address in the same subnet as the host.

In general, servers should always have static addresses, so clients will know how to contact them reliably.  DHCP is fine while setting things up, but ultimately you should give the machine a static address.

---

