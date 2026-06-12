---
title: "fiesty fawn on hp computer wireless setup problem"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by nnugnafets on 2008-10-13
Hi, having trouble finding advice specific to my problem, though i know there is a lot of similar questions out there. 

computer recognizes that there are networks available but wont connect.

these are the readouts to iwconfig, ifconfig and sudo lshw -C network.

thanks for your help

stefan@ubuntustefan:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  IEEE 802.11g  Frequency:2.427 GHz  

          RTS thr:off   Fragment thr=2346 B   

          

wlan0     IEEE 802.11g  ESSID:""  

          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:17:3F:BF:97:45   

          RTS thr:off   Fragment thr=2346 B   

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



stefan@ubuntustefan:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1A:92:5C:FD:78  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

          Interrupt:16 Base address:0xc000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:772 errors:0 dropped:0 overruns:0 frame:0

          TX packets:772 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:61424 (59.9 KiB)  TX bytes:61424 (59.9 KiB)



wlan0     Link encap:Ethernet  HWaddr 00:C0:A8:D7:BF:F6  

          inet6 addr: fe80::2c0:a8ff:fed7:bff6/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 b)  TX bytes:5604 (5.4 KiB)



wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-D7-BF-F6-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



stefan@ubuntustefan:~$ 

stefan@ubuntustefan:~$ sudo lshw -C network

  *-network               

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:c0:a8:d7:bf:f6

       capabilities: ethernet physical wireless

       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by anewguy on 2008-10-13
A couple of questions:

- what wireless card/chipset are you using (try lspci) ?

- what driver are you using ?

- do the networks show under network manager ?

- do any of the networks you are trying to connect to require WEP or WPA ?

- when you go to system/administration/network, does the wireless option show there, and is roaming mode enabled ?

We can go from there to see if we can help you.  You already provided a lot of information and that is appreciated!!

Dave :)

---

### Post by ibizatunes on 2008-10-13
You maybe better off with ubuntu 8.04 maybe even 8.10 if you dont mind the odd bug
Ubuntu 7.10 didnt detect my wireless 8.04 did, but didnt work 100% and 8.10 it works perfectly!!
Maybe you should try a newer version?

---

### Post by nnugnafets on 2008-10-13
thanks for getting back sooon anewguy
- what wireless card/chipset are you using (try lspci) ?
i dont know.  i tried lspci but didnt find anything that jumped out as being 
- what driver are you using ?
dont know what driver either.  i tried to look online for the driver for a bit, but networks and their availability show up on the dropdown menu that comes off of the little network icon in what i am maybe inaccurately calling the system tray
- do the networks show under network manager ?
i think they do.  as i mentioned above, they show up but i havent found them in the system/administration/network window
- do any of the networks you are trying to connect to require WEP or WPA ?
are wep or wpa passwords?  my roomate has a windows pc that is connecting fine.
- when you go to system/administration/network, does the wireless option show there, and is roaming mode enabled ?
roaming mode is enabled, but i'm not sure the networks do

thanks, sorry these answers are incomplete.  let me know how to find out what driver/what my wireless card is and i will look that stuff up

---

### Post by anewguy on 2008-10-14
Maybe we should back up a step - what brand/model of PC is this?  Is the wireless "in the box" or do you use a USB or PCMCIa adapter?

As far as lspci goes, just copy/paste the output back here.

Also, look under system/preferences/hardware information and see if you can spot your wireless adapter there.  If so, post back what it is.  Also in the details (you may need to go through tabs to find it) on this item will be what driver, if any, it is using.  Post all of that back here as well.

WEP and WPA are encryption techniques used on wireless communications links.  If it works on your room mates' PC it may be that "back when" when they first installed they set up a key and now have forgotten about it because it "just works".  The best way to know this is to know the router you want to connect to and its' configuration, as the encryption will be defined there.

Dave :)

---

