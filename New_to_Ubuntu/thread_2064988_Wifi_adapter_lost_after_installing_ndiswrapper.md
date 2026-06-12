---
title: "Wifi adapter lost after installing ndiswrapper"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by bonehunter on 2012-09-30
Hey guys after endless searching google and forums I hope to get help here. But first of hello to all and thanks in advance.

Now to my problem;

I installed on my Laptop Acer Aspire 5750G running Ubuntu Linux 12.04 Lts ndiswrapper through Ubuntu Software Center. After installation I installed through gui an Windows wireless driver which I used in Windows 7 x64 same notebook. After installation it showed up in ndiswrapper hardware found: yes. 

Atheros Wireless Adapter AR9287

But!!!

I lost actually my wifi adapter, which means there is no possibility to reach my wifi adapter or to connect to wirless lan. I can only plug a cable to my computer to get Internet access.

So again what happened to my computer? I removed diswrapper but could not get the previous configuration back.

No I´m whithout any clue or idea what to do!

Thanks guys quite a lat for any help you can provide.

---

### Post by daslinkard on 2012-10-05
Welcome to the forums!  Please give the output of the following sudo command:
```

lspci
```

---

### Post by bonehunter on 2012-10-06
Thanks for your replay,.... here as you asked me to print...


00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
02:00.2 System peripheral: Broadcom Corporation Device 16be (rev 10)
02:00.3 System peripheral: Broadcom Corporation Device 16bf (rev 10)
03:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01

---

### Post by daslinkard on 2012-10-07
I have been gone for most of yesterday and will be looking at this later on today....unless someone else can also help!

---

### Post by daslinkard on 2012-10-07
Let's see if this gets you moving in the right direction...
```
sudo apt-get update 
``````
sudo apt-get install linux-backports-modules-wireless-lucid-generic
``` ```
sudo reboot
```Let me know if this works for you...

---

### Post by NikTh on 2012-10-07
> **bonehunter said:**
> 
I installed on my Laptop Acer Aspire 5750G running **Ubuntu Linux 12.04 Lts **

> **daslinkard said:**
> Let's see if this gets you moving in the right direction...
```
sudo apt-get update 
``````
sudo apt-get install linux-backports-modules-wireless-**lucid**-generic
```

He has Ubuntu 12.04 Precise Pangolin , not 10.04 Lucid Lynx. 

I suggest 

1) First remove completely the ndiswrapper . 
```
sudo modprobe -rf ndiswrapper 
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk 
sudo rm /etc/modprobe.d/ndiswrapper.conf 
sudo rm -r /etc/ndiswrapper/*  
sudo depmod -a
```Reboot your PC 
Then give the results***** of bellow commands 

```
lspci -nnk | grep -iA2 net 
lsmod 
ifconfig 
nmcli nm status
rfkill list all
nm-tool
```*****Put the results between the brackets **[noparse]```
Here
```[/noparse]**.

Thanks

---

### Post by daslinkard on 2012-10-07
Thank you NikTH for the catch!

---

### Post by bonehunter on 2012-10-10
Thanks guys...
The thread from NikTH helped to solve the problem. Wifi is back on my laptop but now I have another issule.

Code (02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: tg3
--
02:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0504]
    Kernel driver in use: sdhci-pci
--
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6603]
    Kernel driver in use: ath9k
)

lsmod

lsmod 
Module                  Size  Used by
ppp_deflate            13038  0 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             25670  0 
vboxnetflt             23441  0 
vboxdrv               282587  3 vboxpci,vboxnetadp,vboxnetflt
bbswitch               13396  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   224173  1 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
cdc_ether              13536  0 
option                 25932  2 
usbnet                 26212  1 cdc_ether
usb_wwan               20491  1 option
usbserial              47077  7 option,usb_wwan
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411151  2 ath9k,ath9k_common
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97362  0 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13211  0 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  473240  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
mei                    41616  0 
i2c_algo_bit           13423  1 i915
mxm_wmi                12979  0 
video                  19596  1 i915
ndiswrapper           282628  0 
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18180  0 
usb_storage            49198  1 
mmc_block              27300  2 
tg3                   152032  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci

