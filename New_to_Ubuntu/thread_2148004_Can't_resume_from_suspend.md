---
title: "Can't resume from suspend"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by 0N3 on 2013-05-23
Pretty much the title explains it. I have to hard reset my laptop everytime it suspends. Im using Ubuntu 13.04 64bit with AMD closed source drivers.

Below is a copy of my /var/log/pm-suspend.log

```
Initial commandline parameters: Tue May 21 20:23:39 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
binfmt_misc            17500  1 
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
rts5139               352481  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
arc4                   12615  2 
toshiba_bluetooth      12852  0 
snd_hda_codec_hdmi     36989  1 
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_hw              413680  2 ath9k_common,ath9k
snd_hda_codec_realtek    47037  1 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
snd_rawmidi            30180  1 snd_seq_midi
snd_hda_intel          43715  5 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mac_hid                13205  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
alx                    67960  0 
cfg80211              510937  3 ath,ath9k,mac80211
fglrx                5294837  156 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mdio                   13807  1 alx
lpc_ich                17061  0 
snd_timer              29425  2 snd_pcm,snd_seq
psmouse                95870  0 
serio_raw              13215  0 
mei                    41158  0 
amd_iommu_v2           19068  1 fglrx
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
microcode              22881  0 
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  3 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       6067804    1921848    4145956          0      78456     820612
-/+ buffers/cache:    1022780    5045024
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue May 21 20:23:40 IST 2013: performing suspend
Tue May 21 20:34:12 IST 2013: Awake.
Tue May 21 20:34:12 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sdb:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sda:
 setting standby to 36 (3 minutes)


/dev/sdb:
 setting standby to 36 (3 minutes)


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue May 21 20:34:12 IST 2013: Finished.
Initial commandline parameters: 
Wed May 22 00:16:53 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
rts5139               352481  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     36989  1 
snd_hda_codec_realtek    47037  1 
arc4                   12615  2 
toshiba_bluetooth      12852  0 
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
mac_hid                13205  0 
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
alx                    67960  0 
fglrx                5294837  196 
lpc_ich                17061  0 
cfg80211              510937  3 ath,ath9k,mac80211
mdio                   13807  1 alx
psmouse                95870  0 
serio_raw              13215  0 
soundcore              12680  1 snd
amd_iommu_v2           19068  1 fglrx
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
mei                    41158  0 
microcode              22881  0 
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  3 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       6067804    2210008    3857796          0      82944     678544
-/+ buffers/cache:    1448520    4619284
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed May 22 00:16:54 IST 2013: performing suspend
Wed May 22 01:03:32 IST 2013: Awake.
Wed May 22 01:03:32 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sdb:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sda:
 setting standby to 36 (3 minutes)


/dev/sdb:
 setting standby to 36 (3 minutes)


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Wed May 22 01:03:32 IST 2013: Finished.
Initial commandline parameters: 
Thu May 23 07:32:10 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  16 
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
rts5139               352481  0 
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     36989  1 
arc4                   12615  2 
snd_hda_codec_realtek    47037  1 
toshiba_bluetooth      12852  0 
ath9k                 149924  0 
snd_hda_intel          43715  5 
ath9k_common           14055  1 ath9k
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ath9k_hw              413680  2 ath9k_common,ath9k
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
mac80211              606457  1 ath9k
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
cfg80211              510937  3 ath,ath9k,mac80211
fglrx                5294837  273 
alx                    67960  0 
mdio                   13807  1 alx
mei                    41158  0 
lpc_ich                17061  0 
psmouse                95870  0 
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     17759  0 
amd_iommu_v2           19068  1 fglrx
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
serio_raw              13215  0 
microcode              22881  0 
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       6067804    5724012     343792          0    1524808    2357960
-/+ buffers/cache:    1841244    4226560
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu May 23 07:32:11 IST 2013: performing suspend
Thu May 23 10:16:22 IST 2013: Awake.
Thu May 23 10:16:22 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sdb:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sda:
 setting standby to 36 (3 minutes)


/dev/sdb:
 setting standby to 36 (3 minutes)


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu May 23 10:16:23 IST 2013: Finished.
Initial commandline parameters: 
Thu May 23 16:52:15 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
binfmt_misc            17500  1 
rts5139               352481  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
joydev                 17377  0 
snd_hda_codec_hdmi     36989  1 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
snd_hda_codec_realtek    47037  1 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
arc4                   12615  2 
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ath9k                 149924  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
toshiba_bluetooth      12852  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
fglrx                5294837  136 
snd_timer              29425  2 snd_pcm,snd_seq
psmouse                95870  0 
cfg80211              510937  3 ath,ath9k,mac80211
mac_hid                13205  0 
alx                    67960  0 
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mdio                   13807  1 alx
lpc_ich                17061  0 
microcode              22881  0 
mei                    41158  0 
serio_raw              13215  0 
amd_iommu_v2           19068  1 fglrx
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       6067804    2177120    3890684          0      95552    1046712
-/+ buffers/cache:    1034856    5032948
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu May 23 16:52:16 IST 2013: performing suspend
Thu May 23 18:02:33 IST 2013: Awake.
Thu May 23 18:02:33 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sdb:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sda:
 setting standby to 36 (3 minutes)


/dev/sdb:
 setting standby to 36 (3 minutes)


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu May 23 18:02:33 IST 2013: Finished.
Initial commandline parameters: 
Thu May 23 18:13:34 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ath3k                  12918  0 
btusb                  22474  0 
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
rts5139               352481  0 
videodev              129260  2 uvcvideo,videobuf2_core
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     36989  1 
arc4                   12615  2 
snd_hda_codec_realtek    47037  1 
ath9k                 149924  0 
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
mac80211              606457  1 ath9k
toshiba_bluetooth      12852  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
psmouse                95870  0 
snd_timer              29425  2 snd_pcm,snd_seq
cfg80211              510937  3 ath,ath9k,mac80211
serio_raw              13215  0 
fglrx                5294837  126 
mac_hid                13205  0 
mei                    41158  0 
alx                    67960  0 
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
amd_iommu_v2           19068  1 fglrx
mdio                   13807  1 alx
lp                     17759  0 
lpc_ich                17061  0 
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
soundcore              12680  1 snd
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       6067804    2029296    4038508          0      81960     894984
-/+ buffers/cache:    1052352    5015452
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu May 23 18:13:35 IST 2013: performing suspend
Thu May 23 18:13:49 IST 2013: Awake.
Thu May 23 18:13:49 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sdb:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sda:
 setting standby to 36 (3 minutes)


/dev/sdb:
 setting standby to 36 (3 minutes)


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu May 23 18:13:49 IST 2013: Finished.
Initial commandline parameters: 
Thu May 23 18:21:47 IST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000record-status hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ath3k                  12918  0 
btusb                  22474  0 
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
rts5139               352481  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
arc4                   12615  2 
snd_hda_codec_hdmi     36989  1 
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
ath9k_hw              413680  2 ath9k_common,ath9k
snd_hda_codec_realtek    47037  1 
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
snd_seq_midi           13324  0 
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13602  1 snd_hda_codec
toshiba_bluetooth      12852  0 
snd_rawmidi            30180  1 snd_seq_midi
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
cfg80211              510937  3 ath,ath9k,mac80211
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
psmouse                95870  0 
fglrx                5294837  119 
mac_hid                13205  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
alx                    67960  0 
lpc_ich                17061  0 
mdio                   13807  1 alx
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     17759  0 
mei                    41158  0 
amd_iommu_v2           19068  1 fglrx
microcode              22881  0 
parport                46345  3 lp,ppdev,parport_pc
serio_raw              13215  0 
soundcore              12680  1 snd
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       6067804    1836568    4231236          0      77432     877252
-/+ buffers/cache:     881884    5185920
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock hibernate hibernate:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay hibernate hibernate:


/usr/lib/pm-utils/sleep.d/49bay hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan hibernate hibernate:


/usr/lib/pm-utils/sleep.d/49wwan hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:


/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:


/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:


/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Thu May 23 18:21:48 IST 2013: performing hibernate
Thu May 23 18:23:00 IST 2013: Awake.
Thu May 23 18:23:00 IST 2013: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sdb:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sda:
 setting standby to 36 (3 minutes)


/dev/sdb:
 setting standby to 36 (3 minutes)


/usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:


/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:


/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:


/usr/lib/pm-utils/sleep.d/90clock thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan thaw hibernate:


/usr/lib/pm-utils/sleep.d/49wwan thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay thaw hibernate:


/usr/lib/pm-utils/sleep.d/49bay thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock thaw hibernate:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status thaw hibernate:


/usr/lib/pm-utils/sleep.d/000record-status thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Thu May 23 18:23:00 IST 2013: Finished.
Initial commandline parameters: 
Thu May 23 18:27:22 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
rts5139               352481  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
joydev                 17377  0 
snd_hda_codec_hdmi     36989  1 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_realtek    47037  1 
arc4                   12615  2 
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ath9k_hw              413680  2 ath9k_common,ath9k
snd_seq_midi           13324  0 
toshiba_bluetooth      12852  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_rawmidi            30180  1 snd_seq_midi
mac80211              606457  1 ath9k
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
fglrx                5294837  149 
cfg80211              510937  3 ath,ath9k,mac80211
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mei                    41158  0 
amd_iommu_v2           19068  1 fglrx
alx                    67960  0 
lpc_ich                17061  0 
psmouse                95870  0 
serio_raw              13215  0 
mdio                   13807  1 alx
lp                     17759  0 
soundcore              12680  1 snd
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       6067804    2471176    3596628          0      78984    1029124
-/+ buffers/cache:    1363068    4704736
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu May 23 18:27:23 IST 2013: performing suspend
Thu May 23 18:27:34 IST 2013: Awake.
Thu May 23 18:27:34 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sdb:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sda:
 setting standby to 36 (3 minutes)


/dev/sdb:
 setting standby to 36 (3 minutes)


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu May 23 18:27:35 IST 2013: Finished.
Initial commandline parameters: 
Thu May 23 18:30:09 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
rts5139               352481  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
joydev                 17377  0 
snd_hda_codec_hdmi     36989  1 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_realtek    47037  1 
arc4                   12615  2 
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ath9k_hw              413680  2 ath9k_common,ath9k
snd_seq_midi           13324  0 
toshiba_bluetooth      12852  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_rawmidi            30180  1 snd_seq_midi
mac80211              606457  1 ath9k
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac_hid                13205  0 
fglrx                5294837  189 
cfg80211              510937  3 ath,ath9k,mac80211
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mei                    41158  0 
amd_iommu_v2           19068  1 fglrx
alx                    67960  0 
lpc_ich                17061  0 
psmouse                95870  0 
serio_raw              13215  0 
mdio                   13807  1 alx
lp                     17759  0 
soundcore              12680  1 snd
parport                46345  3 lp,ppdev,parport_pc
microcode              22881  0 
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       6067804    2565996    3501808          0      79660    1080296
-/+ buffers/cache:    1406040    4661764
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu May 23 18:30:10 IST 2013: performing suspend
Thu May 23 18:30:14 IST 2013: Awake.
Thu May 23 18:30:14 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sdb:
 setting Advanced Power Management level to 0x80 (128)
 APM_level	= 128


/dev/sda:
 setting standby to 36 (3 minutes)


/dev/sdb:
 setting standby to 36 (3 minutes)


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu May 23 18:30:15 IST 2013: Finished.
Initial commandline parameters: 
Thu May 23 20:16:16 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
rts5139               352481  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
joydev                 17377  0 
snd_hda_codec_hdmi     36989  1 
arc4                   12615  2 
snd_hda_codec_realtek    47037  1 
coretemp               13355  0 
ath9k                 149924  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ghash_clmulni_intel    13259  0 
snd_hwdep              13602  1 snd_hda_codec
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
ath9k_common           14055  1 ath9k
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ath9k_hw              413680  2 ath9k_common,ath9k
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
toshiba_bluetooth      12852  0 
cfg80211              510937  3 ath,ath9k,mac80211
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
fglrx                5294837  1046 
mac_hid                13205  0 
amd_iommu_v2           19068  1 fglrx
alx                    67960  0 
lpc_ich                17061  0 
psmouse                95870  0 
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     17759  0 
mei                    41158  0 
microcode              22881  0 
parport                46345  3 lp,ppdev,parport_pc
mdio                   13807  1 alx
soundcore              12680  1 snd
serio_raw              13215  0 
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       8132180    3248696    4883484          0     114612    1613236
-/+ buffers/cache:    1520848    6611332
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu May 23 20:16:18 IST 2013: performing suspend
Thu May 23 20:16:29 IST 2013: Awake.
Thu May 23 20:16:29 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu May 23 20:16:29 IST 2013: Finished.
Initial commandline parameters: 
Thu May 23 20:20:34 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
rts5139               352481  0 
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
ath3k                  12918  0 
btusb                  22474  0 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
joydev                 17377  0 
arc4                   12615  2 
coretemp               13355  0 
kvm_intel             132891  0 
snd_hda_codec_hdmi     36989  1 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_realtek    47037  1 
ath9k                 149924  0 
ath9k_common           14055  1 ath9k
toshiba_bluetooth      12852  0 
ath9k_hw              413680  2 ath9k_common,ath9k
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_hwdep              13602  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
mac80211              606457  1 ath9k
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
alx                    67960  0 
mdio                   13807  1 alx
fglrx                5294837  126 
mei                    41158  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mac_hid                13205  0 
cfg80211              510937  3 ath,ath9k,mac80211
snd_timer              29425  2 snd_pcm,snd_seq
lpc_ich                17061  0 
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lp                     17759  0 
psmouse                95870  0 
amd_iommu_v2           19068  1 fglrx
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
microcode              22881  0 
serio_raw              13215  0 
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       8132180    1951868    6180312          0      83948     882732
-/+ buffers/cache:     985188    7146992
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu May 23 20:20:35 IST 2013: performing suspend
\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00\00Initial commandline parameters: 
Thu May 23 20:32:00 IST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Ubuntu-PC 3.8.0-21-generic #32-Ubuntu SMP Tue May 14 22:16:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
ath3k                  12918  0 
btusb                  22474  0 
nvram                  14362  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  16 
bnep                   18036  2 
bluetooth             228619  23 bnep,ath3k,btusb,rfcomm
binfmt_misc            17500  1 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
rts5139               352481  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
joydev                 17377  0 
coretemp               13355  0 
kvm_intel             132891  0 
kvm                   443165  1 kvm_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_hda_codec_hdmi     36989  1 
snd_hda_codec_realtek    47037  1 
snd_hda_intel          43715  5 
snd_hda_codec         188899  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
arc4                   12615  2 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ath9k                 149924  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_common           14055  1 ath9k
snd_rawmidi            30180  1 snd_seq_midi
ath9k_hw              413680  2 ath9k_common,ath9k
toshiba_bluetooth      12852  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mac80211              606457  1 ath9k
snd                    68876  20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac_hid                13205  0 
cfg80211              510937  3 ath,ath9k,mac80211
fglrx                5294837  143 
alx                    67960  0 
mdio                   13807  1 alx
mei                    41158  0 
amd_iommu_v2           19068  1 fglrx
lpc_ich                17061  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
psmouse                95870  0 
serio_raw              13215  0 
microcode              22881  0 
vesafb                 13828  1 
video                  19390  0 
ahci                   25731  6 
libahci                31364  1 ahci
             total       used       free     shared    buffers     cached
Mem:       8132180    2019752    6112428          0      85360     858016
-/+ buffers/cache:    1076376    7055804
Swap:      3998716          0    3998716


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay suspend suspend:


/usr/lib/pm-utils/sleep.d/49bay suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan suspend suspend:


/usr/lib/pm-utils/sleep.d/49wwan suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu May 23 20:32:01 IST 2013: performing suspend
Thu May 23 20:32:15 IST 2013: Awake.
Thu May 23 20:32:15 IST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sdb:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49wwan resume suspend:


/usr/lib/pm-utils/sleep.d/49wwan resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bay resume suspend:


/usr/lib/pm-utils/sleep.d/49bay resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend:


/usr/lib/pm-utils/sleep.d/48tlp-rdw-lock resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu May 23 20:32:15 IST 2013: Finished.
```

