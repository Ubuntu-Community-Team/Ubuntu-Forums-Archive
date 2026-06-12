---
title: "How to get my wireless modem working in precise 12.04"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by eshant_engineer on 2012-05-16
Hi,

I am strugling with my CDMA 2000 Modem. Please help me to get my modem supported in network Manager. Please find below logs generated:-

```
May 16 11:56:18 ebuntu-Inspiron-N5110 kernel: [ 1475.512423] usb 2-1.2: new full-speed USB device number 8 using ehci_hcd
May 16 11:56:18 ebuntu-Inspiron-N5110 [COLOR="Red"]kernel[/COLOR]: [ 1475.607702] cdc_acm 2-1.2:1.0: This device cannot do calls on its own. It is not a modem.   [COLOR="Red"]#Here saying not modem[/COLOR]
May 16 11:56:18 ebuntu-Inspiron-N5110 kernel: [ 1475.607754] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
May 16 11:56:18 ebuntu-Inspiron-N5110 mtp-probe: checking bus 2, device 8: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2"
May 16 11:56:18 ebuntu-Inspiron-N5110 kernel: [ 1475.609715] scsi10 : usb-storage 2-1.2:1.2
May 16 11:56:18 ebuntu-Inspiron-N5110 mtp-probe: bus: 2, device: 8 was not an MTP device
May 16 11:56:18 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  (ttyACM0) opening serial port...  
May 16 11:56:19 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  (ttyACM0) closing serial port...
May 16 11:56:19 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  (ttyACM0) serial port closed
May 16 11:56:19 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  (ttyACM0) opening serial port...
May 16 11:56:19 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  (Generic): CDMA modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2 claimed port ttyACM0
May 16 11:56:19 ebuntu-Inspiron-N5110 kernel: [ 1476.613365] scsi 10:0:0:0: CD-ROM            BSNL     Mass Storage CD  7.00 PQ: 0 ANSI: 2
May 16 11:56:19 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  (ttyACM0) closing serial port...
May 16 11:56:19 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  (ttyACM0) serial port closed
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: [COLOR="Red"]<warn> (ttyACM0): failed to look up interface index[/COLOR]
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): new CDMA/EVDO device (driver: 'cdc_acm' ifindex: 0)
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): exported as /org/freedesktop/NetworkManager/Devices/4
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): now managed
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 16 11:56:19 ebuntu-Inspiron-N5110 kernel: [ 1476.622099] scsi 10:0:0:1: Direct-Access     BSNL     Mass Storage SD  7.00 PQ: 0 ANSI: 0 CCS
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): deactivating device (reason 'managed') [2]
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
May 16 11:56:19 ebuntu-Inspiron-N5110 kernel: [ 1476.625429] sr1: scsi3-mmc drive: 0x/0x caddy
May 16 11:56:19 ebuntu-Inspiron-N5110 kernel: [ 1476.626186] sr 10:0:0:0: Attached scsi CD-ROM sr1
May 16 11:56:19 ebuntu-Inspiron-N5110 kernel: [ 1476.627716] sr 10:0:0:0: Attached scsi generic sg3 type 5
May 16 11:56:19 ebuntu-Inspiron-N5110 kernel: [ 1476.628331] sd 10:0:0:1: Attached scsi generic sg4 type 0
May 16 11:56:19 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): device state change: unavailable -> disconnected (reason 'none') [20 30 0]
May 16 11:56:19 ebuntu-Inspiron-N5110 kernel: [ 1476.656138] sd 10:0:0:1: [sdc] Attached SCSI removable disk
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> Activation (ttyACM0) starting connection 'BSNL connection' [COLOR="Red"]# Dialing for connection[/COLOR]
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): device state change: prepare -> need-auth (reason 'none') [40 60 0]
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
May 16 11:58:31 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  (ttyACM0) opening serial port...
May 16 11:58:31 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (disabled -> enabling)
May 16 11:58:31 ebuntu-Inspiron-N5110 modem-manager[1030]: <info>  Modem /org/freedesktop/ModemManager/Modems/2: state changed (enabling -> enabled)
May 16 11:58:31 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> WWAN now enabled by management service
May 16 11:59:32 ebuntu-Inspiron-N5110 NetworkManager[1138]: [COLOR="Red"]<warn> CDMA connection failed: (32) No service[/COLOR]
May 16 11:59:32 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): device state change: prepare -> failed (reason 'none') [40 120 0]
May 16 11:59:32 ebuntu-Inspiron-N5110 NetworkManager[1138]: <warn> Activation (ttyACM0) failed.
May 16 11:59:32 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 16 11:59:32 ebuntu-Inspiron-N5110 NetworkManager[1138]: <info> (ttyACM0): deactivating device (reason 'none') [0]
May 16 11:59:32 ebuntu-Inspiron-N5110 NetworkManager[1138]: nm_system_iface_flush_routes: assertion `ifindex > 0' failed
May 16 11:59:32 ebuntu-Inspiron-N5110 NetworkManager[1138]: nm_system_iface_flush_addresses: assertion `ifindex > 0' failed
l
```

