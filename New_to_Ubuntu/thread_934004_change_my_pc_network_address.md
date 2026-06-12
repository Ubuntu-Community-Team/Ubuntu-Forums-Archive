---
title: "change my pc network address"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by jammin007 on 2008-09-30
Hello all,
  I am a totally newbie to ubuntu and linux. I have change the network address (physical address) in windows to use interet. and it works well. I do not know how to change the network address(physical address) in ubuntu in same computer as its physical address in windows is changed. I am using ubuntu 7.  I tried to change it by command: "sudo ifconfig down" but it shows
"SIOCSIFFLAGS : Permission Denied" .

my etc/network/interfaces shows 

auto lo
iface lo inet loopback


what should i do?

how can i be confirmed that my eth0 physical address/hardware address is changed?


is there any other easy way to do this?
Help me.
Thanks in advance.

---

### Post by jamesrl on 2008-09-30
Most network settings you can change within
System->Preferences->Network Settings
However, it seems that you want to change the MAC address of your ethernet (or wireless) card.  You can see your hardwire address by:

```

ifconfig -a | grep HWaddr

```
(ifconfig -a lists "all" info about your network InterFaces, and grep finds the lines that contain HWaddr).

To change a MAC address add a line to /etc/network/interfaces saying below
the interface you want to change (e.g., if you are changing eth0, add it below the "iface eth0 inet dhcp" line)
```

hwaddress ether 01:23:45:67:89:ab

```
with the MAC address you want.  You'll have to restart networking, by 
```

sudo /etc/init.d/networking restart

```

Also, FYI, ubuntu releases are the date of the release (e.g., 7.04 is the April 2007 release, 7.10 is the Oct 2007), so you probably should specify full decimal (though this stuff shouldn't be particularly release dependent).

---

