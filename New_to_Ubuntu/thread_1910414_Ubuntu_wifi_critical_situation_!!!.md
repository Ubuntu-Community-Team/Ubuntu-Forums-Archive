---
title: "Ubuntu wifi critical situation !!!"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by thelionphoenix on 2012-01-17
All my information is available below


============ lspci ============
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
    Kernel driver in use: i915
    Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
01:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
01:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
01:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
    Kernel driver in use: rtl819xSE
    Kernel modules: r8192se_pci
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Kernel driver in use: r8169
    Kernel modules: r8169
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

============ lsusb ============
Bus 002 Device 003: ID 0930:0508 Toshiba Corp. Integrated Bluetooth HCI
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:1804 Ricoh Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

============ lsmod ============
Module                  Size  Used by
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
arc4                    1153  2 
rfcomm                 33421  8 
binfmt_misc             6587  1 
ppdev                   5259  0 
sco                     7885  2 
bridge                 45582  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
joydev                  8708  0 
snd_hda_codec_intelhdmi    11622  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  282354  3 
uvcvideo               56990  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
btusb                  10925  2 
drm_kms_helper         29297  1 i915
sdhci_pci               5470  0 
snd                    54148  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162471  4 i915,drm_kms_helper
intel_agp              24177  2 i915
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
sdhci                  15462  1 sdhci_pci
serio_raw               3978  0 
led_class               2864  1 sdhci
r8192se_pci           446468  0 
video                  17375  1 i915
soundcore               6620  1 snd
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32008  4 
r8169                  33884  0 
mii                     4381  1 r8169

============ dmesg-firmware ============
[    9.018078] rtl819xSE 0000:02:00.0: firmware: requesting RTL8192SE/rtl8192sfw.bin

============ kernel version ============
2.6.32-21-generic

============ ifconfig ============
eth0      Link encap:Ethernet  HWaddr 00:23:54:fa:bc:47  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:33 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2180 (2.1 KB)  TX bytes:2180 (2.1 KB)

wlan0     Link encap:Ethernet  HWaddr 70:1a:04:f1:f5:da  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f80c8000-f80c8100 


============ iwconfig ============
wlan0     802.11bg  ESSID:"hello"  Nickname:"rtl8191SEVA2"
          Mode:Ad-Hoc  Frequency=2.457 GHz  Cell: 2A:92:01:BA:13:0B   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by thelionphoenix on 2012-01-17
Well, the problem is i cannot connect to the WIFI, though its being detected.

---

### Post by carl4926 on 2012-01-17
Did you try 11.10?
It should work from the Live CD

Might be time to upgrade

Though it should work with your current install.

Install rfkill
And check if it's being blocked

```
sudo rfkill list
```

---

