---
title: "Wireless connection is super slow, did not install &quot;Third Party&quot; during installation"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by Amii on 2012-09-09
I have Windows 7 and Ubuntu 12.04 LTS installed. 

Windows 7 wireless works just fine. 

When switched over to Ubuntu, the wireless connection is unbearable (I think it also caused other computers in the network to lag too). When wired, the connection works fine. 

I remember during the installation, I did not check "Download updates" and "Install Third Party Software". 

I did not check "Download updates" because my first installation was stuck at "downloading language pack" (the speed was going like something B/sec) 

I looked back the "install third party software" box and saw that the description mentions something about wireless driver management. I wonder if that could've been why that my wireless is unbearable? :confused:

How do I fix the slow wireless connection? 

One thread that I looked up is this one (the topic is for a different version but I thought why not give it a try >_>)
[http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/](http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/)

The sudo command suggested is: 
sudo iwconfig
sudo iwconfig wlan0 power off

Did not solve my problem (>_<) 

Any other suggestions? 
Thank you in advance.

---

### Post by NikTh on 2012-09-09
Hi , 

if you want to see what drivers offered for you wireless , open additional drivers. 
From terminal ```
jockey-gtk
``` and see if any additional drivers are there for your wireless.

Give some more info . 

```
iwconfig 
ifconfig
lspci -nnk|grep -iA2 net
lsusb
```put the results between the ```
 brackets , so can be readable. 

**[noparse][code]The Results Here
```[/noparse]**

Thanks

---

### Post by Amii on 2012-09-09
@NikTh, 

Here are the requested information. Thank you so much for helping! :KS

[jockey-gtk screenshot: an window popped up after the terminal message. ]("http://i.imgur.com/kgh9tl.jpg")
[IMG]http://i.imgur.com/kgh9tl.jpg[/IMG]

jockey-gtk message:
```
lin@lin-A6200:~$ jockey-gtk 

(jockey-gtk:1947): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed 

(jockey-gtk:1947): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed 
lin@lin-A6200:~$ 

```


 

For lwconfig, I had to install it first (took like 5 minutes to download 2.9MB (T_T)” ) I don't think you want to see the installation message part, so the message log below is after I have already installed it :D 

```
lin@lin-A6200:~$ lwconfig
Usage: lwconfig [OPTIONS] [COMMAND]
Modify or view the configuration.

 Options:
    --verbose               Display additional information.

 Commands:
  SETTING [VALUE]           Change SETTING to the given VALUE(s) or the
                              default value if no value is specified.
  --list                    Display names of all settings.
  --show SETTING            Display current value(s) of SETTING.
  --detail SETTING          Display current value(s) and details of SETTING.
  --file FILE               Read FILE with each line beginning with a
                              setting name followed by value(s). Use '.'
                              for reading from stdin.
  --dump                    Dump all settings in a format suitable for use
                              with --file.
lin@lin-A6200:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 40:61:86:18:1f:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:125 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15078 (15.0 KB)  TX bytes:15078 (15.0 KB)

wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:5c:30:6f  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:fe5c:306f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4065 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3801138 (3.8 MB)  TX bytes:215728 (215.7 KB)

lin@lin-A6200:~$ lspci -nnk|grep -iA2 net
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Micro-Star International Co., Ltd. Device [1462:1033]
	Kernel driver in use: r8169
lin@lin-A6200:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 003: ID 045e:0737 Microsoft Corp. Compact Optical Mouse 500
lin@lin-A6200:~$ 

```

---

### Post by NikTh on 2012-09-09
Hi , 

please copy-paste from here to your terminal the command 

```
iwconfig
``` 

is not l(L) is (i) , like **i**fconfig

Thanks

---

### Post by Amii on 2012-09-09
@NikTh, 
Oh my god, sorry :( should've gotten my eye contacts before I wrote them down on the paper. I will be right back with the correct info!

Edited: 

Correct iwconfig info :D

```
lin@lin-A6200:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn   
          Mode:Managed  Frequency:2.437 GHz  Access Point: C8:3A:35:5E:57:D8   
          Bit Rate=121.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:54   Missed beacon:0

eth0      no wireless extensions.

lin@lin-A6200:~$






```

---

### Post by NikTh on 2012-09-09
Hi , 

you can **remove the ESSID** from the results. Edit your post above. 

and try this 

```
sudo iwconfig wlan0 bit 54M
``` copy-paste the command from here to terminal and then give again the results 

```
iwconfig
```Thanks

---

### Post by Amii on 2012-09-10
Here is the new log:


```
lin@lin-A6200:~$ iwconfig 
lo        no wireless extensions. 
 
wlan0     IEEE 802.11bgn     
          Mode:Managed  Frequency:2.437 GHz  Access Point: C8:3A:35:5E:57:D8    
          Bit Rate=54 Mb/s   Tx-Power=15 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:on 
          Link Quality=53/70  Signal level=-57 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:144  Invalid misc:42   Missed beacon:0 
 
eth0      no wireless extensions. 
 
lin@lin-A6200:~$  
 
 


```

One really weird thing that I found out is that I have no problem with wireless connection with Ubuntu on campus (X_X). So this wireless problem only occurs with my home connection in Ubuntu. I hope this problem can be fixed because Ubuntu is much faster to use >_<

---

### Post by NikTh on 2012-09-11
Hi , 

Now its seems much better. 

You have a good wireless signal ```

Link Quality=53/70
```and the bit rate is more appropriate. 54Mb/s 

Still having the same problem ?

The modification we did before is not permanent. It will be lost in next reboot. 

So give the command 

```
sudo iwconfig wlan0 bit 54M
``` 

and then check if your wireless works better. If yes , we can do it permanent later. 

Thanks

---

