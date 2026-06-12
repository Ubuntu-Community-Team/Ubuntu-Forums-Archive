---
title: "Not Connecting"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by 5quid on 2012-01-26
Hello,

I am unable to connect to the internet on my Ubuntu PC. I have another pc beside it running Win7 and when I connect the ethernet to it, it connects just fine. The Ubuntu use to connect, about a year ago, but doesn't anymore. I had to replace the heatsink so that PC was offline for a while, but before I took it offline, it connected just fine. Well, now I can't seem to connect to save my life. The DHCP is set to automatic. It is version... 10.04. I did ifconfig and included a screenshot of it. Any help would be GREATLY appreciated. Thank you.

---

### Post by SuaSwe on 2012-01-26
Hello 5quid!

Is it wireless that's not working? I can't see any wireless instance in your ifconfig (what happens if you do "iwconfig?"). Can you remember if you had to install any proprietary drivers or anything when you first got it working? What happens if you do:

```

sudo ifconfig wlan0 up

```

and/or 

```

sudo lshw | grep -i wlan

```

? Have you checked if there are any proprietary drivers available under 'Additional Drivers'?

---

### Post by SuaSwe on 2012-01-26
Actually, maybe I read that wrong - is it a wired connection that isn't working? If so, was it connected up when you grabbed that screenshot? It doesn't appear to be picking up an IP address. What do you have in the /etc/network/interfaces file?

---

### Post by 5quid on 2012-01-26
Hi Suaswe,

Yes it is a wired ethernet connection. I had it connected when I took that screenshot. I opened the command menu, went into superuser mode, typed in /etc/network/interfaces and it said "permission denied". :/

---

### Post by SuaSwe on 2012-01-26
Hello again!

It's just a text file so if you do the following:

```

cat /etc/network/interfaces

```

... it should display. :) Add sudo before the command if it still says Permission Denied.

Could you also run the following so we can see what hardware you have:

```

lspci -nn | grep -e 0200 -e 0280 > ~/Desktop/hwinfo
sudo lshw -C network >> ~/Desktop/hwinfo

```

Then attach the file to your post. :)

---

### Post by 5quid on 2012-01-26
Okay, here is the screenshot and the hwinfo file. :)

02:0c.0 Ethernet controller [0200]: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 [8086:1229] (rev 10)
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:07:e9:da:f7:db
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:18 memory:fe1fd000-fe1fdfff ioport:ec00(size=64) memory:fe1c0000-fe1dffff

---

### Post by SuaSwe on 2012-01-26
OK, I must say, I'm looking at that and can't see any problems, looks like the config is default and the driver is loaded. Do you have the icon in the top right-hand corner? If you click on it, go to Edit Connections and select your wired connection (e.g. Auto eth0), do you have config similar to:

- Connect automatically ticked; Device MAC same as "serial" in lshw output; cloned MAC address field empty; MTU automatic
- 802.1x Security de-selected
- IPv4 Settings method Automatic (DHCP) with Require IPv4 addressing for this connection to complete ticked
- IPv6 Settings set to Ignore

That's just a copy of my ethernet settings, which work fine!

Moreover, when the ethernet cable is connected to the router, does the ethernet ports on the router and PC light up? Are you trying with the same cable and router port as for the Windows machine? If not, have a go of that!

Anyone else got any ideas? :)

---

### Post by 5quid on 2012-01-26
Yup, all my connections are set the same way as yours. The port lights are on for the router. I took the cable out of the Ubuntu PC and put it in the Win7 PC to see if it was the cable, but it worked fine in that PC and I was able to connect. I don't know what else to try. I really appreciate you giving it a look over though, thank you very much. If I can't get it within a few days, I think I'll just start over with a reinstall. :P  Thank you SuaSwe

---

### Post by SuaSwe on 2012-01-26
Hmm... OK, keeping the ethernet cable connected (I take it the link light is illuminated on the PC side as well as the router, by the way?) what do you get if you do:

```

sudo /etc/init.d/networking restart

```

Then do "ifconfig eth0"? If this doesn't give you an inet addr line (something like 192.168.1.4, for instance), what about this:

```

sudo ifconfig eth0 down
sudo ifconfig eth0 up

```

Then ifconfig eth0 again? I'm rather grasping for straws here, I must admit - really can't see any issues with the output! :D

