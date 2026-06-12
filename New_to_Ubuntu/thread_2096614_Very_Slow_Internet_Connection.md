---
title: "Very Slow Internet Connection"
date: 2012-12-20
forum: New to Ubuntu
---

### Post by philwx on 2012-12-20
I am new to linux and am experiencing problems with my wired network connection - slow internet browsing, online speed test was 6mbps. Some web sites load fine, others not at all, others apparently with no css. This happens with firefox and chrome browsers.

I have installed the correct card drivers following this post: [http://ubuntuforums.org/showthread.php?t=1964200](http://ubuntuforums.org/showthread.php?t=1964200)

I have disabled ipv6 for the network connection (set to ignore).

I have searched the many solutions online but most are either for wireless or peter out.

I am using 12.04 using the kxstudio 3.2.0-35-lowlatency kernel. Here are some command outputs that might help.

```
phil@phil-G41D3:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION=&quot;KXStudio 12.04.1&quot;
Linux phil-G41D3 3.2.0-35-lowlatency #34-Ubuntu SMP PREEMPT Tue Dec 18 18:13:23 UTC 2012 i686 i686 i386 GNU/Linux
``````
phil@phil-G41D3:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Biostar Microtech Int'l Corp Device [1565:2308]
    Kernel driver in use: r8101
``````
phil@phil-G41D3:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0557:8021 ATEN International Co., Ltd
Bus 003 Device 003: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
``````
phil@phil-G41D3:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:67:3b:ca:24  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:fe3b:ca24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:15373444 (15.3 MB)  TX bytes:1767091 (1.7 MB)
          Interrupt:42 Base address:0x8000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:894 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:70076 (70.0 KB)  TX bytes:70076 (70.0 KB)
``````
phil@phil-G41D3:~$ lsmod
Module                  Size  Used by
rfcomm                 38063  0
bnep                   17830  2
bluetooth             158089  10 rfcomm,bnep
binfmt_misc            17292  1
snd_hda_codec_realtek   174313  1
snd_hda_codec_hdmi     31775  1
snd_hda_intel          28669  0
snd_hda_codec         109527  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_aloop              18892  0
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_aloop
snd_seq_midi           13132  0
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_aloop,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
i915                  419354  2
drm_kms_helper         45466  1 i915
drm                   197602  3 i915,drm_kms_helper
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
ppdev                  12849  0
video                  19068  1 i915
parport_pc             32114  1
joydev                 17322  0
lp                     17455  0
psmouse                96718  0
mac_hid                13077  0
serio_raw              13027  0
parport                40904  3 ppdev,parport_pc,lp
usbhid                 41937  0
hid                    77428  1 usbhid
r8101                  90453  0
floppy                 60184  0
```

---

### Post by philwx on 2012-12-28
My network problems were solved by updating my old vigor2600 router's firmware. 

Hurrah!

---

### Post by thenox on 2013-01-03
Good to know. I'm having similar issues. I'll have to check my wireless firmware.

---

