---
title: "[SOLVED] WLAN does not function after Ubuntu Installation?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by germanix on 2008-07-23
Up until a few hours ago my WLAN functioned without any problem. I had both Windoes XP and Ubuntu installed on the laptop and both connected. I then installed Ubuntu new,de-installed xp and gave Ubuntu the whole HHD. Normally I configure the WLAN with an installation CD that came with the router. This installation CD however, does not start automatically and open the installations assistant, as normal under windows. It now only puts an icon on my desktop. When I open it there are many files but none of them will start the programm. I am now at a loss as to how to get the WLAN to function. My router is WAP2 secured and under windows/router CD I have to give a password before I can connect with my wlan. I was expecting a similar programm in Ubuntu, that shows me the routers in my area, asks me wich one I want to connect to, lets me enter my password etc. I cannot seem to find such an assistant in Ubuntu. I have tried "Network", "connecting to the server". etc. Im now stuck. Could someone please explain to me how I am to connect wlan under Ubuntu.
Thank you all in advance.

---

### Post by dca on 2008-07-23
If the software on the CD was written for Windows than it won't run on Ubuntu.  Do you know what kinf od Wifi NIC you have installed on your computer?

---

### Post by germanix on 2008-07-23
I dont even know what a Wifi NIC is? All I can tell you is the wlan card in my computer is a 802.11 b/g card. I do not know the manufacturer. I have a sony vaio VGN-FS315E

---

### Post by northern lights on 2008-07-23
From a terminal can post the output of ```
sudo lshw -C network
```
Thank you.

---

### Post by germanix on 2008-07-23
Just by the way, looking at your avatar, anyone ever tell you, you look like Mel Gibson?

---

### Post by germanix on 2008-07-23
Gee you guys, I sure appreciate you all trying to help me, but I am the worst user ever. I have never been in a terminal. I think I can find it and give in this code, but I would not know how to then post the result!

---

### Post by northern lights on 2008-07-23
okay. let's go step by step:

1. A terminal launcher should also be in your applications menu, but to be foolproof, press "Alt+F2", in the radio box type "gnome-terminal" and hit Enter.

2. Mark ```
sudo lshw -C network
```press "Ctrl+C" (alternatively "Edit > Copy") to copy, switch focus to the terminal window and paste by pressing "Shift+Ctrl+V" (alternatively "Edit > Paste"). Hit Enter.

3. Mark the text that appeared in the terminal window under the executed command. Copy via "Shift+Ctrl+C" (alternatively "Edit > Copy") and paste it into a new post here.

---

### Post by germanix on 2008-07-23
Sorry, I cant seem to do that. I get to where you say "switch focus to the terminal window" then I am lost. Is this not the window that I am in? or do I go into the pulldown menue that says terminal? and then whereto?
Again sorry im just plain dumb when it comes to these things

---

### Post by germanix on 2008-07-23
jacques@jacques-desktop:~$ sudo lshw -C network
[sudo] password for jacques: 
jacques@jacques-desktop:~$ 

Does this help?

---

### Post by germanix on 2008-07-23
jacques@jacques-desktop:~$ sudo lshw -C network
[sudo] password for jacques: 
jacques@jacques-desktop:~$ sudo lshw -C network
[sudo] password for jacques: 
  *-network               
       description: Ethernet interface
       product: 82562V 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:19:d1:4e:f9:f2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=1.1-2 ip=192.168.178.36 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
jacques@jacques-desktop:~$ 
or is this what you mean?

---

### Post by northern lights on 2008-07-23
It should look something like this...

---

### Post by northern lights on 2008-07-23
Yepp, that's what I meant. Yet funny enough, it only shows an ethernet interface, not a wireless adapter.

Physically speaking there's one in the comp for sure?! Is this a laptop or a desktop pc?

What do you see when you navigate to "System > Administration > Network"?

---

### Post by germanix on 2008-07-23
Not much to see, what is there is dark and is prpceeded with an - (minus and not highlighted) I can unlock it but whats in there does not mean much to me.

---

### Post by germanix on 2008-07-23
Wait a minute, I am realy as dumm as they get. I have writing in this forum from my pc. The problem with my wlan is on my laptop. However the info that I have send you is that from my pc. I will now change to my laptop and do it all over again

---

### Post by dca on 2008-07-23
> **germanix said:**
> Just by the way, looking at your avatar, anyone ever tell you, you look like Mel Gibson?

...only when I've had too much to drink...:)

---

### Post by dca on 2008-07-23
When the laptop fires up before you enter the command line to enter those commands given, see what happens when you click (left mouse click once) on the icons next to where the time is...  It looks like a network kind of icon, oh somebody give me a hand...  In other words, just to see if your wireless card will detect any access points without any other intervention...

