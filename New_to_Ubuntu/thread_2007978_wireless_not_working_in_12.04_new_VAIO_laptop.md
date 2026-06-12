---
title: "wireless not working in 12.04 new VAIO laptop"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by Wraith101 on 2012-06-21
Just got a new VAIO laptop (model: SVT131190S) and did an installation  of Ubuntu 12.04 via windows. The wireless is not working though. 

I tried following the steps at [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers) but I can't really tell what is going on.

I  will go through the steps I followed with my results and hopefully  someone can solve my problem and /or explain the outputs of the various  commands.

I ran nm-tool

```

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        30:F9:ED:FD:2E:58

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        08:ED:B9:BC:B6:93

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


```and lshw -C network

```

  *-network DISABLED
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 08:ed:b9:bc:b6:93
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
        configuration: broadcast=yes driver=ath9k  driverversion=3.2.0-23-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:c3000000-c307ffff memory:c0000000-c000ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 07
       serial: 30:f9:ed:fd:2e:58
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
        capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet  physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half  firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes  port=MII speed=10Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:c4404000-c4404fff memory:c4400000-c4403fff

```So it looks like I have a wireless that is disabled using an ath9k driver. I ran lsmd

```

Module                  Size  Used by
usb_storage            49198  1 
rfcomm                 47604  12 
parport_pc             32866  0 
bnep                   18281  2 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
acer_wmi               28418  0 
sparse_keymap          13890  1 acer_wmi
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
arc4                   12529  2 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k                 132390  0 
mac80211              506816  1 ath9k
rts_pstor             445196  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
btusb                  18288  2 
uvcvideo               72627  0 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
videodev               98259  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17128  1 videodev
sony_laptop            45393  0 
bluetooth             180104  23 rfcomm,bnep,btusb
psmouse                87603  0 
serio_raw              13211  0 
cfg80211              205544  3 ath9k,mac80211,ath
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                     78855  16  snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  468651  3 
wmi                    19256  1 acer_wmi
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
r8169                  62099  0 

```I  don't think there is more than one module there, but I don't really  understand the output so I might be wrong. I also ran iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off     

```The  gui also indicates that I have wireless but that it is disabled. When I  try to enable it it switches back to 'off' almost immediately. I ran  the scanning command iwlist scan

```

wlan0    Interface doesn't support scanning. 

```I  did do some googling about upgrading my drivers but as I understand it  that means compiling the kernel and so I wussed out of that idea.

The  last section of the troubleshooter mentions that the device might be  disabled. My laptop doesn't appear to have this functionality. There are  no Fn+x keys that disable/enable wireless as far as I can tell.

I ran rfkill list

```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```huh? why do I have an entry for acer-wireless? it is blocked but is that my actual wireless, or something random?

Based on all this output, I am not really sure what my problem is. Any assistance would be very much apreciated. 

Thanks in advance.

---

### Post by wildmanne39 on 2012-06-21
Hi, please do:
```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.
Thanks

---

### Post by Wraith101 on 2012-06-21
That worked, thank you very much. 

I assume that means that I did have multiple drivers installed after all? Is it possible to determine this from the lsmod output?

Again thankyou, it is very disheartening when windows just works and with ubuntu I have to resort to asking questions within a few hours of installing it, but your prompt reply makes up for it in a big way.

---

### Post by wildmanne39 on 2012-06-21
Hi, your welcome!!!

---

