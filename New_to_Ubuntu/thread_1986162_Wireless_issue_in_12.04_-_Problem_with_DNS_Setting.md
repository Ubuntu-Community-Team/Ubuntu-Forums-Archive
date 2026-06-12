---
title: "Wireless issue in 12.04 - Problem with DNS Settings?"
date: 2012-05-24
forum: New to Ubuntu
---

### Post by jojo4349 on 2012-05-24
Hello

I am a relative newcomer to Ubuntu (and the forums).  I have had Ubuntu on my laptop for a few months now.  I upgraded to 12.04 a couple of weeks ago and since then, I cannot use the wireless.  It somehow connects and opens to my homepage, but then there is an error message which says the 'DNS lookup failed'.  I only have this problem with my home wireless and nowhere else...yet. 

I have looked at some other help topics about wireless issues and DNS settings, but as everything is so new to me, I don't understand it all :)

Any help would be greatly appreciated and I hope I explained my problem.

---

### Post by chamber on 2012-05-24
Post the output of 

```
lspci
```

---

### Post by jojo4349 on 2012-05-24
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 100
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

---

### Post by chamber on 2012-05-24
post output of

```
dmesg | grep wlan
lsmod | sort 
```

---

### Post by jojo4349 on 2012-05-24
Ok, here goes: 

