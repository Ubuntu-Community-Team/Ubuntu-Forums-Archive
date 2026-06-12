---
title: "Internet sharing inconstant"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by Texline on 2012-01-28
I have Ubuntu 10.04 in a Dell desk top accessing a wifi hot spot through a USB radio and cantenna. eth(0) is connected to port 1 of the Linksys WRT54G.  No set up of the router has been done so it shows as "Linksys" with no security.  My Kindle Keyboard can access Amazon through the set up.  I have tried a Dell laptop with XP, a Compaq laptop with Linux Mint 9 and a Viewsonic GTab with Android Honeycomb on this setup also.  All units will connect to "Linksys" but only the Kindle has successfully gotten on the Internet through the wireless router so far.
 

 Why don't the three units access the Internet and what do I need to do to get them on line also?

---

### Post by sandyd on 2012-01-28
> **Texline said:**
> I have Ubuntu 10.04 in a Dell desk top accessing a wifi hot spot through a USB radio and cantenna. eth(0) is connected to port 1 of the Linksys WRT54G.  No set up of the router has been done so it shows as "Linksys" with no security.  My Kindle Keyboard can access Amazon through the set up.  I have tried a Dell laptop with XP, a Compaq laptop with Linux Mint 9 and a Viewsonic GTab with Android Honeycomb on this setup also.  All units will connect to "Linksys" but only the Kindle has successfully gotten on the Internet through the wireless router so far.
 

 Why don't the three units access the Internet and what do I need to do to get them on line also?

Connect to (only) the wireless, and run
```

sudo traceroute -T google.com
```
post the output.

P.S. If your tech savvy enough, try running dd-wrt on that. From what ive heard, it runs quite well.

---

### Post by Texline on 2012-01-28
> **sandyd said:**
> Connect to (only) the wireless, and run
```

sudo traceroute -T google.com
```post the output.

P.S. If your tech savvy enough, try running dd-wrt on that. From what ive heard, it runs quite well.


My installation of 10.04 doesn't know traceroute:

sudo: traceroute: command not found


I will explore options as I can.  I've had to reload systems from trying to get  Internet sharing to work (Mint 8 & 9) by experimenting with different How To's for a few months.  I thought I would peal off one layer and have come close to success.

---

### Post by halitech on 2012-01-28
you say all the devices will connect to the router, what are you basing this on?

Have you checked to make sure the router is configured to allow more then one connection? Reset the router? tried with a wired connection?

---

### Post by sandyd on 2012-01-28
nvm

---

### Post by Texline on 2012-01-29
> **halitech said:**
> you say all the devices will connect to the router, what are you basing this on?

Have you checked to make sure the router is configured to allow more then one connection? Reset the router? tried with a wired connection?

The router (WRT54G) had been reset and no modifications were done to the default settings. 

Only one unit was tested at a time (only the Dell desktop with Internet access via the wifi hot spot which is sharing the internet through eth(0) and the WRT54G and one device (Kindle, Android, XP or Mint 10) was powered up when testing for Internet sharing access.

All test units list "Linksys" as available.  All units will indicate bing connected "Linksys" after selecting it (no password needed with default router settings).  All units indicate good or strong signal strength.  The Kindle will access the Amazon web page and page through listings.  All others respond that the server is not available (Firefox) or webpage not available (Android browser).

Testing for LAN connection was done with the Compaq running Mint 10.  eth(0) was selected and "Linksys" disconnected.  eth(0) was shown as connected and Firefox gave the server not available message.

I have not attempted file sharing or printer sharing.  Research is needed first and I was wanting to have only one problem at a time.

---

### Post by Texline on 2012-01-29
> **sandyd said:**
> ah.
I see they don't install traceroute by default now....

Connect to a wired network, and type
```

sudo apt-get install traceroute
```to install traceroute

Also, type in 
```

sudo iwconfig
sudo route -n

```while you are connected to the network (but can't access it)

The Ubuntu 10.04 unit is not experiencing the problem.  These are the results there.

```
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Texline"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:F8:D2:08   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:A311-66B3-58
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

The results with the Compaq running Mint 10 wirelessly are:

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:87:E7:0B   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
```

---

### Post by lisati on 2012-01-29
> **Texline said:**
> 
Copying and pasting with Office seems to have added some graphics.

Fixed by wrapping with [noparse]```
 and 
```[/noparse]

---

### Post by sandyd on 2012-01-29
> **Texline said:**
> The Ubuntu 10.04 unit is not experiencing the problem.  These are the results there.

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Texline"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:F8:D2:08   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:A311-66B3-58
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0

The results with the Compaq running Mint 10 wirelessly are:

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:87:E7:0B   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
Thats weird.
your route tables are identical, yet you can't seem to access the net on one of them...

---

### Post by lisati on 2012-01-29
Very strange: the OP complains about the smileys and then undoes the efforts to help. This *is* a moderated forum: having the smileys there makes it hard to read and thus harder to help.

---

### Post by Texline on 2012-01-29
> **sandyd said:**
> Thats weird.
your route tables are identical, yet you can't seem to access the net on one of them...

I decided to try an experiment.  I swapped an old Linksys BEFW11S4 I've had collecting dust for the WRT54G.  Now both the Kindle and Android tablet will go on line.  The Compaq with Mint 10 still doesn't find a server and I didn't bother getting the Dell with XP out.

---