Three other queries/suggestions I have would be:

1. Have you checked on the router side that it doesn't have anything set up that might affect the connection, such as "permitted devices", or no running DHCP server?
2. If you have the ability to burn a LiveCD either on disc or Startup USB, you could boot into that and see if you get an ethernet connection; if you do, this would suggest that there's some config in your current session that's stopping the connection
3. You could try setting up a fixed IP scheme under the Edit Connections bit (go to IPv4 settings and select Manual), using the default gateway and netmask broadcast by your router (for example 192.168.1.1 / 255.255.255.0) and an available address from the range.

---

### Post by 5quid on 2012-01-26
Yup, the light is on both ends, Router and PC.
Okay, here's what I got after those 2 sets of code, took a SS of both.
Nothing is offset on the router. I have not tried a live cd yet, I will though. I tried a manual IP from the scheme given to my win7 PC, didn't work. :(

---

### Post by varunendra on 2012-01-27
Hi quid,

Just a humble input while *SuaSwe* is away:

When you tried manually setting the IP, make sure you enter all the following info in the Network Manager:

[LIST]
[*]IP: **xx.xx.xx.[COLOR=Red]yy[/COLOR]** (where all the x's are same as those in windows, but yy is different from that of any other device on the network. If unsure, please post the IPs of your windows machine and those you set manually to verify if it is consistent.
[*]Netmask: same as 'subnet' in windows
[*]Gateway: same as in windows
[*]DNS: same again (separated by a comma (,) if there are two)
[/LIST]
If all of these are already okay, then I would recommend to try a live session (either from a live cd or usb) before trying anything else.


With this, I'd leave it to *SuaSwe* again.

---

### Post by SuaSwe on 2012-01-27
Morning!

Firstly, I second Varun's statement. :) Could you submit to us the IP settings you used for Windows and the ones you configured on Ubuntu? I take it these are the only two devices connected to this router? 

Secondly, the only to me unexpected thing I can see in your earlier output is the "no such device" error message when trying to 'ifconfig up' eth0, especially where the 'networking restart' error works. I'm thinking it might be worth researching the interwebs about this error message, which is fairly generic far as I know and could have many different solutions - I've read a few posts in its relation and another bunch of possibilities have appeared: module conflict or other related issue, network interface disabled or misconfigured in BIOS, etc. Have you checked BIOS for anything suspicious regarding the ethernet connection? Also, since the "no such device" error, it looks like your eth0 device is now no longer up; would probably be worth running 'sudo /etc/init.d/networking restart' again to see if ifconfig once again lists it as 'UP BROADCAST MULTICAST' (currently it's listed without the "UP"). 

Other than that, once again, I must advocate the virtues of LiveCD - at least if it works in a live environment we know the issue must be with your install and not with BIOS/hardware. :)

---

### Post by 5quid on 2012-01-27
I tried the next and previous IP in the range, got nothing. I woke up today feeling frisky, so decided to format the drive and reinstall. I have a feeling a file got corrupted or something. Anyways, thanks for all the help. :) Just gonna scratch it and start over since nothing was stored on that pc anyways. ;)

---

### Post by SuaSwe on 2012-01-27
Yay for a fresh install! Out of interest, is its wired connection working now?

---

### Post by 5quid on 2012-01-27
Nope, still not working, but I think I figured out why. Seems weird that I can't get a connection, the cable is good, router good, configurations are good, and my other pc has no problem. So I got to looking, my audio card wasn't working either. I think when I replaced the heatsink and thermal compound, I may have given off a static shock and killed the NIC and Audio card in the process. I didn't protect myself w/ an anti-static cord because it's an old pc. But anyways, that is all I can come up with. Seems logical since the audio card is dead too. Oh well, good excuse to buy a new one. :D

---

### Post by btindie on 2012-01-27
You can check it with the following when the ethernet cable is connected. From a terminal type
```
sudo ethtool eth0
```
At the bottom it'll let you know if the link is detected or not and the speed it's negotiated. If that's no/Unknow then there may be a problem. If it has got a link and it appears connected then try a LiveCD just to be sure.
You have just got the one NIC installed and it's not getting mixed up with another one is it?
```
ifconfig -a | grep ^eth
```
will list all detected ethernet interfaces.
Also check in the BIOS to make sure it's not disabled or anything stupid like that!

---

