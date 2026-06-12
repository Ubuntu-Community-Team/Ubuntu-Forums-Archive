---
title: "Time to get internet working! :D"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by Skyker on 2008-09-26
Ooooo yeah, I finally installed Xubuntu on a separate partition than my XP pro.  I haven't re logged onto XP to see how that came out after the install, but I've been playing around with Xubuntu.

Now for the daunting task for getting my wireless USB device to hook up to my dad's wireless router!  Yaaay! *confetti*
:lolflag:

Well, I have all the settings entered into the Network manager thinga magjigga.  Where do I go from here?  Dad's router isn't registering anything from my USB thinga.  And I have no internet.

Please tell me where to start in finding out what to do so that I can start this process of getting it to work.

Here's some general info I found on the box of both router and USB thinga.

802.11 b/g 2.4GHz, UR055 USB device. The brand is INEXQ (I think?). (not sure how much of this info is needed :P)

Wireless router info:
brand: Network Everywhere
standards: IEEE 802.3, IEEE 802.3u, IEEE 802.11b
Model: NWR04B

and a setup wizard CD was included in the box...

*rubs hands together and prepares for an ordeal*

---

### Post by Sycron on 2008-09-26
Is the ip dinamically assigned  ?

---

### Post by Skyker on 2008-09-26
dinamically?  dynamically?  I'm not sure what you mean.  Please keep in mind that I'm such a complete newb :P  But I do have the ip address for the router entered in.
s
Just read some other people's threads about how they got their wireless to work through ndiswrapper and ndisgtk, should I look into this?

---

### Post by Sycron on 2008-09-26
The ip address is asigned by DHCP ?

---

### Post by halitech on 2008-09-26
first, lets make sure xubuntu is actually seeing the usb device. open a terminal and with the usb adapter not plugged in, type the following```
lsusb
```then plug the usb adapter in, wait a minute and do the same again and then post the information back here

---

### Post by Sycron on 2008-09-26
If ubuntu recognize the wireless drives then you don't have to use ndiswrapper.

---

### Post by NullHead on 2008-09-26
> **halitech said:**
> first, lets make sure xubuntu is actually seeing the usb device. open a terminal and with the usb adapter not plugged in, type the following```
lsusb
```then plug the usb adapter in, wait a minute and do the same again and then post the information back here

+1 I was about to suggest the same exact thing :)

---

### Post by halitech on 2008-09-26
I've seen so many threads where people are having them try to install ndiswrapper and wicd and other crap only to find the device isn't even seen so I always go with the basics first :D

---

### Post by Skyker on 2008-09-26
> kimberley@kimber:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
kimberley@kimber:~$ lsusb
Bus 002 Device 004: ID 1435:0711  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000


voila!  It took awhile to get the damn thing to write to my mem stick, but I did it :D

thanks for starting from square one with me.  This way I can learn and understand better :D

---

### Post by halitech on 2008-09-26
ok, the fact that the usb adapter is being seen is a good thing :)

lets see if its been setup already for the network (thus negating the need to install drivers). in a terminal type```
ifconfig
``` and post back to us

edit: did some searching and it *looks* like the device uses the ZD1211 chipset which is similar to one I had. I honestly can't remember if I ever got it working so not sure if it will work or not but certainly won't give up on you :)

---

### Post by Skyker on 2008-09-26
> kimberley@kimber:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:07:95:12:cb:3d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:10:a7:2d:f6:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:21 dropped:0 overruns:0 frame:21
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:239 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15061 (14.7 KB)  TX bytes:15061 (14.7 KB)


^^ makes no sense to me, but I'm sure you can decipher it.:)

---

### Post by halitech on 2008-09-26
strange, it seems to be seeing 2 wired network adapters....

is the laptop plugged direct to the router right now? it will be easier to get things working if we can for the moment.

try this and post the results```
iwconfig
```

---

### Post by Skyker on 2008-09-26
there's no way to directly connect my computer upstaires to the router which is here, downstaires.  AM on my dad's computer lol.  and its a desktop computer, not a laptop.  And I'm not sure, but there MIGHT be an ethernet card, I really can't remember, but I'll go pull it out from the wall and have a look.  (dad refuses to go out and buy cables required for hooking it up physically >.>)
```

kimberley@kimber:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by NullHead on 2008-09-26
It looks like it's working. Post the output of: ```
iwlist scan
```

---

### Post by Skyker on 2008-09-26
```
kimberley@kimber:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0C:41:1A:90:92
                    ESSID:"cybercycle"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=100/100  Signal level=82/100  
                    Extra: Last beacon: 68ms ago

