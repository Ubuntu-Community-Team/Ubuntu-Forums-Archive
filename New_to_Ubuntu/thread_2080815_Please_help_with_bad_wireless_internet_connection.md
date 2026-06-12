---
title: "Please help with bad wireless internet connection"
date: 2012-11-05
forum: New to Ubuntu
---

### Post by skullnbones on 2012-11-05
I've been having problems with my USB wireless driver.  It's a TL-WN727N.  Since upgrading to 11.10 my connections have been slow to non-existent.  I thought that maybe the drivers were not installed so I followed the steps on this page <link> [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M) </link>.  When I save rt5370sta to /etc/modules/ I get full bars on my indicator, activity monitor shows some network movement.  But, I cannot open a webpage and the system seems to slow down.  For example, I opened terminal and it was hesitant coming up.  Not the window but the line to input a command and apt-get update took 15 min to get to 24%.  So I deleted the module rt5370sta from /etc/modules so I can have some internet access.  

I am new to Ubuntu and just trying to get my internet to its fullest wireless potential.  If anyone can help I would be very grateful.

Misc info:

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"###"  
          Mode:Managed  Frequency:2.422 GHz  Access Point:  ########  
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:57  Invalid misc:3   Missed beacon:0 
```ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 6c:62:6d:dd:0c:ae  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2280 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:187728 (187.7 KB)  TX bytes:187728 (187.7 KB)

wlan0     Link encap:Ethernet  HWaddr 54:e6:fc:8a:6e:c2  
          inet addr:195.189.0.3  Bcast:162.165.0.255  Mask:255.255.255.0
          inet6 addr: fe80::56e6:fcff:fe8a:6ec2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:40799117 (40.7 MB)  TX bytes:8911462 (8.9 MB)
```
lspci -nnk | grep -iA2 net:

```
02:00.0 Ethernet controller [0200]: Atheros Communications AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7623]
    Kernel driver in use: atl1c
```
uname -r:

```
 3.0.0-26-generic
```
lshw -C network:

```
  *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 6c:62:6d:dd:0c:ae
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=atl1c  driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:41 memory:febc0000-febfffff ioport:e800(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 54:e6:fc:8a:6e:c2
       capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=rt2800usb  driverversion=3.0.0-26-generic firmware=0.29 ip=122.167.0.3 link=yes  multicast=yes wireless=IEEE 802.11bgn
```


Please let me know if anything else will help.

Thank you!

---

### Post by squakie on 2012-11-05
Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1902715") thread?

---

### Post by NikTh on 2012-11-05
Hi , 

**please edit your post** and remove **ESSID** and **Access Point** from iwconfig results. Not needed and can be considered as a security issue. 

Try this command and see if makes any difference 
```
sudo iwconfig wlan0 bit 54M
```

Also I see the link quality to 31/70 , this is not completely bad , but can be the reason of low speed.

Thanks

---

### Post by skullnbones on 2012-11-05
> **squakie said:**
> Have you seen [this]("http://ubuntuforums.org/showthread.php?t=1902715") thread?


It seems to be working a lot quicker than before.  But how do I blacklist other drivers if I need to reboot the system?  Thank you!!

---

### Post by skullnbones on 2012-11-05
> **NikTh said:**
> Hi , 

**please edit your post** and remove **ESSID** and **Access Point** from iwconfig results. Not needed and can be considered as a security issue. 

Try this command and see if makes any difference 
```
sudo iwconfig wlan0 bit 54M
```Also I see the link quality to 31/70 , this is not completely bad , but can be the reason of low speed.

Thanks

Thanks for the heads up...I tried the code but didn't see any results.

---

### Post by NikTh on 2012-11-05
> **skullnbones said:**
> It seems to be working a lot quicker than before.  But how do I blacklist other drivers if I need to reboot the system?  Thank you!!


You have to edit the file /etc/modprobe.d/blacklist.conf and add the entries manually like this 
```
blacklist <module name>
``` 

Open the file with root privileges with gedit editor 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` 

and add at the end the lines (blacklist) you want. Save the file and when reboot the specific modules (you blacklisted) will not load. 

Thanks

---

### Post by skullnbones on 2012-11-05
> **NikTh said:**
> You have to edit the file /etc/modprobe.d/blacklist.conf and add the entries manually like this 
```
blacklist <module name>
```Open the file with root privileges with gedit editor 
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```and add at the end the lines (blacklist) you want. Save the file and when reboot the specific modules (you blacklisted) will not load. 

Thanks

That sounds clear enough but how do I find which modules I have that need to be blacklisted?

---

### Post by NikTh on 2012-11-05
I don't know , you said (asked) about blacklist some drivers. 
If you followed this solution and worked => [http://ubuntuforums.org/showthread.php?t=1902715](http://ubuntuforums.org/showthread.php?t=1902715)
then I don't think you have to blacklist something. Only the opposite in case you had blacklisted the rt2800usb module but you hadn't , because the rt2800usb seems loaded from the results of "lshw -C network" at the first post.

---

### Post by skullnbones on 2012-11-06
> **NikTh said:**
> I don't know , you said (asked) about blacklist some drivers. 
If you followed this solution and worked => [http://ubuntuforums.org/showthread.php?t=1902715](http://ubuntuforums.org/showthread.php?t=1902715)
then I don't think you have to blacklist something. Only the opposite in case you had blacklisted the rt2800usb module but you hadn't , because the rt2800usb seems loaded from the results of "lshw -C network" at the first post.

I did follow some of the instructions on that link but I got lost at the blacklisting part.  I've never done that before.  I think we'll leave this as it is now.  Thank you both for your help.  I'll mark this as solved....for now.

---

