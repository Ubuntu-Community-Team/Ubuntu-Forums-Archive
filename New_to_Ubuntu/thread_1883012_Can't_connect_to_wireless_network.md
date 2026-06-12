---
title: "Can't connect to wireless network"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by divyansh.sachdeva on 2011-11-18
Hello people...

Recently I upgraded from Ubuntu 11.04 to 11.10 and since then I haven't been able to connect to wireless networks. Though I am able to see all the connections available, I can't connect to them. 

Stats: 

lspci -nnk | grep -iA2 net

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7175]
	Kernel driver in use: brcmsmac
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:fd50]
	Kernel driver in use: atl1
```

lsmod

```
Module                  Size  Used by
pppoe                  17513  2 
pppox                  13158  1 pppoe
bnep                   17923  2 
rfcomm                 38408  10 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
bcma                   19571  0 
arc4                   12473  2 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_codec_conexant    52418  1 
snd_hda_intel          28358  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
btusb                  18160  2 
snd_seq_midi_event     14475  1 snd_seq_midi
bluetooth             148839  23 bnep,rfcomm,btusb
brcmsmac              591864  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
brcmutil               16885  1 brcmsmac
mac80211              272785  1 brcmsmac
psmouse                63474  0 
sparse_keymap          13658  0 
serio_raw              12990  0 
radeon                961723  3 
wmi                    18744  0 
intel_ips              17753  0 
toshiba_bluetooth      12711  0 
cfg80211              172392  2 brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18908  0 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    36466  0 
drm                   196322  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  3 
libahci                25761  1 ahci
atl1c                  36638  0 
```

rfkill list

```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.

```

---

### Post by grahammechanical on 2011-11-18
What have you done to try to connect? What happens when you try to connect to your wireless network? What messages does Network Manager give you as the desktop loads?

This is what I think is strange about the printouts that you have given:

rfkill list gives your wireless adapter (lan) as phy0 but iwconfig says your wireless adapter is wlan0. Does this make any difference? I do not know. I do know this, that wlan0 is not connected to any wireless network and phy0 is not showing in iwconfig.

May I suggest that you edit the wireless connections and delete all of them. Then reboot and use the Network Manager icon to select your wireless network and attempt to make the connection. Your attempts to make a connection might be causing a conflict.

Regards.

---

### Post by divyansh.sachdeva on 2011-11-18
When I try to connect to the wireless network, ubuntu first tries to connect to the network and fails. The message that appears(in a balloon) is "Wireless Network: Disconnected".

I tried deleting and re-establishing the connection... Still no luck.

---

### Post by prookie on 2011-11-18
divyansh.sachdeva,

I'm new with Ubuntu, but anyway, upgrading your kernel might help.

I had problems with my Vodafone Mobile Connect modem (my modem was not recognized in Network Manager), and I solved it by upgrading to 3.1 kernel version.

Maybe this approach can help in your case. Feel free to ask me for support how I've done kernel upgrade.

pRookie

---

### Post by divyansh.sachdeva on 2011-11-18
Been there, done that! :(

---

### Post by prookie on 2011-11-18
The problems like this is something why I don't like system upgrades to versions which are not LTS (Long Term Support). Stability and reliability are for me above all.

---

### Post by divyansh.sachdeva on 2011-11-18
Thats so true. Messed up my perfectly fine system! aarrghhh!!!

---

