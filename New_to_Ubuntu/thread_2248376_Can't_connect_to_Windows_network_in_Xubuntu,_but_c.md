---
title: "Can't connect to Windows network in Xubuntu, but could in Ubuntu (+VirtualBox)"
date: 2014-10-14
forum: New to Ubuntu
---

### Post by xtina-schelin on 2014-10-14
I'm new to this-all, I admit it.

I'm using VirtualBox.  I set up a VM of Ubuntu 14.04.  When I went into the network area, it displayed the network connections as I see them through Windows.  I didn't have to do anything for this to work.

I have a VM of Xubuntu 14.04 now.  I go into the network area, but it sees nothing at all.  :confused:

What am I missing?

Thank you!

---

### Post by TheFu on 2014-10-14
Bridged network or NAT? Check in the VM network settings for the client-OS.
You want "bridged".

UPDATED LATER - this is wrong for the root problem.

---

### Post by xtina-schelin on 2014-10-14
NAT, for Xubuntu.  I can't recall what I had for Ubuntu itself; I'd deleted that VM before I noticed the networking oddness.  I'm rebuilding the Ubuntu VM now to see if there's owt I can compare.

---

### Post by TheFu on 2014-10-14
No need to rebuild anything.
Just change the setting and boot the VM.

---

### Post by xtina-schelin on 2014-10-14
NAT for Ubuntu as well, and yet with that, I go to Network > Browse Network, and it sees my host plus the Windows Network, which sees the CORP network I'm on.  Xubuntu thinks I'm on crack when I try to do anything like the same thing.

---

### Post by ajgreeny on 2014-10-14
Actually I think you need exactly what you've already got, ie, NAT.  Bridged does not work on my Xubuntu 14.04 VM running in VBox on a host Xubuntu 12.04.  What do you get when you run ```
sudo apt-get update
```in terminal of the VM?

Surely your host is seen only by using the shared folders on the VBox system settings for the VMs

As far as I'm aware NAT is the normal connection for a VM irrespective of whether the computer has an ethernet or wireless connection, unless TheFu knows something that I don't

---

### Post by TheFu on 2014-10-14
Ah  .... there is a client-samba package that is needed.  Xubuntu is lighter, so it doesn't install it by default, I'm guessing.  Ubuntu is bloated, so it installs hundreds-thousands of packages you'll never use, just in case.  In this situation, you want it installed.

Might try entering a URL into the xubuntu file manager ( it is a different program than ubuntu uses, right?) - 
smb://server-ip-address/ to see what shares are available too. Different file browsers work differently. I use pcmanfm about once a month for stuff, not daily.  Nautilus is another option and thunar is another. Thunar has a network browser for CIFS shares for me. Don't know why.  It doesn't see NFS shares.

Sorry for the prior wild-goose chase - saw some geese here going south yesterday, BTW. ;)

---

### Post by TheFu on 2014-10-14
> **ajgreeny said:**
> As far as I'm aware NAT is the normal connection for a VM, unless TheFu knows something that I don't

Nope - don't know anything more specifically about that, but ... 

NAT adds another private network for the guestOS systems.  Basically it makes double-NAT and makes it a big hassle to access VMs from other machines on the network. On a 1 machine network, it probably doesn't matter.

However .... using bridged mode puts the VM guestOS onto the same network as the hostOS leveraging that same subnet and usually getting an IP from the network DHCP server (or router).  In bridged mode, other systems can easily get to the guestOSes on VMs.  The host-machine firewall doesn't get in the way at all.  This is easier on home networks with 2 or more physical machines where the owner doesn't think 1 pc = 1 purpose, but the computer IS the network.

Bridged is easier for my needs. About the only time I want NAT for a VM is when I'm testing dangerous-to-the-LAN stuff.

---

### Post by ajgreeny on 2014-10-14
> **TheFu said:**
> Nope - don't know anything more specifically about that, but ... 

NAT adds another private network for the guestOS systems.  Basically it makes double-NAT and makes it a big hassle to access VMs from other machines on the network. On a 1 machine network, it probably doesn't matter.

However .... using bridged mode puts the VM guestOS onto the same network as the hostOS leveraging that same subnet and usually getting an IP from the network DHCP server (or router).  In bridged mode, other systems can easily get to the guestOSes on VMs.  The host-machine firewall doesn't get in the way at all.  This is easier on home networks with 2 or more physical machines where the owner doesn't think 1 pc = 1 purpose, but the computer IS the network.

Bridged is easier for my needs. About the only time I want NAT for a VM is when I'm testing dangerous-to-the-LAN stuff.
Hmmm! Interesting.

So why is it that when I move my VM settings to bridged and not NAT, which I normally use, I can not connect the VM to anything at all; no LAN, no internet, no updates, etc etc?

Am I misunderstanding all this whole business, or just missing some detail in the setup of my VMs?

---

### Post by TheFu on 2014-10-14
@aj - Could it be that the network dhcp server is out of leases?

If the hostOS has a DHCP address of 192.168.1.100/24, and you use a bridged VM with Linux set to use DHCP too, I would expect it to get 192.168.1.101/24 as the IP/network.

With NAT, it would be placed on a different subnet - perhaps 192.168.122.1/24 as the IP/network.

Besides that, can't really say.  There can be confusion between how the hostOS is connected to the network - wired or wifi. Setup the VM for both using NIC-A and NIC-B, then just toggle the "cable connect" for which is working on the hostOS.  Hope that is clear.  Inside the VM, only the virtIO network driver should be used for Linux systems.  This is set in the "advanced" network settings for the VM settings.

---

