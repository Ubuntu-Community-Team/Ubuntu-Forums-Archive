---
title: "Wifi not working : Buntu 11.10, Lenovo Z560, Atheros 9285"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by dmantampfl on 2011-12-20
Hi all,
   I was installing Ubuntu 11.10 on my lenovo Z560. It has Atheros 9285 wifi. But I am not able to connect to wifi. The network drop-down says wifi is switched off using hardware switch. I can see that harware switch is on and in BIOS it is enabled. I see the wifi radio LED on. Later I used a USB wifi device. Still the same problem. I tried the following based on suggestions on the forums.
   
1. Blacklisting acer_wmi
  added 'blacklist acer_wmi' to blacklist.conf. lsmod now does not list this module.
  
2. When I run 'dmesg' command I see that the 'ath9k' is loaded properly without any error message.

3. I set the BIOS to defauls as someone suggested this option. Still no solution. Can anybudy help.

4. Tried pressiong 'Fn' combination to enable the wifi. Still same issue.

Wifi works fine on Windows 7.

Thanks in advance
DM

---

### Post by drpjkurian on 2011-12-20
Try this
[http://ubuntuforums.org/showthread.php?t=1484242](http://ubuntuforums.org/showthread.php?t=1484242)

---

### Post by wildmanne39 on 2011-12-20
Hi, you should be able to use the driver that comes with ubuntu for your card but let's run some commands and make sure.

Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
nm-tool
sudo iwlist scan

```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by dmantampfl on 2011-12-20
```

dmantampfl@xxxxx-laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux xxxxx-laptop 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
dmantampfl@xxxxx-laptop:~$
dmantampfl@xxxxx-laptop:~$ lspci -nnk | grep -iA2 net
05:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
        Subsystem: Lenovo Device [17aa:30a1]
        Kernel driver in use: ath9k
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
        Subsystem: Lenovo Device [17aa:392e]
        Kernel driver in use: r8169
dmantampfl@xxxxx-laptop:~$ 
dmantampfl@xxxxx-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
dmantampfl@xxxxx-laptop:~$ 
dmantampfl@xxxxx-laptop:~$ rfkill list all
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: yes
2: ideapad_wlan: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
3: ideapad_bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
dmantampfl@xxxxx-laptop:~$ lsmod
Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
bnep                   17923  2 
rfcomm                 38408  8 
joydev                 17393  0 
binfmt_misc            17292  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ideapad_laptop         13575  0 
sparse_keymap          13658  1 ideapad_laptop
arc4                   12473  2 
wmi                    18744  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  8 
uvcvideo               67271  0 
ath9k                 112711  0 
videodev               85626  1 uvcvideo
mac80211              272785  1 ath9k
btusb                  18160  2 
ath9k_common           13599  1 ath9k
ath9k_hw              293893  2 ath9k,ath9k_common
bluetooth             148839  23 bnep,rfcomm,btusb
drm_kms_helper         32889  1 i915
ath                    19387  2 ath9k,ath9k_hw
drm                   192226  4 i915,drm_kms_helper
psmouse                73673  0 
intel_ips              17753  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
cfg80211              172392  3 ath9k,mac80211,ath
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
mei                    36466  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 
dmantampfl@xxxxx-laptop:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        78:E4:00:FA:BF:ED

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        88:AE:1D:37:28:6E

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             xxx.xxx.xxx.xxx
    DNS:             xxx.xxx.xxx.xxx 


dmantampfl@xxxxx-laptop:~$ 
dmantampfl@xxxxx-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

dmantampfl@xxxxx-laptop:~$ 

```

---

### Post by dmantampfl on 2011-12-20
Hi drpjkurian,
   The commands didn't work. Wireless menu items are not missing.

Thanks
DM

---

### Post by wildmanne39 on 2011-12-20
Hi, your drivers are loaded but you have a hard block and a soft block please try this:
```
sudo rmmod -f wmi
```
and for the hard block try to turn it on with the switch or keys on the keyboard.
Thanks

---

### Post by dmantampfl on 2011-12-21
Hi wildmanne39,
  You solution worked. Now I added wmi to blacklist. Using Fn keys to unblock hard lock was not working in Ubuntu. So, I went to windows 7 and then switched of the hard lock. With these two my wifi is working. Rebooted twice to confirm. No issues.

Thank you very much for the solution.

Thanks
DM

---

### Post by wildmanne39 on 2011-12-21
Hi, your welcome! I am glad it worked.
Thanks

---

