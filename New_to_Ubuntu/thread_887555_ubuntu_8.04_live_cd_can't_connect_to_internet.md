---
title: "ubuntu 8.04 live cd can't connect to internet"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by no_idea on 2008-08-12
Hello all you ubuntu gurus out there :) I've just burned an ubuntu 8.04 live cd and after booting i've noticed that the internet isn't working. It's ok when booting from windows, though.
I've tried to set DHCP mode (this is how i connect when in win), but still nothing.
Please, I beg you, I need heeeelp!!!

---

### Post by brujoand on 2008-08-12
are you on cable or wirelesss?

---

### Post by no_idea on 2008-08-12
cable

---

### Post by gjoellee on 2008-08-12
well thats weird, are you sure it is connected properly?

---

### Post by brujoand on 2008-08-12
well it should just work.. as long as there is a DHCP server running at the router.. You could try to go to a terminal and type "sudo dhclient eth0" 
( appli.. -> acces.. --> term.. )

but then again.. it could be that the live cd is messing up.. thats not unheard of.

---

### Post by no_idea on 2008-08-12
So it should just work? I'll boot and try again but if it doesn't I should try and install ubuntu on my HDD? (Even though i have less than no idea about how to do this but this is another thread i guess..) Or if i burn another cd and try again? Is it possible that the cd i have now is somehow messed up?

---

### Post by no_idea on 2008-08-12
Yes, gjoelle, I think it is connected properly since the internet is working under windown i mean windows :D. That CAT5 cable can't just go insane.. can it? :confused:
What to do? :((

---

### Post by LowSky on 2008-08-12
run this command, your ethernet card may not be natively supported but lets find out what hardware you have. Try rebooting the router (unplug power wait a minute the plug back in)
type this command in a terminal window Applications> Accessories> Terminal
```
lspci
```
then pleas epost here

---

### Post by hvac3901 on 2008-08-12
Something happened to my wireless under 8.04, it gets on some networks but doesn't work at home, on my 2-wire DSL, IT DID WORK UNDER Gutsy Gibon. 

err.....nevermind, your talking wired network.

---

### Post by Riffer on 2008-08-12
Do you have a proxy?

---

### Post by no_idea on 2008-08-12
No proxy, Riffer.

---

### Post by 7raTEYdCql on 2008-08-12
I had some kind off problem myself connecting to the net, being on cable. Read some help pages and that helped. If you are connected via pppoe then you can use the command
```
sudo pppoeconf
```

---

### Post by 7raTEYdCql on 2008-08-12
I had some kind off problem myself connecting to the net, being on cable. Read some help pages and that helped. If you are connected via pppoe then you can use the command
```
sudo pppoeconf
```

---

### Post by no_idea on 2008-08-12
I ran sudo dhclient eth0 and this is what i got:
```
ubuntu@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d3:8f:6e:57
Sending on   LPF/eth0/00:16:d3:8f:6e:57
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

And I also ran lscpi and this is what i got:
```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

what does this mean? Please please help me!!!

---

### Post by no_idea on 2008-08-13
Please somebody tell me what to do!! I really can't manage by myself and I really need this up and running
So please heeeeeeelp!!

---

### Post by brujoand on 2008-08-13
Well the only things left to check, is 
- that the dhcp server on your router is really running. Beacuse the lspci output shows that your ethernet card is recognized and therefore, the appropriate drivers are in place.. 
- that the drivers are restricted and if that is the case, there should be a green "motherboard" looking thing up in the right part of the taskbar. 

I guess thats all i've got

---

### Post by no_idea on 2008-08-13
> that the dhcp server on your router is really running. Beacuse the lspci output shows that your ethernet card is recognized and therefore, the appropriate drivers are in place..
check, because everything works fine in win
> that the drivers are restricted and if that is the case, there should be a green "motherboard" looking thing up in the right part of the taskbar.

check too because at startup i get some message about restricted drivers and i do have that green thing showing on the taskbar

so i guess i just have bad luck...

---

### Post by nothingspecial on 2008-08-13
You need to enable the driver. Click on the green thingy and put a tick in the boxes next to the restricted drivers.

---

### Post by Crafty Kisses on 2008-08-13
Post these outputs:
```
lshw -C network
```
Then this one if you have a wired connection:
```
ifconfig
```
Then this one if you have a wireless connection:
```
iwconfig
```

---

### Post by no_idea on 2008-08-13
I finally got it :D I took the static network setting from windows (IP subnet mask and so on) and I put them in Ubuntu and it works!!
This is officially my first Internet session from Ubuntu :D
Thanks to everybody for their help :)

---

