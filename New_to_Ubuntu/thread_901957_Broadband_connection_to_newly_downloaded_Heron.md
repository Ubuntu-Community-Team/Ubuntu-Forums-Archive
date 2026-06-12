---
title: "Broadband connection to newly downloaded Heron"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by James Lee on 2008-08-26
I'm trying to get Heron working. I tried Wubi back in September and got help from this site but for one reason or another had to give up. I have just rebuilt my system with XP Pro which is attached to broadband and works OK. I have the IP, S/Net, G/Way and P and A server addresses. I have now downloaded Heron and am trying to connect it to the broadband.
I went System/Administration/Network and wanted to select Wired Connection but all the options were unavailable. I tried clicking on "Unlock" expecting that this might make the options available. This gives me an "Authenticate" screen asking for my password. Sometimes before I enter the password and, if not then, after I enter the password, I get a message "Could not authenticate, an unexpected error has occurred".
I checked the modem connection                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             using 192.168.100.1 and everything seems OK. When I try the Firefox icon I get the message "Firefox cannot find the server."
Please can anyone tell me 1. If I'm trying the right things, 2. if so what might the problem be and how might it be addressed or 3. (more likely) what I am doing wrong and suggest what I should be doing.
I'll be very grateful for any and all advice.

James Lee

---

### Post by damis648 on 2008-08-26
Hover over the NetworkManager icon in the notification applet of your top panel. What is the status it gives?

---

### Post by nicedude on 2008-08-26
Here I will break it down for you,

I'm trying to get Heron working. I tried Wubi back in September and got help from this site but for one reason or another had to give up.  ( I hear ya Wubi stinks and is not a true install at all )



I have just rebuilt my system with XP Pro which is attached to broadband and works OK. 
(good deal )

I have the IP, S/Net, G/Way and P and A server addresses. I have now downloaded Heron and am trying to connect it to the broadband.
(at this point you should have to do nothing but put the Ethernet cord in the network connector of your PC, Unless you are using a DSL PPPOE modem to try and connect )

I went System/Administration/Network and wanted to select Wired Connection but all the options were unavailable. I tried clicking on "Unlock" expecting that this might make the options available. 

( yep because you need to be an admin to unlock them )

This gives me an "Authenticate" screen asking for my password. Sometimes before I enter the password and, if not then, after I enter the password, I get a message "Could not authenticate, an unexpected error has occurred".

( um are you the admin of this box and if so it looks like you forgot your password - oops )

I checked the modem connection using 192.168.100.1 and everything seems OK. When I try the Firefox icon I get the message "Firefox cannot find the server."

( because it is not connected - as in your internet is non-functional )

Please can anyone tell me 1. If I'm trying the right things, 

(NOPE)

2. if so what might the problem be and how might it be addressed 

( Uh what kind of internet do you have DSL or CABLE etc - If DSL then I would bet it is a PPPOE connection & authentication problem )

3. (more likely) what I am doing wrong and suggest what I should be doing.

( Nothing wrong since you asked here as that is the right place for it :-) )

But in general try posting the output of the following commands to let everyone see what is the state of your connection as well as tell us if you have DSL or not since that could also be the problem ( as in bad PPPOE setup )

ifconfig

lshw -C Network

Please post the outputs of those commands as well as if you have DSL and maybe I can spot what is wrong ( In general though wired Ethernet works with no extra help so yours makes me lean toward PPPOE problem )

nciedude

---

### Post by James Lee on 2008-08-27
To damis648 and nicedude

Thank you both for your very prompt responses and I've tried to work on your suggestions.

damis648

I'm afraid I'm somewhat of a newbie on unix et al and I've not been able to work out how I get to the NetworkManager icon. I've tried Network and Network Tools but without any success. Please can simplify it a bit for me? Many thanks

Best regards

James Lee


nicedude

I understand I am using CABLE together with cable TV and telephone.

This is the output for ifconfig

