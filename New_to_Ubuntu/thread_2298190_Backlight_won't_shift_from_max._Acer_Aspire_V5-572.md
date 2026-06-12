---
title: "Backlight won't shift from max. Acer Aspire V5-572G. 14.04.3 LTS"
date: 2015-10-09
forum: New to Ubuntu
---

### Post by Jon_Taylor on 2015-10-09
Hi, I'm new to ubuntu. I know there's a variety of threads about this, and I've tried some of the fixes, but I'm so clueless I'm not sure which commands are intended to be diagnostic an which are fixes so I'm a bit scared!

My backlight is stuck on max brightness. It used to work fine via the hotkeys. That's about the size of it. I also have problems with splash screen hang and HDMI connections not being detected which are covered in other threads. I found some diagnostic requests in another thread so here's the results of a variety of things:

I am using 14.04.3 LTS Xubuntu flavour

Kernel boot line is:
```
BOOT_IMAGE=/boot/vmlinuz-3.13.0-65-generic.efi.signed root=UUID=e213e2b4-03bd-4c40-9e53-7c1469a27514 ro recovery nomodeset

Video card info via lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Acer Incorporated [ALI] Device 0798
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)

...but there is also an NVIDIA Optimus 3D accelerator which I think can cause problems?
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev ff)

results of [COLOR=#000000][FONT=Ubuntu Mono]for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done[/FONT][/COLOR]
 /sys/class/backlight/*
cat: /sys/class/backlight/*/brightness: No such file or directory
cat: /sys/class/backlight/*/max_brightness: No such file or directory
cat: /sys/class/backlight/*/actual_brightness: No such file or directory

Loaded kernel modules:
Module                  Size  Used by
nfnetlink_queue        22408  0 
nfnetlink_log          17926  0 
nfnetlink              14606  2 nfnetlink_log,nfnetlink_queue
ctr                    13049  2 
ccm                    17773  2 
bbswitch               13943  0 
rfcomm                 69160  12 
bnep                   19624  2 
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
intel_rapl             18773  0 
arc4                   12608  2 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
coretemp               13435  0 
ath9k_hw              453856  2 ath9k_common,ath9k
acer_wmi               32522  0 
kvm_intel             143187  0 
sparse_keymap          13948  1 acer_wmi
kvm                   455843  1 kvm_intel
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
ath3k                  17414  0 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
mac80211              630728  1 ath9k
ghash_clmulni_intel    13216  0 
snd_hda_codec_hdmi     46368  1 
btusb                  32412  0 
snd_hda_codec_realtek    65812  1 
cfg80211              484040  3 ath,ath9k,mac80211
snd_hda_intel          56531  3 
snd_hda_codec         193017  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
i915                  788212  0 
aesni_intel            55624  4 
aes_x86_64             17131  1 aesni_intel
rtsx_pci_ms            18151  0 
snd_hwdep              13602  1 snd_hda_codec
lrw                    13286  1 aesni_intel
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
memstick               16966  1 rtsx_pci_ms
snd_seq_midi           13324  0 
drm_kms_helper         55071  1 i915
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
drm                   303102  2 i915,drm_kms_helper
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29482  2 snd_pcm,snd_seq
joydev                 17381  0 
serio_raw              13462  0 
snd                    69322  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
lpc_ich                21080  0 
i2c_algo_bit           13413  1 i915
video                  19476  2 i915,acer_wmi
soundcore              12680  1 snd
wmi                    19177  1 acer_wmi
mei_me                 18627  0 
shpchp                 37032  0 
mei                    82276  1 mei_me
mac_hid                13205  0 
rtsx_pci_sdmmc         23274  0 
psmouse               106692  0 
r8169                  71677  0 
ahci                   34091  3 
libahci                32716  1 ahci
mii                    13934  1 r8169
rtsx_pci               46245  2 rtsx_pci_ms,rtsx_pci_sdmmc
```

Pastebin /var/log/Xorg.0.log
[http://paste.ubuntu.com/12726400/](http://paste.ubuntu.com/12726400/)




One more thing I have tried installing xbacklight but the commands don't work because:
No outputs have backlight property

That last one sounds important...

Thanks in advance!

Jon

---

### Post by Joelb955 on 2015-10-09
I seem to be having the exact opposite problem. Mine is stuck on minimum.
Open the driver manager and see if there is a proprietary video driver available, E.G. from AMD. That seemed to fix my issue but created 10 more lol

---

