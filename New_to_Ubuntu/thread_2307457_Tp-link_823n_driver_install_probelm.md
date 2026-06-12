---
title: "Tp-link 823n driver install probelm"
date: 2015-12-25
forum: New to Ubuntu
---

### Post by leisureren on 2015-12-25
DEAR ALL,
I have successfully installed the driver, but i still can't have wireless connection. 
leisure@leisure-All-Series:~/Desktop$ ifconfig
eth0      Link encap:Ethernet  HWaddr 30:5a:3a:58:99:fc  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::325a:3aff:fe58:99fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:276468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:157924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:396102211 (396.1 MB)  TX bytes:12150682 (12.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3765 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:366650 (366.6 KB)  TX bytes:366650 (366.6 KB)

wlan0     Link encap:Ethernet  HWaddr 22:22:20:4e:49:43  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
leisure@leisure-All-Series:~/Desktop$ iwconfig
eth0      no wireless extensions.

wlan0     unassociated  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency=2.412 GHz  Access Point: Not-Associated   
          Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.
please give me a guide, thank you!

---

### Post by kurt18947 on 2015-12-25
There are experts here, I am not one. A good start though would be to read this sticky if you haven't done so.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Run the wireless script and post the results here using code tags to make the output readable. Another simple step would be to run a command from a terminal. If PCI:
"lspci"

If USB
"lsusb"

The lines of interest would be those that mention 'network controller' or 'ethernet'. These will tell us what kind of chip set your adapter uses which is a place to start. It should look something like this:

```
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
```

The wireless script will tell us that and much more.

Edit:  Which driver did you install? According to wikidevi, if you have ver. 1 of that device, it uses an RTL-8192CU chip. 

[https://wikidevi.com/wiki/TP-LINK_TL-WN823N_v1](https://wikidevi.com/wiki/TP-LINK_TL-WN823N_v1)

That should 'sorta' work out of the box. There is a patch that makes it work much better. If you have ver. 2 or later it may well be a different chip set.

---

