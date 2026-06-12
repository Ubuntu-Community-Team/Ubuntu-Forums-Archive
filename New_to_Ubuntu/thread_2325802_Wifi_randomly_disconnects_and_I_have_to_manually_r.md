---
title: "Wifi randomly disconnects and I have to manually reconnect it"
date: 2016-05-25
forum: New to Ubuntu
---

### Post by Rokas_Jonushas on 2016-05-25
So recently I have downgraded from 16.04 to 14.04 due to steam not working with some games and now I seem to have a problem with the WIFI, I use a wireless adapter and have a desktop PC

I have a copy of my wireless info here below


```
########## wireless info START ##########

Report from: 25 May 2016 16:59 IST +0100

Booted last: 25 May 2016 16:39 IST +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-60-generic #67~14.04.1-Ubuntu SMP Wed May 18 17:22:23 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 002 Device 006: ID 060b:8003 Solid Year 
Bus 002 Device 005: ID 145f:01ac Trust 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 003: ID 1a2c:4e2f China Resource Semico Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              69632  0 
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                73728  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              720896  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              532480  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18121140 (18.1 MB)  TX bytes:1353352 (1.3 MB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"eircom06110556"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'eircom06110556' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1000     1  0 16:39 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1  [eircom06110556] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *eircom06110556: Infra, <MAC 'eircom06110556' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.1
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/eircom06110556]] (600 root)
[connection] id=eircom06110556 | type=802-11-wireless
[802-11-wireless] ssid=eircom06110556 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Dublin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

wlan1     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'eircom06110556' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"eircom06110556"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c0e2392990
                    Extra: Last beacon: 80ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.19.0-60-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     6ACA0A2E14F5D60DF6DBD99
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.19.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BC:18:1F:61:FD:59:33:15:F9:91:F4:48:25:41:73:F4:A4:ED:E3:71
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.19.0-60-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D999E42F5A856FDC2499003
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.19.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BC:18:1F:61:FD:59:33:15:F9:91:F4:48:25:41:73:F4:A4:ED:E3:71
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.19.0-60-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     134BAE300AAF914967D6C6C
depends:        rtlwifi
intree:         Y
vermagic:       3.19.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BC:18:1F:61:FD:59:33:15:F9:91:F4:48:25:41:73:F4:A4:ED:E3:71
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-60-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BC:18:1F:61:FD:59:33:15:F9:91:F4:48:25:41:73:F4:A4:ED:E3:71
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-60-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A1851295567B306D1C939BC
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BC:18:1F:61:FD:59:33:15:F9:91:F4:48:25:41:73:F4:A4:ED:E3:71
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-60-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     381EA511B7BC282E4E24C0E
depends:        
intree:         Y
vermagic:       3.19.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BC:18:1F:61:FD:59:33:15:F9:91:F4:48:25:41:73:F4:A4:ED:E3:71
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wifi_pwr_off] (755 root)
    #!/bin/sh 
    /sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   13.140470] rtl8192cu: Board Type 0
[   13.140713] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   13.140736] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   13.144230] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.145325] rtl8192cu 1-1.2:1.0 wlan1: renamed from wlan0
[   13.156454] systemd-udevd[315]: renamed network interface wlan0 to wlan1
[   18.725212] rtl8192cu: MAC auto ON okay!
[   18.758235] rtl8192cu: Tx queue select: 0x05
[   19.180669] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   20.725687] wlan1: authenticate with <MAC 'eircom06110556' [AC1]>
[   20.749474] wlan1: send auth to <MAC 'eircom06110556' [AC1]> (try 1/3)
[   20.764134] wlan1: authenticated
[   20.765348] wlan1: associate with <MAC 'eircom06110556' [AC1]> (try 1/3)
[   20.780775] wlan1: RX AssocResp from <MAC 'eircom06110556' [AC1]> (capab=0x411 status=0 aid=3)
[   20.781899] wlan1: associated
[   20.781912] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   20.832712] wlan1: deauthenticating from <MAC 'eircom06110556' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   20.845176] wlan1: authenticate with <MAC 'eircom06110556' [AC1]>
[   20.856787] wlan1: send auth to <MAC 'eircom06110556' [AC1]> (try 1/3)
[   20.858789] wlan1: authenticated
[   20.861411] wlan1: associate with <MAC 'eircom06110556' [AC1]> (try 1/3)
[   20.871580] wlan1: RX AssocResp from <MAC 'eircom06110556' [AC1]> (capab=0x411 status=0 aid=3)
[   20.872719] wlan1: associated
[  644.246821] wlan1: deauthenticating from <MAC 'eircom06110556' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  645.033690] wlan1: authenticate with <MAC 'eircom06110556' [AC1]>
[  645.058237] wlan1: send auth to <MAC 'eircom06110556' [AC1]> (try 1/3)
[  645.065088] wlan1: authenticated
[  645.069300] wlan1: associate with <MAC 'eircom06110556' [AC1]> (try 1/3)
[  645.091604] wlan1: RX AssocResp from <MAC 'eircom06110556' [AC1]> (capab=0x411 status=0 aid=3)
[  645.092335] wlan1: associated
[ 1092.920404] wlan1: deauthenticating from <MAC 'eircom06110556' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1093.691411] wlan1: authenticate with <MAC 'eircom06110556' [AC1]>
[ 1093.715117] wlan1: send auth to <MAC 'eircom06110556' [AC1]> (try 1/3)
[ 1093.718465] wlan1: authenticated
[ 1093.719093] wlan1: associate with <MAC 'eircom06110556' [AC1]> (try 1/3)
[ 1093.733866] wlan1: RX AssocResp from <MAC 'eircom06110556' [AC1]> (capab=0x411 status=0 aid=3)
[ 1093.734817] wlan1: associated

########## wireless info END ############
```

