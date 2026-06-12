---
title: "Problem with Alfa AWUS036H"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by bobmars1260 on 2012-04-16
Hello,

I have a problem with my network adapter.  

I am running Ubuntu 10.04.4 LTS
Laptop is a Dell Latitude C620 with 256 MB Ram.
My network adapter is a Alfa USB  AWUS036H ( 1 Watt version )
The adapter works pretty well under Win XP SP3

Under Ubuntu, the adapter is remarkably slow.  I take it a very long time to resolve DNS. And then it is really slow to download the site.

I have looked and looked for a posting similar to my problems and have been unable to find one.

Any assistance would be appreciated.

Thank You,
Bob

---

### Post by wildmanne39 on 2012-04-16
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bobmars1260 on 2012-04-16
Here is the information you asked for:

1.) cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux bt 3.2.6 #1 SMP Fri Feb 17 10:40:05 EST 2012 i686 GNU/Linux

2.) lsusb

Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

3.) iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"La Resolana"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:D3:3F:50   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

4.) rfkill list all

1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no

5.) lsmod

Module                  Size  Used by
radeon                731553  0 
ttm                    61659  1 radeon
drm_kms_helper         30737  1 radeon
drm                   183453  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           12980  1 radeon
dm_crypt               22236  0 
arc4                   12473  2 
snd_intel8x0           33017  0 
snd_ac97_codec        104623  1 snd_intel8x0
ac97_bus               12602  1 snd_ac97_codec
snd_pcm                72878  2 snd_intel8x0,snd_ac97_codec
pcnet_cs               30572  1 
8390                   17898  1 pcnet_cs
snd_seq_midi           13132  0 
snd_rawmidi            24215  1 snd_seq_midi
snd_seq_midi_event     14076  1 snd_seq_midi
rtl8187                56060  0 
snd_seq                50403  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12840  0 
pcmcia                 38533  1 pcnet_cs
lp                     13321  0 
joydev                 17161  0 
parport_pc             31867  1 
yenta_socket           27030  0 
pcmcia_rsrc            18100  1 yenta_socket
snd_timer              23911  2 snd_pcm,snd_seq
snd_seq_device         13817  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              410313  1 rtl8187
snd                    52787  7 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12534  1 snd
snd_page_alloc         13709  2 snd_intel8x0,snd_pcm
parport                34960  3 ppdev,lp,parport_pc
pcmcia_core            20902  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                72465  0 
shpchp                 32187  0 
cfg80211              160399  2 rtl8187,mac80211
dcdbas                 14009  0 
mac_hid                13037  0 
serio_raw              13027  0 
eeprom_93cx6           12560  1 rtl8187
dm_mirror              21585  0 
dm_region_hash         15035  1 dm_mirror
dm_log                 17871  2 dm_mirror,dm_region_hash
aufs                  162169  0 
video                  18434  0 
floppy                 59430  0 


Thank you,
Bob

---

### Post by wildmanne39 on 2012-04-16
Hi, there is a lot of problems with this driver, please try:
```
gksu gedit /etc/rc.local
```
Add one line:
```
iwconfig wlan0 rate 5.5M
```
before the exit 0, save,close gedit and reboot.
Thanks

---

### Post by RJARRRPCGP on 2012-04-16
> **bobmars1260 said:**
>   I take it a very long time to resolve DNS. 

Known bug that many people act like the problem don't even exist! 

Most Linux distros will hang at looking up DNS entries for many domains! 

There's a bug where it fails to retrieve the DNS correctly when the DNS is managed by the router. 

It's clearly an auto-managed DNS issue that only shows up with Linux distros.

Windows don't have such a bug.

It's guaranteed to forget the DNS and take longer than freaking 56K to resolve the DNS for weather.com and MANY sites!

This is one nasty bug that looks like I must report, even when there's a chance of someone declaring it a dupe. :( 

The DNS resolving only works correctly when added to /etc/resolv.conf 

But, here's another pitfall, something keeps fighting with my changing of resolv.conf and something will just go ahead and change it back to 192.168.1.254. 

But, it will not work correctly when set to 192.168.1.254!

It looks like anything else works correctly, including possibly when adding the ISP's DNS server directly.

---

### Post by bobmars1260 on 2012-04-16
That is very good to know. I was really puzzled when it didn't seem to have any DNS problems under Windows, but it does under Ubuntu and Back Track....

---

### Post by bobmars1260 on 2012-04-20
WILDMANNE39,

