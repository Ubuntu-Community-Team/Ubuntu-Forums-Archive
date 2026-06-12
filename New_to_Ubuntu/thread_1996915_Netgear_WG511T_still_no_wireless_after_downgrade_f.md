---
title: "Netgear WG511T: still no wireless after downgrade from 12.04 to clean 10.04"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by G M on 2012-06-04
All right: I was lost but now it is worse.

You can find here a short presentation of myself and my (past) issue, i.e. the lack of wireless with a Netgear WG511T after the update to 12.04.
[http://ubuntuforums.org/showthread.php?t=1993245](http://ubuntuforums.org/showthread.php?t=1993245)
Note: on the other side of the dual boot (XP) it is still working flawlessly and so it worked since Ubuntu 8.04...

Given that 12.04 is actually a pain on this laptop (Sony Vaio PCG-FXA48 with AMD processor at 1 GHz and something and 512 MB), I decided to take the occasion and downgrade the Ubuntu partition to something more adapt to the hardware. So I formatted the partition and I installed a clean 10.04.

Probably you can't imagine my surprise when I realized that, even after the clean install, the wireless card was not working (though, at least, it was recognized). I have the wifi "fan" on the top bar and, no matter what I try to access my network, the fan "flashes" for the while and eventually I am just presented with a dialog window to enter again the credentials.

No change in removing the protection of the network, checking the MAC address (but the XP side works!), configuring the address manually, ...

Since I already tried anything in my power (and even much beyond), I would really appreciate some basic hint at the absolute beginner level. To me it looks really weird that the card is still working when booting in XP as it worked for years since 8.04...

Sorry for the lengthy message and thanks in advance,

Giulio

---

### Post by wildmanne39 on 2012-06-05
Hi, this is an old card so it may be hard to get it working and I am leaving town soon but since you were asking for my help I will do the best I can in the amount of time that I have please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
sudo pccardctl ident
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by chili555 on 2012-06-05
Have a great trip, Wild Man! I've subscribed to this thread.

---

### Post by G M on 2012-06-05
Dear wildmanne39, thanks a lot for your intervention (and also to chili555, in case...).

Right, it is old but, as I wrote, it always worked with Ubuntu since 8.04 and it still works from the XP partition. Anyway, here are my homeworks.
```
ubuno@ubuno-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ubuno-laptop 2.6.32-41-generic #89-Ubuntu SMP Fri Apr 27 22:22:09 UTC 2012 i686 GNU/Linux

``````
ubuno@ubuno-laptop:~$ lspci -nnk | grep -iA2 net
00:10.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp
--
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter [168c:0013] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k

``````
ubuno@ubuno-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

``````
ubuno@ubuno-laptop:~$ sudo pccardctl ident
[sudo] password for ubuno: 
Socket 0:
  no product info available
Socket 1:
  no product info available

``````
ubuno@ubuno-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````
ubuno@ubuno-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
ubuno@ubuno-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
arc4                    1153  2 
snd_via82xx            20058  2 
snd_via82xx_modem       8486  5 
gameport                9089  1 snd_via82xx
ath5k                 121632  0 
snd_ac97_codec        100646  2 snd_via82xx,snd_via82xx_modem
mac80211              205434  1 ath5k
ath                     7611  1 ath5k
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
cfg80211              126528  3 ath5k,mac80211,ath
led_class               2864  1 ath5k
snd_mpu401_uart         5617  1 snd_via82xx
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  6 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
pcmcia                 30784  0 
bitblit                 4707  1 fbcon
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
video                  17375  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
softcursor              1189  1 bitblit
joydev                  8740  0 
yenta_socket           20408  3 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
output                  1871  1 video
rsrc_nonstatic         10015  1 yenta_socket
ppdev                   5259  0 
lp                      7028  0 
via686a                11050  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_timer              19130  2 snd_pcm,snd_seq
parport_pc             25962  1 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
i2c_viapro              5573  0 
shpchp                 28835  0 
parport                32635  3 ppdev,lp,parport_pc
snd                    54244  24 snd_via82xx,snd_via82xx_modem,snd_ac97_codec,snd_pcm_oss,snd_mpu401_uart,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
via_agp                 5310  1 
psmouse                63677  0 
agpgart                31724  1 via_agp
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  3 snd_via82xx,snd_via82xx_modem,snd_pcm
8139too                18545  0 
ohci1394               26950  0 
8139cp                 16186  0 
ieee1394               81181  1 ohci1394
mii                     4381  2 8139too,8139cp
pata_via                7272  2 
floppy                 53016  0 

```Thanks again!

Giulio

---

### Post by G M on 2012-06-05
By the way, sorry if my other post was considered as a duplicate but I thought it was more appropriate to open a separate discussion especially given the different Ubuntu version. Evidently this was not the case.

Secondly, I was expecting notifications for new posts but it appears that it is not the default setting and that the control panel is accessible only after 50 posts. It seems that I have to read more about the local rules.

Cheers,

Giulio

---

### Post by wildmanne39 on 2012-06-05
Hi, try this:
```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1
sudo ifconfig wlan0 up
```
do not reboot, if this helps we will need to make it permanent, if not post:
```
nm-tool
sudo iwlist scan
dmesg | egrep 'ath|firm|wlan'
```

Thank you chili555!!!

---

### Post by G M on 2012-06-05
Hi, at the third step (sudo modprobe ath5k nohwcrypt=1), the wireless connection "pop-up" appeared stating that it was going to connect but it didn't. I run the fourth line and an exclamation mark was still present on the wi-fi symbol. Also trying to access the network resulted in the usual and useless long wait

By the way, SSID is invisible, WPA-PSK with MAC access control. In case, I may turn SSID on, MAC and security off for a while. I am plugging/unplugging the ethernet cable, in case you are interested.

Here the outputs.

```
ubuno@ubuno-laptop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        08:00:46:5A:71:05

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:14:6C:44:61:48

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    makossa:         Infra, F0:7D:68:FB:CD:F7, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    fallofalloadesso:Infra, 00:25:BC:8C:88:21, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    AlessandroNet:   Infra, F0:7D:68:10:83:6C, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2

``````
ubuno@ubuno-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:25:BC:8C:88:21
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"fallofalloadesso"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000225f84de495
                    Extra: Last beacon: 916ms ago
                    IE: Unknown: 001066616C6C6F66616C6C6F61646573736F
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 0706495420010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A0C501BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD07000393016D0320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F207000101060025BC8C8822
          Cell 02 - Address: F0:7D:68:10:83:6C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"AlessandroNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000013e118bc
                    Extra: Last beacon: 500ms ago
                    IE: Unknown: 000D416C657373616E64726F4E6574
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
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

``````
ubuno@ubuno-laptop:~$ dmesg | egrep 'ath|firm'
[    0.370149] device-mapper: multipath: version 1.1.0 loaded
[    0.370158] device-mapper: multipath round-robin: version 1.0.0 loaded
[   10.594787] ath5k 0000:06:00.0: enabling device (0000 -> 0002)
[   10.594815] ath5k 0000:06:00.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   10.594938] ath5k 0000:06:00.0: registered as 'phy0'
[   11.213666] ath: EEPROM regdomain: 0x0
[   11.213677] ath: EEPROM indicates default country code should be used
[   11.213681] ath: doing EEPROM country->regdmn map search
[   11.213689] ath: country maps to regdmn code: 0x3a
[   11.213693] ath: Country alpha2 being used: US
[   11.213697] ath: Regpair used: 0x3a
[   11.692601] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[   17.006192] ath5k phy0: noise floor calibration timeout (2412MHz)
[   19.418803] ath5k phy0: noise floor calibration timeout (2412MHz)
[   20.785983] ath5k phy0: noise floor calibration timeout (2412MHz)
[   39.273636] ath5k phy0: noise floor calibration timeout (2412MHz)
[   39.576370] ath5k phy0: noise floor calibration timeout (2412MHz)
[   40.906076] ath5k phy0: noise floor calibration timeout (2412MHz)
[   69.275981] ath5k phy0: noise floor calibration timeout (2412MHz)
[   69.578833] ath5k phy0: noise floor calibration timeout (2412MHz)
[   70.925773] ath5k phy0: noise floor calibration timeout (2412MHz)
[  642.627284] ath5k phy0: noise floor calibration timeout (2412MHz)
[  880.055952] ath5k phy0: noise floor calibration timeout (2412MHz)
[  880.459427] ath5k phy0: noise floor calibration timeout (2412MHz)
[ 1301.134833] ath5k phy0: noise floor calibration timeout (2412MHz)
[ 1541.225231] ath5k phy0: noise floor calibration timeout (2412MHz)
[ 1719.951833] ath5k 0000:06:00.0: PCI INT A disabled
[ 1728.740951] ath5k 0000:06:00.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[ 1728.741178] ath5k 0000:06:00.0: registered as 'phy1'
[ 1729.341530] ath: EEPROM regdomain: 0x0
[ 1729.341547] ath: EEPROM indicates default country code should be used
[ 1729.341556] ath: doing EEPROM country->regdmn map search
[ 1729.341570] ath: country maps to regdmn code: 0x3a
[ 1729.341579] ath: Country alpha2 being used: US
[ 1729.341588] ath: Regpair used: 0x3a
[ 1729.393513] ath5k phy1: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[ 1729.768115] ath5k phy1: noise floor calibration timeout (2412MHz)
[ 1730.087342] ath5k phy1: noise floor calibration timeout (2412MHz)
[ 1732.149048] ath5k phy1: noise floor calibration timeout (2412MHz)
[ 1786.334699] ath5k 0000:06:00.0: PCI INT A disabled
[ 1793.276903] ath5k 0000:06:00.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[ 1793.277084] ath5k 0000:06:00.0: registered as 'phy2'
[ 1793.873031] ath: EEPROM regdomain: 0x0
[ 1793.873042] ath: EEPROM indicates default country code should be used
[ 1793.873046] ath: doing EEPROM country->regdmn map search
[ 1793.873053] ath: country maps to regdmn code: 0x3a
[ 1793.873058] ath: Country alpha2 being used: US
[ 1793.873061] ath: Regpair used: 0x3a
[ 1793.902019] ath5k phy2: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[ 1794.255609] ath5k phy2: noise floor calibration timeout (2412MHz)
[ 1794.571711] ath5k phy2: noise floor calibration timeout (2412MHz)
[ 1795.078952] ath5k phy2: noise floor calibration timeout (2412MHz)
[ 1886.322423] ath5k phy2: noise floor calibration timeout (2412MHz)
[ 1936.192897] ath5k phy2: noise floor calibration timeout (2412MHz)

```Thanks.

---

### Post by wildmanne39 on 2012-06-05
Hi, what network are you trying to connect too?

Ubuntu can have a hard time connecting to a hidden network and it is a myth that they are more secure.

You should set encryption to wpa2 only in your router if you have that option it usually works best with ubuntu.

Let's make the change permanent:
```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
``` 

Also you should turn power management off:

```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
```
#!/bin/sh

/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit, close and reboot.

In 10.04 wireless will only try to connect when the wired connection is unplugged.
Thanks

---

### Post by G M on 2012-06-05
> **wildmanne39 said:**
> Hi, what network are you trying to connect too?It is my home network with a Netgear DG834GT. SSID was hidden and now I set it to visible (right, I know it is a myth but I like to be shy :)). Security is set to WPA-PSK with MAC address control on. The transmission is mixed b/g.