---

### Post by wildmanne39 on 2016-05-25
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by wildmanne39 on 2016-05-25
That driver needs to be updated, please do by copying and pasting one line at a time.
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential git dkms
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.10
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by Rokas_Jonushas on 2016-05-25
I have done what you said and now it doesn't detect the WiFi adapter anymore

---

### Post by wildmanne39 on 2016-05-25
Run the wireless script again and post the new file created and we can take a look.
Were there any errors when you ran the commands?

---

### Post by Rokas_Jonushas on 2016-05-25
Yeah it said some files weren't recognised retrying the code  now

---

### Post by Rokas_Jonushas on 2016-05-25
Since most of these were already installed it should that they already exsist but here is the code anyway

```
ubus@ubus-desktop:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential git dkms
[sudo] password for ubus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-x
  libatk-bridge2.0-0:i386 libatk1.0-0:i386 libatspi2.0-0:i386
  libcairo-gobject2:i386 libcairo2:i386 libcolord1:i386 libdatrie1:i386
  libechonest2.1 libftgl2 libgdk-pixbuf2.0-0:i386 libgpod-common libgpod4
  libgraphite2-3:i386 libgsm1:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer1.0-0:i386 libgtk-3-0:i386 libharfbuzz0b:i386 libjasper1:i386
  liblastfm1 libodbc1:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpcap0.8:i386 libpixman-1-0:i386 libprojectm2
  libqjson0 libqxt-core0 libqxt-gui0 libsgutils2-2 libsidplay1 libthai0:i386
  libva-drm1 libva-drm1:i386 libva-x11-1:i386 libva1:i386
  libwayland-client0:i386 libwayland-cursor0:i386 libxcb-render0:i386
  libxcb-shm0:i386 libxkbcommon0:i386 projectm-data wine-staging
  wine-staging-amd64 wine-staging-i386:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 5 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/3,412 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 248782 files and directories currently installed.)
Preparing to unpack .../build-essential_11.6ubuntu6_amd64.deb ...
Unpacking build-essential (11.6ubuntu6) over (11.6ubuntu6) ...
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.5_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.5) over (2.2.0.3-1.1ubuntu5.14.04.5) ...
Preparing to unpack .../git_1%3a1.9.1-1ubuntu0.3_amd64.deb ...
Unpacking git (1:1.9.1-1ubuntu0.3) over (1:1.9.1-1ubuntu0.3) ...
Preparing to unpack .../linux-headers-3.19.0-60-generic_3.19.0-60.67~14.04.1_amd64.deb ...
Unpacking linux-headers-3.19.0-60-generic (3.19.0-60.67~14.04.1) over (3.19.0-60.67~14.04.1) ...
Preparing to unpack .../linux-headers-generic_3.13.0.87.93_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.87.93) over (3.13.0.87.93) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up build-essential (11.6ubuntu6) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.5) ...
Setting up git (1:1.9.1-1ubuntu0.3) ...
Setting up linux-headers-3.19.0-60-generic (3.19.0-60.67~14.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.19.0-60-generic /boot/vmlinuz-3.19.0-60-generic
Setting up linux-headers-generic (3.13.0.87.93) ...
Processing triggers for initramfs-tools (0.103ubuntu4.3) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-60-generic
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'getdeb.list.bck' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
ubus@ubus-desktop:~$ git clone https://github.com/pvaret/rtl8192cu-fixes.git
fatal: destination path 'rtl8192cu-fixes' already exists and is not an empty directory.
ubus@ubus-desktop:~$ sudo dkms add ./rtl8192cu-fixes
Error! DKMS tree already contains: 8192cu-1.10
You cannot add the same module/version combo more than once.
ubus@ubus-desktop:~$ sudo dkms install 8192cu/1.9
Error! Could not find module source directory.
Directory: /usr/src/8192cu-1.9 does not exist.
ubus@ubus-desktop:~$ echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist rtl8192cu
ubus@ubus-desktop:~$ 

```

