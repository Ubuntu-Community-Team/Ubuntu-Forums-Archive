---
title: "Won't suspend"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by Arendyl on 2012-06-18
Hi, my computer is having issues when I try to put it to sleep (suspend). When I close my laptop (in power settings, i have ti set to suspend) or hit the suspend but in the menu bar, the computer screen goes black (but still backlit) and it continues to run (also, the wifi indicator shows that wifi is turn off). Nothing I can do will return the computer to normal either, and I have to forcibly shut it down with the power switch. I have just recently installed 12.04, and I have Myunity and compiz config installed, and transmission is usually running (i made sure the "dont hibernate button" on transmission is off), and I have an external harddrive attach usually. Any suggestions are greatly appreciated.

---

### Post by Arendyl on 2012-06-20
Do bumps work on this site?

---

### Post by Toz on 2012-06-20
Can you provide some more information?

1. The make/model of your computer.
2. Does it work if you suspend manually? Open a terminal window and type in the following command to attempt a manual suspend:
```
sudo pm-suspend
```
3. Post back the contents of **/var/log/pm-suspend.log**
4. Also post back the results of this command (also run in a terminal window) to see what kernel parameters you are using:
```
cat /proc/cmdline
```

---

### Post by flanker12 on 2012-06-20
Recently found my laptop screen went black (suspended) when the lid was closed and would not return when the lid was opened. I found that going to System settings/brightness and lock, then turn off the lock solved the problem.

---

### Post by Arendyl on 2012-06-22
> **Toz said:**
> Can you provide some more information?

1. The make/model of your computer.
2. Does it work if you suspend manually? Open a terminal window and type in the following command to attempt a manual suspend:
```
sudo pm-suspend
```
3. Post back the contents of **/var/log/pm-suspend.log**
4. Also post back the results of this command (also run in a terminal window) to see what kernel parameters you are using:
```
cat /proc/cmdline
```

1.  HP mini, in use for two years.

2.  Sleep works when I don't have my external drive attached, and doesn't when it is.



