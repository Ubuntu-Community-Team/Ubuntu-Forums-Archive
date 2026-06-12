---
title: "Internet problems! (Wireless and Wired)"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by acidydragon on 2013-04-04
I just installed Ubuntu, and so far its great! Except... It says both internets are connected (wireless and wired), but randomly decides when it will work, and when it wont, and when it works, it's very slow.
The internet gets 55 mps download on speedtest.
Am I missing something?

---

### Post by wildmanne39 on 2013-04-05
Hi, follow the directions in the link for running the script with no internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by acidydragon on 2013-04-05
*************** info trace ****************



**** uname -a ****


Linux Desktop-Kyle 3.5.0-26-generic #42-Ubuntu SMP Fri Mar 8 23:18:20 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


**** lsb-release ****


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"


**** lspci ****


07:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Atheros Communications Inc. DW1525 802.11abgn WLAN PCIe Card [AR9280] [168c:0203]
    Kernel driver in use: ath9k
--
0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8505]
    Kernel driver in use: r8169


**** lsusb ****


Bus 007 Device 002: ID 046d:c531 Logitech, Inc. 
Bus 007 Device 003: ID 046d:c22d Logitech, Inc. G510 Gaming Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


**** iwconfig ****


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=21 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


**** rfkill ****


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


**** lsmod ****


Module                  Size  Used by
nls_utf8               12558  1 
udf                    89521  1 
crc_itu_t              12708  1 udf
snd_hda_codec_hdmi     32049  1 
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
binfmt_misc            17501  1 
nls_iso8859_1          12714  1 
arc4                   12530  2 
kvm_amd                55605  0 
kvm                   414071  1 kvm_amd
ghash_clmulni_intel    13221  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
eeepc_wmi              13110  0 
asus_wmi               24089  1 eeepc_wmi
sparse_keymap          13891  1 asus_wmi
mxm_wmi                13022  0 
snd_hda_codec_realtek    78147  1 
microcode              22804  0 
snd_seq_midi           13325  0 
snd_hda_intel          33492  5 
joydev                 17458  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    19071  2 asus_wmi,mxm_wmi
snd                    78921  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_rawmidi,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
ath9k                 131317  0 
mac80211              540032  1 ath9k
mac_hid                13206  0 
radeon                895730  2 
fam15h_power           13120  0 
ath9k_common           14056  1 ath9k
ath9k_hw              395357  2 ath9k,ath9k_common
edac_core              52452  0 
edac_mce_amd           23304  0 
ath                    23828  3 ath9k,ath9k_common,ath9k_hw
k10temp                13127  0 
ttm                    83596  1 radeon
sp5100_tco             13698  0 
i2c_piix4              13168  0 
drm_kms_helper         49113  1 radeon
cfg80211              206797  3 ath9k,mac80211,ath
drm                   288721  4 radeon,ttm,drm_kms_helper
psmouse                95595  0 
soundcore              15048  1 snd
serio_raw              13216  0 
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13414  1 radeon
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
r8169                  61651  0 
ahci                   25721  4 
libahci                31192  1 ahci


**** nm-tool ****



NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.75.75
    DNS:             75.75.76.76


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HOME-E2A2:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2

---

### Post by wildmanne39 on 2013-04-05
Please do:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Hopefully that will improve signal also because your signal strength is to low to connect too.

Where is the rest of the information from the script?

Also it will best with just wpa2 encryption if you have that option in your router settings.
Thanks

---

