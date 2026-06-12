---
title: "Use of Logitech c100m webcam disables my wireless USB adapter"
date: 2011-09-19
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by elzindar3 on 2011-09-19
Just as the title says, my wireless USB adapter works fine...until I try to use my  Logitech c100m webcam. Once I start my Logitech c100m webcam, I get a notification that my wireless card has been disabled. The only solution that I have thus far, is to restart the computer, then the wireless network is functioning again, however, any further attempt to start the webcam again will disable the wireless.

Any help would be greatly appreciated.

lsusb:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:0817 Logitech, Inc. 
Bus 003 Device 002: ID 192f:0616 Avago Technologies, Pte. 
Bus 001 Device 005: ID 0cf3:1006 Atheros Communications, Inc. TP-Link TL-WN322G v3 / TL-WN422G v2 802.11g [Atheros AR9271]

---

### Post by cariboo on 2011-09-19
What's the output of:

```
dmesg | tail -n25
```

when you plug your webcam in?

---

### Post by elzindar3 on 2011-09-19
[19703.408417] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[19703.408419] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[19703.408422] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[19703.408425] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[19703.408428] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[19703.408430] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[19703.408433] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[19703.408436] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[19703.408439] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[19703.408441] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[19703.408444] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[19703.408447] cfg80211: Disabling freq 2484 MHz
[19703.408450] cfg80211: World regulatory domain updated:
[19703.408452] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[19703.408459] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19703.408462] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[19703.408465] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[19703.408468] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19703.408471] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[19703.413875] ath: Failed to wakeup in 500us
[19703.561531] ath: Failed to wakeup in 500us
[19703.930175] usb 1-4: ath9k_htc: USB layer deinitialized
[19706.610080] usb 1-5: new high speed USB device number 6 using ehci_hcd
[19706.879024] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0817)
[19706.919791] input: UVC Camera (046d:0817) as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input13

---

### Post by elzindar3 on 2011-09-19
Bump!!!

---

### Post by lucazade on 2011-09-20
you should wait a bit longer before bump..
the problem is visible in the output cariboo asked you, 

[19703.413875] ath: Failed to wakeup in 500us
[19703.561531] ath: Failed to wakeup in 500us
[19703.930175] usb 1-4: ath9k_htc: USB layer deinitialized

it seems a common issue for ath9k, do some googling.. never seen here with a ath5k.

paste the output of:
dmesg | grep ath

---

### Post by elzindar3 on 2011-09-20
```
mohamad@mohamad-A780GM-A:~$ dmesg | grep ath
[   32.437152] usb 1-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   32.672991] ath9k_htc 1-4:1.0: ath9k_htc: HTC initialized with 33 credits
[   32.881972] ath9k_htc 1-4:1.0: ath9k_htc: FW Version: 1.3
[   32.881977] ath: EEPROM regdomain: 0x809c
[   32.881979] ath: EEPROM indicates we should expect a country code
[   32.881982] ath: doing EEPROM country->regdmn map search
[   32.881984] ath: country maps to regdmn code: 0x52
[   32.881986] ath: Country alpha2 being used: CN
[   32.881987] ath: Regpair used: 0x52
[   32.891824] Registered led device: ath9k_htc-phy0
[   32.891830] usb 1-4: ath9k_htc: USB layer initialized
[   32.891930] usbcore: registered new interface driver ath9k_htc
[   42.426272] type=1400 audit(1316518060.303:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=982 comm="apparmor_parser"
[   42.431132] type=1400 audit(1316518060.313:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=982 comm="apparmor_parser"
[ 7775.512275] ath: Failed to wakeup in 500us
[ 7775.661458] ath: Failed to wakeup in 500us
[ 7775.783303] usb 1-4: ath9k_htc: USB layer deinitialized
[ 7786.613588] usb 1-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 7786.848562] ath9k_htc 1-4:1.0: ath9k_htc: HTC initialized with 33 credits
[ 7787.039672] ath9k_htc 1-4:1.0: ath9k_htc: FW Version: 1.3
[ 7787.039677] ath: EEPROM regdomain: 0x809c
[ 7787.039679] ath: EEPROM indicates we should expect a country code
[ 7787.039681] ath: doing EEPROM country->regdmn map search
[ 7787.039683] ath: country maps to regdmn code: 0x52
[ 7787.039685] ath: Country alpha2 being used: CN
[ 7787.039687] ath: Regpair used: 0x52
[ 7787.042081] Registered led device: ath9k_htc-phy1
[ 7787.042084] usb 1-4: ath9k_htc: USB layer initialized

```

