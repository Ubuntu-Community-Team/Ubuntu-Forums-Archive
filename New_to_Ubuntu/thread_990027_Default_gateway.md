---
title: "Default gateway?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by garyed on 2008-11-22
I just had Verizon FIOS installed & they supplied a wireless router too.
I've got a linksys wrt54-g router also & am trying to hook it to the Verizon router to give me an the extra ports. I assume it would hook up with no problem but I can't get it to work. I think its because the linksys doesn't get a default gateway from the Verizon router. Anyways what I noticed in Windows/Dos - ipconfig gives me the default gateway (192.168.1.1) of the verizon router but in Linux the route commmand doesn't as you can see below. So my question is why can't Linux find my default gateway when Windows can, dual booting from the same computer? 

gary@dell-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         Wireless_Broadb 0.0.0.0         UG    0      0        0 eth0

---

### Post by Yaspoon on 2008-11-22
Looks like your linux box is using the wrong router for its dhcp have you disabled dhcp on one of the routers? Because they will be fighting to assign ips you from the sounds of it you need to make the linksys listen to the verizon router I don't really know I haven't delt with either of these routers.
Hope that helps

---

### Post by garyed on 2008-11-22
I haven't tried disabling DHCP yet so that will be my next step.
I still can't figure out why I can't get Linux to show my default gateway yet it connects to the internet fine.

---

