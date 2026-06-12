---
title: "Connected to wi-fi, but no internet access"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by greenpy on 2013-06-01
Hi, relatively new to Ubuntu. It's been working fine, but recently had this problem. I've checked other threads but their solutions didn't work on mine.

Distro is 12.04 LTS on a Dell Inspiron 1525.

Some information from the terminal:

```
alexander@buffalo-buffalo:~$ netstat -rnKernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
alexander@buffalo-buffalo:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux buffalo-buffalo 3.5.0-31-generic #52~precise1-Ubuntu SMP Fri May 17 15:27:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
alexander@buffalo-buffalo:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 12)
    Subsystem: Dell Device [1028:022f]
    Kernel driver in use: sky2
--
0b:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Subsystem: Intel Corporation Device [8086:1121]
    Kernel driver in use: iwl4965
alexander@buffalo-buffalo:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abg  ESSID:"virginmedia4863546"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 84:1B:5E:B7:21:2B   
          Bit Rate=48 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:95   Missed beacon:0


alexander@buffalo-buffalo:~$ rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
alexander@buffalo-buffalo:~$ lsmod
Module                  Size  Used by
snd_hda_codec_idt      70774  1 
snd_hda_codec_hdmi     32476  1 
joydev                 17694  0 
coretemp               13642  0 
arc4                   12530  2 
kvm                   422160  0 
dell_wmi               12682  0 
snd_hda_intel          34063  3 
snd_hda_codec         135141  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
parport_pc             32867  0 
ppdev                  17114  0 
sparse_keymap          13891  1 dell_wmi
hid_generic            12541  0 
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rfcomm                 47562  12 
bnep                   18240  2 
gpio_ich               13384  0 
snd_seq_midi           13325  0 
mac_hid                13254  0 
snd_rawmidi            30750  1 snd_seq_midi
dell_laptop            17426  0 
dcdbas                 14491  1 dell_laptop
usbhid                 47259  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
hid                   100815  2 hid_generic,usbhid
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19257  1 dell_wmi
r592                   18145  0 
r852                   18282  0 
sm_common              16861  1 r852
nand                   54999  2 r852,sm_common
nand_ids               12724  1 nand
mtd                    44946  2 sm_common,nand
nand_bch               13148  1 nand
bch                    22064  1 nand_bch
memstick               16606  1 r592
nand_ecc               13274  1 nand
btusb                  22432  0 
microcode              23030  0 
iwl4965               114730  0 
iwlegacy              105121  1 iwl4965
psmouse               102506  0 
mac80211              555272  2 iwl4965,iwlegacy
snd                    83674  16 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             211812  24 bnep,rfcomm,btusb
serio_raw              13216  0 
uvcvideo               78117  0 
i915                  535128  3 
drm_kms_helper         49259  1 i915
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
drm                   290344  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
soundcore              15092  1 snd
lpc_ich                17145  0 
video                  19653  1 i915
cfg80211              208382  3 iwl4965,iwlegacy,mac80211
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ahci                   25869  2 
libahci                27338  1 ahci
firewire_ohci          41034  0 
sdhci_pci              18749  0 
firewire_core          64697  1 firewire_ohci
sdhci                  33145  1 sdhci_pci
crc_itu_t              12708  1 firewire_core
sky2                   59074  0 
alexander@buffalo-buffalo:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:62:e4:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67614 (67.6 KB)  TX bytes:67614 (67.6 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:ca:68:15  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3bff:feca:6815/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4701562 (4.7 MB)  TX bytes:436781 (436.7 KB)


alexander@buffalo-buffalo:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan0  [virginmedia4863546] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl4965
  State:             connected
  Default:           yes
  HW Address:        00:1F:3B:CA:68:15


  Capabilities:
    Speed:           54 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    NetgearHPVirgin: Infra, C0:3F:0E:D8:F1:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    SKY9A310:        Infra, 7C:4C:A5:06:A4:89, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2
    SKYFB0C0:        Infra, 7C:4C:A5:30:9B:F5, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2
    *virginmedia4863546: Infra, 84:1B:5E:B7:21:2B, Freq 2412 MHz, Rate 54 Mb/s, Strength 83 WPA WPA2
    linksys:         Infra, 00:18:F8:34:6B:65, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    virginmedia2751469: Infra, C4:3D:C7:41:C0:84, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    virginmedia2966504: Infra, 00:8E:F2:DB:67:5E, Freq 2422 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    BTWiFi-with-FON: Infra, 12:FE:F4:35:0E:F0, Freq 2412 MHz, Rate 54 Mb/s, Strength 15


  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             194.168.4.100
    DNS:             194.168.8.100




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1D:09:62:E4:B9


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off



```

Just as I was posting this, it managed to update some software. Other programs that use the internet (eg Anki) haven't been able to sync.

Any help would be greatly appreciated. Feel free to point out how my post could be better, too.

---

### Post by ohnonot on 2013-06-01
no internet access?
have you tried```
ping google.com
```?

---

### Post by chili555 on 2013-06-02
Please try:```
sudo modprobe -r iwl4965
sudo modprobe iwl4965 11n_disable=1
```If it helps, we'll write one file and make it persistent.

---