I tried the rate reduction you suggested.  I unfortunately cannot detect any difference in performance.   Especially in resolving DNS..

Thank You,
Bob

---

### Post by wildmanne39 on 2012-04-20
Hi, please set your wireless settings to match the settings in the screenshot.

If this does not help you can also go to Realtek site and download and install there driver or use ndiswrapper.
Thanks

---

### Post by otinanix on 2012-08-07
Hi there,
I 'm new in Ubuntu and Linux in general. In fact I just recently switched to Ubuntu a couple of days ago. I have a similar issue with my awus036h and thought that I should post it here instead of creating a new thread. I 'm on a macbook pro with native ubuntu 12.04 install. I 'm using the alfa for internet because the A.P. is far away and the built in airport cannot reach it. The problem is that while network manager shows that I 'm connected, I cannot surf. There are times when I am able to surf like there is no problem but that doesn 't last much. Maybe for a couple of minutes. Getting closer to the A.P. has the same results. I guess it's that DNS thing that you people mentioned above. One thing that I have noticed on the alfa is that the led indicator does not glow as bright as it does when using the card under osx. It's like it doesn 't receive enough power. Don 't know if that's the case though, I have read numerous posts and everywhere people are talking of driver issue. I have installed the latest drivers from realtek by the way.

Bellow I post the output of

cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod


I have tried editing the rc.local as suggested by wildmanne39 but the problem remains. I have also edit the connection settings to match the screenshots but that didn 't solve it either.
I' ld really appreciate if somebody could help me out. I hate the idea to have to use ndiswrapper. Thank you in advance!!
Here are the outputs

1. cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux pueblo 3.2.0-27-generic-pae #43-Ubuntu SMP Fri Jul 6 15:06:05 UTC 2012 i686 i686 i386 GNU/Linux

2. lspci -nnk | grep -iA2 net

0b:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) [168c:0024] (rev 01)
    Subsystem: Apple Inc. AR5BXB72 802.11abgn Mini PCIe Card [AR5008E-3NX] [106b:0087]
    Kernel driver in use: ath9k
--
0c:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8058 PCI-E Gigabit Ethernet Controller [11ab:436a] (rev 13)
    Subsystem: Marvell Technology Group Ltd. Device [11ab:00ba]
    Kernel driver in use: sky2

3. lsusb

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 007 Device 002: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 007 Device 003: ID 05ac:021b Apple, Inc. Internal Keyboard/Trackpad (ISO)
Bus 003 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI

4. iwconfig

lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:"ThomsonF6091E" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9F:CE:D6:5B  
          Bit Rate=48 Mb/s   Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:401  Invalid misc:1584   Missed beacon:0

wlan0     IEEE 802.11abgn  ESSID:off/any 
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         
eth0      no wireless extensions.

5. rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

6. lsmod

Module                  Size  Used by
btusb                  17912  2
pci_stub               12550  1
vboxpci                22882  0
vboxnetadp             25616  0
vboxnetflt             27211  0
vboxdrv               252228  3 vboxpci,vboxnetadp,vboxnetflt
r8187l                143411  0
snd_hda_codec_realtek   174134  1
snd_hda_intel          32765  2
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0
snd_rawmidi            25424  1 snd_seq_midi
rfcomm                 38139  12
bnep                   17830  2
joydev                 17393  0
hid_apple              13166  0
parport_pc             32114  0
bluetooth             158438  23 btusb,rfcomm,bnep
ppdev                  12849  0
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
usbhid                 41906  0
appletouch             17318  0
hid                    77367  2 hid_apple,usbhid
uvcvideo               67203  0
videodev               86588  1 uvcvideo
arc4                   12473  4
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rtl8187                56323  0
eeprom_93cx6           12653  1 rtl8187
applesmc               18978  0
input_polldev          13648  1 applesmc
ath9k                 117326  0
nouveau               712356  3
snd                    62064  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              436455  2 rtl8187,ath9k
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
ath9k_common           13781  1 ath9k
ath9k_hw              391523  2 ath9k,ath9k_common
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
drm                   197692  5 nouveau,ttm,drm_kms_helper
cfg80211              178679  4 rtl8187,ath9k,mac80211,ath
soundcore              14635  1 snd
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
wmi                    18744  1 mxm_wmi
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 nouveau
mac_hid                13077  0
apple_bl               13425  0
lp                     17455  0
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   53628  0

---