---

### Post by northern lights on 2008-07-23
> **germanix said:**
> Wait a minute, I am realy as dumm as they get. I have writing in this forum from my pc. The problem with my wlan is on my laptop. However the info that I have send you is that from my pc. I will now change to my laptop and do it all over again

yeah, good idea...

---

### Post by germanix on 2008-07-23
jacques@jacques-laptop:~$ sudo lshw -C network
[sudo] password for jacques: 
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:06:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:c4:ed:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.178.24 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
jacques@jacques-laptop:~$ 

this is now my laptop, sorry

---

### Post by northern lights on 2008-07-23
Okay.

So you're missing proper drivers for the wireless network device.

Run ```
sudo apt-get install linux-restricted-modules madwifi-tools
```
from a terminal on the laptop.

Afterwards, check "System > Administration > Network" on the laptop.

---

### Post by dca on 2008-07-23
> **northern lights said:**
> Okay.

So you're missing proper drivers for the wireless network device.

Run ```
sudo apt-get install linux-restricted-modules madwifi-tools
```
from a terminal on the laptop.

Afterwards, check "System > Administration > Network" on the laptop.

Is the madwifi installed on 8.04 in the 'restricted drivers' portion by default?   I can't remember...

---

### Post by northern lights on 2008-07-23
> **dca said:**
> Is the madwifi installed on 8.04 in the 'restricted drivers' portion by default?   I can't remember...

In Hardy, madwifi is included in "linux-restricted-modules"...

---

### Post by dca on 2008-07-23
Yeah, but doesn't that install as well by default?  The little dealie (with bubble message) in the tray, he should've gotten a notification that a 'restricted driver' was in use...  Sorry, just didn't want him to install something that might already be there and pre-config...

---

### Post by northern lights on 2008-07-23
> **dca said:**
> Yeah, but doesn't that install as well by default?  The little dealie (with bubble message) in the tray, he should've gotten a notification that a 'restricted driver' was in use...  Sorry, just didn't want him to install something that might already be there and pre-config...

Nothing to be sorry for.

Fair enough, it might be also - I have never personally owned a machine with an Atheros wireless device.

Simply given that the device does not have a driver allocated made me think it isn't - can you miss a 100x200 pixel tooltip?!

---

### Post by germanix on 2008-07-23
The tools are now installed but nothing has changed

---

### Post by northern lights on 2008-07-23
Have you rebooted the laptop?

What appears in "System > Administration > Network"?

---

### Post by dca on 2008-07-23
Restart the laptop and after logging back in see if the networking icon somewhere on the top right bar allows you to click once and display available networks...
 
@lights= you're gonna' have to help him out for the rest, I gotta' split...

---

### Post by germanix on 2008-07-23
dca, I tried your tip with the left mouse click but no luck.

---

### Post by germanix on 2008-07-23
now rebooting, will try left click again

---

### Post by germanix on 2008-07-23
Rebooted, no networks are displayed, nothing changed is systems, admin, network

---

### Post by germanix on 2008-07-23
In networks it shows that the network is not configurated

---

### Post by northern lights on 2008-07-23
If you select the "Wireless connection" in the "Network" menu, can't you check its properties?

When you run ```
sudo lshw -C network
```does it still read "*-network:0 UNCLAIMED"?

---

### Post by germanix on 2008-07-23
it says network: 1

---

### Post by northern lights on 2008-07-23
> **germanix said:**
> it says network: 1

yeah, that it did before also - that's you're ethernet device...

---

### Post by match002001 on 2008-07-23
Just out of curiousity what do you get when you type:

```
iwconfig
```

---

### Post by germanix on 2008-07-23
lo no wire extensions
etho same as above
wifi same as above
atho retry off, RTS off, Fragment off, Power management off

---

### Post by germanix on 2008-07-23
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-92 dBm  Noise level=-92 dBm
          Rx invalid nwid:10825  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jacques@jacques-laptop:~$

---

### Post by germanix on 2008-07-23
Thanks you guys, you have been very helpfull. my wlan still does not function but in the process I have learned to use the terminal and to copy and paste from it. I have also learned a few codes. I have emailed the manufacturers of my router to see if they have any advice. Its now nearly 12 at night here so its time I go to bed. If you guys think of anything else I will check this post again tomorrow. Thank you all and good night.

---

### Post by germanix on 2008-07-24
Hi everyone, I am back and somethings seemed to have changed overnight. I now have a connection to my router. The icon top right shows that I am connected but I cannot get the internet. The network window now shows wireless connection active, 
Settings are as follows:
Roaming mode: not activated
Network (ESSID) shows the correct router
Passwordtype: WPA personal
Configuration: set at Automatic
I entered the correct password

