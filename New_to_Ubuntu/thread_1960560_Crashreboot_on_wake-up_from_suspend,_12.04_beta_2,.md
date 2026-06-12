---
title: "Crash/reboot on wake-up from suspend, 12.04 beta 2, VAIO VGN-FW590"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by EternalMelody on 2012-04-17
Hello Ubuntu forums. I'm a newbie here and I'm having problems with my Ubuntu, and I'm hoping that someone here can help me out. My computer is VAIO VGN-FW590 running Ubuntu 12.04 beta 2.

The problem:
My computer cannot wake-up/resume. I can suspend just fine, I tell this by looking at the LED power indicator flashing properly. But whenever I try to resume, it just reboots. I'll tell you guys everything that I see when this happens. I choose suspend from power menu. I can see the lock screen, and the computer suspends not long after (screen goes off, LED power indicator flashing orange). I then resume by pressing a button on the keyboard (the CTRL button). **The screen turns on, but is black for one or two seconds, then the VAIO logo pops up just like as if the computer was booting up from a shutdown**. I then see the GRUB menu, etc.

Please help me out guys. Here's /var/log/pm-suspend.log

```
Initial commandline parameters: 
Tue Apr 17 03:10:50 CDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux marioandhika-VGNFW590F 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             32866  0 
ppdev                  17113  0 
rfcomm                 47604  12 
bnep                   18281  2 
vesafb                 13844  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
iwlwifi               328352  0 
snd_hda_intel          33773  5 
hid_logitech_dj        18593  0 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
mac80211              506816  1 iwlwifi
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
btusb                  18288  2 
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             180104  23 rfcomm,bnep,btusb
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
mac_hid                13253  0 
v4l2_compat_ioctl32    17128  1 videodev
r592                   18144  0 
sony_laptop            45393  0 
snd_timer              29990  2 snd_pcm,snd_seq
psmouse                87603  0 
serio_raw              13211  0 
fglrx                3263886  88 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
memstick               16569  1 r592
video                  19596  0 
cfg80211              205544  2 iwlwifi,mac80211
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   59043  0 
             total       used       free     shared    buffers     cached
Mem:       4016332    1181480    2834852          0      75556     458060
-/+ buffers/cache:     647864    3368468
Swap:            0          0          0

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
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
Selected interface 'wlan0'
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
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Apr 17 03:10:52 CDT 2012: performing suspend
Initial commandline parameters: 
Tue Apr 17 03:12:47 CDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux marioandhika-VGNFW590F 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
parport_pc             32866  0 
rfcomm                 47604  12 
bnep                   18281  2 
ppdev                  17113  0 
vesafb                 13844  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlwifi               328352  0 
hid_logitech_dj        18593  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
fglrx                3263886  92 
psmouse                87603  0 
uvcvideo               72627  0 
mac80211              506816  1 iwlwifi
videodev               98259  1 uvcvideo
snd_timer              29990  2 snd_pcm,snd_seq
serio_raw              13211  0 
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
r592                   18144  0 
btusb                  18288  2 
bluetooth             180104  23 rfcomm,bnep,btusb
cfg80211              205544  2 iwlwifi,mac80211
memstick               16569  1 r592
sony_laptop            45393  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
video                  19596  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   59043  0 
             total       used       free     shared    buffers     cached
Mem:       4016332     982712    3033620          0      61112     294928
-/+ buffers/cache:     626672    3389660
Swap:            0          0          0

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
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
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Apr 17 03:12:49 CDT 2012: performing suspend
Initial commandline parameters: 
Tue Apr 17 03:27:04 CDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux marioandhika-VGNFW590F 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
vesafb                 13844  1 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
arc4                   12529  2 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
iwlwifi               328352  0 
mac80211              506816  1 iwlwifi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
hid_logitech_dj        18593  0 
btusb                  18288  2 
bluetooth             180104  23 rfcomm,bnep,btusb
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
r592                   18144  0 
memstick               16569  1 r592
fglrx                3263886  91 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                87603  0 
serio_raw              13211  0 
cfg80211              205544  2 iwlwifi,mac80211
soundcore              15091  1 snd
mac_hid                13253  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sony_laptop            45393  0 
video                  19596  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   59043  0 
             total       used       free     shared    buffers     cached
Mem:       4016332     900828    3115504          0      70440     267432
-/+ buffers/cache:     562956    3453376
Swap:            0          0          0

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
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
Unloading kernel module xhci-hcd...Done.

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Apr 17 03:27:06 CDT 2012: performing suspend
Initial commandline parameters: 
Tue Apr 17 03:28:28 CDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux marioandhika-VGNFW590F 3.2.0-20-generic #33-Ubuntu SMP Tue Mar 27 16:42:26 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47604  12 
parport_pc             32866  0 
bnep                   18281  2 
ppdev                  17113  0 
vesafb                 13809  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
arc4                   12529  2 
joydev                 17693  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13668  1 snd_hda_codec
iwlwifi               328352  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              506816  1 iwlwifi
snd_timer              29990  2 snd_seq,snd_pcm
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_seq_device,snd_pcm,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
fglrx                3263886  91 
r592                   18144  0 
memstick               16569  1 r592
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
btusb                  18288  2 
psmouse                87603  0 
serio_raw              13211  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
cfg80211              205544  2 iwlwifi,mac80211
bluetooth             180104  23 rfcomm,bnep,btusb
hid_logitech_dj        18593  0 
video                  19411  0 
mac_hid                13253  0 
sony_laptop            45393  0 
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   58918  0 
             total       used       free     shared    buffers     cached
Mem:       4016332     868108    3148224          0      57332     276896
-/+ buffers/cache:     533880    3482452
Swap:            0          0          0

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
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
Unloading kernel module xhci-hcd...Done.

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
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
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Apr 17 03:28:30 CDT 2012: performing suspend
Initial commandline parameters: 
Tue Apr 17 03:39:48 CDT 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux marioandhika-VGNFW590F 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
rfcomm                 47604  12 
bnep                   18281  2 
parport_pc             32866  0 
ppdev                  17113  0 
vesafb                 13844  1 
joydev                 17693  0 
arc4                   12529  2 
psmouse                87603  0 
serio_raw              13211  0 
snd_hda_codec_hdmi     32474  1 
btusb                  18288  2 
bluetooth             180104  23 rfcomm,bnep,btusb
r592                   18144  0 
memstick               16569  1 r592
fglrx                3263886  92 
snd_hda_codec_realtek   223867  1 
snd_seq_midi           13324  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30748  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
hid_logitech_dj        18593  0 
sony_laptop            45393  0 
snd_seq_midi_event     14899  1 snd_seq_midi
mac_hid                13253  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
video                  19596  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              29990  2 snd_pcm,snd_seq
iwlwifi               328352  0 
mac80211              506816  1 iwlwifi
cfg80211              205544  2 iwlwifi,mac80211
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_seq_device,snd_timer
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
sky2                   59043  0 
             total       used       free     shared    buffers     cached
Mem:       4016332    2040636    1975696          0      76852    1166080
-/+ buffers/cache:     797704    3218628
Swap:            0          0          0

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend:

/etc/pm/sleep.d/20_custom-ehci_hcd suspend suspend: success.
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
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0

/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Tue Apr 17 03:39:50 CDT 2012: performing suspend
```

---

### Post by anewguy on 2012-04-17
Since 12.04 is still in beta testing and not officially released, you may want to post this in the 12.04 site so the testers know there is some sort of problem.

[http://ubuntuforums.org/forumdisplay.php?f=412]("http://ubuntuforums.org/forumdisplay.php?f=412")

Dave ;)

---

### Post by EternalMelody on 2012-04-17
Sorry about that. Can a mod move this there then please?

---

### Post by EternalMelody on 2012-04-17
Although the problem has slight differences, in that those in this thread don't have their computer automatically reboot when the crash happens, the solution worked for me.

[http://ubuntuforums.org/showpost.php?p=9992908&postcount=33](http://ubuntuforums.org/showpost.php?p=9992908&postcount=33)

---

