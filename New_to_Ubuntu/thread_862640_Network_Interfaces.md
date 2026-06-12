---
title: "Network Interfaces"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Horomancer on 2008-07-17
Hello everyone. I have been having a devil of a time getting my Ubuntu desktop to see my Vista laptop.
When i first used Ubuntu with Gutsy, I manage to view my local network by changing the network interface from Loop Back (lo) to Ethernet Interface (eth0). Since updating to Hardy I have not been able to see my network and trying to configure my Ethernet Interface from System> Administration> Network Tools gives me the error message:

This Interface does not Exist.
Check that it is correctly typed and supported by your system.

Some looking around the forums led me to [this thread]("http://ubuntuforums.org/showthread.php?t=826834&highlight=Network+Interfaces")
I tried the command line towards the bottom of the post:
dpkg --search /etc/network/interfaces

but this did not work. I recieved a read out of:

jackmo@time-control:~$ dpkg --search /etc/network/interfaces
dpkg: /etc/network/interfaces not found.

I've navigated and opened the file through my gui since i'm all thumbs with the command line and below is the contents of the file.

auto lo
iface lo inet loopback






iface eth0 inet dhcp

auto eth0

I have a feeling this is wrong ecspecially after seeing what _sphinx_ had posted in the linked thread.
I do not know what to do from here. Any help would be appreciated.
I have managed to connect to my laptop via the command line

nautilus smb://x.x.x.x

where x.x.x.x is the ip address of my laptop.

---

### Post by Iowan on 2008-07-17
My **/etc/network/interfaces** file looks much like yours (with some extraneous junk I should clean up...).  Your machines(s) gets DHCP address(es)? Static addresses might require additional setup.

---

### Post by Horomancer on 2008-07-17
Yes my machines are DHCP.

---

### Post by johnnybravo666 on 2008-07-17
When you say can't see your network do you mean the windows network? If so the problem is most likely with vista. If you can view your laptop with 'nautilus smb://x.x.x.x' then the problem isn't with the network setup, it's with vista. Can other(non-linux) computers see your vista laptop?

---

### Post by Horomancer on 2008-07-17
I take the vista laptop everywhere for work and have used it in LANs with othr vista machines. At those times the problem is i can be seen, but not directly accessed without using my IP address. In my home network i only have the ubuntu desktop and vista laptop.
I can get neither the laptop nor the desktop to view one another from network places or vista's network map. I've tried many times with all of vista's firewalls off. I can normaly be viewed by other vista machines when my firewall is on and i'm set to private networking.

---

