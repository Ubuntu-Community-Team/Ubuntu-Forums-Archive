---
title: "My download speed is being throttled at ~300KB/s on battery power"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by akand074 on 2011-09-12
Is anyone else getting their internet throttled on battery? I'm at my University and I get about 2-3MB/s download when I plug my laptop into power in Ubuntu 11.10 but I always get about 300KB/s on battery power. I haven't tested the speed in the same place but I just did a speed test on Wifi in Ubuntu and it gave me ~3Mb/s. I did it on my Android phone on Wifi and I got ~15.5Mb/s speed. So I believe Ubuntu is throttling me on battery power. Is there anyway to find these settings and disable them?

---

### Post by hugmenot on 2011-09-12
Look in /usr/lib/pm-utils/power.d. It’s probably in wireless there.

What card and driver do you have?

---

### Post by akand074 on 2011-09-12
> **hugmenot said:**
> Look in /usr/lib/pm-utils/power.d. It’s probably in wireless there.

What card and driver do you have?

Broadcom BCM4322. I have the proprietary drivers installed via Additional Drivers. I am looking at the wireless script in that folder, it looks like there is power saving features but nothing standing out that points to throttling. I wouldn't mind disabling power saving for wireless all together but I wouldn't be positive as to what to change.

---

### Post by sammiev on 2011-09-12
Tried it every which here and all is at it's max. I hope you get by it. :) Please give us updates.

---

### Post by alexmurray on 2011-09-12
To disable power-management of the wifi card, when on battery try running the following from a console:

```
sudo iwconfig ethX power off
```

(where ethX is your wifi device)

---

### Post by akand074 on 2011-09-13
> **alexmurray said:**
> To disable power-management of the wifi card, when on battery try running the following from a console:

```
sudo iwconfig ethX power off
```(where ethX is your wifi device)

You sir, are a genius. Ran that code and boom immediately jumped to 2MB/s download speed. Thanks!

---

### Post by alexvy13 on 2011-09-13
What exactly do I put in place for ethX? I'm not sure where to get the info

---

### Post by hugmenot on 2011-09-13
What are you people doing testing the development release when you are not capable of figuring out which network device has which name?

---

### Post by alexvy13 on 2011-09-13
Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

what exactly do i put in?

---

### Post by JD8182 on 2011-09-13
People learn by doing my friend, no reason to point fingers at those of us that are still in the learning process of using the wonderful world of Ubuntu. Problems happen, and I believe this is the purpose of this website to post your issues, even if we are unexperienced users. Good day..


> **hugmenot said:**
> What are you people doing testing the development release when you are not capable of figuring out which network device has which name?

---

### Post by alexmurray on 2011-09-13
Run iwconfig in a terminal and it should list all network interfaces, and for those which are a wifi device it will display a bunch of stuff like SSID etc - from this you should see what name is given to your wifi device (each is named something like eth0 or eth1 - or maybe even wifi0 etc)

---

### Post by alexvy13 on 2011-09-13
> **alexmurray said:**
> Run iwconfig in a terminal and it should list all network interfaces, and for those which are a wifi device it will display a bunch of stuff like SSID etc - from this you should see what name is given to your wifi device (each is named something like eth0 or eth1 - or maybe even wifi0 etc)

this is what i got


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Red Panda"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:2F:E8:4D:0A   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid: 0  Rx invalid crypt:0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc:66   Missed beacon: 0

idk why it says no wireless extensions when my wireless works fine

---

### Post by cariboo on 2011-09-13
Are you sure your device isn't wlan0? Open a terminal and type:

```
ifconfig
```

you should see all your network interfaces listed.

---

### Post by alexvy13 on 2011-09-13
eth0      Link encap:Ethernet  HWaddr c8:0a:a9:54:9a:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 78:e4:00:32:af:a2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae4:ff:fe32:afa2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:37938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42859415 (42.8 MB)  TX bytes:6321380 (6.3 MB)

---

### Post by cariboo on 2011-09-14
From your ifconfig output your wireless device is wlan0, so the command would look like this.

```
sudo iwconfig wlan0 power off
```

---

### Post by alphacrucis2 on 2011-09-14
Your wireless device is wlan0. Eth0 is the wired ethernet port which I presume you are not using. Some wireless drivers will name the wireless as though it is an ethernet device but not in your case (or mine) ;)

---

