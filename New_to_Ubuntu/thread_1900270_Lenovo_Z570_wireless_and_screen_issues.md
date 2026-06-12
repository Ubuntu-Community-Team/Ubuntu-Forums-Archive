---
title: "Lenovo Z570 wireless and screen issues"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by sideffects on 2011-12-25
Okay. After much hassle and a lot of weird partitioning, and reinstalling GRUB 2, I finally have Ubuntu dualbooting with Windows 7. Now, there are a couple of issues that I'm hurting my brain trying to resolve. First is the wireless card issue. I have to enable it everytime I boot up by using:

```
sudo modprobe acer_wmi
sudo modprobe -r acer_wmi
```

I tried a couple of things I found online to try and make it permanent, but they didn't work, so how can I make this permanent?

Another issue that I'm having is that when I close the lid, or when the system dims the screen it won't come back on. At all. I have to hold the power button down and reboot. Any suggestions? Thanks in advance for the help!

---

### Post by shovenose on 2011-12-25
Does this apply for the IdeaPad V570 as well?
As far as the screen, I was having a similar problem with Ubuntu 10.10 PPC on my PowerBook G4.
Waking it up using the Brightness Up key works while waking it up from the trackpad doesn't work reliably.
Hope this helps.
-shovenose

---

### Post by sideffects on 2011-12-25
> **shovenose said:**
> Does this apply for the IdeaPad V570 as well?
As far as the screen, I was having a similar problem with Ubuntu 10.10 PPC on my PowerBook G4.
Waking it up using the Brightness Up key works while waking it up from the trackpad doesn't work reliably.
Hope this helps.
-shovenose
I tried the brightness up key to no avail :(

EDIT: I did get the Wireless working properly! Still having a problem with the screen dimness, though.

---

### Post by wildmanne39 on 2011-12-25
Hi, please post the results of the following commands:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by shovenose on 2011-12-25
```
michel@Lenovo-V570:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
michel@Lenovo-V570:~$ ^C

```
```

michel@Lenovo-V570:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
usb0      no wireless extensions.

michel@Lenovo-V570:~$ 

```
```

michel@Lenovo-V570:~$ lsmod
Module                  Size  Used by
rndis_host             13848  0 
cdc_ether              13536  1 rndis_host
usbnet                 26212  2 rndis_host,cdc_ether
usb_storage            57901  0 
uas                    18027  0 
prism2_usb            214370  0 
rt73usb                31735  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20830  1 rt73usb
rt2x00lib              50325  2 rt73usb,rt2x00usb
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
joydev                 17693  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
rts5139               351143  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
psmouse                73882  0 
v4l2_compat_ioctl32    17083  1 videodev
serio_raw              13166  0 
iwlagn                314213  0 
mac80211              462092  3 rt2x00usb,rt2x00lib,iwlagn
i915                  566827  3 
soundcore              12680  1 snd
drm_kms_helper         42558  1 i915
cfg80211              199587  4 prism2_usb,rt2x00lib,iwlagn,mac80211
mei                    41480  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  52788  0 
ahci                   26002  3 
libahci                26861  1 ahci
michel@Lenovo-V570:~$ 


```

---

### Post by wildmanne39 on 2011-12-25
Hi shovenose, please post all the commands in my post so I can see what drivers and wireless card you have and a few other things.
Also are you able to get your wireless to come on like the original poster?
Thanks

---

### Post by shovenose on 2011-12-26
Thank you I posted some more! (Refresh page I added to my post with an edit)

---

### Post by wildmanne39 on 2011-12-26
Hi, you do not have the same problem as the original poster.

Please show:
```
lspci -nnk | grep -iA2 net
lsusb
```
Are you wanting to use the usb adapter or the internal? I see a driver for an internal card but I need the information from the commands to put more of the pieces together.
Thanks

---

### Post by shovenose on 2011-12-26
Oh sorry, I tried a Netgear Wireless and a TP-Link Wireless USB card but neither worked...
Right now I'm using my Phone USB tethered, (the phone is connected to my wifi lol)

I don't want to use the extrernal USB adapters, I want to use internal.
Let me get that info for u just a sec :)
```

michel@Lenovo-V570:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)
    Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1315]
    Kernel driver in use: iwlagn
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
michel@Lenovo-V570:~$ 


```
```

michel@Lenovo-V570:~$ lsusb
Bus 001 Device 008: ID 0bb4:0ffe High Tech Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 8087:07d7 Intel Corp. 
Bus 001 Device 004: ID 5986:0364 Acer, Inc 
Bus 002 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
michel@Lenovo-V570:~$ 


```