```
[   18.459304] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.460066] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2484.348722] wlan0: authenticate with 00:0c:c3:7c:75:04 (try 1)
[ 2484.351317] wlan0: authenticated
[ 2484.357141] wlan0: associate with 00:0c:c3:7c:75:04 (try 1)
[ 2484.362867] wlan0: RX AssocResp from 00:0c:c3:7c:75:04 (capab=0x411 status=0 aid=2)
[ 2484.362888] wlan0: associated
[ 2484.375165] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2487.608873] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55933 PROTO=2 
[ 2487.705438] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=6865 PROTO=2 
[ 2495.448105] wlan0: no IPv6 routers present
[ 2495.796170] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55934 PROTO=2 
[ 2496.102229] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=51442 PROTO=2 
[ 2511.769503] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55935 PROTO=2 
[ 2512.076737] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=39808 PROTO=2 
[ 2527.846486] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55936 PROTO=2 
[ 2543.820885] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55937 PROTO=2 
[ 2543.923407] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=55181 PROTO=2 
[ 2559.897797] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55938 PROTO=2 
[ 2560.307488] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=61438 PROTO=2 
[ 2569.933128] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55939 PROTO=2 
[ 2570.342999] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=480 PROTO=2 
[ 2635.059950] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55940 PROTO=2 
[ 2635.162249] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=26365 PROTO=2 
[ 2700.084297] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55941 PROTO=2 
[ 2700.186734] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=20233 PROTO=2 
[ 2830.235581] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55943 PROTO=2 
[ 2830.542774] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=15566 PROTO=2 
[ 2960.386717] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55945 PROTO=2 
[ 2960.591595] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=6839 PROTO=2 
[ 3025.411133] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55946 PROTO=2 
[ 3025.615985] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=44357 PROTO=2 
[ 3090.537964] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55947 PROTO=2 
[ 3090.845288] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:f8:1e:df:e0:6e:97:08:00 SRC=192.168.100.27 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=6232 PROTO=2 
[ 3155.562464] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55948 PROTO=2 
[ 3181.482776] wlan0: deauthenticating from 00:0c:c3:7c:75:04 by local choice (reason=3)
[ 6271.348892] wlan0: authenticate with 00:0c:c3:7c:75:04 (try 1)
[ 6271.350735] wlan0: authenticated
[ 6271.352100] wlan0: associate with 00:0c:c3:7c:75:04 (try 1)
[ 6271.355999] wlan0: RX ReassocResp from 00:0c:c3:7c:75:04 (capab=0x411 status=0 aid=1)
[ 6271.356067] wlan0: associated
[ 6275.307337] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55996 PROTO=2 
[ 6282.704096] wlan0: no IPv6 routers present
[ 6291.378315] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55997 PROTO=2 
[ 6307.455296] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55998 PROTO=2 
[ 6323.429548] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=55999 PROTO=2 
[ 6325.215923] wlan0: deauthenticating from 00:0c:c3:7c:75:04 by local choice (reason=3)
[ 6326.337679] wlan0: authenticate with 00:0c:c3:7c:75:04 (try 1)
[ 6326.339477] wlan0: authenticated
[ 6326.340183] wlan0: associate with 00:0c:c3:7c:75:04 (try 1)
[ 6326.344105] wlan0: RX ReassocResp from 00:0c:c3:7c:75:04 (capab=0x411 status=0 aid=1)
[ 6326.344136] wlan0: associated
[ 6330.358143] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56000 PROTO=2 
[ 6337.731204] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56001 PROTO=2 
[ 6337.776118] wlan0: no IPv6 routers present
[ 6353.842602] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56002 PROTO=2 
[ 6369.817072] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56003 PROTO=2 
[ 6385.893943] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56004 PROTO=2 
[ 6401.868486] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56005 PROTO=2 
[ 6412.006089] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56006 PROTO=2 
[ 6456.668269] wlan0: deauthenticating from 00:0c:c3:7c:75:04 by local choice (reason=3)
[ 6820.918688] wlan0: authenticate with 00:0c:c3:7c:75:04 (try 1)
[ 6820.920641] wlan0: authenticated
[ 6820.921645] wlan0: associate with 00:0c:c3:7c:75:04 (try 1)
[ 6820.925687] wlan0: RX ReassocResp from 00:0c:c3:7c:75:04 (capab=0x11 status=0 aid=2)
[ 6820.925700] wlan0: associated
[ 6824.606287] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56013 PROTO=2 
[ 6831.520085] wlan0: no IPv6 routers present
[ 6833.078892] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56014 PROTO=2 
[ 6865.129262] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56016 PROTO=2 
[ 6897.180555] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56018 PROTO=2 
[ 6907.215899] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56019 PROTO=2 
[ 6972.342526] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56020 PROTO=2 
[ 6992.617848] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56021 PROTO=2 
[ 7057.744743] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56022 PROTO=2 
[ 7122.769432] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56023 PROTO=2 
[ 7187.895898] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56024 PROTO=2 
[ 7252.920671] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56025 PROTO=2 
[ 7318.047344] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56026 PROTO=2 
[ 7383.071785] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56027 PROTO=2 
[ 7448.198469] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56028 PROTO=2 
[ 7513.223782] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56029 PROTO=2 
[ 7643.374342] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56031 PROTO=2 
[ 7708.501751] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56032 PROTO=2 
[ 7773.525338] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56033 PROTO=2 
[ 7838.652321] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56034 PROTO=2 
[ 7903.676689] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56035 PROTO=2 
[ 7968.803528] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56036 PROTO=2 
[ 8033.828133] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56037 PROTO=2 
[ 8098.955020] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56038 PROTO=2 
[ 8229.003780] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56040 PROTO=2 
[ 8294.130516] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56041 PROTO=2 
[ 8359.155111] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56042 PROTO=2 
[ 8424.282764] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56043 PROTO=2 
[ 8462.135738] wlan0: deauthenticating from 00:0c:c3:7c:75:04 by local choice (reason=3)
[11174.085128] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11190.145071] wlan0: authenticate with 00:0c:c3:7c:75:04 (try 1)
[11190.147147] wlan0: authenticated
[11190.147865] wlan0: associate with 00:0c:c3:7c:75:04 (try 1)
[11190.151911] wlan0: RX AssocResp from 00:0c:c3:7c:75:04 (capab=0x11 status=0 aid=2)
[11190.151924] wlan0: associated
[11190.163222] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11193.718983] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56137 PROTO=2 
[11197.762520] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56138 PROTO=2 
[11198.694977] wlan0: deauthenticating from 00:0c:c3:7c:75:04 by local choice (reason=3)
[12852.140731] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12872.330892] wlan0: authenticate with 00:0c:c3:7c:75:04 (try 1)
[12872.333373] wlan0: authenticated
[12872.334477] wlan0: associate with 00:0c:c3:7c:75:04 (try 1)
[12872.338409] wlan0: RX AssocResp from 00:0c:c3:7c:75:04 (capab=0x411 status=0 aid=1)
[12872.338421] wlan0: associated
[12872.349831] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12875.862431] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56726 PROTO=2 
[12880.962212] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56727 PROTO=2 
[12884.088058] wlan0: no IPv6 routers present
[12896.981242] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56728 PROTO=2 
[12913.007037] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56729 PROTO=2 
[12923.096108] wlan0: deauthenticating from 00:0c:c3:7c:75:04 by local choice (reason=3)
[12928.753886] wlan0: authenticate with 00:0c:c3:7c:75:04 (try 1)
[12928.756493] wlan0: authenticated
[12928.757896] wlan0: associate with 00:0c:c3:7c:75:04 (try 1)
[12928.761877] wlan0: RX ReassocResp from 00:0c:c3:7c:75:04 (capab=0x411 status=0 aid=1)
[12928.761888] wlan0: associated
[12931.782223] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56731 PROTO=2 
[12934.146136] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56732 PROTO=2 
[12939.808133] wlan0: no IPv6 routers present
[12950.163576] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56733 PROTO=2 
[12966.189301] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56734 PROTO=2 
[12982.214939] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56735 PROTO=2 
[12998.240731] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56736 PROTO=2 
[13008.298658] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56737 PROTO=2 
[13073.364590] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56738 PROTO=2 
[13203.511981] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56740 PROTO=2 
[13268.585797] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56741 PROTO=2 
[13333.659485] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56742 PROTO=2 
[13398.733356] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56743 PROTO=2 
[13463.807676] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56744 PROTO=2 
[13528.881130] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56745 PROTO=2 
[13593.954883] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56746 PROTO=2 
[13659.028511] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56747 PROTO=2 
[13724.104581] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56748 PROTO=2 
[13789.175832] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56749 PROTO=2 
[13854.249839] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=56750 PROTO=2 
[13900.163789] wlan0: deauthenticating from 00:0c:c3:7c:75:04 by local choice (reason=3)
[13913.917333] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[20671.096989] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[23387.915063] wlan0: authenticate with 00:0c:c3:7c:75:04 (try 1)
[23387.917785] wlan0: authenticated
[23387.918980] wlan0: associate with 00:0c:c3:7c:75:04 (try 1)
[23387.922867] wlan0: RX AssocResp from 00:0c:c3:7c:75:04 (capab=0x411 status=0 aid=1)
[23387.922880] wlan0: associated
[23387.936378] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[23390.640346] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57493 PROTO=2 
[23398.502516] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57494 PROTO=2 
[23398.832073] wlan0: no IPv6 routers present
[23414.525856] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57495 PROTO=2 
[23430.547256] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57496 PROTO=2 
[23446.572901] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57497 PROTO=2 
[23462.598572] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57498 PROTO=2 
[23472.653134] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57499 PROTO=2 
[23537.722124] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57500 PROTO=2 
[23602.795710] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57501 PROTO=2 
[23667.869718] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57502 PROTO=2 
[23732.942962] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57503 PROTO=2 
[23798.016647] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57504 PROTO=2 
[23863.090264] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57505 PROTO=2 
[23928.184074] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57506 PROTO=2 
[23993.277592] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:0c:c3:7c:75:03:08:00 SRC=192.168.100.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0xC0 TTL=1 ID=57507 PROTO=2 
```


