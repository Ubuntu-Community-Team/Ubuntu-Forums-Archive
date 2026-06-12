---
title: "Wireless Problems (Can detect networks, but not connect)"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by CeBiff on 2008-06-13
Hi, this is my first day with ubuntu..

I'm loving it so far, but I ca'nt get wireless working!

I have a lenovo t61p thinkpad with a ThinkPad 11a/b/g Wi-Fi wireless LAN Mini-PCIe US/EMEA/LA/ANZ

I'm using the Atheros hardware access layer (HAL)  and support for atheros 802.11 wireless lan card drivers that came with 8.04

I can detect networks and i enter in the password for my connection, but it either gets stuck on the part where it sohws two arrows making a circle, or it connects but doesn't get any packets.

What can I do?

Thanks

If it would be easier for you to talk to me on AIM about this, my AIM is cebiff

---

### Post by balagosa on 2008-06-13
> **CeBiff said:**
> Hi, this is my first day with ubuntu..

I'm loving it so far, but I ca'nt get wireless working!

I have a lenovo t61p thinkpad with a ThinkPad 11a/b/g Wi-Fi wireless LAN Mini-PCIe US/EMEA/LA/ANZ

I'm using the Atheros hardware access layer (HAL)  and support for atheros 802.11 wireless lan card drivers that came with 8.04

I can detect networks and i enter in the password for my connection, but it either gets stuck on the part where it sohws two arrows making a circle, or it connects but doesn't get any packets.

What can I do?

Thanks

If it would be easier for you to talk to me on AIM about this, my AIM is cebiff

hmmm....mind posting the output of ```
iwconfig
``` and also ```
lshw -C network
```

---

### Post by CeBiff on 2008-06-13
iwconfig yielded this

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"domo"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:10:04:E0:A0   
          Bit Rate:54 Mb/s   Tx-Power:17 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-42 dBm  Noise level=-93 dBm
          Rx invalid nwid:34244  Rx invalid crypt:0  Rx invalid frag:0

Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)


lshw-c network yielded that

---

### Post by balagosa on 2008-06-13
> **CeBiff said:**
> 

lshw-c network yielded that

it is supposed to be **Capital C**. so do ```
lshw -**C** network
```

unlike windows, linux commands are Case-Sensitive.

yes you definitely can spot a Wireless network via ath. problem is, i need the output of lshw -C network to verify further. but i am puzzled about wifi0 though.

---

### Post by hyper_ch on 2008-06-13
what encryption does that wifi have?

---

### Post by CeBiff on 2008-06-13
*-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:8c:d1:16
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=0.3-0 latency=0 module=e1000 multicast=yes
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1f:3a:66:d5:55
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


that's what i got with the capital C

and it's a 64/128 hex WEP key i believe.

Sorry about messing up the console command

---

### Post by ukripper on 2008-06-13
Your drivers are fine. You need to check your WEP key. Is it ASCII or HEX?

---

### Post by CeBiff on 2008-06-13
> **ukripper said:**
> Your drivers are fine. You need to check your WEP key. Is it ASCII or HEX?

Well, just to make sure i'l lchange it to WPA and try it

---

### Post by ukripper on 2008-06-13
> **CeBiff said:**
> Well, just to make sure i'l lchange it to WPA and try it

you can try your WEP key with both hex and ascii and see if it connects but make sure your key is right. And I would recommend you use WPA or WPA2 as it is more secure

---

### Post by balagosa on 2008-06-13
> **ukripper said:**
> Your drivers are fine. You need to check your WEP key. Is it ASCII or HEX?

second to that...just had to check if your drivers were working fine.

---

### Post by CeBiff on 2008-06-13
> **ukripper said:**
> Your drivers are fine. You need to check your WEP key. Is it ASCII or HEX?

> **CeBiff said:**
> Well, just to make sure i'l lchange it to WPA and try it


:O

It works!  but it's kind of slow, but it works! it works! it works!

---

### Post by CeBiff on 2008-06-13
Well, now that i've been using it for a bit... I'm connected, but the packets seem to come in bursts.  It's like i'm disconnected for 5 seconds, then for one second I'm conenected  and i'm getting packets (but it always shows as connected)

---

### Post by balagosa on 2008-06-13
slow, you mean the signal strength or internet? even if you're like just a feet away from it?

glad to see it working. Go Ubuntu!

:KS

---