---

### Post by lucazade on 2011-09-20
> **elzindar3 said:**
> ```
mohamad@mohamad-A780GM-A:~$ dmesg | grep ath
[   32.437152] usb 1-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   32.672991] ath9k_htc 1-4:1.0: ath9k_htc: HTC initialized with 33 credits
[   32.881972] ath9k_htc 1-4:1.0: ath9k_htc: FW Version: 1.3
[   32.881977] ath: EEPROM regdomain: 0x809c
[   32.881979] ath: EEPROM indicates we should expect a country code
[   32.881982] ath: doing EEPROM country->regdmn map search
[   32.881984] ath: country maps to regdmn code: 0x52
[   32.881986] ath: Country alpha2 being used: CN
[   32.881987] ath: Regpair used: 0x52
[   32.891824] Registered led device: ath9k_htc-phy0
[   32.891830] usb 1-4: ath9k_htc: USB layer initialized
[   32.891930] usbcore: registered new interface driver ath9k_htc
[   42.426272] type=1400 audit(1316518060.303:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=982 comm="apparmor_parser"
[   42.431132] type=1400 audit(1316518060.313:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=982 comm="apparmor_parser"
[ 7775.512275] ath: Failed to wakeup in 500us
[ 7775.661458] ath: Failed to wakeup in 500us
[ 7775.783303] usb 1-4: ath9k_htc: USB layer deinitialized
[ 7786.613588] usb 1-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 7786.848562] ath9k_htc 1-4:1.0: ath9k_htc: HTC initialized with 33 credits
[ 7787.039672] ath9k_htc 1-4:1.0: ath9k_htc: FW Version: 1.3
[ 7787.039677] ath: EEPROM regdomain: 0x809c
[ 7787.039679] ath: EEPROM indicates we should expect a country code
[ 7787.039681] ath: doing EEPROM country->regdmn map search
[ 7787.039683] ath: country maps to regdmn code: 0x52
[ 7787.039685] ath: Country alpha2 being used: CN
[ 7787.039687] ath: Regpair used: 0x52
[ 7787.042081] Registered led device: ath9k_htc-phy1
[ 7787.042084] usb 1-4: ath9k_htc: USB layer initialized

```

your problem is likely due to these:
[ 7775.661458] ath: Failed to wakeup in 500us
[ 7775.783303] usb 1-4: ath9k_htc: USB layer deinitialized
i've tried to search for it and it seems an old and known issue, haven't found anything interesting at the moment :/

EDIT:
try to power off powersaving for wlan and restart
sudo iwconfig wlan2 power off

where wlan2 is your wireless interface, in case check it with ifconfig

---

### Post by elzindar3 on 2011-09-20
ok... but what exectly the old issue is?? can you tell me briefly that old issue, what it is about??

---

### Post by elzindar3 on 2011-09-20
ok i have done your command, and then i do this again:

```

mohamad@mohamad-A780GM-A:~$ dmesg | grep ath
[   32.437152] usb 1-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   32.672991] ath9k_htc 1-4:1.0: ath9k_htc: HTC initialized with 33 credits
[   32.881972] ath9k_htc 1-4:1.0: ath9k_htc: FW Version: 1.3
[   32.881977] ath: EEPROM regdomain: 0x809c
[   32.881979] ath: EEPROM indicates we should expect a country code
[   32.881982] ath: doing EEPROM country->regdmn map search
[   32.881984] ath: country maps to regdmn code: 0x52
[   32.881986] ath: Country alpha2 being used: CN
[   32.881987] ath: Regpair used: 0x52
[   32.891824] Registered led device: ath9k_htc-phy0
[   32.891830] usb 1-4: ath9k_htc: USB layer initialized
[   32.891930] usbcore: registered new interface driver ath9k_htc
[   42.426272] type=1400 audit(1316518060.303:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=982 comm="apparmor_parser"
[   42.431132] type=1400 audit(1316518060.313:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=982 comm="apparmor_parser"
[ 7775.512275] ath: Failed to wakeup in 500us
[ 7775.661458] ath: Failed to wakeup in 500us
[ 7775.783303] usb 1-4: ath9k_htc: USB layer deinitialized
[ 7786.613588] usb 1-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 7786.848562] ath9k_htc 1-4:1.0: ath9k_htc: HTC initialized with 33 credits
[ 7787.039672] ath9k_htc 1-4:1.0: ath9k_htc: FW Version: 1.3
[ 7787.039677] ath: EEPROM regdomain: 0x809c
[ 7787.039679] ath: EEPROM indicates we should expect a country code
[ 7787.039681] ath: doing EEPROM country->regdmn map search
[ 7787.039683] ath: country maps to regdmn code: 0x52
[ 7787.039685] ath: Country alpha2 being used: CN
[ 7787.039687] ath: Regpair used: 0x52
[ 7787.042081] Registered led device: ath9k_htc-phy1
[ 7787.042084] usb 1-4: ath9k_htc: USB layer initialized

```

