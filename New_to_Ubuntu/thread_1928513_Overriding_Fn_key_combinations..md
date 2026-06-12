---
title: "Overriding Fn key combinations."
date: 2012-02-20
forum: New to Ubuntu
---

### Post by flashgo9 on 2012-02-20
Hi there folks,

I've got a Lenovo Y410 laptop. Pressing the Fn key + F5 enables/disables  the WLAN. I had to resort to disable the WLAN last night. Unfortunately  enough, the F5 key has stopped working. I crosschecked its  functionality in BIOS. The key just doesn't work.

Yes, I have an external switch to power on/off the bluetooth along with  the wifi, but it just doesn't work that way. I will have to enable it by  using the F5 key alone. I even tried plugging in an USB keyboard,  holding the Fn key of my laptop while pressing the F5 of my USB  keyboard, but in vain.

I`m using Ubuntu 10.10, the Maverick Meerkat, btw. I tried Googling for a solution, but nothing seems to work. 

Here is what some commands return: 

rfkill list all returned: 

> 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
lspci returned:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
06:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
08:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
08:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
sudo lshw -c network returned:

>  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:a1:48:84
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-32-generic firmware=15.32.2.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:f0000000-f0000fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:1b:38:a7:87:cb
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=sb v3.03 ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:47 memory:b8000000-b800ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
I have tried rfkill unblock all, rfkill unblock wifi, but nothing seems to work as well.

I appreciate your time and effort. Thank you.

---

### Post by raja.genupula on 2012-02-20
look like we have a way 
[http://askubuntu.com/questions/88063/how-to-invert-fn-keys-on-dell-laptop](http://askubuntu.com/questions/88063/how-to-invert-fn-keys-on-dell-laptop)

---

### Post by flashgo9 on 2012-02-20
The laptop is a Lenovo model, by the way. Specifically, Lenovo Y410 3000 is the product name.

EDIT: I`ve tried the BIOS workaround, but my BIOS, strangely, has very limited options. All I can do is set the system time and date, and also the master password. No other options. 
Phoenix Trustedcore v3.02 is the version. Any help would be much appreciated.

Thank you for the efforts.

---

### Post by raja.genupula on 2012-02-20
[http://forums.lenovo.com/t5/A-and-M-Series-ThinkCentre/Can-I-use-my-function-keys-as-function-keys/td-p/475431](http://forums.lenovo.com/t5/A-and-M-Series-ThinkCentre/Can-I-use-my-function-keys-as-function-keys/td-p/475431)

but i am sure about this .

lemme know what you got .
all the best . :)

---

### Post by flashgo9 on 2012-02-20
Hi. 

Tried, but in vain.

Went ahead to edit the Wireless option in BIOS, but alas, there isn`t one. Just like I said, all I can edit is the system time and date and of course, the boot order. Wired internet for my laptop it is, I guess.

Thank you raja.genupula, for the efforts.

---

### Post by wildmanne39 on 2012-02-20
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by flashgo9 on 2012-02-20
Hi wildmanne39! 

cat /etc/lsb-release; uname -a

```
 DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux ubuntu 2.6.35-32-generic #65-Ubuntu SMP Tue Jan 24 13:48:14 UTC 2012 i686 GNU/Linux

```lspci -nnk | grep -iA2 net

```
04:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:1000]
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
06:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Subsystem: Lenovo Device [17aa:3861]
    Kernel driver in use: tg3

```iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

```rfkill list all:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by wildmanne39 on 2012-02-20
Hi, your wireless is not longer hard blocked.

Please do:
```
nm-tool
lsmod
```
Thanks

---

### Post by flashgo9 on 2012-02-20
Thank you, wilmanne39, for your time. These were the results.

nm-tool:

```
NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:1C:BF:A1:48:84

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        00:1B:38:A7:87:CB

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

```lsmod:

