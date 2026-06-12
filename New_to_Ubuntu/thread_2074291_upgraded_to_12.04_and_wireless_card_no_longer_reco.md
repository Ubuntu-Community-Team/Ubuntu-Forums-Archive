---
title: "upgraded to 12.04 and wireless card no longer recognised"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by LvonR on 2012-10-21
Hi, 

I have recently upgraded to Ubintu 12.04 and now find that I no longer have any wireless connectivity.  It seems that the wireless card is not even recognised.  An internet search led me to a question asked on this forum where the member was asked to run lspci - nn | grep 0280 and post the answer to give a hint as to what was possibly the reason.

So I did likewise - the reply came as

06:05.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Caltexico2] Network Connection [8086:4220] (rev 05)

which means not a lot to me at thi time!  I assume this identifies the card.  Can anyone give me assistance please.

Thanks in advance.

---

### Post by offgridguy on 2012-10-21
Ubuntu 12.04 may not have downloaded the device driver automatically, you may have to go to
the Intel Corporation website to find a linux compatible driver to download.

---

### Post by LvonR on 2012-10-21
Thanks for that - I have now looked on the Intel site and it says that "drivers for 2200 devices can be found in any recent kernel so it is not necessary to obtain the source code", also "The iwlwifi driver has been merged into mailine kernel since 2.6.24. If you are using kernels after this release, please use the intree (drivers/net/wireless/iwlwifi) driver directly"

I read this to mean that I do not need another driver? How do I tell which kernel I have?

---

### Post by westcoast01 on 2012-10-21
No offence but is it turned on? If you know how to open a terminal might try ..  sudo apt-get update .. I just did an upgrade and my wireless was not turned on sooo??? Best of luck.

---

### Post by offgridguy on 2012-10-21
> **westcoast01 said:**
> No offence but is it turned on? If you know how to open a terminal might try ..  sudo apt-get update .. I just did an upgrade and my wireless was not turned on sooo??? Best of luck.

Good thought, first things first, By the way LvonR you can open a terminal by
ctrl+alt+t, but you probably knew that.

---

### Post by LvonR on 2012-10-22
No offence taken - all ideas are good ideas!

I can open a terminal - I did so to run lspci.

The upgrade to 12.04 was done via the wireless and worked fine - until rebooted after the upgrade at which point it no longer worked.

All the wireless connection settings are correct if I check Edit Connections, however the Wireless Networks shows " device not managed".

So when you say is it turned on what do you mean - is there something else I should do to turn it on?

---

### Post by LvonR on 2012-10-22
Oh, and I meant to say that Enable Wireless is ticked.

---

### Post by gerrman97 on 2012-10-22
try a reset. open up the computer and pull out the wireless card. wait about an hour and put it back in. i tried it before, kinda worked for my computer but not all of the way cuz something is wrong with the power managing in the motherboard.

---

### Post by LvonR on 2012-10-22
Thanks German97 - sounds like a last resort but I may get t that!

Since my last post I have unticked "Enable Wireless networks" and now it is greyed out and is not reselectable!

I have also run sudo apt-get update - which worked Ok but didn't solve the problem - thanks anyway.

---

### Post by plucky on 2012-10-22
Post output for ```
rfkill list
```

---

### Post by LvonR on 2012-10-24
OK rfkill list gives


0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by plucky on 2012-10-24
> **LvonR said:**
> OK rfkill list gives


0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


Why is it showing two wireless interfaces?

What does ```
iwconfig
lsmod
``` show you?

---

### Post by LvonR on 2012-10-27
Hi, sorry for delay in replying - work gets in the way!
iwconfig shows

lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"Accplus1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7D:47:27:37   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/100  Signal level=-72 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


lsmod shows

Module                  Size  Used by
dm_crypt               22528  0 
arc4                   12473  2 
lib80211_crypt_wep     12746  1 
joydev                 17393  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
snd_intel8x0           33455  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
pcmcia                 39791  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            17292  1 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ipw2200               146210  0 
libipw                 46701  1 ipw2200
snd                    62064  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 ipw2200,libipw
psmouse                96619  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
serio_raw              13027  0 
soundcore              14635  1 snd
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211               14040  3 lib80211_crypt_wep,ipw2200,libipw
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414939  3 
8139too                23283  0 
8139cp                 22633  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
wmi                    18744  1 acer_wmi
video                  19068  1 i915


I hope this means more to you than it does to me!  Many thanks for your assistance.

---

### Post by NikTh on 2012-10-27
Hi , 

please open a terminal and post the results of bellow commands 

```
lspci -nnk | grep -iA2 net 
cat /etc/network/interfaces
cat /etc/resolv.conf 
nmcli nm status
```You have to put the results between these brackets **[noparse]```
the results here
```[/noparse]** so can be easy to read. 

Thank you.

---

### Post by plucky on 2012-10-27
> eth1 IEEE 802.11bg ESSID:"Accplus1"
Mode:Managed Frequency:2.437 GHz Access Point: 00:1D:7D:47:27:37
Bit Rate:54 Mb/s Tx-Power=20 dBm Sensitivity=8/0
Retry limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality=48/100 Signal level=-72 dBm Noise level=-88 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


Do you recognise that Access Point? 

Is that your router?

---

### Post by LvonR on 2012-11-04
```
lspci -nnk | grep -iA2 net 
06:05.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
    Subsystem: Intel Corporation Device [8086:2701]
    Kernel driver in use: ipw2200
--
06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:006a]
    Kernel driver in use: 8139too

```
```
 cat /etc/network/interfaces
auto lo
iface lo inet loopback
iface eth1 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:1347165191024
wireless-essid Accplus1

auto eth1


```
```
 /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1

```




[/code]
[code]nmcli nm status
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       enabled         enabled    enabled         disabled  
[/code

---

