---
title: "WiFi network don't show. Lenovo z560 with BCM4313"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by Reaz0n on 2012-01-11
Hi! I have Lenovo z560 end installed ubuntu 11.10

In ubuntu 10.10 wifi works perfect, but in ubuntu 11.x WiFi network don't show!
I put to blacklist.conf bcma/ssd/b43 - wifi does not work.
Install [Broadcom HYBRID DRIVER]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

### Post by westie457 on 2012-01-11
Welcome to the Forum

Could you open a terminal (Ctrl+Alt+T) please. Then type in ```
lspci -vnn

lsmod

rfkill list all
``` pressing Enter after each command.

Copy the entire out put and paste between [CODE] brackets by clicking on # at the top of the message pane.

Thank you

---

### Post by Reaz0n on 2012-01-11
Hi! I have Lenovo z560 end installed ubuntu 11.10

In ubuntu 10.10 wifi works perfect, but in ubuntu 11.x WiFi network don't show!
What I did to fix it:
I put to blacklist.conf bcma/ssd/b43 - wifi does not work.
Install [Broadcom HYBRID DRIVER]("http://www.broadcom.com/support/802.11/linux_sta.php") - nothing chenges.

```
reaz0n@reaz0n-Ideapad-Z560:~$ lspci | grep Network
06:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
reaz0n@reaz0n-Ideapad-Z560:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
reaz0n@reaz0n-Ideapad-Z560:~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

reaz0n@reaz0n-Ideapad-Z560:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
usb_storage            44173  1 
uas                    17699  0 
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  4 
snd_hda_codec_conexant    52418  1 
arc4                   12473  2 
snd_hda_intel          24262  3 
snd_seq_midi           13132  0 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_rawmidi            25241  1 snd_seq_midi
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               663211  3 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 nouveau
drm_kms_helper         32889  1 nouveau
brcmsmac              591864  0 
drm                   192194  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
mxm_wmi                12859  1 nouveau
brcmutil               16885  1 brcmsmac
btusb                  18160  2 
wmi                    18744  1 mxm_wmi
uvcvideo               67271  0 
bluetooth             148839  23 bnep,rfcomm,btusb
video                  18908  1 nouveau
psmouse                73673  0 
mac80211              393459  1 brcmsmac
videodev               85626  1 uvcvideo
serio_raw              12990  0 
cfg80211              172392  2 brcmsmac,mac80211
soundcore              12600  1 snd
crc_ccitt              12595  1 brcmsmac
mei                    36466  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  4 
libahci                25727  1 ahci
r8169                  43104  0 

reaz0n@reaz0n-Ideapad-Z560:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        00:26:82:B4:E2:75

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        88:AE:1D:39:80:9E

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

reaz0n@reaz0n-Ideapad-Z560:~$ sudo iwlist scan
[sudo] password for reaz0n: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results



```


P.S. Sorry for my english :)..

---

### Post by bkratz on 2012-01-11
You might also want to look at this thread

[http://ubuntuforums.org/showthread.php?t=1889170](http://ubuntuforums.org/showthread.php?t=1889170)

---

### Post by bkratz on 2012-01-11
Please see your duplicate thread

---

### Post by Double.J on 2012-01-11
Hi there!
Welcome to the forums!

Ubuntu does supply drivers for your card, but they aren't on the disks - don't ask - First things first connect the computer to the internet via a cable then follow the [help page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")


If it's all a bit too much it looks like you can just open up the software centre and search 'broadcom'

the 'bcmwl-kernel-source' package is the one you want - click install.

You'll probably have to restart

---

### Post by anewguy on 2012-01-11
Do not create duplicate posts - keep everything in the original post.

I will be sending a message to the maintainers so this thread can be closed and merged into your original thread.

---

### Post by TBABill on 2012-01-11
> **gnu/mirow said:**
> Ubuntu does supply drivers for your card, but they aren't on the disks - don't ask [help page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")the 'bcmwl-kernel-source' package is the one you want - click install.

You'll probably have to restartThis is untrue. The driver and firmware ARE on the disk. Follow the link you provided down to the STA driver no internet access portion. They're contained and you can get a complete connection without ever connecting via ethernet. Simply go to additional drivers, select the STA driver and when it says to restart, DO NOT restart. Just ```
sudo modprobe wl
```Then enjoy.

OP, did you install the STA driver via additional drivers or install bcmwl kernel source?

---

### Post by overdrank on 2012-01-11
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)

---

### Post by Reaz0n on 2012-01-12
> **TBABill said:**
> This is untrue. The driver and firmware ARE on the disk. Follow the link you provided down to the STA driver no internet access portion. They're contained and you can get a complete connection without ever connecting via ethernet. Simply go to additional drivers, select the STA driver and when it says to restart, DO NOT restart. Just ```
sudo modprobe wl
```Then enjoy.

OP, did you install the STA driver via additional drivers or install bcmwl kernel source?

Ohh.. Sorry for duplicate posts(wtf? maybe internet connection lags)

**TBABill**, My configuration don't need STA driver because Oneric kernel have [new open source brcm80211/brcmsmac driver]("http://askubuntu.com/a/67806")(new, awesome.. and don't want work for me:(), but I still installed bcmwl kernel source as you like and nothing happened.

In another forum I read about that bluetooth and WiFi are working on a single chip, and if in M$ Windows  enable bluetooth - wifi will work in Ubuntu. But nothing change for me.

**bkratz**, thanks, I try all methods from [this thread]("http://ubuntuforums.org/showthread.php?t=1889170") - nothing help.

I do not believe that Broadcom stronger than me:)!

---

### Post by TBABill on 2012-01-12
My apologies. What I meant was in response to the quote in my post that you can enable the device with the wl module directly from the CD in a live session. If you don't do that before installing, then you still have to connect via ethernet and either run the GUI to install the STA driver or do it manually via terminal. I always enable mine in the live session to see how it performs prior to installing so I end up with a working Broadcom connection after install.

---

