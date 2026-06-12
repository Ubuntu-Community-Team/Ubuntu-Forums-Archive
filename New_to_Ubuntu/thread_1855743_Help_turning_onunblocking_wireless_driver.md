---
title: "Help turning on/unblocking wireless driver"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by 450rOOST on 2011-10-06
I´ve been going through the other wireless thread and following along doing some of the commands but I need some of my own help. 

What do you want to know?

```
smoker@smoker-Dell-System-XPS-L502X:~$ rfkill
Usage:	rfkill [options] command
Options:
	--version	show version (0.4-1 (Ubuntu))
Commands:
	help
	event
	list [IDENTIFIER]


	block IDENTIFIER
	unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
	<idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
smoker@smoker-Dell-System-XPS-L502X:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        AC:72:89:39:62:23

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        14:FE:B5:BC:47:98

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


smoker@smoker-Dell-System-XPS-L502X:~$ 
```

```
smoker@smoker-Dell-System-XPS-L502X:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
smoker@smoker-Dell-System-XPS-L502X:~$ ^C
smoker@smoker-Dell-System-XPS-L502X:~$ 

```

```
smoker@smoker-Dell-System-XPS-L502X:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
smoker@smoker-Dell-System-XPS-L502X:~$ 

```

```
smoker@smoker-Dell-System-XPS-L502X:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
smoker@smoker-Dell-System-XPS-L502X:~$ ^C
smoker@smoker-Dell-System-XPS-L502X:~$ 

```

---

### Post by wildmanne39 on 2011-10-06
Hi, try this please:
```
sudo rmmod -f dell-laptop
```
if it does not come on post the results of this again.
```
rfkill list all
```
Thank you

---

### Post by 450rOOST on 2011-10-06
```
smoker@smoker-Dell-System-XPS-L502X:~$ sudo rmmod -f dell-laptop
smoker@smoker-Dell-System-XPS-L502X:~$ sudo rmmod -f dell-laptop
ERROR: Removing 'dell_laptop': No such file or directory
smoker@smoker-Dell-System-XPS-L502X:~$ rfkill list all
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
smoker@smoker-Dell-System-XPS-L502X:~$ 

```

yes, I entered the command you told me to twice, not sure why I did that.  Looks like the soft block was changed to 'no'.

---

### Post by wildmanne39 on 2011-10-06
Hi, please post the results of these commands if the first one does not turn it on.
```
sudo rfkill unblock all
```
```
sudo iwlist scan
```
```
dmesg | egrep 'iwl|firm|wlan0'
```
```
lsmod | grep iwl
```
```
lsmod
```
```
nm-tool
```
Thank you

---

### Post by 450rOOST on 2011-10-06
```
smoker@smoker-Dell-System-XPS-L502X:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


```

```
dmesg | egrep 'iwl|firm|wlan0'
the output was '>'
then when I tried to type a command and when I pressed enter, just another line with '>' Had to close that terminal and open another
```

```
smoker@smoker-Dell-System-XPS-L502X:~$ lsmod grep iwl
Usage: lsmod

```


```
smoker@smoker-Dell-System-XPS-L502X:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nvidia               9766978  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
lp                     13349  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  451068  2 
psmouse                59039  0 
uvcvideo               66851  0 
serio_raw              12990  0 
videodev               75143  1 uvcvideo
joydev                 17322  0 
parport                36746  3 parport_pc,ppdev,lp
iwlagn                284777  0 
iwlcore               148964  1 iwlagn
drm_kms_helper         40745  1 i915
drm                   184164  3 i915,drm_kms_helper
dell_wmi               12601  0 
mac80211              257001  2 iwlagn,iwlcore
sparse_keymap          13666  1 dell_wmi
dcdbas                 14054  0 
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
cfg80211              156212  3 iwlagn,iwlcore,mac80211
video                  18951  1 i915
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  4 
libahci                25548  1 ahci
r8169                  46630  0 
xhci_hcd               72190  0 

```

```
smoker@smoker-Dell-System-XPS-L502X:~$ nm-tool

NetworkManager Tool

State: connected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        AC:72:89:39:62:23

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        14:FE:B5:BC:47:98

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


```

THANKS!!!!!!!!

---

### Post by wildmanne39 on 2011-10-06
Hi, it makes it hard when some of the commands do not work, please just copy and paste the commands, let's try this.

Please do:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0:
```
rmmod -r iwlagn
rfkill unblock all
modprobe iwlagn
```
Proofread carefully, save and close gedit. Reboot and tell us if it's working as expected.
Thank you

---

### Post by 450rOOST on 2011-10-06
Roger on the copy/paste.

is this correct, what do you mean without sudo?

[IMG]http://i678.photobucket.com/albums/vv143/RideRed/WirelessHelp.png[/IMG]

---

### Post by wildmanne39 on 2011-10-06
Hi, that looks correct.
Thank you

---

### Post by 450rOOST on 2011-10-06
were still blocked

```
smoker@smoker-Dell-System-XPS-L502X:~$ rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
3: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
smoker@smoker-Dell-System-XPS-L502X:~$ 

```

---

### Post by wildmanne39 on 2011-10-06
Hi, disconnect your wired connection and restart your computer, if it does not come on see if it will turn on with the key.
Thank you

---

### Post by 450rOOST on 2011-10-06
> **wildmanne39 said:**
> Hi, disconnect your wired connection and restart your computer, if it does not come on see if it will turn on with the key.
Thank you


ok, what do you mean by turn on with key?

Thanks.

---

### Post by wildmanne39 on 2011-10-06
Hi there is a key like fn f5 or a button or switch on the laptop that turns it on or off.
Thank you

---

### Post by 450rOOST on 2011-10-07
did another reboot without the cable and it's working.  

Thanks again, very grateful for your help

---

### Post by wildmanne39 on 2011-10-07
Hi, your welcome! I am glad we go it fixed.

---