---

### Post by wildmanne39 on 2016-05-25
Did you manually install this driver before? Please post a new file from running the wireless script again so we can see what is going on.
Thanks

---

### Post by Rokas_Jonushas on 2016-05-25
No I just hooked up an ethernet cable to my pc I didnt copy the terminal when i originally ran the code would there be any way to delete all the drivers and reinstall them or?

---

### Post by wildmanne39 on 2016-05-25
New file from script please.

---

### Post by Rokas_Jonushas on 2016-05-25
How do you do that? sorry im kinda new to ubuntu

---

### Post by wildmanne39 on 2016-05-25
You posted the wireless info file in the first post just run the script again, and it will create a new file for you to post.

---

### Post by Rokas_Jonushas on 2016-05-25
Yeah I realised sorry XD here you go

```


########## wireless info START ##########

Report from: 25 May 2016 18:52 IST +0100

Booted last: 25 May 2016 18:00 IST +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-60-generic #67~14.04.1-Ubuntu SMP Wed May 18 17:22:23 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Foxconn International, Inc. Device [105b:0dcc]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 006: ID 060b:8003 Solid Year 
Bus 002 Device 005: ID 145f:01ac Trust 
Bus 002 Device 004: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 003: ID 1a2c:4e2f China Resource Semico Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              532480  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.59  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:350572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:501833905 (501.8 MB)  TX bytes:15946451 (15.9 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       959     1  0 18:00 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.59
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/eircom06110556]] (600 root)
[connection] id=eircom06110556 | type=802-11-wireless
[802-11-wireless] ssid=eircom06110556 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Dublin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.19.0-60-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     381EA511B7BC282E4E24C0E
depends:        
intree:         Y
vermagic:       3.19.0-60-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        BC:18:1F:61:FD:59:33:15:F9:91:F4:48:25:41:73:F4:A4:ED:E3:71
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
blacklist rtl8192cu
blacklist rtl8192cu

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/wifi_pwr_off] (755 root)
    #!/bin/sh 
    /sbin/iwconfig wlan0 power off

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[   19.403752] r8169 0000:02:00.0 eth0: link down (repeated 2 times)
[   19.403800] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.186515] r8169 0000:02:00.0 eth0: link up
[   22.186530] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  997.844025] r8169 0000:02:00.0 eth0: link down
[ 1001.110388] r8169 0000:02:00.0 eth0: link up
[ 1004.472689] r8169 0000:02:00.0 eth0: link down
[ 1018.895981] r8169 0000:02:00.0 eth0: link up

########## wireless info END ############


```

---

### Post by wildmanne39 on 2016-05-25
Did you change the name from 8192cu/1.9 to 8192cu-1.10? 
Thanks

---

### Post by Rokas_Jonushas on 2016-05-25
I probably didn't cause I just copied the code you sent me

---

### Post by wildmanne39 on 2016-05-25
Please do:
```
sudo dkms install 8192cu-1.10
```
Watch for error's.
Reboot

---

### Post by Rokas_Jonushas on 2016-05-25
Im gonna reboot now but here is the code

```

ubus@ubus-desktop:~$ sudo dkms install 8192cu-1.10
[sudo] password for ubus: 
Error! Invalid number of arguments passed.
Usage: add <module>/<module-version> or
       add -m <module>/<module-version> or
       add -m <module> -v <module-version>
ubus@ubus-desktop:~$ 


```

---

### Post by Rokas_Jonushas on 2016-05-25
I Put the code in rebooted everything is working fine im having a strong 4 bar signal

Thanks man will do some random internet testing and will get back to you if it messes up but ill mark this post as solved for the time being

---

### Post by wildmanne39 on 2016-05-25
I will cross my fingers for you.
Good Luck!

---

