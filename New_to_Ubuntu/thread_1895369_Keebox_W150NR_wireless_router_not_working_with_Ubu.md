---
title: "Keebox W150NR wireless router not working with Ubuntu 11.10"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by rajaMTM@gmail.com on 2011-12-14
[B]Problem Description:
[/B]I have a 64 bit Ubuntu 11.04 on my new laptop. I am a newbie to Linux,  heard a lot about its power but never experienced and wanted to  experience that. But for some reason i am not able to connect wirelessly  to my router. Net is working fine when I connect my laptop to my  wireless router through a cable. But when i try wireless, my network  adapter is able to see the wireless network, it tries to connect and  shows me a success msg that connection is established, but when I open  any webpage it says 'Page cannot be displayed'.

I was unable to find any possible solution for this issue across various  forums/google but could not find any. The same works fine with my  Windows 7 OS. This is the link to keebox product [http://www.keebox.com/products/produ..._W150NR&cat=66]("http://www.keebox.com/products/productdetail.asp?prod=100_W150NR&cat=66")

I checked with Keebox in case i need to install any driver and below is their response.
"Dear Customer, 

 We only provide TCP/IP support for Linux.  However, the router does not  require or need any specific drivers or use  any drivers. Your network  adapter should be able to see the routers  wireless network SSID  broadcast. Check to make sure that you are  broadcasting the SSID in a  mixed b/g/n mode unless your adapters N  capable. Try connecting your  wireless network adapter to the router with  an unsecured connection."

If any of you could solve this problem, I will be motivated to explore  more on Linux. Let me know if you need any other configuration details.  Thanks in advance.

Below are the details of my laptop in the format recommended by the help forums for detailing on wireless related issues.
[B]
1) Machine Brand and Model (Laptop)[/B]: Dell Inspiron 15R
[B]2) Wireless Brand, Model and Wireless Chipset:
[/B]$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core  Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
0b:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)


$ lsusb

Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0c45:6485 Microdia 
Bus 001 Device 004: ID 8086:0189 Intel Corp. 
Bus 001 Device 003: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[B]3 ) check interface:

[/B]ifconfig
eth0      Link encap:Ethernet  HWaddr 18:03:73:52:cd:62  
          inet addr:192.168.10.105  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::1a03:73ff:fe52:cd62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:557094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:284657 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:838969862 (838.9 MB)  TX bytes:19705374 (19.7 MB)
          Interrupt:45 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

wlan0     Link encap:Ethernet  HWaddr bc:77:37:9b:57:bc  
          inet addr:192.168.10.102  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::be77:37ff:fe9b:57bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3560 (3.5 KB)  TX bytes:12165 (12.1 KB)


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"RAJini"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:14:grin:1:7C:FD:E0   
          Bit Rate=5.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:eek:ff   Fragment thr:eek:ff
          Power Management:eek:n
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

[B]4 ) Check for modules:

[/B]lsmod:

Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   21708  1 
fat                    61374  1 vfat
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
rfcomm                 47694  0 
binfmt_misc            17565  1 
sco                    18187  0 
bnep                   18308  0 
l2cap                  53570  4 rfcomm,bnep
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_idt      71137  1 
arc4                   12529  2 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
iwlagn                333716  0 
i915                  515121  3 
snd_rawmidi            30486  1 snd_seq_midi
uvcvideo               72195  0 
iwlcore               167502  1 iwlagn
dell_wmi               12681  0 
btusb                  18600  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
videodev               82052  1 uvcvideo
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop
sparse_keymap          13898  1 dell_wmi
bluetooth              72320  5 rfcomm,sco,bnep,l2cap,btusb
drm_kms_helper         42136  1 i915
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
serio_raw              13166  0 
mac80211              294370  2 iwlagn,iwlcore
drm                   227534  4 i915,drm_kms_helper
i2c_algo_bit           13400  1 i915
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178528  3 iwlagn,iwlcore,mac80211
snd                    67382  14  snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel   ,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_s   eq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  4 
libahci                26642  1 ahci
r8169                  48022  0 
xhci_hcd               77643  0 

[B]5 ) Kernel boot messages
[/B]dmesg | grep "wlan"

[   19.260409] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.283811] wlan0: authenticate with 00:14:d1:7c:fd:e0 (try 1)
[   28.294506] wlan0: authenticated
[   28.298048] wlan0: associate with 00:14:d1:7c:fd:e0 (try 1)
[   28.303855] wlan0: RX AssocResp from 00:14:d1:7c:fd:e0 (capab=0xc11 status=0 aid=1)
[   28.303860] wlan0: associated
[   28.311560] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.429395] wlan0: no IPv6 routers present

**6 ) Network configuration**
sudo lshw -C network
[sudo] password for raginiraja: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 05
       serial: 18:03:73:52:cd:62
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.10.105 latency=0  link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:e000(size=256) memory:f1104000-f1104fff memory:f1100000-f1103fff
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 34
       serial: bc:77:37:9b:57:bc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn  driverversion=2.6.38-11-generic firmware=17.168.5.2 build 35905  ip=192.168.10.102 latency=0 link=yes multicast=yes wireless=IEEE  802.11bgn
       resources: irq:52 memory:f7e00000-f7e01fff

[B]7 ) Scan for networks:
[/B]iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:14:grin:1:7C:FD:E0
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:eek:n
                    ESSID:"RAJini"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000024ad825b18b
                    Extra: Last beacon: 8480ms ago
                    IE: Unknown: 000652414A696E69
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030104
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FF000000010000000000000000000000000C0000  000000
                    IE: Unknown: 3D1604050400000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F  00
                    IE: Unknown: 0B0500001B127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FF000000010000000000000000000000  000C0000000000
                    IE: Unknown: DD1A00904C3404050400000000000000000000000000000000  000000
                    IE: Unknown: DD050050F20500
                    IE: Unknown:  DD720050F204104A00011010440001011041000100103B0001   0310470010C74A3DF12029FD5C20FD0014D17CFDE110210006   4B4545424F5810230006573135304E5210240006573135304E   521042000830303030303030301054000800060050F2040001   10110006573135304E52100800020086

[B]8 ) Ubuntu Version:
[/B]Description:    Ubuntu 11.10[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]3.0.0-14-generic x86_64[B]10 ) Restarting the network:

 [/B]* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                           [  OK ]

---