and also this command:

dmesg | tail -n25
```

mohamad@mohamad-A780GM-A:~$ dmesg | tail -n25
[ 7787.046781] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 7787.046783] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 7787.046786] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 7787.046789] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 7787.046792] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 7787.046794] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 7787.046797] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 7787.046800] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 7787.046803] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 7787.046805] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 7787.046808] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[ 7787.046810] cfg80211: Disabling freq 2484 MHz
[ 7787.046814] cfg80211: Regulatory domain changed to country: CN
[ 7787.046816] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 7787.046819] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 7787.046822] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 3000 mBm)
[ 7787.280825] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7790.542452] wlan0: authenticate with 5c:d9:98:b8:16:29 (try 1)
[ 7790.544859] wlan0: authenticated
[ 7790.545384] wlan0: associate with 5c:d9:98:b8:16:29 (try 1)
[ 7790.548116] wlan0: RX AssocResp from 5c:d9:98:b8:16:29 (capab=0x411 status=0 aid=1)
[ 7790.548121] wlan0: associated
[ 7790.556426] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7801.200025] wlan0: no IPv6 routers present
[ 9252.121994] usb 1-5: USB disconnect, device number 4

```

SOORY Bro, i forgot to restart... now i will restart....

---

### Post by lucazade on 2011-09-20
> **elzindar3 said:**
> ok... but what exectly the old issue is?? can you tell me briefly that old issue, what it is about??

the old issue is that wlan interface goes down, as you stated, and it is not a regression of new kernels.
have you tried that command?

---

### Post by lucazade on 2011-09-20
maybe you missed my edit before:
try to power off powersaving for wlan and restart
sudo iwconfig wlan2 power off

where wlan2 is your wireless interface, in case check it with ifconfig

---

### Post by elzindar3 on 2011-09-20
ok this the result after i had restarted the PC:

```

mohamad@mohamad-A780GM-A:~$ dmesg | grep ath
[   32.922490] usb 1-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   33.157840] ath9k_htc 1-4:1.0: ath9k_htc: HTC initialized with 33 credits
[   33.353698] ath9k_htc 1-4:1.0: ath9k_htc: FW Version: 1.3
[   33.353703] ath: EEPROM regdomain: 0x809c
[   33.353705] ath: EEPROM indicates we should expect a country code
[   33.353707] ath: doing EEPROM country->regdmn map search
[   33.353709] ath: country maps to regdmn code: 0x52
[   33.353711] ath: Country alpha2 being used: CN
[   33.353713] ath: Regpair used: 0x52
[   33.358879] Registered led device: ath9k_htc-phy0
[   33.358885] usb 1-4: ath9k_htc: USB layer initialized
[   33.358907] usbcore: registered new interface driver ath9k_htc
[   42.866458] type=1400 audit(1316528576.747:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=986 comm="apparmor_parser"
[   42.868927] type=1400 audit(1316528576.747:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=986 comm="apparmor_parser"

```

and also this command:

