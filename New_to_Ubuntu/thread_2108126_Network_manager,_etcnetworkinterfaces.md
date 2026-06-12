---
title: "Network manager, /etc/network/interfaces"
date: 2013-01-23
forum: New to Ubuntu
---

### Post by Cthulu2156 on 2013-01-23
I have been experimenting with the interfaces file to tweak my connection.  It just wasn't a good connection before and now it is great.  I added the following to the file
auto lo
iface lo inet loopback
dns-nameservers 8.8.8.8 8.8.4.4

however have to use dhclient to get the connection working really well, found this and was thinking about adding it
auto eth0
iface eth0 inet dhcp

don't know if that will work.  My real question is, what are these commands?  Would it be something written in python?  Or some other commands?  I am trying to research it but there is nothing out there about this.  What kind of script it it?

---

### Post by tgalati4 on 2013-01-23
```
man interfaces
```

Depending on what desktop environment you are running, there are graphical user interfaces (gui's) to change them.  Look in your Control Panel.

From a Dapper Drake machine with static address:

tgalati4@tubuntu2:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet static
address 192.168.1.114
netmask 255.255.255.0
gateway 192.168.1.1

And in Quantal Quetzal: (with dhcp)

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
man ifup
```

---

### Post by Cthulu2156 on 2013-01-23
That helps a lot, thanks.  I was not aware of a man page for interfaces, there are a ton of files, and I honestly can't even remember how I found the interfaces file.

---

### Post by steeldriver on 2013-01-23
Just a word of caution - newer desktop editions of Ubuntu use a whole different service (network-manager) which is configured via the GUI applet (and uses config files in /etc/NetworkManager) - that's why the default /etc/network/interfaces file only contains a definition for the loopback (lo) interface.

If you want to manually set DNS servers for a connection that's managed by network-manager, then the right place to do that is to edit the connection via the applet and change the IPv4 settings from 'Automatic (DHCP)' to 'Automatic (DHCP) addresses only' and then input your DNS server IP(s) in the box(es) provided

---

### Post by Cthulu2156 on 2013-01-23
I did try that, but there was no change in my connection, the only thing that made the connection better was by adding the DNS info to the interfaces file, but then I still had to start the dhclient which was in another thread, I know the dhcp should be  working with what is already in the interfaces file, but for some reason worked better when I used dhclient, I'm not sure why it is better but it's much faster now.  This is what I have in my interfaces file

auto lo
iface lo inet loopback
dns-nameservers 8.8.8.8 8.8.4.4
auto eth0
iface eth0 inet dhcp

which I'm guessing just gets dhcp working with the dns nameservers i am using

---

### Post by tgalati4 on 2013-01-24
Interfaces is a legacy configuration file used in the "old days" of linux.  However, I believe it is still used for server installs and lightweight distros.  So just be mindful that network configuration is slightly different for each distro.

Also realize that dhcp is a client-server process.  If the server (a router that hands out IP addresses) is having issues then you will have issues on your machine (the dhcp client).  Without knowing anything about your dhcp server, it's hard to troubleshoot this issue.

---

