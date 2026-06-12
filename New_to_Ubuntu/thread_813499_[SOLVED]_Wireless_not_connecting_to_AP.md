---
title: "[SOLVED] Wireless not connecting to AP"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by nittanylion on 2008-05-30
I've been troubleshooting this problem for quite a bit today, and haven't made much progress. For some unknown reason, a previously working wireless card will no longer connect to my network. It tries to connect, but at no point do any of the circles turn green in the wireless icon.

A few outputs (selected text):

**lspci -v** (truncated, as pertinent)
```
06:00.0 Network controller: Intel CorporationPRO/Wireless 3945ABG Network Connection (rev 02)
Subsystem: Intel Corporation Unknown device 1050
Flags: bus master, fast devsel, latency 0, IRQ 219
Memory at cc000000 (32-bit, non-prefetchable) [size=4K]
Capabilities: [c8] Power Management version 2
Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
Capabilities: [e0]Express Legacy Endpoint IRQ 0

0a:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
Subsystem: Sony Corporation Unknown device 81ef
Flags: bus master, medium devsel, latency 64, IRQ 21
Memory at d000f000 (32-bit, non-prefetchable) [size=4K]
I/O ports at 6000 [size=64]
Capabilities: [dc] Power Management version 2
```

**cat /etc/network/interfaces**
This doesn't look right, but after multiple alterations I haven't been able to find a fix. Below is default before I made any changes to the file, and my wireless card is and always has been eth1.
```
auto lo
iface lo inet loopback

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp
```

**ifdown eth1**
```
ifdown: interface not configured
```

**ifup eth1**
```
Ignoring unknown interface eth1=eth1.
```

**ifconfig**
```
eth0
Link encap:Ethernet HWaddr **:**:**:**:**:**:**
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
TX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

eth1
Link encap:Ethernet HWaddr: **:**:**:**:**:**:**
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
TX packets: 0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

lo
Link encap:Local loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACKRUNNING MTU:16436 Metric:1
RX packets:2111 errors:0 dropped:0 overruns:0 frame:0
TX packets:2111 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:109374 (106.8 KB) TX bytes:109374 (106.8 KB)

wmaster0
Link encap:UNSPEC HWaddr **-**-**-**-**-**-**-**-**-**-**-**-**-**-**-**
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:) errors:0 dropped:0 overruns:0 frame:0
TX packets:) errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0B)
```

**iwconfig**
```
lo     no wireless extensions
eth0     no wireless extensions
wmaster0     no wireless extensions
eth1     IEEE 802.11G ESSID:"" Nickname:""
Mode:Managed Frequenecy:2.462 GHz Access Point: **:**:**:**:**:**
Tx-Power:27 dBm
Retry min limit:7 RTS thr:off Fragment thr=2346 B
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
```

**cat /var/log/syslog** (these appear repeatedly as I attempt to connect to the AP)
```
...
<info> Device eth1 activation scheduled...
<info> Activation (eth1) started...
<info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
<info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
<info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
<info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete...
<info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
<info> Activation (eth1/wireless):access point '***' is unencrypted, no key needed.
<info> retry to connect to global supplicant socket (try=1)
<info> SUP: sending command 'INTERFACE_ADD eth1&I&Iwext&I/var/run/wpa_supplicant0^I'
<info> SUP: response was 'OK'
<info> SUP: sending command 'AP_SCAN 1'
<info> SUP: response was 'OK'
<info> SUP: sending command 'ADD_NETWORK'
<info> SUP: response was '0'
<info> SUP: sending command 'SET_NETWORK 0 ssid ******'
<info> SUP: response was 'OK'
<info> SUP: sending command 'SET_NETWORK 0 key_mgmt NONE'
<info> SUP: response was 'OK'
<info> SUP: sending command 'ENABLE_NETWORK 0'
<info> SUP: response was 'OK'
<info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
eth1: Initial auth_alg=0
eth1: authenticate with AP **:**:**:**:**:**
eth1: RX authentication from **:**:**:**:**:** (alg=0 transaction=2 status=0)
eth1: authenticated
eth1: associated with AP **:**:**:**:**:**
eth1: invalid aid value 0; bits 15:14 not set
eth1: RX AssocResp from **:**:**:**:**:** (capab=0x5 status=18 aid=0)
eth1: AP denied association (code=18)
eth1: associate with AP **:**:**:**:**:**
eth1: invalid aid value 0; bits 15:14 not set
eth1: RX AssocResp from **:**:**:**:**:** (capab=0x5 status=18 aid=0)
eth1: AP denied association (code=18)
eth1: associate with AP **:**:**:**:**:**
eth1: invalid aid value 0; bits 15:14 not set
eth1: RX AssocResp from **:**:**:**:**:** (capab=0x5 status=18 aid=0)
eth1: AP denied association (code=18)
eth1: association with AP **:**:**:**:**:** timed out
.....
```

A few other notes:
[LIST]
[*]"network-admin --configure eth1" produces a dialog box saying, "The interface does not exist. Check that it is correctly typed and that it is correctly supported by your system."
[*]The router has been completely reset to factory defaults, and the laptop will connect in WinXP from dual-boot.
[/LIST]

I really don't know where to go from here .. although finding out what code=18 means would be a step, I suppose. Does anyone see anything in these logs even hinting at what the problem is? Thanks for any help!

---

### Post by nittanylion on 2008-05-30
For future searches:

sudo apt-get install linux-backports-modules-hardy-generic

Unfortunately, I have no idea why this worked, but after this and a reboot, it works. Good times...

---