dmesg | tail -n25
```

mohamad@mohamad-A780GM-A:~$ dmesg | tail -n25
[   43.397245] Bluetooth: HCI socket layer initialized
[   43.397247] Bluetooth: L2CAP socket layer initialized
[   43.398169] Bluetooth: SCO socket layer initialized
[   43.401786] Bluetooth: RFCOMM TTY layer initialized
[   43.401793] Bluetooth: RFCOMM socket layer initialized
[   43.401795] Bluetooth: RFCOMM ver 1.11
[   43.420435] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   43.420440] Bluetooth: BNEP filters: protocol multicast
[   45.238684] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   45.538588] init: plymouth-stop pre-start process (1406) terminated with status 1
[   46.650508] wlan0: authenticate with 5c:d9:98:b8:16:29 (try 1)
[   46.652649] wlan0: authenticated
[   46.806993] wlan0: associate with 5c:d9:98:b8:16:29 (try 1)
[   46.810089] wlan0: RX AssocResp from 5c:d9:98:b8:16:29 (capab=0x411 status=0 aid=1)
[   46.810094] wlan0: associated
[   46.818763] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.949769] EXT4-fs (sdb5): re-mounted. Opts: errors=remount-ro,commit=0
[   57.740021] wlan0: no IPv6 routers present
[  474.143581] exe (1945): /proc/1945/oom_adj is deprecated, please use /proc/1945/oom_score_adj instead.
[  662.660044] usb 1-5: new high speed USB device number 4 using ehci_hcd
[  663.444473] Linux video capture interface: v2.00
[  663.453112] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0817)
[  663.493697] input: UVC Camera (046d:0817) as /devices/pci0000:00/0000:00:12.2/usb1/1-5/1-5:1.0/input/input12
[  663.493789] usbcore: registered new interface driver uvcvideo
[  663.493791] USB Video Class driver (v1.1.0)

```

---

### Post by lucazade on 2011-09-20
those warnings are no more present in your outputs.. well.. how it work?

---

### Post by elzindar3 on 2011-09-20
Hold on... something weird happen after i do this command:

```
mohamad@mohamad-A780GM-A:~$ gstreamer-properties

(gstreamer-properties:2342): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:2342): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]
```

My wireless and network had been disabled after i done that and here the checking commands:

```
mohamad@mohamad-A780GM-A:~$ dmesg | tail -n25
[  778.966881] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  778.966883] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  778.966886] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  778.966889] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  778.966892] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  778.966894] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  778.966897] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  778.966900] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  778.966903] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  778.966905] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[  778.966908] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  778.966911] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[  778.966914] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[  778.966916] cfg80211: Disabling freq 2484 MHz
[  778.966920] cfg80211: World regulatory domain updated:
[  778.966922] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  778.966925] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  778.966928] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  778.966931] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  778.966934] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  778.966937] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  778.972691] ath: Failed to wakeup in 500us
[  779.141079] ath: Failed to wakeup in 500us
[  779.560169] usb 1-4: ath9k_htc: USB layer deinitialized
[  779.560314] usb 1-5: USB disconnect, device number 4

mohamad@mohamad-A780GM-A:~$ dmesg | grep ath
[   32.922490] usb 1-4: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   33.157840] ath9k_htc 1-4:1.0: ath9k_htc: HTC initialized with 33 credits
[   33.353698] ath9k_htc 1-4:1.0: ath9k_htc: FW Version: 1.3
[   33.353703] ath: EEPROM regdomain: 0x809c
[   33.353705] ath: EEPROM indicates we should expect a country code
[   33.353707] ath: doing EEPROM country->regdmn map search
[   33.353709] ath: country maps to regdmn code: 0x52
[   33.353711] ath: Country alpha2 being used: CN
[   33.353713] ath: Regpair used: 0x52
[   33.358879] Registered led device: ath9k_htc-phy0
[   33.358885] usb 1-4: ath9k_htc: USB layer initialized
[   33.358907] usbcore: registered new interface driver ath9k_htc
[   42.866458] type=1400 audit(1316528576.747:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=986 comm="apparmor_parser"
[   42.868927] type=1400 audit(1316528576.747:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=986 comm="apparmor_parser"
[  778.972691] ath: Failed to wakeup in 500us
[  779.141079] ath: Failed to wakeup in 500us
[  779.560169] usb 1-4: ath9k_htc: USB layer deinitialized
```

---

### Post by elzindar3 on 2011-09-23
Bump bump!!!

---

### Post by robadamson on 2011-09-24
I have a very similar problem in 11.04 whenever I plug in my Technika webcam directly into my Toshiba laptop the wireless in disconnected and requires a reboot without the webcam to get the wireless back on also the webcam doesn't work. Funny thing though if I connect the webcam to a Belikin 4 port hub it all works fine!!!!. Totally confused. By the way the webcam comes up in lsusb as  Bus 001 Device 005: ID 0c45:62e0 Microdia MSI Starcam Racer.

---

### Post by elzindar3 on 2011-10-04
Ahaha... I had solve the problem my self.. i think the already available usb port at the backside of my PC had not enough power.  so the problem happen... After I plugin External Multi USB port... the problem is solved for time being...

Sorry If my english is not so good.. I'm from Malaysia...):P

---

