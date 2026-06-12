---
title: "Wireless - Sees neworks but can't connect"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by franklin_m on 2008-08-16
Hello,

I'm an absolute newbie to Linux. Have been messing around with the live CD version for a couple weeks. When using that version, it sees my wireless network (via Linksys USB wireless G) and connects just fine.

I installed Ubuntu to the hard drive, and now it can see my wireless device, see the network, see my neighbors' networks, but it will not connect.

I've made sure all the settings are correct that I can find (WPA, wireless password, etc.).

Any ideas?

Thanks,
Frank

[email]frankmellott@earthlink.net[/email]

---

### Post by Badoxide on 2008-08-16
Hello.franklin_m

I am also new to this. Not to sure if this is what your asking, but here is what I did to get it working, for me right click on the network icon next to the clock make sure its Enabled then left click you're see your name click it, and you should have it.

Well this is how I did it and so far all is working great.

Best of luck

Badoxide

---

### Post by franklin_m on 2008-08-16
Thanks. I tried that. It's the craziest thing. Works fine from LiveCD, works fine from Windows, and when working from the full install, it can see networks, but won't connect.

Frank

---

### Post by nicedude on 2008-08-16
Franklin you might give everyone some more info such as,

What device you are using? be as specific as possible such as model number and version if you can find that out.

Please list the output of these commands

iwconfig

sudo lshw -C Network

This will help anyone who looks at this out so they can help you

---

### Post by franklin_m on 2008-08-16
Thanks.

It's a Linksys model WUSB 54G Version 4.

Printout of commands listed above shown below:

---------------------------------------------------------------
iwconfig
---------------------------------------------------------------

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"LT1932TQ"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:75:EE:DC   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=30/100  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


---------------------------------------------------------
sudo lshw -C Network
---------------------------------------------------------
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:a2:64:f0
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f8:ab:3a:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by nicedude on 2008-08-16
First of all is 00:18:39:75:??? your access point because it is the one your associating with. Second I would try to setup WEP first and see if you can get that to work and then if so then try WPA last ( it goes like this -> first check unsecured with no encryption -> then WEP -> then WPA ), its just the best and simplest way for everyone to troubleshoot your connection as then we can see if it is WPA trouble or overall some other trouble. But your iwconfig looks like you at least have a driver and your system can see the adapter.

---

### Post by franklin_m on 2008-08-17
Sorry, been out at the movies with my kids.

I just checked the LAN settings and 00:18:39:75:EE:DC is the MAC address of the Linksys Wireless router (WRT54GS V6).

I'll try the above and keep posting results. Thanks for the help. My 12 year old has been interested in trying this for over a year, I'm finally getting around to it.

Frank

---

