---
title: "wireless hardware switch disabled"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by uwillpanic on 2012-07-23
I recently installed Ubuntu, and after I did, the constant need of code offset me, so I booted back to windows. When I did, I found the wireless wasn't working. So I went back to ubuntu, and tried to learn. I got frustrated again, ported back to windows, and the wireless wasn't working again, so I ported back to Ubuntu another time. However, this time, my wifi wasn't working in ubuntu either. When checking in the wireless icon, it sais my wireless is disabled by a hardware switch. I have tried fn f2 and f8, as well as my normal hardware wifi switch. I don't know if this will help, but here is the output of lshw -C network


PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 05
       serial: dc:0e:a1:30:4e:f2
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.135 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:41:c0:66
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-27-generic firmware=39.31.5.1 build 35138 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:49 memory:f7e00000-f7e01fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

help would be infinitely appreciated.

---

### Post by Hadaka on 2012-07-23
Hi, please post the output of..

```
 rfkill list 
```

thanks.

---

### Post by uwillpanic on 2012-07-25
~$  rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
~$

---

### Post by NikTh on 2012-07-25
> **uwillpanic said:**
> ~$  rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
~$

Hi , 
this "Hard blocked:yes" shows that Wifi is closed. 
Try to open it with Function Keys (Fn+F? ) you can try all F keys 
or 
see in Bios if wireless is disabled. 

You can also try this command from terminal 
```
sudo rfkill unblock all
```

Thanks

---

### Post by uwillpanic on 2012-07-25
I tried the code and all of the function f keys, my wifi still isn't working. I don't know how to look in the Bios, though.

---

### Post by josephmills on 2012-07-25
can we see ```
lsmod
```
thanks

---

### Post by NikTh on 2012-07-25
> **uwillpanic said:**
>  I don't know how to look in the Bios, though.

Hi , 
usually you can get in to Bios configuration page by press an F key or "Del" key. 
At my pc this key is F2 . 
When you boot up at pre-boot screen (the first screen that appears when open your pc) you will see (usually down) what key must pressed to get in Bios config page. 
You will see a message similar to that 
" F2 to setup" 
You must press this key  BEFORE screen change. 

**But if you are not familiar with Bios configuration leave it for now.. **
follow joshephmills suggestions .. give the results of command (maybe some module conflict and block your wireless)

Thanks

---

### Post by uwillpanic on 2012-07-25
~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61512  1 vfat
uas                    18180  0 
usb_storage            49198  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223962  1 
binfmt_misc            17540  1 
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
bluetooth             180104  10 bnep,rfcomm
ppdev                  17113  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
iwlwifi               332672  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  472897  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
snd_timer              29990  2 snd_pcm,snd_seq
lp                     17799  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
toshiba_acpi           18582  0 
joydev                 17693  0 
sparse_keymap          13890  1 toshiba_acpi
jmb38x_ms              17646  0 
mei                    41616  0 
psmouse                87692  0 
mac_hid                13253  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
memstick               16569  1 jmb38x_ms
video                  19596  1 i915
parport                46562  3 parport_pc,ppdev,lp
serio_raw              13211  0 
uvcvideo               72627  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
videodev               98259  1 uvcvideo
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
wmi                    19256  1 toshiba_acpi
v4l2_compat_ioctl32    17128  1 videodev
usbhid                 47199  0 
hid                    99559  1 usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62099  0 

here's the output

---

### Post by NikTh on 2012-07-25
Hi , 
you can try this.. 
```
sudo modprobe -rf toshiba_acpi
sudo modprobe -rf  iwlwifi
sudo modprobe  iwlwifi 
```Or 
```
sudo modprobe iwlwifi 11n_disable=1
``` instead of last command.

Wifi awakened ?

Thanks

---

### Post by uwillpanic on 2012-07-25
> **NikTh said:**
> Hi , 
you can try this.. 
```
sudo modprobe -rf toshiba_acpi
sudo modprobe -rf  iwlwifi
sudo modprobe  iwlwifi 
```Or 
```
sudo modprobe iwlwifi 11n_disable=1
``` instead of last command.

Wifi awakened ?

Thanks
no go. When I did some research, I found that my problem may be that I need a driver. thoughts?

---

### Post by NikTh on 2012-07-26
Hi , 
I think the driver is already there (in the system) but maybe something is wrong with firmware , or something conflict. 
Take a look at here --> [http://askubuntu.com/questions/74692/wifi-for-centrino-wireless-n-1000-intel-corporation-hp-pavillion-dm4-2070us](http://askubuntu.com/questions/74692/wifi-for-centrino-wireless-n-1000-intel-corporation-hp-pavillion-dm4-2070us)

Thanks

---

### Post by uwillpanic on 2012-07-27
> **NikTh said:**
> Hi , 
I think the driver is already there (in the system) but maybe something is wrong with firmware , or something conflict. 
Take a look at here --> [http://askubuntu.com/questions/74692/wifi-for-centrino-wireless-n-1000-intel-corporation-hp-pavillion-dm4-2070us](http://askubuntu.com/questions/74692/wifi-for-centrino-wireless-n-1000-intel-corporation-hp-pavillion-dm4-2070us)

Thanks

nope.

---

### Post by uwillpanic on 2012-08-04
> **NikTh said:**
> Hi , 
I think the driver is already there (in the system) but maybe something is wrong with firmware , or something conflict. 
Take a look at here --> [http://askubuntu.com/questions/74692/wifi-for-centrino-wireless-n-1000-intel-corporation-hp-pavillion-dm4-2070us](http://askubuntu.com/questions/74692/wifi-for-centrino-wireless-n-1000-intel-corporation-hp-pavillion-dm4-2070us)

Thanks
Actually, when I did it it no longer said that the WiFi was disabled by a hardware switch, but still isn't connecting.

---

