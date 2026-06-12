---
title: "Toshiba satellite P745 wifi hardware not detected 10.04 LTS"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by raoshivani on 2012-03-03
I am tired and frustrated of trying to solve the wifi issue on my Toshiba P745 laptop. Here are the details  of the typical commands used to 


```

shivani@shivani-laptop:~$ uname -a
Linux shivani-laptop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 x86_64 GNU/Linux

``````

shivani@shivani-laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Intel Corporation Device [8086:0885] (rev 67)
05:00.0 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2392] (rev 30)
05:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2391] (rev 30)

``````

shivani@shivani-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 05
       serial: dc:0e:a1:33:7e:b0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=128.46.144.224 latency=0 multicast=yes
       resources: irq:29 ioport:e000(size=256) memory:f0004000-f0004fff(prefetchable) memory:f0000000-f0003fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 67
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7e00000-f7e01fff

``````

shivani@shivani-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

``````

shivani@shivani-laptop:~$ lsmod
Module                  Size  Used by
intel_agp              29319  0 
drm_kms_helper         30742  0 
drm                   200384  1 drm_kms_helper
i2c_algo_bit            6024  0 
binfmt_misc             7960  1 
ppdev                   6375  0 
dm_crypt               13043  0 
joydev                 11104  0 
snd_hda_codec_realtek   279072  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
uvcvideo               62915  0 
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
videodev               40550  1 uvcvideo
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            15495  2 uvcvideo,videodev
sdhci_pci               6700  0 
v4l2_compat_ioctl32    11892  1 videodev
sdhci                  17960  1 sdhci_pci
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
xhci                   42775  0 
soundcore               8052  1 snd
psmouse                65040  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
serio_raw               4918  0 
led_class               3764  1 sdhci
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 41116  0 
hid                    83888  1 usbhid
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
r8169                  39714  0 
vga16fb                12757  1 
mii                     5237  1 r8169
vgastate                9857  1 vga16fb
ahci                   38350  5 
video                  20623  0 
output                  2503  1 video

``````

shivani@shivani-laptop:~$ rfkill list
shivani@shivani-laptop:~$ dmesg | egrep 'rtl8|r8'
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff88002c200000 s91608 r8192 d23080 u524288
[    0.000000] pcpu-alloc: s91608 r8192 d23080 u524288 alloc=1*2097152
[    1.413939] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.413981] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.414094] r8169 0000:02:00.0: setting latency timer to 64
[    1.414110] r8169 0000:02:00.0: unknown MAC, using family default
[    1.414317] r8169 0000:02:00.0: irq 29 for MSI/MSI-X
[   27.250499] r8169: eth0: link up
[   27.250515] r8169: eth0: link up

```I know this problem seems really similar to the one posted by this [thread]("http://ubuntuforums.org/showthread.php?t=1608908"), I tried the following solution provided by them but nothing changed

```

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkm

```I tried downloading drivers from the internet and attempting to install them but I always got "hardware not detected".  I installed ndiswrapper and then tried to use the .inf file to install the driver. Did not work. What I tried is summarized in this thread

```

https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667

```I even tried installing the bw43fcutter and all that  using the following [thread]("http://www.qc4blog.com/?p=857")

I am so tired and frustated please help me

Shivani

---

### Post by Daveth on 2012-03-03
and does toggling the Fn-F8 wireless on/off command do anything? I wonder if it has fallen asleep.

---

### Post by raoshivani on 2012-03-05
Well, I tried that , that does change the LED that indicates if the wireless is on or not. but does not help in detection of wifi hardware. So even when the Wireless LED is glowing, no wifi hardware is detected

---