```
Module                  Size  Used by
binfmt_misc             6599  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
snd_atiixp_modem        9147  0 
snd_via82xx_modem       8498  0 
parport_pc             26058  0 
ppdev                   5556  0 
snd_intel8x0m          10731  0 
snd_ac97_codec         99227  3 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m
snd_hda_codec_si3054     3440  1 
ac97_bus                1014  1 snd_ac97_codec
snd_hda_codec_realtek   218460  1 
joydev                  8767  0 
arc4                    1165  2 
snd_hda_intel          22235  2 
snd_hda_codec          87552  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  296139  4 
snd_seq_midi_event      6047  1 snd_seq_midi
iwl3945                85349  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
iwlcore               127415  1 iwl3945
drm_kms_helper         30200  1 i915
mac80211              231959  2 iwl3945,iwlcore
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168124  4 i915,drm_kms_helper
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
psmouse                59027  0 
mtd                    18877  2 sm_common,nand
snd                    49102  18 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_ac97_codec,snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              144758  3 iwl3945,iwlcore,mac80211
serio_raw               4022  0 
intel_agp              26566  2 i915
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
agpgart                32011  2 drm,intel_agp
video                  18712  1 i915
snd_page_alloc          7120  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
sdhci_pci               6633  0 
firewire_ohci          21330  0 
sdhci                  15922  1 sdhci_pci
firewire_core          46675  1 firewire_ohci
tg3                   123310  0 
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core

```

---

### Post by wildmanne39 on 2012-02-20
Hi, unplug your wired connection and see if it turns on.

Make enable wireless is checked in the network manager settings in the top right corner of the screen.

Please post the output of:
```
modinfo iwl3945
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by flashgo9 on 2012-02-21
Hi wildmanne39,

I unplugged the wired connection, but it still doesn't turn on. Enable wireless is checked. 

But now, I cannot use the wired internet as well. I'm posting this from another computer. Would you still like me to give the two outputs you mentioned in your last post?

---

### Post by wildmanne39 on 2012-02-21
Hi, yes please and post the complete results, you can paste them to a usb drive and then use another computer to post them here.
Thanks

---

### Post by flashgo9 on 2012-02-21
Hi wildmanne39,

modinfo iwl3945 returned:

```
filename:       /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     55BD8546797AE5D310D9762
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.35-32-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software])
 (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           fw_restart3945:restart firmware in case of error (int)


```

sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75 returned:

```
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> (wlan0): bringing up device.
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> (wlan0): device state change: 5 -> 9 (reason 4)
Feb 21 13:14:20 ubuntu NetworkManager[829]: <warn> Activation (wlan0) failed for access point (UTStarcom)
Feb 21 13:14:20 ubuntu NetworkManager[829]: <warn> Activation (wlan0) failed.
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Feb 21 13:14:20 ubuntu kernel: [   25.170313] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
Feb 21 13:14:20 ubuntu NetworkManager[829]: <info> (wlan0): deactivating device (reason: 0).
Feb 21 13:14:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:15:01 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:15:41 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:16:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:17:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:18:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:19:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:20:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:21:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:22:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:23:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:24:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:25:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:26:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:27:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:28:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:29:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:30:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:31:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:32:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:33:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:34:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:35:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:36:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:37:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:38:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:39:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:40:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:41:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:42:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:43:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:44:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:45:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:46:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:47:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:48:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:49:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:50:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:51:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:52:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:53:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:54:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:55:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:56:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:57:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:58:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 13:59:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:00:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:01:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:02:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:03:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:04:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:05:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:06:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:07:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:08:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:09:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:10:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:11:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:12:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:13:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.
Feb 21 14:14:31 ubuntu wpa_supplicant[885]: Failed to initiate AP scan.


```

Thank you, sire.

---

### Post by wildmanne39 on 2012-02-21
Hi, please try:
```
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```
Thanks

---

### Post by flashgo9 on 2012-02-22
Hi. First of all, sorry for the late reply. I am from a different timezone. 

The above code, when typed inside the terminal shows "permission denied", but somehow, the wired internet is working again.

> 
bash: /etc/modprobe.d/iwl3945: Permission denied

---

### Post by wildmanne39 on 2012-02-22
Hi, try it this way:
```
sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
```
Then enter your user password.
Thanks

---

### Post by flashgo9 on 2012-02-23
The above code returned no results. I tried rebooting my system and WLAN still doesn`t work.

---

### Post by wildmanne39 on 2012-02-23
Hi, that command would only show output if there were errors.

Please post the contents of:
```
gksu gedit /etc/modprobe.d/iwl3945.conf
```
Thanks

---

### Post by flashgo9 on 2012-02-24
Hi, the above command opened a file iwl3945.conf. The file had no contents in it.

---

### Post by wildmanne39 on 2012-02-24
Hi, please do:
```
gksu gedit /etc/modprobe.d/iwl3945.conf
```
Add a single line:
```
options iwl3945 disable_hw_scan=1
```
save, close gedit and reboot.
Thanks

---

### Post by flashgo9 on 2012-02-24
Hi, I did the tasks. 

The LED light remained unlit while Ubuntu was loading which diminished my hopes. 

No. It still doesn`t work.

Thank you.

---

### Post by wildmanne39 on 2012-02-26
Hi, please post the output of:
```
cat /var/lib/NetworkManager/NetworkManager.state
dmesg | egrep 'iwl|firm|radio|switch|wmi'

```
Thanks

---

### Post by flashgo9 on 2012-02-27
Hi, this is what the above codes returned. 

```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
lenovo@ubuntu:~$ dmesg | egrep 'iwl|firm|radio|switch|wmi'
[   16.431489] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   16.431494] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   16.431605] iwl3945 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.431622] iwl3945 0000:04:00.0: setting latency timer to 64
[   16.494393] iwl3945 0000:04:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   16.494400] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   16.494571] iwl3945 0000:04:00.0: irq 44 for MSI/MSI-X
[   16.584081] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.148361] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[   17.148616] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
[   17.214823] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
[   17.407309] Console: switching to colour frame buffer device 160x50
[   28.859780] iwl3945 0000:04:00.0: Radio disabled by HW RF Kill switch
```

---

### Post by wildmanne39 on 2012-02-27
Hi, please do:
```
sudo gedit /etc/rc.local
```
Add your three lines above exit 0
```
rmmod -r ath5k
rfkill unblock all
modprobe ath5k
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working.
Thanks

