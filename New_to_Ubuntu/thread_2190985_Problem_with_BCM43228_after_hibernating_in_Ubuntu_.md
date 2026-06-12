---
title: "Problem with BCM43228 after hibernating in Ubuntu 12.04 Precise"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by jason-cordero on 2013-11-30
I got suddenly a lot of problems after hibernating my pc with my  wireless. It is installed but it does not detect any connection. The  wired connection works however perfect. My OS is Ubuntu 12.04 and I have  a wireless with a bcm43228.

I have already tried everything from the forums where you have written,  and I still haven't found any solution, it does still not work...

Could you please help me?

Thousand thanks in advance.

PS.: with lspci -nn | grep 0280
I get this:
03:00.0 Network controller [0280]: Broadcom Corporation BCM43228 802.11a/b/g/n [14e4:4359]

and I already did this without problems (but it is still not working...):
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source

---

### Post by jason-cordero on 2013-11-30
With  *rfkill list all* I got:
0: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: acer-bluetooth: Bluetooth
        Soft blocked: yes
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

With *dmesg | grep* wl I got:
[   15.780767] wl: module license 'MIXED/Proprietary' taints kernel.
[   15.785254] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.785263] wl 0000:03:00.0: setting latency timer to 64
[   15.814582] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   23.688051] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   24.139568] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   44.116599] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[   74.092823] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  114.065170] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  164.021524] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  223.973623] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  283.926234] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  343.878675] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  403.830914] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  463.783595] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  523.736049] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  583.688208] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  643.640708] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  703.593278] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  763.545515] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  823.497923] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  883.450335] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[  943.402787] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1003.355202] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1063.307655] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1123.249606] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1183.171866] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1243.094166] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1303.016854] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1362.939376] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1422.861839] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1482.784283] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1542.706768] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1602.628567] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1662.551778] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1722.473990] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1782.396116] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1842.319053] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1902.242031] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 1962.163712] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2022.086288] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 2082.008759] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)

---

### Post by chili555 on 2013-11-30
> [ 15.814582] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[ 23.688051] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 24.139568] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)
[ 44.116599] ERROR @wl_cfg80211_scan : WLC_SCAN error (-22)You have a very unhappy driver there! Which version is it?```
sudo dpkg -s bcmwl-kernel-source | head -n10
```May I also see:```
lsmod
```

---

### Post by jason-cordero on 2013-11-30
I got:

```
Package: bcmwl-kernel-source
Status: install ok installed
Priority: optional
Section: admin
Installed-Size: 3582
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: bcmwl
Version: 6.20.155.1+bdcom-0ubuntu0.0.2
Replaces: bcmwl-modaliases
```

```
Module                  Size  Used by
binfmt_misc            17292  1 
btrfs                 638387  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
ufs                    78131  0 
qnx4                   13309  0 
hfsplus                83544  0 
hfs                    49479  0 
minix                  31453  0 
ntfs                  100206  0 
vfat                   17308  0 
msdos                  17132  0 
fat                    55605  2 vfat,msdos
jfs                   175085  0 
xfs                   747534  0 
reiserfs              230943  0 
ext2                   67987  0 
cfg80211              178877  0 
usblp                  17885  0 
usb_storage            39646  1 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158447  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_intel          32719  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
joydev                 17393  0 
snd_hwdep              13276  1 snd_hda_codec
i915                  428127  3 
nouveau               712674  0 
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ttm                    65344  1 nouveau
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
drm_kms_helper         45466  2 i915,nouveau
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67203  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
videodev               86588  1 uvcvideo
drm                   197641  6 i915,nouveau,ttm,drm_kms_helper
mac_hid                13077  0 
psmouse                86546  0 
i2c_algo_bit           13199  2 i915,nouveau
mxm_wmi                12893  1 nouveau
acer_wmi               23612  0 
serio_raw              13027  0 
mei                    36570  0 
sparse_keymap          13658  1 acer_wmi
lp                     17455  0 
snd_timer              28931  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17275  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19115  2 i915,nouveau
wmi                    18744  2 mxm_wmi,acer_wmi
snd                    62218  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2646632  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lib80211               14040  2 lib80211_crypt_tkip,wl
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci


```

---

### Post by chili555 on 2013-12-01
> Version: [COLOR="#FF0000"]6.20.155.1[/COLOR]+bdcom-0ubuntu0.0.2I suggest you try an earlier version as here:  [http://askubuntu.com/questions/359262/difficulties-with-bcm4313-driver-in-ubuntu-studio-13-04/359406#359406](http://askubuntu.com/questions/359262/difficulties-with-bcm4313-driver-in-ubuntu-studio-13-04/359406#359406)

Then reboot and give us your report.

---

