---
title: "Wifi connects but no internet"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by javalsu on 2012-05-22
I'm running ubuntu 12.04 lts

I've got a samsung qx-411 laptop

It's got an intel centrino wireless-n + wimax 6150

I'm connecting to a linksys router WRT160N with firmware v3.3.03.

Wired connections work fine, but the wifi doesn't.
It finds the ssid by itself, and connects with no issue but I can't ping the router or any other computers on the network.

However, I can view the dhcp table on the router and see that it has a connection for the laptop and has an IP addressed assigned to it, and I can also view the IP address on ubuntu under the network connection.

Any ideas?

---

### Post by wildmanne39 on 2012-05-22
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by javalsu on 2012-05-22
Here you go

```

javier@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
javier@ubuntu:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
    Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
    Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c0a0]
    Kernel driver in use: r8169
javier@ubuntu:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"kavier" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:18:C7:3A:D8  
          Bit Rate=150 Mb/s   Tx-Power=15 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-35 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:43  Invalid misc:538   Missed beacon:0

eth0      no wireless extensions.

javier@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
javier@ubuntu:~$ lsmod
Module                  Size  Used by
parport_pc             32866  0
ppdev                  17113  0
lp                     17799  0
parport                46562  3 parport_pc,ppdev,lp
rfcomm                 47604  0
bnep                   18281  2
bluetooth             180104  10 rfcomm,bnep
joydev                 17693  0
snd_hda_codec_hdmi     32474  1
snd_hda_codec_realtek   223867  1
nouveau               774571  0
i915                  468651  3
ttm                    76949  1 nouveau
drm_kms_helper         46978  2 nouveau,i915
drm                   242038  6 nouveau,i915,ttm,drm_kms_helper
arc4                   12529  2
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
i2c_algo_bit           13423  2 nouveau,i915
snd_hda_intel          33773  3
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
snd_rawmidi            30748  1 snd_seq_midi
uvcvideo               72627  0
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlwifi               328352  0
video                  19596  2 nouveau,i915
mac_hid                13253  0
mac80211              506816  1 iwlwifi
psmouse                87603  0
serio_raw              13211  0
cfg80211              205544  2 iwlwifi,mac80211
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0
r8169                  62099  0
```

---

### Post by wildmanne39 on 2012-05-22
Hi, plese do:
```
gksudo gedit /etc/pm/power.d/wireless
```

(this will create or edit a configuration file that will override the default powermanagement behavior) and enter the following: 
#!/bin/sh

```
/sbin/iwconfig wlan0 power off
```

above exit0, then save gedit and close.

```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Add one line:
```
options iwlwifi 11n_disable=1
```
Reboot
Thanks

---

### Post by javalsu on 2012-05-22
That worked! Thanks so much.

One quick question.  Is it normal for my laptop to run hotter in ubuntu?  I think it might be the graphic card switching.

---

### Post by wildmanne39 on 2012-05-22
Hi, your welcome! please use the thread tools at the top of the page to mark the thread solved.

It can someties caused by grapic card drivers you can install jupiter and it helps.
[http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html](http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html)
Thanks

---

### Post by gillecaluim on 2012-08-19
I'm having a similar problem....to save time I've run the previous diagnostics ;)
Here's the output:

*@server:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:47:13:66
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45

eth1      Link encap:Ethernet  HWaddr 00:11:6b:d0:35:fd
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fed0:35fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14048 (14.0 KB)  TX bytes:39729 (39.7 KB)
          Interrupt:19 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:27468 (27.4 KB)  TX bytes:27468 (27.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5a:c0:bb:76
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5aff:fec0:bb76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:114187 (114.1 KB)  TX bytes:34366 (34.3 KB)

root@server:~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable


when I ping....why is it trying to reach eth0 (192.168.1.4) instead of the gateway???  Is that the root of the problem?

---

### Post by perw on 2013-05-21
I had the same problem on a Fujitsu-Siemens Lifebook S6420 running 12.04 when on vacation in Canada connecting to a WRT310N. 
I've never experienced that problem before when at home or at work accesing different brands of routers/APs.
Just by chance I also had brought 13.04 on an USB stick with me and had no problems accessing Internet running from the live verson on the stick. Not wanting to upgrade, I had to find another solution.

Luckily the suggestions from Wild Man worked like a charm :D 

Thanks a lot!!

---

