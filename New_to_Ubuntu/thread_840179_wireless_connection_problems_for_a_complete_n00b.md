---
title: "wireless connection problems for a complete n00b"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Marvxcore on 2008-06-25
Hey I set up Ubuntu round my friends house and everything seemed to work fine there. But now I'm home I can't seem to connect to my router. It came up showing a list of networks but when I tried to connect to mine it just wouldn't connect. I tried disabling and enabling the broadcom driver and that didn't work. Then, being the idiot I am, tried to do it through the Manual Configuration and now it doesn't show that there are any networks!

there's not much to go on there, so if you do need to know anything just ask and I'll try and find out:)

thanks in advance

---

### Post by dwhitney67 on 2008-06-25
Do you remember the driver that you were using?  Is it still loaded?  If you know the name, try this:
```
$ lsmod | grep <driver>
```
where <driver> is the driver name.

While your at is, also post the results from this command:
```
$ lspci | grep Network
```

P.S.  Is your wired-network interface available?

---

### Post by Marvxcore on 2008-06-25
> **dwhitney67 said:**
> Do you remember the driver that you were using?  Is it still loaded?  If you know the name, try this:
```
$ lsmod | grep <driver>
```
where <driver> is the driver name.

While your at is, also post the results from this command:
```
$ lspci | grep Network
```

P.S.  Is your wired-network interface available?
Hey, I tried "lsmod | grep <Broadcom B43>" but to no avail. it came up with "bash: syntax error near unexpected token `newline'":s

This is what came up with the other command
"marv@marv-laptop:~$  lspci | grep Network
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)"

I'm plugged directly into my router at the moment and all is working fine

---

### Post by dwhitney67 on 2008-06-25
> **Marvxcore said:**
> Hey, I tried "lsmod | grep <Broadcom B43>" but to no avail. it came up with "bash: syntax error near unexpected token `newline'":s

I believe you now!  Incredulous that a noob would assist friends in setting up Ubuntu.

Try running:
```
$ lsmod | grep b43
```

---

### Post by Marvxcore on 2008-06-25
> **dwhitney67 said:**
> I believe you now!  Incredulous that a noob would assist friends in setting up Ubuntu.

Try running:
```
$ lsmod | grep b43
```
lol me and my friend just thought we would try out ubuntu, he is a bit more computer literate me though and hasn't really had any problems.

and that command came up with 

"marv@marv-laptop:~$ lsmod | grep b43
b43                   144420  0 
rfkill                  8592  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  2 b43,b44"


sorry i really know nothing! what can i do with that?

---

### Post by dwhitney67 on 2008-06-25
The 'b43' is hopefully the appropriate kernel driver for your wireless chipset.  I just wanted to make sure that it is still being loaded during boot-up.

Let's see if your wireless is being initialized... run these and please report back the results:
```
$ dmesg | grep wlan0
$ dmesg | grep b43
```

---

### Post by Marvxcore on 2008-06-25
ok done that, here are the results

> marv@marv-laptop:~$ dmesg | grep wlan0
[   96.451231] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  103.889201] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  594.024276] wlan0: Initial auth_alg=0
[  594.024284] wlan0: authenticate with AP 00:11:f5:86:56:5b
[  594.026059] wlan0: RX authentication from 00:11:f5:86:56:5b (alg=0 transaction=2 status=1)
[  594.026065] wlan0: AP denied authentication (auth_alg=0 code=1)
[  594.060652] wlan0: authenticate with AP 00:11:f5:86:56:5b
[  594.061069] wlan0: RX authentication from 00:11:f5:86:56:5b (alg=0 transaction=2 status=1)
[  594.061074] wlan0: AP denied authentication (auth_alg=0 code=1)
[  594.140243] wlan0: authenticate with AP 00:11:f5:86:56:5b
[  594.140668] wlan0: RX authentication from 00:11:f5:86:56:5b (alg=0 transaction=2 status=1)
[  594.140673] wlan0: AP denied authentication (auth_alg=0 code=1)
[  594.170722] wlan0: authentication with AP 00:11:f5:86:56:5b timed out
[  732.838164] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  732.850956] wlan0: Initial auth_alg=0
[  732.850965] wlan0: authenticate with AP 00:11:f5:86:56:5b
[  732.852544] wlan0: RX authentication from 00:11:f5:86:56:5b (alg=0 transaction=2 status=1)
[  732.852549] wlan0: AP denied authentication (auth_alg=0 code=1)
[  732.897872] wlan0: authenticate with AP 00:11:f5:86:56:5b
[  732.898277] wlan0: RX authentication from 00:11:f5:86:56:5b (alg=0 transaction=2 status=1)
[  732.898281] wlan0: AP denied authentication (auth_alg=0 code=1)
[  732.951235] wlan0: authenticate with AP 00:11:f5:86:56:5b
[  732.951666] wlan0: RX authentication from 00:11:f5:86:56:5b (alg=0 transaction=2 status=1)
[  732.951671] wlan0: AP denied authentication (auth_alg=0 code=1)
[  732.960878] wlan0: authentication with AP 00:11:f5:86:56:5b timed out


and


