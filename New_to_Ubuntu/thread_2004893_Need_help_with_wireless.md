---
title: "Need help with wireless"
date: 2012-06-16
forum: New to Ubuntu
---

### Post by tschwab5 on 2012-06-16
Making a long story short... These commands were typed in my terminal: 


sudo rmmod -f iwlwifi

gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf


Now I have absolutely zero wireless connection and am not seeing any wireless networks. I have an asus u52f and am running ubuntu 12.04 on it if that info helps.

---

### Post by conbot on 2012-06-16
What were you trying to do with your wifi? Can you pastebin the contents of the file you edited?

---

### Post by steeldriver on 2012-06-16
I think you just need to reload the module 

```
sudo modprobe iwlwifi
```I assume you just unloaded it to disabled the troublesome 802.11n capability?

---

### Post by tschwab5 on 2012-06-16
I was trying to make it go faster. For whatever reason when I'm connected to the wifi here it's extremely slow on my computer for no apparent reason, but not on my phone, others' computers, ipad, etc.

Not sure what you mean, but I figured what you're talking about and found the file and this is what's inside:

options iwlwifi 11n_disable=1

---

### Post by tschwab5 on 2012-06-16
> **steeldriver said:**
> I think you just need to reload the module 

```
sudo modprobe iwlwifi
```I assume you just unloaded it to disabled the troublesome 802.11n capability?

That command brought back this:

FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-24-generic/kernel/drivers/net/wereless/iwlwifi/iwlwifi.ko): Unkown symbol in module, or unknown parameter (see dmesg)

I have absolutely no idea what I'm doing here since the only coding I've ever done was a python class in college I got a D in... but I type dmesg in and a bunch of nonsense comes back, but the last line says:

iwlwifi: Unknown parameter 'lln_disable'

---

### Post by steeldriver on 2012-06-16
are you sure you typed it correctly in the /etc/modprobe.d/iwlwifi-disable11n.conf file? it should be **11n**_disable (number **eleven**) not **lln**_disable (you are trying to disable the 802.**11n** wireless extension)

go back and edit your file - or delete it if the new line is the only one - and then reload the module - you can try the disable 11n temporarily 

```
sudo modprobe iwlwifi 11n_disable=1
```if it works THEN make it permanent with the conf file - if it still won't load the module then 11n_disable=1 isn't the correct fix for you

---

### Post by tschwab5 on 2012-06-16
Oh darn, this is what I get for letting a friend mess with my stuff, haha. Lucky for me I'm a fast learner and I'm trying to work through this.

I'm not sure what's relevant and what's not so I'll list everything I can think of. There's two files from what he did I think are giving me the most problems: /etc/modprobe.d/iwlwifi-disable11n.conf and /etc/modprobe.d/iwlwifi-disablelln.conf 

Open them up and they both have just one line in them: options iwlwifi 11n_disable=1 and options iwlwifi lln_disable=l. I'm sure you can guess which goes with which one.

There's a third file which I'm not sure is relevant but I'll include it because it has some of the same letters. It is /etc/modprobe.d/iwl.conf and it has only one line: options iwlwifi bt_coex_active=0

I've tried both the rm and rm -rf commands to delete the first two and get the message cannot remove... Permission denied

---

### Post by steeldriver on 2012-06-16
you will need administrator (root) privileges to remove those files

```
sudo rm /etc/modprobe.d/iwlwifi-disablelln.conf 
```

you don't need 'rm -r' because it's just a file, not a directory that you're trying to delete recursively

---

### Post by tschwab5 on 2012-06-16
Awesome! Deleted both files and after a quick reboot my wireless now works again. steeldriver thank you so much for your patience and walking me through it. 

I do still have the problem of my internet connection being terribly slow for no apparent reason. Any tips on where to start with that?

---

### Post by steeldriver on 2012-06-16
Well it's still worth trying the 11n_disable=1 fix - now you've fixed the errors

I would try it WITHOUT the conf file first - this will only last until the next reboot but will tell you if the fix works:

```
sudo rmmod -f iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```**If** that works you can go ahead and create the conf file

```
gksu gedit /etc/modprobe.d/iwlwifi-disable11n.conf
```and add 

```
options iwlwifi 11n_disable=1
```

as you were trying to do before

---

### Post by wildmanne39 on 2012-06-16
Hi, I would also recommend to post the output from these commands so we can help you and you might avoid another breakage.

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
nm-tool
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by tschwab5 on 2012-07-09
I really apologize for the lateness of the reply, but my duties in the military have kept me away from my girlfriend's house for a while. I'm not sure what the issue is, but it only seems to come up when I'm connected to her wifi network. On her own laptop and my android tablet it loads webpages pretty much instantly. My laptop does fine on other wireless networks including my phone used as a hotspot and restaurant and hotel wifi networks. Here's the information asked for and hopefully someone can help me out with this.

