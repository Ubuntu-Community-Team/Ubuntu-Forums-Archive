---
title: "NOOB status: Configure wireless card for Ubuntu 11.10"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by ibthevivin on 2012-01-05
I'm completely new to Linux and I've been playing around with it for  about 2 days. I've picked up on some things pretty quick, but I just  can't seem to understand how to install the appropriate drivers for the  wireless card I've installed. 

Currently the proprietary drivers are installed and I have slow web  browsing performance. What would be the appropriate fix? Installing  drivers meant for my wireless card (Intel Centrino 6230) or are the  proprietary drivers enough but something else is slowing my web  performance?

My dad is running quick on Windows 7 but I'm slower since I've switched.

For the record, I've been to [www.intellinuxwireless.org]("http://www.intellinuxwireless.org/")  and found the specific drivers for my card, but I'm unsure of how to  install tar.gz files. Am I supposed to use the terminal? If so, how (if  someone could provide me a good instructional website)?

---

### Post by chipbuster on 2012-01-05
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)  I'm guessing this is what you'll need to do.  If you enter the command with "configure" in it and the shell spits back an error, try just going to the next step (make). Some drivers come without a configure script.  Also, before you do anything, make sure to take a look at the readme and post back if anything doesn't make sense. Some drivers require you to change options in some files before installing.

---

### Post by sandyd on 2012-01-05
> **ibthevivin said:**
> I'm completely new to Linux and I've been playing around with it for  about 2 days. I've picked up on some things pretty quick, but I just  can't seem to understand how to install the appropriate drivers for the  wireless card I've installed. 

Currently the proprietary drivers are installed and I have slow web  browsing performance. What would be the appropriate fix? Installing  drivers meant for my wireless card (Intel Centrino 6230) or are the  proprietary drivers enough but something else is slowing my web  performance?

My dad is running quick on Windows 7 but I'm slower since I've switched.

For the record, I've been to [www.intellinuxwireless.org]("http://www.intellinuxwireless.org/")  and found the specific drivers for my card, but I'm unsure of how to  install tar.gz files. Am I supposed to use the terminal? If so, how (if  someone could provide me a good instructional website)?
Are you broadcasting on N or G.
If your broadcasting on N, kill it, and sink to G-level speeds. That card doesn't work well with N specs.

---

### Post by ibthevivin on 2012-01-06
@Chipbuster: I'll get back to you on that and let you know. I'm reading the README file and responding to daniweb.com users on their feedback and I'll let you know what I don't understand. 

@sandyd: My network's perfect. I rarely have a down connection and I've several shared devices. The router broadcasts a mixed signal in 2.4ghz on a low traffic channel. I never had issues with this card but since I've moved to Ubuntu 11.10 when I stream videos, it seems to need to buffer every other minute. So my goal here is to try a driver made for the card and learn how to install drivers. 

So two birds, one stone. Learn to install drivers and try and resolve the issue with my card. 

What makes you say this card doesn't work well with N-specs?

Thank you both for your responses.

---

### Post by ibthevivin on 2012-01-06
> **chipbuster said:**
> [http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)  I'm guessing this is what you'll need to do.  If you enter the command with "configure" in it and the shell spits back an error, try just going to the next step (make). Some drivers come without a configure script.  Also, before you do anything, make sure to take a look at the readme and post back if anything doesn't make sense. Some drivers require you to change options in some files before installing.

Stupid question. Is this assuming the file is located on the desktop, in the home folder, or documents? Where? Or does it not matter (if so, why?)?

Thanks again!

---

### Post by wildmanne39 on 2012-01-07
Hi, > What makes you say this card doesn't work well with N-specs?
because of working in networking I can confirm intel cards have trouble with N speed in linux but unless you have a real fast connection above 54 it will not matter and we can disable that module in the driver and you should have improved speed.

I believe I know the driver you are using but I want to make sure please post the results of:
```
lspci -nnk | grep -iA2 net
```
if you want to get the speed fixed the  best it can be in linux until the driver is redone.
Thanks

---

### Post by ibthevivin on 2012-01-07
Don't thank me. I should be thanking you.

The results were:

```
ibthevivin@Cronos:~$ lspci -nnk | grep -A2 net
02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:0364]
	Kernel driver in use: atl1c

```

I noticed that the card has a connect speed of 54mbps (which used to be +/-120mpbs before I switched to Ubuntu) and when streaming video it disconnects and reconnects. 

Thanks!

---

### Post by wildmanne39 on 2012-01-07
Hi, your wireless card did not show up only the wired connection, was that all the information?
Please double check if it was try these three commands:
```
lsusb
```
```
lspci -nn
```
```
sudo pccardctl ident
```
Thanks

---

### Post by ibthevivin on 2012-01-07
Yup. That was all the information. For that prior command.

The last command you had me run didn't yield anything. As you can see it did ask for password though.

So assuming from your responses, I guess installing the drivers provided in intellinuxwireless.org wouldn't do anything? lol

Thank you! 

