---
title: "wireless connection"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by deephorizon on 2012-02-28
Hello everybody, I’m very new to Linux I meant very new to it but so far I like what I see a lot, I did install Ubuntu 11.10 in a Dell 8300 tower everything went smooth is working fine I have it connect to the internet with a wire from my modem the connection is working fine, but I like to make wireless conection, I have two Belkin routers one is model F5d6231-4 the other is a F5d9230-4 G plus MIMO, and also have al Belkin adapter, are any of these work with Linux or I have to buy router and adapter compatible this Linux, I did try to install the software but did not work or I do not know to do it, will appreciate your help I’m trying to read as much as I can to learn about Linux because I really like what I see.

---

### Post by pedja_portugalac on 2012-02-28
Every wireless router works with linux. You must click on the network icon, above right corner close to the clock, and choose yours.

---

### Post by musicman10489 on 2012-02-28
If anything were to **not** work, it would be your adapter. But you mentioned that it is a Belkin so I think you'll be fine. The closest thing to an "incompatible" adapter that I've had was an off-brand usb adapter that cut in and out somewhat randomly. It worked, just not very well ;)

That's the one of beauties of Linux, *wonderful* hardware support.

---

### Post by varunendra on 2012-02-28
Hi deephorizon, Welcome to the forums!

Try what pedja_portugalac suggested. If your wireless adapter is recognized and is natively supported in Linux, it should work out-of-box.

However, if you are having problems in connecting, or if the adapter is not recognized at all, please open a terminal (shortcut: **Ctrl+Alt+T**), run the following commands and post back their outputs here:
```

lsb_release -d
uname -mr
lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/network/interfaces
rfkill list all
```

While posting outputs, click on **# **at the top of the edit box to auto-generate 'code' tags, then copy-paste the outputs in-between those tags.

---

### Post by deephorizon on 2012-02-29
Thank you gang, I was able to connect wireless today it was not my hardware it was my setting it felt good I;m a long time windows user I feel free knowing that there is an option to windows and the better part is all free I can not believe it, once again thank you for your help.

---

### Post by CidNight on 2012-02-29
Hi everyone, I am having an almost identical problem and was wondering if anyone had any advice.  I started a thread yesterday but I think it got lost in the woods.  I am also a longtime Windows user and am very new to Linux, really liking it so far!  Here is the output that was asked for by *varunendra*.

bill@bill-MS-7325:~$ lsb_release -d
Description:    Ubuntu 11.10
bill@bill-MS-7325:~$ uname -mr
3.0.0-16-generic-pae i686
bill@bill-MS-7325:~$ lspci -nnk | grep -iA2 net
00:0a.0 Bridge [0680]: nVidia Corporation CK804 Ethernet Controller [10de:0057] (rev f3)
    Subsystem: Micro-Star International Co., Ltd. Device [1462:7325]
    Kernel driver in use: forcedeth
--
01:09.0 Network controller [0280]: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus [1814:0701]
    Subsystem: Ralink corp. RT2760 Wireless 802.11n 1T/2R Cardbus [1814:0701]
    Kernel driver in use: rt2800pci
bill@bill-MS-7325:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
bill@bill-MS-7325:~$ lsmod
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
vesafb                 13489  1 
binfmt_misc            17292  1 
nvidia               7098131  34 
ppdev                  12849  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80435  2 snd_intel8x0,snd_ac97_codec
arc4                   12473  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rt2800pci              18340  0 
rt2800lib              48909  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci
parport_pc             32114  1 
mac80211              393421  3 rt2800lib,rt2x00pci,rt2x00lib
psmouse                63474  0 
serio_raw              12990  0 
cfg80211              172427  2 rt2x00lib,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
eeprom_93cx6           12653  1 rt2800pci
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                 12905  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_intel8x0,snd_pcm
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
forcedeth              58103  0 
sata_nv                23379  2 
pata_amd               13753  0 
bill@bill-MS-7325:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:19:db:23:ea:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:128 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9920 (9.9 KB)  TX bytes:9920 (9.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:02:6f:69:c8:e6  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:6fff:fe69:c8e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14856096 (14.8 MB)  TX bytes:2928593 (2.9 MB)

bill@bill-MS-7325:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Quechee"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:78:B0:A8   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:33  Invalid misc:98   Missed beacon:0

bill@bill-MS-7325:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

bill@bill-MS-7325:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Thanks so much!

---

### Post by coolman98 on 2012-02-29
try a different adapter and any router will work welcome to ubuntu Yeahhhh been using fer three years and im 13 what what what!

---

### Post by varunendra on 2012-03-01
> **CidNight said:**
> Hi everyone, I am having an almost identical problem....
Hi CidNight,
Please see your [original thread]("http://ubuntuforums.org/showthread.php?p=11729874#post11729874") where I have answered you.

Best of luck!

---

