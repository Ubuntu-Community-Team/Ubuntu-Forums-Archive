---
title: "Wireless Connection Issues"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Corvid133 on 2012-05-17
Hi all,

I am a total linux newbie, having bought a second-hand desktop, and done a complete install of 12.04.  Navigating my way around and picking things up as I go, and so far I am liking ubuntu and finding it very useful.

Thing is, I have developed connection problems to my wireless network (admittedly after running the inbuilt System Testing program by mistake).  The wireless network symbol will start to cycle through as it tries to re-acquire my network, and the connection will fail, or it will ask me over and over for the network password.

When I do get a connection, it's running at very slow speeds (it got down to 1mb/s earlier), whilst my laptop (running windows) zips along with no problems at all, so clearly the problem lies with my desktop.

So - question: Is it the hardware or the software, do we think?  And what can I do about it?

I'd be very grateful for any and all input.

Thank you

---

### Post by Lisiano on 2012-05-17
Let's assume it's software. To eliminate hardware, boot into a LiveCD and try it there. Also please show us the output of these commands (Not while using the LiveCD)
```
lspci
```
```
lsusb
```
```
dmesg | tail -n 20
```
```
lsmod | sort
```

Please use the code tags (The hash (#) button) to display the output

---

### Post by Corvid133 on 2012-05-17
Hello and thank you.

I'll try the live CD in the morning, but in the meantime, here are the outputs:

lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. CN896/VN896/P4M900 I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Security Device
00:00.7 Host bridge: VIA Technologies, Inc. CN896/VN896/P4M900 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:03.0 PCI bridge: VIA Technologies, Inc. CN896/VN896/P4M900 PCI to PCI Bridge Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. Device 5337 (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8237/8251 Ultra VLINK Controller
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
02:00.0 VGA compatible controller: NVIDIA Corporation G86 [GeForce 8500 GT] (rev a1)
04:06.0 Network controller: Ralink corp. RT2600 802.11 MIMO
80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10)
```

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 004 Device 002: ID 1241:f728 Belkin
Bus 005 Device 002: ID 15c2:ffdc SoundGraph Inc. iMON PAD Remote Controller
Bus 001 Device 005: ID 13fe:3100 Kingston Technology Company Inc. 2/4 GB stick
```

dmesg | tail -n 20:
```
[   89.340092] usb 1-5: new high-speed USB device number 5 using ehci_hcd
[   89.515436] Initializing USB Mass Storage driver...
[   89.515865] scsi4 : usb-storage 1-5:1.0
[   89.516446] usbcore: registered new interface driver usb-storage
[   89.516450] USB Mass Storage support registered.
[   89.526232] usbcore: registered new interface driver uas
[   90.543809] scsi 4:0:0:0: Direct-Access     Integral AG47             PMAP PQ: 0 ANSI: 0 CCS
[   90.545047] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   91.442409] sd 4:0:0:0: [sdb] 15646720 512-byte logical blocks: (8.01 GB/7.46 GiB)
[   91.445402] sd 4:0:0:0: [sdb] Write Protect is off
[   91.445409] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
[   91.448413] sd 4:0:0:0: [sdb] No Caching mode page present
[   91.448421] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   91.457524] sd 4:0:0:0: [sdb] No Caching mode page present
[   91.457532] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   91.473318]  sdb: sdb1
[   91.480791] sd 4:0:0:0: [sdb] No Caching mode page present
[   91.480799] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   91.480806] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   94.700014] wlan0: no IPv6 routers present
```

lsmod | sort:
```
arc4                   12529  2
bluetooth             180104  10 bnep,rfcomm
bnep                   18281  2
cfg80211              205544  2 rt2x00lib,mac80211
crc_itu_t              12707  1 rt61pci
drm                   242038  5 nouveau,ttm,drm_kms_helper
drm_kms_helper         46978  1 nouveau
eeprom_93cx6           12725  1 rt61pci
fat                    61512  1 vfat
hid                    99559  1 usbhid
i2c_algo_bit           13423  1 nouveau
i2c_viapro             13153  0
imon                   32839  0
ir_jvc_decoder         12507  0
ir_lirc_codec          12859  0
ir_mce_kbd_decoder     12777  0
ir_nec_decoder         12507  0
ir_rc5_decoder         12507  0
ir_rc6_decoder         12507  0
ir_sony_decoder        12510  0
joydev                 17693  0
lirc_dev               19204  1 ir_lirc_codec
lp                     17799  0
mac80211              506816  2 rt2x00pci,rt2x00lib
mac_hid                13253  0
Module                  Size  Used by
mxm_wmi                12979  1 nouveau
nls_cp437              16991  1
nls_iso8859_1          12713  1
nouveau               774571  3
parport                46562  3 parport_pc,ppdev,lp
parport_pc             32866  0
pata_via               13701  0
ppdev                  17113  0
psmouse                87603  0
rc_core                26412  10 ir_lirc_codec,ir_mce_kbd_decoder,rc_imon_mce,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder,imon
rc_imon_mce            12505  0
rfcomm                 47604  0
rt2x00lib              55301  2 rt61pci,rt2x00pci
rt2x00pci              14577  1 rt61pci
rt61pci                32257  0
sata_via               13799  2
serio_raw              13211  0
shpchp                 37277  0
snd                    78855  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec         127706  2 snd_hda_codec_realtek,snd_hda_intel
snd_hda_codec_realtek   223867  1
snd_hda_intel          33773  3
snd_hwdep              13668  1 snd_hda_codec
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13324  0
snd_seq_midi_event     14899  1 snd_seq_midi
snd_timer              29990  2 snd_pcm,snd_seq
soundcore              15091  1 snd
ttm                    76949  1 nouveau
uas                    18027  0
usbhid                 47199  0
usb_storage            49198  1
vfat                   17585  1
video                  19596  1 nouveau
wmi                    19256  1 mxm_wmi
```

Not sure what any of this means, but hopefully you can make something of it.

Thank you again.

---

### Post by Lisiano on 2012-05-18
You have a Ralink RT2600, which is using the mac80211 driver. You aren't plagued by kernel errors. Sadly I don't have much experience with Ralink, I only had 1 adapter and it worked out of the box beautifully. Hopefully someone who knows more about Ralinks will help you.

---

### Post by josephmills on 2012-05-18
could we please see a 
```
lspci -nn | grep Ralink
```
thanks 

-nn gives us name and number of the card

---

### Post by Corvid133 on 2012-05-18
Lisiano - many thanks. Doubtless I shall enlist your help further down the line; sadly I am a programming doofus so shan't likely be able to offer much help to anyone until I've picked up a bit of nous :-)

Josephmills - will do; I'm away from my desktop for a couple of days but will get right on it as soon as I'm home. Sorry for the delay - I don't mean to mess you about.

---

### Post by Corvid133 on 2012-05-20
Righty:

It says:

```
04:05.0 Network controller [0280}:Ralink corp. RT2600 802.11 MIMO [1814:0401]
```

Does that help?

---

### Post by Corvid133 on 2012-05-23
Can anyone help me?

I have tried entering the following command:

```
sudo -s gksu gedit /etc/modprobe.d/ath9k.conf
```
 
and adding this to the file before saving:

```
options ath9k nohwcrypt=1
```

No joy. So I tried entering this command:

```
sudo rmmod -f iwlagn
```

But it tells me that there is no such file or directory.  I have set the ipv6 to 'ignore' and still have the same problem.

Can anybody tell me what is causing the issue and how I might resolve it?  Do I need a new network adaptor?  If so, which should I get, and will this solve the problem?

I run my own business from home and want to use Ubuntu for that, but I may have to scrap the whole idea and go back to windows if I can't use my emails, so any help would be very greatly appreciated.

Many thanks.

---

### Post by Corvid133 on 2012-05-23
Hi All,

I have 12.04 running on a desktop, with a Ralink RT2600 network card.  The connection is very slow and frequently drops out altogether, which is no use.

I have tried a number of fixes suggested here and elsewhere, and not one has made a scrap of difference.

Should I replace the network card?  If so, what with?

Many thanks

---

### Post by rgreener25 on 2012-05-23
Hmm is this a pci or usb card?

---

### Post by Corvid133 on 2012-05-23
It's a PCI card. The existing connection slows right down and cuts out a lot, and if the software fixes don't work, i guess replacement hardware is the way to go...

---

### Post by rgreener25 on 2012-05-23
Okay open terminal type lspci and lsusb and paste the results here

---

### Post by wildmanne39 on 2012-05-23
Hi, those things you tried you should undo them, they are not for your device, you need to make sure what drivers you are using before you start making changes to your system.

Please open this file back up:
```
gksu gedit /etc/modprobe.d/ath9k.conf
```
and change the ath9k everywhere you see it to rt61pci then save and close gedit and reboot.
Thanks

---

### Post by The Cog on 2012-05-23
Duplicate threads merged

---

### Post by Corvid133 on 2012-05-23
Done - thank you.

---

### Post by wildmanne39 on 2012-05-23
Hi Corvid133, is your wireless working now? if so please use thread tools at the top off the page aqnd mark your thread solved.
Thanks

---

### Post by Corvid133 on 2012-05-23
No, the problem is persisting; very slow speed (1mb/s much of the time) and frequently dropping off the network altogether.

Still looking for suggestions, if anyone can help...

---

### Post by wildmanne39 on 2012-05-23
Hi, post the contents of:
```
gksu gedit /etc/modprobe.d/rt61pci.conf
```
Thanks

---

### Post by Corvid133 on 2012-05-23
Hi,

It comes up blank - nothing in the file.  What does that mean?

---

### Post by wildmanne39 on 2012-05-23
Hi, it means everything did not go well with the directions in post 13.

Please do:
```
gksu gedit /etc/modprobe.d/rt61pci.conf
```
Then add one line:
```
options rt61pci nohwcrypt=1
```
save and close gedit then reboot.
Thanks

---

### Post by Corvid133 on 2012-05-23
OK - still slow (11mb/s) but it hasn't fallen over as yet; I'll leave it running a while and we'll see how it goes...

Thank you

---

### Post by wildmanne39 on 2012-05-23
Hi, that number is a little arbitrary it will go up and down depending on signal strength.

Also set your wireless setting in network manager to match the screenshots and it should increase your speed.
Thanks

---

### Post by Corvid133 on 2012-05-23
Done - thank you very, very much.

Big learning curve for me, but I am determined to learn what I can about using linux (esp. Ubuntu, at least for now) as I can see that the benefits could outweigh the drawbacks.

Thank you again.

---

### Post by wildmanne39 on 2012-05-23
Hi, your welcome!

---

### Post by Corvid133 on 2012-05-24
Oh dear.

Problem still occurring. Hardware issue?

---

### Post by wildmanne39 on 2012-05-24
Hi, what exactly is happening now slowness or having trouble connecting, and by slowness I mean how slow pages load and downloads complete not what it says you are connected at.
Thanks

---

### Post by wildmanne39 on 2012-05-24
Hi, also please post the output of:
```
dmesg | grep -e minstrel -e rt6
```
Thanks

---

### Post by Corvid133 on 2012-05-24
Hi,

Slow loading of pages, big difficulty with more than one tab, and it keeps losing the connection.  When the connection drops, it will ask me to confirm the network password and then try to reconnect - usually failing - and will then do the same thing every couple of minutes until I get annoyed and disconnect it from the network.

Then it'll owrk fine for a couple of hours before playing up again...

---

### Post by Corvid133 on 2012-05-24
Output is:


```
[   12.763455] rt61pci 0000:04:06.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.855600] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   12.856333] Registered led device: rt61pci-phy0::radio
[   12.856400] Registered led device: rt61pci-phy0::assoc
```

Thank you again :)