```
ibthevivin@Cronos:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 003: ID 8086:0189 Intel Corp. 
Bus 002 Device 004: ID 0402:9665 ALi Corp. 
Bus 002 Device 005: ID 045e:075d Microsoft Corp. LifeCam Cinema

```
```

ibthevivin@Cronos:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 18)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 18)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
02:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
04:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 05)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 05)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 05)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 05)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 05)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 05)

```
```

ibthevivin@Cronos:~$ sudo pccardctl ident
[sudo] password for ibthevivin: 
ibthevivin@Cronos:~$ 

```

---

### Post by wildmanne39 on 2012-01-07
Hi, the card showed up, please post output of:
```
lsmod
```
this will confirm if the driver is loading properly.
Thanks

---

### Post by ibthevivin on 2012-01-08
Where did you learn all this?!? lol Does your occupation involve much of Linux based coding?

Thanks!

```
ibthevivin@Cronos:~$ lsmod
Module                  Size  Used by
snd_usb_audio         118064  0 
snd_usbmidi_lib        25371  1 snd_usb_audio
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
hidp                   22862  1 
hid                    95463  1 hidp
bnep                   18436  2 
rfcomm                 47946  8 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282548  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
binfmt_misc            17540  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
keucr                  85590  0 
btusb                  18600  4 
bluetooth             166112  28 hidp,bnep,rfcomm,btusb
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
usb_storage            57901  1 
snd_pcm                96714  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uas                    18027  0 
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
iwlagn                314213  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  566827  9 
snd_timer              29991  2 snd_pcm,snd_seq
drm_kms_helper         42558  1 i915
drm                   236290  5 i915,drm_kms_helper
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13423  1 i915
acer_wmi               23948  0 
snd                    68266  16 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap          13890  1 acer_wmi
video                  19412  1 i915
wmi                    19256  1 acer_wmi
soundcore              12680  1 snd
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
joydev                 17693  0 
psmouse                73882  0 
serio_raw              13166  0 
intel_ips              18089  0 
mac80211              462092  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211
mei                    41480  0 
ahci                   26002  2 
libahci                26861  1 ahci
atl1c                  41643  0 

```

Tell me a little bit of what I'm reading here. I understand it sorta. So the "module" is the device or driver? "Used by" meaning what?

Thank  you again. This is a great learning experience. I don't want to be totally reliant. This was the whole purpose of moving to Linux. lol

---

### Post by alexandari on 2012-01-08
An unexplainable fix to most wireless problems (I won't go into details) is being fixed with (for example for me) WICD network manager. You can give it a try,you can install it via the package manager,nothing complicated. The only thing that you have to add manually is the **wireless interface** in the Preferences,which should be **wlan0** (you have to type it) ,tell me how it went,cheers

++ Here's an exact screenshot if I got you confused with my explanation [http://4.bp.blogspot.com/-FgQHVo9XFIw/ThrMfJP_6VI/AAAAAAAAAdk/JDrbWMuXNsI/s1600/wicd-preferences.png](http://4.bp.blogspot.com/-FgQHVo9XFIw/ThrMfJP_6VI/AAAAAAAAAdk/JDrbWMuXNsI/s1600/wicd-preferences.png)

---

### Post by ibthevivin on 2012-01-08
I barely understood that! lol. But I got it. I downloaded the manager via Synaptic and opened up the wizard. So what does this do anyways? Got any idea? You said it was an odd fix.

I'll let you know how it affects my network performance and if my wireless is still dropping signal.

---

### Post by wildmanne39 on 2012-01-08
Hi, the information you posted shows all the drivers in use on your system, and the driver is loaded for your wireless card there are two things most likely going on by looking at your information, we need to disable N speed and you may have a problem with the kernel telling the wireless to turn on, so we need to check for that as well.

Everything I have learned is from working on the forum, spending hours and hours of studying and research.

Please do this for the N speed issue.
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
add one line:
```
options iwlagn 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot.

If it does not come on post:
```
iwconfig
rfkill list all
nm-tool
```
Thanks

---

### Post by ibthevivin on 2012-01-08
These are the results. The speeds are still the same. It started off lower but worked its way up to 54mbps.

```
ibthevivin@Cronos:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"742 Evergreen Terr"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 30:46:9A:00:F2:0C   
          Bit Rate=5.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:45   Missed beacon:0

ibthevivin@Cronos:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
ibthevivin@Cronos:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        20:6A:8A:2C:07:06

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [742 Evergreen Terr] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        88:53:2E:28:13:88

  Capabilities:
    Speed:           5 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    QCRL1:           Infra, 00:1F:90:E9:AA:26, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WEP
    D5136:           Infra, 00:1F:90:BE:F7:1C, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WEP
    NETGEAR:         Infra, A0:21:B7:A4:B3:14, Freq 2417 MHz, Rate 54 Mb/s, Strength 17 WPA2
    UWC88:           Infra, 00:1F:90:E1:C0:1F, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WEP
    belkin.d6f:      Infra, 08:86:3B:23:4D:6F, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    *742 Evergreen Terr: Infra, 30:46:9A:00:F2:0C, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA2
    HomeHUB:         Infra, C0:C1:C0:97:F4:EF, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


ibthevivin@Cronos:~$ 

```

---

### Post by wildmanne39 on 2012-01-08
Hi, change your settings to match the screenshots except leave yours to auto connect then reboot.

---

