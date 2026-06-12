---
title: "OPEN VPN, Static IP Client and Network Manager"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by varzues on 2012-11-15
So, I seem to be having a series of issues that may or may not be correlated. I thought asking if anyone has any suggestions to help/point me in the right direction is my best bet. I'm trying to setup OPEN VPN on a Static IP Client. I'm fine with using the cmd line and avoiding Gnome Network Manager.

If I use Network Manager on DHCP the VPN works fine with network-manager-openvpn-gnome. My problem lies in the fact I need to get two and from both boxes regularly, sometimes I'm at home and need to get to work, sometimes I'm at work and need to get to the house leaving me with needing a static ip on my dev vm at home(im open to other ideas if there are any). There's no rush on this, as I can still get in just fine with putty, but I thought I'd be nice to live in linux for a few months from a learning perspective.

1. If i assign my client (Virtual Box 4.2 Xubuntu 12.04) a static IP network manager no longer works. The connection is fine and works as expected. I have the network setup in the vbox as bridged.

[INDENT]```

auto lo 
iface lo inet loopback

auto eth0
address 192.168.1.xxx
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameserver 8.8.8.8 192.168.1.1

```[/INDENT]

This would be fine if I could connect via cli, but OPEN VPN doesn't connect without the use of network manager (yes I'm using the same files that do connect on dhcp).

2. OPEN VPN doesn't connect via cli, or at least let me access the remote host (cannot ping it etc...). The tap interface is being created, but isn't communicating over it, regardless of dhcp or static. Maybe I'm missing something here? I'm invoking the connection with

[INDENT]```

sudo openvpn my_config_name.ovpn

```[/INDENT]

I get the result of 'Initialization Sequence Completed' and can see the tap0 interface with 'ifconfig'. I'd copy some info in, but vbox extensions aren't working either :confused:.

Still pretty new to linux, and would just like pointed in the right direction. This is an updated fresh install outside of openvpn, gnome network manager, vim and vbox extensions.

---

### Post by varzues on 2012-11-16
I had the time to spend today to experiment more.

Still couldn't get the CLI interface openvpn to work. I was able to setup a static ip with network manager and then connect to openvpn with network manager... so this will work for now.

If anyone knows a good though cli openvpn reference I'd love to read it.

---