> marv@marv-laptop:~$ dmesg | grep b43
[   94.918759] b43-phy0: Broadcom 4318 WLAN found
[   94.926106] b43-phy0 debug: Found PHY: Analog 3, Type 2, Revision 7
[   94.926133] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   95.099607] b43-phy1: Broadcom 4318 WLAN found
[   95.143058] b43-phy1 debug: Found PHY: Analog 3, Type 2, Revision 7
[   95.143086] b43-phy1 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 8
[   95.295463] input: b43-phy1 as /devices/virtual/input/input9
[   95.497339] b43-phy1 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   96.416781] b43-phy1 debug: Chip initialized
[   96.417241] b43-phy1 debug: 32-bit DMA initialized
[   96.421396] Registered led device: b43-phy1:tx
[   96.421615] Registered led device: b43-phy1:rx
[   96.421745] Registered led device: b43-phy1:radio
[   96.421781] b43-phy1 debug: Wireless interface started
[   96.434790] b43-phy1: Radio hardware status changed to DISABLED
[   96.448262] b43-phy1 debug: Adding Interface type 2
[   96.593016] b43-phy1 debug: Removing Interface type 2
[   96.607357] b43-phy1 debug: Wireless interface stopped
[   96.607453] b43-phy1 debug: DMA-32 0x0200 (RX) max used slots: 0/64
[   96.607509] b43-phy1 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[   96.613693] b43-phy1 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[   96.614395] b43-phy1 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[   96.617657] b43-phy1 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[   96.618944] b43-phy1 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[   96.619611] b43-phy1 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[  102.848053] input: b43-phy1 as /devices/virtual/input/input10
[  102.981177] b43-phy1 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  103.870760] b43-phy1 debug: Chip initialized
[  103.871223] b43-phy1 debug: 32-bit DMA initialized
[  103.875078] Registered led device: b43-phy1:tx
[  103.875321] Registered led device: b43-phy1:rx
[  103.875452] Registered led device: b43-phy1:radio
[  103.875489] b43-phy1 debug: Wireless interface started
[  103.882805] b43-phy1: Radio hardware status changed to DISABLED
[  103.886271] b43-phy1 debug: Adding Interface type 2
[  580.588244] b43-phy1: Radio hardware status changed to ENABLED
[  731.644313] b43-phy1 debug: Removing Interface type 2
[  731.655742] b43-phy1 debug: Wireless interface stopped
[  731.655841] b43-phy1 debug: DMA-32 0x0200 (RX) max used slots: 1/64
[  731.655901] b43-phy1 debug: DMA-32 0x02A0 (TX) max used slots: 0/128
[  731.661959] b43-phy1 debug: DMA-32 0x0280 (TX) max used slots: 0/128
[  731.662630] b43-phy1 debug: DMA-32 0x0260 (TX) max used slots: 0/128
[  731.663098] b43-phy1 debug: DMA-32 0x0240 (TX) max used slots: 0/128
[  731.663591] b43-phy1 debug: DMA-32 0x0220 (TX) max used slots: 2/128
[  731.664123] b43-phy1 debug: DMA-32 0x0200 (TX) max used slots: 0/128
[  731.697844] input: b43-phy1 as /devices/virtual/input/input11
[  731.838275] b43-phy1 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  732.822801] b43-phy1 debug: Chip initialized
[  732.823288] b43-phy1 debug: 32-bit DMA initialized
[  732.826358] Registered led device: b43-phy1:tx
[  732.826663] Registered led device: b43-phy1:rx
[  732.826831] Registered led device: b43-phy1:radio
[  732.826869] b43-phy1 debug: Wireless interface started
[  732.835029] b43-phy1 debug: Adding Interface type 2

---

### Post by dwhitney67 on 2008-06-25
Well, it appears that your wlan0 (wireless) interface is up, but is failing to connect to the Access Point (AP) as shown below:
```
[ 594.024284] wlan0: authenticate with AP 00:11:f5:86:56:5b
[ 594.026059] wlan0: RX authentication from 00:11:f5:86:56:5b (alg=0 transaction=2 status=1)
[ 594.026065] wlan0: AP denied authentication (auth_alg=0 code=1)
```

I presume you have the Gnome Network Manager applet running.  Using the mouse, right-click on the icon and select "Enable Wireless" to ensure that it is enabled.

Then repeat, using a left-click... do you see any wireless Access Points listed?

P.S.  You should also be able to view if wlan0 exists by running:
```
$ /sbin/ifconfig wlan0
```

---

### Post by Marvxcore on 2008-06-25
now the problem is, when i go to that, it doesn't say enable wireless, only enable networking which is ticked.:s

> marv@marv-laptop:~$ /sbin/ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:19:7d:0c:5d:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by dwhitney67 on 2008-06-25
Well, I don't know... here are something you can play with and report back results... maybe someone else can help:
```
$ iwlist wlan0 scan
$ iwconfig wlan0
```
And lastly, I assume you have a laptop... is the physical hardware switch for the wireless chipset turned on?

Ubuntu dumbs-down their System->Administration->Networks Gnome GUI so much that it is essentially useless.  On Fedora, one can setup a new interface, associate it with a particular interface (e.g. wlan0), activate/deactivate it, etc.  I wish there was something similar with Ubuntu.

Btw, on my system, there is a script that lives in /etc/NetworkManager/dispatcher.d called '01ifupdown'.  If this exists on your system, try running it like:
```
$ sudo /etc/NetworkManager/dispatcher.d/01ifupdown wlan0 up
```
or maybe running
```
$ sudo /sbin/ifup wlan0
```

---