```
acer_wmi               23612  0 
arc4                   12473  2 
binfmt_misc            17292  1 
bluetooth             158438  10 rfcomm,bnep
bnep                   17830  2 
cfg80211              178679  2 iwlwifi,mac80211
drm                   197692  3 i915,drm_kms_helper
drm_kms_helper         45466  1 i915
i2c_algo_bit           13199  1 i915
i915                  414568  2 
ip6table_filter        12711  1 
ip6_tables             22528  3 ip6t_LOG,ip6t_rt,ip6table_filter
ip6t_LOG               16846  4 
ip6t_rt                12473  3 
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
ipt_LOG                12783  5 
ipt_REJECT             12512  1 
iwlwifi               287751  0 
joydev                 17393  0 
lp                     17455  0 
mac80211              436455  1 iwlwifi
mac_hid                13077  0 
Module                  Size  Used by
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_conntrack_ipv6      13581  7 
nf_conntrack_netbios_ns    12585  0 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
nf_nat                 24959  1 nf_nat_ftp
nf_nat_ftp             12595  0 
parport                40930  3 parport_pc,ppdev,lp
parport_pc             32114  0 
ppdev                  12849  0 
psmouse                87213  0 
r8169                  56321  0 
rfcomm                 38139  0 
rts_pstor             353215  0 
serio_raw              13027  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec_realtek   174055  1 
snd_hda_intel          32765  3 
snd_hwdep              13276  1 snd_hda_codec
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25424  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28931  2 snd_pcm,snd_seq
soundcore              14635  1 snd
sparse_keymap          13658  1 acer_wmi
uas                    17699  0 
usb_storage            39646  0 
uvcvideo               67203  0 
video                  19068  1 i915
videodev               86588  1 uvcvideo
wmi                    18744  1 acer_wmi
x_tables               21974  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
xt_addrtype            12596  4 
xt_hl                  12465  6 
xt_limit               12541  12 
xt_state               12514  14 
xt_tcpudp              12531  23 

```

---

### Post by chamber on 2012-05-25
Can you set IPv6 to ignore.

Go to your network connections and click edit connections, go to wireless, select your ssid and click edit. In IPv4 settings add 8.8.8.8 and 8.8.4.4 in the DNS Servers field, move to IPv6 settings and select the method to be ignore.