eth0 Link encap:Ethernet HWaddr 00:16:36:20:bc:ef
inet6 addr: fe80::216:36ff:fe20:bcef/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:14122 errors:0 dropped:0 overruns:0 frame:0
TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:856098 (836.0 KB) TX bytes:5945 (5.8 KB)
Interrupt: 16 Base address:0x1800

eth):avahi Link encap Ethernet HWaddr 00:16:36:20:bc:ef
inet addr:169.254.8.126 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
Interrupt:16 Base address:0x1800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2245 errors:0 dropped:0 overruns:0 frame:0
TX packets:2245 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:138886 (135.6 KB) TX bytes:138886 (135.6 KB)


I tried several variations on the ishw -C Network as follows:

jim@jim-laptop:~$ ifconfig ishw -CNetwork
-C: Unknown host
ifconfig: `--help' gives usage information

jim@jim-laptop:~$ ifconfig ishw
ishw: error fetching interface information: Device not found

jim@jim-laptop:~$ ifconfig -CNetwork
ifconfig: option `-CNetwork' not recognised
ifconfig: `--help' gives usage information

You ask about who is the admin of this box and whether the password may have been forgotten. I can only say that I have only entered Jim as the computer name and a password during the instal process. I have to use both of these to access the system when I power up and that works. Is there some process where I have to explicitly take admin authority which I have so far not perhaps done?

Many thanks for your help and I look forward to your comments for which I would like to thank you in anticipation

Best regards

James Lee

---

### Post by James Lee on 2008-08-29
On reviewing and checking my response above I realised I goofed with the lshw command. On running it as lshw I get:

WARNING: you should run this program as super-user
 *-network:0
    description: Ethernet interface
    product: SiS900 PCI Fast Ethernet
    vendor: Silicon Integrated Systems [SiS]
    physical id: 4
    bus info: pci@0000:00:04.0
    logical name: eth0
    version: 91
    serial: 00:16:36:20:bc:ef
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master cap_list ethernet physical
    configuration: broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 latency=173 maxlatency=11 mingnt=52 module=sis900 multicast=yes
 *-network:1
    description: Network controller
    product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
    vendor: Broadcom Corporation
    physical id: b
    bus info: pci@0000:00:0b.0
    version: 02
    width: 32 bits
    clock: 33MHz
    capabilities: bus_master
    configuration: driver=b43-pci-bridge latency=64 module=ssb
 *-network DISABLED
    description: Wireless interface
    physical id: 1
    logical name: wlan0
    serial: 00:16:ce:55:dc:19
    capabilities: ethernet physical wireless
    configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

Hope this is helpful, apologies for the delay, look forward to your response, many thanks, best regards

James Lee

---

### Post by ugm6hr on 2008-08-29
Your ethernet card should be supported by Ubuntu (sis900 driver).

Does it work in the LiveCD of Ubuntu?

> I checked the modem connection using 192.168.100.1 and everything seems OK.
What does this mean?  I'm afraid you are going to have to explain yourself much more clearly if anyone is to have a hope of helping you.

In any case - I would suggest you read point 8 of this: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)

---

### Post by James Lee on 2008-08-31
Thank you for your response, I have been working on the things you suggested.

1. I don't have a LiveCD for Ubuntu as I downloaded a Wubi version.

2. I found the 192.168.100.1 address when I was roamimg around looking for help. The recommendation was to use it to check the modem connection. I was told to enter it into the Firefox browser after I got Ubuntu working and check the results. I got a table saying all the items except one were done. The odd item told me that the cable modem status was operational.

3. I have ACPI on my machine and am trying to find out more about the issue you raised.

Are you able to suggest anything specific, I'll be very grateful for any ideas. Look forward to your response and would like to thank you in anticipation, best regards

James Lee.

---

### Post by ugm6hr on 2008-08-31
I'm afraid I know very little about Wubi.

I also didn't realise that there was a "Wubi" version.  Wubi is included on the LiveCD, as far as I know.

---

