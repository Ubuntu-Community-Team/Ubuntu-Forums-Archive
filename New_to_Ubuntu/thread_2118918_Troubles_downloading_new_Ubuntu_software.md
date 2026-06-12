---
title: "Troubles downloading new Ubuntu software"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by Crooow on 2013-02-22
I'm running Ubuntu 10.04 on a desktop with an Edimax EW-7811UN wireless USB adapter. I just got the computer online earlier today. My internet source is tethered from my Android smartphone, so it can be a bit slow at times, but it works. Except when I try to get new software from the Ubuntu Software Center. Downloads reach 50%, then suddenly stop with a message telling me to check my internet connection, and this: "Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7~dfsg-1ubuntu3.8_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.4.7%7Edfsg-1ubuntu3.8_i386.deb") 404  Not Found [IP: 91.189.92.200 80]"

iwconfig gives this reading:
```
jacob@jacob-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Dr Dugong Loves You"  Nickname:"<WIFI@REALTEK>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 44:A7:CF:EC:49:F9   
          Bit Rate:48 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-45 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```And ifconfig gives this reading:

```

jacob@jacob-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:c2:0e:c8:30  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3776 (3.7 KB)  TX bytes:3776 (3.7 KB)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:94:34:07  
          inet addr:192.168.43.232  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fe94:3407/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76042 errors:0 dropped:33780 overruns:0 frame:0
          TX packets:66385 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:102757341 (102.7 MB)  TX bytes:9122626 (9.1 MB)

```I'm still new to Ubuntu, and so I have no idea why this dialog appears or what to do about it. :( Any help would be highly appreciated!

---

### Post by collisionystm on 2013-02-22
You need to first do a 

sudo apt-get update

and then try to install that again.

---

### Post by Crooow on 2013-02-22
Thank you. I'm updating now, if I have any other problems I'll be sure to post them here. ):P

---

### Post by Crooow on 2013-02-22
Ok, so I've updated Ubuntu. Now when I try downloading Wine, I receive a different error message: that this download requires the installation of untrustworthy packages, with this line of detail:

ttf-symbol-replacement-wine1.3 wine wine1.3 wine1.3-gecko winetricks

---

### Post by collisionystm on 2013-02-22
Try adding the repo and then installing Wine.

[I]sudo add-apt-repository ppa:ubuntu-wine/ppa

sudo apt-get update

sudo apt-get install wine1.5



[/I]You should know that the version of Ubuntu you are running, 10.04 LTS is no longer supported after April of this year. It will have hit its 3 year support mark.

You should upgrade it to 12.04 LTS which will be supported until 2017.

---

### Post by Crooow on 2013-02-23
Thanks, your solution worked brilliantly. 

Updating to 12.04 is definitely on my list once my data plan renews next week.

---

### Post by camarodemon on 2013-02-23
im a noob at this im having a hard time finding a way to install my AMD Radeon HD 6310 Discrete-Class graphics drivers any one know how to do this? im using 12.10 64 bit HP 2000-2b09wm

---

### Post by zombifier25 on 2013-02-23
Open Software Sources, go to the Additional Drivers tab. The proprietary drivers should be listed there.

---

### Post by Mark Phelps on 2013-02-24
> **Crooow said:**
> Ok, so I've updated Ubuntu. Now when I try downloading Wine, I receive a different error message: that this download requires the installation of untrustworthy packages, with this line of detail:

ttf-symbol-replacement-wine1.3 wine wine1.3 wine1.3-gecko winetricks

Just curious ... why are you installing Wine? Did someone tell you that you could use Wine to install Windows drivers? Because, if they did, that's not true.  You can only use Wine to install SOME Windows apps -- NOT drivers.

---

