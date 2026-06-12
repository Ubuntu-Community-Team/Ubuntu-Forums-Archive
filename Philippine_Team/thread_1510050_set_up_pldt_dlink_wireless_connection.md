---
title: "set up pldt dlink wireless connection"
date: 2010-06-15
forum: Philippine Team
---

### Post by undersweet_21 on 2010-06-15
hope somebody could help me set up my internet wireless connection.

i've done some reading on how to set it up but just couldn't get it right. here are some info that i think would be needed in setting up a wireless connection in ubuntu: 

im using ubuntu 9.10
my dsl provider is pldt
my router is dlink-300
my network adapter is atheros ar5007eg

pls pls provide a step by step guide on how i should do this.

---

### Post by antoniomiguel on 2010-06-15
I suppose you're done configuring your wifi router basics (SSID, Security, etc).

Can your Ubuntu discover the wifi signal?

---

### Post by undersweet_21 on 2010-06-15
Yes, I have already configured my router and its working fine in Vista.
But, when I boot in Ubuntu and have supplied the WEP password for the connection it still doesn't connect.

I tried typing some terminal commands that I've read in Ubuntu documentations like *iwconfig*, it displays this output: lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

[FONT=monospace][/FONT]

---

### Post by antoniomiguel on 2010-06-15
no mention about wlan0?

iwconfig should at least display a state of your wlan interface

---

### Post by undersweet_21 on 2010-06-15
oops sorry left that one out.

here it is:

wlan0  IEEE 802.11bg  ESSID:"Undersweet Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:F0: DF:1B:E3   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=30/70  Signal level=-80 dBm  Noise level=-99 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0



thanks so much antoniomiguel for helping me out :)

---

### Post by spotted zebra on 2010-06-15
do you have the drivers installed for you wireless card?

---

### Post by undersweet_21 on 2010-06-15
I just finished downloading the driver.
I'm not sure what step to take next. 
Do I have to download *ndiswrapper*, so that i can install the driver?

---

### Post by spotted zebra on 2010-06-15
how did you download the driver?

hopefully system>admin>hardware drivers and let this program find them for you and install one. if you downloaded an actual file leave it there because my way may not work but it usually does and it is much easier. try the way prescribed here and see if it works if not we will try something else.

---

### Post by undersweet_21 on 2010-06-16
I logged into Vista to download the actual file. I copied it into a USB, logged into Ubuntu then copy-paste the file to the desktop. I followed your instructions but unfortunately, Ubuntu can't find the driver.

---

### Post by spotted zebra on 2010-06-16
ok i think i am confusing you and i am sorry. i will try to explain myself below.

the driver that you downloaded in vista will not help us right now so just forget about it. 

you need to plug your computer into a LAN connection and boot into ubuntu. you should have support for a LAN connection by default, make sure that you are able to access the internet.

now go to system>admin>hardware drivers. this program will search the internet for drivers for hardware you have plugged in which includes your wireless card. if you are lucky it will find a driver(s) for your wireless card. Now you will select one of them and install it. 

just for good measure run this in a terminal while you still have your LAN connection after the wireless driver is downloaded and installed.

```


sudo apt-get update && sudo apt-get upgrade


```

this may take a while depending on your internet connection speed. once it is completed unplug your LAN connection and restart the computer. when it comes back up see if you can connect to your wireless.

don't forget if your wireless is hidden you will have to manually set up the connection. if you need help with this just ask.

i hope this is a clear explanation. if you have any question about it just let me know and i will try to explain anything in more detail or make it more clear.

---

### Post by antoniomiguel on 2010-06-16
> **undersweet_21 said:**
> 
wlan0  IEEE 802.11bg  ESSID:"Undersweet Network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:F0: DF:1B:E3   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=30/70  Signal level=-80 dBm  Noise level=-99 dBm
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0


Seems to me that your laptop is already connected with the wifi router, ESSID and signal level tell so. However, the signal level is quite low, though this wouldn't prevent you from connecting to the internet.

Can you run these (one at a time) in a terminal and post the results:
1. ifconfig
2. host [www.yahoo.com](www.yahoo.com)