Is there anything else I can do?

---

### Post by germanix on 2008-07-24
Well this i now find very strangr. I have now notiched that the network icon (top right of the screen) shows that I am connected to my router/internet. When I switch my wlan card off it still shows that I am connected. I tried this with my lan cable and even when I disconnect the lan cable and have the wlan card switched off, the icon still shows me that I am connected. This cannot be normal? It seems the connection to my router works, I just cannot connect to any page on the internet by wlan. The lan works fine!
Any ideas, someone!

---

### Post by dca on 2008-07-24
One more time, at CLI type:
 
ifconfig
 
...display results...
 
After that go back to (from menus) System -> Administration -> Network
 
...press unlock and enter p/w.  Make sure you disconnect your LAN cable (just for the heck of it) and open each adapter (wired and wireless) and set each to DHCP and make sure check box set for roaming mode enabled.  (If this doesn't work for wireless we'll turn it off later...
 
...then just for kicks, restart laptop again, go back to the top right where the network manager is and see if it still displays a list of available access points...

---

### Post by germanix on 2008-07-24
RX packets:2219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1738 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:2830958 (2.6 MB)  TX bytes:190290 (185.8 KB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2442 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:123748 (120.8 KB)  TX bytes:123748 (120.8 KB)

wifi0     Link encap:UNSPEC  Hardware Adresse 00-14-A4-50-1D-03-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:26023 errors:0 dropped:0 overruns:0 frame:731
          TX packets:14390 errors:16 dropped:88 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:199 
          RX bytes:4316352 (4.1 MB)  TX bytes:1153563 (1.1 MB)
          Interrupt:22 

jacques@jacques-laptop:~$ 


will now do the rest and report

---

### Post by germanix on 2008-07-24
Guess I should not have done that. As soon as I checked the box for roaming mode under wlan the router disappeared. When I then unchecked the box again the router remained missing. I cannot remember exactly what was written there before so I cant re write what was there. Just to clarify matters when I click on the icon (networks) it never showed anything before, only "manual settings) now it shows something new namely: cabel network, connect to 802.1 or manuel. As soon as I however disconnect the lan cable those option are no longer available to me.

---

### Post by germanix on 2008-07-24
Furthermore when I now go to system/Network, it no longer shows wlan as an option.

---

### Post by dca on 2008-07-24
Okay, go ahead and set it back to disabled.  This could be an issue with the router itself.  Something it doesn't like.  When you're trying to config the wireless adapter, don't have a LAN cable connected to the laptop.  Just try and get it to connect to the router wirelessly or it may come up with a false positive when trying to diagnose.  Once deactivating roaming mode, type ifconfig again and see if wireless displays.
 
...see on my laptop (my PC(s) are a different story) both wireless and wired work fine w/ roaming mode enabled whether at work or at my house or hotel, etc.  Sometime this setting can cause a fist between certain routers.

---

### Post by germanix on 2008-07-24
jacques@jacques-laptop:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:01:4a:c4:ed:2e  
          inet Adresse:192.168.178.24  Bcast:192.168.178.255  Maske:255.255.255.0
          inet6-Adresse: fe80::201:4aff:fec4:ed2e/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:4462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3270 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6185162 (5.8 MB)  TX bytes:287779 (281.0 KB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2348 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:117400 (114.6 KB)  TX bytes:117400 (114.6 KB)

jacques@jacques-laptop:~$

---

### Post by germanix on 2008-07-24
Well at the moment as I explained I cannot configure anything to do with wlan on the network window as there is no wlan displayed anymore.

---

### Post by germanix on 2008-07-24
jacques@jacques-laptop:~$ ifconfig
eth0      Link encap:Ethernet  Hardware Adresse 00:01:4a:c4:ed:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:4500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3343 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6203537 (5.9 MB)  TX bytes:299616 (292.5 KB)

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:2348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2348 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:117400 (114.6 KB)  TX bytes:117400 (114.6 KB)

jacques@jacques-laptop:~$ 
this was now done with the lan cable disconnected and the wlan swithed on.

---

### Post by thecircusb0y on 2008-07-24
Is it just me or does that seem to be an ethernet connection, not a wireless connection.

In that terminal, type 'ifconfig eth0' (without the ' )
try to find your gateway number, it should be something like 192.168.178.1
whatever it is, i want you to take that number, and put it in the url box in firefox, and try to see if that brings you to what you need to configure your "wlan".

EDIT: I just realized I had more to read on this thread, disregard this reply if its working now..

---

### Post by dca on 2008-07-24
Even after restarting the laptop, ifconfig displays no WLAN adapter?  That's odd, the module should load on start-up...  After it starts, you should be able to click on the network manager on the top right of your screen and see available wireless network access points.
 
What kind of router is this?  How far away from the laptop is it?  There's no ethernet cable connected and is the WiFi light on your laptop lit?

---

### Post by dca on 2008-07-24
> **thecircusb0y said:**
> Is it just me or does that seem to be an ethernet connection, not a wireless connection.

In that terminal, type 'ifconfig eth0' (without the ' )
try to find your gateway number, it should be something like 192.168.178.1
whatever it is, i want you to take that number, and put it in the url box in firefox, and try to see if that brings you to what you need to configure your "wlan".

EDIT: I just realized I had more to read on this thread, disregard this reply if its working now..

No, it's not working...  Trying to figure out on his laptop what the router is and why ath0 disappears when activating 'roaming mode' on his Wifi NIC.  What I'm thinking is the router is set to static IP addresses or something else instead of using just DHCP...

---

### Post by germanix on 2008-07-24
The router is a so called "FritzBox" very popular in Germany. it is close to my laptop, there is no ethernet cable connected, and the wifi light is lit.

---

### Post by dca on 2008-07-24
It seems a lot of people in Germany have rotweilers (mean dogs) named Fritz.  I lived in Erlangen for three years along time ago...

---

### Post by dca on 2008-07-24
Under your System -> Administration - Network (from the menu) it still only lists your one network card, not the wireless, yes?
 
at the CLI type:
 
sudo modprobe -l | grep ath_pci
 
[enter your p/w]

---

### Post by germanix on 2008-07-24
Just for additional info. My son has a apple laptop. This connected automatically to the Fritzbox. All he had to do was enter the WPA password.

---

### Post by germanix on 2008-07-24
correct the wireless card is not listed

---

### Post by germanix on 2008-07-24
dont seem to be able to type this. what is that between -1 and grep. How do I get that?

---

### Post by northern lights on 2008-07-24
It's a pipe. On a U.S. keyboard layout it's on top of the Enter key.

Apart from knowing for the future, you can copy & paste, remember?

---

### Post by germanix on 2008-07-24
jacques@jacques-laptop:~$ sudo modprobe -l | grep ath_pci
/lib/modules/2.6.24-19-generic/madwifi/ath_pci.ko
jacques@jacques-laptop:~$ 

I do not find this pipe on my german keyboard. Forgot all about copy and paste. Thanks for the reminder

---

### Post by germanix on 2008-07-24
Ontop of the enter button on the german keyboard there is a Bratwurst and a bottle of beer

---

### Post by dca on 2008-07-24
> **germanix said:**
> Ontop of the enter button on the german keyboard there is a Bratwurst and a bottle of beer

PROST!
 
...okay, it shows the module/drivers loaded...
 
@Lights= you think having him re-add the module will do any good?

---

### Post by germanix on 2008-07-24
Hi Guys. It wouls seem that this is not a problem so easily fixed. I even contacted the manufacturers of the router and they cant help either. I do not want to waste anymore of your time on this. I have Ubuntu on my PC with lan and I can offcourse also use the laptop with lan. It is not the way I would like it, but that is the way it is.
Thank you all for your efforts.

---

### Post by dca on 2008-07-24
I wouldn't give up on the WLAN yet...
 
Do me a favor and just for giggles, go to 'System -> Administration -> Hardware Drivers' and see what's listed and what has a check mark in it.  The only time I've seen a module/driver get wiped is during an Ubuntu kernel update....

---

### Post by northern lights on 2008-07-24
> **germanix said:**
> Ontop of the enter button on the german keyboard there is a Bratwurst and a bottle of beer
Thanks! This one made sticking with this thread entirely worth it (Currently residing in Hamburg, Germany).

> **dca said:**
> @Lights= you think having him re-add the module will do any good?I dunno man, I'm sort of at the end of my wits. This darn wireless should have been running yesterday night. Concur?

---

### Post by germanix on 2008-07-24
hi guys. My wlan is running. I found the answer in the Linux Mint Wiki.
[http://www.linuxmint.com/wiki/index.php?title=Mi](http://www.linuxmint.com/wiki/index.php?title=Mi)...
Here is what you do:
sudo gedit /etc/network/interfaces
then edit the interfaces file. Leave the loopback interfaces lo (the first two line)
They should now look like this:
auto lo
iface to inet loopback
save and close the file
In a terminal type:
sudo /etc/init.d/networking restart
Right click on the Network manager icon. It should show "networking enabled"
Left click on the icon.
It now shows the varios wireless routers detected in your area
click on the router you wish to connect to, enter your password or key and low and behold you are connected.

---