```

maybe I input something wrong, or maybe we need to set up the router to recognize the USB device again...  Anyways, I tried to configure it to the best of my ability...

---

### Post by halitech on 2008-09-26
it is already seeing the router, looks like its just a matter of getting it to connect. Do you know if the router is set up with any password protection like WEP or WPA?

---

### Post by Skyker on 2008-09-26
yep, it has encryption.  Wow this is alot easier than i thought, I guess I just have to make sure I have the right WEP in.  though i though i did.

---

### Post by halitech on 2008-09-26
I think you got lucky with your wireless card, most don't go quite this easy ;)

try these steps```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```

its from this thread: [http://ubuntuforums.org/showthread.php?t=684495&highlight=wep](http://ubuntuforums.org/showthread.php?t=684495&highlight=wep)

---

### Post by Skyker on 2008-09-26
OKAY.  So I went on Xubuntu and changed the WEP password.  After that, ZoneAlarm came up on this computer (XP pro) asking me if I wanted to let a new network connection access this computer.  So I said yes.  I still didn't get any internet access upstairs (Xubuntu), but the internet down here stopped working.  The page would either not load, or would continuously 'load' and never actually do anything.  So I unchecked the box on my network manager upstairs (Xubuntu) and VOILA the internet down here (XP) works again.

I don't know whats wrong.

I assume the network works in some way, but its just not going...  *frazzled*

---

### Post by Skyker on 2008-09-26
in the code provided, do i need to change <interface>?

And I'm assuming HEX_KEY is where i put my WEP passcode thing.

---

### Post by cardinals_fan on 2008-09-26
> **Skyker said:**
> in the code provided, do i need to change <interface>?

And I'm assuming HEX_KEY is where i put my WEP passcode thing.
Yes.  Change <interface> to "eth1" (without quotes).

---

### Post by Skyker on 2008-09-26
do i need to put it in < and >  or just by itself?

---

### Post by taladan on 2008-09-26
I don't know if it comes with ubuntu as a default, but if you've got a hardwire you can plug it into for the moment to get net access, you can always

```
sudo apt-get install wlassistant
```

However it should be noted that wlassistant is listed as a front end for wireless lan management for KDE - it's going to dl all the kde libs that it needs to be able to run, so this may not be something that you want to do if space is an issue on your drive.  I know that I use it with my laptop on Kubuntu 7.10 and then 8.04 and it works flawlessly though.

Something to think about maybe.

Tal

---

### Post by cardinals_fan on 2008-09-26
> **Skyker said:**
> do i need to put it in < and >  or just by itself?
Just by itself.

---

### Post by Skyker on 2008-09-26
```
 kimberley@kimber:~$ sudo ifconfig eth1 down
[sudo] password for kimberley: 
kimberley@kimber:~$ sudo ifconfig eth1 down
kimberley@kimber:~$ sudo dhclient -r eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:10:a7:2d:f6:43
Sending on   LPF/eth1/00:10:a7:2d:f6:43
Sending on   Socket/fallback
kimberley@kimber:~$ sudo ifconfig eth1 up
kimberley@kimber:~$ sudo iwconfig eth1 essid "cybercyle"
kimberley@kimber:~$ sudo iwconfig eth1 key 123456789A
kimberley@kimber:~$ sudo iwconfig eth1 mode Managed
kimberley@kimber:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:10:a7:2d:f6:43
Sending on   LPF/eth1/00:10:a7:2d:f6:43
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I followed the steps and this is what I got.  Any explanation or further help?

---

### Post by Skyker on 2008-09-26
anyone? ... ._.

---

### Post by cardinals_fan on 2008-09-26
**Reboot** and try the following again:```
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "cybercyle"
sudo iwconfig eth1 key 123456789A
sudo iwconfig eth1 mode Managed
sudo dhclient eth1
```

---

### Post by Sycron on 2008-09-27
Well, it works ?

---

### Post by Skyker on 2008-09-27
```
kimberley@kimber:~$ sudo ifconfig eth1 up
[sudo] password for kimberley: 
kimberley@kimber:~$ sudo iwconfig eth1 essid "cybercyle"
kimberley@kimber:~$ sudo iwconfig eth1 key 123456789A
kimberley@kimber:~$ sudo iwconfig eth1 mode Managed
kimberley@kimber:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:10:a7:2d:f6:43
Sending on   LPF/eth1/00:10:a7:2d:f6:43
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

now what? :P

---

### Post by cardinals_fan on 2008-09-27
> **Skyker said:**
> ```
kimberley@kimber:~$ sudo ifconfig eth1 up
[sudo] password for kimberley: 
kimberley@kimber:~$ sudo iwconfig eth1 essid "cybercyle"
kimberley@kimber:~$ sudo iwconfig eth1 key 123456789A
kimberley@kimber:~$ sudo iwconfig eth1 mode Managed
kimberley@kimber:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:10:a7:2d:f6:43
Sending on   LPF/eth1/00:10:a7:2d:f6:43
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

now what? :P
Your router seems to be refusing the DHCP connection.  I'm not really an expert on wireless stuff, so maybe somebody else can explain why...?

---

### Post by Skyker on 2008-09-27
I'll take this over to the wireless section and see if I can't get some help.  thanks anyways :)

---

### Post by Sycron on 2008-09-28
Well good luck.

---

### Post by halitech on 2008-09-28
Have you tried rebooting the roouter and the system? I find mine was cranky at times and a reboot on the router fixed things up.

also, if you can, try disabling the WEP and see if it will connect without it.

---

### Post by Skyker on 2008-09-28
I'll give it a go, thanks for the patience and help. :)

---