3.  Initial commandline parameters: ```

Thu Jun 14 09:04:52 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
uvcvideo               67203  0 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
videodev               86588  1 uvcvideo
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                72919  0 
uas                    17828  0 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17275  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
wl                   2646601  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
i915                  414663  3 
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
soundcore              14635  1 snd
drm                   197692  4 i915,drm_kms_helper
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  2 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     995492      19628          0      55864     550744
-/+ buffers/cache:     388884     626236
Swap:      1037308       1776    1035532

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 09:04:58 EDT 2012: performing suspend
Thu Jun 14 09:06:11 EDT 2012: Awake.
Thu Jun 14 09:06:11 EDT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jun 14 09:06:16 EDT 2012: Finished.
Initial commandline parameters: 
Thu Jun 14 09:13:32 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
uvcvideo               67203  0 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
videodev               86588  1 uvcvideo
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                72919  0 
uas                    17828  0 
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17275  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
wl                   2646601  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
i915                  414663  3 
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
soundcore              14635  1 snd
drm                   197692  4 i915,drm_kms_helper
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     997716      17404          0     160536     477120
-/+ buffers/cache:     360060     655060
Swap:      1037308      19268    1018040

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 09:13:36 EDT 2012: performing suspend
Initial commandline parameters: 
Thu Jun 14 09:33:41 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  414663  3 
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  0 
rfcomm                 38139  0 
hp_wmi                 13652  0 
i2c_algo_bit           13199  1 i915
ppdev                  12849  0 
uvcvideo               67203  0 
soundcore              14635  1 snd
usbhid                 41906  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
psmouse                72919  0 
videodev               86588  1 uvcvideo
serio_raw              13027  0 
hid                    77367  1 usbhid
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
wmi                    18744  1 hp_wmi
lp                     17455  0 
mac_hid                13077  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
video                  19068  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
usb_storage            39646  3 ums_realtek
uas                    17828  0 
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     999500      15620          0     204300     374108
-/+ buffers/cache:     421092     594028
Swap:      1037308      54752     982556

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 09:33:48 EDT 2012: performing suspend
Initial commandline parameters: 
Thu Jun 14 13:15:27 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17275  0 
i915                  414663  3 
wl                   2646601  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
parport_pc             32114  0 
uvcvideo               67203  0 
i2c_algo_bit           13199  1 i915
bnep                   17830  2 
soundcore              14635  1 snd
ppdev                  12849  0 
ums_realtek            17920  0 
hp_wmi                 13652  0 
usbhid                 41906  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
psmouse                72919  0 
videodev               86588  1 uvcvideo
uas                    17828  0 
serio_raw              13027  0 
hid                    77367  1 usbhid
wmi                    18744  1 hp_wmi
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
lib80211               14040  2 lib80211_crypt_tkip,wl
lp                     17455  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
video                  19068  1 i915
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     944968      70152          0     200224     386804
-/+ buffers/cache:     357940     657180
Swap:      1037308      37140    1000168

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 13:15:33 EDT 2012: performing suspend
Initial commandline parameters: 
Thu Jun 14 19:24:00 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17275  0 
joydev                 17393  0 
wl                   2646601  0 
uvcvideo               67203  0 
bnep                   17830  2 
parport_pc             32114  0 
usbhid                 41906  0 
ums_realtek            17920  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
videodev               86588  1 uvcvideo
uas                    17828  0 
psmouse                72919  0 
serio_raw              13027  0 
hid                    77367  1 usbhid
lib80211               14040  2 lib80211_crypt_tkip,wl
rfcomm                 38139  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
wmi                    18744  1 hp_wmi
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
i915                  414663  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     888572     126548          0     328752     188120
-/+ buffers/cache:     371700     643420
Swap:      1037308     375208     662100

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Thu Jun 14 19:24:04 EDT 2012: performing suspend
Initial commandline parameters: 
Fri Jun 15 22:00:27 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17275  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414663  3 
wl                   2646601  0 
ums_realtek            17920  0 
parport_pc             32114  0 
bnep                   17830  2 
drm_kms_helper         45466  1 i915
uvcvideo               67203  0 
hp_wmi                 13652  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
videodev               86588  1 uvcvideo
psmouse                72919  0 
serio_raw              13027  0 
uas                    17828  0 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  1 hp_wmi
lib80211               14040  2 lib80211_crypt_tkip,wl
drm                   197692  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     969808      45312          0     148432     552256
-/+ buffers/cache:     269120     746000
Swap:      1037308       1984    1035324

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jun 15 22:00:30 EDT 2012: performing suspend
Initial commandline parameters: 
Sat Jun 16 10:06:01 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
i915                  414663  3 
snd_hda_intel          32765  3 
drm_kms_helper         45466  1 i915
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17275  0 
drm                   197692  4 i915,drm_kms_helper
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
parport_pc             32114  0 
uvcvideo               67203  0 
bnep                   17830  2 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
hp_wmi                 13652  0 
soundcore              14635  1 snd
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
psmouse                72919  0 
videodev               86588  1 uvcvideo
serio_raw              13027  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
lp                     17455  0 
i2c_algo_bit           13199  1 i915
wmi                    18744  1 hp_wmi
video                  19068  1 i915
mac_hid                13077  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
usb_storage            39646  3 ums_realtek
uas                    17828  0 
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     971124      43996          0      25728     307220
-/+ buffers/cache:     638176     376944
Swap:      1037308      50696     986612

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Jun 16 10:06:03 EDT 2012: performing suspend
Initial commandline parameters: 
Sun Jun 17 11:24:14 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17393  0 
uvcvideo               67203  0 
bnep                   17830  2 
parport_pc             32114  0 
hp_wmi                 13652  0 
ums_realtek            17920  0 
sparse_keymap          13658  1 hp_wmi
uas                    17828  0 
videodev               86588  1 uvcvideo
psmouse                72919  0 
serio_raw              13027  0 
lib80211_crypt_tkip    17275  0 
wmi                    18744  1 hp_wmi
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
wl                   2646601  0 
ppdev                  12849  0 
i915                  414663  3 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
usbhid                 41906  0 
i2c_algo_bit           13199  1 i915
hid                    77367  1 usbhid
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     929524      85596          0      34132     519404
-/+ buffers/cache:     375988     639132
Swap:      1037308          0    1037308

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Jun 17 11:24:16 EDT 2012: performing suspend
Initial commandline parameters: 
Mon Jun 18 18:24:57 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
i915                  414663  3 
drm_kms_helper         45466  1 i915
ums_realtek            17920  0 
bnep                   17830  2 
uvcvideo               67203  0 
parport_pc             32114  0 
usbhid                 41906  0 
videodev               86588  1 uvcvideo
uas                    17828  0 
psmouse                72919  0 
hid                    77367  1 usbhid
serio_raw              13027  0 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
wmi                    18744  1 hp_wmi
lib80211               14040  2 lib80211_crypt_tkip,wl
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     897924     117196          0      77792     494168
-/+ buffers/cache:     325964     689156
Swap:      1037308      27900    1009408

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Mon Jun 18 18:25:00 EDT 2012: performing suspend
Initial commandline parameters: 
Tue Jun 19 09:47:31 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414663  3 
bnep                   17830  2 
soundcore              14635  1 snd
drm_kms_helper         45466  1 i915
parport_pc             32114  0 
usbhid                 41906  0 
hp_wmi                 13652  0 
ums_realtek            17920  0 
uvcvideo               67203  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
videodev               86588  1 uvcvideo
psmouse                72919  0 
serio_raw              13027  0 
uas                    17828  0 
hid                    77367  1 usbhid
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
wmi                    18744  1 hp_wmi
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
drm                   197692  4 i915,drm_kms_helper
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  2 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     801664     213456          0      20100     358240
-/+ buffers/cache:     423324     591796
Swap:      1037308     122448     914860

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jun 19 09:47:34 EDT 2012: performing suspend
Tue Jun 19 10:26:51 EDT 2012: Awake.
Tue Jun 19 10:26:51 EDT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Jun 19 10:26:53 EDT 2012: Finished.
Initial commandline parameters: 
Tue Jun 19 10:27:55 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  414663  3 
bnep                   17830  2 
soundcore              14635  1 snd
drm_kms_helper         45466  1 i915
parport_pc             32114  0 
usbhid                 41906  0 
hp_wmi                 13652  0 
ums_realtek            17920  0 
uvcvideo               67203  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
videodev               86588  1 uvcvideo
psmouse                72919  0 
serio_raw              13027  0 
uas                    17828  0 
hid                    77367  1 usbhid
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
ppdev                  12849  0 
wmi                    18744  1 hp_wmi
lib80211               14040  2 lib80211_crypt_tkip,wl
mac_hid                13077  0 
drm                   197692  4 i915,drm_kms_helper
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     836908     178212          0      23432     374984
-/+ buffers/cache:     438492     576628
Swap:      1037308     115024     922284

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jun 19 10:27:57 EDT 2012: performing suspend
Initial commandline parameters: 
Tue Jun 19 12:38:03 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211_crypt_tkip    17275  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wl                   2646601  0 
i915                  414663  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17393  0 
usbhid                 41906  0 
rfcomm                 38139  0 
drm_kms_helper         45466  1 i915
uvcvideo               67203  0 
parport_pc             32114  0 
hp_wmi                 13652  0 
soundcore              14635  1 snd
ums_realtek            17920  0 
sparse_keymap          13658  1 hp_wmi
videodev               86588  1 uvcvideo
uas                    17828  0 
psmouse                72919  0 
serio_raw              13027  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
hid                    77367  1 usbhid
drm                   197692  4 i915,drm_kms_helper
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     695548     319572          0      34768     416808
-/+ buffers/cache:     243972     771148
Swap:      1037308          0    1037308

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jun 19 12:38:05 EDT 2012: performing suspend
Initial commandline parameters: 
Tue Jun 19 13:24:56 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211_crypt_tkip    17275  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
i915                  414663  3 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
joydev                 17393  0 
rfcomm                 38139  0 
soundcore              14635  1 snd
parport_pc             32114  0 
usbhid                 41906  0 
uvcvideo               67203  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
videodev               86588  1 uvcvideo
psmouse                72919  0 
serio_raw              13027  0 
hid                    77367  1 usbhid
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
wmi                    18744  1 hp_wmi
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ums_realtek            17920  0 
uas                    17828  0 
usb_storage            39646  2 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     916752      98368          0      38012     533716
-/+ buffers/cache:     345024     670096
Swap:      1037308          0    1037308

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jun 19 13:24:59 EDT 2012: performing suspend
Tue Jun 19 13:27:47 EDT 2012: Awake.
Tue Jun 19 13:27:47 EDT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Jun 19 13:27:49 EDT 2012: Finished.
Initial commandline parameters: 
Tue Jun 19 16:50:03 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                72919  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414663  3 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lib80211               14040  2 lib80211_crypt_tkip,wl
i2c_algo_bit           13199  1 i915
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
wmi                    18744  1 hp_wmi
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
uas                    17828  0 
usb_storage            39646  2 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     948680      66440          0      43636     505116
-/+ buffers/cache:     399928     615192
Swap:      1037308        600    1036708

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jun 19 16:50:06 EDT 2012: performing suspend
Tue Jun 19 16:50:52 EDT 2012: Awake.
Tue Jun 19 16:50:52 EDT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Tue Jun 19 16:50:54 EDT 2012: Finished.
Initial commandline parameters: 
Tue Jun 19 16:59:07 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                72919  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414663  3 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lib80211               14040  2 lib80211_crypt_tkip,wl
i2c_algo_bit           13199  1 i915
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
wmi                    18744  1 hp_wmi
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
uas                    17828  0 
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     999604      15516          0     152468     425612
-/+ buffers/cache:     421524     593596
Swap:      1037308       3092    1034216

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Jun 19 16:59:10 EDT 2012: performing suspend
Initial commandline parameters: 
Wed Jun 20 22:22:16 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
lib80211_crypt_tkip    17275  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wl                   2646601  0 
i915                  414663  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 17393  0 
bnep                   17830  2 
parport_pc             32114  0 
uvcvideo               67203  0 
ums_realtek            17920  0 
usbhid                 41906  0 
soundcore              14635  1 snd
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
videodev               86588  1 uvcvideo
psmouse                72919  0 
serio_raw              13027  0 
hid                    77367  1 usbhid
uas                    17828  0 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
wmi                    18744  1 hp_wmi
lib80211               14040  2 lib80211_crypt_tkip,wl
ppdev                  12849  0 
mac_hid                13077  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  3 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     975348      39772          0     122520     318492
-/+ buffers/cache:     534336     480784
Swap:      1037308     335160     702148

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'eth2'
OK

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Wed Jun 20 22:22:22 EDT 2012: performing suspend
Initial commandline parameters: 
Fri Jun 22 11:00:01 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55605  1 vfat
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  414663  3 
usbhid                 41906  0 
bnep                   17830  2 
parport_pc             32114  0 
hp_wmi                 13652  0 
ums_realtek            17920  0 
uvcvideo               67203  0 
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
psmouse                72919  0 
serio_raw              13027  0 
videodev               86588  1 uvcvideo
uas                    17828  0 
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
rfcomm                 38139  0 
wmi                    18744  1 hp_wmi
bluetooth             158438  10 bnep,rfcomm
mac_hid                13077  0 
ppdev                  12849  0 
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 i915
hid                    77367  1 usbhid
drm                   197692  4 i915,drm_kms_helper
lib80211               14040  2 lib80211_crypt_tkip,wl
soundcore              14635  1 snd
i2c_algo_bit           13199  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            39646  2 ums_realtek
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     798916     216204          0      16536     335328
-/+ buffers/cache:     447052     568068
Swap:      1037308      11060    1026248

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'eth1'
OK

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jun 22 11:00:03 EDT 2012: performing suspend
Initial commandline parameters: 
Fri Jun 22 11:21:27 EDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Arlithen 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
Module                  Size  Used by
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
lib80211_crypt_tkip    17275  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  414663  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  0 
uvcvideo               67203  0 
bnep                   17830  2 
ppdev                  12849  0 
soundcore              14635  1 snd
hp_wmi                 13652  0 
i2c_algo_bit           13199  1 i915
joydev                 17393  0 
sparse_keymap          13658  1 hp_wmi
videodev               86588  1 uvcvideo
psmouse                72919  0 
serio_raw              13027  0 
rfcomm                 38139  0 
wmi                    18744  1 hp_wmi
bluetooth             158438  10 bnep,rfcomm
lp                     17455  0 
mac_hid                13077  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lib80211               14040  2 lib80211_crypt_tkip,wl
video                  19068  1 i915
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
usb_storage            39646  0 
uas                    17828  0 
atl1c                  36718  0 
             total       used       free     shared    buffers     cached
Mem:       1015120     673920     341200          0      42296     380024
-/+ buffers/cache:     251600     763520
Swap:      1037308          0    1037308

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Selected interface 'eth2'
OK

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
Kernel modesetting video driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Jun 22 11:21:29 EDT 2012: performing suspend
Fri Jun 22 11:21:35 EDT 2012: Awake.
Fri Jun 22 11:21:35 EDT 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

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
Selected interface 'eth2'
OK

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Jun 22 11:21:37 EDT 2012: Finished.
```


4. BOOT_IMAGE=/boot/vmlinuz-3.2.0-25-generic-pae root=UUID=3fe66fa1-d99a-4fd0-ac03-fb9c747b9224 ro quiet splash vt.handoff=7

---

### Post by anewguy on 2012-06-23
Do us all a favor and either pipe all that to a file then attach the file, or at a minimum post all that between code tags (the # on the menu).  It's a heck of a lot of information for any us to really try to look at.  Just my opinion - I am in no way associated with the forum mods, admins, etc..

---