cat /etc/lsb-release; uname -a```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux Schwab 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net```
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N + WiMAX 6250 [8086:0087] (rev 5f)
	Subsystem: Intel Corporation Centrino Advanced-N + WiMAX 6250 2x2 AGN [8086:1301]
	Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1820]
	Kernel driver in use: atl1c

```

nm-tool```
NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        20:CF:30:69:5D:5D

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Pfeifer Network] ---------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        00:23:15:50:8C:E4

  Capabilities:
    Speed:           81 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    AirStream7:      Infra, 74:44:01:8C:C8:99, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Jackson:         Infra, 00:1D:5A:CE:14:19, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WEP
    Joseph:          Infra, 18:F4:6A:76:0B:65, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WEP
    ekaragol:        Infra, 00:1C:DF:8B:E7:6C, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP
    *Pfeifer Network:Infra, 00:1B:11:5E:67:15, Freq 2452 MHz, Rate 54 Mb/s, Strength 52 WPA
    linksys:         Infra, 00:13:10:C9:AB:8A, Freq 2437 MHz, Rate 54 Mb/s, Strength 17

  IPv4 Settings:
    Address:         192.168.0.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        64:D4:DA:08:F6:F1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

iwconfig```
lo        no wireless extensions.

wmx0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Pfeifer Network"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:1B:11:5E:67:15   
          Bit Rate=81 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:9187  Invalid misc:649   Missed beacon:0

eth0      no wireless extensions.
```

rfkill list all```
0: i2400m-usb:1-1.1:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod```
Module                  Size  Used by
usbhid                 47199  0 
hid                    99559  1 usbhid
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
binfmt_misc            17540  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i2400m_usb             36569  0 
i2400m                107975  1 i2400m_usb
psmouse                87692  0 
serio_raw              13211  0 
wimax                  34762  1 i2400m
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
asus_laptop            24493  0 
sparse_keymap          13890  1 asus_laptop
input_polldev          13896  1 asus_laptop
iwlwifi               332672  0 
mac_hid                13253  0 
mac80211              506816  1 iwlwifi
i915                  468737  9 
soundcore              15091  1 snd
drm_kms_helper         46978  1 i915
drm                   242038  5 i915,drm_kms_helper
lp                     17799  0 
i2c_algo_bit           13423  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
intel_ips              18089  0 
cfg80211              205544  2 iwlwifi,mac80211
parport                46562  3 parport_pc,ppdev,lp
video                  19596  1 i915
atl1c                  41717  0 

```

---

### Post by wildmanne39 on 2012-07-10
Hi, did you remove this file?
```
options iwlwifi bt_coex_active=0
```
if not please do so.

Did you make this permanent?
```
options iwlwifi 11n_disable=1
```
if not I please do so but I recommend this name for the file:
```
gksu gedit /etc/modprobe.d/iwlwifi.conf
```

How far away is the computer from the wireless router is there a wall or door in between the router and the computer? because the signal is a little weak and the link quality is very bad.
Thanks

---

### Post by tschwab5 on 2012-07-10
> **wildmanne39 said:**
> Hi, did you remove this file?
```
options iwlwifi bt_coex_active=0
```
if not please do so.

Did you make this permanent?
```
options iwlwifi 11n_disable=1
```
if not I please do so but I recommend this name for the file:
```
gksu gedit /etc/modprobe.d/iwlwifi.conf
```

How far away is the computer from the wireless router is there a wall or door in between the router and the computer? because the signal is a little weak and the link quality is very bad.
Thanks

I did the ```
sudo modprobe iwlwifi 11n_disable=1
```, but it's not permanent yet.

I did remove ```
options iwlwifi bt_coex_active=0
```

These seemed to help a little bit, however compared to other devices on the same network my laptop is still noticeably slower.
The router is in the room next to this one and there is a wall between it, but if that was the issue I would assume that it would effect all devices and not just this one.

---

### Post by wildmanne39 on 2012-07-10
Hi, go ahead and make 
```
options iwlwifi 11n_disable=1
```
permanent then set your wireless settings in network manager to match the screenshots and reboot.
Thanks

---

### Post by tschwab5 on 2012-07-10
Holy crap that did the magic. Everything's just fine now! Any chance you could explain the why behind it? If not, it's cool because I understand it could be a lot of information. But thanks for your help!

---

### Post by wildmanne39 on 2012-07-10
Hi, glad to hear that it is working.

The google dns servers you set your dns server to is usually a lot faster then the one's our ip uses, and IPV6 still has issues so setting it to ignore usually speeds things up a lot then the command we had you make permanent to disable N speed because a lot of the linux drivers have trouble with N speed and unless you have a real fast connection it will not make any difference.
Enjoy

---

