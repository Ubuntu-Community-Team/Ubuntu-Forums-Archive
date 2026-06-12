---
title: "Intel PRO/Wireless 3945 driver not in Hardy?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by liquidus219 on 2008-05-04
I have recently done a fresh install of Hardy Heron on an Acer Aspire 5600 series latop, and now my intel PRO/Wireless 3945 card isn't using a proprietary driver, and there aren't any to choose from in the restricted drivers list.

Gutsy Gibbon had no problems with my card and had the driver installed - why has this feature been removed?

---

### Post by liquidus219 on 2008-05-04
I would really appreciate some help with finding and installing my wireless drivers, could someone please help me?

---

### Post by liquidus219 on 2008-05-04
Anybody?

---

### Post by bobnutfield on 2008-05-04
I can't tell you why the drive does not show up in Ubuntu's kernel, but the driver for this card is apparently available at:

[]("http://intellinuxwireless.org/iwlwifi.")

---

### Post by bobnutfield on 2008-05-04
Sorry, link did not post.  Here it is@

[http://intellinuxwireless.org/iwlwifi.]("http://intellinuxwireless.org/iwlwifi.")

---

### Post by PeterJS on 2008-05-04
They changed drivers, the Intel wireless now uses the free iwl3945 driver. It should just work, no need for an additional driver. Is the iwl3945 module loaded? and/or what happens when you load it?

---

### Post by Zorael on 2008-05-04
Intel's new driver is open source! :>

Small note though; my 3945ABG card wouldn't work at all until I created a file named **iwl3945** and placed it in **/etc/modprobe.d/**, with the following contents:
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1
```
If you see any networks at all then you likely don't need to do this. Mine couldn't see any, and by extension, I couldn't connect to any.


To perform a network scan in a terminal, enter this.
```
$ sudo iwlist scan
```

---

### Post by raskolikov on 2008-05-07
> **Zorael said:**
> Intel's new driver is open source! :>

Small note though; my 3945ABG card wouldn't work at all until I created a file named **iwl3945** and placed it in **/etc/modprobe.d/**, with the following contents:
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1
```
If you see any networks at all then you likely don't need to do this. Mine couldn't see any, and by extension, I couldn't connect to any.


To perform a network scan in a terminal, enter this.
```
$ sudo iwlist scan
```

I try, and for the first time it works.
I do, in shell, sudo iwlist eth1 scan, and finally it found my wireless network.
I configure by myself in system-Administration-network, with the ESSID and password for my network.
I get connect.
I reboot, but now doesn't work anymore......
There a new facts. When i type ifconfig, there's a new device:

eth1:avahi Link encap:Ethernet  HWaddr 00:1b:77:f1:0d:29  
          inet addr:169.254.4.222  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

and if I type iwconfig
eth1      IEEE 802.11g  ESSID:"Appa"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point  Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
This doesn't happen first to introduce your "magic" file in /etc/modprobe.d/
So, what i should do to get everything working automatically?

---

### Post by BoardDWorld on 2008-05-09
> **Zorael said:**
> Intel's new driver is open source! :>

Small note though; my 3945ABG card wouldn't work at all until I created a file named **iwl3945** and placed it in **/etc/modprobe.d/**, with the following contents:
```
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1 hwcrypto=1
```
If you see any networks at all then you likely don't need to do this. Mine couldn't see any, and by extension, I couldn't connect to any.


To perform a network scan in a terminal, enter this.
```
$ sudo iwlist scan
```

That's just what I needed to know, working perfect thank you.

---

### Post by idoisler on 2008-05-10
i tried to create the file and past it but it just wouldn't let me ???

---

### Post by liquidus219 on 2008-05-12
Well, my card technically does work without the proprietary driver, and everything works fine.

But when I shutdown, my network manager fails.

---

### Post by trondhuso on 2008-05-19
In Gutsy Wireless 3945 uses the restricted driver. In hardy it uses the open source driver. On my Dell d420 the WIFI-led didn't show up. It does under Gutsy (downgraded)

---

### Post by Nepherte on 2008-05-19
> **trondhuso said:**
> In Gutsy Wireless 3945 uses the restricted driver. In hardy it uses the open source driver. On my Dell d420 the WIFI-led didn't show up. It does under Gutsy (downgraded)
If you install the linux-backports-modules, the wifi led should work.

---

### Post by DO55 on 2008-05-20
> **Nepherte said:**
> If you install the linux-backports-modules, the wifi led should work.

i install backports but it  dose not solve the problem

---

### Post by trondhuso on 2008-05-27
> **Nepherte said:**
> If you install the linux-backports-modules, the wifi led should work.

Yup. Worked perfectly for me.

---

### Post by VitalBodies on 2008-05-27
This is a general/basic question un-related to the Intel pro/wireless:
How does one install backports? What are backports? Where are backports?

---

### Post by Nepherte on 2008-05-27
A full explanation on what a backport is: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

As for the modules for linux, the intel 3945 driver is an example, they are all packed into one package named 'linux-backports-modules-hardy'.

---

### Post by acreech on 2008-07-07
> **Nepherte said:**
> If you install the linux-backports-modules, the wifi led should work.



I did this and then was prompted to restart the computer. When it came back up I lost my screen resolution (1440X900) and my sound will not work. it also did not fix the problem with my Intel 3945ABG wireless network card. 

Any suggestions would be great.

---

### Post by VitalBodies on 2008-07-07
> **acreech said:**
> I did this and then was prompted to restart the computer. When it came back up I lost my screen resolution (1440X900) and my sound will not work. it also did not fix the problem with my Intel 3945ABG wireless network card. 

Any suggestions would be great.

Backports are really intended for advanced users so be careful if you are new to Ubuntu using them. 

You might try SYSTEM > ADMINISTRATION > SOFTWARE SOURCES 
And un-check anything related to the backports in an effort to try to make it back to where you began before the backports were used.

---

