---
title: "undo changes to wireless config"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by carleton97 on 2008-08-04
A while back, I was having issues with torrents, so I assigned a static ip, enabled port forwarding and all that good stuff. 

Now, I've moved to a new location and am unable to connect to the new router. I'm pretty sure I need to undo all of those changes and  go back to the basic Ubuntu wireless settings, but I cannot remember how to do it or where I found the info in the first place. 

Is there a command that will reset all of that? 

Thanks!

---

### Post by K2712 on 2008-08-04
Check [this link]("http://ubuntuforums.org/showthread.php?p=2316847#post2316847").

---

### Post by carleton97 on 2008-08-04
Thanks, but that didn't help. 

What's happening is that I choose my new home network from the dropdown and put in the passphrase in the window, but it's not accepting it. It just keeps bringing up the "Wireless Network Key Required" window again and again.

---

### Post by K2712 on 2008-08-04
Have you installed wpa-supplicant?

Also, could you post the output of:

```
lshw -C net
```

---

### Post by carleton97 on 2008-08-04
> **K2712 said:**
> Have you installed wpa-supplicant?

Also, could you post the output of:

```
lshw -C net
```

I have wpa-supplicant installed, yes. 

lshw -C net : 

*-network
     description: Wireless interface
     product: PRO/Wireless 4965 AG or AGN Network Connection
     vendor: Intel Corporation
     physical id: 0
     bus info: pci@0000:0600.0
     logical name: wmaster0
     version: 61
     serial: 00:1d:30:0f:11:dd
     width: 64 bits
     clock: 33MHz
     capabilities: bus_master cap_list logical ethernet physical wireless
     configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

*-network
     description: Ethernet interface
     product: NetLink BCM5787M Gigabit Ethernet PCI Express
     vendor: Broadcom Corporation
     physical id: 0
     bus info: pci@0000:08:00.0
     logical name: eth0
     version: 02
     serial: 00:1b:24:b4:65
     width: 64 bits
     clock 33MHz
     capabilities: bus_master cap_list ethernet physical
     configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m=v3.23 latency=0 module=tg3 multicast=yes

---

### Post by K2712 on 2008-08-04
Just covering the bases here but have you done [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Router%20Connection")?

---

### Post by carleton97 on 2008-08-04
> **K2712 said:**
> Just covering the bases here but have you done [this]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Router%20Connection")?

What I get from iwconfig is: 

lo          no wireless extensions.

eth0        no wireless extensions.

wmaster0    no wireless extensions.

wlan0       IEEE 802.11g  ESSID:"" Nickname:""
            Mode: Managed Frequency:2.437 GHz Access Point: 00.16:B6:B3:92:ff
            Bit Rate=54 Mb/s  Tx-Power=27 dBm
            Retry min limit:7   RTS thr:off   Fragment thr=2346 B
            Power Management: off
            Link Quality-84/100 Signal level=-64 dBm Noise level=-99 dBm 
            Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
            Tx excessive retries:0 Invalid misc:0 Missed beacon:0

---

### Post by carleton97 on 2008-08-04
UPDATE: 

For the first time I'm connected enough to see the signal bars, but I still keep getting asked for the password.

I checked my dmesg output adn get a repetition of: 

wlan0: authenticated
wlan0: associate with AP 00:16:b6:b3:92:ff
wlan0: RX ReassocResp from 00:16:b6:b3:92:ff
wlan0: associated
wlan0: RX deauthentication from 00:16:b6:b3:92:ff (reason=15)
wlan0: deauthenticated
wlan0: authenticate with AP 00:16:b6:b3:92:ff
wlan0: authentication from 00:16:b6:b3:92:ff (alg=0 transaction=2 status=0)
wlan0: autthenticated

the above just loops again and again.

---