---

### Post by wildmanne39 on 2011-12-26
Hi, alright we are going to blacklist a driver and load another and hopefully it will work if not we may need to set some parameters for the driver.

```
sudo su
echo "blacklist rt73usb" >> /etc/modprobe.d/blacklist.conf

``` 
Then:
```
sudo modprobe iwlagn 
```
Thanks

---

### Post by shovenose on 2011-12-26
OK I did that.
It still says Disabled By Hardware Switch :(

---

### Post by wildmanne39 on 2011-12-26
Hi, let's see how everything looks now that we blacklisted the driver, please run the commands with the wire connection unplugged.
```
rfkill list all
sudo rfkill unblock all
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wmi -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by shovenose on 2011-12-26
> **wildmanne39 said:**
> Hi, let's see how everything looks now that we blacklisted the driver, please run the commands with the wire connection unplugged.
```
rfkill list all
sudo rfkill unblock all
lsmod | grep iwl
``````
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wmi -e wpa -e wlan -e etork | tail -n55
```Thanks
ok 1 minute plz

---

### Post by shovenose on 2011-12-26
```

michel@Lenovo-V570:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
michel@Lenovo-V570:~$ sudo rfkill unblock all
[sudo] password for michel: 
michel@Lenovo-V570:~$ lsmod | grep iwl
iwlagn                314213  0 
mac80211              462092  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
michel@Lenovo-V570:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wmi -e wpa -e wlan -e etork | tail -n55
Dec 25 21:41:48 Lenovo-V570 kernel: [   14.483113] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Dec 25 21:41:48 Lenovo-V570 kernel: [   14.483422] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
Dec 25 21:41:48 Lenovo-V570 kernel: [   14.516549] wmi: Mapper loaded
Dec 25 21:41:48 Lenovo-V570 kernel: [   14.672721] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
Dec 25 21:41:48 Lenovo-V570 kernel: [   14.675200] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]: <info> (wlan0): now managed
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]: <info> (wlan0): bringing up device.
Dec 25 21:41:48 Lenovo-V570 NetworkManager[949]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.211209] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.211214] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.211318] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.211367] iwlagn 0000:02:00.0: setting latency timer to 64
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.211451] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.221954] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.221958] iwlagn 0000:02:00.0: Device SKU: 0X9
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.221960] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.223071] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.223357] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.266275] wmi: Mapper loaded
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.439949] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
Dec 25 21:43:56 Lenovo-V570 kernel: [   14.442214] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]: <info> (wlan0): now managed
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]: <info> (wlan0): bringing up device.
Dec 25 21:43:56 Lenovo-V570 NetworkManager[926]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 25 21:45:40 Lenovo-V570 NetworkManager[926]: <info> (wlan0): now unmanaged
Dec 25 21:45:40 Lenovo-V570 NetworkManager[926]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Dec 25 21:45:44 Lenovo-V570 NetworkManager[926]: <info> (wlan0): now managed
Dec 25 21:45:44 Lenovo-V570 NetworkManager[926]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 25 21:45:44 Lenovo-V570 NetworkManager[926]: <info> (wlan0): bringing up device.
Dec 25 21:45:44 Lenovo-V570 NetworkManager[926]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 25 21:46:39 Lenovo-V570 NetworkManager[926]: <info> (wlan0): now unmanaged
Dec 25 21:46:39 Lenovo-V570 NetworkManager[926]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Dec 25 21:54:14 Lenovo-V570 kernel: [  183.151000] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x1ff)
Dec 25 21:54:14 Lenovo-V570 kernel: [  183.151039] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd0500004)
Dec 25 21:54:14 Lenovo-V570 kernel: [  183.151047] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Dec 25 21:54:14 Lenovo-V570 kernel: [  183.151058] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
Dec 25 21:54:14 Lenovo-V570 kernel: [  183.151836] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.
Dec 25 21:54:18 Lenovo-V570 NetworkManager[926]: <info> (wlan0): now managed
Dec 25 21:54:18 Lenovo-V570 NetworkManager[926]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 25 21:54:18 Lenovo-V570 NetworkManager[926]: <info> (wlan0): bringing up device.
Dec 25 21:54:18 Lenovo-V570 NetworkManager[926]: <info> (wlan0): deactivating device (reason 'managed') [2]
michel@Lenovo-V570:~$ 

