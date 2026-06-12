---
title: "bluetooth not working in ubuntu"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by arai on 2013-03-07
Bluetooth does not work for ubuntu. Please help me. I have a normal sony ericsson phone. i want to transfer mp3 files from my system to cell phone.

please help me. thanks in advance.

I am using ubuntu 12.04 LTS

---

### Post by jazzpi on 2013-03-07
Could you tell us how exactly you are trying to transfer the files?
Are you able to connect to the phone at all, or even to any other bluetooth device?
Just give some sort of more detailed information of what you're doing, posts like "HELP ME!!!" won't get solved too quickly...

---

### Post by arai on 2013-03-07
> **jazzpi said:**
> Could you tell us how exactly you are trying to transfer the files?
Are you able to connect to the phone at all, or even to any other bluetooth device?
Just give some sort of more detailed information of what you're doing, posts like "HELP ME!!!" won't get solved too quickly...


phone shows bluetooth icon. system show bluetooth on.

when i copy mp3 file to mobile folder the window closes or says cannot send file.

thanks.

---

### Post by gordintoronto on 2013-03-07
Tell us about your computer? Are you sure it supports Bluetooth? If so, how?

---

### Post by arai on 2013-03-09
> **gordintoronto said:**
> Tell us about your computer? Are you sure it supports Bluetooth? If so, how?


Yes it worked before when i had windows. It's a lenovo laptop. It has bluetooth.

---

### Post by arai on 2013-03-10
It's lenovo B560

---

### Post by varunendra on 2013-03-10
> **arai said:**
> when i copy mp3 file to mobile folder...
So are you able to 'view' the mobile's folders on your laptop?
Could you show us a screenshot of the "Bluetooth Settings" window while it is On ?

Please post outputs of -
```
usb-devices
lsmod
dmesg | grep -i bluetooth
```

---

### Post by arai on 2013-03-12
[IMG]http://i.imgur.com/TysihyV.png[/IMG]

---

### Post by arai on 2013-03-12
Please see this snapshot. It shows an error when the mp3 file is sent to the mobile phone.

[IMG]http://i.imgur.com/lk2gGd9.jpg[/IMG]

---

### Post by varunendra on 2013-03-12
If I am to believe what the 2nd screenshot you posted suggests, then it most probably is an authentication/permission issue on the mobile phone side.

Can you remove the phone from blueman, then re-associate it again? If yes then double check the settings in your mobile phone.
However, if the problem is on the system side, then I suspect you won't be able to even discover the phone once removed from blueman (the graphical interface in the screenshot).

In that case, I have a very crude workaround that I have used on my own lappy to make bt work.

But in order to try that or anything, please post the command outputs again (simple copy-paste from terminal would be much better) as the screenshot you posted doesn't have the full output, as you may notice yourself.

---

### Post by techvish81 on 2013-03-13
go to personal file sharing from the dash and allow bluetooth sharing by marking related check boxes and you are good to go!

cheers!

---

### Post by varunendra on 2013-03-13
> **techvish81 said:**
> go to personal file sharing from the dash and allow bluetooth sharing by marking related check boxes and you are good to go!
Good idea, just a bit of clarification -

That option is meant for making only the contents of "Public" folder viewable from an external device, like mobile phone. In other words, it facilitates 'Pulling' of files from the Public folder. While the OP is trying to 'Push' the files into the mobile, which doesn't need that option enabled (for example I have it disabled and still I can copy 'Any' file to my cheap mobile phone over bluetooth).

Without that sharing enabled, the contents of the Public folder can't be viewed from the mobile, but after enabling it they can be.

Although if there is a connectivity issue, it won't help. But if it is just a permission issue on mobile side, then it should. (desired files would have to be copied in the Public folder first, then they can be viewed and copied from within the mobile phone.)

---

### Post by techvish81 on 2013-03-13
you are right but strangely, it has helped many times to me and many others !!!!

---