[[img]http://ompldr.org/tZHdxNg[/img]](http://ompldr.org/vZHdxNg)

---

### Post by jojo4349 on 2012-05-25
Hi, I have done as you said, but it hasn't worked.  
I have attached a screen shot, just in case it helps. 


[ATTACH]218690[/ATTACH]


Thanks

---

### Post by steeldriver on 2012-05-25
Have you tried

```
Automatic (DHCP)
```instead of 

```
Automatic (DHCP) addresses only
```

---

### Post by jojo4349 on 2012-05-26
The original setting was as 'automatic DHCP' and the only way I could change the DNS settings to 8.8.8.8 and 8.8.4.4 was to change to automatic DCHP addresses only.  

There are also these options - 
Automatic (DHCP)
Automatic (DHCP) Addresses only
Manual
Link-local
Share to other computers
Disable

Is there anything I can do with those? 
Thanks!

---

### Post by steeldriver on 2012-05-26
^^^ unfortunately that's getting into the territory of dnsmasq which I know nothing about (I'm still on 11.10 - which uses a conventional upstream DNS server model)

you could at least try 

```
sudo service dnsmasq status
```and then```
nm-tool
```to check that it's running and picking up your chosen server(s), and maybe

```
grep -i dns /var/log/dmesg
```to see if there are any obvious error messages? (I see a lot of blocked multicast packets but I have no idea if that means anything).

Good luck

---

### Post by jojo4349 on 2012-07-24
Hello, 

Sorry for the long absence. I hope I can still bother people with my problem as I am still in the same situation :) 

For sudo service dnsmasq status
```
joanne@joanne-AOD257:~$ sudo service dnsmasq status
[sudo] password for joanne: 
dnsmasq: unrecognized service

```


For nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: easytether0 ----------------------------------------------------------
  Type:              Wired
  Driver:            easytether
  State:             disconnected
  Default:           no
  HW Address:        62:FF:A9:1C:3A:A2

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0  [Auto ElisaKoti91] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        78:92:9C:18:1E:74

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Elisa-8e30:      Infra, 00:0C:C3:A2:8E:32, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    linksys:         Infra, 68:7F:74:2B:D0:1A, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    Elisa-7EA0:      Infra, 00:0C:C3:4D:7E:A2, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    *ElisaKoti91:    Infra, 00:0C:C3:7C:75:04, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA
    Elisa-eec0:      Infra, 00:0C:C3:C1:EE:C2, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Apple Network d6f93f: Infra, 90:84:0D:D6:F9:3F, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Elisa-b440:      Infra, 00:0C:C3:CE:B4:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ZyXEL:           Infra, 00:13:49:46:BC:09, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    Elisa-55e0:      Infra, 00:0C:C3:CA:55:E2, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Elisa-75d0:      Infra, 00:0C:C3:A2:75:D2, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2

  IPv4 Settings:
    Address:         192.168.100.40
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1

    DNS:             192.168.100.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E8:9A:8F:81:51:64

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

For grep -i dns /var/log/dmesg

```
joanne@joanne-AOD257:~$ grep -i dns /var/log/dmesg
[    1.954701] Registering the dns_resolver key type

```

---

### Post by jojo4349 on 2012-07-24
Hello, 

Sorry for the long absence. I hope I can still bother people with my problem as I am still in the same situation :) 

For sudo service dnsmasq status
```
joanne@joanne-AOD257:~$ sudo service dnsmasq status
[sudo] password for joanne: 
dnsmasq: unrecognized service

```For nm-tool
```
NetworkManager Tool

State: connected (global)

- Device: easytether0 ----------------------------------------------------------
  Type:              Wired
  Driver:            easytether
  State:             disconnected
  Default:           no
  HW Address:        62:FF:A9:1C:3A:A2

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         on


- Device: wlan0  [Auto ElisaKoti91] --------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        78:92:9C:18:1E:74

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Elisa-8e30:      Infra, 00:0C:C3:A2:8E:32, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    linksys:         Infra, 68:7F:74:2B:D0:1A, Freq 2462 MHz, Rate 54 Mb/s, Strength 27
    Elisa-7EA0:      Infra, 00:0C:C3:4D:7E:A2, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    *ElisaKoti91:    Infra, 00:0C:C3:7C:75:04, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA
    Elisa-eec0:      Infra, 00:0C:C3:C1:EE:C2, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    Apple Network d6f93f: Infra, 90:84:0D:D6:F9:3F, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Elisa-b440:      Infra, 00:0C:C3:CE:B4:42, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ZyXEL:           Infra, 00:13:49:46:BC:09, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA
    Elisa-55e0:      Infra, 00:0C:C3:CA:55:E2, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Elisa-75d0:      Infra, 00:0C:C3:A2:75:D2, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2

  IPv4 Settings:
    Address:         192.168.100.40
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.1

    DNS:             192.168.100.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        E8:9A:8F:81:51:64

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```For grep -i dns /var/log/dmesg

```
joanne@joanne-AOD257:~$ grep -i dns /var/log/dmesg
[    1.954701] Registering the dns_resolver key type

```
I hope this makes sense to someone :confused:
- Thanks

---