```

---

### Post by wildmanne39 on 2011-12-26
Hi, I am about to get off of here for tonight because I am very tired but a hard block is usually caused by a physical switch being off and can be turned on by the switch on the computer or a combination of fn f12 for example, you may have to look at your documentation for your computer to find out which method turns it on, and there may be an issue after that but we need to get the hardblock removed before we will know for sure.
Thanks

---

### Post by sideffects on 2011-12-26
So...any ideas about the screen not coming back on?

---

### Post by sideffects on 2011-12-26
Okay, so there is a bug for my Intel on-board graphics card. The workaround is to remove gnome-screensaver and to install xscreensaver. Works like a charm! [http://www.liberiangeek.net/2011/10/enable-screensavers-in-ubuntu-11-10-oneiric-ocelot/]("http://www.liberiangeek.net/2011/10/enable-screensavers-in-ubuntu-11-10-oneiric-ocelot/")

---

### Post by shovenose on 2011-12-26
Well, looks like my screensaver is buggy too. I failed to wake up my laptop this morning.
Since I have no wireless internet I can't install anything (unless I remove the ethernet cable from my other computer...
I'll install that Xscreensaver thing when I have internet...

@wildmanne39, my HP netbook running Lubuntu 11.10 has a similar problem where it sometimes says it's disabled by hardware switch and I have to move the switch for wifi on the computer back and forth a few times to make it work (and sometimes have to restart completely)...
That seems to be a similar problem here. Because when I do  Fn+F5 (it has the wireless icon) nothing happens. If I do it a bunch of times nothing happens. Then there's the other actual hardware wireless switch on the front, that doesn't do anything either.
I know the wireless is functional as it worked in Windows 7 a week ago lol.

Thanks for all the help and hopefully you'll have some more insights :D

---

### Post by wildmanne39 on 2011-12-26
Hi, we need to add the parameter to the driver and go from there:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
Add a single line:
```
options iwlagn 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by shovenose on 2011-12-26
That made absolutely no difference, sorry. More ideas?

---

### Post by wildmanne39 on 2011-12-26
Hi, run this:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
copy the contents here please also since you have made that change post the information from the commands in 13 again.
Thanks

---

### Post by shovenose on 2011-12-26
That conf file you had me edit was actually empty until I added that thing to it, just to let you know.
I'll update this thread shortly with the neccesary information, thank you for your time and patience and please bear with me in my linux noobery (well, I can run a GUI-less server but I can't get my internet working on Ubuntu :( )

---

### Post by wildmanne39 on 2011-12-26
Hi, that is okay it should have been empty.
Thanks

---

### Post by shovenose on 2011-12-26
Here are more than you wanted :)
```

michel@Lenovo-V570:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
michel@Lenovo-V570:~$ sudo rfkill unblock all
[sudo] password for michel: 
michel@Lenovo-V570:~$ lsmod | grep iwl
iwlagn                314213  0 
mac80211              462092  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
michel@Lenovo-V570:~$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wmi -e wpa -e wlan -e etork | tail -n55
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]: <info> (wlan0): now managed
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]: <info> (wlan0): bringing up device.
Dec 26 20:07:23 Lenovo-V570 NetworkManager[924]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.363637] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.363640] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.363741] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.363806] iwlagn 0000:02:00.0: setting latency timer to 64
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.363881] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.374742] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.374745] iwlagn 0000:02:00.0: Device SKU: 0X9
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.374747] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.378638] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.378993] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.390638] wmi: Mapper loaded
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.528566] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
Dec 26 20:11:52 Lenovo-V570 kernel: [   14.530927] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]: <info> (wlan0): now managed
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]: <info> (wlan0): bringing up device.
Dec 26 20:11:52 Lenovo-V570 NetworkManager[887]: <info> (wlan0): deactivating device (reason 'managed') [2]
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.043151] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.043154] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.043243] iwlagn 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.043283] iwlagn 0000:02:00.0: setting latency timer to 64
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.043354] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.054001] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.054005] iwlagn 0000:02:00.0: Device SKU: 0X9
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.054007] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.054229] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.054463] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.081330] wmi: Mapper loaded
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.173609] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
Dec 26 20:13:20 Lenovo-V570 kernel: [   14.175970] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]: <info> monitoring kernel firmware directory '/lib/firmware'.
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]: <info> (wlan0): now managed
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]: <info> (wlan0): bringing up device.
Dec 26 20:13:20 Lenovo-V570 NetworkManager[926]: <info> (wlan0): deactivating device (reason 'managed') [2]
michel@Lenovo-V570:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        40:25:C2:2E:FF:58

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:5C:A1:D3

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1


michel@Lenovo-V570:~$ 

```

