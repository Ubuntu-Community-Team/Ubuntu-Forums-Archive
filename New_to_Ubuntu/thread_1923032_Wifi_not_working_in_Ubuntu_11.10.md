---
title: "Wifi not working in Ubuntu 11.10"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by kmann on 2012-02-09
I'm completely  new to Ubuntu. I downloaded it and immediately ran into a huge problem: no wifi. With a wired connection it works like a charm, but away from my wired modem it won't connect. I've seen similar threads but they were too complicated for me to understand. I literally just found out how to open terminals, and keep in mind I'm only 15, so please keep your advice step by step and extremely simple. I'm sorry if I begin to ask alot of questions but I would like to have this working.

Basic info: I'm using a Lenovo B-575 laptop w/ 4 gigabytes of RAM and a 250 gigabyte hard drive. It hasn't been tampered with or anything apart from the Ubuntu download. Now, I know that there is more info I need to post but I'm not sure what it is. So please tell me exactly what I need to do as simply and clearly as you can. I appreciate any help you can give me. Thanks.

---

### Post by wolfen69 on 2012-02-09
With your wired connection plugged in, hit the windows key and type *additional drivers*. But it will pop up before you are finished typing it. Open additional drivers and see if a driver is offered for download.

---

### Post by wildmanne39 on 2012-02-10
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here if you do not have any wireless drivers in additional drivers:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Neal12 on 2012-02-10
#neal@neal-desktop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux neal-desktop 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 15:59:53 UTC 2012 i686 i686 i386 GNU/Linux
neal@neal-desktop:~$ lspci -nnk | grep -iA2 net
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: ASRock Incorporation Device [1849:8139]
    Kernel driver in use: 8139too
neal@neal-desktop:~$ iwcinfig
No command 'iwcinfig' found, did you mean:
 Command 'iwconfig' from package 'wireless-tools' (main)
iwcinfig: command not found
neal@neal-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

neal@neal-desktop:~$ rfkill list all
neal@neal-desktop:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
vesafb                 13489  1 
binfmt_misc            17292  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ppdev                  12849  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
nvidia               7098131  34 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
parport_pc             32114  1 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
8139too                23283  0 
8139cp                 22636  0 
floppy                 60310  0 
neal@neal-desktop:~$ 
What would this tell you Please?

---

### Post by wildmanne39 on 2012-02-10
Hi, first please copy and paste all commands for accuracy iwconfig has a typo.

Is that all the information from the ```
lsmod
```
command?

You wireless adapter did not show up is it a usb adapter? if it is please post:
```
lsusb
```
if not check your bios and make sure it is turned on, if this is a desktop make sure it is seated good or move the wireless card to a new pci slot.

Please check and see if rfkill package is installed if not install it then run:
```
rfkill list all
```
Thanks

---

### Post by kmann on 2012-02-11
Wildmanne 39: 


kylan@kylan-Lenovo-B575:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux kylan-Lenovo-B575 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux

kylan@kylan-Lenovo-B575:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Lenovo Device [17aa:3975]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: Lenovo Device [17aa:f101]
    Kernel driver in use: rt2800pci

kylan@kylan-Lenovo-B575:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

kylan@kylan-Lenovo-B575:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

kylan@kylan-Lenovo-B575:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
joydev                 17393  0 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
rts5139               279514  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_codec_conexant    52418  1 
snd_hda_codec_hdmi     31426  1 
arc4                   12473  2 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
rt2800pci              18340  0 
binfmt_misc            17292  1 
rt2800lib              48717  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48114  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              272785  3 rt2800lib,rt2x00pci,rt2x00lib
psmouse                73673  0 
cfg80211              172392  2 rt2x00lib,mac80211
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              12990  0 
snd_seq_midi           13132  0 
eeprom_93cx6           12653  1 rt2800pci
k10temp                12990  0 
snd_rawmidi            25241  1 snd_seq_midi
sp5100_tco             13495  0 
i2c_piix4              13093  0 
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2756885  108 
wmi                    18744  0 
soundcore              12600  1 snd
video                  18908  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci

---

