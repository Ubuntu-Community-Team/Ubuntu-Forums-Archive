---
title: "[SOLVED] Fresh Install of 8.04LTS Will Not Allow Connectivity To The Internet!"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by suomalainen on 2008-11-17
Ubunteros,

A friend asked me to install Ubuntu 8.04LTS on his old Compaq Presario 5140.

The install process was straight forward and ran smoothly. In the end, I was amazed that Ubuntu ran at all. But it did and with minimal latency. This is an old machine built on 22 April 1998 in the PRC... At least this is what the stamp inside says.....

After any new install I perform, I always search for updates before doing anything else. BUT... the PC would not connect to the Internet. I made sure my RJ-45 connections were correctly connected but still nothing. I then used my laptop as a test to determine that Internet access was available and indeed I was able to get onto a few favorite web sites. I then re-connected the RJ-45 back to the Compaq PC. Still nothing.

I also took a look at the BIOS settings and everything appeared to be in order.

On a PC I own and which runs Ubuntu 8.04, I removed the D-Link Model WDA-1320 Wireless G Desktop Adapter that I had inside and installed it into the Compaq. As a reference note, I have three PC's of various age that all run Ubuntu 8.04LTS. They also all have the WDA-1320 installed in them. When I upgraded each box to 8.04LTS the entire install went without a hitch. As a matter of fact, when I booted for the first time, I received on each machine a message stating that restricted drivers are in use. And of course going through System>Administration>Hardware Drivers this fact can be verified.

To make a long story short the Compaq install of 8.04 did not even see this wireless card. I even went so far as to perform a re-install and still nothing.....

Be it as it may, I want to FORGET about using the wireless card and simply get my LAN (RJ-45) connection working.

Based upon what I have been able to offer thus far, does this appear to be possible to do? If so, would anyone mind walking me through the process.

Many thanks!!! I look forward to your reply.....

---

### Post by kestrel1 on 2008-11-17
double posted, sorry

---

### Post by kestrel1 on 2008-11-17
You need to determine that you are gaining an IP address via DHCP from the router. Type the following in a terminal:
```
ifconfig
```
What is the result?

---

### Post by suomalainen on 2008-11-17
kestrel1,

I got an error message. Please see attached screenshot.

---

### Post by suomalainen on 2008-11-17
kestrel1,

Here are the new results with the command that you asked me to use. 

I don't know what this all means.... so what do you see????