---

### Post by wildmanne39 on 2011-12-26
Hi, I know of one last thing to try so here goes.

Please do:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit:
```
rmmod -f iwlagn
rfkill unblock all
modprobe iwlagn
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

---

### Post by shovenose on 2011-12-27
Nope, it still says "wireless is disabled by hardware switch"

---

### Post by shovenose on 2011-12-27
Well I might go back to XP 64-bit...
because while I love 7 it was a bit slow :(

---

### Post by wildmanne39 on 2011-12-27
Hi, this is going to sound strange but some people say they have got rid of the hardblock by going into windows and then pressing the switch or keys that turn it on or off and then they boot back into ubuntu and it works but I believe there is another issue I think there is a bug I just have not found it yet.
Thanks

---

### Post by jpotvin on 2012-03-24
Hello, I have an individual instance question, and a broad community question about this issue. First the broad community question...

1. It appears from my web wanderings about this issue I'm experiencing on a newly-aquired Lenovo z570 that the Ocelot release has introduced wireless network loss to quite a few users, for several months. This thread is about the Lenovo z570 (which I am currently trying to diagnose) but I reckon I now have an explanation for why the wireless cut out some months ago when I updated an Acer Aspire 540 to 11.04.  I've come to know Ubuntu as the most glitch-free distro for years. So what is it that is leaving the wireless problems unresolved for many months as simple updates to the the Ocelot distro? I ran an update to make sure I have all the recent fixes, and yet I still have to fix something as basic as wireless this way. (Some nostalgia for other earlier Linux distros, is what I feel.)

2. My individual case:  From the present thread I did manage to get a functioning wireless connection on my Lenovo z570 with 
```

sudo modprobe acer_wmi
sudo modprobe -r acer_wmi

```Thanks for that. Hmm, how about inserting that into a startup script as a once-only workaround until the source of the problem is figured out by the Ubuntu developer community?

Following the info in this thread from wildmanne39 I ran the following diagnosis. Can you suggest exactly what you think I ought to do to resolve my case?

```

jpotvin@jpotvin-Ideapad:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

jpotvin@jpotvin-Ideapad:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux jpotvin-Ideapad 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

jpotvin@jpotvin-Ideapad:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux jpotvin-Ideapad 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
jpotvin@jpotvin-Ideapad:~$ ^C
jpotvin@jpotvin-Ideapad:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlagn
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169

jpotvin@jpotvin-Ideapad:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

jpotvin@jpotvin-Ideapad:~$ rfkill list all
0: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

jpotvin@jpotvin-Ideapad:~$ lsmod
Module                  Size  Used by
usb_storage            57901  1 
uas                    18027  0 
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330815  1 
binfmt_misc            17540  1 
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61475  1 vfat
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17693  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
rts5139               351143  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18600  2 
bluetooth             166112  23 bnep,rfcomm,btusb
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
wmi                    19256  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                314257  0 
mac80211              462046  1 iwlagn
psmouse                73882  0 
serio_raw              13166  0 
i915                  571251  2 
cfg80211              199630  2 iwlagn,mac80211
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  3 
libahci                26861  1 ahci
r8169                  52788  0 

```

---

### Post by jpotvin on 2012-03-24
So, here's an elegant workaround that works on my z570...

In terminal:
```

sudo gedit /etc/rc.local

``` 

In gedit:
```

sudo modprobe acer_wmi
sudo modprobe -r acer_wmi

```

Save. Reboot. Done. Wireless now working on boot-up.

Thanks to others for the guidance towards this.

---

