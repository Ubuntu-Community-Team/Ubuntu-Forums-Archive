---
title: "disabling wireless network in ubuntu 12.10"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by mr1holmes on 2012-10-25
hi.. i'm completely new to ubuntu.
i have dual os (win7 and ubuntu 12.10) on sony vaio.
i want to turn off my wireless network as i never use it.
i've already tried disabling wireless network from windows.
in ubuntu it says "wireless is disabled by hardware switch" but the LED  of wireless on my laptop is still turned on.(any function key is not  provided on my laptop to turn off the wireless directly).
in windows "vaio smartnetwork" automatically turns off the wireless when the system boots but in ubuntu it never goes off.
it's my first day of using ubuntu and i'm loving it... except this thing.
please help..

---

### Post by NikTh on 2012-10-25
Hi and Welcome to Ubuntu world (-Forums) . 

How you installed Ubuntu ? is this a regular installation or wubi (from within Windows OS).

Please open a terminal (CTRL+ALT+T) and give the results of these  commands 

```
lspci -nnk | grep -iA2 net 
lsmod 
nmcli nm status
```Post back here full results and put the results between the brackets **[noparse]```
the results here
```[/noparse]** so can be easy to read. 

Thank you.

---

### Post by danielbauwens on 2012-10-25
I don't know if this works for you too, but on my keyboard I can press
```
Fn-F2
```To deactivate the internet connection.
Or you can just right-click the Internet Connection *thingie* on the bar on the top of your screen and select 

```
Enable Wireless
```

Hope this helped a bit.
NikTh knows a lot more then me though, so I would suggest listening more to him then to me.

---

### Post by NikTh on 2012-10-25
> **danielbauwens said:**
> 
NikTh knows a lot more then me though, so I would suggest listening more to him then to me.

Hah ! :P

And how do you know that ? 

Maybe the solution is just as simple as you provided. 

Don't judge someones knowledges from the beans or the rank. 

Maybe you (who have 34 beans=posts in the support section) you know many more things from a user with 20.000 beans 

After all , [beans are just for fun](http://ubuntuforums.org/showthread.php?t=239560) 
:guitar:

---

### Post by danielbauwens on 2012-10-25
I don't judge people from how many beans they have, and what their rank is :)
I know that you know a lot, because I read stuff about you, and what other people say about you is also pretty impressive.

Daniel

---

### Post by newb85 on 2012-10-25
+1 to what danielbauwens has said about you NikTh!  You are one of the most helpful posters out there, when it comes to wireless-related issues.

@mr1holmes, are you certain the wireless isn't actually disabled?  It's common that LED indicators don't behave the same way in Ubuntu as they do in Windows.  So, at this point, you probably shouldn't use the LED as a conclusive assessment of the state of your Wifi.

---

### Post by mr1holmes on 2012-10-26
@danielbauwens- no such function keys works on my laptop
@newb85 - if the thing "wireless is disabled by hardware switch" means my wireless is turned off then i don't care about the LED, thank you.
@nikth
(1)
```

Network controller : Atheros Communications Inc. AR9485 Wireless Network Adapter(rev 01)
Subsystem: Foxconn International, Inc. Device
Kernel driver in use: ath9k
--
Ethernet controller : Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller(rev 07)
Subsystem: Sony Corporation Device
Kernel driver in use: r8169

```(2)
```

Module                  Size  Used by
pppoe                  17511  2 
pppox                  13158  1 pppoe
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
parport_pc             31968  0 
ppdev                  12817  0 
bnep                   17707  2 
rfcomm                 37276  0 
bluetooth             183228  10 bnep,rfcomm
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_realtek    63356  1 
joydev                 17161  0 
coretemp               13168  0 
kvm                   357806  0 
snd_hda_intel          32515  3 
microcode              18209  0 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25382  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
sony_laptop            44183  0 
mac_hid                13037  0 
uvcvideo               71277  0 
videobuf2_core         32070  1 uvcvideo
rts_pstor             346736  0 
videodev               95841  2 uvcvideo,videobuf2_core
snd_timer              24411  2 snd_pcm,snd_seq
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                84843  0 
serio_raw              13031  0 
arc4                   12473  2 
snd                    61991  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k                 116549  0 
i915                  457161  3 
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mac80211              461161  1 ath9k
ath9k_common           13783  1 ath9k
drm_kms_helper         45271  1 i915
ath9k_hw              376155  2 ath9k,ath9k_common
ath                    19187  3 ath9k,ath9k_common,ath9k_hw
drm                   230463  4 i915,drm_kms_helper
lpc_ich                16925  0 
mei                    35796  0 
cfg80211              175375  3 ath9k,mac80211,ath
i2c_algo_bit           13197  1 i915
video                  18847  1 i915
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
r8169                  55976  0 

```(3)

```

RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         connected       disabled        disabled   enabled         disabled

```

---

### Post by NikTh on 2012-10-26
Hi , 

look now what is the difference here. 

**IF you want** to completely power off your wireless network cuz you never used it (as you said in first post) then you can do it easily from your router. 
Either from router's configuration page or from a physical switch (usually routers have one). 

This way you will disable the wireless transmitter completely and wireless will be unavailable to everyone. 
If you want something like that and you want further help , let me know. 

**IF you want** to disable the wireless adapter in your PC only , then (in Ubuntu) you can blacklist the driver (module) that loads during boot and your wireless will be dead. 
Give this command 
```
echo 'blacklist ath9k' | sudo tee -a /etc/modprobe.d/blacklist.conf
``` reboot and no wireless from Ubuntu anymore. 

Thanks

---

### Post by mr1holmes on 2012-10-26
thanks for the help.

---

### Post by mr1holmes on 2012-11-11
is there a way to turn off the wireless LED ??

---