### Post by arai on 2013-03-13
g1@g1-Lenovo-B560:~$ usb - devices
No command 'usb' found, did you mean:
 Command 'jsb' from package 'jsonbot' (universe)
 Command 'sb' from package 'lrzsz' (universe)
usb: command not found
g1@g1-Lenovo-B560:~$ clear

g1@g1-Lenovo-B560:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-38-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e00d Rev=04.72
S:  Manufacturer=Broadcom Corp
S:  Product=Broadcom Bluetooth 2.1 Device
S:  SerialNumber=3859F9CC8907
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c7a ProdID=0801 Rev=01.00
S:  Manufacturer=Generic
S:  Product=FingerPrinter Reader
S:  SerialNumber=00000000000006
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=5986 ProdID=a002 Rev=14.07
S:  Manufacturer=Bison Corp.
S:  Product=Lenovo EasyCamera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=128mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-38-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
g1@g1-Lenovo-B560:~$ ^C
g1@g1-Lenovo-B560:~$ clear

g1@g1-Lenovo-B560:~$ usb-devices

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-38-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1a.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=e0(wlcon) Sub=01 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0489 ProdID=e00d Rev=04.72
S:  Manufacturer=Broadcom Corp
S:  Product=Broadcom Bluetooth 2.1 Device
S:  SerialNumber=3859F9CC8907
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 1 Alt= 0 #EPs= 2 Cls=e0(wlcon) Sub=01 Prot=01 Driver=btusb
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 0 Cls=fe(app. ) Sub=01 Prot=01 Driver=(none)

T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1c7a ProdID=0801 Rev=01.00
S:  Manufacturer=Generic
S:  Product=FingerPrinter Reader
S:  SerialNumber=00000000000006
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

T:  Bus=01 Lev=02 Prnt=02 Port=05 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=5986 ProdID=a002 Rev=14.07
S:  Manufacturer=Bison Corp.
S:  Product=Lenovo EasyCamera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=128mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.02
S:  Manufacturer=Linux 3.2.0-38-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:1d.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=8087 ProdID=0020 Rev=00.00
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
g1@g1-Lenovo-B560:~$ 

second command result

g1@g1-Lenovo-B560:~$ lsmod
Module                  Size  Used by
irda                  185517  0 
crc_ccitt              12627  1 irda
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  16 
joydev                 17393  0 
snd_hda_codec_realtek   174313  1 
acer_wmi               23612  0 
snd_hda_intel          32765  5 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                86520  0 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
intel_ips              17822  0 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  17948  2 
bluetooth             158479  23 bnep,rfcomm,btusb
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
ath9k                 117356  0 
mac80211              436493  1 ath9k
ideapad_laptop         17890  0 
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
ath9k_common           13781  1 ath9k
ath9k_hw              391626  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178877  3 ath9k,mac80211,ath
snd                    62218  18 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  423451  9 
mac_hid                13077  0 
wmi                    18744  1 acer_wmi
drm_kms_helper         45466  1 i915
drm                   197641  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
mei                    36570  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0 
g1@g1-Lenovo-B560:~$ 

third command result

g1@g1-Lenovo-B560:~$ dmesg | grep -i bluetooth
[   17.942942] Bluetooth: Core ver 2.16
[   17.942995] Bluetooth: HCI device and connection manager initialized
[   17.942998] Bluetooth: HCI socket layer initialized
[   17.943000] Bluetooth: L2CAP socket layer initialized
[   17.943006] Bluetooth: SCO socket layer initialized
[   17.943388] Bluetooth: Generic Bluetooth USB driver ver 0.6
[   18.854727] Bluetooth: RFCOMM TTY layer initialized
[   18.854733] Bluetooth: RFCOMM socket layer initialized
[   18.854735] Bluetooth: RFCOMM ver 1.11
[   18.859210] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.859213] Bluetooth: BNEP filters: protocol multicast
g1@g1-Lenovo-B560:~$

---