### Post by Neal12 on 2012-02-11
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17292  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               7098131  38 
soundcore              12600  1 snd
parport_pc             32114  1 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
8139too                23283  0 
8139cp                 22636  0 
floppy                 60310  0 
neal@neal-desktop:~$

---

### Post by Neal12 on 2012-02-11
put in and ran  the cd, then I think it installed, but don't see it.
I'm running with a Zonet USB wireless adapter (ZEW2545) plugged nto my desktop.

---

### Post by wildmanne39 on 2012-02-12
Hi kmann, please try:
```
gksudo gedit /etc/modprobe.d/rt2800pci.conf
```
Add a single line:
```
options ath9k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.

If your wireless does not come on check and make sure your wireless is turned on with the switch on your computer or it could be a key like fn f5 that turns it on because it is showing the wireless is off.
Thanks

---

### Post by wildmanne39 on 2012-02-12
Hi Neal12 I still need to see the output of:
```
lsmod
```
Thanks

---

### Post by cooljaini on 2012-02-15
abhishek@abhishek-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux abhishek-laptop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
abhishek@abhishek-laptop:~$ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Kernel driver in use: r8169
	Kernel modules: r8169
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
	Kernel driver in use: wl
	Kernel modules: wl, ssb
abhishek@abhishek-laptop:~$ iwconfig
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

abhishek@abhishek-laptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
abhishek@abhishek-laptop:~$ lsmod
Module                  Size  Used by
ppp_deflate             3682  0 
zlib_deflate           19568  1 ppp_deflate
bsd_comp                4811  0 
ppp_async               6734  1 
crc_ccitt               1339  1 ppp_async
option                 20198  1 
usbserial              33694  4 option
rfcomm                 33453  8 
sco                     7949  2 
bridge                 45614  0 
stp                     1655  1 bridge
bnep                    9436  2 
l2cap                  30656  16 rfcomm,bnep
btusb                  11053  2 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
nls_utf8                1069  0 
isofs                  29250  0 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      52042  1 
snd_hda_intel          22069  2 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
joydev                  8740  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  289715  3 
drm_kms_helper         29329  1 i915
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
lib80211_crypt_tkip     7596  0 
uvcvideo               57438  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   163747  4 i915,drm_kms_helper
videodev               34425  1 uvcvideo
psmouse                63677  0 
v4l1_compat            13251  2 uvcvideo,videodev
lp                      7028  0 
i2c_algo_bit            5028  1 i915
dell_wmi                1793  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   1959598  0 
serio_raw               3978  0 
video                  17375  1 i915
dell_laptop             6888  0 
parport                32635  2 ppdev,lp
soundcore               6620  1 snd
output                  1871  1 video
lib80211                5046  2 lib80211_crypt_tkip,wl
dcdbas                  5422  1 dell_laptop
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
intel_agp              24375  2 i915
agpgart                31724  2 drm,intel_agp
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            39969  0 
r8169                  34140  0 
mii                     4381  1 r8169
ahci                   32680  3

---

### Post by sadaruwan12 on 2012-02-15
I don't know if this will help you but try this as well.

```

$ sudo rmmod -f ideapad_wlan

$ sudo rfkill unblock all

$ rfkill list all

```

After the above steps if it starts to work let me know then we'll work on how to make it permanent.

---

### Post by wildmanne39 on 2012-02-15
Hi cooljaini, there is a problem with the wireless driver for your card with ubuntu using the earlier kernels so please plug in a wired internet connection and update all packages then post the output of:
```
cat /etc/lsb-release; uname -a
```
so we can make sure the kernel upgraded to at least 2.6.33 if it did then run these commands.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install b43-fwcutter
```
watch the terminal for errors, after the commands are done unplug your wired connection and reboot and it should be working.
Thanks

---

### Post by Neal12 on 2012-02-16
neal@neal-desktop:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
vesafb                 13489  1 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
binfmt_misc            17292  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
nvidia               7098131  38 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
parport_pc             32114  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
8139too                23283  0 
8139cp                 22636  0 
floppy                 60310  0 
neal@neal-desktop:~$

---

### Post by Neal12 on 2012-02-16
Everything is working great on my laptop.  That is running with Broadcom.

---

