---
title: "Configuring Intel Pro/Wireless iwl-4965agn"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by jheaton5 on 2008-10-11
My card and driver are working well.  The card is the Intel Pro/Wireless 4965agn and the driver is the linux driver for that card: iwlagn.  Network Manager says my throughput speed is 1Mb/s.  That can't be right.  The appearance of speed is not much different from Firefox on vista.  My wireless router is Linksys WRT160N.  When I am booted on Windows Vista the througput is >120Mb/s.  Is NM not able to recognize 802.11n and therefore computes the speed incorrectly?  Or, is my card actually connected at 1Mb/s?  Is there a way to configure which channel is used?

---

### Post by jbrown96 on 2008-10-11
You might want to check your router and see the what speeds it supports/has enabled. I doubt that is the problem though. Could you try a speed test? If you have ssh install (```
sudo apt-get install openssh-server
``` if not), try to copy something large (like a Ubuntu disk image). ```
scp /PATH/TO/FILE USERNAME@LOCAL.IP.ADDRESS:./Desktop/
``` This will show you the speed during the transfer. You can then delete the copy from your Desktop.

---

### Post by jheaton5 on 2008-10-11
I have installed ssh and am trying to figure out how to do the copy test.  Exactly how will I know the transfer rate?  Will it show me in terminal?

In the meantime I ran this command
```
joel@joels-laptop:~$ sudo iwlist wlan0 scan
sudo: unable to resolve host joels-laptop
[sudo] password for joel: 
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:50:55:CF
                    ESSID:"linksysn"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=100/100  Signal level:-22 dBm  Noise level=-94 dBm
                    Encryption key:off
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000003db7aa1183
                    Extra: Last beacon: 12ms ago

```

According to the [manufacturer's guide]("http://download.intel.com/network/connectivity/products/prodbrf/Intel_Wireless_WiFi_Link_4965AGN_User_Guide.pdf") these bit rates correspond to 802.11g.

---

### Post by jbrown96 on 2008-10-13
Those rates do look a little slow, but I've never messed with 802.1n. Here is a sample scp command. Note that I ran a very small file, so the transfer never went too fast. You should use a large file (>100MB) to get accurate throughput. > jbrown96@LinuxLab13:~$ scp ./Documents/crack3.c jbrown96@HOST:./
jbrown96@HOST's password:
crack3.c                                      100% 2952     2.9KB/s   00:00


---

