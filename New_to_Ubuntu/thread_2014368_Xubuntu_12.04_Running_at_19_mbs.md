---
title: "Xubuntu 12.04 Running at 19 mb/s"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by Absolummetry on 2012-07-01
Why hello there.

I've recently gotten into Xubuntu, after spending much time on XP. I currently run a Xubuntu and XP dual boot. My problem today is my Xubuntu speed.

It has always ran at a maximum of 54 mb/s. My XP, however, will run at a few hundred mb/s. I've been told that turning off Power Management, then adjusting the speed in the terminal would work.

In etc/pm/power.d I created a document called Wireless. Inside it says 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```

Now, I don't know if there is something wrong with that. Surely there must be, because when I enter **iwconfig **in Terminal, it comes  up with 
```
wlan0     IEEE 802.11bgn  ESSID:"Ravens"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 94:44:52:80:68:0C   
          Bit Rate=19.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1606  Invalid misc:5942   Missed beacon:0
```

If I go to change to bit rate...
```
matt@matt-MS-7255:~$ iwconfig wlan0 rate auto
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Operation not permitted.
```

Is Mode:Managed my problem? That is what I researched and found it out  to be. If so, how do I change it and why wasn't my fix working?

---

### Post by Merrattic on 2012-07-03
Try with sudo in front e.g.
```
sudo iwconfig wlan0 rate auto
```

---

