---
title: "How to set up the DWL G510 C. under Ubuntu/Windows"
date: 2006-05-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Z3r0- on 2006-05-15
The RT61 chipset is a wlan (wireless local area network) chipset which is compliant with wireless standards 802.11 b/g

This page provides information about how where to find drivers and how to set up Windows XP or Ubuntu Linux Dapper with the RT61 chipset

There are a vast amount of wireless lan manufacturers who include the RT61 as the main chip in their wlan cards and resell it, for instance the D-Link DWL G510 Rev C. (Australia) a PCI Card is based on this chip.

D-Link haven't updated their buggy drivers in a while so it was necessary to find new drivers from the chipset manufacturer

The latest drivers for the ralink chipset can be found here [www.ralink.com.tw/supp-1.htm](www.ralink.com.tw/supp-1.htm)

At the time of writing driver version 1.1.1.0 the RT61 chipset for windows was available released 12th June 06

[http://www.ralink.com.tw/drivers/Windows/IS_AP_STA_6x_D-1.1.1.0_2500_D-3.2.0.0_RU-1.2.2.0_AU_1.1.0.0_060906_0.0.3.0.exe](http://www.ralink.com.tw/drivers/Windows/IS_AP_STA_6x_D-1.1.1.0_2500_D-3.2.0.0_RU-1.2.2.0_AU_1.1.0.0_060906_0.0.3.0.exe)

and Linux version 1.0.4.0 released on the 25th of April 06

[http://www.ralink.com.tw/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz](http://www.ralink.com.tw/drivers/Linux/RT61_Linux_STA_Drv1.0.4.0.tar.gz)

Index
1 Connecting to a router under Windows XP with WPA/WPA2
2 Setting up a wireless access point under Windows XP with WPA/WPA2
3 Connecting to a router under Ubuntu Linux with WPA/WPA2
4 Setting up a wireless access point under Ubuntu Linux with WPA/WPA2

1 Connecting to a router under Windows XP
----------------------------------* ------
For connecting directly to a adsl/cable wireless router

Firstly install the RT61 drivers above, you will be prompted to choose wi-fi or performance mode, no information regarding the difference between wifi and performance mode is available so choose either.

After installing, reboot, go to control panel -> network connections, if you can't see your wireless card in the control panel go to system settings and install drivers manually

Run the home networking wizard to correctly configure your card, if connecting through a router you can choose other -> this computer connects to the internet directly through a hub, other computers on my network connect directly through this hub

Your wireless card will now be assigned an IP address by the router using DHCP

Now we must configure the card correctly,

Go to control panel -> network connections -> right click on the wireless adapter -> go to properties -> configure

For the RT61 you have these options
Adhoc wireless mode -> 802.11 G only
Auto Channel Select -> Disable
Auto Reconnect Mode -> Enable
B/G Protection -> Auto
CAM when AC Power -> Disable
Country Region 11A -> Ch(36-48) #for australia #this shouldn't matter as we don't use 802.11A but set it correctly for your regulatory domain
Country Region 11G -> 1 - 13 #for australia
Fragment Threshold -> 2347
Frame Aggregation -> Enable
IEEE802.11h -> Enable #something to do with interferring with fighter jets and their radar, please enable unless you want to have the military turn up at your door
Local Administration MAC Network -> empty
Network Type -> Infrastructure
Power Saving Mode -> Fast_PSP (power save mode) #max puts the unit into power save mode all the time, it can still receive packets but may not work as fast when transferring large amounts of data, fast can wake the unit for large amounts of data Radio On/Off -> Enable
RTS Threshold -> 2346
SSID -> myssid #your routers ssid
WMM Capable -> Enable #this is like QoS, quality of service, it doesn't matter if this is enabled or disabled

There should be an RA icon in your system tray, double click it, go to profile, add
SSID: myssid #routers SSID
PSM: PSM (Power saving mode)
Network type: Infrastructure
TX Power: Auto

Go to Authentication and Security Authentication:

Open #when initially setting up I suggest using open, otherwise use WPA2-PSK

Encryption: None #when initially setting up I suggest using None, otherwise use AES

Go back to profile, go to the advanced tab

Wireless mode: 802.11G only
Tx Rate: auto
Tx burst: disabled #for compatibility, this is proprietory and causes ping spikes
Enable TCP Window Size: disabled
Fast roaming at -70 dbm: enabled

Apply

You have now set up the card successfully, all you need to do is go back to profile and activate the connection

Troubleshooting
---------------

I suggest pinging the router from the command prompt start -> run -> command

ping 10.0.0.138 -n 10000 #routers ip pinged 10000 times

Additionally you may find resuming from hibernation causes a problem, you can use the Wireless Zero Configuration to configure your card and this will work, but if you get ping spikes try using the ralink utility instead.

2 Setting up a wireless access point under Windows XP
----------------------------------*-------------------

For using your PC as a wireless access point (i.e. so that the internet can be shared from one PC through wireless to other PCs)

Firstly install the RT61 drivers above, you will be prompted to choose wi-fi or performance mode, no information regarding the difference between wifi and performance mode is available so choose either.

After installing, reboot, go to control panel -> network connections, if you can't see your wireless card in the control panel go to system settings and install drivers manually

Run the home networking wizard to correctly configure your card, if connecting through a router you can choose other -> this computer connects to the internet other computers on my network

connect through this computer

Your ethernet card will be assigned an IP address by your adsl/cable modem using DHCP, but you need to define static LAN IP addresses for the computers on your local network

Control panel -> network connections -> wireless network -> properties -> scroll down to tcp/ip

IP address 192.168.0.1
Subnet 255.255.255.0
Gateway 10.0.0.138 #your router
Preferred DNS 10.0.0.138 #your router or ISP DNS IP
Alternate DNS 192.168.0.1 #anything here or ISP DNS IP #2

For computers connecting to your home network you must run home networking wizard again and select, This computer connects through another PC, follow the rest of the prompts to complete setup.

set up the wireless adapter for that computer as IP address 192.168.0.2 #192.168.0.x for the other computers where x is a number from 3 to 254

Subnet 255.255.255.0
Gateway 192.168.0.1 #your gateway PC
Preferred DNS 10.0.0.138 #your router or ISP DNS IP
Alternate DNS 192.168.0.1 #anything here or ISP DNS

Now we must configure the card correctly,

Go to control panel -> network connections -> right click on the wireless adapter -> go to properties -> configure

For the RT61 you have these options

Adhoc wireless mode -> 802.11 G only
Auto Channel Select -> Disable
Auto Reconnect Mode -> Enable
B/G Protection -> Auto
CAM when AC Power -> Disable
Country Region 11A -> Ch(36-48) #for australia #this shouldn't matter as we don't use 802.11A but set it correctly for your regulatory domain
Country Region 11G -> 1 - 13 #for australia
Fragment Threshold -> 2347
Frame Aggregation -> Enable
IEEE802.11h -> Enable #something to do with interferring with fighter jets and their radar, please enable unless you want to have the military turn up at your door
Local Administration MAC Network -> empty
Network Type -> Infrastructure
Power Saving Mode -> Fast_PSP (power save mode) #max puts the unit into power save mode all the time, it can still receive packets but may not work as fast when transferring large amounts of data, fast can wake the unit for large amounts of data
Radio On/Off -> Enable
RTS Threshold -> 2346
SSID -> myssid #your SSID
WMM Capable -> Enable #this is like QoS, quality of service, it doesn't matter if this is enabled or disabled

There should be an RA icon in your system tray -> Right click on RA icon -> Access point mode

Set the card up as follows:
Wireless Mode -> 802.11G Only
TX Rate -> Auto #or 54MB/s
Channel -> 6 #most stable channel IMHO
SSID -> myssid #whatever you want here
B/G Protection -> Auto #May not be needed since we are using G only but set on anyway
TX Burst -> Unticked #proprietory, gives a speed increase but can cause compatibility problems and ping spikes
No Forwarding among wireless clients -> Unticked
Preamble -> Short Preamble #smaller preamble with each frame
Hide SSID -> Unticked
Beacon(ms) -> 60
Use Short Slot -> Unticked #makes internet lose packets I think
TX Power -> 100% #tbh you can use lowest power of 10% and you will get around 50% throughput in a small house
Auto Channel Selection at next boot -> Unticked to set up wireless encryption go to Auth Vs Security and WPA2-PSK -> encryption type can be AES (more secure) #do this once you have tested the network works)

Now you have set up the wireless access point you must configure the computers on your network to use it, my suggestion is, ping one PC from the other, you must first allow echo requests by changing Control panel -> windows firewall -> Advanced tab -> select your wireless network card -> settings -> icmp -> allow incoming echo request -> YES

in the command prompt of the connecting PC type (start -> run -> command) ping -n 10000 192.168.0.1

Just leave it running until you fix the problem

3 Connecting to a router under Ubuntu Linux with WPA/WPA2
----------------------------------* ----------------------

If you wish to get WEP/WPA working you will need to compile the ralink drivers available from their site (link at top of page)

You also need to install the 'build-essentials' and 'kernel headers' packages from the apt repositories

As superuser start a terminal and type

cd /home/%username%/Desktop

tar xvf RT61_Linux_STA_Drv1.0.4.0.tar.gz

cd RT61_Linux_STA_Drv1.0.4.0

cd Modules #capital M

make all #this will install the drivers as a module

mkdir /etc/Wireless #capital W!

mkdir /etc/Wireless/RT61STA #note the capitals

cp *.bin /etc/Wireless/RT61STA

cp *.dat /etc/Wireless/RT61STA

rmmod rt61.ko #unload running driver

insmod rt61.ko #load new driver

cd /etc/Wireless/RT61STA

gedit rt61sta.dat #edit the your own configuration variables, mine are below, you can find more info in readme.txt

vi -b and paste this into vi to make this a binary file

[Default]
CountryRegion=1 #1-13 Australia
CountryRegionABand=6 #36-48 Australia
WirelessMode=4 #G only
SSID=Z3R0SROUTER
NetworkType=Infra
Channel=6
AuthMode=WPA2PSK
EncrypType=AES
DefaultKeyID=1 #ignored
Key1Type=0 #ignored
Key1Str=0123456789 #ignored
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
WPAPSK=63letterkey here #for 128bit encryption enter 63 letters
TxBurst=0 #play around with this
PktAggregate=0 #and this
TurboRate=0 #and this
WmmCapable=1
AckPolicy1=0
AckPolicy2=0
AckPolicy3=0
AckPolicy4=0
BGProtection=0
IEEE80211H=1
TxRate=0
RTSThreshold=2347
FragThreshold=2346
RoamThreshold=75
PSMode=FAST_PSP

ifconfig ra0 up #put your own static IP here

dhclient ra0 #to get dhcp ip address

The easiest way to get the drivers to load up on every boot is to go to

/lib/modules/2.6.15-22-386/kernel/drivers/net/wireless/rt2600

mv rt61.ko rt61.bak

cp /home/%user%/Desktop/RT61_Linux_STA_Drv1.0.4.0/Modules/rt61.ko .

add ifconfig ra0 up

add dhclient ra0

Troubleshooting
---------------

The drivers (1.0.4.0) are buggy and require you to ping a local IP address constantly to keep the connection up. 

4 Setting up a wireless access point under Ubuntu Linux with WPA/WPA2
---------------------------------------------------------------------

I haven't tried this myself but here is what you need to do

Just follow the above and edit rt61sta.dat accordingly with master instead of managed mode, you

will also need to assign your own static IP addresses instead (bring the connection up with

ifconfig ra0 inet 192.168.0.1 up #assigned static IP route add default gw 10.0.0.138 #ip of router

you then need to allow ip masquerading for all clients on the network connected to the wireless access point so that they can access the ethernet (internet) connection

modprobe iptable_nat
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

you must add this to /etc/rc.local to execute on each boot up

---

### Post by FooAtari on 2006-07-15
Hi,

HELP!

when I do this "make all"

i get....

make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/allie/Desktop/RT61_Linux_STA_Drv1.0.4.0/Modules modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [all] Error 2

I am doing it as root, why isnt it working?

Thanks

---

### Post by Z3r0- on 2006-08-05
this should get you past that error

modules-assistant update
modules-assistant prepare

it will download the kernel headers and install them for you

---

### Post by boyle on 2006-09-26
I have the same problem when 'make all'

and 'modules-assistant update' only give me 'command not found'

can anyone please guide me on how to make this thing work step by step.


though I have some experiences in dos programming..
i'm totally noob in unix world.:confused:  (been in it for a day)

thank you.

---

### Post by alecjw on 2006-09-29
> **boyle said:**
> I have the same problem when 'make all'

and 'modules-assistant update' only give me 'command not found'

can anyone please guide me on how to make this thing work step by step.


though I have some experiences in dos programming..
i'm totally noob in unix world.:confused:  (been in it for a day)

thank you.

Same here...
Any solutions?

---

### Post by Qwerty_ on 2007-01-15
Hey guys im having a bit of trouble 

mike@mike-desktop:~$ sudo dhclient ra0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device
wmaster0: unknown hardware address type 801
Bind socket to interface: No such device

any ideas ive followed the howto but iam stuck here any ideas/suggestions?

---