---

### Post by wildmanne39 on 2012-05-24
Hi, I am researching trying to find and answer to you problem.
Thanks

---

### Post by wildmanne39 on 2012-05-24
Hi, please post the output of:
```
cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo
```
Thanks

---

### Post by Corvid133 on 2012-05-24
Thank you - it's greatly appreciated.

---

### Post by Corvid133 on 2012-05-24
Hi,

I simply says:

```
minstrel_ht
```

Thanks

---

### Post by wildmanne39 on 2012-05-24
Hi, please post the results of:
```
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod | grep rt6
nm-tool
sudo iwlist scan
```
Thanks

---

### Post by Corvid133 on 2012-05-24
OK, outputs are given in order:

```
lspci -nnk | grep -iA2 net
04:06.0 Network controller [0280]: Ralink corp. RT2600 802.11 MIMO [1814:0401]
	Subsystem: Belkin Device [1799:900b]
	Kernel driver in use: rt61pci
```
```
iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"IntexSystems"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:B0:5C:98:93   
          Bit Rate=6 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:45  Invalid misc:18   Missed beacon:0
```

```
rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

```
lsmod | grep rt6
rt61pci                32257  0
crc_itu_t              12707  1 rt61pci
rt2x00pci              14577  1 rt61pci
rt2x00lib              55301  2 rt61pci,rt2x00pci
eeprom_93cx6           12725  1 rt61pci
```

```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [IntexSystems] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt61pci
  State:             connected
  Default:           yes
  HW Address:        00:1C:DF:D9:9B:3E

  Capabilities:
    Speed:           6 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *IntexSystems:   Infra, 00:22:B0:5C:98:93, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    virginmedia3930228: Infra, A0:21:B7:D2:F7:70, Freq 2417 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    virginmedia3126496: Infra, A0:21:B7:D1:44:68, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    virginmedia3134385: Infra, A0:21:B7:56:2C:FE, Freq 2472 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             8.8.8.8
    DNS:             8.8.4.4