Thanks for your time and reply...:)

---

### Post by ikt on 2012-05-16
What's the device name?

---

### Post by Lisiano on 2012-05-16
Please provide information for those that know about modems (I don't).
Connect the modem and run the following. (If it was connected, reconect the modem and wait for around 10 seconds, then run them)
```
uname -a
```
```
lspci
```
```
lsusb
```
```
dmesg | tail -n 50
```
```
lsmod | sort
```
Please use separate code tags for each command above.

---

### Post by eshant_engineer on 2012-05-16
This is new modem distributed by BSNL, India carrier manufactured by Prithvi solutions


uname -a:```
root@ebuntu-Inspiron-N5110:~# uname -a
Linux ebuntu-Inspiron-N5110 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```


lspci:
```
root@ebuntu-Inspiron-N5110:~# lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
0b:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

lsusb:
```
root@ebuntu-Inspiron-N5110:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 001 Device 003: ID 1bcf:2881 Sunplus Innovation Technology Inc. 
Bus 002 Device 007: ID 15eb:1231  
Bus 002 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. Card reader
Bus 001 Device 004: ID 8086:0189 Intel Corp. 
```


dmesg | tail -n 50:
```
root@ebuntu-Inspiron-N5110:~# dmesg | tail -n 50
[ 1911.331886] CPU3: Package power limit normal
[ 1911.331889] CPU0: Package power limit normal
[ 1911.331891] CPU1: Package power limit normal
[ 2345.857532] usb 3-1: new high-speed USB device number 3 using xhci_hcd
[ 2345.876887] usb 3-1: ep 0x81 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2345.876894] usb 3-1: ep 0x1 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2345.876899] usb 3-1: ep 0x83 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2345.876907] usb 3-1: ep 0x84 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2345.876911] usb 3-1: ep 0x3 - rounding interval to 32768 microframes, ep desc says 0 microframes
[ 2345.878588] cdc_acm 3-1:1.0: This device cannot do calls on its own. It is not a modem.
[ 2345.878643] cdc_acm 3-1:1.0: ttyACM1: USB ACM device
[ 2345.880261] scsi9 : usb-storage 3-1:1.2
[ 2346.879389] scsi 9:0:0:0: Direct-Access     Texas In struments Inc.OM AP4  PQ: 0 ANSI: 2
[ 2346.879872] scsi 9:0:0:1: Direct-Access     Texas In struments Inc.OM AP4  PQ: 0 ANSI: 2
[ 2346.880888] sd 9:0:0:0: Attached scsi generic sg5 type 0
[ 2346.881486] sd 9:0:0:1: Attached scsi generic sg6 type 0
[ 2346.886289] sd 9:0:0:0: [sdd] Attached SCSI removable disk
[ 2346.886491] sd 9:0:0:1: [sde] Attached SCSI removable disk
[ 8148.594392] keyboard: can't emulate rawmode for keycode 240
[ 8148.594417] keyboard: can't emulate rawmode for keycode 240
[ 8148.607341] iwlwifi 0000:09:00.0: RF_KILL bit toggled to enable radio.
[ 8148.846944] usb 1-1.4: new full-speed USB device number 4 using ehci_hcd
[ 8149.092591] Bluetooth: Generic Bluetooth USB driver ver 0.6
[ 8149.093889] usbcore: registered new interface driver btusb
[ 8149.827206] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[ 8149.833730] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[ 8149.919929] iwlwifi 0000:09:00.0: L1 Disabled; Enabling L0S
[ 8149.926447] iwlwifi 0000:09:00.0: Radio type=0x2-0x2-0x1
[ 8150.021837] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8151.632695] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[ 8151.632732] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[ 8151.632766] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[20350.344429] usb 3-1: USB disconnect, device number 3
[20373.179220] usb 3-2: USB disconnect, device number 2
[23955.093061] usb 3-2: new low-speed USB device number 4 using xhci_hcd
[23955.142790] usb 3-2: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[23955.155745] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1c.4/0000:0b:00.0/usb3/3-2/3-2:1.0/input/input18
[23955.156280] generic-usb 0003:046D:C05A.0002: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:0b:00.0-2/input0
[24134.359702] usb 2-1.2: USB disconnect, device number 6
[24139.962316] usb 2-1.2: new full-speed USB device number 7 using ehci_hcd
[24140.057100] cdc_acm 2-1.2:1.0: This device cannot do calls on its own. It is not a modem.
[24140.057155] cdc_acm 2-1.2:1.0: ttyACM0: USB ACM device
[24140.059034] scsi10 : usb-storage 2-1.2:1.2
[24141.059230] scsi 10:0:0:0: CD-ROM            BSNL     Mass Storage CD  7.00 PQ: 0 ANSI: 2
[24141.060350] scsi 10:0:0:1: Direct-Access     BSNL     Mass Storage SD  7.00 PQ: 0 ANSI: 0 CCS
[24141.064178] sr1: scsi3-mmc drive: 0x/0x caddy
[24141.064450] sr 10:0:0:0: Attached scsi CD-ROM sr1
[24141.064709] sr 10:0:0:0: Attached scsi generic sg3 type 5
[24141.065179] sd 10:0:0:1: Attached scsi generic sg4 type 0
[24141.081803] sd 10:0:0:1: [sdc] Attached SCSI removable disk
```


lsmod | sort:
```
root@ebuntu-Inspiron-N5110:~# lsmod | sort
arc4                   12529  2 
bluetooth             180104  23 btusb,rfcomm,bnep
bnep                   18281  2 
bsd_comp               12994  0 
btusb                  18288  2 
cdc_acm                26858  0 
cfg80211              205544  2 iwlwifi,mac80211
crc_ccitt              12667  1 ppp_async
dcdbas                 14490  1 dell_laptop
dell_laptop            18119  0 
dell_wmi               12681  0 
dm_crypt               23125  1 
drm                   242038  6 nouveau,ttm,i915,drm_kms_helper
drm_kms_helper         46978  2 nouveau,i915
hid                    99559  1 usbhid
i2c_algo_bit           13423  2 nouveau,i915
i915                  468651  3 
iwlwifi               328352  0 
joydev                 17693  0 
lp                     17799  0 
mac80211              506816  1 iwlwifi
mac_hid                13253  0 
mei                    41616  0 
Module                  Size  Used by
mxm_wmi                12979  1 nouveau
nouveau               774571  0 
parport                46562  3 parport_pc,ppdev,lp
parport_pc             32866  0 
ppdev                  17113  0 
ppp_async              17539  0 
ppp_deflate            13038  0 
psmouse                87603  0 
r8169                  62099  0 
rfcomm                 47604  12 
serio_raw              13211  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_hdmi     32474  4 
snd_hda_codec_idt      70795  1 
snd_hda_intel          33773  5 
snd_hwdep              13668  1 snd_hda_codec
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_timer              29990  2 snd_pcm,snd_seq
soundcore              15091  1 snd
sparse_keymap          13890  1 dell_wmi
ttm                    76949  1 nouveau
uas                    18027  0 
ums_realtek            18248  0 
usbhid                 47199  0 
usb_storage            49198  2 ums_realtek
uvcvideo               72627  0 
v4l2_compat_ioctl32    17128  1 videodev
video                  19596  2 nouveau,i915
videodev               98259  1 uvcvideo
wmi                    19256  2 dell_wmi,mxm_wmi
zlib_deflate           27139  1 ppp_deflate


```

---

### Post by eshant_engineer on 2012-05-17
I am proficient in c as well as shell scripting. Please let me know...what should I ask from vendor on the basis of which I can resolve this issue as I know Network Manager is open source.

Please also tell me how to compile and test...

Thanks a ton to reply...:)

---

### Post by eshant_engineer on 2012-05-17
Anybody, please tell what is the right place to discuss this problem?

---

### Post by westie457 on 2012-05-17
Does it have a network provider's sim card in it? 

If it has it should just work after setting it up through the 'Mobile Broadband' tab of Network Managers Edit Connections option. The detected defaults usually work.

---

### Post by eshant_engineer on 2012-05-18
Yes it has SIM card for authentication. But it doesn't work. If some one help me on my previous post, it can help me to solve the problem.

Thanks in advance...:)

---