```
ubuno@ubuno-laptop:~$ echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
[sudo] password for ubuno:
options ath5k nohwcrypt=1

``````
ubuno@ubuno-laptop:~$ sudo modprobe -rfv ath5k
rmmod /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/2.6.32-41-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/2.6.32-41-generic/kernel/net/wireless/cfg80211.ko
rmmod /lib/modules/2.6.32-41-generic/kernel/drivers/leds/led-class.ko

``````
ubuno@ubuno-laptop:~$ sudo modprobe -v ath5k
insmod /lib/modules/2.6.32-41-generic/kernel/drivers/leds/led-class.ko
insmod /lib/modules/2.6.32-41-generic/kernel/net/wireless/cfg80211.ko
insmod /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/ath/ath.ko
insmod /lib/modules/2.6.32-41-generic/kernel/net/mac80211/mac80211.ko
insmod /lib/modules/2.6.32-41-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1

```Here I got again the pop-up informing about the wireless network available (ethernet was disconnected, still the exclamation mark on the wi-fi symbol remained).

> **wildmanne39 said:**
> (this will create or edit a configuration file that will override the  default powermanagement behavior) and enter the following: 
#!/bin/shSorry but here I lost you or I misunderstood the sequence: I opened gedit with your command, I entered  "#!/bin/sh" but then it was not clear to me whether I had to save and exit before or after giving the last command (especially since the terminal appeared busy). So I saved and closed but the terminal appeared still busy and I had to close it and reopen it where I run the command:
```
ubuno@ubuno-laptop:~$ /sbin/iwconfig wlan0 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not permitted.

```But I rebooted, removed the MAC control and the network was still unaccessible (still with ethernet disconnected) and invisible despite SSID visible... . Anyway at least now I could connect to a neighbor open network.