---

### Post by flashgo9 on 2012-02-27
Hi wildmanne39, 

This is how rc.local looks now. I included a screenshot, just in case.

[http://i39.tinypic.com/33vdbt0.png](http://i39.tinypic.com/33vdbt0.png)

The results were negative this time around too.

---

### Post by wildmanne39 on 2012-02-27
Hi, I made a mistake when I copied and pasted the commands, I got distracted and forgot to change the driver, please open the file and change ```
ath5k to iwl3945
```
every time is appears which is twice.
Thanks

---

### Post by flashgo9 on 2012-02-27
Hi, changed the driver name, no luck this time either. :(

---

### Post by wildmanne39 on 2012-02-27
Hi, did you reboot?

---

### Post by flashgo9 on 2012-02-28
Hi.
Yes sir, I did perform a reboot.

---

### Post by wildmanne39 on 2012-02-28
Hi, please try:
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot.
Thanks

---

### Post by flashgo9 on 2012-02-28
Hi,
Isn`t the aforementioned code for an Acer laptop?

---

### Post by wildmanne39 on 2012-02-28
Hi, also included in many leveno's and others.
Thanks

---

### Post by flashgo9 on 2012-02-28
Hi,
The code I tried above returned:

```
blacklist acer-wmi
```

Performed a reboot, but the wifi is still not working. 

Thank you.

---

### Post by flashgo9 on 2012-03-03
*bump*

---

### Post by flashgo9 on 2012-03-07
Hi,
Can someone tell me if buying a new wifi dongle will solve the issue?
Please?

Thank you.

---

### Post by wildmanne39 on 2012-03-09
Hi, sorry I am not available much right now and that I do not know how to solve your issue.

I do not think that buying an usb adapter will fix your problem but you can try it if you want too, you can always return it and get your money back.
Thanks

---

