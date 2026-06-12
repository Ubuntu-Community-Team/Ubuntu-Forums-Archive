---
title: "Grey wireless enabling box..."
date: 2011-10-07
forum: New to Ubuntu
---

### Post by Innernet on 2011-10-07
Hi.
Checked existing posts on the subject and will try a couple of things, but meanwhile:

On a Compaq Presario CQ50 laptop,
Wireless connection is **via USB port**,

When installed 10.10 last year, wireless worked flawlessly installing no drivers of any kind. 
Never had to type any adress, or IPV4, or IPV6, or gateway, or subnet mask, or IP address, or server...
Never typed anything related to WLAN ID's
Worked p e r f e c t since day 1 doing nothing to the OS/laptop
No keyboard button to enable wireless ever touched,
Always searched and connected automatically to internet at end of booting. Perfect.
I have never installed any updates, and feel happy without them.

Went on a trip and at a friend's house, used his wireless; worked fine.
Am back and **my** wireless does not work at all any more, (*,)
the 'wireless enable' checkbox is grey; unable to find where/how to enable it.  The wifi button does nothing (but was never needed before)

Had to swap hard drive to the Windows one to post this. So the USB wireless hardware is good.
It has to be a setting.  Everything I checked is in 'automatic' mode

Thanks.

---