michel@michel-desktop:~$ <CODE>ifconfig</CODE>
bash: syntax error near unexpected token `newline'
michel@michel-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:d0:00:dc:57  
          inet6 addr: fe80::240:d0ff:fe00:dc57/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:157 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x2000 

eth0:avahi Link encap:Ethernet  HWaddr 00:40:d0:00:dc:57  
          inet addr:169.254.7.4  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14592 (14.2 KB)  TX bytes:14592 (14.2 KB)

---

### Post by suomalainen on 2008-11-17
Does anyone know what these results mean? kestrel1, asked me to report them and as I was waiting for feedback s/he left without word.

Any assistance would be appreciated.

---

### Post by mapes12 on 2008-11-17
For whatever reason you are not getting a valid Private IP address from your router. The valid ranges are:

        * 10.0.0.1 through 10.255.255.254
              o 16,777,214 addresses
              o 16,777,214 computers on 1 network
                (10.x.x.x)
              o Uses a subnet mask of 255.0.0.0
              o First octet must be the same on all computers
              o A Class A address range 

        * 172.16.0.1 through 172.31.255.254
              o 1,048,574 addresses
              o 65,534 computers on each of 16 possible networks
                (172.16.x.x to 172.31.x.x)
              o Uses a subnet mask of 255.255.0.0
              o First two octets must be the same on all computers
              o A Class B address range 

        * 192.168.0.1 through 192.168.255.254
              o 65,534 addresses
              o 254 computers on each of 256 possible networks
                (192.168.0 to 255.x)
              o Uses a subnet mask of 255.255.255.0
              o First three octets must be the same on all computers
              o A Class C address range 

These are normally assigned by a DHCP server within your router. 

Are you working on a system with static IP addresses?

What is the output from:```
sudo dhclient
```

---

### Post by suomalainen on 2008-11-17
Below is the information that Mapes12 had asked me to run via Terminal.

But s/he has gone off line now. Is there anyone else out there that can analyze the data for me? See also attachment.

Thank you!

michel@michel-desktop:~$ sudo dhclient
[sudo] password for michel: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:40:d0:00:dc:57
Sending on   LPF/eth0/00:40:d0:00:dc:57
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
michel@michel-desktop:~$

---

### Post by suomalainen on 2008-11-17
Hello again Everyone!!!

I wanted to point out that I believe my cable provider provides my with a "dynamic address".

I have things arranged this way.

1. Broadband high speed Internet cable connected to Motorola SURFboard Cable Modem Model: SB5101

2. Motorola Cable Modem is connected to D-Link Ethernet Broadband Router Model: DI-604. Currently, one PC is connected to the D-Link Router. HOWEVER, I also have a Linksys Wireless-G Broadband Router Model:WRTP54G which is also connected to the D-Link. The Linksys Router provides me with Vonage telephone service and also Wifi access. The Linksys also has four (4) RJ-45 ports to connect to.

The Compaq PC that I'm having trouble connecting to the Internet was connected to the Linksys Router when I executed Mapes12's  "sudo dhclient" request.

With this point in mind, I wondered if anything would change if I connected the Compaq directly to the D-Link Router as the D-Link is connected dirtectly to my Motorola broadband modem. But this didn't work either. I still could not connect to the Internet.

I also ran again the "sudo dhclient" command while connected to the D-Link Router and it appears the results are the same as when the Compaq was connected to the Linksys Router. See results below and attached.

If anyone is able to tell me if I'm heading in the right direction that would be awesome. I would also like to understand what the results of the commands that others asked me to run fully mean?

I'm at a loss......

Thank You!!!!



michel@michel-desktop:~$ sudo dhclient
[sudo] password for michel: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:40:d0:00:dc:57
Sending on   LPF/eth0/00:40:d0:00:dc:57
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
michel@michel-desktop:~$

---

### Post by Shazaam on 2008-11-17
More fiddling with wires sorry...
Plug the Compaq directly into the cable modem (Motorola) and see what happens. If it connects then you have a configuration problem with your router(s).

---

### Post by suomalainen on 2008-11-17
Shazaam,

Thanks for the note. I performed the action you requested and determined that the PC will still not connect to the Internet even if via the Motorola modem....

Have any idea what to do next?

Thank You

---

### Post by suomalainen on 2008-11-17
Anyone know how I can get this PC online?

---

### Post by kestrel1 on 2008-11-18
You need to ensure that your router is setup to give out IP addresses via DHCP. It probably is, but you never know. You need to know the IP address of your router & type that in to a web browser. It will probably be something like 192.168.0.1, but you need to set your machine to use the same type of IP address & subnet mask.
To do this go to System - Preferences - Network Configuration & then select eth0 & click edit.
On my 8.10 system I select IPv4 Settings & set the method to Manual then click on Add & enter a valid IP address, subnet mask & gateway. The gateway would normally be that of your router.
For your IP address use something like 192.168.0.2 With a subnet mask of 255.255.255.0
Once this is set you should be able to gain access to your router via a web browser by typing in its IP address.

---

### Post by suomalainen on 2008-11-18
Below are some stats on the way my Router is set up.

PLEASE CONFIRM IF ANY INFORMATION IS PRESENT THAT WOULD BE USEFUL TO A HACKER SO THAT I CAN GET FORUM STAFF TO REMOVE SUCH INFORMATION FROM THIS POST!

As can be seen from the post before this one, Kestrel1, asked that I perform some exercises that should enable my PC to connect to the Internet. However, as stated in that post above the user is using Ubuntu 8.10. In turn, not one of the references explained in that post was met with success. Unfortunately for me, the only steps that were correct were System--> Preferences. After that nothing as described in the post could be found... Not even closely found!!!

I'm using Ubuntu 8.04LTS.

Please don't lead me on a wild goose chase. If you can help then please offer concrete information that I can work off of. It would even be nice to know what we are doing, so if you ask me to do a "Terminal" command please explain what we are looking for so we are singing off the same sheet of music.

I will be more than happy to acknowledge your kind help and assistance by submitting a "Thank You" offered via this post.

Thank You!


LINKSYS DI-604 Ethernet Broadband Router

LAN
MAC Address 
	XXXXXXXXXXXXXXXXXXXXXXXXXx
IP Address 
	192.168.0.1
Subnet Mask 
	255.255.255.0
DHCP Server 
	Enabled
  	 
WAN
MAC Address 
	XXXXXXXXXXXXXXXXXXXXXXXx
Connection 
	DHCP Client Connected  
IP Address 
	XXX.XXX.XX.XXX
Subnet Mask 
	255.255.248.0
Default Gateway 
	XXX.XX.XXX.XXX
DNS 
	XXXXXXXXXXXXXXXXXXXXXXXXXX

---

### Post by suomalainen on 2008-11-18
Can someone help me connect to the Internet please?

---

### Post by kestrel1 on 2008-11-18
I am now working on my 8.04lts machine, so hopefully this will be more accurate.
From the above I can see that your router has an IP address of 192.168.0.1
Where did you get the information? I assume you got it from the documentation that came with your router.
Also you have DHCP turned on which is good, but I cannot understand why you are not getting an IP address when connected to the router. If your network card has been installed correctly & the drivers are present you should get an IP address when you connect your computer to the router via ethernet cable. Are you sure that you ethernet cable is OK?
To ensure that your network card is set to pick up an IP address via DHCP do the following (shouldn't be a wild goose chase)
Go to System - Administratoin - Network
Once you have this screen open you will need to unlock it by clicking Unlock & entering your password.
Click on the Wired Connection & select Properties
Make sure that Enable Roaming Mode is ticked. You may then need to reboot unless you get a connection.
If it is already set to roaming mode untick the box & in the configuration select Automatic Configuration (DHCP).
To do this I would suggest that you are directly connected to your cable router.
Let us know what happens.

---

### Post by suomalainen on 2008-11-18
kestrel1,

192.168.0.1 along with User Name and P/W grants user access directly to the router where specific data can be found. This is how I got the info from the Router that I posted earlier.

The ethernet cable is working. I even tested it using a laptop and PC. It works. I'm connected also right into the router itself. 

I made the changes you requested in System - Administratoin - Network

and still nothing :<.... I even re-booted a few time and no Internet. Even checked that changes made in System - Administratoin - Network held and they were there but no Internet....

What you think it is?

---

### Post by suomalainen on 2008-11-18
F.Y.I.

When I went back to System - Administratoin - Network to check the properties for "eth0 Properties" The "connection Settings" label "configuration" had "Automatic Configuration (DHCP) but the "Enable roaming mode" was un-ticked. When I ticked the empty box then all settings "Grayed" out.

I looked this in my other Ubuntu 8.04LTS PC with is connected to the internet and this is the way it seems to be.

My Working PC which is connected to the same router only has the "Enable roaming mode" box ticked. Everything else is grayed out.

Hope this helps.........

---

### Post by kestrel1 on 2008-11-18
I must say that mine has only ever worked with the roaming mode turned on, so I would stay with that.
What network card is installed or is it onboard?
If it is onboard is it enabled in the BIOS?

---

### Post by suomalainen on 2008-11-18
Thank you for the reply.

The card is built into the motherboard and is "on" in BIOS.

I have another card that I did install into a vacant PCI slot, only problem was that when I booted the machine the card would load itself but then, in one way or another, prevented Ubuntu from starting up.

I thus removed the card and then Ubuntu started up just fine.

I'm gonna try to stick to the onboard card.

What can we try next?

---

### Post by kestrel1 on 2008-11-18
Now you are connected to the cable router directly, what do you get from the following commands
```
sudo dhclient
```
```
ifconfig
```
```
ping 192.168.0.1
```

with the last command use Ctrl & C to exit
I expect you will not get a response with the last command, but leave it for a few seconds before pressing Ctrl & C to exit.

---

### Post by suomalainen on 2008-11-18
kestrel1,

I knew that my card was "enabled" in the BIOS because I checked it. Then I thought that maybe this is why Ubuntu could not boot when I had the previous card installed? 

Regardless, because of these "key words" I remembered that I had an old Amstrad laying around and so I got the LAN card out of it and installed it into the Compaq. This time I disabled the onboard LAN in BIOS.....

The result this time whether it be due to the correct install of VERY out dated components or not was success nonetheless.

I can now connect to the World Wide Web!! :>

I sent you a thank you as you may have noticed so this takes you from 18  to 19....

I'll make this post as solved when or if I hear back from you. Thanks for the help on this one!!!

---

### Post by suomalainen on 2008-11-18
P.S.

So what's this mean? The onboard card is bad or what?

---

### Post by kestrel1 on 2008-11-18
I would think there are two possible conclusions to the onboard card:
1) The card is bad as you suggest
2) The chipset for the net interface is not supported in Ubuntu.
My next suggestion was going to be, get another PCI card & try it, but not the one you tried previously. You beat me to it :lolflag:
Glad you got it working & thanks for the thanks \\:D/

---

### Post by suomalainen on 2008-11-18
No... Thank YOU! :guitar:

And now to the Internet :popcorn:

Thanks again!!!!

---

