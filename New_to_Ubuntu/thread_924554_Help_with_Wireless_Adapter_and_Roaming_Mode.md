---
title: "Help with Wireless Adapter and Roaming Mode"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by styfle on 2008-09-19
I'm am new to ubuntu (windows user) and I thought I would give my laptop a new life by installing ubuntu on it. Everything seems to work great considering its about 6 or 7 years old. The problem is my network adapter. It completely screws up my system when I have it in roaming mode, but I tried manual connection and that worked perfectly. It's a Linksys WPC54G Ver.2. Here's a picture [IMG]http://www.intellex-it.com/shop/images/LINKSYS%20Wireless-G%20Notebook%20Adapter.jpg[/IMG]

Any ideas how to fix it?

---

### Post by styfle on 2008-09-20
I forgot to mention what happens if I have roaming selected, it startes to connect to the network and then the icon next the the volume disappears. Then my keyboard doesnt work and the only thing I can do is reboot.

---

### Post by styfle on 2008-09-22
Bump...
Any ideas?

---

### Post by anewguy on 2008-09-22
Did you install a driver for your wireless, and if so, how?  If not, is it using one of the ones built in to Ubuntu?

---

### Post by styfle on 2008-09-23
> **anewguy said:**
> Did you install a driver for your wireless, and if so, how?  If not, is it using one of the ones built in to Ubuntu?

No I didn't install any drivers. I just assumed it was working since I could see wireless networks. I honestly don't know how to install drivers on ubuntu.

---

### Post by styfle on 2008-09-23
Oh, and when I try to connect, the wifi icon next to the volume disappears and then my keyboard stops working. It's really weird

---

### Post by Tatty on 2008-09-23
try running:

```
sudo iwconfig <your device (eg wlan0)> essid <your ESSID> key <key>
```

---

### Post by styfle on 2008-09-23
Is the ESSID the name of the router?
I forgot to mention that my router has WEP encryption

---

### Post by Tatty on 2008-09-23
> **styfle said:**
> Is the ESSID the name of the router?
I forgot to mention that my router has WEP encryption

Yes ESSID is the name of your router.  If you are unsure then do ```
sudo iwlist scan
``` to get this information.

WEP is fine for now, as it is easier to get working than WPA, just put your wep key where i wrote <key>.  Make sure you put this in as a hex key rather than a passphrase - you are supposed to be able to put in a passphrase in the format key s:<passphrase>, however this never worked for me.

After you get this problem sorted you may wish to consider converting to WPA as WEP can be cracked fairly easily.  Then you will have to install wpasuppliment to get ubuntu to connect.

---

### Post by styfle on 2008-09-23
> **Tatty said:**
> try running:

```
sudo iwconfig <your device (eg wlan0)> essid <your ESSID> key <key>
```

I did that and nothing seemed to happen. I did another sudo iwconfig and only my network came up

---

### Post by Tatty on 2008-09-23
> **styfle said:**
> I did that and nothing seemed to happen. I did another sudo iwconfig and only my network came up

In theory that command should have connected you to your wireless point.

Can you post the output of ```
sudo iwlist scan
``` and ```
iwconfig
```, just to make things a bit easier to see.

EDIT <offtopic>My 1000th post!  Just wanted to mark this :)</offtopic>

---

### Post by styfle on 2008-09-23
I just typed in iwconfig and only my network comes up
Im not connected though and firefox wont load sites

---

### Post by Tatty on 2008-09-23
> **styfle said:**
> I just typed in iwconfig and only my network comes up
Im not connected though and firefox wont load sites

If you could post the output of the above two commands it will help to see where you are at.

---

### Post by styfle on 2008-09-23
Ok I'll try to type it all (I'm typing on my desktop)

Output of sudo iwlist scan:
Cell 01 - Address: 00:18:39:D6:81:E6
ESSID: "Frausto"
Mode: Master
Frequency: 2.437 GHz Channel 6
Quality=32/100 Signal level 5/100 Noise lefvel 0/100
Encryption key: off
Bit rates: etc...
Thats my neigherbors and like 6 of these come up (im just gonna email the text

---

### Post by styfle on 2008-09-23
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:C4:4A:CB:B9
                    ESSID:"2WIRE744"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:29  Signal level:0  Noise level:0
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:18:39:D6:81:E6
                    ESSID:"Frausto"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/100  Signal level=11/100  Noise level=0/100
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:21:29:A1:1B:4C
                    ESSID:"linksys"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:29  Signal level:0  Noise level:0
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:12:17:E4:44:61
                    ESSID:""
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:29  Signal level:0  Noise level:0
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:0F:66:E4:AF:A6
                    ESSID:"Styfle"
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality=44/100  Signal level=21/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:21:7C:03:1C:49
                    ESSID:"2WIRE634"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/100  Signal level=2/100  Noise level=0/100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s

---

### Post by styfle on 2008-09-23
wlan0     IEEE 802.11b+/g+  ESSID:"Styfle"  Nickname:"Styfle"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0F:66:E4:AF:A6   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality=41/100  Signal level=17/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Tatty on 2008-09-23
Ok I see copying and pasting could be a problem, apologies.

Try this:

```
sudo dhclient wlan0
```

---

### Post by styfle on 2008-09-23
Well right now I'm connected through a manual connection (So I can copy and paste this)

Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:12:17:14:72:c8
Sending on   LPF/wlan0/00:12:17:14:72:c8
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.104 from 192.168.1.1
bound to 192.168.1.104 -- renewal in 34850 seconds.

---

### Post by styfle on 2008-09-23
I g2g so I'll check this thread tomorrow
Thanks for your help so far

---

### Post by Tatty on 2008-09-23
> **styfle said:**
> bound to 192.168.1.104 -- renewal in 34850 seconds.

According to this line, you now have an IP address so you should be connected to the internet.

Can you connect?  If not then try connecting to your router via firefox (usually an address such as 192.168.1.1)

---

### Post by styfle on 2008-09-24
Like I said in my first post: I can connect via Manual connection but I want to know why my computer F's up when its in roaming mode.

---

### Post by styfle on 2008-09-24
Well the good news is, I figured out how to change my theme. The bad news is I still have to reboot if I set my wireless to roaming mode.

---