### Post by wildmanne39 on 2011-10-07
Hi, please post the results of these commands:
```
lsusb
```
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
iwconfig
```
```
lsmod
```
```
sudo iwlist scan
```
```
rfkill list all
```
clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Innernet on 2011-10-07
Thanks.
Am using the Windows hard drive now, will swap hard drives and do your request, but will take a while as I have to swap drives again to be able to access internet.

What would the [rfkill unblock all] do; as learned in other similar older post ?

---

### Post by wildmanne39 on 2011-10-07
Hi, this command rfkill unblock all might unblock all your connections but we do not know if that is the problem, until we see the information.

I will need to see all the output from the commands, you can put it on a flash drive then use the flash drive to paste it here.
Thank you

---

### Post by Innernet on 2011-10-07
Hi. This is the report :

externet@Externet:~$ lsusb
Bus 004 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
=================================================================

externet@Externet:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
Linux Externet 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
==================================================================

externet@Externet:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             unavailable
  Default:           no
  HW Address:        00:00:00:00:00:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            forcedeth
  State:             unavailable
  Default:           no
  HW Address:        00:1D:72:72:04:3F

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        00:22:69:7A:D9:47

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
===================================================================

externet@Externet:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
=======================================================================
          
externet@Externet:~$ lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_nvhdmi    12879  1 
snd_hda_codec_conexant    29736  1 
joydev                  8735  0 
arc4                    1165  2 
nouveau               516971  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ath9k                  88756  0 
snd_seq_midi            4588  0 
ath9k_common            5982  1 ath9k
ttm                    56633  1 nouveau
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 nouveau
snd_seq_midi_event      6047  1 snd_seq_midi
ath9k_hw              292297  2 ath9k,ath9k_common
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168054  4 nouveau,ttm,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2870sta             405890  0 
agpgart                32011  2 ttm,drm
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
hp_wmi                  5191  0 
i2c_algo_bit            5168  1 nouveau
crc_ccitt               1351  1 rt2870sta
snd                    49006  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18712  0 
led_class               2633  1 ath9k
output                  1883  1 video
psmouse                59033  0 
serio_raw               4022  0 
soundcore                880  1 snd
k10temp                 2607  0 
i2c_nforce2             5179  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
shpchp                 29886  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
forcedeth              49433  0 
libahci                21667  3 ahci
pata_amd                8746  0 
=================================================================

externet@Externet:~$ sudo iwlist scan
[sudo] password for externet: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

wlan1     Interface doesn't support scanning : Network is down

externet@Externet:~$ 



Sorry , I missed the last [rfkill list all]

---

### Post by wildmanne39 on 2011-10-07
Hi, you have an internal card and the usb adapter, if you want to use the usb adapter we will need to blacklist the driver for the internal card, please let me know which way you want to go with this both can not connect at the same time they conflict with each other.
Thank you

---

### Post by Innernet on 2011-10-07
The missing one is :


externet@Externet:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yesreless LAN
	Soft blocked: yes
	Hard blocked: yes

========================================

And after the command [rfkill unblock all] the result is:


externet@Externet:~$ rfkill list all
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
=======================================

There has been NO change in drivers nor hardware in the compfuser;  would like your best suggestion to bring back the previous settings that worked very well a looong time.

Thanks.

---

### Post by wildmanne39 on 2011-10-07
Hi, you have an internal card and the usb adapter, if you want to use the usb adapter we will need to blacklist the driver for the internal card, please let me know which way you want to go with this both can not connect at the same time they conflict with each other.

Did you use the usb adapter when it was working good? 
Thank you

---

### Post by Innernet on 2011-10-07
Yes, the connections and hardware have not changed.

In the good past, while booting, the blue indicator for wifi button always came on and then off, and the whole thing ended seizing the USB WLAN with no problems.
Am an ignorant in many things, but believe the wifi/blue light button is for the internal 'antennas or internal radio link' to be enabled; not to enable/disable the USB WLAN.

So I will proceed on whatever you suggest.

If I have to reload 10.10 I have no problem but would prefer a method that will not erase my data while redoing the Ubuntu OS.

The laptop has never had Windows and Linux merged in a hard drive.  When I decided to install Ubuntu I did it on a new hard drive and kept the Windows as backup; as it is working now.  Takes some screws to swap, but the functionality of using the compfuser is not risked.

Thanks

---

### Post by thatguruguy on 2011-10-07
As an aside, why do you write "compfuser"?

As a second aside, why not just use an external hard drive, or place one of the drives in a casing and use it as an external hard drive?

---

### Post by wildmanne39 on 2011-10-07
Hi, let's do this then. Plug your usb adapter in and run these commands please:
```
sudo su
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist.conf
exit
```
Then
```
sudo modprobe rt2870sta
```
Cross your fingers
Thank you

---

### Post by bkratz on 2011-10-08
> **wildmanne39 said:**
> Hi, let's do this then. Plug your usb adapter in and run these commands please:
```
sudo su
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist.conf
exit
```Then
```
sudo modprobe rt2870sta
```Cross your fingers
Thank you


@wildmanne, aren't we going to have to temporarily remove ath9k with

sudo rmmod -f ath9k  if the machine is not rebooted??? If rebooted the blacklist should take care of it for us and congratulations!

---

### Post by Innernet on 2011-10-08
Sorry for the delay. I was unable to continue yesterday.

Unsuccessful.   The same condition persisted.

After reboot, goes back to soft and hard blocked.  When doing the [rfkill unblock all] only the 'soft' becomes enabled; only until the next reboot where all are blocked again.

-------------------

Why did I write 'compfuser' ?  Because that is what computers do, confusing.  A guru should know that.
A second external drive ? On a laptop ? What for?  For Windows ? I do not want Windows; Linux works much better, when it works.

Thanks.

---

### Post by wildmanne39 on 2011-10-08
Hi, let's try this please:

Please do:
```
gksudo gedit /etc/rc.local
```
Add your three lines above exit 0 
```
rmmod -f rt2870sta
rfkill unblock all
modprobe rt2870sta
```
@bkratz Thank you and yes I believe you are correct.
Proofread carefully, save and close gedit. Reboot and tell us if it's working.
Thank you

---

### Post by Innernet on 2011-10-08
Nope.  :-(   - Gave up-.

Reinstalled wiping all hard drive as there is no option to keep settings as keyboard layouts, languages, many preferences... and data files.

Am on the net with 11.04 now.   Brutally slower than it was with 10.10, but hey, that is what compfusers do.  Confuse.

Thanks for your patience.  We may never find out where the bug was.

---

### Post by wildmanne39 on 2011-10-08
Hi, as long as you are satisfied that is what matters.
Thank you

---

### Post by Innernet on 2011-10-09
Hi all.
Well, I felt I had to come back and let know...

After solving the wireless hickup by the undesired method of reloading Ubuntu; found that 11.04 misbehaved being veeeery slow as told on post #15

The 'System monitor' feature showed both CPUs showing turns into 100% activity with nothing going on, while just idling.

Got angry and wiped 11.04 and went back to 10.10   It is smooth fast sailing again.

In my very poor computer skills, **seems** that the cure for the probem **may** had been installing the original WinVista hard drive to gain access to enabling wireless; which was elusive under Ubuntu.

The _hardware seems to latch_ into enabled or disabled status and Linux is unable to deal with.

10.10 just reloaded did not need ANY setup/loading/drivers... to jump onto the net. 

Thanks for your help again, wildmanne39.

---

