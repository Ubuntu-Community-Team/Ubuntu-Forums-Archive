---
title: "Slow internet while using Ubuntu"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by lordboobatron on 2012-03-25
Hi, I'm brand new to Ubuntu and Linux altogether. I believe I installed Ubuntu using Wubi, in order to dual boot it along with Windows 7. I'm running Ubuntu 11.10.

 Everything seems to work find, and I'm starting to like using Ubuntu, but for some reason my wireless internet always runs slowly on Ubuntu. It still runs normally on Windows, only slow on Ubuntu. 

I've noticed the speed sort of fluctuates a lot. While it's usually running slow, sometimes it'll run at it's faster, normal speed. It's weird, and it's annoying!

I'm not sure what kind of information you guys need in order to assess this problem. So I'll just start off posting my router type: NETGEAR WNR834Bv2

Thanks.

---

### Post by wildmanne39 on 2012-03-25
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

### Post by d4m1r on 2012-03-25
Please complete a test at both speedtest.net and pingtest.net (under Windows 7 AND Ubuntu) and post the results here.

---

### Post by lordboobatron on 2012-03-25
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux ubuntu 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169
--
03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlagn

```

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:d104 Suyin Corp. 
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 003: ID 04e8:681c Samsung Electronics Co., Ltd Galaxy Portal/Spica Android Phone

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Longhi"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:3F:1A:84:9C   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4872  Invalid misc:102   Missed beacon:0


```

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
Module                  Size  Used by
usb_storage            57901  0 
uas                    18027  0 
cdc_acm                26857  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
rfcomm                 47946  0 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330815  1 
arc4                   12529  2 
snd_hda_intel          33390  4 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
i915                  571251  4 
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlagn                314257  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         42558  1 i915
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
drm                   236290  5 i915,drm_kms_helper
snd_timer              29991  2 snd_pcm,snd_seq
uvcvideo               72711  0 
mac80211              462046  1 iwlagn
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               92992  1 uvcvideo
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73882  0 
i2c_algo_bit           13423  1 i915
soundcore              12680  1 snd
cfg80211              199630  2 iwlagn,mac80211
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
v4l2_compat_ioctl32    17083  1 videodev
serio_raw              13166  0 
video                  19412  1 i915
joydev                 17693  0 
sparse_keymap          13890  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
mmc_block              22923  2 
r8169                  52788  0 
ahci                   26002  1 
libahci                26861  1 ahci
sdhci_pci              14032  0 
sdhci                  32166  1 sdhci_pci

```

---

### Post by wildmanne39 on 2012-03-25
Hi, try this if it works and it usually does we will need to make it permanent:
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up
```
do not reboot after running these commands.
Thanks

---

### Post by lordboobatron on 2012-03-25
Awesome! this seems to have worked! :]
Before this, i was having trouble completing a run of speedtest.net, but right after trying this, it worked fast perfectly!

[[IMG]http://www.speedtest.net/result/1855800564.png[/IMG]](http://www.speedtest.net)

---

### Post by idoitprone on 2012-03-25
> **lordboobatron said:**
> Awesome! this seems to have worked! :]
Before this, i was having trouble completing a run of speedtest.net, but right after trying this, it worked fast perfectly!

[[IMG]http://www.speedtest.net/result/1855800564.png[/IMG]]("http://www.speedtest.net")

```
sudo echo "options iwlagn 11n_disable=1" >> /etc/modprobe.d/iwlagn.conf
```if wildmann39 suggestion works then i guess you have configure you kernel modules

run that command above in the terminal
copy paste in terminal

---

### Post by wildmanne39 on 2012-03-25
Hi, I am glad it work and thanks idoitprone good job.

---

### Post by lordboobatron on 2012-03-25
Thanks i appreciate it a lot!

just checking, i typed the last thing into terminal and got this:
```
bash: /etc/modprobe.d/iwlagn.conf: Permission denied

```

is that normal?

---

### Post by wildmanne39 on 2012-03-25
Hi, did you just copy and past the command?

You can do it this way:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
Add one line:
```
options iwlagn 11n_disable=1
```
save gedit, close and reboot.
Thanks

---

### Post by lordboobatron on 2012-03-25
Yeah I just copy and pasted the command. I did your way and rebooted, everything works fine with my internet now. Thanks again!

---

### Post by wildmanne39 on 2012-03-25
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by matt_symes on 2012-03-25
Hi

Just for completeness in this thread, that command line command can be run in a couple of ways to stop it getting the permissions problems.

```
sudo bash -c 'echo "options iwlagn 11n_disable=1" >> /etc/modprobe.d/iwlagn.conf'
```

or

```
echo 'options iwlagn 11n_disable=1' | sudo tee -a /etc/modprobe.d/iwlagn.conf
```

It's the appending to the file that requires root privileges and not the echo command.

I didn't know about that module parameter for iwlagn. Thanks for that wildmanne39. I've learnt something useful from this thread.

Kind regards

---

### Post by wildmanne39 on 2012-03-25
Hi, thank you matt_symes for adding your knowledge it is appreciated.

---

### Post by idoitprone on 2012-03-26
> **wildmanne39 said:**
> Hi, I am glad it work and thanks idoitprone good job.

i didnt do anything i;m just the idoit that is trollin around

opps the nuisance of bash confuses me. Bourne too smart compare to moi

---