(eth0      Link encap:Ethernet  HWaddr b8:70:f4:ac:ca:46  
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
          RX packets:7946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:842846 (842.8 KB)  TX bytes:842846 (842.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:109.125.16.72  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1090 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:978935 (978.9 KB)  TX bytes:131242 (131.2 KB)
)

( nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         disabled   enabled         enabled   )

(rfkill list all
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no)

(nm-tool

NetworkManager Tool

State: connected (global)

- Device: ttyUSB0  [E-Mobile Broadband To Go] ----------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            option1
  State:             connected
  Default:           yes

  Capabilities:

  IPv4 Settings:
    Address:         109.125.16.72
    Prefix:          32 (255.255.255.255)
    Gateway:         10.64.64.64

    DNS:             212.129.64.220
    DNS:             212.129.64.221


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        68:A3:C4:ED:72:2B

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        B8:70:F4:AC:CA:46

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
)


Sorry mate I know it´s not what was meant by ().

But anyway I hope you can see where it is divided.

thanks again quite a lot!

---

### Post by squakie on 2012-10-10
Just as a note to you and to others who may have the same issue and are looking for help:

Normally ndiswrapper is not needed for most people.  Driver support has been much improved over the last few releases, but there remain many of the old posts both in these forums and else where on the net regarding using ndiswrapper.

If your wireless doesn't work, the first thing to try, if possible, is temporarily connecting a hard wire between your PC and the router, then trying Additional Drivers.  If it returns with a driver and says it is not activated, then activate it.

There are also some Broadcom devices which used to require ndiswrapper that don't anymore.  Some require the addition of a couple of files.  If you search the forum you may find those - if not, create a post and include the output of lspci and lsusb (type these in a terminal window).  These 2 commands list the devices on your pci buss and on the USB busses - where your wireless device will be found - so that people here can look further without having to ask for that information first.  Further information may be requested as well.

---

### Post by squakie on 2012-10-10
And now onto your latest post - what is the additional problem you are having now?

---

### Post by bonehunter on 2012-10-14
Thanks guys that you are still willing to help me with my other system problems:
#
There are three issues:

- if I send my computer to suspend and wake it up again, I get an black screen with three error messages. I can not report them because its just for an instant  of time until the gui starts, if the gui starts which is sometimes not sure. When the gui does not start I change to alt+ctrl+F1 and force a reboot.

- another problem, my short cuts are not working like ctrl+alt+D or T, in the system it´s enabled

- last problem which is just a minor problem, if I want to dim my screen through Fn + required key it dims but I don´t get an visual note like it does if I adjust the volume (I did this to achieve the fn key working: Summary:
  
[LIST=1]
[*]Edit your /etc/default/grub file:
  *sudo gedit /etc/default/grub*
[*]Add the options "acpi_osi=Linux acpi_backlight=vendor" to the GRUB_CMDLINE_LINUX_DEFAULT line. It should look like this:
  *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"*
  original line was:
  *GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"*
[*]Update grub configuration!!!! - do not forget to do this, the  configuration change will not be set up if you don't run the next  command:
  *sudo update-grub*
[/LIST]
  This worked for me after trying a lot of other solutions. I have a HP dv7-6090ef with hybrid graphics Intel/AMD.
)

Thanks again

By the way I don´t want to bother you with my kind of bad English, I´m still working on it.

---

### Post by wildmanne39 on 2012-10-14
Hi, if your first issue is solved please mark this thread solved and start a new thread for each one of the issue's you still have because you are allowed only one issue per thread.
Thanks

---

### Post by bonehunter on 2012-10-15
pls close thread, it´s solved

---

### Post by squakie on 2012-10-15
If you go to just above the first post in the thread you will see "Thread Options".  You can use this and mark the thread as "Solved".

---

