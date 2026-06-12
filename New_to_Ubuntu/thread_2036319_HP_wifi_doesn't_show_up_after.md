---
title: "HP wifi doesn't show up after"
date: 2012-08-01
forum: New to Ubuntu
---

### Post by iamsamami on 2012-08-01
HP wifi doesn't show up after recently installing Ubuntu onto Hp Netbook next to old Ubuntu installation when it went kapuuutt on me.
 
Wifi already wasn't showing up on original install, and when I installed on a divided partition I wasn't near a signal to get connected during install. Later when I got to a signal - configuration won't go through.
 
Is it possible the wifi device went kapuuutt? Could that have something to do with my system crapping out on me? How can I find out? Can I just get a wifi card to plug in to get internet to work again??

---

### Post by wildmanne39 on 2012-08-01
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by iamsamami on 2012-08-01
```
[SIZE=2] [/SIZE]
sam1@netbook-10-4-4:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux netbook-10-4-4 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
sam1@netbook-10-4-4:~$ lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb
02:00.0 Ethernet controller [0200]: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter [1969:1062] (rev c0)
Kernel driver in use: atl1c
Kernel modules: atl1c
sam1@netbook-10-4-4:~$ lsusb
Bus 005 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 174f:1105 Syntek 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
sam1@netbook-10-4-4:~$ iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry long limit:7 RTS thr:off Fragment thr:off
Power Management:off

sam1@netbook-10-4-4:~$ rfkill list all
0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no
sam1@netbook-10-4-4:~$ lsmod
Module Size Used by
binfmt_misc 6587 1 
ppdev 5259 0 
snd_hda_codec_idt 52042 1 
fbcon 35102 71 
tileblit 1999 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0 
vgastate 8961 1 vga16fb
joydev 8740 0 
snd_hda_intel 22069 2 
snd_hda_codec 74201 2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep 5412 1 snd_hda_codec
snd_pcm_oss 35308 0 
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70694 3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy 1338 0 
snd_seq_oss 26722 0 
snd_seq_midi 4557 0 
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 19130 2 snd_pcm,snd_seq
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
arc4 1153 2 
b43 163556 0 
i915 289715 3 
snd 54244 16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo 57438 0 
mac80211 205434 1 b43
drm_kms_helper 29329 1 i915
videodev 34425 1 uvcvideo
cfg80211 126528 2 b43,mac80211
intel_agp 24375 2 i915
soundcore 6620 1 snd
v4l1_compat 13251 2 uvcvideo,videodev
drm 163747 4 i915,drm_kms_helper
i2c_algo_bit 5028 1 i915
psmouse 63677 0 
serio_raw 3978 0 
led_class 2864 1 b43
atl1c 27955 0 
agpgart 31724 2 intel_agp,drm
snd_page_alloc 7076 2 snd_hda_intel,snd_pcm
video 17375 1 i915
output 1871 1 video
lp 7028 0 
parport 32635 2 ppdev,lp
usbhid 36110 0 
hid 67288 1 usbhid
ssb 38934 1 b43
sam1@netbook-10-4-4:~$ 

```

---

### Post by wildmanne39 on 2012-08-01
Hi, this card can be a problem with 10.04, did you install the restricted drivers for the card using a wired connection?

b43 in not correct for 10.04 you need the sta driver which is also the wl driver.
Thanks

---

### Post by iamsamami on 2012-08-01
> **wildmanne39 said:**
> Hi, this card can be a problem with 10.04, did you install the restricted drivers for the card using a wired connection?
 
I wasn't able to add anything during install except the iso image, but it ended up being the desktop version instead of netbook.
 
> **wildmanne39 said:**
> b43 in not correct for 10.04 you need the sta driver which is also the wl driver.
Thanks
 
Alright, can I download such driver and use aptget install?
 
Appreciate your replies,
, sam1

---

### Post by wildmanne39 on 2012-08-01
Hi, you need to have a wired internet connection then open synaptic and type bcm and remove the b43 driver and fw-cutter then do:
```
sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source bcmwl-modaliases
```
Reboot.
Thanks

---

### Post by iamsamami on 2012-08-01
O.K., I'll see what I can do with what I got.
Gotta go for now, might be a while b4 I get back on.
 
Thanks,
, sam1

---

### Post by iamsamami on 2012-09-06
Wild Man,
finally got a chance to get a land-line connection to internet; found a saved copy of this page and copied into a 'root' terminal the line you posted above. That got me started towards a wifi connection, but one of the files wouldn't finish installing.
anyway, while connected by lan -line, the update manager kicked in and let it download and install all available updates; rebooted.
O.K., I got wifi, but I still got one more little problem. Now I am requested to provide user keyring login. Again, I tried all the passwords I can think of; none of 'em work
I can see wifi signals to connect to, but I need to (con)figure keyring login.
Can you help me with that???

---

