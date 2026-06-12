---
title: "Wireless Authentication Problem"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by eigersa on 2012-10-09
Hi all. I recently installed Ubuntu (12) onto my Compaq 610 laptop (about 3 weeks ago), I installed it as a dual boot with Vista.

Up until now, everything has been perfect. On installation Ubuntu picked up my wireless router and on putting my pass-code in, authorized with no problem.

Yesterday, we had some power outages in the area, so I switched off the laptop and router for the day. But when I re-booted last night, Ubuntu picked up the wireless network, but kept asking for the pass-code over and over again without connecting.

When I re-boot into windows, there's no problem, I connect with no issues so I can't see it being the router or wireless. It must be a software issue. 

I did a forum search and followed the advice where I could, the steps I followed...

1) Disable wireless and re-enable: had no effect.
2) Disable wireless, re-boot then enable: had no effect
3) run "sudo restart network-manager": no effect

So anything I could try?

---

### Post by techvish81 on 2012-10-09
if it is a dial on demand connection created by you from the network manager, you can try to create a new connection  giving your credentials.

---

### Post by eigersa on 2012-10-09
Makes no difference, it stills asks for authentication, over and over again without connecting. A 2nd screen also pops up asking me to enter the pass code again.

---

### Post by NikTh on 2012-10-09
Hi , 

try to put your password manually in network-manager 

run in terminal 
```
gksudo nm-connection-editor
```Goto "wireless" section > click on your connection > click edit. 

First make sure that "available to all users" and "connect automatically" are marked up , then you can go to "wireless security" and set your password manually. 

Close and reboot. 

Thanks

---

### Post by moocow1452 on 2012-10-09
Same problem, looks like someone borked a driver that was pushed out recently. If you have a USB Wireless stick or can move it to a hardwire port, now would be a good time to bust it out, otherwise wait until it gets fixed or try and reset it yourself.

---

### Post by eigersa on 2012-10-09
@nikTH: Thanks for the advice, but no difference at all. ubuntu still insists on asking for authentication but never connects. I did notice that two separate screens ask, the first is a gnome3 type screen, the 2nd is a unity type screen. I did remove UNTIY when I first installed Ubuntu and was able to connect no problem, so I don't thank that's the problem.

@moowcow: unfortunately the wireless isn't usb so i guess I'll have to wait. 

Am going to try re-install ubuntu and see what happens.

---

### Post by eigersa on 2012-10-14
Since creating this thread a few days ago, I've re-installed Ubuntu twice now, googled for similar problems (which there seems to be many) and tried the suggestions made by various websites.

Still nothing. Pretty frustrating since I had it running perfectly at one stage! I really want to use Ubuntu and recommend it to family and friends, not too mention run it on my office laptops, but this lack of help and assistance is a definite killer, I have no option BUT to stick to windows! My experience with Ubuntu is definitely souring.

I would love to help solve this problem, but being a complete beginner to Ubuntu makes it difficult to even know where to start!

Where would one report this issue, is there a central database? Is there any way I could get hold of a developer, even if it is to just confirm an error on my side?

---

### Post by steeldriver on 2012-10-14
If it is a driver issue it is likely to be specific to a particular driver / chipset, so we will need to know exactly what wireless hardware you have - you can get the info by running these commands in a terminal and posting back the results:

```
lspci -vnn | grep -e '\[0200\]' -e '\[0280\]'
```

```
lshw -C network
```

Also would be good to see what drivers are getting loaded:

```
lsmod
```

---

### Post by elad21 on 2013-04-22
Hi,
I just now installed ubuntu and have the same problem, I keep getting these authentification messages for wifi connection passwords (though I am actually connected therough a wired connection). I printed the above codes and here are the results:
1)
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0082] (rev 34)
0a:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5761 Gigabit Ethernet PCIe [14e4:1681] (rev 10)
elad@elad-Latitude-E5420:~$ 

2) *-network               
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 34
       serial: 8c:70:5a:6a:a5:d0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-17-generic firmware=18.168.6.1 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:43 memory:e3c00000-e3c01fff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5761 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 10
       serial: d0:67:e5:4a:51:88
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=5761-v3.78 ip=132.66.42.238 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:e2010000-e201ffff memory:e2000000-e200ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
3)
elad@elad-Latitude-E5420:~$ lsmod
Module                  Size  Used by
bnep                   17707  2 
rfcomm                 37276  12 
uvcvideo               71277  0 
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_idt      59761  1 
videobuf2_core         32070  1 uvcvideo
videodev               95841  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
joydev                 17161  0 
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
arc4                   12473  2 
iwlwifi               348544  0 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              461161  1 iwlwifi
snd_seq_midi           13132  0 
coretemp               13168  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
kvm_intel             126745  0 
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
btusb                  17950  0 
snd_timer              24411  2 snd_pcm,snd_seq
kvm                   357806  1 kvm_intel
i915                  457161  3 
bluetooth             183228  22 bnep,rfcomm,btusb
cfg80211              175375  2 iwlwifi,mac80211
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
drm_kms_helper         45271  1 i915
wmi                    18590  1 dell_wmi
aesni_intel            17938  0 
dell_laptop            17161  0 
drm                   230463  4 i915,drm_kms_helper
cryptd                 15614  1 aesni_intel
aes_i586               16956  1 aesni_intel
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    35796  0 
i2c_algo_bit           13197  1 i915
psmouse                84843  0 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
serio_raw              13031  0 
dcdbas                 14054  1 dell_laptop
video                  18847  1 i915
ppdev                  12817  0 
lpc_ich                16925  0 
microcode              18209  0 
mac_hid                13037  0 
parport_pc             31968  0 
lp                     13299  0 
parport                40753  3 ppdev,parport_pc,lp
hid_generic            12445  0 
hid_a4tech             12590  0 
usbhid                 41702  0 
hid                    82142  3 hid_generic,hid_a4tech,usbhid
firewire_ohci          35521  0 
tg3                   130448  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci

Its all chinese to me - hope it can help in solving the issue.

---

### Post by Feathers McGraw on 2013-04-22
Any chance your router updated its firmware after you reset it? Might be worth booting into Vista and having a look in the router admin page (e.g. type 192.168.0.1 or something similar in your browser's address bar) to see if you could revert to the older version, if that is what has happened.

Might be easier than trying to find a compatible driver on the Ubuntu end.



Also, I had a similar problem with my laptop continually asking for a wifi password recently when I was trying to connect to a different router (a "MiFi") when my home router was down. The most frustrating thing about it was that I realised the problem was compatibility between the MiFi and the wireless driver on the laptop...but I had no internet connection to download and enable the proprietary driver with :mad:.




Feathers

---

### Post by steeldriver on 2013-04-22
elad21: sometimes the Intel wifi devices don't play nice with wireless-n mode - try opening a terminal and doing

```
sudo modprobe -r iwlwifi

sudo modprobe -v iwlwifi 11n_disable=1
```

If that stops the authentication requests then you can make it persistent (i.e. disable 11n every time the module loads) by doing

```
echo "options iwlwifi 11n_disable=1" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```

eigersa: your hardware may be different - if you are still having issues then please post the same info as elad21 and we can help you troubleshoot

---