I am going to switch on/off the router just in case.

Thanks.

---

### Post by G M on 2012-06-05
Wait a minute: I changed channel, rebooted the router and now the network is visible and I could connect it...

Let me do some more testing. I already rebooted the router (I switch it off for the night and I have been tinkering with this stuff for days...) but it is the first time I think to change the channel...

---

### Post by wildmanne39 on 2012-06-05
Hi, the code tag was in the wrong place for power management I fixed it so look at it again, what is in the box under power management should be in the power management file.

I still recommend setting encryption to just wpa2 if possible if not try just wpa.
Thanks

---

### Post by wildmanne39 on 2012-06-05
Hi, you are correct changing channels can help, try 11.
Thanks

---

### Post by G M on 2012-06-05
> **wildmanne39 said:**
> Hi, the code tag was in the wrong place for power management I fixed it so look at it againAh, I thought about that but I also thought that the second line had to be run in the terminal. Now I corrected it, saved, rebooted but, even before doing so, it appears that the real culprit is channel 13!! As soon as I moved it to 3, I could immediately connect to the hidden SSID and MAC protected network while, as soon as I move it back to 13, no connection is possible!

> **wildmanne39 said:**
> I still recommend setting encryption to just wpa2 if possible if not try just wpa.Right, as soon as I can put my hands on all home devices, I will (or somebody may put his/her hands on me beforehand).

Dear wildmanne39, thanks for the support. Everything seems to run smoothly. I just wonder if you suggest to move back from some of your suggestion or just to leave any setting as it is.

Thanks.

---

### Post by wildmanne39 on 2012-06-05
Hi, I recommend leaving all settings for best performance, the two you made permanent with the code and file have a big impact on whether you can connect at all.

Please use thread tools at the top of the page and mark the thread solved.
Thanks

---

### Post by G M on 2012-06-05
Perfect, thanks again.

Giulio

---

### Post by wildmanne39 on 2012-06-05
Your welcome!
Enjoy

---