---

### Post by undersweet_21 on 2010-06-17
> **antoniomiguel said:**
> Seems to me that your laptop is already connected with the wifi router, ESSID and signal level tell so. However, the signal level is quite low, though this wouldn't prevent you from connecting to the internet.

Can you run these (one at a time) in a terminal and post the results:
1. ifconfig
2. host [www.yahoo.com]("http://www.yahoo.com")
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:93:fd:2b  
          inet6 addr: fe80::2a0:d1ff:fe93:fd2b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6090 (6.0 KB)  TX bytes:468 (468.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:84:fd:eb  
          inet6 addr: fe80::21b:9eff:fe84:fdeb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5940 (5.9 KB)
          Interrupt:17 Memory:f1000000-f1010000 

~$ host [www.yahoo.com]("http://www.yahoo.com")
;; connection timed out; no servers could be reached

---

### Post by undersweet_21 on 2010-06-17
> **spotted zebra said:**
> ok i think i am confusing you and i am sorry. i will try to explain myself below.

the driver that you downloaded in vista will not help us right now so just forget about it. 

you need to plug your computer into a LAN connection and boot into ubuntu. you should have support for a LAN connection by default, make sure that you are able to access the internet.

now go to system>admin>hardware drivers. this program will search the internet for drivers for hardware you have plugged in which includes your wireless card. if you are lucky it will find a driver(s) for your wireless card. Now you will select one of them and install it. 

just for good measure run this in a terminal while you still have your LAN connection after the wireless driver is downloaded and installed.

```


sudo apt-get update && sudo apt-get upgrade


```

this may take a while depending on your internet connection speed. once it is completed unplug your LAN connection and restart the computer. when it comes back up see if you can connect to your wireless.

don't forget if your wireless is hidden you will have to manually set up the connection. if you need help with this just ask.

i hope this is a clear explanation. if you have any question about it just let me know and i will try to explain anything in more detail or make it more clear.
read your post too late.. ><

i was able to install ndiswrapper and the driver that is compatible with my chipset according to this website: 

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Atheros_AR5001](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Atheros_AR5001)

i followed the instructions on this website: 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Identifying%20Wireless%20Adapter](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Identifying%20Wireless%20Adapter)

on how to install the driver. and here's the ouput:

~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathw : driver installed
    device (168C:001C) present (alternate driver: ath5k)

when i still couldn't get a connection. i tried your suggestion - connected the lan etc.  it couldn't connect on the internet to find the driver.

i even tried stopping eth0, as instructed by this website: [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

have done the blacklist thing:

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a "blacklist bcm43xx\n blacklist b43\nblacklist b43legacy\nblacklist ssb\nblacklist ath_pci\nblacklist ath_hal\nblacklist rt2500usb"

should i update my kernel and recompile? cause i've read here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Identifying%20Wireless%20Adapter](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Identifying%20Wireless%20Adapter)

that it should have .config directory but it's not there when i run: ls /lib/modules/`uname -r`/build

omg.. i hope i didn't do anything wrong! hehe.. THIS IS QUITE CHALLENGING! but i like it. :) have to review on sql first. ill view your suggestions again later. thanks so much! :)

---

### Post by antoniomiguel on 2010-06-17
> **undersweet_21 said:**
> ~$ 
wlan0     Link encap:Ethernet  HWaddr 00:1b:9e:84:fd:eb  
          inet6 addr: fe80::21b:9eff:fe84:fdeb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5940 (5.9 KB)
          Interrupt:17 Memory:f1000000-f1010000 
Interesting, why can't i see your IP address?

> **undersweet_21 said:**
> ~$ host [www.yahoo.com]("http://www.yahoo.com")
;; connection timed out; no servers could be reached

No DNS eh? Im not sure :p

On a terminal..
sudo gedit /etc/resolv.conf

add these..
nameserver 208.67.220.220
nameserver 208.67.222.222

then save.

Try "host www.yahoo.com" on a terminal again. Result should be different from your earlier trial

---