```


```
sudo iwlist scan
[sudo] password for ben:
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:22:B0:5C:98:93
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"IntexSystems"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008def95a3e0
                    Extra: Last beacon: 1376ms ago
                    IE: Unknown: 000C496E74657853797374656D73
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: A0:21:B7:D2:F7:70
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"virginmedia3930228"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000836835b7b
                    Extra: Last beacon: 1324ms ago
                    IE: Unknown: 001276697267696E6D6564696133393330323238
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602051700000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F204000110110007564D4447343830100800020088
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3402051700000000000000000000000000000000000000
          Cell 03 - Address: A0:21:B7:56:2C:FE
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"virginmedia3134385"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d326adbe76
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 001276697267696E6D6564696133313334333835
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160D0F0000000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F204000110110007564D4447343830100800020088
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340D0F0000000000000000000000000000000000000000
```

Thank you again

---

### Post by wildmanne39 on 2012-05-24
Hi, your link quality is low get right next to your router and see if your speed increases.

Go into your router settings and set your encryption to just wpa2 if possible.

In network manager is MTU set to auto?

Did you do anything to try to force a higher speed like 54 mbs?

Please post the contents of:
```
gksu gedit /etc/modprobe.d/rt61pci.conf
```
Thanks

---

### Post by Corvid133 on 2012-05-24
Hi,

OK, I'll try to move things about; the router is in the other room and the computer is a big beast, but I will do what I can.

Not quite sure how to change the router settings - jiggered if I can remember the login name and password for it, but will dig them out.

MTU is set to auto.

I've done nothing to try and force higher speeds - if I'm honest, I wouldn't know how :-)

Contents:
```
options rt61pci nohwcrypt=1
```

Thanks again

---

### Post by wildmanne39 on 2012-05-24
Hi, other then the suggestions in my last post I do not know of anything else to try.
Thanks

---

### Post by Corvid133 on 2012-05-24
You've been more than helpful, thank you.  I may swap out the adaptor at some point, otherwise I'll run an extension to the phone socket and put the router in the office here with me.

Thank you again, wildemanne39.

---

### Post by wildmanne39 on 2012-05-24
Hi, your welcome! I wish we could have gotten better results but it looks like we have done all we can do.

---