---

### Post by Toz on 2013-05-23
What is the make and model of the laptop? 

According to the log file, the suspend/resume cycle is completing successfully. Perhaps the screen brightness is just turned down. Can you try adjusting brightness to see if the image returns? You can also try Ctrl+Alt+F1 and then returning (Ctrl+Alt+F7) to see if that helps as well.

You also have a number of additional files in /usr/lib/pm-utils/sleep.d:
- 48tlp-rdw-lock
- 49bay
- 49wwan
I can't seem to find them in the regular ubuntu repositories. Do you know which packages you installed to get these files?

And finally, what is your kernel boot line:
```
cat /proc/cmdline
```

EDIT: The results of this command might help as well:
```
cat /var/log/syslog | grep PM:
```

---

### Post by 0N3 on 2013-05-23
cat /proc/cmdline```
BOOT_IMAGE=/boot/vmlinuz-3.8.0-21-generic root=UUID=855ace7b-2f23-4ed2-b340-60f76efcb914 ro quiet splash nomodeset vt.handoff=7


```

[COLOR=#000000]48tlp-rdw-lock[/COLOR]
[COLOR=#000000]- 49bay[/COLOR]
[COLOR=#000000]- 49wwan
[/COLOR]
The above packages are from tlp (power management program replacing jupiter if im correct) Basically my battery life has tripled since using it beating windows by over an hour fantastic software.

I saw everything was a success it does suspend and also the screen lights up but no login screen ive waited 15mins nothing happens. Ctrl Alt F1 brings me to console login and Ctrl Alt F7 brings me back to blank screen I did try this numerous times. I have tried editing boot parameters, uninstalled gnome power management swapped out and replaed my RAM nothing works. I have tried everything that has worked for other users just wont work for me. 

Laptp is a Toshiba Satelite:

Core i7 2.40Ghz
AMD HD 7670M 2GB DDR3
8GB RAM
Sata HDD 750GB
Sata HDD 320GB (swapped my CD/DVD burner for another HDD)

Think I have covered your Q's anything else you need?

Thank for quick reply!

---

### Post by newb85 on 2013-05-23
Did suspend work on your machine prior to the installation of TLP?

---

### Post by 0N3 on 2013-05-23
It did work prior to installing TLP and also afterwards. I think it is my graphics card. I found a script to fix the issue but it doesn't actually suspend the machine the screen turns off but the machine doesn't actually go into suspend hard drive is still making noise and the fan too minimal noise but there not suspended. I am going to try the open source driver see if it resolves the issue if not I will uninstall TLP and see if it changes anything.

---

### Post by 0N3 on 2013-05-23
Uninstalling the AMD closed source driver and using the open source driver solved the issue. My only problem is that the fan doesn't stop spinning and thus reduces my battery life by almost half using the closed source driver :( the fan also becomes a little uncomfortable to listen to when it is continually spinning around.

---

### Post by 0N3 on 2013-05-23
Sorry using the open source driver reduce my battery by half and makes the fan discomforting to listen to after 10 20 mins usage.

---

### Post by 0N3 on 2013-05-23
Solved it I did install the beta version of the AMD Driver so went back to the normal AMD closed source driver and the issue is resolved now :)

---

### Post by 0N3 on 2013-05-24
Take that back problem is happening again. It does suspend and wake up but my mouse locks up causing me to hard reset again. So no better off then I was before. I think it is time to admit defeat to Ubuntu and head back to a more reliable windows. 3 weeks fighting with Ubuntu to make a workable OS is a bit much. Since Unity things have seriously declined in Ubuntu and has become far too unstable with constant system errors. May wait till 13.10 to see if things improve but I have seriously little or no hope in Ubuntu. Thanks again for yere replies and help!

---

### Post by Toz on 2013-05-24
> **0N3 said:**
> Take that back problem is happening again. It does suspend and wake up but my mouse locks up causing me to hard reset again. 
Is it just the mouse that hangs, or the whole system? If its just the mouse, try unloading and reloading the psmouse module:
```
sudo modprobe -r psmouse
sudo modprobe psmouse
```
> 3 weeks fighting with Ubuntu to make a workable OS is a bit much. Since Unity things have seriously declined in Ubuntu and has become far too unstable with constant system errors.
As an FYI, there are alternatives to unity. Search for Xubuntu (Xfce), lubuntu (lxde) or kubuntu (kde). 
> So no better off then I was before. I think it is time to admit defeat to Ubuntu and head back to a more reliable windows.
> May wait till 13.10 to see if things improve but I have seriously little or no hope in Ubuntu. Thanks again for yere replies and help!
Life is too short to spend worrying about O/Ss. You should use what works best for you. Good luck.

---

### Post by 0N3 on 2013-05-24
Toz ](*,) it was killing me what the hell was causing it. You were bang on from the start TLP was the issue. I had to fight this to see what the problem was it was really bugging me. Without installing TLP I can't reproduce the problem. As soon as I install TLP BAM!!! it starts happening. The only problem is I don't know how to report the bug or is it specific for my hardware......
I did email the PPA owner as there was no option to report a bug on his page. I can live without the extra 2 hours battery life. Going to look into some other power management options.

---

### Post by Toz on 2013-05-24
Are you using the proprietary fglrx driver or the open source radeon one? The proprietary drivers often give better power management performance.

Also, what is the model number of your laptop? Is it one of those hybrid laptops that has both an intel and amd graphics card? This will help identify the video card(s):
```
sudo lspci- vnn | grep -A15 VGA
```

---

### Post by 0N3 on 2013-05-24
Open source I do get slightly longer with the fglrx driver. I have smoother experience with the open source driver. But my fan almost never stops spinning even if its idle for over an hour.... It does stop frequently using the fglrx driver thus giving me slightly better battery life. fglrx maybe 2hrs max open source 1hr 30 mins max and using the TLP I was getting 3 1/2 - 4 hours.

---

### Post by 0N3 on 2013-05-24
Sorry it isn't hybrid laptop either it has Radeon HD 7670M dedicated graphics.

---

### Post by Toz on 2013-05-24
What model number is the laptop?

---

### Post by 0N3 on 2013-05-24
```
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Thames XT [Radeon HD 7670M] [1002:6840] (prog-if 00 [VGA controller])	Subsystem: Toshiba America Info Systems Device [1179:fb22]
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c0000000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 3000 [size=256]
	Expansion ROM at c0040000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Capabilities: [150] Advanced Error Reporting
	Kernel driver in use: radeon


01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Turks/Whistler HDMI Audio [Radeon HD 6000 Series] [1002:aa90]
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]



```

Toshiba Satellite L855 - 149

---

### Post by Toz on 2013-05-24
Can you try some kernel boot parameters to see if you get better power performance? See the "Kernel Boot Parameters" link in my signature for more information on how. I would suggest trying, one at a time, the following:

acpi_osi=
```
GRUB_CMDLINE_LINUX="acpi_osi="
```
acpi_osi=Linux
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```
acpi_osi="!Windows 2012"
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

---

### Post by 0N3 on 2013-05-24
Can I add them like this:

```
[COLOR=#000000][FONT=Ubuntu Mono]GRUB_CMDLINE_LINUX="acpi_osi= [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Beta]quiet splash radeon.audio=1[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]"[/FONT][/COLOR]
```

I need the radeon.audio=1 for my HDMI sound to work with the radeon open source driver.

---

### Post by Toz on 2013-05-24
You could, but the general convention is to add new parameters to the GRUB_CMDLINE_LINUX line (leaving the originals on the GRUB_CMDLINE_LINUX_DEFAULT line) like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="radeon.audio=1 acpi_osi="
```

---

### Post by linrunner on 2013-05-25
Hi,

the official way to file a bug report against TLP is now mentioned in the [documentation]("http://linrunner.de/en/tlp/docs/tlp-linux-advanced-power-management.html#support"): [Issue Tracker]("https://github.com/linrunner/TLP/issues?state=open").

Anyway, i found your post here. Does the suspend problem occur on ac and battery power or only in one of the cases?

Please show the complete output of (on battery):
```
sudo tlp-stat
```

---

### Post by 0N3 on 2013-05-25
On battery power heres the output of:

```
sudo tlp stat
```

```
--- TLP 0.3.9 --------------------------------------------

+++ Configured Settings: /etc/default/tlp
TLP_ENABLE=1
DISK_IDLE_SECS_ON_AC=0
DISK_IDLE_SECS_ON_BAT=2
MAX_LOST_WORK_SECS_ON_AC=15
MAX_LOST_WORK_SECS_ON_BAT=60
SCHED_POWERSAVE_ON_AC=0
SCHED_POWERSAVE_ON_BAT=1
NMI_WATCHDOG=0
DISK_DEVICES="sda sdb"
DISK_APM_LEVEL_ON_AC="254 254"
DISK_APM_LEVEL_ON_BAT="128 128"
SATA_LINKPWR_ON_AC=max_performance
SATA_LINKPWR_ON_BAT=min_power
PCIE_ASPM_ON_AC=performance
PCIE_ASPM_ON_BAT=powersave
RADEON_POWER_PROFILE_ON_AC=high
RADEON_POWER_PROFILE_ON_BAT=low
WIFI_PWR_ON_AC=1
WIFI_PWR_ON_BAT=5
WOL_DISABLE=Y
SOUND_POWER_SAVE=1
SOUND_POWER_SAVE_CONTROLLER=Y
BAY_POWEROFF_ON_BAT=0
BAY_DEVICE="sr0"
RUNTIME_PM_ON_AC=on
RUNTIME_PM_ON_BAT=auto
RUNTIME_PM_ALL=0
USB_AUTOSUSPEND=1
RESTORE_DEVICE_STATE_ON_STARTUP=0


+++ System Info
System         = TOSHIBA PSKFWE-00K00REN SATELLITE L855
BIOS           = 6.60
Release        = Ubuntu 13.04
Kernel         = 3.8.0-22-generic x86_64
/proc/cmdline  = BOOT_IMAGE=/boot/vmlinuz-3.8.0-22-generic root=UUID=f299c4ae-e565-473c-8633-bb4faef42c39 ro radeon.audio=1 "acpi_osi=!Windows 2012" quiet splash vt.handoff=7


+++ System Status
TLP power save = enabled
power source   = battery


+++ Processor
CPU Model      = Intel(R) Core(TM) i7-3630QM CPU @ 2.40GHz


/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq  =  2401000 [kHz]
/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies = 2401000 2400000 2300000 2200000 2100000 2000000 1900000 1800000 1700000 1600000 1500000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu1/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq  =  2401000 [kHz]
/sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies = 2401000 2400000 2300000 2200000 2100000 2000000 1900000 1800000 1700000 1600000 1500000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu2/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu2/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_max_freq  =  2401000 [kHz]
/sys/devices/system/cpu/cpu2/cpufreq/scaling_available_frequencies = 2401000 2400000 2300000 2200000 2100000 2000000 1900000 1800000 1700000 1600000 1500000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu3/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu3/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_max_freq  =  2401000 [kHz]
/sys/devices/system/cpu/cpu3/cpufreq/scaling_available_frequencies = 2401000 2400000 2300000 2200000 2100000 2000000 1900000 1800000 1700000 1600000 1500000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu4/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu4/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu4/cpufreq/scaling_max_freq  =  2401000 [kHz]
/sys/devices/system/cpu/cpu4/cpufreq/scaling_available_frequencies = 2401000 2400000 2300000 2200000 2100000 2000000 1900000 1800000 1700000 1600000 1500000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu5/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu5/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu5/cpufreq/scaling_max_freq  =  2401000 [kHz]
/sys/devices/system/cpu/cpu5/cpufreq/scaling_available_frequencies = 2401000 2400000 2300000 2200000 2100000 2000000 1900000 1800000 1700000 1600000 1500000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu6/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu6/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu6/cpufreq/scaling_max_freq  =  2401000 [kHz]
/sys/devices/system/cpu/cpu6/cpufreq/scaling_available_frequencies = 2401000 2400000 2300000 2200000 2100000 2000000 1900000 1800000 1700000 1600000 1500000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpu7/cpufreq/scaling_governor  = ondemand
/sys/devices/system/cpu/cpu7/cpufreq/scaling_min_freq  =  1200000 [kHz]
/sys/devices/system/cpu/cpu7/cpufreq/scaling_max_freq  =  2401000 [kHz]
/sys/devices/system/cpu/cpu7/cpufreq/scaling_available_frequencies = 2401000 2400000 2300000 2200000 2100000 2000000 1900000 1800000 1700000 1600000 1500000 1400000 1300000 1200000 [kHz]


/sys/devices/system/cpu/cpufreq/boost                  = 1
/proc/sys/kernel/nmi_watchdog                          = 0


+++ Undervolting
PHC kernel not available.


+++ Temperatures
CPU temp               =    49 [°C]
Fan speed              = (not available)


+++ File System
/proc/sys/vm/laptop_mode               =     2
/proc/sys/vm/dirty_writeback_centisecs =  6000
/proc/sys/vm/dirty_expire_centisecs    =  6000
/proc/sys/vm/dirty_ratio               =    60
/proc/sys/vm/dirty_background_ratio    =    40
/proc/sys/fs/xfs/age_buffer_centisecs  = (not available)
/proc/sys/fs/xfs/xfssyncd_centisecs    = (not available)
/proc/sys/fs/xfs/xfsbufd_centisecs     = (not available)


+++ Storage Devices
/dev/sda:
          Model     = Hitachi HTS547575A9E384                 
          Firmware  = JE4OA60B
          APM Level = 128
          Status    = active/idle
          scheduler = deadline


        SMART info:
            4 Start_Stop_Count          =      690 
            5 Reallocated_Sector_Ct     =        0 
            9 Power_On_Hours            =      524 [h]
          193 Load_Cycle_Count          =     6823 
          194 Temperature_Celsius       =       32 (Min/Max 12/48)  [°C]


/dev/sdb:
          Model     = Hitachi HTS545032B9A300                 
          Firmware  = PB3OC60N
          APM Level = 128
          Status    = active/idle
          scheduler = deadline


        SMART info:
            4 Start_Stop_Count          =     2498 
            5 Reallocated_Sector_Ct     =        0 
            9 Power_On_Hours            =     4432 [h]
          193 Load_Cycle_Count          =    23010 
          194 Temperature_Celsius       =       26 (Min/Max 5/50)  [°C]




+++ SATA Aggressive Link Power Management
/sys/class/scsi_host/host0/link_power_management_policy  = min_power
/sys/class/scsi_host/host1/link_power_management_policy  = min_power
/sys/class/scsi_host/host2/link_power_management_policy  = min_power
/sys/class/scsi_host/host3/link_power_management_policy  = min_power
/sys/class/scsi_host/host4/link_power_management_policy  = min_power
/sys/class/scsi_host/host5/link_power_management_policy  = min_power


+++ PCIe Active State Power Management
/sys/module/pcie_aspm/parameters/policy = default (using bios preferences)


+++ Wireless
bluetooth = on
wifi      = on
wwan      = none (no device)


wlan0(ath9k): power management = on


+++ Audio
/sys/module/snd_hda_intel/parameters/power_save            = 1
/sys/module/snd_hda_intel/parameters/power_save_controller = Y


+++ Battery Status
/sys/class/power_supply/BAT0/manufacturer                   = (not available)
/sys/class/power_supply/BAT0/model_name                     = PA5024U-1BRS
/sys/class/power_supply/BAT0/cycle_count                    = (not supported)
/sys/class/power_supply/BAT0/energy_full_design             =  47520 [mWh]
/sys/class/power_supply/BAT0/energy_full                    =  42800 [mWh]
/sys/class/power_supply/BAT0/energy_now                     =  32529 [mWh]
/sys/class/power_supply/BAT0/power_now                      =  15735 [mW]
/sys/class/power_supply/BAT0/status                         = Discharging


+++ Runtime Power Management
/sys/bus/pci/devices/0000:00:00.0/power/control = auto (0x060000 Host bridge)
/sys/bus/pci/devices/0000:00:01.0/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:14.0/power/control = on   (0x0c0330 USB controller)
/sys/bus/pci/devices/0000:00:16.0/power/control = on   (0x078000 Communication controller)
/sys/bus/pci/devices/0000:00:1a.0/power/control = on   (0x0c0320 USB controller)
/sys/bus/pci/devices/0000:00:1b.0/power/control = auto (0x040300 Audio device)
/sys/bus/pci/devices/0000:00:1c.0/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:1c.1/power/control = on   (0x060400 PCI bridge)
/sys/bus/pci/devices/0000:00:1d.0/power/control = on   (0x0c0320 USB controller)
/sys/bus/pci/devices/0000:00:1f.0/power/control = on   (0x060100 ISA bridge)
/sys/bus/pci/devices/0000:00:1f.2/power/control = on   (0x010601 SATA controller)
/sys/bus/pci/devices/0000:00:1f.3/power/control = on   (0x0c0500 SMBus)
/sys/bus/pci/devices/0000:01:00.0/power/control = on   (0x030000 VGA compatible controller)
/sys/bus/pci/devices/0000:01:00.1/power/control = auto (0x040300 Audio device)
/sys/bus/pci/devices/0000:07:00.0/power/control = auto (0x020000 Ethernet controller)
/sys/bus/pci/devices/0000:08:00.0/power/control = auto (0x028000 Network controller)


+++ USB
tlp usb autosuspend = enabled
tlp usb blacklist   = (not configured)


Bus 001 Device 002 ID 8087:0024 control = auto, autosuspend_delay_ms =  2000 -- Intel Corp. Integrated Rate Matching Hub (hub)
Bus 002 Device 002 ID 8087:0024 control = auto, autosuspend_delay_ms =  2000 -- Intel Corp. Integrated Rate Matching Hub (hub)
Bus 001 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 002 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 003 Device 001 ID 1d6b:0002 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 2.0 root hub (hub)
Bus 004 Device 001 ID 1d6b:0003 control = auto, autosuspend_delay_ms =  2000 -- Linux Foundation 3.0 root hub (hub)
Bus 001 Device 003 ID 0bda:0129 control = auto, autosuspend_delay_ms =  2000 -- Realtek Semiconductor Corp.  (rts5139)
Bus 001 Device 007 ID 0930:0219 control = auto, autosuspend_delay_ms =  2000 -- Toshiba Corp.  (btusb)
Bus 001 Device 004 ID 10f1:1a43 control = auto, autosuspend_delay_ms =  2000 -- Importek  (uvcvideo)
```

I can't seem to reproduce the problem at all now it's frustrating but fingers crossed it doesn't happen again.

Sorry if I went about the wrong procedure reporting the issue and a big thank you to all for your time and effort :)

---

### Post by linrunner on 2013-05-25
No need to say "sorry" :D. 

Suspend/resume problems are notoriously hard to isolate and fix. Because of the black screen upon resume i guess fglrx is the main suspect here. The tlp-stat output doesn't show anything exceptional.

I wish you good luck.

ps. do you have the latest BIOS version installed?

---

### Post by 0N3 on 2013-05-26
Yeah updated the bios 3-4 weeks ago I will go check the toshiba website to be double sure

---

