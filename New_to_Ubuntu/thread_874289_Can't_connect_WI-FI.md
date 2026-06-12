---
title: "Can't connect WI-FI"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Inzo on 2008-07-29
Hi, I have problem to use my university wifi with ubuntu. I'm able to connect the wireless, however i can't browse internet or use any internet facility. it ask to set VPN and proxy. I don't know how to set VPN. I did ask help from computer people in university but they said they don't have the program or something like that.

I hope any one can help me. Thanks:)

---

### Post by phidia on 2008-07-29
open a terminal window (Applications>Acessories>Terminal) and enter this: > iwconfig & this: > lshw -C network
copy & paste the output here.

---

### Post by Inzo on 2008-07-29
iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"UCWIFI"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:4D:C6:E8:DE   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=93/100  Signal level=-35 dBm  Noise level=-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:120   Missed beacon:3

lshw -C network:

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 03
       serial: 00:0f:b0:98:2f:51
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5788-v3.04 latency=128 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:94:fd:97
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.12 latency=128 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

Thanks

---

### Post by phidia on 2008-07-29
I'm not completely sure but given what you listed-how did you enable your wireless card?
> description: Wireless interface
product: PRO/Wireless 2200BG Network Connection
vendor: Intel Corporation
That's your card. There are a [lot of hits]("http://ubuntuforums.org/search.php?searchid=45386844") in the wireless forums for intel cards with connection problems. 
There is a native driver for that card. Again in terminal > sudo modprobe ipw2200 What does that result in-can you connect?

---

### Post by Inzo on 2008-07-29
do you mean its my wireless card problem?
after I enter the code you said nothing happen..

---

### Post by phidia on 2008-07-29
I've looked at this some more. Did wireless ever work on this computer?
From the output you provided it looks like the ipw2200 driver is there.
If there is a switch for your card try turning it off and on again too.

---

### Post by Inzo on 2008-07-29
the wireless connection is ok in other place other than my uni, its just uni set the wireless with VPN and proxy.. i dont know how to set them in linux, and uni only provide setting on apple and windows..

---

### Post by UbuntuNerd on 2008-07-29
try this 

sudo modprobe fsam7400 radio=1

---

### Post by Inzo on 2008-07-29
what is the code for?
i cant see any changes..:(

---

### Post by UbuntuNerd on 2008-07-29
so is still not working?

---

### Post by Inzo on 2008-07-29
no.. are there any tutorial how to set VPN, proxy and stuff like that for ubuntu? and maybe tutorial for linux beginner, coz i'm new with linux:)

---

### Post by phidia on 2008-07-29
I think you need openvpn installed. Check out [this thread]("http://ubuntuforums.org/showthread.php?t=857994&highlight=openvpn") for starters.

---

### Post by Inzo on 2008-07-29
Thanks i'll try it

---