### Post by CeBiff on 2008-06-13
> **balagosa said:**
> slow, you mean the signal strength or internet? even if you're like just a feet away from it?

glad to see it working. Go Ubuntu!

:KS

i'm only a few feet from the router

in fact... the wireless is kinda unusable.. :(

but it works!  So that's progress

---

### Post by ukripper on 2008-06-13
> **CeBiff said:**
> i'm only a few feet from the router

in fact... the wireless is kinda unusable.. :(

but it works!  So that's progress

can you do folowing : ```
iwconfig
```

and ```
iwlist scan
```

---

### Post by hyper_ch on 2008-06-13
and put output text into

[noparse]```

```[/noparse]

brackets. that makes it easier to read.

---

### Post by CeBiff on 2008-06-13
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:"domo"  Nickname:""
          Mode:Managed  Frequency:2.484 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-42 dBm  Noise level=-94 dBm
          Rx invalid nwid:74978  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:13:10:04:E0:A0
                    ESSID:"domo"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-43 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:0C:41:F4:4E:C9
                    ESSID:"PrivateGetLost"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:12:88:36:52:E1
                    ESSID:"2WIRE006"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:13:10:04:E0:A0
                    ESSID:"domo"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-43 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:0C:41:F4:4E:C9
                    ESSID:"PrivateGetLost"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:12:88:36:52:E1
                    ESSID:"2WIRE006"
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Quality=3/70  Signal level=-92 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
```

---

### Post by CeBiff on 2008-06-13
did I do something wrong?  I'm not very good with the terminal

---

### Post by ukripper on 2008-06-13
> **CeBiff said:**
> did I do something wrong?  I'm not very good with the terminal

You did it right. Just looking at your Access point it seems normal to me. What exactly you think is running slow on your machine?

Looking at your iwconfig output your Accespoint is not associated.

Are you using nm-applet?

---

### Post by CeBiff on 2008-06-13
> **balagosa said:**
> slow, you mean the signal strength or internet? even if you're like just a feet away from it?

glad to see it working. Go Ubuntu!

:KS

> **ukripper said:**
> You did it right. Just looking at your Access point it seems normal to me. What exactly you think is running slow on your machine?

the connection is slow, or it's like a leaky faucet with the drops being packets, if that makes sense 

it takes a while for each drop, but there is a steady supply of them, band once it's dripping it loads stuff pretty fast

---

### Post by CeBiff on 2008-06-13
> **ukripper said:**
> You did it right. Just looking at your Access point it seems normal to me. What exactly you think is running slow on your machine?

Looking at your iwconfig output your Accespoint is not associated.

Are you using nm-applet?

oh sorry missed the applet part.. i don't know what that is :\

---

### Post by ukripper on 2008-06-13
> **CeBiff said:**
> the connection is slow, or it's like a leaky faucet with the drops being packets, if that makes sense 

it takes a while for each drop, but there is a steady supply of them, band once it's dripping it loads stuff pretty fast

you might want to try turning ipv 6 off.

do following:

1. ```
sudo gedit /etc/modprobe.d/aliases
``` 
2. Find the line: > alias net-pf-10 ipv6
3. change this to: > alias net-pf-10 **off ipv6**
4. Save  file, exit and reboot

---

### Post by CeBiff on 2008-06-13
well right now wireless is working really well :O

---

### Post by ukripper on 2008-06-13
> **CeBiff said:**
> well right now wireless is working really well :O

you mean after turning ipv6 off or just without?

---

### Post by CeBiff on 2008-06-13
well i didn't do the ipv6 and it was owrking well, but i left for 5 minutes and when i came back it was down again.  i'm gonna try the ipv6 fix now

---

### Post by CeBiff on 2008-06-13
i just rebooted after turning ipv6 off and it seems to be working great, but only time will tell

---

### Post by ukripper on 2008-06-13
> **CeBiff said:**
> i just rebooted after turning ipv6 off and it seems to be working great, but only time will tell

Yeh, can you post your iwconfig now while it is working.

---

### Post by CeBiff on 2008-06-13
```
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"domo"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:10:04:E0:A0   
          Bit Rate:1 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-42 dBm  Noise level=-99 dBm
          Rx invalid nwid:2790  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by ukripper on 2008-06-13
> **CeBiff said:**
> ```
 Access Point: **00:13:10:04:E0:A0 **  
          
```

That confirms it is connected to your router/access point.

---

