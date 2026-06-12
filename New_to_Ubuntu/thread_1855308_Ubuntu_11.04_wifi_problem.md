---
title: "Ubuntu 11.04 wifi problem"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by Airward on 2011-10-05
I have ubuntu 11.04 wifi works, but is unstable, sometimes it works for hours but more often connection disappears and I to reset it.

I was trying to solve this problem on my own for couple of days, but no luck... And it is annoying.

06:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

# ndiswrapper -l
netathw : driver installed
	device (168C:002B) present (alternate driver: ath9k)

airward@xxx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"virginmedia5755028"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: C4:3D:C7:3A:3D:89   
          Bit Rate=11 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:65  Invalid misc:633   Missed beacon:0


Any advice?

---

### Post by ubun2geek on 2011-10-05
If you have a internet connection that you can use temporarily, search additional drivers. Download the driver and reboot. Ndiswrapper does not help and is outdated.

---

### Post by anewguy on 2011-10-05
> **OpenOffice.org said:**
> If you have a internet connection that you can use temporarily, search additional drivers. Download the driver and reboot. Ndiswrapper does not help and is outdated.

Ndiswrapper still has plenty of uses - this is very important for beginners to know, and that they shouldn't follow old posts about it either.  But.... in this case probably not.  I suspect one of the delivered atheros modules is probably conflicting with driver loaded with ndiswrapper.

What would I do?

(1) reverse everything you did when setting up ndiswrapper - this includes removing ndiswrapper from the /etc/modules file, backing out any changes made to blacklist.conf, etc.. 

(2) reboot - this should clear anything remaining from your use of ndiswrapper from memory, etc.

(3) try:  sudo modprobe ath9k

(4) wait a few minutes and see if your wireless works

If not, THEN go online with a hardwire connection as per OpenOffice.org.  This means a hard-wired connection to your router, then the following steps:

(1) sudo apt-get update

(2) go to system/administration/additional drivers - this will start the search for a restricted driver and if found show it on the screen from which you will need to enable it.

(3) disconnect the hard-wire cable

(4) reboot and see if your wireless works.


Dave ;)

---

### Post by ubun2geek on 2011-10-05
+1 anewguy
I have been using ubuntu for a somewhat short time. :)
EDIT: So what I mean to say is that your answer is probably better. :)

---

### Post by wildmanne39 on 2011-10-06
Hi, this is the command to get rid of ndiswrapper.
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
please run the commands one at a time, unplug your wired connection and run this command as anewguy suggested.
```
sudo modprobe ath9k
```
Thank you

---

### Post by anewguy on 2011-10-06
Forgot to mention - if this works okay just let us know so we can help you make the change permanent.  Right now it would only be good until the next reboot.  Very simple to make permanent.

Dave ;)

---

### Post by Airward on 2011-10-06
I'm not sure if I have done everything properly, but it seems I have removed ndiswrapper.
When entering 
sudo modprobe ath9k in terminal, nothing happened.

But wifi is working for now, I just need to wait and see if I get anymore DC's

---

### Post by Airward on 2011-10-06
> **Airward said:**
> But wifi is working for now, I just need to wait and see if I get anymore DC's

I still get DC's... :(

p.s. I can't find system/administration/additional drivers, Only thing I find is System setings/harware/aditional drivers, but it finds no drivers.

---

### Post by wildmanne39 on 2011-10-06
Hi, you do not need to do anything with additional drivers.

This card does not work very well in linux, you have to stay close to your AP, but there are a few thing we an look at.

Please do this:
```
gksudo gedit /etc/modprobe.d/ath9k.conf

```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Let us know if it helps, if not we will need to go further.
Thank you

---

### Post by anewguy on 2011-10-06
Glad you replied here, wildmanne39!  I couldn't remember for the life of me where I had found what I was thinking, and I didn't want to mess it up, and then you posted it - saved me some hunting ;)

Dave ;)

---

### Post by wildmanne39 on 2011-10-06
Hi anewguy your welcome! I have that problem to sometimes. There maybe other things we will have to do as well, his card is not the best in linux.
Thank you

---

### Post by Airward on 2011-10-06
Now we play the waiting game... :neutral:

---

### Post by Airward on 2011-10-06
OK it happened again :(

---

### Post by ubun2geek on 2011-10-06
> **Airward said:**
> I still get DC's... :(

p.s. I can't find system/administration/additional drivers, Only thing I find is System setings/harware/aditional drivers, but it finds no drivers.
You need to be connected to the internet to get drivers.

---

### Post by Airward on 2011-10-06
> **ubun2geek said:**
> You need to be connected to the internet to get drivers.

Thing is I am connected but connection disapear randomly, sometimes it lasts for an hour but mostly it happens every few minutes or so... :/

---

### Post by wildmanne39 on 2011-10-06
Hi, when you can not connect please run this command.
```
nm-tool
```
```
sudo iwlist scan
```
```
dmesg | egrep 'ath|firm|wlan0'
```
Thank you

---

### Post by Airward on 2011-10-06
Thanks a lot. I am really greatfull for your help guys.
I'll try that and see what happens.

---

### Post by Airward on 2011-10-06
OK I have done it and thats what it gave me

```
airward@copypirated:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:24:54:D5:DF:6A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto virginmedia5755028] -------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        B4:74:9F:3A:03:D5

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia0605562: Infra, A0:21:B7:CA:2D:C7, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    The_Portal_Of_Doom: Infra, C4:3D:C7:42:32:CC, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    virginmedia1178398: Infra, A0:21:B7:D4:0C:80, Freq 2452 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    *virginmedia5755028: Infra, C4:3D:C7:3A:3D:89, Freq 2462 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
    Apollo:          Infra, 00:26:5A:1E:AC:18, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WEP
    Mylink:          Infra, 00:1D:7E:1F:91:6F, Freq 2472 MHz, Rate 54 Mb/s, Strength 41 WPA

  IPv4 Settings:
    Address:         192.168.0.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100

airward@copypirated:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C4:3D:C7:3A:3D:89
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"virginmedia5755028"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002bb53ee189
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 001276697267696E6D6564696135373535303238
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B071700000000000000000000000000000000000000
                    IE: Unknown: DD6F0050F204104A0001101044000102103B000103104700104D73C5C27E6B5243D6440AAB1719670B102100074E657467656172102300074E6574676561721024000631323334353610420007303030303030311054000800060050F204000110110007564D4447343830100800020088
                    IE: Unknown: DD090010180207F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337E181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B071700000000000000000000000000000000000000
          Cell 02 - Address: 00:26:5A:1E:AC:18
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Apollo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002d14651d15e
                    Extra: Last beacon: 148ms ago
                    IE: Unknown: 000641706F6C6C6F
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D160B070700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706474220010D10
                    IE: Unknown: DD1E00904C33EE1117FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C340B070700000000000000000000000000000000000000
          Cell 03 - Address: 00:1D:7E:1F:91:6F
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Mylink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000975ab5d187
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 00064D796C696E6B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010D
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180202F5000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: A0:21:B7:D4:0C:80
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"virginmedia1178398"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001ab4dc6d18c
                    Extra: Last beacon: 624ms ago
                    IE: Unknown: 001276697267696E6D6564696131313738333938
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180200F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


airward@copypirated:~$ dmesg | egrep 'ath|firm|wlan0'
[    0.877360] device-mapper: multipath: version 1.2.0 loaded
[    0.877364] device-mapper: multipath round-robin: version 1.0.0 loaded
[    8.400512] elantech: assuming hardware version 2, firmware version 4.2.21
[    9.601752] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    9.601767] ath9k 0000:06:00.0: setting latency timer to 64
[    9.652136] ath: EEPROM regdomain: 0x65
[    9.652139] ath: EEPROM indicates we should expect a direct regpair map
[    9.652142] ath: Country alpha2 being used: 00
[    9.652144] ath: Regpair used: 0x65
[   10.797050] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   10.797811] Registered led device: ath9k-phy0::radio
[   10.797839] Registered led device: ath9k-phy0::assoc
[   10.797862] Registered led device: ath9k-phy0::tx
[   10.797891] Registered led device: ath9k-phy0::rx
[   15.301154] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.481645] wlan0: authenticate with c4:3d:c7:3a:3d:89 (try 1)
[   45.483726] wlan0: authenticated
[   45.500547] wlan0: associate with c4:3d:c7:3a:3d:89 (try 1)
[   45.511585] wlan0: RX AssocResp from c4:3d:c7:3a:3d:89 (capab=0x411 status=0 aid=5)
[   45.511588] wlan0: associated
[   45.518143] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   54.094508] wlan0: deauthenticated from c4:3d:c7:3a:3d:89 (Reason: 15)
[   55.233929] wlan0: authenticate with c4:3d:c7:3a:3d:89 (try 1)
[   55.236228] wlan0: authenticated
[   55.236257] wlan0: associate with c4:3d:c7:3a:3d:89 (try 1)
[   55.240211] wlan0: RX AssocResp from c4:3d:c7:3a:3d:89 (capab=0x411 status=0 aid=5)
[   55.240214] wlan0: associated
[   56.352028] wlan0: no IPv6 routers present
[ 1016.292126] wlan0: deauthenticating from c4:3d:c7:3a:3d:89 by local choice (reason=3)
[ 1017.397899] wlan0: authenticate with c4:3d:c7:3a:3d:89 (try 1)
[ 1017.402166] wlan0: authenticated
[ 1017.420129] wlan0: associate with c4:3d:c7:3a:3d:89 (try 1)
[ 1017.424096] wlan0: RX AssocResp from c4:3d:c7:3a:3d:89 (capab=0x411 status=0 aid=5)
[ 1017.424102] wlan0: associated
[ 1149.357629] wlan0: deauthenticating from c4:3d:c7:3a:3d:89 by local choice (reason=3)
[ 1150.467890] wlan0: authenticate with c4:3d:c7:3a:3d:89 (try 1)
[ 1150.469992] wlan0: authenticated
[ 1150.470021] wlan0: associate with c4:3d:c7:3a:3d:89 (try 1)
[ 1150.474096] wlan0: RX AssocResp from c4:3d:c7:3a:3d:89 (capab=0x411 status=0 aid=5)
[ 1150.474101] wlan0: associated
[ 3690.176237] wlan0: authenticate with c4:3d:c7:3a:3d:89 (try 1)
[ 3690.179408] wlan0: authenticated
[ 3690.179438] wlan0: associate with c4:3d:c7:3a:3d:89 (try 1)
[ 3690.183416] wlan0: RX AssocResp from c4:3d:c7:3a:3d:89 (capab=0x411 status=0 aid=5)
[ 3690.183421] wlan0: associated

```

Have no idea what that means... :-k

---

### Post by wildmanne39 on 2011-10-06
Hi, what is the name of the network you are trying to connect to so I can see if there is a setting we can change to help.
Thank you

---

### Post by Airward on 2011-10-06
> **wildmanne39 said:**
> Hi, what is the name of the network you are trying to connect to so I can see if there is a setting we can change to help.
Thank you

Sr, what do you mean "the name" ?

---

### Post by wildmanne39 on 2011-10-06
Hi, to connect you have to have a wireless router and connection setup up and it has a name which is called SSID.
Thank you

---

### Post by Airward on 2011-10-06
virginmedia5755028

---

### Post by wildmanne39 on 2011-10-06
Hi, never mind I found it, you need to go into your routers settings and change the encryption to wpa2 only and not wpa/wpa2, and also do the same in wireless network in the icon in the top right corner.
Thank you

---

### Post by Airward on 2011-10-07
Hi, how I do wpa2 only?
[IMG]http://1.bp.blogspot.com/-31gNUwawdVE/To7qdhZ0huI/AAAAAAAAANw/JKtgM_-Fp1A/s1600/Screenshot.png[/IMG]

Thanks.

---

### Post by wildmanne39 on 2011-10-07
Hi, you can not do it in network manager on yours, so just try the commands in my last post and let me know if it helps and remember that if you restart your computer those settings will reset, we will have to make them permanent if they help.
Thank you

---

### Post by Airward on 2011-10-07
It didn't really helped. I still get DC randomly but it look like i have connection for a bit longer. 
Thanks.

---

### Post by wildmanne39 on 2011-10-07
Hi, I will do some more research, but this card is known to have issues with linux, let me know if you want to make the changes permanent.
Thank you

---

### Post by Airward on 2011-10-07
Thanks a lot

---

### Post by wildmanne39 on 2011-10-07
Hi, one other thing that usually helps,plug your computer into the router with your ehternet port then open your browser and type 192.168.0.1 into the address bar and hopefully that will take you to your router settings.

Under wireless make sure your speed is set to b,g,n and that the power settings are turned all the way up.
Thank you

---

### Post by Airward on 2011-10-08
I do not have cable at the moment, but I found this:
[http://muzehyun.blogspot.com/2009/04/workaround-for-wireless-disconnection.html]("http://muzehyun.blogspot.com/2009/04/workaround-for-wireless-disconnection.html")
would that be any help?
Oh, and I have ralink usb wifi adabter, but that one is SLOW and I don't really know how properly install drivers for it.

Thanks.

---

### Post by wildmanne39 on 2011-10-08
Hi, I am not sure if the script in the link will help or not a lot of times it is a matter of trying and seeing.

Plug your usb adapter in and run:
```
lsusb
``` 
and post the results here please.
Thank you

---

### Post by Airward on 2011-10-08
> **wildmanne39 said:**
> Hi, I am not sure if the script in the link will help or not a lot of times it is a matter of trying and seeing.

Plug your usb adapter in and run:
```
lsusb
``` 
and post the results here please.
Thank you

Bus 002 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter

---

### Post by wildmanne39 on 2011-10-08
Hi, that is a pretty good usb adapter, let's see:
```
lsmod
```
Thank you

---

### Post by Airward on 2011-10-08
> **wildmanne39 said:**
> Hi, that is a pretty good usb adapter, let's see:
```
lsmod
```
Thank you

Not shure wich part you need, so:


```
Module                  Size  Used by
rt2870sta             410104  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  2 rt2870sta,rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
snd_seq_dummy          12686  0 
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
arc4                   12473  4 
snd_hda_intel          24113  4 
ath9k                 103633  0 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_intel,snd_hda_codec
mac80211              257001  4 rt2800lib,rt2x00usb,rt2x00lib,ath9k
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
ath9k_common           13611  1 ath9k
ath9k_hw              300328  2 ath9k,ath9k_common
snd_seq_midi_event     14475  1 snd_seq_midi
ath                    19141  2 ath9k,ath9k_hw
snd_seq                51291  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
i915                  451033  3 
uvcvideo               66851  0 
cfg80211              156212  4 rt2x00lib,ath9k,mac80211,ath
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
videodev               75143  1 uvcvideo
snd                    55295  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
drm_kms_helper         40745  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
drm                   184164  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
sky2                   49172  0 
```

---

### Post by wildmanne39 on 2011-10-08
Hi, let's see if this improves your speed.
```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rt2x00usb" >> /etc/modprobe.d/blacklist.conf
exit
```
Then restart your computer and tell me if it is better.

If not post:
```
lsmod
```
again so I can make sure the drivers did not load.
Thank you

---

### Post by Airward on 2011-10-11
Hey, 
sorry, but speed is still WAY slower than it was on win7 and I still gettin' DC's... :(

---

### Post by Airward on 2011-10-11
Hey, that's lsmod

```
airward@copypirated:~$ lsmod
Module                  Size  Used by
rt2870sta             410104  1 
crc_ccitt              12595  1 rt2870sta
cryptd                 19801  0 
aes_i586               16956  1 
aes_generic            38023  1 aes_i586
nls_utf8               12493  1 
udf                    83795  1 
crc_itu_t              12627  1 udf
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255882  1 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_intel          24113  4 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12473  2 
snd                    55295  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k                 103633  0 
uvcvideo               66851  0 
mac80211              257001  1 ath9k
psmouse                73312  0 
soundcore              12600  1 snd
videodev               75143  1 uvcvideo
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ath9k_common           13611  1 ath9k
i915                  451033  3 
ath9k_hw              300328  2 ath9k,ath9k_common
ath                    19141  2 ath9k,ath9k_hw
drm_kms_helper         40745  1 i915
cfg80211              156212  3 ath9k,mac80211,ath
drm                   184164  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
sky2                   49172  0 
libahci                25548  1 ahci

```

thanks

---

### Post by wildmanne39 on 2011-10-11
Hi, I suspect it is still using the internal card let's do this please:
```
sudo su
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist.conf
exit
```
```
sudo modprobe rt2870sta
```
Thank you

---

### Post by Airward on 2011-10-11
Thanks, let's see where we'll get now...

---

### Post by wildmanne39 on 2011-10-11
Hi, your welcome!

---

### Post by Airward on 2011-10-11
Just got discconected again... :/ And when I chose to connect via USB, it showed that is is connected, but it was a lie... And I was able to do it with ath9k succsesfuly...

---

### Post by wildmanne39 on 2011-10-11
Hi, how did you connect with ath9k if it is blacklisted?

Please post the results of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thank you

---

### Post by Airward on 2011-10-11
You see screenshot? it gave me the list, first I chose USB, id connected, but I wasn't able to do anything. So I chose the one on top of the list and it connected. 
(just in case I'm not able to connect with ath9k couse its banned and cant connect with usb, how I remove it from banlist?)

---

### Post by Airward on 2011-10-11
> **wildmanne39 said:**
> Hi, how did you connect with ath9k if it is blacklisted?

Please post the results of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thank you

That's weird:
```
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00usb
blacklist ath9k
airward@copypirated:~$ 

```

---

### Post by wildmanne39 on 2011-10-11
Hi, that is not weird that is what it should look like. I could not see anything that made me think the ath9k was connected, I believe you are connected with the usb device.

To unblacklist the ath9k you just do this:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Then remove blacklist ath9k save and exit.
Thank you

---

### Post by Airward on 2011-10-11
Yeah, I am connected with USB (just tried to unplug it and i lost conecction). 
And what that rt2*b stuff is?
(and yeah I just got a dc again... #-o )
Thanks

---

### Post by wildmanne39 on 2011-10-11
Hi, that is more drivers for your usb adapter but if they are not blacklisted it will not work.

We stand a better chance of getting the usb adapter to work right then the ath9k.
Thank you

---

### Post by Airward on 2011-10-12
> **wildmanne39 said:**
> Hi, that is more drivers for your usb adapter but if they are not blacklisted it will not work.

We stand a better chance of getting the usb adapter to work right then the ath9k.
Thank you

Hello, but there is chance that in the future ath9k problem will be fixed?

---

### Post by Airward on 2011-10-12
Hello
It was allright for a while, it used to DC, but RC in a few min, but now it just was not able to connect back... So I removed ath9k from black list, just to connect again... Oh... What a headache...
Thanks

---

### Post by wildmanne39 on 2011-10-12
Hi, it is possible that it will be fixed in the new release but we will not know that until it comes out.
Thank you

---

### Post by Airward on 2011-10-15
> **wildmanne39 said:**
> Hi, it is possible that it will be fixed in the new release but we will not know that until it comes out.
Thank you

No DC's on 11.10 so far, it is SLOW, but at least no more DC's.

Thanks for your help.

---

### Post by wildmanne39 on 2011-10-15
Hi, are you using the internal wireless in the usb in 11.10?
Thank you

---

### Post by Airward on 2011-10-16
> **wildmanne39 said:**
> Hi, are you using the internal wireless in the usb in 11.10?
Thank you

Hello, 

No, haven't even tried USB yet, tottaly forgot to check the difrence.

Thanks

---

### Post by Airward on 2011-10-16
Ok, I have wireless on USB now, but for some reason my deluge bit torrent client crashed... :/

---

### Post by wildmanne39 on 2011-10-16
Hi, I doubt it crashed because of the usb adapter.
Thank you

---

### Post by siddi on 2011-10-30
Hey guys...

I read the entire tread but am unsure what i should do finally. Recently upgraded to 11.10 and i am having the same issues. The wifi keeps disconnecting every few minutes for a few seconds and then reconnects

Please help

---

### Post by wildmanne39 on 2011-10-30
Hi siddi, you should start your own thread in networking because you are using a different version of ubuntu then the original poster and you may have a different wireless card.
Thank you

---

