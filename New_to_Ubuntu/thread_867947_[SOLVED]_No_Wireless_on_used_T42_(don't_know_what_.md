---
title: "[SOLVED] No Wireless on used T42 (don't know what I'm supposed to see or have)"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by bellmount on 2008-07-23
Hello,
I bought a used IBM T42 (my first laptop) without OS, installed Ubuntu (my first linux), am now trying to set up the wireless (unexperienced yet) and now find myself in for a bit too much.

The installation went rather smoothly; got the video, managed to get the audio working, played around with the Ubuntu-laptop for about two weeks so we could become friends, found out I couldn't connect my old adsl-modem as it is not supported by linux (doesn't matter, just telling you so you know I haven't installed anything other than Ubuntu yet) but I can't see any wireless.

[FONT=Courier New] ifconfig[/FONT]    shows only [FONT=Courier New]eth0 [/FONT]and[FONT=Courier New] lo[/FONT]
[FONT=Courier New] iwconfig[/FONT]    lists 3 items ([FONT=Courier New]lo, eth0, irda0[/FONT]), all have "[FONT=Courier New]no wireless extensions"[/FONT]

One of my problems using all the various help-pages is that I can't really specify "my" make or model of e.g. the wificard and also, I can only use my old XP PC for the information-hunt on the internet and can't easily transfer stuff between the laptop and the pc because only the laptop has a working CDdrive so I'm typing the outputs manually here, hoping to avoid typos while trying to give you as much information as you need. :-/
 
From the seller I know there should be "Modem 56Kbps ITU V.92 Hayes AT-Befehlssatz, Intel PRO/1000 MT Mobile Connection, Cisco Wireless 802.11b 11MBit". From Ubuntu I get:

l[FONT=Courier New]shw
*network:0
Ethernet interface
82540EP Gigabit Ethernet Controller (Mobile)
    configuration: broadcast=yes   driver=e1000   driverversion=7.3.20-k2-NAPI             firmware=N/A  latency=64   mingnt=255   module=e1000   multicast=yes

*network:1
Network Controller
Cisco Aironet Wireless 802.11b (driver=airo)

*-communication UNCLAIMED
    description: Modem
    product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
    vendor: Intel Corporation
    configuration: latency=0
[/FONT]   

I'm very confused right now as this is really not my field of expertise and I'm beginning to run in circles so I'd love to hear from someone who knows what they're doing where I need go from here. Do I need the firmware for the ethernet device (is this the Intel Pro/1000?), is Cisco the wireless and if it is, I read it should work out of the box so does it have the right driver?

Any help or hint is greatly appreciated.
Have a nice day,
bellmount

---

### Post by northern lights on 2008-07-23
Run ```
gedit /etc/modprobe.d/blacklist
``` from a terminal and at the end of the file add these lines:

```
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
```

---

### Post by cozmicharlie on 2008-07-23
> **northern lights said:**
> Run [gedit /etc/modprobe.d/blacklist]("gedit /etc/modprobe.d/blacklist")

and at the end of the file add these lines:

```
# these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes
```


northernlights suggestion should work for you.  

Since you are new to Linux I thought you might need a little more detail.
To run gedit you open a terminal and copy and paste the command at the prompt.
```
gedit /etc/modprobe.d/blacklist
```
  Once the file comes up, copy and paste the lines from northernlights post to the end of the file.  Save and close.  Retry your wireless.

---

### Post by bellmount on 2008-07-23
My, you guys are quick. And efficient. *beam*

After a reboot the wireless lights up now and I get "wireless" as an option when I click on the network manager. 

ifconfig shows eth0, lo and eth1 now
iwconfig additionally gives wifi0
lshw shows *-network:1 configured with driver=airo  (which I hope is okay since you  instructed me to "break" the driver  - which I hadn't heard before and will google now.)


So thank you both ever so much, you've totally made my day. :-))
All the best,
bellmount

---

### Post by cozmicharlie on 2008-07-23
Great to hear you are up and running.  Have fun with your new Ubuntu OS.  Also, please mark this thread as solved.

Enjoy

---

### Post by headfirst_for_halos on 2010-03-19
Is the file supposed to look like this?

---

