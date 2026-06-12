---
title: "Mac Wireless problem on Ubuntu 11.10"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by eggherd on 2011-12-09
I just downloaded Ubuntu last night and started fiddling around with it however right away I realized the wireless didn't work. With a wired connection I downloaded the updates and also a wireless driver that was recommended (Broadcom) I believe and restarted. Now, however Network Settings won't even bring up wireless options on the top bar.

Would really appreciate some help on this I've looked at some other threads and haven't managed to resolve my issue. 

Here are my specs:
chris@chris-iMac:~$ sudo dmidecode -s system-product-name
iMac4,1
chris@chris-iMac:~$ uname -a
Linux chris-iMac 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux
chris@chris-iMac:~$ lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
chris@chris-iMac:~$ sudo fdisk -1

---

### Post by josephmills on 2011-12-09
> **eggherd said:**
> I just downloaded Ubuntu last night and started fiddling around with it however right away I realized the wireless didn't work. With a wired connection I downloaded the updates and also a wireless driver that was recommended (Broadcom) I believe and restarted. Now, however Network Settings won't even bring up wireless options on the top bar.

Would really appreciate some help on this I've looked at some other threads and haven't managed to resolve my issue. 

Here are my specs:
chris@chris-iMac:~$ sudo dmidecode -s system-product-name
iMac4,1
chris@chris-iMac:~$ uname -a
Linux chris-iMac 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux
chris@chris-iMac:~$ lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01)
chris@chris-iMac:~$ sudo fdisk -1

Hello there and wecolme to the forum! 
you have the 03:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 01
which works great with the b43 drivers
Please take a moment to over look 
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
Hope this helps


**EDIT** could we also see a ```
lsmod 
```

---

### Post by eggherd on 2011-12-09
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
hfsplus                83507  1 
nls_utf8               12493  2 
udf                    83826  1 
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  1 
bnep                   17923  2 
rfcomm                 38408  8 
btusb                  18160  2 
bluetooth             148839  23 bnep,rfcomm,btusb
applesmc               18978  0 
input_polldev          13648  1 applesmc
isight_firmware        12586  0 
binfmt_misc            17292  1 
snd_hda_codec_idt      60049  1 
tpm_infineon           13200  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
apple_bl               13049  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wl                   2646601  0 
lib80211               14570  1 wl
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_apple              13166  0 
usbhid                 41905  0 
hid                    77367  2 hid_apple,usbhid
ses                    17217  0 
enclosure              14744  1 ses
usb_storage            44173  3 
uas                    17699  0 
radeon                925094  4 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  2 udf,firewire_core
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  6 radeon,ttm,drm_kms_helper
video                  18908  0 
i2c_algo_bit           13199  1 radeon
sky2                   49317  0

---

### Post by josephmills on 2011-12-09
wl 2646601 0 
lib80211 14570 1 wl   <--- not good 


open terminal and do a 
```
sudo rmmod wl && sudo modprobe b43 
```

then post 
```
dmesg | grep b43
```
thanks

---

### Post by eggherd on 2011-12-09
sudo rmmod wl && sudsudo rmmod wl && sudo modprobe
ERROR: Module wl does not exist in /proc/modules
[1]+  Exit 1                  sudo rmmod wl
chris@chris-iMac:~$ dmesg | grep b43
[22629.174714] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[22629.480766] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[22629.819455] Registered led device: b43-phy0::tx
[22629.819506] Registered led device: b43-phy0::rx
[22629.819562] Registered led device: b43-phy0::radio
[22630.358033] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[22630.358038] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[22630.358042] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

I'm on the website now, I just downloaded initially the driver the OS itself recommended.

Edit: Fixed it. Thanks for showing me where to look Joe! Turns out I just had to install it in the terminal. I have a lot to learn but it felt really cool doing it. Thanks again.

---

### Post by josephmills on 2011-12-09
> **eggherd said:**
> sudo rmmod wl && sudsudo rmmod wl && sudo modprobe
ERROR: Module wl does not exist in /proc/modules
[1]+  Exit 1                  sudo rmmod wl
chris@chris-iMac:~$ dmesg | grep b43
[22629.174714] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[22629.480766] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[22629.819455] Registered led device: b43-phy0::tx
[22629.819506] Registered led device: b43-phy0::rx
[22629.819562] Registered led device: b43-phy0::radio
[22630.358033] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[22630.358038] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[22630.358042] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

I'm on the website now, I just downloaded initially the driver the OS itself recommended.

Edit: Fixed it. Thanks for showing me where to look Joe! Turns out I just had to install it in the terminal. I have a lot to learn but it felt really cool doing it. Thanks again.

NP please take a moment to mark as solved so others might see down the road

---

### Post by eggherd on 2011-12-09
I went to bed last night and woke up this morning and it's the same problem as before. No wireless options appears. I tried re-installing but it says everything was up to date.

Looking through troubleshooting guides it says
 sudo lshw -c network

 *-network unclaimed

---

