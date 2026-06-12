---
title: "Suspend/Resume issue with Compaq NC4010"
date: 2013-09-19
forum: New to Ubuntu
---

### Post by YBGQT4s on 2013-09-19
Hello all,

I've installed lubuntu on my Compaq NC4010 (old computer which likes lightweight distros) but I have an issue with the suspend mode. When I request for suspend, the computer is going fine (power down then blinking power led) but when I press the power button the display keeps black and nothing happens. Only solution: hardware shut off.

Can someone guide me to retrieve logs and identify what is going wrong?

PS: Due to my CPU is not pae, I've installed lubuntu 11.10 then let OS upgrade to 12.10 LTS.

Any help will be appreciated! Thank you :-)

---

### Post by Toz on 2013-09-19
Hello and welcome to the forums.

There are many reports on the internet of suspend not working on this laptop. But lets have a closer look.

The first thing you'll want to make sure of is that you have the latest bios installed. Also, look into the bios settings to see if there any specific settings for acpi or sleep/suspend.

The second thing to do would be to review the log files. The ones of interest would be:
a. /var/log/pm-suspend.log
b. /var/log/dmesg
c. the results of the following command:
```
cat /var/log/syslog | grep PM:
```
It would be best to post these back right after a suspend attempt. Make sure to use code blocks ([noparse]```

```[/noparse]) or a pastebin facility.

As an alternative, have you tried hibernating? You may have more success with it.

---

### Post by YBGQT4s on 2013-09-19
Hello !

I've updated the BIOS to the last version available ([COLOR=#121212][FONT=arial]F.30 - [/FONT][/COLOR][COLOR=#121212][FONT=arial]30/08/2006) but no change at all :-(. And nothing related to [/FONT][/COLOR]specific settings for acpi or sleep/suspend in BIOS.[COLOR=#121212][FONT=arial]

And here are the log files:

[/FONT][/COLOR]```
Initial commandline parameters: Tue Sep 17 23:45:20 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
radeon                733899  2 
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
eeprom_93cx6           12687  1 rtl8187
ttm                    65344  1 radeon
psmouse                96744  0 
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
serio_raw              13027  0 
i2c_ali15x3            12878  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_ali1535            12777  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_algo_bit           13199  1 radeon
video                  19115  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
wmi                    18744  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              14635  1 snd
shpchp                 32265  0 
ati_agp                13242  1 
snd_page_alloc         14115  1 snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     430412     562656          0      44420     264556
-/+ buffers/cache:     121436     871632
Swap:      1013756          0    1013756


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
Tue Sep 17 23:45:25 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 20:13:21 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_seq_midi           13132  0 
eeprom_93cx6           12687  1 rtl8187
i2c_ali15x3            12878  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia                 39826  0 
psmouse                96744  0 
serio_raw              13027  0 
i2c_ali1535            12777  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  19115  0 
i2c_algo_bit           13199  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  0 
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
mac_hid                13077  0 
shpchp                 32265  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     543988     449080          0      44540     327996
-/+ buffers/cache:     171452     821616
Swap:      1013756          0    1013756


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
Wed Sep 18 20:13:26 CEST 2013: performing suspend
Initial commandline parameters: 
mercredi 18 septembre 2013, 22:02:44 (UTC+0200): Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
snd_seq_midi           13132  0 
rtl8187                56323  0 
snd_rawmidi            25424  1 snd_seq_midi
mac80211              436493  1 rtl8187
ttm                    65344  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         45466  1 radeon
cfg80211              178877  2 rtl8187,mac80211
drm                   197641  4 radeon,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
i2c_algo_bit           13199  1 radeon
eeprom_93cx6           12687  1 rtl8187
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96744  0 
i2c_ali15x3            12878  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
shpchp                 32265  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  1 snd_pcm
i2c_ali1535            12777  0 
ati_agp                13242  1 
video                  19115  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     565528     427540          0      48316     341260
-/+ buffers/cache:     175952     817116
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:


/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:


/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:


/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
mercredi 18 septembre 2013, 22:02:47 (UTC+0200): performing hibernate
mercredi 18 septembre 2013, 22:03:57 (UTC+0200): Awake.
mercredi 18 septembre 2013, 22:03:57 (UTC+0200): Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
mercredi 18 septembre 2013, 22:04:06 (UTC+0200): Finished.
Initial commandline parameters: 
Wed Sep 18 22:08:08 CEST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
ttm                    65344  1 radeon
eeprom_93cx6           12687  1 rtl8187
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
psmouse                96744  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
i2c_ali15x3            12878  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
video                  19115  0 
rfcomm                 38139  0 
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia                 39826  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
wmi                    18744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32265  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     532512     460556          0      44284     326112
-/+ buffers/cache:     162116     830952
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
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


/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Wed Sep 18 22:08:13 CEST 2013: performing hibernate
Wed Sep 18 22:09:17 CEST 2013: Awake.
Wed Sep 18 22:09:17 CEST 2013: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Wed Sep 18 22:09:20 CEST 2013: Finished.
Initial commandline parameters: 
Wed Sep 18 22:20:51 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
btrfs                 638340  0 
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
reiserfs              230928  0 
ext2                   67987  0 
arc4                   12473  0 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
ttm                    65344  1 radeon
eeprom_93cx6           12687  1 rtl8187
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
psmouse                96744  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
i2c_ali15x3            12878  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
video                  19115  0 
rfcomm                 38139  0 
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia                 39826  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
wmi                    18744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32265  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     554004     439064          0      19880     320928
-/+ buffers/cache:     213196     779872
Swap:      1013756        128    1013628


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
Wed Sep 18 22:20:53 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 22:27:34 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12687  1 rtl8187
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197641  4 radeon,ttm,drm_kms_helper
serio_raw              13027  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_ali1535            12777  0 
soundcore              14635  1 snd
i2c_algo_bit           13199  1 radeon
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
ppdev                  12849  0 
bluetooth             158447  10 rfcomm,bnep
video                  19115  0 
wmi                    18744  0 
shpchp                 32265  0 
ati_agp                13242  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     543060     450008          0      44260     324912
-/+ buffers/cache:     173888     819180
Swap:      1013756          0    1013756


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
Wed Sep 18 22:27:37 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 22:49:20 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
radeon                733899  2 
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12687  1 rtl8187
ttm                    65344  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
psmouse                96744  0 
pcmcia                 39826  0 
drm_kms_helper         45466  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197641  4 radeon,ttm,drm_kms_helper
serio_raw              13027  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali1535            12777  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13199  1 radeon
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
video                  19115  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
wmi                    18744  0 
shpchp                 32265  0 
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     531496     461572          0      44240     323988
-/+ buffers/cache:     163268     829800
Swap:      1013756          0    1013756


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
Wed Sep 18 22:49:24 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 23:14:09 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
btrfs                 638340  0 
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
reiserfs              230928  0 
ext2                   67987  0 
arc4                   12473  2 
joydev                 17393  0 
snd_ali5451            23459  2 
rtl8187                56323  0 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
mac80211              436493  1 rtl8187
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
eeprom_93cx6           12687  1 rtl8187
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
i2c_algo_bit           13199  1 radeon
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
i2c_ali15x3            12878  0 
soundcore              14635  1 snd
shpchp                 32265  0 
ati_agp                13242  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_ali1535            12777  0 
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
video                  19115  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     508908     484160          0      47024     347212
-/+ buffers/cache:     114672     878396
Swap:      1013756          0    1013756


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
Wed Sep 18 23:14:13 CEST 2013: performing suspend
Initial commandline parameters: 
Thu Sep 19 22:51:55 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_ali5451            23459  2 
eeprom_93cx6           12687  1 rtl8187
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
psmouse                96744  0 
snd_seq_midi           13132  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
i2c_ali15x3            12878  0 
video                  19115  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_ali1535            12777  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 radeon
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
wmi                    18744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
ati_agp                13242  1 
snd_page_alloc         14115  1 snd_pcm
shpchp                 32265  0 
mac_hid                13077  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     557940     435128          0      44356     329460
-/+ buffers/cache:     184124     808944
Swap:      1013756          0    1013756


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
Thu Sep 19 22:51:59 CEST 2013: performing suspend

```[COLOR=#000000]

[/COLOR]
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-53-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 (Ubuntu 3.2.0-53.81-generic 3.2.50)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003dfd0000 (usable)
[    0.000000]  BIOS-e820: 000000003dfd0000 - 000000003dff0c00 (reserved)
[    0.000000]  BIOS-e820: 000000003dff0c00 - 000000003dffc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003dffc000 - 000000003e000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: Hewlett-Packard HP Compaq nc4010 (DY886AA#ABF)  /0834, BIOS 68BAS Ver. F.30 08/30/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3dfd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 base 03C000000 mask FFE000000 write-back
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bf8000-1c00000
[    0.000000] RAMDISK: 364e0000 - 37268000
[    0.000000] ACPI: RSDP 000f7840 00014 (v00 COMPAQ)
[    0.000000] ACPI: RSDT 3dff0c84 0002C (v01 COMPAQ CPQ005A  30080620 CPQ  00000001)
[    0.000000] ACPI: FACP 3dff0c00 00084 (v02 COMPAQ CPQ005A  00000002 CPQ  00000001)
[    0.000000] ACPI: DSDT 3dff0cb0 0607E (v01 COMPAQ  EVON800 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3dffbe80 00040
[    0.000000] ACPI: SSDT 3dff6d2e 002A7 (v01 COMPAQ  CPQGysr 00001001 MSFT 0100000E)
[    0.000000] 103MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003dfd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003dfd0
[    0.000000] On node 0 totalpages: 253791
[    0.000000] free_area_init_node: node 0, pgdat c182bd40, node_mem_map f5d20200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 208 pages used for memmap
[    0.000000]   HighMem zone: 26370 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3e000000 (gap: 3e000000:c2000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77ea000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 251807
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-generic root=UUID=0e519161-7a32-4e2e-915c-7da765feae21 ro noapic nolapic quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4062208 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003dfd0)
[    0.000000] Memory: 978472k/1015616k available (5636k kernel code, 36692k reserved, 2780k data, 716k init, 106312k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1839000 - 0xc18ec000   ( 716 kB)
[    0.000000]       .data : 0xc1581284 - 0xc1838480   (2780 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1581284   (5636 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1492.633 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2985.26 BogoMIPS (lpj=5970532)
[    0.008014] pid_max: default: 32768 minimum: 301
[    0.008063] Security Framework initialized
[    0.008120] AppArmor: AppArmor initialized
[    0.008123] Yama: becoming mindful.
[    0.008247] Mount-cache hash table entries: 512
[    0.008557] Initializing cgroup subsys cpuacct
[    0.008572] Initializing cgroup subsys memory
[    0.008590] Initializing cgroup subsys devices
[    0.008595] Initializing cgroup subsys freezer
[    0.008599] Initializing cgroup subsys blkio
[    0.008614] Initializing cgroup subsys perf_event
[    0.008680] mce: CPU supports 5 MCE banks
[    0.009153] SMP alternatives: switching to UP code
[    0.022305] Freeing SMP alternatives: 24k freed
[    0.022322] ACPI: Core revision 20110623
[    0.026963] ACPI: setting ELCR to 0200 (from 0c00)
[    0.028091] ftrace: allocating 25519 entries in 50 pages
[    0.032220] weird, boot CPU (#0) not listed by the BIOS.
[    0.032231] SMP motherboard not detected.
[    0.032235] Apic disabled
[    0.032237] Local APIC not detected. Using dummy APIC emulation.
[    0.032240] SMP disabled
[    0.032244] Performance Events: 
[    0.032250] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.032253] no hardware sampling interrupt available.
[    0.032260] p6 PMU driver.
[    0.032270] ... version:                0
[    0.032273] ... bit width:              32
[    0.032275] ... generic registers:      2
[    0.032278] ... value mask:             00000000ffffffff
[    0.032281] ... max period:             000000007fffffff
[    0.032284] ... fixed-purpose events:   0
[    0.032286] ... event mask:             0000000000000003
[    0.032830] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[    0.032938] Brought up 1 CPUs
[    0.032943] Total of 1 processors activated (2985.26 BogoMIPS).
[    0.033425] devtmpfs: initialized
[    0.033699] EVM: security.selinux
[    0.033702] EVM: security.SMACK64
[    0.033705] EVM: security.capability
[    0.033789] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
[    0.033829] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.038783] print_constraints: dummy: 
[    0.038847] RTC time: 20:53:15, date: 09/19/13
[    0.038938] NET: Registered protocol family 16
[    0.039190] EISA bus registered
[    0.039266] ACPI: bus type pci registered
[    0.042112] PCI: PCI BIOS revision 2.10 entry at 0xf031f, last bus=1
[    0.042116] PCI: Using configuration type 1 for base access
[    0.044353] bio: create slab <bio-0> at 0
[    0.044530] ACPI: Added _OSI(Module Device)
[    0.044535] ACPI: Added _OSI(Processor Device)
[    0.044538] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.044542] ACPI: Added _OSI(Processor Aggregator Device)
[    0.046026] ACPI: EC: Look up EC in DSDT
[    0.064096] ACPI: Interpreter enabled
[    0.064122] ACPI: (supports S0 S3 S4 S5)
[    0.064151] ACPI: Using PIC for interrupt routing
[    0.066006] ACPI: Power Resource [C15A] (on)
[    0.068335] ACPI: Power Resource [C15F] (on)
[    0.069483] ACPI: Power Resource [C169] (on)
[    0.070357] ACPI: Power Resource [C17A] (on)
[    0.074697] ACPI: Power Resource [C1F2] (off)
[    0.074781] ACPI: Power Resource [C1F3] (off)
[    0.074869] ACPI: Power Resource [C1F4] (off)
[    0.074959] ACPI: Power Resource [C1F5] (off)
[    0.075676] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.075911] ACPI: No dock devices found.
[    0.075915] HEST: Table not found.
[    0.075926] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.080285] ACPI: PCI Root Bridge [C044] (domain 0000 [bus 00-ff])
[    0.088926] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.088931] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.088936] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.088941] pci_root PNP0A03:00: host bridge window [mem 0x3e000000-0xffffffff] (ignored)
[    0.088945] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.088969] pci 0000:00:00.0: [1002:cbb2] type 0 class 0x000600
[    0.088986] pci 0000:00:00.0: reg 10: [mem 0x9c000000-0x9fffffff pref]
[    0.088993] pci 0000:00:00.0: reg 14: [mem 0x98480000-0x98480fff pref]
[    0.089050] pci 0000:00:01.0: [1002:7010] type 1 class 0x000604
[    0.089088] pci 0000:00:06.0: [10b9:5451] type 0 class 0x000401
[    0.089102] pci 0000:00:06.0: reg 10: [io  0x3000-0x30ff]
[    0.089111] pci 0000:00:06.0: reg 14: [mem 0x98080000-0x98080fff]
[    0.089159] pci 0000:00:06.0: supports D1 D2
[    0.089164] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.089171] pci 0000:00:06.0: PME# disabled
[    0.089189] pci 0000:00:07.0: [10b9:1533] type 0 class 0x000601
[    0.089273] pci 0000:00:08.0: [10b9:5457] type 0 class 0x000703
[    0.089287] pci 0000:00:08.0: reg 10: [mem 0x98100000-0x98100fff]
[    0.089296] pci 0000:00:08.0: reg 14: [io  0x3400-0x34ff]
[    0.089342] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.089347] pci 0000:00:08.0: PME# disabled
[    0.089370] pci 0000:00:0b.0: [1217:7114] type 2 class 0x000607
[    0.089385] pci 0000:00:0b.0: reg 10: [mem 0x98180000-0x98180fff]
[    0.089408] pci 0000:00:0b.0: supports D1 D2
[    0.089412] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089417] pci 0000:00:0b.0: PME# disabled
[    0.089436] pci 0000:00:0b.1: [1217:7114] type 2 class 0x000607
[    0.089451] pci 0000:00:0b.1: reg 10: [mem 0x98200000-0x98200fff]
[    0.089474] pci 0000:00:0b.1: supports D1 D2
[    0.089477] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089483] pci 0000:00:0b.1: PME# disabled
[    0.089501] pci 0000:00:0b.2: [1217:7110] type 0 class 0x000880
[    0.089516] pci 0000:00:0b.2: reg 10: [mem 0x98280000-0x98280fff]
[    0.089573] pci 0000:00:0b.2: supports D1 D2
[    0.089576] pci 0000:00:0b.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089582] pci 0000:00:0b.2: PME# disabled
[    0.089607] pci 0000:00:10.0: [10b9:5229] type 0 class 0x000101
[    0.089641] pci 0000:00:10.0: reg 20: [io  0x3800-0x380f]
[    0.089684] pci 0000:00:11.0: [10b9:7101] type 0 class 0x000680
[    0.089742] pci 0000:00:11.0: quirk: [io  0x1000-0x103f] claimed by ali7101 ACPI
[    0.089747] pci 0000:00:11.0: quirk: [io  0x1100-0x111f] claimed by ali7101 SMB
[    0.089768] pci 0000:00:12.0: [1033:0035] type 0 class 0x000c03
[    0.089782] pci 0000:00:12.0: reg 10: [mem 0x98300000-0x98300fff]
[    0.089834] pci 0000:00:12.0: supports D1 D2
[    0.089837] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089842] pci 0000:00:12.0: PME# disabled
[    0.089859] pci 0000:00:12.1: [1033:0035] type 0 class 0x000c03
[    0.089873] pci 0000:00:12.1: reg 10: [mem 0x98380000-0x98380fff]
[    0.089925] pci 0000:00:12.1: supports D1 D2
[    0.089929] pci 0000:00:12.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.089934] pci 0000:00:12.1: PME# disabled
[    0.089951] pci 0000:00:12.2: [1033:00e0] type 0 class 0x000c03
[    0.089965] pci 0000:00:12.2: reg 10: [mem 0x98400000-0x984000ff]
[    0.090017] pci 0000:00:12.2: supports D1 D2
[    0.090021] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090026] pci 0000:00:12.2: PME# disabled
[    0.090054] pci 0000:00:13.0: [14e4:165d] type 0 class 0x000200
[    0.090078] pci 0000:00:13.0: reg 10: [mem 0x98000000-0x9800ffff 64bit]
[    0.090113] pci 0000:00:13.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.090154] pci 0000:00:13.0: PME# supported from D3hot D3cold
[    0.090159] pci 0000:00:13.0: PME# disabled
[    0.090208] pci 0000:01:05.0: [1002:4337] type 0 class 0x000300
[    0.090223] pci 0000:01:05.0: reg 10: [mem 0x94000000-0x97ffffff pref]
[    0.090232] pci 0000:01:05.0: reg 14: [io  0x2000-0x20ff]
[    0.090241] pci 0000:01:05.0: reg 18: [mem 0x90000000-0x9000ffff]
[    0.090265] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.090292] pci 0000:01:05.0: supports D1 D2
[    0.090321] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.090329] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.090335] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x900fffff]
[    0.090340] pci 0000:00:01.0:   bridge window [mem 0x94000000-0x97ffffff pref]
[    0.090402] pci_bus 0000:00: on NUMA node 0
[    0.090408] ACPI: PCI Interrupt Routing Table [\_SB_.C044._PRT]
[    0.090517] ACPI: PCI Interrupt Routing Table [\_SB_.C044.C045._PRT]
[    0.090599]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.103572] ACPI: PCI Interrupt Link [C0C4] (IRQs 5 *10 11)
[    0.103675] ACPI: PCI Interrupt Link [C0C5] (IRQs 5 *10 11)
[    0.103772] ACPI: PCI Interrupt Link [C0C6] (IRQs 5 10 *11)
[    0.103850] ACPI: PCI Interrupt Link [C0C7] (IRQs 5 10 11) *0, disabled.
[    0.103949] ACPI: PCI Interrupt Link [C0C8] (IRQs 5 *10 11)
[    0.104035] ACPI: PCI Interrupt Link [C0C9] (IRQs 5 10 11) *0, disabled.
[    0.104135] ACPI: PCI Interrupt Link [C0CA] (IRQs 5 10 *11)
[    0.104232] ACPI: PCI Interrupt Link [C0CB] (IRQs 5 10 *11)
[    0.104477] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.104482] vgaarb: loaded
[    0.104485] vgaarb: bridge control possible 0000:01:05.0
[    0.104708] i2c-core: driver [aat2870] using legacy suspend method
[    0.104711] i2c-core: driver [aat2870] using legacy resume method
[    0.104912] SCSI subsystem initialized
[    0.105040] libata version 3.00 loaded.
[    0.105144] usbcore: registered new interface driver usbfs
[    0.105175] usbcore: registered new interface driver hub
[    0.105221] usbcore: registered new device driver usb
[    0.105399] PCI: Using ACPI for IRQ routing
[    0.105407] PCI: pci_cache_line_size set to 64 bytes
[    0.105477] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.105483] reserve RAM buffer: 000000003dfd0000 - 000000003fffffff 
[    0.105712] NetLabel: Initializing
[    0.105716] NetLabel:  domain hash size = 128
[    0.105719] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.105744] NetLabel:  unlabeled traffic allowed by default
[    0.105857] Switching to clocksource pit
[    0.122523] AppArmor: AppArmor Filesystem Enabled
[    0.122654] pnp: PnP ACPI init
[    0.122704] ACPI: bus type pnp registered
[    0.122999] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.123005] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.123010] pnp 00:00: [mem 0x00100000-0x3dffffff]
[    0.123153] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.123160] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.123165] system 00:00: [mem 0x00100000-0x3dffffff] could not be reserved
[    0.123174] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.127572] pnp 00:01: [bus 00-ff]
[    0.127578] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.127582] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.127586] pnp 00:01: [io  0x0d00-0xffff window]
[    0.127590] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.127595] pnp 00:01: [mem 0x3e000000-0xffffffff window]
[    0.127599] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.127773] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.128866] pnp 00:02: [io  0x03f8-0x03ff]
[    0.128876] pnp 00:02: [irq 4]
[    0.128977] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
[    0.130092] pnp 00:03: [io  0x03e8-0x03ef]
[    0.130097] pnp 00:03: [irq 3]
[    0.130101] pnp 00:03: [dma 3]
[    0.130243] pnp 00:03: Plug and Play ACPI device, IDs ALI5123 PNP0510 (active)
[    0.131433] pnp 00:04: [io  0x0378-0x037f]
[    0.131437] pnp 00:04: [io  0x0778-0x077a]
[    0.131441] pnp 00:04: [irq 7]
[    0.131444] pnp 00:04: [dma 1]
[    0.131617] pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.131706] pnp 00:05: [io  0x00f0-0x00ff]
[    0.131710] pnp 00:05: [irq 13]
[    0.131759] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.131779] pnp 00:06: [io  0x0000-0x000f]
[    0.131783] pnp 00:06: [io  0x0080-0x008f]
[    0.131786] pnp 00:06: [io  0x00c0-0x00df]
[    0.131790] pnp 00:06: [dma 4]
[    0.131838] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.131853] pnp 00:07: [io  0x0061]
[    0.131906] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.131922] pnp 00:08: [io  0x0070-0x0071]
[    0.131926] pnp 00:08: [io  0x0072-0x0073]
[    0.131930] pnp 00:08: [irq 8]
[    0.131985] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.132001] pnp 00:09: [io  0x0060]
[    0.132005] pnp 00:09: [io  0x0064]
[    0.132008] pnp 00:09: [irq 1]
[    0.132057] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.132071] pnp 00:0a: [irq 12]
[    0.132130] pnp 00:0a: Plug and Play ACPI device, IDs SYN0102 SYN0100 SYN0002 PNP0f13 (active)
[    0.132278] pnp 00:0b: [io  0x002e-0x002f]
[    0.132282] pnp 00:0b: [io  0x004e-0x004f]
[    0.132285] pnp 00:0b: [io  0x0063]
[    0.132288] pnp 00:0b: [io  0x0065]
[    0.132292] pnp 00:0b: [io  0x0067-0x006f]
[    0.132295] pnp 00:0b: [io  0x0074-0x007f]
[    0.132299] pnp 00:0b: [io  0x0092]
[    0.132302] pnp 00:0b: [io  0x00b0-0x00b3]
[    0.132305] pnp 00:0b: [io  0x0370-0x0371]
[    0.132309] pnp 00:0b: [io  0x040b]
[    0.132312] pnp 00:0b: [io  0x0480-0x048f]
[    0.132316] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.132319] pnp 00:0b: [io  0x04d6]
[    0.132322] pnp 00:0b: [io  0x1400-0x141f]
[    0.132327] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.132330] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.132434] system 00:0b: [io  0x0370-0x0371] has been reserved
[    0.132439] system 00:0b: [io  0x040b] has been reserved
[    0.132443] system 00:0b: [io  0x0480-0x048f] has been reserved
[    0.132448] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.132452] system 00:0b: [io  0x04d6] has been reserved
[    0.132456] system 00:0b: [io  0x1400-0x141f] has been reserved
[    0.132462] system 00:0b: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.132467] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.132472] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.133862] pnp 00:0c: [io  0x1000-0x107f]
[    0.133866] pnp 00:0c: [io  0x1100-0x111f]
[    0.133870] pnp 00:0c: [mem 0x98480000-0x98480fff]
[    0.133965] system 00:0c: [io  0x1000-0x107f] could not be reserved
[    0.133970] system 00:0c: [io  0x1100-0x111f] has been reserved
[    0.133976] system 00:0c: [mem 0x98480000-0x98480fff] has been reserved
[    0.133981] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.134642] pnp 00:0d: [mem 0x000cf000-0x000cffff]
[    0.134733] system 00:0d: [mem 0x000cf000-0x000cffff] has been reserved
[    0.134738] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.134764] pnp: PnP ACPI: found 14 devices
[    0.134769] ACPI: ACPI bus type pnp unregistered
[    0.134778] PnPBIOS: Disabled by ACPI PNP
[    0.172723] Switching to clocksource acpi_pm
[    0.172787] PCI: max bus depth: 1 pci_try_num: 2
[    0.172836] pci 0000:00:13.0: BAR 6: assigned [mem 0x40000000-0x4000ffff pref]
[    0.172844] pci 0000:00:0b.1: BAR 16: assigned [mem 0x44000000-0x47ffffff]
[    0.172849] pci 0000:00:0b.1: BAR 15: assigned [mem 0x48000000-0x4bffffff pref]
[    0.172856] pci 0000:00:0b.1: BAR 14: assigned [io  0x1800-0x18ff]
[    0.172861] pci 0000:00:0b.1: BAR 13: assigned [io  0x1c00-0x1cff]
[    0.172866] pci 0000:00:0b.0: BAR 16: assigned [mem 0x4c000000-0x4fffffff]
[    0.172871] pci 0000:00:0b.0: BAR 15: assigned [mem 0x50000000-0x53ffffff pref]
[    0.172877] pci 0000:00:0b.0: BAR 14: assigned [io  0x3c00-0x3cff]
[    0.172883] pci 0000:00:0b.0: BAR 13: assigned [io  0x4000-0x40ff]
[    0.172889] pci 0000:01:05.0: BAR 6: assigned [mem 0x90020000-0x9003ffff pref]
[    0.172895] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.172901] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.172907] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x900fffff]
[    0.172913] pci 0000:00:01.0:   bridge window [mem 0x94000000-0x97ffffff pref]
[    0.172920] pci 0000:00:0b.0: CardBus bridge to [bus 02-05]
[    0.172924] pci 0000:00:0b.0:   bridge window [io  0x4000-0x40ff]
[    0.172930] pci 0000:00:0b.0:   bridge window [io  0x3c00-0x3cff]
[    0.172935] pci 0000:00:0b.0:   bridge window [mem 0x50000000-0x53ffffff pref]
[    0.172941] pci 0000:00:0b.0:   bridge window [mem 0x4c000000-0x4fffffff]
[    0.172947] pci 0000:00:0b.1: CardBus bridge to [bus 06-09]
[    0.172951] pci 0000:00:0b.1:   bridge window [io  0x1c00-0x1cff]
[    0.172956] pci 0000:00:0b.1:   bridge window [io  0x1800-0x18ff]
[    0.172962] pci 0000:00:0b.1:   bridge window [mem 0x48000000-0x4bffffff pref]
[    0.172967] pci 0000:00:0b.1:   bridge window [mem 0x44000000-0x47ffffff]
[    0.173277] ACPI: PCI Interrupt Link [C0C6] enabled at IRQ 11
[    0.173284] PCI: setting IRQ 11 as level-triggered
[    0.173292] pci 0000:00:0b.0: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[    0.173304] pci 0000:00:0b.1: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[    0.173312] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.173316] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.173321] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.173326] pci_bus 0000:01: resource 1 [mem 0x90000000-0x900fffff]
[    0.173330] pci_bus 0000:01: resource 2 [mem 0x94000000-0x97ffffff pref]
[    0.173334] pci_bus 0000:02: resource 0 [io  0x4000-0x40ff]
[    0.173338] pci_bus 0000:02: resource 1 [io  0x3c00-0x3cff]
[    0.173343] pci_bus 0000:02: resource 2 [mem 0x50000000-0x53ffffff pref]
[    0.173347] pci_bus 0000:02: resource 3 [mem 0x4c000000-0x4fffffff]
[    0.173351] pci_bus 0000:06: resource 0 [io  0x1c00-0x1cff]
[    0.173355] pci_bus 0000:06: resource 1 [io  0x1800-0x18ff]
[    0.173360] pci_bus 0000:06: resource 2 [mem 0x48000000-0x4bffffff pref]
[    0.173364] pci_bus 0000:06: resource 3 [mem 0x44000000-0x47ffffff]
[    0.173477] NET: Registered protocol family 2
[    0.173627] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.174290] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.177506] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.179495] TCP: Hash tables configured (established 131072 bind 65536)
[    0.179502] TCP reno registered
[    0.179513] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.179581] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.179947] NET: Registered protocol family 1
[    0.180109] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    0.180530] ACPI: PCI Interrupt Link [C0C5] enabled at IRQ 10
[    0.180538] PCI: setting IRQ 10 as level-triggered
[    0.180547] pci 0000:00:12.0: PCI INT A -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.180597] pci 0000:00:12.0: PCI INT A disabled
[    0.180617] pci 0000:00:12.1: PCI INT B -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.180628] pci 0000:00:12.1: PCI INT B disabled
[    0.180641] pci 0000:00:12.2: PCI INT C -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.180655] pci 0000:00:12.2: PCI INT C disabled
[    0.180668] pci 0000:01:05.0: Boot video device
[    0.180673] PCI: CLS 64 bytes, default 64
[    0.181600] audit: initializing netlink socket (disabled)
[    0.181631] type=2000 audit(1379623995.176:1): initialized
[    0.216362] Trying to unpack rootfs image as initramfs...
[    0.257263] highmem bounce pool size: 64 pages
[    0.257280] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.268642] VFS: Disk quotas dquot_6.5.2
[    0.268801] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.269979] fuse init (API version 7.17)
[    0.270156] msgmni has been set to 1703
[    0.280850] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.284155] io scheduler noop registered
[    0.284162] io scheduler deadline registered
[    0.284209] io scheduler cfq registered (default)
[    0.284563] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.284602] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.286731] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.286916] ACPI: AC Adapter [C137] (on-line)
[    0.287090] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.287106] ACPI: Sleep Button [C13B]
[    0.287193] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.287269] ACPI: Lid Switch [C13A]
[    0.287354] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.287360] ACPI: Power Button [PWRF]
[    0.287509] ACPI: Fan [C1F6] (off)
[    0.287590] ACPI: Fan [C1F7] (off)
[    0.287667] ACPI: Fan [C1F8] (off)
[    0.287745] ACPI: Fan [C1F9] (off)
[    0.287786] ACPI: Invalid PBLK length [7]
[    0.287875] Marking TSC unstable due to TSC halts in idle
[    0.287893] ACPI: acpi_idle registered with cpuidle
[    0.307167] thermal LNXTHERM:00: registered as thermal_zone0
[    0.307175] ACPI: Thermal Zone [TZ1] (54 C)
[    0.311062] thermal LNXTHERM:01: registered as thermal_zone1
[    0.311066] ACPI: Thermal Zone [TZ2] (42 C)
[    0.325931] thermal LNXTHERM:02: registered as thermal_zone2
[    0.325941] ACPI: Thermal Zone [TZ3] (29 C)
[    0.326083] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.326108] ACPI: Battery Slot [C139] (battery present)
[    0.326132] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.326142] ACPI: Battery Slot [C138] (battery absent)
[    0.326195] ERST: Table is not found!
[    0.326198] GHES: HEST is not enabled!
[    0.326574] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.347200] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.353195] ACPI: Battery Slot [C138] (battery absent)
[    0.353267] isapnp: Scanning for PnP cards...
[    0.445197] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.466637] ACPI: Battery Slot [C139] (battery present)
[    0.495045] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.560932] ACPI: PCI Interrupt Link [C0CA] enabled at IRQ 11
[    0.560949] serial 0000:00:08.0: PCI INT A -> Link[C0CA] -> GSI 11 (level, low) -> IRQ 11
[    0.560979] serial 0000:00:08.0: PCI INT A disabled
[    0.561373] Linux agpgart interface v0.103
[    0.568948] brd: module loaded
[    0.570332] loop: module loaded
[    0.571111] ACPI: PCI Interrupt Link [C0C4] enabled at IRQ 10
[    0.571124] pata_acpi 0000:00:10.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[    0.571242] pata_acpi 0000:00:10.0: PCI INT A disabled
[    0.571916] Fixed MDIO Bus: probed
[    0.571956] tun: Universal TUN/TAP device driver, 1.6
[    0.571959] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.572156] PPP generic driver version 2.4.2
[    0.572347] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.572383] ehci_hcd 0000:00:12.2: PCI INT C -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.572420] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.572486] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.596355] ehci_hcd 0000:00:12.2: irq 10, io mem 0x98400000
[    0.640079] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.716464] hub 1-0:1.0: USB hub found
[    0.716481] hub 1-0:1.0: 5 ports detected
[    0.716687] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.716756] ohci_hcd 0000:00:12.0: PCI INT A -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.716805] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.716980] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 2
[    0.717029] ohci_hcd 0000:00:12.0: irq 10, io mem 0x98300000
[    0.900601] hub 2-0:1.0: USB hub found
[    0.900618] hub 2-0:1.0: 3 ports detected
[    0.900799] ohci_hcd 0000:00:12.1: PCI INT B -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.900850] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.900989] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 3
[    0.901044] ohci_hcd 0000:00:12.1: irq 10, io mem 0x98380000
[    1.072129] isapnp: No Plug & Play device found
[    1.072207] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.092647] hub 3-0:1.0: USB hub found
[    1.092664] hub 3-0:1.0: 2 ports detected
[    1.092843] uhci_hcd: USB Universal Host Controller Interface driver
[    1.093052] usbcore: registered new interface driver libusual
[    1.093170] i8042: PNP: PS/2 Controller [PNP0303:C177,PNP0f13:C178] at 0x60,0x64 irq 1,12
[    1.094865] i8042: Detected active multiplexing controller, rev 1.1
[    1.095627] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.095651] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.100461] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.100572] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.100626] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.100907] mousedev: PS/2 mouse device common for all mice
[    1.101251] rtc_cmos 00:08: RTC can wake from S4
[    1.101487] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.101555] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.101751] device-mapper: uevent: version 1.0.3
[    1.101889] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.101954] EISA: Probing bus 0 at eisa.0
[    1.101971] Cannot allocate resource for EISA slot 1
[    1.101975] Cannot allocate resource for EISA slot 2
[    1.101979] Cannot allocate resource for EISA slot 3
[    1.101983] Cannot allocate resource for EISA slot 4
[    1.102007] EISA: Detected 0 cards.
[    1.102035] cpufreq-nforce2: No nForce2 chipset.
[    1.102112] cpuidle: using governor ladder
[    1.102219] cpuidle: using governor menu
[    1.102223] EFI Variables Facility v0.08 2004-May-17
[    1.102708] TCP cubic registered
[    1.102950] NET: Registered protocol family 10
[    1.103984] NET: Registered protocol family 17
[    1.103994] Registering the dns_resolver key type
[    1.104104] Using IPI No-Shortcut mode
[    1.107783] PM: Hibernation image not present or could not be loaded.
[    1.107823] registered taskstats version 1
[    1.122990] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.299456] Freeing initrd memory: 13856k freed
[    1.365883]   Magic number: 13:906:902
[    1.366240] rtc_cmos 00:08: setting system clock to 2013-09-19 20:53:16 UTC (1379623996)
[    1.367342] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.367349] EDD information not available.
[    1.367804] Freeing unused kernel memory: 716k freed
[    1.368857] Write protecting the kernel text: 5640k
[    1.368916] Write protecting the kernel read-only data: 2332k
[    1.399821] udevd[80]: starting version 175
[    1.600602] pata_ali 0000:00:10.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[    1.610579] scsi0 : pata_ali
[    1.614002] scsi1 : pata_ali
[    1.614618] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x3800 irq 14
[    1.614624] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3808 irq 15
[    1.763356] tg3.c:v3.121 (November 2, 2011)
[    1.763711] ACPI: PCI Interrupt Link [C0C8] enabled at IRQ 10
[    1.763723] tg3 0000:00:13.0: PCI INT A -> Link[C0C8] -> GSI 10 (level, low) -> IRQ 10
[    1.783607] ata1.00: ATA-6: Hitachi IC25N040ATMR04-0, MO2AAD0A, max UDMA/100
[    1.783616] ata1.00: 78140160 sectors, multi 16: LBA48 
[    1.817302] ata1.00: configured for UDMA/100
[    1.817645] scsi 0:0:0:0: Direct-Access     ATA      Hitachi IC25N040 MO2A PQ: 0 ANSI: 5
[    1.818034] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.818116] sd 0:0:0:0: [sda] Write Protect is off
[    1.818122] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.818156] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.818738] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.833800] tg3 0000:00:13.0: eth0: Tigon3 [partno(BCM5705mA1) rev 3003] (PCI:33MHz:32-bit) MAC address 00:0d:9d:8e:45:25
[    1.833812] tg3 0000:00:13.0: eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0], EEE[0])
[    1.833818] tg3 0000:00:13.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.833823] tg3 0000:00:13.0: eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    1.865741]  sda: sda1 sda2 < sda5 >
[    1.866434] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.384163] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.384172] EXT4-fs (sda1): write access will be enabled during recovery
[    3.288740] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.288764] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1706033
[    3.288931] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1706022
[    3.288954] EXT4-fs (sda1): 2 orphan inodes deleted
[    3.288958] EXT4-fs (sda1): recovery complete
[    3.474577] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   26.026680] Adding 1013756k swap on /dev/sda5.  Priority:-1 extents:1 across:1013756k 
[   26.052314] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.112869] udevd[316]: starting version 175
[   26.229525] lp: driver loaded but no devices found
[   26.660178] agpgart-ati 0000:00:00.0: Ati IGP345M chipset
[   26.687758] wmi: Mapper loaded
[   26.986116] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0x9c000000
[   26.987796] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.989049] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input4
[   26.990521] ACPI: Video Device [C046] (multi-head: yes  rom: no  post: no)
[   27.064573] parport_pc 00:04: reported by Plug and Play ACPI
[   27.064651] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   27.176589] lp0: using parport0 (interrupt-driven).
[   27.197615] ACPI: resource ali1535_smbus [io  0x1100-0x111f] conflicts with ACPI region C092 [io 0x1100-0x1107]
[   27.197623] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   27.197631] ali1535_smbus 0000:00:11.0: ALI1535 not detected, module not inserted.
[   27.206637] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   27.206650] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   27.210305] yenta_cardbus 0000:00:0b.0: CardBus bridge found [0e11:005a]
[   27.210330] yenta_cardbus 0000:00:0b.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   27.336966] yenta_cardbus 0000:00:0b.0: ISA IRQ mask 0x0038, PCI irq 11
[   27.336974] yenta_cardbus 0000:00:0b.0: Socket status: 30000820
[   27.344694] yenta_cardbus 0000:00:0b.1: CardBus bridge found [0e11:005a]
[   27.364153] [drm] Initialized drm 1.1.0 20060810
[   27.472798] yenta_cardbus 0000:00:0b.1: ISA IRQ mask 0x0038, PCI irq 11
[   27.472807] yenta_cardbus 0000:00:0b.1: Socket status: 30000006
[   27.481519] type=1400 audit(1379624022.611:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=536 comm="apparmor_parser"
[   27.482304] type=1400 audit(1379624022.611:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=536 comm="apparmor_parser"
[   27.482780] type=1400 audit(1379624022.611:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=536 comm="apparmor_parser"
[   27.572868] cfg80211: Calling CRDA to update world regulatory domain
[   27.616652] type=1400 audit(1379624022.747:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=542 comm="apparmor_parser"
[   27.868491] [drm] radeon defaulting to kernel modesetting.
[   27.868503] [drm] radeon kernel modesetting enabled.
[   27.868696] radeon 0000:01:05.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[   27.870598] [drm] initializing kernel modesetting (RS200 0x1002:0x4337 0x0E11:0x005A).
[   27.870782] [drm] register mmio base: 0x90000000
[   27.870785] [drm] register mmio size: 65536
[   27.871374] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   27.871469] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   27.871961] radeon 0000:01:05.0: putting AGP V2 device into 4x mode
[   27.871969] radeon 0000:01:05.0: GTT: 64M 0x9C000000 - 0x9FFFFFFF
[   27.871983] radeon 0000:01:05.0: VRAM: 32M 0x000000003E000000 - 0x000000003FFFFFFF (32M used)
[   27.877986] [drm] Detected VRAM RAM=32M, BAR=64M
[   27.877995] [drm] RAM width 64bits DDR
[   27.880188] [TTM] Zone  kernel: Available graphics memory: 443378 kiB.
[   27.880193] [TTM] Zone highmem: Available graphics memory: 496534 kiB.
[   27.880198] [TTM] Initializing pool allocator.
[   27.880271] [drm] radeon: 32M of VRAM memory ready
[   27.880275] [drm] radeon: 64M of GTT memory ready.
[   28.113500] radeon 0000:01:05.0: WB disabled
[   28.113517] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   28.113521] [drm] Driver supports precise vblank timestamp query.
[   28.113561] [drm] radeon: irq initialized.
[   28.145944] psmouse serio4: synaptics: Touchpad model: 1, fw: 5.9, id: 0x1b6eb1, caps: 0xa84793/0x100000/0x0
[   28.145966] psmouse serio4: synaptics: serio: Synaptics pass-through port at isa0060/serio4/input0
[   28.156298] [drm] Loading R100 Microcode
[   28.195444] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   28.232164] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   28.232202] pci 0000:02:00.0: [1033:0035] type 0 class 0x000c03
[   28.232231] pci 0000:02:00.0: reg 10: [mem 0x00000000-0x00000fff]
[   28.232319] pci 0000:02:00.0: supports D1 D2
[   28.232323] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[   28.232331] pci 0000:02:00.0: PME# disabled
[   28.232355] pci 0000:02:00.1: [1033:0035] type 0 class 0x000c03
[   28.232374] pci 0000:02:00.1: reg 10: [mem 0x00000000-0x00000fff]
[   28.232449] pci 0000:02:00.1: supports D1 D2
[   28.232452] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot
[   28.232458] pci 0000:02:00.1: PME# disabled
[   28.232479] pci 0000:02:00.2: [1033:00e0] type 0 class 0x000c03
[   28.232498] pci 0000:02:00.2: reg 10: [mem 0x00000000-0x000000ff]
[   28.232573] pci 0000:02:00.2: supports D1 D2
[   28.232576] pci 0000:02:00.2: PME# supported from D0 D1 D2 D3hot
[   28.232582] pci 0000:02:00.2: PME# disabled
[   28.232613] pci 0000:02:00.0: BAR 0: assigned [mem 0x4c000000-0x4c000fff]
[   28.232622] pci 0000:02:00.0: BAR 0: set to [mem 0x4c000000-0x4c000fff] (PCI address [0x4c000000-0x4c000fff])
[   28.232628] pci 0000:02:00.1: BAR 0: assigned [mem 0x4c001000-0x4c001fff]
[   28.232635] pci 0000:02:00.1: BAR 0: set to [mem 0x4c001000-0x4c001fff] (PCI address [0x4c001000-0x4c001fff])
[   28.232640] pci 0000:02:00.2: BAR 0: assigned [mem 0x4c002000-0x4c0020ff]
[   28.232647] pci 0000:02:00.2: BAR 0: set to [mem 0x4c002000-0x4c0020ff] (PCI address [0x4c002000-0x4c0020ff])
[   28.232901] ohci_hcd 0000:02:00.0: enabling device (0000 -> 0002)
[   28.232923] ohci_hcd 0000:02:00.0: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   28.232966] ohci_hcd 0000:02:00.0: setting latency timer to 64
[   28.232972] ohci_hcd 0000:02:00.0: OHCI Host Controller
[   28.233268] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 4
[   28.233316] ohci_hcd 0000:02:00.0: irq 11, io mem 0x4c000000
[   28.327273] hub 4-0:1.0: USB hub found
[   28.327288] hub 4-0:1.0: 3 ports detected
[   28.327675] ohci_hcd 0000:02:00.1: enabling device (0000 -> 0002)
[   28.327699] ohci_hcd 0000:02:00.1: PCI INT B -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   28.327759] ohci_hcd 0000:02:00.1: setting latency timer to 64
[   28.327767] ohci_hcd 0000:02:00.1: OHCI Host Controller
[   28.327920] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 5
[   28.327962] ohci_hcd 0000:02:00.1: irq 11, io mem 0x4c001000
[   28.375934] ACPI: PCI Interrupt Link [C0CB] enabled at IRQ 11
[   28.375953] snd_ali5451 0000:00:06.0: PCI INT A -> Link[C0CB] -> GSI 11 (level, low) -> IRQ 11
[   28.424386] hub 5-0:1.0: USB hub found
[   28.424412] hub 5-0:1.0: 2 ports detected
[   28.425320] ehci_hcd 0000:02:00.2: enabling device (0000 -> 0002)
[   28.425345] ehci_hcd 0000:02:00.2: PCI INT C -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   28.425408] ehci_hcd 0000:02:00.2: EHCI Host Controller
[   28.427162] ehci_hcd 0000:02:00.2: new USB bus registered, assigned bus number 6
[   28.450103] ehci_hcd 0000:02:00.2: irq 11, io mem 0x4c002000
[   28.460145] ehci_hcd 0000:02:00.2: USB 2.0 started, EHCI 1.00
[   28.460569] hub 6-0:1.0: USB hub found
[   28.460581] hub 6-0:1.0: 5 ports detected
[   28.801246] ppdev: user-space parallel port driver
[   28.986669] [drm] radeon: ring at 0x000000009C001000
[   28.986697] [drm] ring test succeeded in 1 usecs
[   28.987099] [drm] radeon: ib pool ready.
[   28.987249] [drm] ib test succeeded in 0 usecs
[   28.987993] [drm] Panel ID String: 1024x768                
[   28.987997] [drm] Panel Size 1024x768
[   28.999243] [drm] radeon legacy LVDS backlight initialized
[   28.999275] [drm] No TV DAC info found in BIOS
[   28.999436] [drm] Radeon Display Connectors
[   28.999439] [drm] Connector 0:
[   28.999442] [drm]   VGA
[   28.999446] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   28.999449] [drm]   Encoders:
[   28.999453] [drm]     CRT1: INTERNAL_DAC1
[   28.999456] [drm] Connector 1:
[   28.999458] [drm]   LVDS
[   28.999460] [drm]   Encoders:
[   28.999463] [drm]     LCD1: INTERNAL_LVDS
[   28.999466] [drm] Connector 2:
[   28.999468] [drm]   S-video
[   28.999470] [drm]   Encoders:
[   28.999473] [drm]     TV1: INTERNAL_DAC2
[   29.039650] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x207 0x220-0x22f 0x330-0x337 0x370-0x37f 0x388-0x38f
[   29.041964] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding
[   29.042619] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x3e8-0x3ff 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   29.058947] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   29.059762] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: 0x1f0-0x1f7 0x200-0x207 0x220-0x22f 0x330-0x337 0x370-0x37f 0x388-0x38f
[   29.060999] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7 clean.
[   29.109167] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   29.109209] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   29.109254] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   29.109294] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   29.122547] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   29.131028]  clean.
[   29.131125] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   29.154319] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   29.154419] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   29.154459] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
[   29.154501] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   29.171282] cfg80211: World regulatory domain updated:
[   29.171298] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.171303] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.171308] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.171313] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.171317] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.171322] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.186069] [drm] fb mappable at 0x94040000
[   29.186076] [drm] vram apper at 0x94000000
[   29.186079] [drm] size 786432
[   29.186082] [drm] fb depth is 8
[   29.186085] [drm]    pitch is 1024
[   29.186457] fbcon: radeondrmfb (fb0) is primary device
[   29.186946] Console: switching to colour frame buffer device 128x48
[   29.186999] fb0: radeondrmfb frame buffer device
[   29.187003] drm: registered panic notifier
[   29.187028] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   29.411093] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.411103] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411108] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.411113] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411117] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.411122] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411126] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.411131] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411135] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.411140] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411144] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.411149] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411153] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.411158] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411162] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.411167] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411171] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.411176] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411180] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.411185] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411189] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.411194] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.411198] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.411203] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.411207] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.411212] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.411216] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   29.411221] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.434461] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   29.436757] ieee80211 phy0: hwaddr 00:1c:df:38:18:a0, RTL8187BvE V0 + rtl8225z2, rfkill mask 2
[   29.462144] rtl8187: Customer ID is 0x00
[   29.467270] Registered led device: rtl8187-phy0::radio
[   29.469314] Registered led device: rtl8187-phy0::tx
[   29.472669] Registered led device: rtl8187-phy0::rx
[   29.476380] rtl8187: wireless switch is on
[   29.477018] usbcore: registered new interface driver rtl8187
[   32.140242] psmouse serio5: hgpk: ID: 10 00 64
[   33.320050] AC'97 1 does not respond - RESET
[   33.336041] AC'97 1 access is not valid [0xffffffff], removing mixer.
[   33.336058] ali mixer 1 creating error.
[   35.330642] input: PS/2 Generic Mouse as /devices/platform/i8042/serio4/serio5/input/input6
[   39.434877] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   39.655703] init: failsafe main process (754) killed by TERM signal
[   39.863202] Bluetooth: Core ver 2.16
[   39.863275] NET: Registered protocol family 31
[   39.863279] Bluetooth: HCI device and connection manager initialized
[   39.863284] Bluetooth: HCI socket layer initialized
[   39.863288] Bluetooth: L2CAP socket layer initialized
[   39.865171] Bluetooth: SCO socket layer initialized
[   39.918553] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   39.918565] Bluetooth: BNEP filters: protocol multicast
[   39.938059] Bluetooth: RFCOMM TTY layer initialized
[   39.938073] Bluetooth: RFCOMM socket layer initialized
[   39.938076] Bluetooth: RFCOMM ver 1.11
[   40.020732] type=1400 audit(1379624035.151:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=817 comm="apparmor_parser"
[   40.022663] type=1400 audit(1379624035.151:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=817 comm="apparmor_parser"
[   40.196756] type=1400 audit(1379624035.327:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=851 comm="apparmor_parser"
[   40.197425] type=1400 audit(1379624035.327:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=851 comm="apparmor_parser"
[   40.206267] type=1400 audit(1379624035.335:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=852 comm="apparmor_parser"
[   40.217776] type=1400 audit(1379624035.347:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=852 comm="apparmor_parser"
[   40.218263] type=1400 audit(1379624035.347:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=852 comm="apparmor_parser"
[   40.309868] type=1400 audit(1379624035.439:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=853 comm="apparmor_parser"
[   40.321493] type=1400 audit(1379624035.451:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//launchpad_integration" pid=853 comm="apparmor_parser"
[   40.325129] type=1400 audit(1379624035.455:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=853 comm="apparmor_parser"
[   40.994451] init: lxdm main process (924) killed by TERM signal

```

```
Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 21:43:24 Compaq kernel: [    0.033926] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 21:43:24 Compaq kernel: [    1.000104] PM: Hibernation image not present or could not be loaded.
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:23:07 Compaq kernel: [    0.033784] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:23:07 Compaq kernel: [    1.103971] PM: Hibernation image not present or could not be loaded.
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:27:13 Compaq kernel: [    0.033785] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:27:13 Compaq kernel: [    1.101704] PM: Hibernation image not present or could not be loaded.
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:35:48 Compaq kernel: [    0.029788] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:35:48 Compaq kernel: [    1.097048] PM: Hibernation image not present or could not be loaded.
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:37:46 Compaq kernel: [    0.029784] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:37:46 Compaq kernel: [    1.104826] PM: Hibernation image not present or could not be loaded.
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:40:09 Compaq kernel: [    0.029791] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:40:09 Compaq kernel: [    1.101065] PM: Hibernation image not present or could not be loaded.
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:41:27 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:41:27 Compaq kernel: [    1.092148] PM: Hibernation image not present or could not be loaded.
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:47:09 Compaq kernel: [    0.029782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:47:09 Compaq kernel: [    1.103811] PM: Hibernation image not present or could not be loaded.
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 17:46:40 Compaq kernel: [    0.029791] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 17:46:40 Compaq kernel: [    1.099818] PM: Hibernation image not present or could not be loaded.
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 20:10:14 Compaq kernel: [    0.029783] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 20:10:14 Compaq kernel: [    1.097037] PM: Hibernation image not present or could not be loaded.
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 21:58:19 Compaq kernel: [    0.033793] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 21:58:19 Compaq kernel: [    1.101104] PM: Hibernation image not present or could not be loaded.
Sep 18 22:02:48 Compaq kernel: [  295.310964] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 18 22:02:48 Compaq kernel: [  295.310973] PM: Basic memory bitmaps created
Sep 18 22:03:57 Compaq kernel: [  295.310976] PM: Syncing filesystems ... done.
Sep 18 22:03:57 Compaq kernel: [  295.528191] PM: Preallocating image memory... done (allocated 136646 pages)
Sep 18 22:03:57 Compaq kernel: [  295.788864] PM: Allocated 546584 kbytes in 0.26 seconds (2102.24 MB/s)
Sep 18 22:03:57 Compaq kernel: [  296.002283] PM: freeze of drv:sd dev:0:0:0:0 complete after 176.707 msecs
Sep 18 22:03:57 Compaq kernel: [  296.002318] PM: freeze of drv:scsi dev:target0:0:0 complete after 176.625 msecs
Sep 18 22:03:57 Compaq kernel: [  296.002358] PM: freeze of drv:scsi dev:host0 complete after 176.635 msecs
Sep 18 22:03:57 Compaq kernel: [  296.012852] PM: freeze of drv:radeon dev:0000:01:05.0 complete after 181.797 msecs
Sep 18 22:03:57 Compaq kernel: [  296.170751] PM: freeze of drv:tg3 dev:0000:00:13.0 complete after 298.077 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620242] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 1617.932 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620256] PM: freeze of drv: dev:pci0000:00 complete after 1616.766 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620267] PM: freeze of devices complete after 1815.683 msecs
Sep 18 22:03:57 Compaq kernel: [  297.621287] PM: late freeze of devices complete after 1.013 msecs
Sep 18 22:03:57 Compaq kernel: [  297.621931] PM: Saving platform NVS memory
Sep 18 22:03:57 Compaq kernel: [  297.622181] PM: Creating hibernation image:
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Need to copy 93323 pages
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Normal pages needed: 84157 + 1024, available pages: 143037
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Restoring platform NVS memory
Sep 18 22:03:57 Compaq kernel: [  298.432884] PM: early restore of devices complete after 712.531 msecs
Sep 18 22:03:57 Compaq kernel: [  298.779205] PM: restore of drv:tg3 dev:0000:00:13.0 complete after 303.038 msecs
Sep 18 22:03:57 Compaq kernel: [  298.900641] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 424.579 msecs
Sep 18 22:03:57 Compaq kernel: [  298.930423] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 457.279 msecs
Sep 18 22:03:57 Compaq kernel: [  298.933337] PM: restore of drv: dev:platform complete after 460.668 msecs
Sep 18 22:03:57 Compaq kernel: [  299.001898] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 525.762 msecs
Sep 18 22:03:57 Compaq kernel: [  299.061491] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 124.655 msecs
Sep 18 22:03:57 Compaq kernel: [  299.112219] PM: restore of drv:radeon dev:0000:01:05.0 complete after 332.990 msecs
Sep 18 22:03:57 Compaq kernel: [  299.112242] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 175.290 msecs
Sep 18 22:03:57 Compaq kernel: [  299.156388] PM: restore of drv:battery dev:PNP0C0A:00 complete after 222.500 msecs
Sep 18 22:03:57 Compaq kernel: [  299.160370] PM: restore of drv:sd dev:0:0:0:0 complete after 223.843 msecs
Sep 18 22:03:57 Compaq kernel: [  299.160416] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 223.767 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232090] PM: restore of drv:hub dev:3-0:1.0 complete after 296.153 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232104] PM: restore of drv: dev:ep_00 complete after 296.114 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232112] PM: restore of drv: dev:ep_81 complete after 296.151 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244063] PM: restore of drv:hub dev:6-0:1.0 complete after 307.024 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244076] PM: restore of drv: dev:ep_00 complete after 306.984 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244085] PM: restore of drv: dev:ep_81 complete after 307.020 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248059] PM: restore of drv:hub dev:2-0:1.0 complete after 312.235 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248071] PM: restore of drv: dev:ep_00 complete after 312.191 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248079] PM: restore of drv: dev:ep_81 complete after 312.228 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256070] PM: restore of drv:hub dev:4-0:1.0 complete after 319.318 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256083] PM: restore of drv: dev:ep_00 complete after 319.274 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256091] PM: restore of drv: dev:ep_81 complete after 319.310 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296063] PM: restore of drv:hub dev:5-0:1.0 complete after 359.154 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296075] PM: restore of drv: dev:ep_00 complete after 359.153 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296085] PM: restore of drv: dev:ep_81 complete after 359.171 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336059] PM: restore of drv:hub dev:1-0:1.0 complete after 465.313 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336073] PM: restore of drv: dev:ep_00 complete after 400.314 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336104] PM: restore of drv: dev:ep_81 complete after 400.413 msecs
Sep 18 22:03:57 Compaq kernel: [  299.580046] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 1107.232 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599320] PM: restore of drv:usb dev:1-1:1.0 complete after 663.127 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599369] PM: restore of drv: dev:ep_00 complete after 662.897 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599378] PM: restore of drv: dev:ep_83 complete after 663.154 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599387] PM: restore of drv: dev:ep_04 complete after 663.136 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599396] PM: restore of drv: dev:ep_05 complete after 663.119 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599405] PM: restore of drv: dev:ep_06 complete after 663.100 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599413] PM: restore of drv: dev:ep_07 complete after 663.082 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599421] PM: restore of drv: dev:ep_89 complete after 663.062 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599431] PM: restore of drv: dev:ep_0a complete after 663.045 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599439] PM: restore of drv: dev:ep_0b complete after 663.024 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599448] PM: restore of drv: dev:ep_0c complete after 663.005 msecs
Sep 18 22:03:57 Compaq kernel: [  299.728146] PM: restore of devices complete after 1257.420 msecs
Sep 18 22:03:57 Compaq kernel: [  300.016377] PM: Image restored successfully.
Sep 18 22:03:57 Compaq kernel: [  300.046631] PM: Basic memory bitmaps freed
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:07:06 Compaq kernel: [    0.029793] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:07:06 Compaq kernel: [    1.038553] PM: Hibernation image not present or could not be loaded.
Sep 18 22:08:14 Compaq kernel: [   93.892782] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 18 22:08:14 Compaq kernel: [   93.892791] PM: Basic memory bitmaps created
Sep 18 22:09:17 Compaq kernel: [   93.892794] PM: Syncing filesystems ... done.
Sep 18 22:09:17 Compaq kernel: [   94.124175] PM: Preallocating image memory... done (allocated 136646 pages)
Sep 18 22:09:17 Compaq kernel: [   94.388209] PM: Allocated 546584 kbytes in 0.26 seconds (2102.24 MB/s)
Sep 18 22:09:17 Compaq kernel: [   94.702697] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 252.759 msecs
Sep 18 22:09:17 Compaq kernel: [   94.702711] PM: freeze of drv: dev:pci0000:00 complete after 252.547 msecs
Sep 18 22:09:17 Compaq kernel: [   94.702720] PM: freeze of devices complete after 298.170 msecs
Sep 18 22:09:17 Compaq kernel: [   94.703740] PM: late freeze of devices complete after 1.013 msecs
Sep 18 22:09:17 Compaq kernel: [   94.704412] PM: Saving platform NVS memory
Sep 18 22:09:17 Compaq kernel: [   94.704665] PM: Creating hibernation image:
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Need to copy 83329 pages
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Normal pages needed: 74341 + 1024, available pages: 152853
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Restoring platform NVS memory
Sep 18 22:09:17 Compaq kernel: [   95.512881] PM: early restore of devices complete after 712.522 msecs
Sep 18 22:09:17 Compaq kernel: [   95.673584] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 124.482 msecs
Sep 18 22:09:17 Compaq kernel: [   95.703352] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 154.283 msecs
Sep 18 22:09:17 Compaq kernel: [   95.703422] PM: restore of drv: dev:platform complete after 154.833 msecs
Sep 18 22:09:17 Compaq kernel: [   95.783721] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 231.832 msecs
Sep 18 22:09:17 Compaq kernel: [   95.813507] PM: restore of drv:ohci_hcd dev:0000:02:00.0 complete after 108.116 msecs
Sep 18 22:09:17 Compaq kernel: [   95.843282] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 137.735 msecs
Sep 18 22:09:17 Compaq kernel: [   95.894088] PM: restore of drv:radeon dev:0000:01:05.0 complete after 341.921 msecs
Sep 18 22:09:17 Compaq kernel: [   95.894118] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 188.425 msecs
Sep 18 22:09:17 Compaq kernel: [   95.935024] PM: restore of drv:battery dev:PNP0C0A:00 complete after 231.020 msecs
Sep 18 22:09:17 Compaq kernel: [   95.938057] PM: restore of drv:sd dev:0:0:0:0 complete after 232.797 msecs
Sep 18 22:09:17 Compaq kernel: [   95.938097] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 232.735 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012095] PM: restore of drv:hub dev:3-0:1.0 complete after 307.274 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012108] PM: restore of drv: dev:ep_00 complete after 307.233 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012116] PM: restore of drv: dev:ep_81 complete after 307.271 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024063] PM: restore of drv:hub dev:6-0:1.0 complete after 318.251 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024076] PM: restore of drv: dev:ep_00 complete after 318.222 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024084] PM: restore of drv: dev:ep_81 complete after 318.263 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028081] PM: restore of drv:hub dev:2-0:1.0 complete after 384.388 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028096] PM: restore of drv: dev:ep_00 complete after 323.336 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028103] PM: restore of drv: dev:ep_81 complete after 323.421 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036070] PM: restore of drv:hub dev:4-0:1.0 complete after 330.602 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036081] PM: restore of drv: dev:ep_00 complete after 330.562 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036088] PM: restore of drv: dev:ep_81 complete after 330.595 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088065] PM: restore of drv:hub dev:5-0:1.0 complete after 382.452 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088078] PM: restore of drv: dev:ep_00 complete after 382.413 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088086] PM: restore of drv: dev:ep_81 complete after 382.448 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116057] PM: restore of drv:hub dev:1-0:1.0 complete after 472.402 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116072] PM: restore of drv: dev:ep_00 complete after 472.398 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116102] PM: restore of drv: dev:ep_81 complete after 472.438 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391129] PM: restore of drv:usb dev:1-1:1.0 complete after 686.199 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391178] PM: restore of drv: dev:ep_00 complete after 685.974 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391188] PM: restore of drv: dev:ep_83 complete after 686.232 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391196] PM: restore of drv: dev:ep_04 complete after 686.213 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391205] PM: restore of drv: dev:ep_05 complete after 686.193 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391213] PM: restore of drv: dev:ep_06 complete after 686.170 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391223] PM: restore of drv: dev:ep_07 complete after 686.152 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391231] PM: restore of drv: dev:ep_89 complete after 686.134 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391241] PM: restore of drv: dev:ep_0a complete after 686.116 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391249] PM: restore of drv: dev:ep_0b complete after 686.098 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391257] PM: restore of drv: dev:ep_0c complete after 686.080 msecs
Sep 18 22:09:17 Compaq kernel: [   96.392045] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 843.324 msecs
Sep 18 22:09:17 Compaq kernel: [   96.520171] PM: restore of devices complete after 971.924 msecs
Sep 18 22:09:17 Compaq kernel: [   96.828836] PM: Image restored successfully.
Sep 18 22:09:17 Compaq kernel: [   96.903572] PM: Basic memory bitmaps freed
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:22:31 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:22:31 Compaq kernel: [    1.107872] PM: Hibernation image not present or could not be loaded.
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:26:35 Compaq kernel: [    0.033786] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:26:35 Compaq kernel: [    1.100991] PM: Hibernation image not present or could not be loaded.
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:28:57 Compaq kernel: [    0.029787] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:28:57 Compaq kernel: [    1.101105] PM: Hibernation image not present or could not be loaded.
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:48:08 Compaq kernel: [    0.029789] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:48:08 Compaq kernel: [    0.988271] PM: Hibernation image not present or could not be loaded.
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:50:49 Compaq kernel: [    0.040495] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:50:49 Compaq kernel: [    1.087600] PM: Hibernation image not present or could not be loaded.
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:56:49 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:56:49 Compaq kernel: [    1.109377] PM: Hibernation image not present or could not be loaded.
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:58:56 Compaq kernel: [    0.033771] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:58:56 Compaq kernel: [    1.038893] PM: Hibernation image not present or could not be loaded.
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 23:16:03 Compaq kernel: [    0.033781] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 23:16:03 Compaq kernel: [    0.976427] PM: Hibernation image not present or could not be loaded.
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:09:46 Compaq kernel: [    0.029799] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:09:46 Compaq kernel: [    0.968474] PM: Hibernation image not present or could not be loaded.
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:46:50 Compaq kernel: [    0.029787] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:46:50 Compaq kernel: [    0.963342] PM: Hibernation image not present or could not be loaded.
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:50:26 Compaq kernel: [    0.036423] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:50:26 Compaq kernel: [    1.103797] PM: Hibernation image not present or could not be loaded.
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:53:55 Compaq kernel: [    0.033789] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:53:55 Compaq kernel: [    1.107783] PM: Hibernation image not present or could not be loaded.

```[COLOR=#000000]

I've tried hibernating, and it works fine (better than nothing :-))[/COLOR]

---

### Post by Toz on 2013-09-19
Well, the log files reinforce your observations. System suspends but never returns. Hibernation works fine.

There are a few things from your dmesg log that I would like to ask about:
> [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-generic root=UUID=0e519161-7a32-4e2e-915c-7da765feae21 ro noapic nolapic quiet splash vt.handoff=7
...why are you using the "noapic nolapic" boot parameters? Is it for a specific reason? The system has issues with them:
> [    0.032235] Apic disabled
[    0.032237] Local APIC not detected. Using dummy APIC emulation.
[    0.032240] SMP disabled
[    0.032244] Performance Events: 
[    0.032250] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.032253] no hardware sampling interrupt available.
...and:
> [    0.032830] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
...and:
> [    0.032220] weird, boot CPU (#0) not listed by the BIOS.

Have you:
1. Tried without those parameters?
2. Check your bios for an apic setting and try flipping it.

---

### Post by YBGQT4s on 2013-09-20
Hello,

I was using [COLOR=#000000]the "noapic nolapic" boot parameters following a try to solve this issue, according to forums on internet. But no luck it solved nothing and I forgot to remove them. Now they are removed but still resume is hanging :-(

The BIOS has almost no features and nothing related to apic or power saving parameters...again :-(

So let's go for a nex extract of logs:

```
[/COLOR]Initial commandline parameters: Tue Sep 17 23:45:20 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
radeon                733899  2 
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
eeprom_93cx6           12687  1 rtl8187
ttm                    65344  1 radeon
psmouse                96744  0 
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
serio_raw              13027  0 
i2c_ali15x3            12878  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_ali1535            12777  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_algo_bit           13199  1 radeon
video                  19115  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
wmi                    18744  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              14635  1 snd
shpchp                 32265  0 
ati_agp                13242  1 
snd_page_alloc         14115  1 snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     430412     562656          0      44420     264556
-/+ buffers/cache:     121436     871632
Swap:      1013756          0    1013756


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
Tue Sep 17 23:45:25 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 20:13:21 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_seq_midi           13132  0 
eeprom_93cx6           12687  1 rtl8187
i2c_ali15x3            12878  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia                 39826  0 
psmouse                96744  0 
serio_raw              13027  0 
i2c_ali1535            12777  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  19115  0 
i2c_algo_bit           13199  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  0 
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
mac_hid                13077  0 
shpchp                 32265  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     543988     449080          0      44540     327996
-/+ buffers/cache:     171452     821616
Swap:      1013756          0    1013756


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
Wed Sep 18 20:13:26 CEST 2013: performing suspend
Initial commandline parameters: 
mercredi 18 septembre 2013, 22:02:44 (UTC+0200): Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
snd_seq_midi           13132  0 
rtl8187                56323  0 
snd_rawmidi            25424  1 snd_seq_midi
mac80211              436493  1 rtl8187
ttm                    65344  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         45466  1 radeon
cfg80211              178877  2 rtl8187,mac80211
drm                   197641  4 radeon,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
i2c_algo_bit           13199  1 radeon
eeprom_93cx6           12687  1 rtl8187
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96744  0 
i2c_ali15x3            12878  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
shpchp                 32265  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  1 snd_pcm
i2c_ali1535            12777  0 
ati_agp                13242  1 
video                  19115  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     565528     427540          0      48316     341260
-/+ buffers/cache:     175952     817116
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:


/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:


/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:


/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
mercredi 18 septembre 2013, 22:02:47 (UTC+0200): performing hibernate
mercredi 18 septembre 2013, 22:03:57 (UTC+0200): Awake.
mercredi 18 septembre 2013, 22:03:57 (UTC+0200): Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
mercredi 18 septembre 2013, 22:04:06 (UTC+0200): Finished.
Initial commandline parameters: 
Wed Sep 18 22:08:08 CEST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
ttm                    65344  1 radeon
eeprom_93cx6           12687  1 rtl8187
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
psmouse                96744  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
i2c_ali15x3            12878  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
video                  19115  0 
rfcomm                 38139  0 
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia                 39826  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
wmi                    18744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32265  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     532512     460556          0      44284     326112
-/+ buffers/cache:     162116     830952
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
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


/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Wed Sep 18 22:08:13 CEST 2013: performing hibernate
Wed Sep 18 22:09:17 CEST 2013: Awake.
Wed Sep 18 22:09:17 CEST 2013: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Wed Sep 18 22:09:20 CEST 2013: Finished.
Initial commandline parameters: 
Wed Sep 18 22:20:51 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
btrfs                 638340  0 
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
reiserfs              230928  0 
ext2                   67987  0 
arc4                   12473  0 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
ttm                    65344  1 radeon
eeprom_93cx6           12687  1 rtl8187
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
psmouse                96744  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
i2c_ali15x3            12878  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
video                  19115  0 
rfcomm                 38139  0 
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia                 39826  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
wmi                    18744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32265  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     554004     439064          0      19880     320928
-/+ buffers/cache:     213196     779872
Swap:      1013756        128    1013628


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
Wed Sep 18 22:20:53 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 22:27:34 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12687  1 rtl8187
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197641  4 radeon,ttm,drm_kms_helper
serio_raw              13027  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_ali1535            12777  0 
soundcore              14635  1 snd
i2c_algo_bit           13199  1 radeon
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
ppdev                  12849  0 
bluetooth             158447  10 rfcomm,bnep
video                  19115  0 
wmi                    18744  0 
shpchp                 32265  0 
ati_agp                13242  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     543060     450008          0      44260     324912
-/+ buffers/cache:     173888     819180
Swap:      1013756          0    1013756


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
Wed Sep 18 22:27:37 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 22:49:20 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
radeon                733899  2 
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12687  1 rtl8187
ttm                    65344  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
psmouse                96744  0 
pcmcia                 39826  0 
drm_kms_helper         45466  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197641  4 radeon,ttm,drm_kms_helper
serio_raw              13027  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali1535            12777  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13199  1 radeon
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
video                  19115  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
wmi                    18744  0 
shpchp                 32265  0 
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     531496     461572          0      44240     323988
-/+ buffers/cache:     163268     829800
Swap:      1013756          0    1013756


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
Wed Sep 18 22:49:24 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 23:14:09 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
btrfs                 638340  0 
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
reiserfs              230928  0 
ext2                   67987  0 
arc4                   12473  2 
joydev                 17393  0 
snd_ali5451            23459  2 
rtl8187                56323  0 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
mac80211              436493  1 rtl8187
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
eeprom_93cx6           12687  1 rtl8187
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
i2c_algo_bit           13199  1 radeon
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
i2c_ali15x3            12878  0 
soundcore              14635  1 snd
shpchp                 32265  0 
ati_agp                13242  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_ali1535            12777  0 
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
video                  19115  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     508908     484160          0      47024     347212
-/+ buffers/cache:     114672     878396
Swap:      1013756          0    1013756


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
Wed Sep 18 23:14:13 CEST 2013: performing suspend
Initial commandline parameters: 
Thu Sep 19 22:51:55 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_ali5451            23459  2 
eeprom_93cx6           12687  1 rtl8187
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
psmouse                96744  0 
snd_seq_midi           13132  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
i2c_ali15x3            12878  0 
video                  19115  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_ali1535            12777  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 radeon
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
wmi                    18744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
ati_agp                13242  1 
snd_page_alloc         14115  1 snd_pcm
shpchp                 32265  0 
mac_hid                13077  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     557940     435128          0      44356     329460
-/+ buffers/cache:     184124     808944
Swap:      1013756          0    1013756


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
Thu Sep 19 22:51:59 CEST 2013: performing suspend
Initial commandline parameters: 
Thu Sep 19 23:32:52 CEST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
arc4                   12473  2 
joydev                 17393  0 
ppdev                  12849  0 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_seq_midi           13132  0 
radeon                733899  2 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
eeprom_93cx6           12687  1 rtl8187
ttm                    65344  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                96744  0 
serio_raw              13027  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
soundcore              14635  1 snd
pcmcia_rsrc            18367  1 yenta_socket
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32114  1 
snd_page_alloc         14115  1 snd_pcm
shpchp                 32265  0 
video                  19115  0 
wmi                    18744  0 
ati_agp                13242  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     725204     267864          0     133752     365128
-/+ buffers/cache:     226324     766744
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
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
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Thu Sep 19 23:32:55 CEST 2013: performing hibernate
Fri Sep 20 11:35:25 CEST 2013: Awake.
Fri Sep 20 11:35:25 CEST 2013: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Fri Sep 20 11:35:29 CEST 2013: Finished.
Initial commandline parameters: 
Fri Sep 20 11:41:10 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
eeprom_93cx6           12687  1 rtl8187
psmouse                96744  0 
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
i2c_ali15x3            12878  0 
serio_raw              13027  0 
i2c_ali1535            12777  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
video                  19115  0 
drm_kms_helper         45466  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia                 39826  0 
parport_pc             32114  1 
bnep                   17830  2 
rfcomm                 38139  0 
ppdev                  12849  0 
bluetooth             158447  10 bnep,rfcomm
i2c_algo_bit           13199  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
wmi                    18744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
ati_agp                13242  1 
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     394240     598828          0      43704     247428
-/+ buffers/cache:     103108     889960
Swap:      1013756          0    1013756


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
Fri Sep 20 11:41:14 CEST 2013: performing suspend
Initial commandline parameters: 
Fri Sep 20 11:49:44 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                96744  0 
i2c_ali15x3            12878  0 
serio_raw              13027  0 
ttm                    65344  1 radeon
i2c_ali1535            12777  0 
drm_kms_helper         45466  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 radeon
video                  19115  0 
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  1 
bluetooth             158447  10 bnep,rfcomm
ppdev                  12849  0 
wmi                    18744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
shpchp                 32265  0 
snd_page_alloc         14115  1 snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
ati_agp                13242  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        960684     368128     592556          0      43008     226908
-/+ buffers/cache:      98212     862472
Swap:      1013756          0    1013756


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
Fri Sep 20 11:49:48 CEST 2013: performing suspend
```


```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-53-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 (Ubuntu 3.2.0-53.81-generic 3.2.50)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bfd0000 (usable)
[    0.000000]  BIOS-e820: 000000003bfd0000 - 000000003bff0c00 (reserved)
[    0.000000]  BIOS-e820: 000000003bff0c00 - 000000003bffc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bffc000 - 000000003c000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: Hewlett-Packard HP Compaq nc4010 (DY886AA#ABF)  /0834, BIOS 68BAS Ver. F.30 08/30/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3bfd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bf8000-1c00000
[    0.000000] RAMDISK: 364e0000 - 37268000
[    0.000000] ACPI: RSDP 000f7840 00014 (v00 COMPAQ)
[    0.000000] ACPI: RSDT 3bff0c84 0002C (v01 COMPAQ CPQ005A  30080620 CPQ  00000001)
[    0.000000] ACPI: FACP 3bff0c00 00084 (v02 COMPAQ CPQ005A  00000002 CPQ  00000001)
[    0.000000] ACPI: DSDT 3bff0cb0 0607E (v01 COMPAQ  EVON800 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3bffbe80 00040
[    0.000000] ACPI: SSDT 3bff6d2e 002A7 (v01 COMPAQ  CPQGysr 00001001 MSFT 0100000E)
[    0.000000] 71MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003bfd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bfd0
[    0.000000] On node 0 totalpages: 245599
[    0.000000] free_area_init_node: node 0, pgdat c182bd40, node_mem_map f5d60200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 144 pages used for memmap
[    0.000000]   HighMem zone: 18242 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3c000000 (gap: 3c000000:c4000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77ea000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243679
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-generic root=UUID=0e519161-7a32-4e2e-915c-7da765feae21 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3931136 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003bfd0)
[    0.000000] Memory: 946088k/982848k available (5636k kernel code, 36308k reserved, 2780k data, 716k init, 73544k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1839000 - 0xc18ec000   ( 716 kB)
[    0.000000]       .data : 0xc1581284 - 0xc1838480   (2780 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1581284   (5636 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1492.545 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2985.09 BogoMIPS (lpj=5970180)
[    0.008013] pid_max: default: 32768 minimum: 301
[    0.008054] Security Framework initialized
[    0.008104] AppArmor: AppArmor initialized
[    0.008107] Yama: becoming mindful.
[    0.008223] Mount-cache hash table entries: 512
[    0.008504] Initializing cgroup subsys cpuacct
[    0.008516] Initializing cgroup subsys memory
[    0.008533] Initializing cgroup subsys devices
[    0.008538] Initializing cgroup subsys freezer
[    0.008542] Initializing cgroup subsys blkio
[    0.008557] Initializing cgroup subsys perf_event
[    0.008618] mce: CPU supports 5 MCE banks
[    0.009083] SMP alternatives: switching to UP code
[    0.022225] Freeing SMP alternatives: 24k freed
[    0.022241] ACPI: Core revision 20110623
[    0.026873] ACPI: setting ELCR to 0200 (from 0c00)
[    0.028091] ftrace: allocating 25519 entries in 50 pages
[    0.032218] weird, boot CPU (#0) not listed by the BIOS.
[    0.032229] SMP motherboard not detected.
[    0.032233] Local APIC not detected. Using dummy APIC emulation.
[    0.032236] SMP disabled
[    0.032240] Performance Events: 
[    0.032245] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.032248] no hardware sampling interrupt available.
[    0.032255] p6 PMU driver.
[    0.032265] ... version:                0
[    0.032268] ... bit width:              32
[    0.032270] ... generic registers:      2
[    0.032273] ... value mask:             00000000ffffffff
[    0.032276] ... max period:             000000007fffffff
[    0.032279] ... fixed-purpose events:   0
[    0.032281] ... event mask:             0000000000000003
[    0.032823] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[    0.032931] Brought up 1 CPUs
[    0.032936] Total of 1 processors activated (2985.09 BogoMIPS).
[    0.033415] devtmpfs: initialized
[    0.033688] EVM: security.selinux
[    0.033691] EVM: security.SMACK64
[    0.033693] EVM: security.capability
[    0.033779] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
[    0.033818] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.038052] print_constraints: dummy: 
[    0.038115] RTC time:  9:53:57, date: 09/20/13
[    0.038206] NET: Registered protocol family 16
[    0.038454] EISA bus registered
[    0.038528] ACPI: bus type pci registered
[    0.041364] PCI: PCI BIOS revision 2.10 entry at 0xf031f, last bus=1
[    0.041367] PCI: Using configuration type 1 for base access
[    0.043567] bio: create slab <bio-0> at 0
[    0.043744] ACPI: Added _OSI(Module Device)
[    0.043748] ACPI: Added _OSI(Processor Device)
[    0.043752] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.043756] ACPI: Added _OSI(Processor Aggregator Device)
[    0.045271] ACPI: EC: Look up EC in DSDT
[    0.064095] ACPI: Interpreter enabled
[    0.064121] ACPI: (supports S0 S3 S4 S5)
[    0.064151] ACPI: Using PIC for interrupt routing
[    0.068339] ACPI: Power Resource [C15A] (on)
[    0.069465] ACPI: Power Resource [C15F] (on)
[    0.070615] ACPI: Power Resource [C169] (on)
[    0.071488] ACPI: Power Resource [C17A] (on)
[    0.075822] ACPI: Power Resource [C1F2] (off)
[    0.075906] ACPI: Power Resource [C1F3] (off)
[    0.076012] ACPI: Power Resource [C1F4] (off)
[    0.076103] ACPI: Power Resource [C1F5] (off)
[    0.076822] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.077058] ACPI: No dock devices found.
[    0.077061] HEST: Table not found.
[    0.077073] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.081418] ACPI: PCI Root Bridge [C044] (domain 0000 [bus 00-ff])
[    0.090069] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.090074] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.090079] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.090083] pci_root PNP0A03:00: host bridge window [mem 0x3c000000-0xffffffff] (ignored)
[    0.090088] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.090112] pci 0000:00:00.0: [1002:cbb2] type 0 class 0x000600
[    0.090127] pci 0000:00:00.0: reg 10: [mem 0xa4000000-0xa7ffffff pref]
[    0.090134] pci 0000:00:00.0: reg 14: [mem 0xa0480000-0xa0480fff pref]
[    0.090192] pci 0000:00:01.0: [1002:7010] type 1 class 0x000604
[    0.090231] pci 0000:00:06.0: [10b9:5451] type 0 class 0x000401
[    0.090245] pci 0000:00:06.0: reg 10: [io  0x3000-0x30ff]
[    0.090254] pci 0000:00:06.0: reg 14: [mem 0xa0080000-0xa0080fff]
[    0.090302] pci 0000:00:06.0: supports D1 D2
[    0.090307] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.090313] pci 0000:00:06.0: PME# disabled
[    0.090332] pci 0000:00:07.0: [10b9:1533] type 0 class 0x000601
[    0.090416] pci 0000:00:08.0: [10b9:5457] type 0 class 0x000703
[    0.090430] pci 0000:00:08.0: reg 10: [mem 0xa0100000-0xa0100fff]
[    0.090439] pci 0000:00:08.0: reg 14: [io  0x3400-0x34ff]
[    0.090485] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.090490] pci 0000:00:08.0: PME# disabled
[    0.090513] pci 0000:00:0b.0: [1217:7114] type 2 class 0x000607
[    0.090528] pci 0000:00:0b.0: reg 10: [mem 0xa0180000-0xa0180fff]
[    0.090551] pci 0000:00:0b.0: supports D1 D2
[    0.090555] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090560] pci 0000:00:0b.0: PME# disabled
[    0.090578] pci 0000:00:0b.1: [1217:7114] type 2 class 0x000607
[    0.090593] pci 0000:00:0b.1: reg 10: [mem 0xa0200000-0xa0200fff]
[    0.090616] pci 0000:00:0b.1: supports D1 D2
[    0.090620] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090625] pci 0000:00:0b.1: PME# disabled
[    0.090643] pci 0000:00:0b.2: [1217:7110] type 0 class 0x000880
[    0.090658] pci 0000:00:0b.2: reg 10: [mem 0xa0280000-0xa0280fff]
[    0.090715] pci 0000:00:0b.2: supports D1 D2
[    0.090719] pci 0000:00:0b.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090724] pci 0000:00:0b.2: PME# disabled
[    0.090749] pci 0000:00:10.0: [10b9:5229] type 0 class 0x000101
[    0.090784] pci 0000:00:10.0: reg 20: [io  0x3800-0x380f]
[    0.090827] pci 0000:00:11.0: [10b9:7101] type 0 class 0x000680
[    0.090884] pci 0000:00:11.0: quirk: [io  0x1000-0x103f] claimed by ali7101 ACPI
[    0.090889] pci 0000:00:11.0: quirk: [io  0x1100-0x111f] claimed by ali7101 SMB
[    0.090909] pci 0000:00:12.0: [1033:0035] type 0 class 0x000c03
[    0.090923] pci 0000:00:12.0: reg 10: [mem 0xa0300000-0xa0300fff]
[    0.090975] pci 0000:00:12.0: supports D1 D2
[    0.090979] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090984] pci 0000:00:12.0: PME# disabled
[    0.091001] pci 0000:00:12.1: [1033:0035] type 0 class 0x000c03
[    0.091015] pci 0000:00:12.1: reg 10: [mem 0xa0380000-0xa0380fff]
[    0.091067] pci 0000:00:12.1: supports D1 D2
[    0.091071] pci 0000:00:12.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091076] pci 0000:00:12.1: PME# disabled
[    0.091093] pci 0000:00:12.2: [1033:00e0] type 0 class 0x000c03
[    0.091107] pci 0000:00:12.2: reg 10: [mem 0xa0400000-0xa04000ff]
[    0.091160] pci 0000:00:12.2: supports D1 D2
[    0.091163] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091168] pci 0000:00:12.2: PME# disabled
[    0.091197] pci 0000:00:13.0: [14e4:165d] type 0 class 0x000200
[    0.091220] pci 0000:00:13.0: reg 10: [mem 0xa0000000-0xa000ffff 64bit]
[    0.091256] pci 0000:00:13.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.091297] pci 0000:00:13.0: PME# supported from D3hot D3cold
[    0.091302] pci 0000:00:13.0: PME# disabled
[    0.091351] pci 0000:01:05.0: [1002:4337] type 0 class 0x000300
[    0.091366] pci 0000:01:05.0: reg 10: [mem 0x98000000-0x9fffffff pref]
[    0.091375] pci 0000:01:05.0: reg 14: [io  0x2000-0x20ff]
[    0.091384] pci 0000:01:05.0: reg 18: [mem 0x90000000-0x9000ffff]
[    0.091408] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.091435] pci 0000:01:05.0: supports D1 D2
[    0.091465] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.091472] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.091478] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x900fffff]
[    0.091484] pci 0000:00:01.0:   bridge window [mem 0x98000000-0x9fffffff pref]
[    0.091545] pci_bus 0000:00: on NUMA node 0
[    0.091552] ACPI: PCI Interrupt Routing Table [\_SB_.C044._PRT]
[    0.091661] ACPI: PCI Interrupt Routing Table [\_SB_.C044.C045._PRT]
[    0.091744]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.104720] ACPI: PCI Interrupt Link [C0C4] (IRQs 5 *10 11)
[    0.104822] ACPI: PCI Interrupt Link [C0C5] (IRQs 5 *10 11)
[    0.104920] ACPI: PCI Interrupt Link [C0C6] (IRQs 5 10 *11)
[    0.104999] ACPI: PCI Interrupt Link [C0C7] (IRQs 5 10 11) *0, disabled.
[    0.105097] ACPI: PCI Interrupt Link [C0C8] (IRQs 5 *10 11)
[    0.105175] ACPI: PCI Interrupt Link [C0C9] (IRQs 5 10 11) *0, disabled.
[    0.105273] ACPI: PCI Interrupt Link [C0CA] (IRQs 5 10 *11)
[    0.105370] ACPI: PCI Interrupt Link [C0CB] (IRQs 5 10 *11)
[    0.105608] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.105613] vgaarb: loaded
[    0.105615] vgaarb: bridge control possible 0000:01:05.0
[    0.105835] i2c-core: driver [aat2870] using legacy suspend method
[    0.105839] i2c-core: driver [aat2870] using legacy resume method
[    0.106038] SCSI subsystem initialized
[    0.106169] libata version 3.00 loaded.
[    0.106274] usbcore: registered new interface driver usbfs
[    0.106307] usbcore: registered new interface driver hub
[    0.106354] usbcore: registered new device driver usb
[    0.106532] PCI: Using ACPI for IRQ routing
[    0.106539] PCI: pci_cache_line_size set to 64 bytes
[    0.106609] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.106615] reserve RAM buffer: 000000003bfd0000 - 000000003bffffff 
[    0.106842] NetLabel: Initializing
[    0.106845] NetLabel:  domain hash size = 128
[    0.106848] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.106873] NetLabel:  unlabeled traffic allowed by default
[    0.106987] Switching to clocksource pit
[    0.122492] AppArmor: AppArmor Filesystem Enabled
[    0.122625] pnp: PnP ACPI init
[    0.122675] ACPI: bus type pnp registered
[    0.122968] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.122975] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.122979] pnp 00:00: [mem 0x00100000-0x3bffffff]
[    0.123120] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.123127] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.123132] system 00:00: [mem 0x00100000-0x3bffffff] could not be reserved
[    0.123141] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.127557] pnp 00:01: [bus 00-ff]
[    0.127562] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.127567] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.127571] pnp 00:01: [io  0x0d00-0xffff window]
[    0.127575] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.127579] pnp 00:01: [mem 0x3c000000-0xffffffff window]
[    0.127583] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.127761] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.128856] pnp 00:02: [io  0x03f8-0x03ff]
[    0.128866] pnp 00:02: [irq 4]
[    0.128966] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
[    0.130123] pnp 00:03: [io  0x03e8-0x03ef]
[    0.130128] pnp 00:03: [irq 3]
[    0.130132] pnp 00:03: [dma 3]
[    0.130237] pnp 00:03: Plug and Play ACPI device, IDs ALI5123 PNP0510 (active)
[    0.131425] pnp 00:04: [io  0x0378-0x037f]
[    0.131430] pnp 00:04: [io  0x0778-0x077a]
[    0.131434] pnp 00:04: [irq 7]
[    0.131437] pnp 00:04: [dma 1]
[    0.131610] pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.131698] pnp 00:05: [io  0x00f0-0x00ff]
[    0.131703] pnp 00:05: [irq 13]
[    0.131751] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.131770] pnp 00:06: [io  0x0000-0x000f]
[    0.131774] pnp 00:06: [io  0x0080-0x008f]
[    0.131778] pnp 00:06: [io  0x00c0-0x00df]
[    0.131781] pnp 00:06: [dma 4]
[    0.131829] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.131844] pnp 00:07: [io  0x0061]
[    0.131897] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.131913] pnp 00:08: [io  0x0070-0x0071]
[    0.131917] pnp 00:08: [io  0x0072-0x0073]
[    0.131920] pnp 00:08: [irq 8]
[    0.131977] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.131993] pnp 00:09: [io  0x0060]
[    0.131997] pnp 00:09: [io  0x0064]
[    0.132000] pnp 00:09: [irq 1]
[    0.132049] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.132064] pnp 00:0a: [irq 12]
[    0.132122] pnp 00:0a: Plug and Play ACPI device, IDs SYN0102 SYN0100 SYN0002 PNP0f13 (active)
[    0.132273] pnp 00:0b: [io  0x002e-0x002f]
[    0.132276] pnp 00:0b: [io  0x004e-0x004f]
[    0.132280] pnp 00:0b: [io  0x0063]
[    0.132283] pnp 00:0b: [io  0x0065]
[    0.132287] pnp 00:0b: [io  0x0067-0x006f]
[    0.132290] pnp 00:0b: [io  0x0074-0x007f]
[    0.132293] pnp 00:0b: [io  0x0092]
[    0.132297] pnp 00:0b: [io  0x00b0-0x00b3]
[    0.132300] pnp 00:0b: [io  0x0370-0x0371]
[    0.132304] pnp 00:0b: [io  0x040b]
[    0.132307] pnp 00:0b: [io  0x0480-0x048f]
[    0.132310] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.132314] pnp 00:0b: [io  0x04d6]
[    0.132317] pnp 00:0b: [io  0x1400-0x141f]
[    0.132321] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.132325] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.132431] system 00:0b: [io  0x0370-0x0371] has been reserved
[    0.132436] system 00:0b: [io  0x040b] has been reserved
[    0.132440] system 00:0b: [io  0x0480-0x048f] has been reserved
[    0.132445] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.132449] system 00:0b: [io  0x04d6] has been reserved
[    0.132454] system 00:0b: [io  0x1400-0x141f] has been reserved
[    0.132459] system 00:0b: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.132464] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.132469] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.133898] pnp 00:0c: [io  0x1000-0x107f]
[    0.133902] pnp 00:0c: [io  0x1100-0x111f]
[    0.133906] pnp 00:0c: [mem 0xa0480000-0xa0480fff]
[    0.134004] system 00:0c: [io  0x1000-0x107f] could not be reserved
[    0.134009] system 00:0c: [io  0x1100-0x111f] has been reserved
[    0.134014] system 00:0c: [mem 0xa0480000-0xa0480fff] has been reserved
[    0.134019] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.134644] pnp 00:0d: [mem 0x000cf000-0x000cffff]
[    0.134735] system 00:0d: [mem 0x000cf000-0x000cffff] has been reserved
[    0.134741] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.134766] pnp: PnP ACPI: found 14 devices
[    0.134769] ACPI: ACPI bus type pnp unregistered
[    0.134779] PnPBIOS: Disabled by ACPI PNP
[    0.172747] Switching to clocksource acpi_pm
[    0.172809] PCI: max bus depth: 1 pci_try_num: 2
[    0.172858] pci 0000:00:13.0: BAR 6: assigned [mem 0x3c000000-0x3c00ffff pref]
[    0.172866] pci 0000:00:0b.1: BAR 16: assigned [mem 0x40000000-0x43ffffff]
[    0.172871] pci 0000:00:0b.1: BAR 15: assigned [mem 0x44000000-0x47ffffff pref]
[    0.172877] pci 0000:00:0b.1: BAR 14: assigned [io  0x1800-0x18ff]
[    0.172883] pci 0000:00:0b.1: BAR 13: assigned [io  0x1c00-0x1cff]
[    0.172888] pci 0000:00:0b.0: BAR 16: assigned [mem 0x48000000-0x4bffffff]
[    0.172893] pci 0000:00:0b.0: BAR 15: assigned [mem 0x4c000000-0x4fffffff pref]
[    0.172899] pci 0000:00:0b.0: BAR 14: assigned [io  0x3c00-0x3cff]
[    0.172904] pci 0000:00:0b.0: BAR 13: assigned [io  0x4000-0x40ff]
[    0.172910] pci 0000:01:05.0: BAR 6: assigned [mem 0x90020000-0x9003ffff pref]
[    0.172916] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.172922] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.172928] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x900fffff]
[    0.172933] pci 0000:00:01.0:   bridge window [mem 0x98000000-0x9fffffff pref]
[    0.172941] pci 0000:00:0b.0: CardBus bridge to [bus 02-05]
[    0.172945] pci 0000:00:0b.0:   bridge window [io  0x4000-0x40ff]
[    0.172950] pci 0000:00:0b.0:   bridge window [io  0x3c00-0x3cff]
[    0.172956] pci 0000:00:0b.0:   bridge window [mem 0x4c000000-0x4fffffff pref]
[    0.172962] pci 0000:00:0b.0:   bridge window [mem 0x48000000-0x4bffffff]
[    0.172968] pci 0000:00:0b.1: CardBus bridge to [bus 06-09]
[    0.172971] pci 0000:00:0b.1:   bridge window [io  0x1c00-0x1cff]
[    0.172977] pci 0000:00:0b.1:   bridge window [io  0x1800-0x18ff]
[    0.172982] pci 0000:00:0b.1:   bridge window [mem 0x44000000-0x47ffffff pref]
[    0.172988] pci 0000:00:0b.1:   bridge window [mem 0x40000000-0x43ffffff]
[    0.173345] ACPI: PCI Interrupt Link [C0C6] enabled at IRQ 11
[    0.173352] PCI: setting IRQ 11 as level-triggered
[    0.173360] pci 0000:00:0b.0: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[    0.173372] pci 0000:00:0b.1: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[    0.173380] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.173385] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.173390] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.173394] pci_bus 0000:01: resource 1 [mem 0x90000000-0x900fffff]
[    0.173398] pci_bus 0000:01: resource 2 [mem 0x98000000-0x9fffffff pref]
[    0.173403] pci_bus 0000:02: resource 0 [io  0x4000-0x40ff]
[    0.173407] pci_bus 0000:02: resource 1 [io  0x3c00-0x3cff]
[    0.173411] pci_bus 0000:02: resource 2 [mem 0x4c000000-0x4fffffff pref]
[    0.173415] pci_bus 0000:02: resource 3 [mem 0x48000000-0x4bffffff]
[    0.173420] pci_bus 0000:06: resource 0 [io  0x1c00-0x1cff]
[    0.173424] pci_bus 0000:06: resource 1 [io  0x1800-0x18ff]
[    0.173428] pci_bus 0000:06: resource 2 [mem 0x44000000-0x47ffffff pref]
[    0.173432] pci_bus 0000:06: resource 3 [mem 0x40000000-0x43ffffff]
[    0.173548] NET: Registered protocol family 2
[    0.173698] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.174276] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.177519] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.179510] TCP: Hash tables configured (established 131072 bind 65536)
[    0.179518] TCP reno registered
[    0.179530] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.179592] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.179966] NET: Registered protocol family 1
[    0.180134] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    0.180555] ACPI: PCI Interrupt Link [C0C5] enabled at IRQ 10
[    0.180564] PCI: setting IRQ 10 as level-triggered
[    0.180573] pci 0000:00:12.0: PCI INT A -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.180623] pci 0000:00:12.0: PCI INT A disabled
[    0.180643] pci 0000:00:12.1: PCI INT B -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.180654] pci 0000:00:12.1: PCI INT B disabled
[    0.180667] pci 0000:00:12.2: PCI INT C -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.180682] pci 0000:00:12.2: PCI INT C disabled
[    0.180694] pci 0000:01:05.0: Boot video device
[    0.180699] PCI: CLS 64 bytes, default 64
[    0.181627] audit: initializing netlink socket (disabled)
[    0.181657] type=2000 audit(1379670837.176:1): initialized
[    0.216389] Trying to unpack rootfs image as initramfs...
[    0.257265] highmem bounce pool size: 64 pages
[    0.257282] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.268657] VFS: Disk quotas dquot_6.5.2
[    0.268816] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.269989] fuse init (API version 7.17)
[    0.270169] msgmni has been set to 1704
[    0.280879] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.284169] io scheduler noop registered
[    0.284177] io scheduler deadline registered
[    0.284221] io scheduler cfq registered (default)
[    0.284576] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.284614] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.286750] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.286936] ACPI: AC Adapter [C137] (on-line)
[    0.287111] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.287127] ACPI: Sleep Button [C13B]
[    0.287213] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.287290] ACPI: Lid Switch [C13A]
[    0.287374] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.287380] ACPI: Power Button [PWRF]
[    0.287529] ACPI: Fan [C1F6] (off)
[    0.287611] ACPI: Fan [C1F7] (off)
[    0.287687] ACPI: Fan [C1F8] (off)
[    0.287766] ACPI: Fan [C1F9] (off)
[    0.287809] ACPI: Invalid PBLK length [7]
[    0.287898] Marking TSC unstable due to TSC halts in idle
[    0.287916] ACPI: acpi_idle registered with cpuidle
[    0.307181] thermal LNXTHERM:00: registered as thermal_zone0
[    0.307190] ACPI: Thermal Zone [TZ1] (52 C)
[    0.311080] thermal LNXTHERM:01: registered as thermal_zone1
[    0.311084] ACPI: Thermal Zone [TZ2] (39 C)
[    0.325984] thermal LNXTHERM:02: registered as thermal_zone2
[    0.325992] ACPI: Thermal Zone [TZ3] (24 C)
[    0.326133] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.326158] ACPI: Battery Slot [C139] (battery present)
[    0.326183] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.326193] ACPI: Battery Slot [C138] (battery absent)
[    0.326246] ERST: Table is not found!
[    0.326249] GHES: HEST is not enabled!
[    0.326621] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.347246] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.353257] ACPI: Battery Slot [C138] (battery absent)
[    0.353327] isapnp: Scanning for PnP cards...
[    0.440076] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.465801] ACPI: Battery Slot [C139] (battery present)
[    0.490867] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.557039] ACPI: PCI Interrupt Link [C0CA] enabled at IRQ 11
[    0.557057] serial 0000:00:08.0: PCI INT A -> Link[C0CA] -> GSI 11 (level, low) -> IRQ 11
[    0.557086] serial 0000:00:08.0: PCI INT A disabled
[    0.557477] Linux agpgart interface v0.103
[    0.566155] brd: module loaded
[    0.567544] loop: module loaded
[    0.568392] ACPI: PCI Interrupt Link [C0C4] enabled at IRQ 10
[    0.568406] pata_acpi 0000:00:10.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[    0.568527] pata_acpi 0000:00:10.0: PCI INT A disabled
[    0.569202] Fixed MDIO Bus: probed
[    0.569241] tun: Universal TUN/TAP device driver, 1.6
[    0.569244] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.569371] PPP generic driver version 2.4.2
[    0.572551] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.572617] ehci_hcd 0000:00:12.2: PCI INT C -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.572658] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.572768] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.635874] ehci_hcd 0000:00:12.2: irq 10, io mem 0xa0400000
[    0.728100] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.728576] hub 1-0:1.0: USB hub found
[    0.728588] hub 1-0:1.0: 5 ports detected
[    0.728787] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.728855] ohci_hcd 0000:00:12.0: PCI INT A -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.728899] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.729016] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 2
[    0.729060] ohci_hcd 0000:00:12.0: irq 10, io mem 0xa0300000
[    0.844779] hub 2-0:1.0: USB hub found
[    0.844797] hub 2-0:1.0: 3 ports detected
[    0.844977] ohci_hcd 0000:00:12.1: PCI INT B -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.845026] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.845141] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 3
[    0.845197] ohci_hcd 0000:00:12.1: irq 10, io mem 0xa0380000
[    0.956577] hub 3-0:1.0: USB hub found
[    0.956595] hub 3-0:1.0: 2 ports detected
[    0.956771] uhci_hcd: USB Universal Host Controller Interface driver
[    0.956979] usbcore: registered new interface driver libusual
[    0.957097] i8042: PNP: PS/2 Controller [PNP0303:C177,PNP0f13:C178] at 0x60,0x64 irq 1,12
[    0.958785] i8042: Detected active multiplexing controller, rev 1.1
[    0.959495] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.959519] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.964253] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.964367] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.964420] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.964690] mousedev: PS/2 mouse device common for all mice
[    0.965039] rtc_cmos 00:08: RTC can wake from S4
[    0.965289] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    0.965331] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    0.965528] device-mapper: uevent: version 1.0.3
[    0.965666] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.965731] EISA: Probing bus 0 at eisa.0
[    0.965748] Cannot allocate resource for EISA slot 1
[    0.965753] Cannot allocate resource for EISA slot 2
[    0.965756] Cannot allocate resource for EISA slot 3
[    0.965761] Cannot allocate resource for EISA slot 4
[    0.965784] EISA: Detected 0 cards.
[    0.965812] cpufreq-nforce2: No nForce2 chipset.
[    0.965889] cpuidle: using governor ladder
[    0.965996] cpuidle: using governor menu
[    0.966000] EFI Variables Facility v0.08 2004-May-17
[    0.966486] TCP cubic registered
[    0.966730] NET: Registered protocol family 10
[    0.967761] NET: Registered protocol family 17
[    0.967771] Registering the dns_resolver key type
[    0.967823] Using IPI No-Shortcut mode
[    0.971446] PM: Hibernation image not present or could not be loaded.
[    0.971485] registered taskstats version 1
[    1.023835] isapnp: No Plug & Play device found
[    1.064344] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.080392] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.299751] Freeing initrd memory: 13856k freed
[    1.366233]   Magic number: 13:812:879
[    1.366590] rtc_cmos 00:08: setting system clock to 2013-09-20 09:53:59 UTC (1379670839)
[    1.367697] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.367704] EDD information not available.
[    1.368410] Freeing unused kernel memory: 716k freed
[    1.369212] Write protecting the kernel text: 5640k
[    1.369271] Write protecting the kernel read-only data: 2332k
[    1.400448] udevd[81]: starting version 175
[    1.629342] pata_ali 0000:00:10.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[    1.647966] scsi0 : pata_ali
[    1.652153] scsi1 : pata_ali
[    1.652800] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x3800 irq 14
[    1.652807] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3808 irq 15
[    1.764995] tg3.c:v3.121 (November 2, 2011)
[    1.765358] ACPI: PCI Interrupt Link [C0C8] enabled at IRQ 10
[    1.765371] tg3 0000:00:13.0: PCI INT A -> Link[C0C8] -> GSI 10 (level, low) -> IRQ 10
[    1.816535] ata1.00: ATA-6: Hitachi IC25N040ATMR04-0, MO2AAD0A, max UDMA/100
[    1.816544] ata1.00: 78140160 sectors, multi 16: LBA48 
[    1.852511] ata1.00: configured for UDMA/100
[    1.852849] scsi 0:0:0:0: Direct-Access     ATA      Hitachi IC25N040 MO2A PQ: 0 ANSI: 5
[    1.853227] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.853309] sd 0:0:0:0: [sda] Write Protect is off
[    1.853314] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.853348] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.853916] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.865068] tg3 0000:00:13.0: eth0: Tigon3 [partno(BCM5705mA1) rev 3003] (PCI:33MHz:32-bit) MAC address 00:0d:9d:8e:45:25
[    1.865078] tg3 0000:00:13.0: eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0], EEE[0])
[    1.865084] tg3 0000:00:13.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.865089] tg3 0000:00:13.0: eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    1.907491]  sda: sda1 sda2 < sda5 >
[    1.908266] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.423382] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   25.143340] Adding 1013756k swap on /dev/sda5.  Priority:-1 extents:1 across:1013756k 
[   25.168268] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.229436] udevd[319]: starting version 175
[   25.358045] lp: driver loaded but no devices found
[   25.519306] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   25.777759] agpgart-ati 0000:00:00.0: Ati IGP345M chipset
[   25.834562] wmi: Mapper loaded
[   26.161880] Bluetooth: Core ver 2.16
[   26.164135] NET: Registered protocol family 31
[   26.164142] Bluetooth: HCI device and connection manager initialized
[   26.164149] Bluetooth: HCI socket layer initialized
[   26.164153] Bluetooth: L2CAP socket layer initialized
[   26.164169] Bluetooth: SCO socket layer initialized
[   26.166832] ppdev: user-space parallel port driver
[   26.174200] parport_pc 00:04: reported by Plug and Play ACPI
[   26.174278] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   26.185935] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xa4000000
[   26.211631] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.211639] Bluetooth: BNEP filters: protocol multicast
[   26.227729] Bluetooth: RFCOMM TTY layer initialized
[   26.227747] Bluetooth: RFCOMM socket layer initialized
[   26.227750] Bluetooth: RFCOMM ver 1.11
[   26.292546] lp0: using parport0 (interrupt-driven).
[   26.296859] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.308557] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input4
[   26.315363] ACPI: Video Device [C046] (multi-head: yes  rom: no  post: no)
[   26.346437] type=1400 audit(1379670864.476:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=571 comm="apparmor_parser"
[   26.347481] type=1400 audit(1379670864.476:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=571 comm="apparmor_parser"
[   26.468645] yenta_cardbus 0000:00:0b.0: CardBus bridge found [0e11:005a]
[   26.468672] yenta_cardbus 0000:00:0b.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   26.549537] [drm] Initialized drm 1.1.0 20060810
[   26.596643] yenta_cardbus 0000:00:0b.0: ISA IRQ mask 0x0038, PCI irq 11
[   26.596651] yenta_cardbus 0000:00:0b.0: Socket status: 30000820
[   26.617728] yenta_cardbus 0000:00:0b.1: CardBus bridge found [0e11:005a]
[   26.742543] type=1400 audit(1379670864.872:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=620 comm="apparmor_parser"
[   26.744929] type=1400 audit(1379670864.876:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=620 comm="apparmor_parser"
[   26.745414] type=1400 audit(1379670864.876:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=620 comm="apparmor_parser"
[   26.746725] yenta_cardbus 0000:00:0b.1: ISA IRQ mask 0x0038, PCI irq 11
[   26.746731] yenta_cardbus 0000:00:0b.1: Socket status: 30000006
[   26.762241] ACPI: resource ali1535_smbus [io  0x1100-0x111f] conflicts with ACPI region C092 [io 0x1100-0x1107]
[   26.762249] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   26.762256] ali1535_smbus 0000:00:11.0: ALI1535 not detected, module not inserted.
[   26.765632] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   26.765643] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   26.810355] cfg80211: Calling CRDA to update world regulatory domain
[   26.868428] type=1400 audit(1379670865.000:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=624 comm="apparmor_parser"
[   27.165741] [drm] radeon defaulting to kernel modesetting.
[   27.165749] [drm] radeon kernel modesetting enabled.
[   27.165942] radeon 0000:01:05.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[   27.170632] [drm] initializing kernel modesetting (RS200 0x1002:0x4337 0x0E11:0x005A).
[   27.170680] [drm] register mmio base: 0x90000000
[   27.170683] [drm] register mmio size: 65536
[   27.171156] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   27.171182] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   27.171245] radeon 0000:01:05.0: putting AGP V2 device into 4x mode
[   27.171252] radeon 0000:01:05.0: GTT: 64M 0xA4000000 - 0xA7FFFFFF
[   27.171264] radeon 0000:01:05.0: VRAM: 64M 0x000000003C000000 - 0x000000003FFFFFFF (64M used)
[   27.190420] [drm] Detected VRAM RAM=64M, BAR=128M
[   27.190429] [drm] RAM width 64bits DDR
[   27.205382] [TTM] Zone  kernel: Available graphics memory: 443570 kiB.
[   27.205390] [TTM] Zone highmem: Available graphics memory: 480342 kiB.
[   27.205394] [TTM] Initializing pool allocator.
[   27.205465] [drm] radeon: 64M of VRAM memory ready
[   27.205469] [drm] radeon: 64M of GTT memory ready.
[   27.292764] radeon 0000:01:05.0: WB disabled
[   27.292778] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   27.292781] [drm] Driver supports precise vblank timestamp query.
[   27.292817] [drm] radeon: irq initialized.
[   27.310247] [drm] Loading R100 Microcode
[   27.436639] psmouse serio4: synaptics: Touchpad model: 1, fw: 5.9, id: 0x1b6eb1, caps: 0xa84793/0x100000/0x0
[   27.436659] psmouse serio4: synaptics: serio: Synaptics pass-through port at isa0060/serio4/input0
[   27.482808] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   27.487696] init: failsafe main process (688) killed by TERM signal
[   27.500147] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   27.500185] pci 0000:02:00.0: [1033:0035] type 0 class 0x000c03
[   27.500214] pci 0000:02:00.0: reg 10: [mem 0x00000000-0x00000fff]
[   27.500300] pci 0000:02:00.0: supports D1 D2
[   27.500304] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[   27.500312] pci 0000:02:00.0: PME# disabled
[   27.500360] pci 0000:02:00.1: [1033:0035] type 0 class 0x000c03
[   27.500379] pci 0000:02:00.1: reg 10: [mem 0x00000000-0x00000fff]
[   27.500454] pci 0000:02:00.1: supports D1 D2
[   27.500458] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot
[   27.500464] pci 0000:02:00.1: PME# disabled
[   27.500485] pci 0000:02:00.2: [1033:00e0] type 0 class 0x000c03
[   27.500504] pci 0000:02:00.2: reg 10: [mem 0x00000000-0x000000ff]
[   27.500579] pci 0000:02:00.2: supports D1 D2
[   27.500582] pci 0000:02:00.2: PME# supported from D0 D1 D2 D3hot
[   27.500588] pci 0000:02:00.2: PME# disabled
[   27.500619] pci 0000:02:00.0: BAR 0: assigned [mem 0x48000000-0x48000fff]
[   27.500629] pci 0000:02:00.0: BAR 0: set to [mem 0x48000000-0x48000fff] (PCI address [0x48000000-0x48000fff])
[   27.500634] pci 0000:02:00.1: BAR 0: assigned [mem 0x48001000-0x48001fff]
[   27.500641] pci 0000:02:00.1: BAR 0: set to [mem 0x48001000-0x48001fff] (PCI address [0x48001000-0x48001fff])
[   27.500647] pci 0000:02:00.2: BAR 0: assigned [mem 0x48002000-0x480020ff]
[   27.500654] pci 0000:02:00.2: BAR 0: set to [mem 0x48002000-0x480020ff] (PCI address [0x48002000-0x480020ff])
[   27.500876] ohci_hcd 0000:02:00.0: enabling device (0000 -> 0002)
[   27.500898] ohci_hcd 0000:02:00.0: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   27.500946] ohci_hcd 0000:02:00.0: setting latency timer to 64
[   27.500951] ohci_hcd 0000:02:00.0: OHCI Host Controller
[   27.501255] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 4
[   27.501302] ohci_hcd 0000:02:00.0: irq 11, io mem 0x48000000
[   27.612630] hub 4-0:1.0: USB hub found
[   27.612646] hub 4-0:1.0: 3 ports detected
[   27.613030] ohci_hcd 0000:02:00.1: enabling device (0000 -> 0002)
[   27.613055] ohci_hcd 0000:02:00.1: PCI INT B -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   27.613110] ohci_hcd 0000:02:00.1: setting latency timer to 64
[   27.613117] ohci_hcd 0000:02:00.1: OHCI Host Controller
[   27.615123] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 5
[   27.615175] ohci_hcd 0000:02:00.1: irq 11, io mem 0x48001000
[   27.699567] hub 5-0:1.0: USB hub found
[   27.699585] hub 5-0:1.0: 2 ports detected
[   27.699965] ehci_hcd 0000:02:00.2: enabling device (0000 -> 0002)
[   27.699990] ehci_hcd 0000:02:00.2: PCI INT C -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   27.702172] ehci_hcd 0000:02:00.2: EHCI Host Controller
[   27.702842] ehci_hcd 0000:02:00.2: new USB bus registered, assigned bus number 6
[   27.724429] ehci_hcd 0000:02:00.2: irq 11, io mem 0x48002000
[   27.736919] ehci_hcd 0000:02:00.2: USB 2.0 started, EHCI 1.00
[   27.737549] hub 6-0:1.0: USB hub found
[   27.737561] hub 6-0:1.0: 5 ports detected
[   27.852676] ACPI: PCI Interrupt Link [C0CB] enabled at IRQ 11
[   27.852694] snd_ali5451 0000:00:06.0: PCI INT A -> Link[C0CB] -> GSI 11 (level, low) -> IRQ 11
[   27.963107] type=1400 audit(1379670866.092:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=796 comm="apparmor_parser"
[   27.963777] type=1400 audit(1379670866.092:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=796 comm="apparmor_parser"
[   27.980505] type=1400 audit(1379670866.112:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=798 comm="apparmor_parser"
[   27.986263] type=1400 audit(1379670866.116:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=798 comm="apparmor_parser"
[   28.601803] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x207 0x220-0x22f
[   28.609332] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x330-0x337 0x370-0x37f 0x388-0x38f
[   28.627205] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x408-0x40f
[   28.639723] [drm] radeon: ring at 0x00000000A4001000
[   28.639754] [drm] ring test succeeded in 1 usecs
[   28.641144] [drm] radeon: ib pool ready.
[   28.641307] [drm] ib test succeeded in 0 usecs
[   28.645978] [drm] Panel ID String: 1024x768                
[   28.645985] [drm] Panel Size 1024x768
[   28.657876] [drm] radeon legacy LVDS backlight initialized
[   28.658267] [drm] No TV DAC info found in BIOS
[   28.659774] [drm] Radeon Display Connectors
[   28.659781] [drm] Connector 0:
[   28.659784] [drm]   VGA
[   28.659789] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   28.659793] [drm]   Encoders:
[   28.659797] [drm]     CRT1: INTERNAL_DAC1
[   28.659799] [drm] Connector 1:
[   28.659801] [drm]   LVDS
[   28.659804] [drm]   Encoders:
[   28.659807] [drm]     LCD1: INTERNAL_LVDS
[   28.659809] [drm] Connector 2:
[   28.659812] [drm]   S-video
[   28.659814] [drm]   Encoders:
[   28.659816] [drm]     TV1: INTERNAL_DAC2
[   28.730775]  0x1f0-0x1f7 0x200-0x207 0x220-0x22f 0x480-0x48f 0x4d0-0x4d7
[   28.819117] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   28.823684] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: 0x330-0x337 0x370-0x37f 0x388-0x38f
[   28.830343] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   28.896295] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   28.905661] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   28.905703] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa04fffff
[   28.905775] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   28.905816] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   28.926057] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7:
[   28.975699] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   28.975709] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975714] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   28.975719] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975723] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   28.975728] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975732] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   28.975737] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975741] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   28.975746] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975750] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   28.975755] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975759] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   28.975764] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975768] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   28.975773] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975777] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   28.975782] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975786] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   28.975791] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975795] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   28.975800] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975804] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   28.975809] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975813] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   28.975818] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   28.975822] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   28.975827] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   28.994356] init: alsa-restore main process (899) terminated with status 19
[   29.036772] [drm] fb mappable at 0x98040000
[   29.036781] [drm] vram apper at 0x98000000
[   29.036785] [drm] size 3145728
[   29.036788] [drm] fb depth is 24
[   29.036790] [drm]    pitch is 4096
[   29.047764]  clean.
[   29.058863] fbcon: radeondrmfb (fb0) is primary device
[   29.061357]  clean.
[   29.061464] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   29.061503] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa04fffff
[   29.061546] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
[   29.061586] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff:
[   29.091544] Console: switching to colour frame buffer device 128x48
[   29.091613] fb0: radeondrmfb frame buffer device
[   29.091618] drm: registered panic notifier
[   29.091644] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   29.119538]  clean.
[   29.624478] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.624488] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624493] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.624498] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624502] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.624507] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624511] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.624516] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624520] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.624525] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624529] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.624534] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624538] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.624543] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624547] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.624552] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624556] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.624561] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624565] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.624570] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624574] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.624579] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624583] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.624588] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.624592] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.624597] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.624601] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   29.624606] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.624613] cfg80211: World regulatory domain updated:
[   29.624617] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.624622] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624626] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.624631] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.624635] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.624639] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

```
Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 21:43:24 Compaq kernel: [    0.033926] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 21:43:24 Compaq kernel: [    1.000104] PM: Hibernation image not present or could not be loaded.
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:23:07 Compaq kernel: [    0.033784] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:23:07 Compaq kernel: [    1.103971] PM: Hibernation image not present or could not be loaded.
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:27:13 Compaq kernel: [    0.033785] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:27:13 Compaq kernel: [    1.101704] PM: Hibernation image not present or could not be loaded.
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:35:48 Compaq kernel: [    0.029788] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:35:48 Compaq kernel: [    1.097048] PM: Hibernation image not present or could not be loaded.
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:37:46 Compaq kernel: [    0.029784] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:37:46 Compaq kernel: [    1.104826] PM: Hibernation image not present or could not be loaded.
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:40:09 Compaq kernel: [    0.029791] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:40:09 Compaq kernel: [    1.101065] PM: Hibernation image not present or could not be loaded.
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:41:27 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:41:27 Compaq kernel: [    1.092148] PM: Hibernation image not present or could not be loaded.
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:47:09 Compaq kernel: [    0.029782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:47:09 Compaq kernel: [    1.103811] PM: Hibernation image not present or could not be loaded.
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 17:46:40 Compaq kernel: [    0.029791] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 17:46:40 Compaq kernel: [    1.099818] PM: Hibernation image not present or could not be loaded.
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 20:10:14 Compaq kernel: [    0.029783] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 20:10:14 Compaq kernel: [    1.097037] PM: Hibernation image not present or could not be loaded.
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 21:58:19 Compaq kernel: [    0.033793] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 21:58:19 Compaq kernel: [    1.101104] PM: Hibernation image not present or could not be loaded.
Sep 18 22:02:48 Compaq kernel: [  295.310964] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 18 22:02:48 Compaq kernel: [  295.310973] PM: Basic memory bitmaps created
Sep 18 22:03:57 Compaq kernel: [  295.310976] PM: Syncing filesystems ... done.
Sep 18 22:03:57 Compaq kernel: [  295.528191] PM: Preallocating image memory... done (allocated 136646 pages)
Sep 18 22:03:57 Compaq kernel: [  295.788864] PM: Allocated 546584 kbytes in 0.26 seconds (2102.24 MB/s)
Sep 18 22:03:57 Compaq kernel: [  296.002283] PM: freeze of drv:sd dev:0:0:0:0 complete after 176.707 msecs
Sep 18 22:03:57 Compaq kernel: [  296.002318] PM: freeze of drv:scsi dev:target0:0:0 complete after 176.625 msecs
Sep 18 22:03:57 Compaq kernel: [  296.002358] PM: freeze of drv:scsi dev:host0 complete after 176.635 msecs
Sep 18 22:03:57 Compaq kernel: [  296.012852] PM: freeze of drv:radeon dev:0000:01:05.0 complete after 181.797 msecs
Sep 18 22:03:57 Compaq kernel: [  296.170751] PM: freeze of drv:tg3 dev:0000:00:13.0 complete after 298.077 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620242] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 1617.932 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620256] PM: freeze of drv: dev:pci0000:00 complete after 1616.766 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620267] PM: freeze of devices complete after 1815.683 msecs
Sep 18 22:03:57 Compaq kernel: [  297.621287] PM: late freeze of devices complete after 1.013 msecs
Sep 18 22:03:57 Compaq kernel: [  297.621931] PM: Saving platform NVS memory
Sep 18 22:03:57 Compaq kernel: [  297.622181] PM: Creating hibernation image:
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Need to copy 93323 pages
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Normal pages needed: 84157 + 1024, available pages: 143037
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Restoring platform NVS memory
Sep 18 22:03:57 Compaq kernel: [  298.432884] PM: early restore of devices complete after 712.531 msecs
Sep 18 22:03:57 Compaq kernel: [  298.779205] PM: restore of drv:tg3 dev:0000:00:13.0 complete after 303.038 msecs
Sep 18 22:03:57 Compaq kernel: [  298.900641] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 424.579 msecs
Sep 18 22:03:57 Compaq kernel: [  298.930423] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 457.279 msecs
Sep 18 22:03:57 Compaq kernel: [  298.933337] PM: restore of drv: dev:platform complete after 460.668 msecs
Sep 18 22:03:57 Compaq kernel: [  299.001898] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 525.762 msecs
Sep 18 22:03:57 Compaq kernel: [  299.061491] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 124.655 msecs
Sep 18 22:03:57 Compaq kernel: [  299.112219] PM: restore of drv:radeon dev:0000:01:05.0 complete after 332.990 msecs
Sep 18 22:03:57 Compaq kernel: [  299.112242] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 175.290 msecs
Sep 18 22:03:57 Compaq kernel: [  299.156388] PM: restore of drv:battery dev:PNP0C0A:00 complete after 222.500 msecs
Sep 18 22:03:57 Compaq kernel: [  299.160370] PM: restore of drv:sd dev:0:0:0:0 complete after 223.843 msecs
Sep 18 22:03:57 Compaq kernel: [  299.160416] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 223.767 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232090] PM: restore of drv:hub dev:3-0:1.0 complete after 296.153 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232104] PM: restore of drv: dev:ep_00 complete after 296.114 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232112] PM: restore of drv: dev:ep_81 complete after 296.151 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244063] PM: restore of drv:hub dev:6-0:1.0 complete after 307.024 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244076] PM: restore of drv: dev:ep_00 complete after 306.984 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244085] PM: restore of drv: dev:ep_81 complete after 307.020 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248059] PM: restore of drv:hub dev:2-0:1.0 complete after 312.235 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248071] PM: restore of drv: dev:ep_00 complete after 312.191 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248079] PM: restore of drv: dev:ep_81 complete after 312.228 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256070] PM: restore of drv:hub dev:4-0:1.0 complete after 319.318 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256083] PM: restore of drv: dev:ep_00 complete after 319.274 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256091] PM: restore of drv: dev:ep_81 complete after 319.310 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296063] PM: restore of drv:hub dev:5-0:1.0 complete after 359.154 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296075] PM: restore of drv: dev:ep_00 complete after 359.153 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296085] PM: restore of drv: dev:ep_81 complete after 359.171 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336059] PM: restore of drv:hub dev:1-0:1.0 complete after 465.313 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336073] PM: restore of drv: dev:ep_00 complete after 400.314 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336104] PM: restore of drv: dev:ep_81 complete after 400.413 msecs
Sep 18 22:03:57 Compaq kernel: [  299.580046] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 1107.232 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599320] PM: restore of drv:usb dev:1-1:1.0 complete after 663.127 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599369] PM: restore of drv: dev:ep_00 complete after 662.897 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599378] PM: restore of drv: dev:ep_83 complete after 663.154 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599387] PM: restore of drv: dev:ep_04 complete after 663.136 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599396] PM: restore of drv: dev:ep_05 complete after 663.119 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599405] PM: restore of drv: dev:ep_06 complete after 663.100 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599413] PM: restore of drv: dev:ep_07 complete after 663.082 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599421] PM: restore of drv: dev:ep_89 complete after 663.062 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599431] PM: restore of drv: dev:ep_0a complete after 663.045 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599439] PM: restore of drv: dev:ep_0b complete after 663.024 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599448] PM: restore of drv: dev:ep_0c complete after 663.005 msecs
Sep 18 22:03:57 Compaq kernel: [  299.728146] PM: restore of devices complete after 1257.420 msecs
Sep 18 22:03:57 Compaq kernel: [  300.016377] PM: Image restored successfully.
Sep 18 22:03:57 Compaq kernel: [  300.046631] PM: Basic memory bitmaps freed
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:07:06 Compaq kernel: [    0.029793] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:07:06 Compaq kernel: [    1.038553] PM: Hibernation image not present or could not be loaded.
Sep 18 22:08:14 Compaq kernel: [   93.892782] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 18 22:08:14 Compaq kernel: [   93.892791] PM: Basic memory bitmaps created
Sep 18 22:09:17 Compaq kernel: [   93.892794] PM: Syncing filesystems ... done.
Sep 18 22:09:17 Compaq kernel: [   94.124175] PM: Preallocating image memory... done (allocated 136646 pages)
Sep 18 22:09:17 Compaq kernel: [   94.388209] PM: Allocated 546584 kbytes in 0.26 seconds (2102.24 MB/s)
Sep 18 22:09:17 Compaq kernel: [   94.702697] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 252.759 msecs
Sep 18 22:09:17 Compaq kernel: [   94.702711] PM: freeze of drv: dev:pci0000:00 complete after 252.547 msecs
Sep 18 22:09:17 Compaq kernel: [   94.702720] PM: freeze of devices complete after 298.170 msecs
Sep 18 22:09:17 Compaq kernel: [   94.703740] PM: late freeze of devices complete after 1.013 msecs
Sep 18 22:09:17 Compaq kernel: [   94.704412] PM: Saving platform NVS memory
Sep 18 22:09:17 Compaq kernel: [   94.704665] PM: Creating hibernation image:
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Need to copy 83329 pages
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Normal pages needed: 74341 + 1024, available pages: 152853
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Restoring platform NVS memory
Sep 18 22:09:17 Compaq kernel: [   95.512881] PM: early restore of devices complete after 712.522 msecs
Sep 18 22:09:17 Compaq kernel: [   95.673584] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 124.482 msecs
Sep 18 22:09:17 Compaq kernel: [   95.703352] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 154.283 msecs
Sep 18 22:09:17 Compaq kernel: [   95.703422] PM: restore of drv: dev:platform complete after 154.833 msecs
Sep 18 22:09:17 Compaq kernel: [   95.783721] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 231.832 msecs
Sep 18 22:09:17 Compaq kernel: [   95.813507] PM: restore of drv:ohci_hcd dev:0000:02:00.0 complete after 108.116 msecs
Sep 18 22:09:17 Compaq kernel: [   95.843282] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 137.735 msecs
Sep 18 22:09:17 Compaq kernel: [   95.894088] PM: restore of drv:radeon dev:0000:01:05.0 complete after 341.921 msecs
Sep 18 22:09:17 Compaq kernel: [   95.894118] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 188.425 msecs
Sep 18 22:09:17 Compaq kernel: [   95.935024] PM: restore of drv:battery dev:PNP0C0A:00 complete after 231.020 msecs
Sep 18 22:09:17 Compaq kernel: [   95.938057] PM: restore of drv:sd dev:0:0:0:0 complete after 232.797 msecs
Sep 18 22:09:17 Compaq kernel: [   95.938097] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 232.735 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012095] PM: restore of drv:hub dev:3-0:1.0 complete after 307.274 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012108] PM: restore of drv: dev:ep_00 complete after 307.233 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012116] PM: restore of drv: dev:ep_81 complete after 307.271 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024063] PM: restore of drv:hub dev:6-0:1.0 complete after 318.251 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024076] PM: restore of drv: dev:ep_00 complete after 318.222 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024084] PM: restore of drv: dev:ep_81 complete after 318.263 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028081] PM: restore of drv:hub dev:2-0:1.0 complete after 384.388 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028096] PM: restore of drv: dev:ep_00 complete after 323.336 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028103] PM: restore of drv: dev:ep_81 complete after 323.421 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036070] PM: restore of drv:hub dev:4-0:1.0 complete after 330.602 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036081] PM: restore of drv: dev:ep_00 complete after 330.562 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036088] PM: restore of drv: dev:ep_81 complete after 330.595 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088065] PM: restore of drv:hub dev:5-0:1.0 complete after 382.452 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088078] PM: restore of drv: dev:ep_00 complete after 382.413 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088086] PM: restore of drv: dev:ep_81 complete after 382.448 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116057] PM: restore of drv:hub dev:1-0:1.0 complete after 472.402 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116072] PM: restore of drv: dev:ep_00 complete after 472.398 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116102] PM: restore of drv: dev:ep_81 complete after 472.438 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391129] PM: restore of drv:usb dev:1-1:1.0 complete after 686.199 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391178] PM: restore of drv: dev:ep_00 complete after 685.974 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391188] PM: restore of drv: dev:ep_83 complete after 686.232 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391196] PM: restore of drv: dev:ep_04 complete after 686.213 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391205] PM: restore of drv: dev:ep_05 complete after 686.193 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391213] PM: restore of drv: dev:ep_06 complete after 686.170 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391223] PM: restore of drv: dev:ep_07 complete after 686.152 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391231] PM: restore of drv: dev:ep_89 complete after 686.134 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391241] PM: restore of drv: dev:ep_0a complete after 686.116 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391249] PM: restore of drv: dev:ep_0b complete after 686.098 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391257] PM: restore of drv: dev:ep_0c complete after 686.080 msecs
Sep 18 22:09:17 Compaq kernel: [   96.392045] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 843.324 msecs
Sep 18 22:09:17 Compaq kernel: [   96.520171] PM: restore of devices complete after 971.924 msecs
Sep 18 22:09:17 Compaq kernel: [   96.828836] PM: Image restored successfully.
Sep 18 22:09:17 Compaq kernel: [   96.903572] PM: Basic memory bitmaps freed
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:22:31 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:22:31 Compaq kernel: [    1.107872] PM: Hibernation image not present or could not be loaded.
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:26:35 Compaq kernel: [    0.033786] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:26:35 Compaq kernel: [    1.100991] PM: Hibernation image not present or could not be loaded.
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:28:57 Compaq kernel: [    0.029787] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:28:57 Compaq kernel: [    1.101105] PM: Hibernation image not present or could not be loaded.
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:48:08 Compaq kernel: [    0.029789] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:48:08 Compaq kernel: [    0.988271] PM: Hibernation image not present or could not be loaded.
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:50:49 Compaq kernel: [    0.040495] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:50:49 Compaq kernel: [    1.087600] PM: Hibernation image not present or could not be loaded.
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:56:49 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:56:49 Compaq kernel: [    1.109377] PM: Hibernation image not present or could not be loaded.
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:58:56 Compaq kernel: [    0.033771] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:58:56 Compaq kernel: [    1.038893] PM: Hibernation image not present or could not be loaded.
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 23:16:03 Compaq kernel: [    0.033781] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 23:16:03 Compaq kernel: [    0.976427] PM: Hibernation image not present or could not be loaded.
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:09:46 Compaq kernel: [    0.029799] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:09:46 Compaq kernel: [    0.968474] PM: Hibernation image not present or could not be loaded.
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:46:50 Compaq kernel: [    0.029787] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:46:50 Compaq kernel: [    0.963342] PM: Hibernation image not present or could not be loaded.
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:50:26 Compaq kernel: [    0.036423] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:50:26 Compaq kernel: [    1.103797] PM: Hibernation image not present or could not be loaded.
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:53:55 Compaq kernel: [    0.033789] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:53:55 Compaq kernel: [    1.107783] PM: Hibernation image not present or could not be loaded.
Sep 19 23:32:56 Compaq kernel: [ 2381.224499] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 19 23:32:56 Compaq kernel: [ 2381.224508] PM: Basic memory bitmaps created
Sep 20 11:35:25 Compaq kernel: [ 2381.224512] PM: Syncing filesystems ... done.
Sep 20 11:35:25 Compaq kernel: [ 2381.520178] PM: Preallocating image memory... done (allocated 136638 pages)
Sep 20 11:35:25 Compaq kernel: [ 2381.918437] PM: Allocated 546552 kbytes in 0.39 seconds (1401.41 MB/s)
Sep 20 11:35:25 Compaq kernel: [ 2382.201635] PM: freeze of drv:sd dev:0:0:0:0 complete after 268.586 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.201656] PM: freeze of drv:scsi dev:target0:0:0 complete after 268.590 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.201675] PM: freeze of drv:scsi dev:host0 complete after 263.757 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.201806] PM: freeze of drv:pata_ali dev:0000:00:10.0 complete after 223.181 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.227499] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 248.926 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.227511] PM: freeze of drv: dev:pci0000:00 complete after 245.532 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.227519] PM: freeze of devices complete after 294.801 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.228567] PM: late freeze of devices complete after 1.041 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.229225] PM: Saving platform NVS memory
Sep 20 11:35:25 Compaq kernel: [ 2382.229477] PM: Creating hibernation image:
Sep 20 11:35:25 Compaq kernel: [ 2382.232016] PM: Need to copy 96476 pages
Sep 20 11:35:25 Compaq kernel: [ 2382.232016] PM: Normal pages needed: 90695 + 1024, available pages: 136499
Sep 20 11:35:25 Compaq kernel: [ 2382.232016] PM: Restoring platform NVS memory
Sep 20 11:35:25 Compaq kernel: [ 2383.036851] PM: early restore of devices complete after 712.489 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.203951] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 124.240 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.233735] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 154.306 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.238068] PM: restore of drv: dev:platform complete after 159.160 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.312113] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 229.671 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.362918] PM: restore of drv:radeon dev:0000:01:05.0 complete after 280.392 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.401739] PM: restore of drv:battery dev:PNP0C0A:00 complete after 163.061 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.475888] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 112.167 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.496078] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 132.208 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504109] PM: restore of drv:hub dev:2-0:1.0 complete after 330.054 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504124] PM: restore of drv: dev:ep_00 complete after 265.089 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504133] PM: restore of drv:hub dev:3-0:1.0 complete after 191.890 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504147] PM: restore of drv: dev:ep_00 complete after 141.124 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504157] PM: restore of drv: dev:ep_81 complete after 266.273 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504165] PM: restore of drv: dev:ep_81 complete after 141.150 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.552264] PM: restore of drv:usb dev:4-0:1.0 complete after 188.632 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.552273] PM: restore of drv: dev:ep_00 complete after 188.582 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.552282] PM: restore of drv: dev:ep_81 complete after 188.621 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.564063] PM: restore of drv:hub dev:5-0:1.0 complete after 200.272 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.564076] PM: restore of drv: dev:ep_00 complete after 200.233 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.564086] PM: restore of drv: dev:ep_81 complete after 200.270 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.600069] PM: restore of drv:hub dev:1-0:1.0 complete after 426.051 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.600083] PM: restore of drv: dev:ep_00 complete after 426.048 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.600117] PM: restore of drv: dev:ep_81 complete after 426.091 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.628084] PM: restore of drv:hub dev:6-0:1.0 complete after 264.135 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.628096] PM: restore of drv: dev:ep_00 complete after 264.092 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.628106] PM: restore of drv: dev:ep_81 complete after 264.129 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875126] PM: restore of drv:usb dev:1-1:1.0 complete after 512.040 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875176] PM: restore of drv: dev:ep_00 complete after 511.784 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875185] PM: restore of drv: dev:ep_83 complete after 512.073 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875194] PM: restore of drv: dev:ep_04 complete after 512.030 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875203] PM: restore of drv: dev:ep_05 complete after 512.011 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875213] PM: restore of drv: dev:ep_06 complete after 511.992 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875221] PM: restore of drv: dev:ep_07 complete after 511.972 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875230] PM: restore of drv: dev:ep_89 complete after 511.950 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875239] PM: restore of drv: dev:ep_0a complete after 511.928 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875248] PM: restore of drv: dev:ep_0b complete after 511.909 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875257] PM: restore of drv: dev:ep_0c complete after 511.892 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.920044] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 840.957 msecs
Sep 20 11:35:25 Compaq kernel: [ 2384.004161] PM: restore of devices complete after 925.625 msecs
Sep 20 11:35:25 Compaq kernel: [ 2384.312813] PM: Image restored successfully.
Sep 20 11:35:25 Compaq kernel: [ 2384.373344] PM: Basic memory bitmaps freed
Sep 20 11:40:01 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:40:01 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:40:01 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:40:01 Compaq kernel: [    0.029790] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 20 11:40:01 Compaq kernel: [    1.104490] PM: Hibernation image not present or could not be loaded.
Sep 20 11:43:05 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:43:05 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:43:05 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:43:05 Compaq kernel: [    0.029788] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 20 11:43:05 Compaq kernel: [    1.101016] PM: Hibernation image not present or could not be loaded.
Sep 20 11:45:16 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:45:16 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:45:16 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:45:16 Compaq kernel: [    0.040539] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 20 11:45:16 Compaq kernel: [    1.108628] PM: Hibernation image not present or could not be loaded.
Sep 20 11:49:15 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:49:15 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:49:15 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:49:15 Compaq kernel: [    0.033784] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 11:49:15 Compaq kernel: [    1.115872] PM: Hibernation image not present or could not be loaded.
Sep 20 11:51:29 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:51:29 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:51:29 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:51:29 Compaq kernel: [    0.029779] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 11:51:29 Compaq kernel: [    1.099562] PM: Hibernation image not present or could not be loaded.
Sep 20 11:52:38 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:52:38 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:52:38 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:52:38 Compaq kernel: [    0.033783] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 11:52:38 Compaq kernel: [    1.039645] PM: Hibernation image not present or could not be loaded.
Sep 20 11:54:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:54:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:54:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:54:24 Compaq kernel: [    0.033779] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 11:54:24 Compaq kernel: [    0.971446] PM: Hibernation image not present or could not be loaded.
```

Thank you beforehand for the help provided.

---

### Post by Toz on 2013-09-20
> [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.032245] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.032248] no hardware sampling interrupt available.
Can you try the "lapic" kernel boot parameter?

Post back the logs again after you've booted with the parameter.

---

### Post by YBGQT4s on 2013-09-20
Tried with "lapic", but no luck again.

Reports:

```
Initial commandline parameters: Tue Sep 17 23:45:20 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
radeon                733899  2 
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
eeprom_93cx6           12687  1 rtl8187
ttm                    65344  1 radeon
psmouse                96744  0 
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
serio_raw              13027  0 
i2c_ali15x3            12878  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_ali1535            12777  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_algo_bit           13199  1 radeon
video                  19115  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
wmi                    18744  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              14635  1 snd
shpchp                 32265  0 
ati_agp                13242  1 
snd_page_alloc         14115  1 snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     430412     562656          0      44420     264556
-/+ buffers/cache:     121436     871632
Swap:      1013756          0    1013756


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
Tue Sep 17 23:45:25 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 20:13:21 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_seq_midi           13132  0 
eeprom_93cx6           12687  1 rtl8187
i2c_ali15x3            12878  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia                 39826  0 
psmouse                96744  0 
serio_raw              13027  0 
i2c_ali1535            12777  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
video                  19115  0 
i2c_algo_bit           13199  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  0 
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
mac_hid                13077  0 
shpchp                 32265  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     543988     449080          0      44540     327996
-/+ buffers/cache:     171452     821616
Swap:      1013756          0    1013756


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
Wed Sep 18 20:13:26 CEST 2013: performing suspend
Initial commandline parameters: 
mercredi 18 septembre 2013, 22:02:44 (UTC+0200): Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
snd_seq_midi           13132  0 
rtl8187                56323  0 
snd_rawmidi            25424  1 snd_seq_midi
mac80211              436493  1 rtl8187
ttm                    65344  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         45466  1 radeon
cfg80211              178877  2 rtl8187,mac80211
drm                   197641  4 radeon,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
i2c_algo_bit           13199  1 radeon
eeprom_93cx6           12687  1 rtl8187
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96744  0 
i2c_ali15x3            12878  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
shpchp                 32265  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  1 snd_pcm
i2c_ali1535            12777  0 
ati_agp                13242  1 
video                  19115  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
parport_pc             32114  1 
ppdev                  12849  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     565528     427540          0      48316     341260
-/+ buffers/cache:     175952     817116
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:


/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:


/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:


/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
mercredi 18 septembre 2013, 22:02:47 (UTC+0200): performing hibernate
mercredi 18 septembre 2013, 22:03:57 (UTC+0200): Awake.
mercredi 18 septembre 2013, 22:03:57 (UTC+0200): Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
mercredi 18 septembre 2013, 22:04:06 (UTC+0200): Finished.
Initial commandline parameters: 
Wed Sep 18 22:08:08 CEST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
ttm                    65344  1 radeon
eeprom_93cx6           12687  1 rtl8187
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
psmouse                96744  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
i2c_ali15x3            12878  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
video                  19115  0 
rfcomm                 38139  0 
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia                 39826  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
wmi                    18744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32265  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     532512     460556          0      44284     326112
-/+ buffers/cache:     162116     830952
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
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


/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Wed Sep 18 22:08:13 CEST 2013: performing hibernate
Wed Sep 18 22:09:17 CEST 2013: Awake.
Wed Sep 18 22:09:17 CEST 2013: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Wed Sep 18 22:09:20 CEST 2013: Finished.
Initial commandline parameters: 
Wed Sep 18 22:20:51 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
btrfs                 638340  0 
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
reiserfs              230928  0 
ext2                   67987  0 
arc4                   12473  0 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
cfg80211              178877  2 rtl8187,mac80211
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
ttm                    65344  1 radeon
eeprom_93cx6           12687  1 rtl8187
drm_kms_helper         45466  1 radeon
snd_seq_midi           13132  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
psmouse                96744  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
i2c_ali15x3            12878  0 
snd_seq_midi_event     14475  1 snd_seq_midi
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
video                  19115  0 
rfcomm                 38139  0 
snd_timer              28931  2 snd_pcm,snd_seq
pcmcia                 39826  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
wmi                    18744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32265  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     554004     439064          0      19880     320928
-/+ buffers/cache:     213196     779872
Swap:      1013756        128    1013628


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
Wed Sep 18 22:20:53 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 22:27:34 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12687  1 rtl8187
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 39826  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                96744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197641  4 radeon,ttm,drm_kms_helper
serio_raw              13027  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_ali1535            12777  0 
soundcore              14635  1 snd
i2c_algo_bit           13199  1 radeon
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
ppdev                  12849  0 
bluetooth             158447  10 rfcomm,bnep
video                  19115  0 
wmi                    18744  0 
shpchp                 32265  0 
ati_agp                13242  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     543060     450008          0      44260     324912
-/+ buffers/cache:     173888     819180
Swap:      1013756          0    1013756


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
Wed Sep 18 22:27:37 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 22:49:20 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
radeon                733899  2 
snd_seq_midi_event     14475  1 snd_seq_midi
eeprom_93cx6           12687  1 rtl8187
ttm                    65344  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
psmouse                96744  0 
pcmcia                 39826  0 
drm_kms_helper         45466  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   197641  4 radeon,ttm,drm_kms_helper
serio_raw              13027  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali1535            12777  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13199  1 radeon
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
video                  19115  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
wmi                    18744  0 
shpchp                 32265  0 
mac_hid                13077  0 
ati_agp                13242  1 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     531496     461572          0      44240     323988
-/+ buffers/cache:     163268     829800
Swap:      1013756          0    1013756


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
Wed Sep 18 22:49:24 CEST 2013: performing suspend
Initial commandline parameters: 
Wed Sep 18 23:14:09 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
btrfs                 638340  0 
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
reiserfs              230928  0 
ext2                   67987  0 
arc4                   12473  2 
joydev                 17393  0 
snd_ali5451            23459  2 
rtl8187                56323  0 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
mac80211              436493  1 rtl8187
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
eeprom_93cx6           12687  1 rtl8187
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
i2c_algo_bit           13199  1 radeon
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
i2c_ali15x3            12878  0 
soundcore              14635  1 snd
shpchp                 32265  0 
ati_agp                13242  1 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_ali1535            12777  0 
snd_page_alloc         14115  1 snd_pcm
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
video                  19115  0 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     508908     484160          0      47024     347212
-/+ buffers/cache:     114672     878396
Swap:      1013756          0    1013756


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
Wed Sep 18 23:14:13 CEST 2013: performing suspend
Initial commandline parameters: 
Thu Sep 19 22:51:55 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_ali5451            23459  2 
eeprom_93cx6           12687  1 rtl8187
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
psmouse                96744  0 
snd_seq_midi           13132  0 
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
i2c_ali15x3            12878  0 
video                  19115  0 
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
i2c_ali1535            12777  0 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 radeon
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
wmi                    18744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
ati_agp                13242  1 
snd_page_alloc         14115  1 snd_pcm
shpchp                 32265  0 
mac_hid                13077  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     557940     435128          0      44356     329460
-/+ buffers/cache:     184124     808944
Swap:      1013756          0    1013756


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
Thu Sep 19 22:51:59 CEST 2013: performing suspend
Initial commandline parameters: 
Thu Sep 19 23:32:52 CEST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158447  10 rfcomm,bnep
arc4                   12473  2 
joydev                 17393  0 
ppdev                  12849  0 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_seq_midi           13132  0 
radeon                733899  2 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
eeprom_93cx6           12687  1 rtl8187
ttm                    65344  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                96744  0 
serio_raw              13027  0 
i2c_ali15x3            12878  0 
yenta_socket           27428  0 
soundcore              14635  1 snd
pcmcia_rsrc            18367  1 yenta_socket
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
parport_pc             32114  1 
snd_page_alloc         14115  1 snd_pcm
shpchp                 32265  0 
video                  19115  0 
wmi                    18744  0 
ati_agp                13242  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     725204     267864          0     133752     365128
-/+ buffers/cache:     226324     766744
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
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
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Thu Sep 19 23:32:55 CEST 2013: performing hibernate
Fri Sep 20 11:35:25 CEST 2013: Awake.
Fri Sep 20 11:35:25 CEST 2013: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Fri Sep 20 11:35:29 CEST 2013: Finished.
Initial commandline parameters: 
Fri Sep 20 11:41:10 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
radeon                733899  2 
cfg80211              178877  2 rtl8187,mac80211
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
eeprom_93cx6           12687  1 rtl8187
psmouse                96744  0 
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
i2c_ali15x3            12878  0 
serio_raw              13027  0 
i2c_ali1535            12777  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
ttm                    65344  1 radeon
video                  19115  0 
drm_kms_helper         45466  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
drm                   197641  4 radeon,ttm,drm_kms_helper
pcmcia                 39826  0 
parport_pc             32114  1 
bnep                   17830  2 
rfcomm                 38139  0 
ppdev                  12849  0 
bluetooth             158447  10 bnep,rfcomm
i2c_algo_bit           13199  1 radeon
snd_timer              28931  2 snd_pcm,snd_seq
wmi                    18744  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
ati_agp                13242  1 
shpchp                 32265  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        993068     394240     598828          0      43704     247428
-/+ buffers/cache:     103108     889960
Swap:      1013756          0    1013756


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
Fri Sep 20 11:41:14 CEST 2013: performing suspend
Initial commandline parameters: 
Fri Sep 20 11:49:44 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
radeon                733899  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                96744  0 
i2c_ali15x3            12878  0 
serio_raw              13027  0 
ttm                    65344  1 radeon
i2c_ali1535            12777  0 
drm_kms_helper         45466  1 radeon
snd_seq_midi_event     14475  1 snd_seq_midi
drm                   197641  4 radeon,ttm,drm_kms_helper
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
i2c_algo_bit           13199  1 radeon
video                  19115  0 
pcmcia                 39826  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  1 
bluetooth             158447  10 bnep,rfcomm
ppdev                  12849  0 
wmi                    18744  0 
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
shpchp                 32265  0 
snd_page_alloc         14115  1 snd_pcm
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
ati_agp                13242  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        960684     368128     592556          0      43008     226908
-/+ buffers/cache:      98212     862472
Swap:      1013756          0    1013756


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
Fri Sep 20 11:49:48 CEST 2013: performing suspend
Initial commandline parameters: 
Fri Sep 20 12:13:28 CEST 2013: Running hooks for hibernate.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
rtl8187                56323  0 
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
mac80211              436493  1 rtl8187
radeon                733899  2 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
cfg80211              178877  2 rtl8187,mac80211
i2c_ali15x3            12878  0 
snd_timer              28931  2 snd_pcm,snd_seq
eeprom_93cx6           12687  1 rtl8187
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39826  0 
psmouse                96744  0 
ttm                    65344  1 radeon
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         45466  1 radeon
drm                   197641  4 radeon,ttm,drm_kms_helper
serio_raw              13027  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
i2c_ali1535            12777  0 
i2c_algo_bit           13199  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_page_alloc         14115  1 snd_pcm
shpchp                 32265  0 
video                  19115  0 
rfcomm                 38139  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
ati_agp                13242  1 
wmi                    18744  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        960684     626876     333808          0      45624     381976
-/+ buffers/cache:     199276     761408
Swap:      1013756          0    1013756


/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:


/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:


/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate: success.
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


/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:


/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:


/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:


/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.
Fri Sep 20 12:13:37 CEST 2013: performing hibernate
Fri Sep 20 14:43:16 CEST 2013: Awake.
Fri Sep 20 14:43:16 CEST 2013: Running hooks for thaw
Running hook /etc/pm/sleep.d/novatel_3g_suspend thaw hibernate:


/etc/pm/sleep.d/novatel_3g_suspend thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate:


/usr/lib/pm-utils/sleep.d/99video thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate:


/usr/lib/pm-utils/sleep.d/95led thaw hibernate: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm thaw hibernate:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254


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
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate: success.
Running hook /etc/pm/sleep.d/10_grub-common thaw hibernate:


/etc/pm/sleep.d/10_grub-common thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:


/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:


/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:


/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate: success.
Fri Sep 20 14:43:23 CEST 2013: Finished.
Initial commandline parameters: 
Fri Sep 20 14:50:47 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux Compaq 3.2.0-53-generic #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 i686 i686 i386 GNU/Linux
Module                  Size  Used by
arc4                   12473  2 
joydev                 17393  0 
rtl8187                56323  0 
mac80211              436493  1 rtl8187
snd_ali5451            23459  2 
snd_ac97_codec        110213  1 snd_ali5451
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_ali5451,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
radeon                733899  2 
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              178877  2 rtl8187,mac80211
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
eeprom_93cx6           12687  1 rtl8187
snd_timer              28931  2 snd_pcm,snd_seq
ttm                    65344  1 radeon
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 radeon
psmouse                96744  0 
pcmcia                 39826  0 
drm                   197641  4 radeon,ttm,drm_kms_helper
snd                    62218  11 snd_ali5451,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13027  0 
i2c_ali15x3            12878  0 
i2c_ali1535            12777  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
soundcore              14635  1 snd
snd_page_alloc         14115  1 snd_pcm
i2c_algo_bit           13199  1 radeon
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
rfcomm                 38139  0 
shpchp                 32265  0 
video                  19115  0 
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158447  10 rfcomm,bnep
ppdev                  12849  0 
wmi                    18744  0 
ati_agp                13242  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
tg3                   141465  0 
pata_ali               13562  2 
             total       used       free     shared    buffers     cached
Mem:        960684     373556     587128          0      43076     229144
-/+ buffers/cache:     101336     859348
Swap:      1013756          0    1013756


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
Fri Sep 20 14:50:51 CEST 2013: performing suspend
```

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-53-generic (buildd@komainu) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #81-Ubuntu SMP Thu Aug 22 21:03:54 UTC 2013 (Ubuntu 3.2.0-53.81-generic 3.2.50)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003bfd0000 (usable)
[    0.000000]  BIOS-e820: 000000003bfd0000 - 000000003bff0c00 (reserved)
[    0.000000]  BIOS-e820: 000000003bff0c00 - 000000003bffc000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003bffc000 - 000000003c000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] SMBIOS 2.3 present.
[    0.000000] DMI: Hewlett-Packard HP Compaq nc4010 (DY886AA#ABF)  /0834, BIOS 68BAS Ver. F.30 08/30/2006
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3bfd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 base 030000000 mask FF8000000 write-back
[    0.000000]   3 base 038000000 mask FFC000000 write-back
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bf8000-1c00000
[    0.000000] RAMDISK: 364e0000 - 37268000
[    0.000000] ACPI: RSDP 000f7840 00014 (v00 COMPAQ)
[    0.000000] ACPI: RSDT 3bff0c84 0002C (v01 COMPAQ CPQ005A  30080620 CPQ  00000001)
[    0.000000] ACPI: FACP 3bff0c00 00084 (v02 COMPAQ CPQ005A  00000002 CPQ  00000001)
[    0.000000] ACPI: DSDT 3bff0cb0 0607E (v01 COMPAQ  EVON800 00010000 MSFT 0100000E)
[    0.000000] ACPI: FACS 3bffbe80 00040
[    0.000000] ACPI: SSDT 3bff6d2e 002A7 (v01 COMPAQ  CPQGysr 00001001 MSFT 0100000E)
[    0.000000] 71MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003bfd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0003bfd0
[    0.000000] On node 0 totalpages: 245599
[    0.000000] free_area_init_node: node 0, pgdat c182bd40, node_mem_map f5d60200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 144 pages used for memmap
[    0.000000]   HighMem zone: 18242 pages, LIFO batch:3
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- reenabling.
[    0.000000] Found and enabled local APIC!
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 3c000000 (gap: 3c000000:c4000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @f77ea000 s31616 r0 d21632 u53248
[    0.000000] pcpu-alloc: s31616 r0 d21632 u53248 alloc=13*4096
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 243679
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-53-generic root=UUID=0e519161-7a32-4e2e-915c-7da765feae21 ro lapic quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3931136 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003bfd0)
[    0.000000] Memory: 946088k/982848k available (5636k kernel code, 36308k reserved, 2780k data, 716k init, 73544k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc1839000 - 0xc18ec000   ( 716 kB)
[    0.000000]       .data : 0xc1581284 - 0xc1838480   (2780 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1581284   (5636 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=f5808000 soft=f580a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1492.619 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2985.23 BogoMIPS (lpj=5970476)
[    0.008014] pid_max: default: 32768 minimum: 301
[    0.008055] Security Framework initialized
[    0.008105] AppArmor: AppArmor initialized
[    0.008108] Yama: becoming mindful.
[    0.008224] Mount-cache hash table entries: 512
[    0.008503] Initializing cgroup subsys cpuacct
[    0.008515] Initializing cgroup subsys memory
[    0.008533] Initializing cgroup subsys devices
[    0.008537] Initializing cgroup subsys freezer
[    0.008542] Initializing cgroup subsys blkio
[    0.008556] Initializing cgroup subsys perf_event
[    0.008616] mce: CPU supports 5 MCE banks
[    0.008633] CPU0: Thermal monitoring enabled (TM2)
[    0.009089] SMP alternatives: switching to UP code
[    0.022197] Freeing SMP alternatives: 24k freed
[    0.022213] ACPI: Core revision 20110623
[    0.026845] ACPI: setting ELCR to 0200 (from 0c00)
[    0.028092] ftrace: allocating 25519 entries in 50 pages
[    0.032220] weird, boot CPU (#0) not listed by the BIOS.
[    0.032230] SMP motherboard not detected.
[    0.032236] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.036002] SMP disabled
[    0.036002] Performance Events: p6 PMU driver.
[    0.036002] ... version:                0
[    0.036002] ... bit width:              32
[    0.036002] ... generic registers:      2
[    0.036002] ... value mask:             00000000ffffffff
[    0.036002] ... max period:             000000007fffffff
[    0.036002] ... fixed-purpose events:   0
[    0.036002] ... event mask:             0000000000000003
[    0.036002] NMI watchdog enabled, takes one hw-pmu counter.
[    0.036002] Brought up 1 CPUs
[    0.036002] Total of 1 processors activated (2985.23 BogoMIPS).
[    0.036002] devtmpfs: initialized
[    0.036002] EVM: security.selinux
[    0.036002] EVM: security.SMACK64
[    0.036002] EVM: security.capability
[    0.036002] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
[    0.036002] HP Compaq Laptop series board detected. Selecting BIOS-method for reboots.
[    0.036449] print_constraints: dummy: 
[    0.036511] RTC time: 12:52:22, date: 09/20/13
[    0.036600] NET: Registered protocol family 16
[    0.036854] EISA bus registered
[    0.036923] ACPI: bus type pci registered
[    0.039727] PCI: PCI BIOS revision 2.10 entry at 0xf031f, last bus=1
[    0.039731] PCI: Using configuration type 1 for base access
[    0.041982] bio: create slab <bio-0> at 0
[    0.042160] ACPI: Added _OSI(Module Device)
[    0.042165] ACPI: Added _OSI(Processor Device)
[    0.042169] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.042172] ACPI: Added _OSI(Processor Aggregator Device)
[    0.043661] ACPI: EC: Look up EC in DSDT
[    0.060094] ACPI: Interpreter enabled
[    0.064028] ACPI: (supports S0 S3 S4 S5)
[    0.064058] ACPI: Using PIC for interrupt routing
[    0.065912] ACPI: Power Resource [C15A] (on)
[    0.067037] ACPI: Power Resource [C15F] (on)
[    0.068203] ACPI: Power Resource [C169] (on)
[    0.069070] ACPI: Power Resource [C17A] (on)
[    0.073397] ACPI: Power Resource [C1F2] (off)
[    0.073482] ACPI: Power Resource [C1F3] (off)
[    0.073569] ACPI: Power Resource [C1F4] (off)
[    0.073661] ACPI: Power Resource [C1F5] (off)
[    0.074379] ACPI: EC: GPE = 0x18, I/O: command/status = 0x66, data = 0x62
[    0.074616] ACPI: No dock devices found.
[    0.074619] HEST: Table not found.
[    0.074631] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.078976] ACPI: PCI Root Bridge [C044] (domain 0000 [bus 00-ff])
[    0.087631] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.087636] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.087641] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.087645] pci_root PNP0A03:00: host bridge window [mem 0x3c000000-0xffffffff] (ignored)
[    0.087650] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff] (ignored)
[    0.087675] pci 0000:00:00.0: [1002:cbb2] type 0 class 0x000600
[    0.087691] pci 0000:00:00.0: reg 10: [mem 0xa4000000-0xa7ffffff pref]
[    0.087698] pci 0000:00:00.0: reg 14: [mem 0xa0480000-0xa0480fff pref]
[    0.087754] pci 0000:00:01.0: [1002:7010] type 1 class 0x000604
[    0.087792] pci 0000:00:06.0: [10b9:5451] type 0 class 0x000401
[    0.087807] pci 0000:00:06.0: reg 10: [io  0x3000-0x30ff]
[    0.087816] pci 0000:00:06.0: reg 14: [mem 0xa0080000-0xa0080fff]
[    0.087864] pci 0000:00:06.0: supports D1 D2
[    0.087869] pci 0000:00:06.0: PME# supported from D2 D3hot D3cold
[    0.087875] pci 0000:00:06.0: PME# disabled
[    0.087893] pci 0000:00:07.0: [10b9:1533] type 0 class 0x000601
[    0.087978] pci 0000:00:08.0: [10b9:5457] type 0 class 0x000703
[    0.087992] pci 0000:00:08.0: reg 10: [mem 0xa0100000-0xa0100fff]
[    0.088001] pci 0000:00:08.0: reg 14: [io  0x3400-0x34ff]
[    0.088052] pci 0000:00:08.0: PME# supported from D3hot D3cold
[    0.088057] pci 0000:00:08.0: PME# disabled
[    0.088080] pci 0000:00:0b.0: [1217:7114] type 2 class 0x000607
[    0.088096] pci 0000:00:0b.0: reg 10: [mem 0xa0180000-0xa0180fff]
[    0.088119] pci 0000:00:0b.0: supports D1 D2
[    0.088123] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.088128] pci 0000:00:0b.0: PME# disabled
[    0.088146] pci 0000:00:0b.1: [1217:7114] type 2 class 0x000607
[    0.088161] pci 0000:00:0b.1: reg 10: [mem 0xa0200000-0xa0200fff]
[    0.088184] pci 0000:00:0b.1: supports D1 D2
[    0.088188] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.088193] pci 0000:00:0b.1: PME# disabled
[    0.088211] pci 0000:00:0b.2: [1217:7110] type 0 class 0x000880
[    0.088226] pci 0000:00:0b.2: reg 10: [mem 0xa0280000-0xa0280fff]
[    0.088284] pci 0000:00:0b.2: supports D1 D2
[    0.088287] pci 0000:00:0b.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.088292] pci 0000:00:0b.2: PME# disabled
[    0.088318] pci 0000:00:10.0: [10b9:5229] type 0 class 0x000101
[    0.088352] pci 0000:00:10.0: reg 20: [io  0x3800-0x380f]
[    0.088395] pci 0000:00:11.0: [10b9:7101] type 0 class 0x000680
[    0.088452] pci 0000:00:11.0: quirk: [io  0x1000-0x103f] claimed by ali7101 ACPI
[    0.088458] pci 0000:00:11.0: quirk: [io  0x1100-0x111f] claimed by ali7101 SMB
[    0.088478] pci 0000:00:12.0: [1033:0035] type 0 class 0x000c03
[    0.088492] pci 0000:00:12.0: reg 10: [mem 0xa0300000-0xa0300fff]
[    0.088544] pci 0000:00:12.0: supports D1 D2
[    0.088548] pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.088553] pci 0000:00:12.0: PME# disabled
[    0.088570] pci 0000:00:12.1: [1033:0035] type 0 class 0x000c03
[    0.088584] pci 0000:00:12.1: reg 10: [mem 0xa0380000-0xa0380fff]
[    0.088636] pci 0000:00:12.1: supports D1 D2
[    0.088640] pci 0000:00:12.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.088645] pci 0000:00:12.1: PME# disabled
[    0.088662] pci 0000:00:12.2: [1033:00e0] type 0 class 0x000c03
[    0.088676] pci 0000:00:12.2: reg 10: [mem 0xa0400000-0xa04000ff]
[    0.088728] pci 0000:00:12.2: supports D1 D2
[    0.088731] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot D3cold
[    0.088737] pci 0000:00:12.2: PME# disabled
[    0.088765] pci 0000:00:13.0: [14e4:165d] type 0 class 0x000200
[    0.088788] pci 0000:00:13.0: reg 10: [mem 0xa0000000-0xa000ffff 64bit]
[    0.088824] pci 0000:00:13.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.088865] pci 0000:00:13.0: PME# supported from D3hot D3cold
[    0.088871] pci 0000:00:13.0: PME# disabled
[    0.088919] pci 0000:01:05.0: [1002:4337] type 0 class 0x000300
[    0.088934] pci 0000:01:05.0: reg 10: [mem 0x98000000-0x9fffffff pref]
[    0.088943] pci 0000:01:05.0: reg 14: [io  0x2000-0x20ff]
[    0.088952] pci 0000:01:05.0: reg 18: [mem 0x90000000-0x9000ffff]
[    0.088976] pci 0000:01:05.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.089003] pci 0000:01:05.0: supports D1 D2
[    0.089033] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.089040] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.089046] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x900fffff]
[    0.089052] pci 0000:00:01.0:   bridge window [mem 0x98000000-0x9fffffff pref]
[    0.089113] pci_bus 0000:00: on NUMA node 0
[    0.089120] ACPI: PCI Interrupt Routing Table [\_SB_.C044._PRT]
[    0.089230] ACPI: PCI Interrupt Routing Table [\_SB_.C044.C045._PRT]
[    0.089314]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.102153] ACPI: PCI Interrupt Link [C0C4] (IRQs 5 *10 11)
[    0.102255] ACPI: PCI Interrupt Link [C0C5] (IRQs 5 *10 11)
[    0.102353] ACPI: PCI Interrupt Link [C0C6] (IRQs 5 10 *11)
[    0.102431] ACPI: PCI Interrupt Link [C0C7] (IRQs 5 10 11) *0, disabled.
[    0.102529] ACPI: PCI Interrupt Link [C0C8] (IRQs 5 *10 11)
[    0.102607] ACPI: PCI Interrupt Link [C0C9] (IRQs 5 10 11) *0, disabled.
[    0.102706] ACPI: PCI Interrupt Link [C0CA] (IRQs 5 10 *11)
[    0.102802] ACPI: PCI Interrupt Link [C0CB] (IRQs 5 10 *11)
[    0.103040] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.103045] vgaarb: loaded
[    0.103047] vgaarb: bridge control possible 0000:01:05.0
[    0.103268] i2c-core: driver [aat2870] using legacy suspend method
[    0.103271] i2c-core: driver [aat2870] using legacy resume method
[    0.103470] SCSI subsystem initialized
[    0.103600] libata version 3.00 loaded.
[    0.103705] usbcore: registered new interface driver usbfs
[    0.103737] usbcore: registered new interface driver hub
[    0.103785] usbcore: registered new device driver usb
[    0.103964] PCI: Using ACPI for IRQ routing
[    0.103972] PCI: pci_cache_line_size set to 64 bytes
[    0.104053] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.104059] reserve RAM buffer: 000000003bfd0000 - 000000003bffffff 
[    0.104286] NetLabel: Initializing
[    0.104290] NetLabel:  domain hash size = 128
[    0.104293] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.104319] NetLabel:  unlabeled traffic allowed by default
[    0.122742] AppArmor: AppArmor Filesystem Enabled
[    0.122877] pnp: PnP ACPI init
[    0.122930] ACPI: bus type pnp registered
[    0.123227] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.123233] pnp 00:00: [mem 0x000e0000-0x000fffff]
[    0.123237] pnp 00:00: [mem 0x00100000-0x3bffffff]
[    0.123381] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.123387] system 00:00: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.123392] system 00:00: [mem 0x00100000-0x3bffffff] could not be reserved
[    0.123401] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.127818] pnp 00:01: [bus 00-ff]
[    0.127824] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.127829] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.127833] pnp 00:01: [io  0x0d00-0xffff window]
[    0.127837] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.127841] pnp 00:01: [mem 0x3c000000-0xffffffff window]
[    0.127845] pnp 00:01: [mem 0x000d0000-0x000dffff window]
[    0.128054] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.129138] pnp 00:02: [io  0x03f8-0x03ff]
[    0.129148] pnp 00:02: [irq 4]
[    0.129249] pnp 00:02: Plug and Play ACPI device, IDs PNP0501 PNP0500 (active)
[    0.130367] pnp 00:03: [io  0x03e8-0x03ef]
[    0.130372] pnp 00:03: [irq 3]
[    0.130376] pnp 00:03: [dma 3]
[    0.130479] pnp 00:03: Plug and Play ACPI device, IDs ALI5123 PNP0510 (active)
[    0.131668] pnp 00:04: [io  0x0378-0x037f]
[    0.131672] pnp 00:04: [io  0x0778-0x077a]
[    0.131676] pnp 00:04: [irq 7]
[    0.131680] pnp 00:04: [dma 1]
[    0.131853] pnp 00:04: Plug and Play ACPI device, IDs PNP0401 (active)
[    0.131940] pnp 00:05: [io  0x00f0-0x00ff]
[    0.131945] pnp 00:05: [irq 13]
[    0.131995] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.132028] pnp 00:06: [io  0x0000-0x000f]
[    0.132032] pnp 00:06: [io  0x0080-0x008f]
[    0.132036] pnp 00:06: [io  0x00c0-0x00df]
[    0.132039] pnp 00:06: [dma 4]
[    0.132088] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.132103] pnp 00:07: [io  0x0061]
[    0.132157] pnp 00:07: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.132173] pnp 00:08: [io  0x0070-0x0071]
[    0.132177] pnp 00:08: [io  0x0072-0x0073]
[    0.132181] pnp 00:08: [irq 8]
[    0.132237] pnp 00:08: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.132253] pnp 00:09: [io  0x0060]
[    0.132257] pnp 00:09: [io  0x0064]
[    0.132260] pnp 00:09: [irq 1]
[    0.132310] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.132324] pnp 00:0a: [irq 12]
[    0.132384] pnp 00:0a: Plug and Play ACPI device, IDs SYN0102 SYN0100 SYN0002 PNP0f13 (active)
[    0.132538] pnp 00:0b: [io  0x002e-0x002f]
[    0.132542] pnp 00:0b: [io  0x004e-0x004f]
[    0.132545] pnp 00:0b: [io  0x0063]
[    0.132548] pnp 00:0b: [io  0x0065]
[    0.132552] pnp 00:0b: [io  0x0067-0x006f]
[    0.132555] pnp 00:0b: [io  0x0074-0x007f]
[    0.132558] pnp 00:0b: [io  0x0092]
[    0.132562] pnp 00:0b: [io  0x00b0-0x00b3]
[    0.132565] pnp 00:0b: [io  0x0370-0x0371]
[    0.132569] pnp 00:0b: [io  0x040b]
[    0.132572] pnp 00:0b: [io  0x0480-0x048f]
[    0.132575] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.132579] pnp 00:0b: [io  0x04d6]
[    0.132582] pnp 00:0b: [io  0x1400-0x141f]
[    0.132586] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.132590] pnp 00:0b: [mem 0xfff00000-0xffffffff]
[    0.132695] system 00:0b: [io  0x0370-0x0371] has been reserved
[    0.132700] system 00:0b: [io  0x040b] has been reserved
[    0.132705] system 00:0b: [io  0x0480-0x048f] has been reserved
[    0.132709] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.132713] system 00:0b: [io  0x04d6] has been reserved
[    0.132718] system 00:0b: [io  0x1400-0x141f] has been reserved
[    0.132723] system 00:0b: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.132728] system 00:0b: [mem 0xfff00000-0xffffffff] has been reserved
[    0.132734] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.134128] pnp 00:0c: [io  0x1000-0x107f]
[    0.134132] pnp 00:0c: [io  0x1100-0x111f]
[    0.134136] pnp 00:0c: [mem 0xa0480000-0xa0480fff]
[    0.134232] system 00:0c: [io  0x1000-0x107f] could not be reserved
[    0.134237] system 00:0c: [io  0x1100-0x111f] has been reserved
[    0.134242] system 00:0c: [mem 0xa0480000-0xa0480fff] has been reserved
[    0.134247] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.134870] pnp 00:0d: [mem 0x000cf000-0x000cffff]
[    0.134960] system 00:0d: [mem 0x000cf000-0x000cffff] has been reserved
[    0.134965] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.134990] pnp: PnP ACPI: found 14 devices
[    0.134994] ACPI: ACPI bus type pnp unregistered
[    0.135003] PnPBIOS: Disabled by ACPI PNP
[    0.172932] Switching to clocksource acpi_pm
[    0.172985] PCI: max bus depth: 1 pci_try_num: 2
[    0.173036] pci 0000:00:13.0: BAR 6: assigned [mem 0x3c000000-0x3c00ffff pref]
[    0.173043] pci 0000:00:0b.1: BAR 16: assigned [mem 0x40000000-0x43ffffff]
[    0.173048] pci 0000:00:0b.1: BAR 15: assigned [mem 0x44000000-0x47ffffff pref]
[    0.173055] pci 0000:00:0b.1: BAR 14: assigned [io  0x1800-0x18ff]
[    0.173060] pci 0000:00:0b.1: BAR 13: assigned [io  0x1c00-0x1cff]
[    0.173065] pci 0000:00:0b.0: BAR 16: assigned [mem 0x48000000-0x4bffffff]
[    0.173070] pci 0000:00:0b.0: BAR 15: assigned [mem 0x4c000000-0x4fffffff pref]
[    0.173076] pci 0000:00:0b.0: BAR 14: assigned [io  0x3c00-0x3cff]
[    0.173081] pci 0000:00:0b.0: BAR 13: assigned [io  0x4000-0x40ff]
[    0.173088] pci 0000:01:05.0: BAR 6: assigned [mem 0x90020000-0x9003ffff pref]
[    0.173094] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.173099] pci 0000:00:01.0:   bridge window [io  0x2000-0x2fff]
[    0.173105] pci 0000:00:01.0:   bridge window [mem 0x90000000-0x900fffff]
[    0.173111] pci 0000:00:01.0:   bridge window [mem 0x98000000-0x9fffffff pref]
[    0.173118] pci 0000:00:0b.0: CardBus bridge to [bus 02-05]
[    0.173122] pci 0000:00:0b.0:   bridge window [io  0x4000-0x40ff]
[    0.173128] pci 0000:00:0b.0:   bridge window [io  0x3c00-0x3cff]
[    0.173134] pci 0000:00:0b.0:   bridge window [mem 0x4c000000-0x4fffffff pref]
[    0.173140] pci 0000:00:0b.0:   bridge window [mem 0x48000000-0x4bffffff]
[    0.173145] pci 0000:00:0b.1: CardBus bridge to [bus 06-09]
[    0.173149] pci 0000:00:0b.1:   bridge window [io  0x1c00-0x1cff]
[    0.173154] pci 0000:00:0b.1:   bridge window [io  0x1800-0x18ff]
[    0.173160] pci 0000:00:0b.1:   bridge window [mem 0x44000000-0x47ffffff pref]
[    0.173166] pci 0000:00:0b.1:   bridge window [mem 0x40000000-0x43ffffff]
[    0.173474] ACPI: PCI Interrupt Link [C0C6] enabled at IRQ 11
[    0.173481] PCI: setting IRQ 11 as level-triggered
[    0.173488] pci 0000:00:0b.0: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[    0.173501] pci 0000:00:0b.1: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[    0.173509] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.173514] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.173519] pci_bus 0000:01: resource 0 [io  0x2000-0x2fff]
[    0.173523] pci_bus 0000:01: resource 1 [mem 0x90000000-0x900fffff]
[    0.173527] pci_bus 0000:01: resource 2 [mem 0x98000000-0x9fffffff pref]
[    0.173531] pci_bus 0000:02: resource 0 [io  0x4000-0x40ff]
[    0.173535] pci_bus 0000:02: resource 1 [io  0x3c00-0x3cff]
[    0.173540] pci_bus 0000:02: resource 2 [mem 0x4c000000-0x4fffffff pref]
[    0.173544] pci_bus 0000:02: resource 3 [mem 0x48000000-0x4bffffff]
[    0.173549] pci_bus 0000:06: resource 0 [io  0x1c00-0x1cff]
[    0.173552] pci_bus 0000:06: resource 1 [io  0x1800-0x18ff]
[    0.173557] pci_bus 0000:06: resource 2 [mem 0x44000000-0x47ffffff pref]
[    0.173561] pci_bus 0000:06: resource 3 [mem 0x40000000-0x43ffffff]
[    0.173678] NET: Registered protocol family 2
[    0.173830] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.174416] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.176762] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.178742] TCP: Hash tables configured (established 131072 bind 65536)
[    0.178749] TCP reno registered
[    0.178761] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.178824] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.179203] NET: Registered protocol family 1
[    0.179276] pci 0000:00:07.0: Activating ISA DMA hang workarounds
[    0.179694] ACPI: PCI Interrupt Link [C0C5] enabled at IRQ 10
[    0.179704] PCI: setting IRQ 10 as level-triggered
[    0.179713] pci 0000:00:12.0: PCI INT A -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.179763] pci 0000:00:12.0: PCI INT A disabled
[    0.179783] pci 0000:00:12.1: PCI INT B -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.179794] pci 0000:00:12.1: PCI INT B disabled
[    0.179807] pci 0000:00:12.2: PCI INT C -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.179821] pci 0000:00:12.2: PCI INT C disabled
[    0.179834] pci 0000:01:05.0: Boot video device
[    0.179838] PCI: CLS 64 bytes, default 64
[    0.180839] audit: initializing netlink socket (disabled)
[    0.180869] type=2000 audit(1379681542.180:1): initialized
[    0.215457] Trying to unpack rootfs image as initramfs...
[    0.257343] highmem bounce pool size: 64 pages
[    0.257360] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.264813] VFS: Disk quotas dquot_6.5.2
[    0.264983] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.266175] fuse init (API version 7.17)
[    0.266353] msgmni has been set to 1704
[    0.280925] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.280994] io scheduler noop registered
[    0.280998] io scheduler deadline registered
[    0.281015] io scheduler cfq registered (default)
[    0.281335] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.281382] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.284148] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.284350] ACPI: AC Adapter [C137] (on-line)
[    0.284537] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.284552] ACPI: Sleep Button [C13B]
[    0.284637] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.284714] ACPI: Lid Switch [C13A]
[    0.284798] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.284804] ACPI: Power Button [PWRF]
[    0.284949] ACPI: Fan [C1F6] (off)
[    0.285031] ACPI: Fan [C1F7] (off)
[    0.285107] ACPI: Fan [C1F8] (off)
[    0.285186] ACPI: Fan [C1F9] (off)
[    0.285229] ACPI: Invalid PBLK length [7]
[    0.285318] Marking TSC unstable due to TSC halts in idle
[    0.285338] ACPI: acpi_idle registered with cpuidle
[    0.298980] thermal LNXTHERM:00: registered as thermal_zone0
[    0.298987] ACPI: Thermal Zone [TZ1] (50 C)
[    0.306998] thermal LNXTHERM:01: registered as thermal_zone1
[    0.307004] ACPI: Thermal Zone [TZ2] (35 C)
[    0.322716] thermal LNXTHERM:02: registered as thermal_zone2
[    0.322724] ACPI: Thermal Zone [TZ3] (23 C)
[    0.322861] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.322886] ACPI: Battery Slot [C139] (battery present)
[    0.322911] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.322922] ACPI: Battery Slot [C138] (battery absent)
[    0.322975] ERST: Table is not found!
[    0.322978] GHES: HEST is not enabled!
[    0.323357] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.343974] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.349188] ACPI: Battery Slot [C138] (battery absent)
[    0.349257] isapnp: Scanning for PnP cards...
[    0.480694] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.508710] ACPI: Battery Slot [C139] (battery present)
[    0.533225] 00:02: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.597300] ACPI: PCI Interrupt Link [C0CA] enabled at IRQ 11
[    0.597317] serial 0000:00:08.0: PCI INT A -> Link[C0CA] -> GSI 11 (level, low) -> IRQ 11
[    0.597347] serial 0000:00:08.0: PCI INT A disabled
[    0.597731] Linux agpgart interface v0.103
[    0.606464] brd: module loaded
[    0.607859] loop: module loaded
[    0.608704] ACPI: PCI Interrupt Link [C0C4] enabled at IRQ 10
[    0.608719] pata_acpi 0000:00:10.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[    0.608840] pata_acpi 0000:00:10.0: PCI INT A disabled
[    0.609521] Fixed MDIO Bus: probed
[    0.609561] tun: Universal TUN/TAP device driver, 1.6
[    0.609564] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.609695] PPP generic driver version 2.4.2
[    0.612542] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.612604] ehci_hcd 0000:00:12.2: PCI INT C -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.612644] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.612745] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.636397] ehci_hcd 0000:00:12.2: irq 10, io mem 0xa0400000
[    0.680026] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.756416] hub 1-0:1.0: USB hub found
[    0.756435] hub 1-0:1.0: 5 ports detected
[    0.756658] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.756734] ohci_hcd 0000:00:12.0: PCI INT A -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.756783] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.756991] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 2
[    0.757043] ohci_hcd 0000:00:12.0: irq 10, io mem 0xa0300000
[    0.888669] hub 2-0:1.0: USB hub found
[    0.888686] hub 2-0:1.0: 3 ports detected
[    0.888864] ohci_hcd 0000:00:12.1: PCI INT B -> Link[C0C5] -> GSI 10 (level, low) -> IRQ 10
[    0.888913] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.932471] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 3
[    0.932524] ohci_hcd 0000:00:12.1: irq 10, io mem 0xa0380000
[    1.019716] isapnp: No Plug & Play device found
[    1.080823] hub 3-0:1.0: USB hub found
[    1.080839] hub 3-0:1.0: 2 ports detected
[    1.081016] uhci_hcd: USB Universal Host Controller Interface driver
[    1.081232] usbcore: registered new interface driver libusual
[    1.081348] i8042: PNP: PS/2 Controller [PNP0303:C177,PNP0f13:C178] at 0x60,0x64 irq 1,12
[    1.083145] i8042: Detected active multiplexing controller, rev 1.1
[    1.083857] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.083880] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.083948] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.083989] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.084087] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.084342] mousedev: PS/2 mouse device common for all mice
[    1.084665] rtc_cmos 00:08: RTC can wake from S4
[    1.085650] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    1.085692] rtc0: alarms up to one month, y3k, 114 bytes nvram
[    1.085893] device-mapper: uevent: version 1.0.3
[    1.088717] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.088796] EISA: Probing bus 0 at eisa.0
[    1.088813] Cannot allocate resource for EISA slot 1
[    1.088818] Cannot allocate resource for EISA slot 2
[    1.088822] Cannot allocate resource for EISA slot 3
[    1.088826] Cannot allocate resource for EISA slot 4
[    1.088849] EISA: Detected 0 cards.
[    1.088881] cpufreq-nforce2: No nForce2 chipset.
[    1.088959] cpuidle: using governor ladder
[    1.089066] cpuidle: using governor menu
[    1.089070] EFI Variables Facility v0.08 2004-May-17
[    1.089574] TCP cubic registered
[    1.089824] NET: Registered protocol family 10
[    1.090861] NET: Registered protocol family 17
[    1.090871] Registering the dns_resolver key type
[    1.090935] Using IPI No-Shortcut mode
[    1.094709] PM: Hibernation image not present or could not be loaded.
[    1.094748] registered taskstats version 1
[    1.104293] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    1.106815] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.297054] Freeing initrd memory: 13856k freed
[    1.363322]   Magic number: 13:133:886
[    1.363667] rtc_cmos 00:08: setting system clock to 2013-09-20 12:52:24 UTC (1379681544)
[    1.365139] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.365147] EDD information not available.
[    1.365484] Freeing unused kernel memory: 716k freed
[    1.366288] Write protecting the kernel text: 5640k
[    1.366347] Write protecting the kernel read-only data: 2332k
[    1.397307] udevd[80]: starting version 175
[    1.703446] tg3.c:v3.121 (November 2, 2011)
[    1.703810] ACPI: PCI Interrupt Link [C0C8] enabled at IRQ 10
[    1.703824] tg3 0000:00:13.0: PCI INT A -> Link[C0C8] -> GSI 10 (level, low) -> IRQ 10
[    1.842303] tg3 0000:00:13.0: eth0: Tigon3 [partno(BCM5705mA1) rev 3003] (PCI:33MHz:32-bit) MAC address 00:0d:9d:8e:45:25
[    1.842315] tg3 0000:00:13.0: eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[0], EEE[0])
[    1.842321] tg3 0000:00:13.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.842326] tg3 0000:00:13.0: eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    1.842432] pata_ali 0000:00:10.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[    1.846267] scsi0 : pata_ali
[    1.846717] scsi1 : pata_ali
[    1.847272] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x3800 irq 14
[    1.847278] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3808 irq 15
[    2.008717] ata1.00: ATA-6: Hitachi IC25N040ATMR04-0, MO2AAD0A, max UDMA/100
[    2.008723] ata1.00: 78140160 sectors, multi 16: LBA48 
[    2.024571] ata1.00: configured for UDMA/100
[    2.024870] scsi 0:0:0:0: Direct-Access     ATA      Hitachi IC25N040 MO2A PQ: 0 ANSI: 5
[    2.025244] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    2.025325] sd 0:0:0:0: [sda] Write Protect is off
[    2.025331] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.025366] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.025944] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.072330]  sda: sda1 sda2 < sda5 >
[    2.072867] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.590948] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.590958] EXT4-fs (sda1): write access will be enabled during recovery
[    2.922386] EXT4-fs (sda1): recovery complete
[    2.922948] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   25.523347] Adding 1013756k swap on /dev/sda5.  Priority:-1 extents:1 across:1013756k 
[   25.548285] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.609609] udevd[316]: starting version 175
[   25.719414] lp: driver loaded but no devices found
[   25.884833] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   26.035270] agpgart-ati 0000:00:00.0: Ati IGP345M chipset
[   26.290854] wmi: Mapper loaded
[   26.297957] agpgart-ati 0000:00:00.0: AGP aperture is 64M @ 0xa4000000
[   26.298103] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   26.472996] ppdev: user-space parallel port driver
[   26.483733] Bluetooth: Core ver 2.16
[   26.485682] NET: Registered protocol family 31
[   26.485692] Bluetooth: HCI device and connection manager initialized
[   26.485699] Bluetooth: HCI socket layer initialized
[   26.485703] Bluetooth: L2CAP socket layer initialized
[   26.485723] Bluetooth: SCO socket layer initialized
[   26.487414] parport_pc 00:04: reported by Plug and Play ACPI
[   26.487491] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   26.523409] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   26.523417] Bluetooth: BNEP filters: protocol multicast
[   26.632109] lp0: using parport0 (interrupt-driven).
[   26.640920] Bluetooth: RFCOMM TTY layer initialized
[   26.640936] Bluetooth: RFCOMM socket layer initialized
[   26.640939] Bluetooth: RFCOMM ver 1.11
[   26.649064] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:00/LNXVIDEO:00/input/input4
[   26.654036] ACPI: Video Device [C046] (multi-head: yes  rom: no  post: no)
[   26.683734] type=1400 audit(1379681569.814:2): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=562 comm="apparmor_parser"
[   26.685195] type=1400 audit(1379681569.818:3): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=562 comm="apparmor_parser"
[   26.856363] ACPI: resource ali1535_smbus [io  0x1100-0x111f] conflicts with ACPI region C092 [io 0x1100-0x1107]
[   26.856371] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   26.856378] ali1535_smbus 0000:00:11.0: ALI1535 not detected, module not inserted.
[   26.857340] yenta_cardbus 0000:00:0b.0: CardBus bridge found [0e11:005a]
[   26.857364] yenta_cardbus 0000:00:0b.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   26.902959] [drm] Initialized drm 1.1.0 20060810
[   26.988845] yenta_cardbus 0000:00:0b.0: ISA IRQ mask 0x0038, PCI irq 11
[   26.988853] yenta_cardbus 0000:00:0b.0: Socket status: 30000820
[   26.999797] yenta_cardbus 0000:00:0b.1: CardBus bridge found [0e11:005a]
[   27.092370] type=1400 audit(1379681570.226:4): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=606 comm="apparmor_parser"
[   27.093163] type=1400 audit(1379681570.226:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=606 comm="apparmor_parser"
[   27.093637] type=1400 audit(1379681570.226:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=606 comm="apparmor_parser"
[   27.136965] yenta_cardbus 0000:00:0b.1: ISA IRQ mask 0x0038, PCI irq 11
[   27.136974] yenta_cardbus 0000:00:0b.1: Socket status: 30000006
[   27.155164] type=1400 audit(1379681570.286:7): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=611 comm="apparmor_parser"
[   27.194336] ali15x3_smbus 0000:00:11.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   27.194347] ali15x3_smbus 0000:00:11.0: ALI15X3 not detected, module not inserted.
[   27.212635] [drm] radeon defaulting to kernel modesetting.
[   27.212647] [drm] radeon kernel modesetting enabled.
[   27.212835] radeon 0000:01:05.0: PCI INT A -> Link[C0C4] -> GSI 10 (level, low) -> IRQ 10
[   27.242409] [drm] initializing kernel modesetting (RS200 0x1002:0x4337 0x0E11:0x005A).
[   27.242471] [drm] register mmio base: 0x90000000
[   27.242474] [drm] register mmio size: 65536
[   27.246151] agpgart-ati 0000:00:00.0: AGP 2.0 bridge
[   27.246609] agpgart-ati 0000:00:00.0: putting AGP V2 device into 4x mode
[   27.249443] radeon 0000:01:05.0: putting AGP V2 device into 4x mode
[   27.249459] radeon 0000:01:05.0: GTT: 64M 0xA4000000 - 0xA7FFFFFF
[   27.249474] radeon 0000:01:05.0: VRAM: 64M 0x000000003C000000 - 0x000000003FFFFFFF (64M used)
[   27.253460] [drm] Detected VRAM RAM=64M, BAR=128M
[   27.253471] [drm] RAM width 64bits DDR
[   27.253799] cfg80211: Calling CRDA to update world regulatory domain
[   27.258267] [TTM] Zone  kernel: Available graphics memory: 443570 kiB.
[   27.258318] [TTM] Zone highmem: Available graphics memory: 480342 kiB.
[   27.258322] [TTM] Initializing pool allocator.
[   27.258675] [drm] radeon: 64M of VRAM memory ready
[   27.258681] [drm] radeon: 64M of GTT memory ready.
[   27.281598] radeon 0000:01:05.0: WB disabled
[   27.281615] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   27.281619] [drm] Driver supports precise vblank timestamp query.
[   27.281660] [drm] radeon: irq initialized.
[   27.293078] [drm] Loading R100 Microcode
[   27.734419] ACPI: PCI Interrupt Link [C0CB] enabled at IRQ 11
[   27.734433] snd_ali5451 0000:00:06.0: PCI INT A -> Link[C0CB] -> GSI 11 (level, low) -> IRQ 11
[   27.821096] psmouse serio4: synaptics: Touchpad model: 1, fw: 5.9, id: 0x1b6eb1, caps: 0xa84793/0x100000/0x0
[   27.821116] psmouse serio4: synaptics: serio: Synaptics pass-through port at isa0060/serio4/input0
[   27.876586] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input5
[   27.888116] pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
[   27.888157] pci 0000:02:00.0: [1033:0035] type 0 class 0x000c03
[   27.888186] pci 0000:02:00.0: reg 10: [mem 0x00000000-0x00000fff]
[   27.888276] pci 0000:02:00.0: supports D1 D2
[   27.888280] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[   27.888288] pci 0000:02:00.0: PME# disabled
[   27.888313] pci 0000:02:00.1: [1033:0035] type 0 class 0x000c03
[   27.888331] pci 0000:02:00.1: reg 10: [mem 0x00000000-0x00000fff]
[   27.888406] pci 0000:02:00.1: supports D1 D2
[   27.888410] pci 0000:02:00.1: PME# supported from D0 D1 D2 D3hot
[   27.888416] pci 0000:02:00.1: PME# disabled
[   27.888437] pci 0000:02:00.2: [1033:00e0] type 0 class 0x000c03
[   27.888456] pci 0000:02:00.2: reg 10: [mem 0x00000000-0x000000ff]
[   27.888531] pci 0000:02:00.2: supports D1 D2
[   27.888534] pci 0000:02:00.2: PME# supported from D0 D1 D2 D3hot
[   27.888540] pci 0000:02:00.2: PME# disabled
[   27.888571] pci 0000:02:00.0: BAR 0: assigned [mem 0x48000000-0x48000fff]
[   27.888581] pci 0000:02:00.0: BAR 0: set to [mem 0x48000000-0x48000fff] (PCI address [0x48000000-0x48000fff])
[   27.888586] pci 0000:02:00.1: BAR 0: assigned [mem 0x48001000-0x48001fff]
[   27.888593] pci 0000:02:00.1: BAR 0: set to [mem 0x48001000-0x48001fff] (PCI address [0x48001000-0x48001fff])
[   27.888599] pci 0000:02:00.2: BAR 0: assigned [mem 0x48002000-0x480020ff]
[   27.888606] pci 0000:02:00.2: BAR 0: set to [mem 0x48002000-0x480020ff] (PCI address [0x48002000-0x480020ff])
[   27.888872] ohci_hcd 0000:02:00.0: enabling device (0000 -> 0002)
[   27.888895] ohci_hcd 0000:02:00.0: PCI INT A -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   27.888939] ohci_hcd 0000:02:00.0: setting latency timer to 64
[   27.888945] ohci_hcd 0000:02:00.0: OHCI Host Controller
[   27.889351] ohci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 4
[   27.889400] ohci_hcd 0000:02:00.0: irq 11, io mem 0x48000000
[   27.912917] init: failsafe main process (682) killed by TERM signal
[   28.123586] hub 4-0:1.0: USB hub found
[   28.123621] hub 4-0:1.0: 3 ports detected
[   28.125196] ohci_hcd 0000:02:00.1: enabling device (0000 -> 0002)
[   28.125220] ohci_hcd 0000:02:00.1: PCI INT B -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   28.125282] ohci_hcd 0000:02:00.1: setting latency timer to 64
[   28.125288] ohci_hcd 0000:02:00.1: OHCI Host Controller
[   28.125689] ohci_hcd 0000:02:00.1: new USB bus registered, assigned bus number 5
[   28.125740] ohci_hcd 0000:02:00.1: irq 11, io mem 0x48001000
[   28.222861] hub 5-0:1.0: USB hub found
[   28.222879] hub 5-0:1.0: 2 ports detected
[   28.224624] ehci_hcd 0000:02:00.2: enabling device (0000 -> 0002)
[   28.224649] ehci_hcd 0000:02:00.2: PCI INT C -> Link[C0C6] -> GSI 11 (level, low) -> IRQ 11
[   28.224701] ehci_hcd 0000:02:00.2: EHCI Host Controller
[   28.224937] ehci_hcd 0000:02:00.2: new USB bus registered, assigned bus number 6
[   28.248162] ehci_hcd 0000:02:00.2: irq 11, io mem 0x48002000
[   28.260124] ehci_hcd 0000:02:00.2: USB 2.0 started, EHCI 1.00
[   28.260556] hub 6-0:1.0: USB hub found
[   28.260568] hub 6-0:1.0: 5 ports detected
[   28.343359] type=1400 audit(1379681571.474:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=786 comm="apparmor_parser"
[   28.344188] type=1400 audit(1379681571.478:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=786 comm="apparmor_parser"
[   28.362290] type=1400 audit(1379681571.494:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=788 comm="apparmor_parser"
[   28.369321] type=1400 audit(1379681571.502:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=788 comm="apparmor_parser"
[   29.003008] [drm] radeon: ring at 0x00000000A4001000
[   29.003037] [drm] ring test succeeded in 1 usecs
[   29.003462] [drm] radeon: ib pool ready.
[   29.003613] [drm] ib test succeeded in 0 usecs
[   29.009225] [drm] Panel ID String: 1024x768                
[   29.009233] [drm] Panel Size 1024x768
[   29.021740] [drm] radeon legacy LVDS backlight initialized
[   29.023748] [drm] No TV DAC info found in BIOS
[   29.025637] [drm] Radeon Display Connectors
[   29.025643] [drm] Connector 0:
[   29.025647] [drm]   VGA
[   29.025652] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[   29.025655] [drm]   Encoders:
[   29.025659] [drm]     CRT1: INTERNAL_DAC1
[   29.025662] [drm] Connector 1:
[   29.025664] [drm]   LVDS
[   29.025666] [drm]   Encoders:
[   29.025669] [drm]     LCD1: INTERNAL_LVDS
[   29.025672] [drm] Connector 2:
[   29.025674] [drm]   S-video
[   29.025676] [drm]   Encoders:
[   29.025679] [drm]     TV1: INTERNAL_DAC2
[   29.066890] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   29.097991] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177
[   29.195473] [drm] fb mappable at 0x98040000
[   29.195482] [drm] vram apper at 0x98000000
[   29.195485] [drm] size 3145728
[   29.195488] [drm] fb depth is 24
[   29.195491] [drm]    pitch is 4096
[   29.200981] fbcon: radeondrmfb (fb0) is primary device
[   29.202339] Console: switching to colour frame buffer device 128x48
[   29.202415] fb0: radeondrmfb frame buffer device
[   29.202419] drm: registered panic notifier
[   29.219776]  0x1f0-0x1f7 0x200-0x207 0x220-0x22f 0x330-0x337 0x370-0x37f 0x388-0x38f
[   29.225990] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x170-0x177 0x1f0-0x1f7 0x200-0x207 0x220-0x22f
[   29.248126] [drm] Initialized radeon 2.12.0 20080528 for 0000:01:05.0 on minor 0
[   29.266265] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.266275] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266280] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.266285] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266289] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.266294] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266298] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.266303] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266307] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.266312] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266316] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.266321] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266325] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.266330] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266334] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.266339] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266343] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.266348] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266352] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.266357] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266361] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.266366] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266370] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.266375] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266379] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.266384] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   29.266388] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   29.266393] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (600 mBi, 2000 mBm)
[   29.301426]  excluding 0x3e8-0x3ff 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7 0x330-0x337 0x370-0x37f 0x388-0x38f
[   29.310148] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3e8-0x3ff 0x408-0x40f 0x480-0x48f 0x4d0-0x4d7
[   29.311028] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff:
[   29.322789] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   29.323590] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   29.344857] init: alsa-restore main process (880) terminated with status 19
[   29.432916]  clean.
[   29.433040] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   29.450571] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   29.450616] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa04fffff
[   29.450661] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   29.450700] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   29.517297]  clean.
[   29.517429] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   29.517473] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa04fffff
[   29.517519] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: clean.
[   29.517559] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   29.550143] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   29.550154] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550159] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   29.550164] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550169] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   29.550174] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550178] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   29.550183] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550187] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   29.550192] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550196] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   29.550201] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550205] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   29.550210] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550214] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   29.550219] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550223] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   29.550228] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550232] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   29.550237] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550241] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.550246] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550250] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.550255] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.550259] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.550264] cfg80211: 2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.550268] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[   29.550273] cfg80211: 2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.550279] cfg80211: World regulatory domain updated:
[   29.550283] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.550288] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550293] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.550297] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   29.550302] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   29.550306] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

```
Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 21:43:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 21:43:24 Compaq kernel: [    0.033926] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 21:43:24 Compaq kernel: [    1.000104] PM: Hibernation image not present or could not be loaded.
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:23:07 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:23:07 Compaq kernel: [    0.033784] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:23:07 Compaq kernel: [    1.103971] PM: Hibernation image not present or could not be loaded.
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:27:13 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:27:13 Compaq kernel: [    0.033785] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:27:13 Compaq kernel: [    1.101704] PM: Hibernation image not present or could not be loaded.
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:35:48 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:35:48 Compaq kernel: [    0.029788] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:35:48 Compaq kernel: [    1.097048] PM: Hibernation image not present or could not be loaded.
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:37:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:37:46 Compaq kernel: [    0.029784] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:37:46 Compaq kernel: [    1.104826] PM: Hibernation image not present or could not be loaded.
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:40:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:40:09 Compaq kernel: [    0.029791] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:40:09 Compaq kernel: [    1.101065] PM: Hibernation image not present or could not be loaded.
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:41:27 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:41:27 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:41:27 Compaq kernel: [    1.092148] PM: Hibernation image not present or could not be loaded.
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 17 23:47:09 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 17 23:47:09 Compaq kernel: [    0.029782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 17 23:47:09 Compaq kernel: [    1.103811] PM: Hibernation image not present or could not be loaded.
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 17:46:40 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 17:46:40 Compaq kernel: [    0.029791] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 17:46:40 Compaq kernel: [    1.099818] PM: Hibernation image not present or could not be loaded.
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 20:10:14 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 20:10:14 Compaq kernel: [    0.029783] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 20:10:14 Compaq kernel: [    1.097037] PM: Hibernation image not present or could not be loaded.
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 21:58:19 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 21:58:19 Compaq kernel: [    0.033793] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 21:58:19 Compaq kernel: [    1.101104] PM: Hibernation image not present or could not be loaded.
Sep 18 22:02:48 Compaq kernel: [  295.310964] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 18 22:02:48 Compaq kernel: [  295.310973] PM: Basic memory bitmaps created
Sep 18 22:03:57 Compaq kernel: [  295.310976] PM: Syncing filesystems ... done.
Sep 18 22:03:57 Compaq kernel: [  295.528191] PM: Preallocating image memory... done (allocated 136646 pages)
Sep 18 22:03:57 Compaq kernel: [  295.788864] PM: Allocated 546584 kbytes in 0.26 seconds (2102.24 MB/s)
Sep 18 22:03:57 Compaq kernel: [  296.002283] PM: freeze of drv:sd dev:0:0:0:0 complete after 176.707 msecs
Sep 18 22:03:57 Compaq kernel: [  296.002318] PM: freeze of drv:scsi dev:target0:0:0 complete after 176.625 msecs
Sep 18 22:03:57 Compaq kernel: [  296.002358] PM: freeze of drv:scsi dev:host0 complete after 176.635 msecs
Sep 18 22:03:57 Compaq kernel: [  296.012852] PM: freeze of drv:radeon dev:0000:01:05.0 complete after 181.797 msecs
Sep 18 22:03:57 Compaq kernel: [  296.170751] PM: freeze of drv:tg3 dev:0000:00:13.0 complete after 298.077 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620242] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 1617.932 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620256] PM: freeze of drv: dev:pci0000:00 complete after 1616.766 msecs
Sep 18 22:03:57 Compaq kernel: [  297.620267] PM: freeze of devices complete after 1815.683 msecs
Sep 18 22:03:57 Compaq kernel: [  297.621287] PM: late freeze of devices complete after 1.013 msecs
Sep 18 22:03:57 Compaq kernel: [  297.621931] PM: Saving platform NVS memory
Sep 18 22:03:57 Compaq kernel: [  297.622181] PM: Creating hibernation image:
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Need to copy 93323 pages
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Normal pages needed: 84157 + 1024, available pages: 143037
Sep 18 22:03:57 Compaq kernel: [  297.624214] PM: Restoring platform NVS memory
Sep 18 22:03:57 Compaq kernel: [  298.432884] PM: early restore of devices complete after 712.531 msecs
Sep 18 22:03:57 Compaq kernel: [  298.779205] PM: restore of drv:tg3 dev:0000:00:13.0 complete after 303.038 msecs
Sep 18 22:03:57 Compaq kernel: [  298.900641] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 424.579 msecs
Sep 18 22:03:57 Compaq kernel: [  298.930423] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 457.279 msecs
Sep 18 22:03:57 Compaq kernel: [  298.933337] PM: restore of drv: dev:platform complete after 460.668 msecs
Sep 18 22:03:57 Compaq kernel: [  299.001898] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 525.762 msecs
Sep 18 22:03:57 Compaq kernel: [  299.061491] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 124.655 msecs
Sep 18 22:03:57 Compaq kernel: [  299.112219] PM: restore of drv:radeon dev:0000:01:05.0 complete after 332.990 msecs
Sep 18 22:03:57 Compaq kernel: [  299.112242] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 175.290 msecs
Sep 18 22:03:57 Compaq kernel: [  299.156388] PM: restore of drv:battery dev:PNP0C0A:00 complete after 222.500 msecs
Sep 18 22:03:57 Compaq kernel: [  299.160370] PM: restore of drv:sd dev:0:0:0:0 complete after 223.843 msecs
Sep 18 22:03:57 Compaq kernel: [  299.160416] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 223.767 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232090] PM: restore of drv:hub dev:3-0:1.0 complete after 296.153 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232104] PM: restore of drv: dev:ep_00 complete after 296.114 msecs
Sep 18 22:03:57 Compaq kernel: [  299.232112] PM: restore of drv: dev:ep_81 complete after 296.151 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244063] PM: restore of drv:hub dev:6-0:1.0 complete after 307.024 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244076] PM: restore of drv: dev:ep_00 complete after 306.984 msecs
Sep 18 22:03:57 Compaq kernel: [  299.244085] PM: restore of drv: dev:ep_81 complete after 307.020 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248059] PM: restore of drv:hub dev:2-0:1.0 complete after 312.235 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248071] PM: restore of drv: dev:ep_00 complete after 312.191 msecs
Sep 18 22:03:57 Compaq kernel: [  299.248079] PM: restore of drv: dev:ep_81 complete after 312.228 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256070] PM: restore of drv:hub dev:4-0:1.0 complete after 319.318 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256083] PM: restore of drv: dev:ep_00 complete after 319.274 msecs
Sep 18 22:03:57 Compaq kernel: [  299.256091] PM: restore of drv: dev:ep_81 complete after 319.310 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296063] PM: restore of drv:hub dev:5-0:1.0 complete after 359.154 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296075] PM: restore of drv: dev:ep_00 complete after 359.153 msecs
Sep 18 22:03:57 Compaq kernel: [  299.296085] PM: restore of drv: dev:ep_81 complete after 359.171 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336059] PM: restore of drv:hub dev:1-0:1.0 complete after 465.313 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336073] PM: restore of drv: dev:ep_00 complete after 400.314 msecs
Sep 18 22:03:57 Compaq kernel: [  299.336104] PM: restore of drv: dev:ep_81 complete after 400.413 msecs
Sep 18 22:03:57 Compaq kernel: [  299.580046] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 1107.232 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599320] PM: restore of drv:usb dev:1-1:1.0 complete after 663.127 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599369] PM: restore of drv: dev:ep_00 complete after 662.897 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599378] PM: restore of drv: dev:ep_83 complete after 663.154 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599387] PM: restore of drv: dev:ep_04 complete after 663.136 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599396] PM: restore of drv: dev:ep_05 complete after 663.119 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599405] PM: restore of drv: dev:ep_06 complete after 663.100 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599413] PM: restore of drv: dev:ep_07 complete after 663.082 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599421] PM: restore of drv: dev:ep_89 complete after 663.062 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599431] PM: restore of drv: dev:ep_0a complete after 663.045 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599439] PM: restore of drv: dev:ep_0b complete after 663.024 msecs
Sep 18 22:03:57 Compaq kernel: [  299.599448] PM: restore of drv: dev:ep_0c complete after 663.005 msecs
Sep 18 22:03:57 Compaq kernel: [  299.728146] PM: restore of devices complete after 1257.420 msecs
Sep 18 22:03:57 Compaq kernel: [  300.016377] PM: Image restored successfully.
Sep 18 22:03:57 Compaq kernel: [  300.046631] PM: Basic memory bitmaps freed
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:07:06 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:07:06 Compaq kernel: [    0.029793] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:07:06 Compaq kernel: [    1.038553] PM: Hibernation image not present or could not be loaded.
Sep 18 22:08:14 Compaq kernel: [   93.892782] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 18 22:08:14 Compaq kernel: [   93.892791] PM: Basic memory bitmaps created
Sep 18 22:09:17 Compaq kernel: [   93.892794] PM: Syncing filesystems ... done.
Sep 18 22:09:17 Compaq kernel: [   94.124175] PM: Preallocating image memory... done (allocated 136646 pages)
Sep 18 22:09:17 Compaq kernel: [   94.388209] PM: Allocated 546584 kbytes in 0.26 seconds (2102.24 MB/s)
Sep 18 22:09:17 Compaq kernel: [   94.702697] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 252.759 msecs
Sep 18 22:09:17 Compaq kernel: [   94.702711] PM: freeze of drv: dev:pci0000:00 complete after 252.547 msecs
Sep 18 22:09:17 Compaq kernel: [   94.702720] PM: freeze of devices complete after 298.170 msecs
Sep 18 22:09:17 Compaq kernel: [   94.703740] PM: late freeze of devices complete after 1.013 msecs
Sep 18 22:09:17 Compaq kernel: [   94.704412] PM: Saving platform NVS memory
Sep 18 22:09:17 Compaq kernel: [   94.704665] PM: Creating hibernation image:
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Need to copy 83329 pages
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Normal pages needed: 74341 + 1024, available pages: 152853
Sep 18 22:09:17 Compaq kernel: [   94.708052] PM: Restoring platform NVS memory
Sep 18 22:09:17 Compaq kernel: [   95.512881] PM: early restore of devices complete after 712.522 msecs
Sep 18 22:09:17 Compaq kernel: [   95.673584] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 124.482 msecs
Sep 18 22:09:17 Compaq kernel: [   95.703352] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 154.283 msecs
Sep 18 22:09:17 Compaq kernel: [   95.703422] PM: restore of drv: dev:platform complete after 154.833 msecs
Sep 18 22:09:17 Compaq kernel: [   95.783721] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 231.832 msecs
Sep 18 22:09:17 Compaq kernel: [   95.813507] PM: restore of drv:ohci_hcd dev:0000:02:00.0 complete after 108.116 msecs
Sep 18 22:09:17 Compaq kernel: [   95.843282] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 137.735 msecs
Sep 18 22:09:17 Compaq kernel: [   95.894088] PM: restore of drv:radeon dev:0000:01:05.0 complete after 341.921 msecs
Sep 18 22:09:17 Compaq kernel: [   95.894118] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 188.425 msecs
Sep 18 22:09:17 Compaq kernel: [   95.935024] PM: restore of drv:battery dev:PNP0C0A:00 complete after 231.020 msecs
Sep 18 22:09:17 Compaq kernel: [   95.938057] PM: restore of drv:sd dev:0:0:0:0 complete after 232.797 msecs
Sep 18 22:09:17 Compaq kernel: [   95.938097] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 232.735 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012095] PM: restore of drv:hub dev:3-0:1.0 complete after 307.274 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012108] PM: restore of drv: dev:ep_00 complete after 307.233 msecs
Sep 18 22:09:17 Compaq kernel: [   96.012116] PM: restore of drv: dev:ep_81 complete after 307.271 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024063] PM: restore of drv:hub dev:6-0:1.0 complete after 318.251 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024076] PM: restore of drv: dev:ep_00 complete after 318.222 msecs
Sep 18 22:09:17 Compaq kernel: [   96.024084] PM: restore of drv: dev:ep_81 complete after 318.263 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028081] PM: restore of drv:hub dev:2-0:1.0 complete after 384.388 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028096] PM: restore of drv: dev:ep_00 complete after 323.336 msecs
Sep 18 22:09:17 Compaq kernel: [   96.028103] PM: restore of drv: dev:ep_81 complete after 323.421 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036070] PM: restore of drv:hub dev:4-0:1.0 complete after 330.602 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036081] PM: restore of drv: dev:ep_00 complete after 330.562 msecs
Sep 18 22:09:17 Compaq kernel: [   96.036088] PM: restore of drv: dev:ep_81 complete after 330.595 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088065] PM: restore of drv:hub dev:5-0:1.0 complete after 382.452 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088078] PM: restore of drv: dev:ep_00 complete after 382.413 msecs
Sep 18 22:09:17 Compaq kernel: [   96.088086] PM: restore of drv: dev:ep_81 complete after 382.448 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116057] PM: restore of drv:hub dev:1-0:1.0 complete after 472.402 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116072] PM: restore of drv: dev:ep_00 complete after 472.398 msecs
Sep 18 22:09:17 Compaq kernel: [   96.116102] PM: restore of drv: dev:ep_81 complete after 472.438 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391129] PM: restore of drv:usb dev:1-1:1.0 complete after 686.199 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391178] PM: restore of drv: dev:ep_00 complete after 685.974 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391188] PM: restore of drv: dev:ep_83 complete after 686.232 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391196] PM: restore of drv: dev:ep_04 complete after 686.213 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391205] PM: restore of drv: dev:ep_05 complete after 686.193 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391213] PM: restore of drv: dev:ep_06 complete after 686.170 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391223] PM: restore of drv: dev:ep_07 complete after 686.152 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391231] PM: restore of drv: dev:ep_89 complete after 686.134 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391241] PM: restore of drv: dev:ep_0a complete after 686.116 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391249] PM: restore of drv: dev:ep_0b complete after 686.098 msecs
Sep 18 22:09:17 Compaq kernel: [   96.391257] PM: restore of drv: dev:ep_0c complete after 686.080 msecs
Sep 18 22:09:17 Compaq kernel: [   96.392045] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 843.324 msecs
Sep 18 22:09:17 Compaq kernel: [   96.520171] PM: restore of devices complete after 971.924 msecs
Sep 18 22:09:17 Compaq kernel: [   96.828836] PM: Image restored successfully.
Sep 18 22:09:17 Compaq kernel: [   96.903572] PM: Basic memory bitmaps freed
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:22:31 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:22:31 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:22:31 Compaq kernel: [    1.107872] PM: Hibernation image not present or could not be loaded.
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:26:35 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:26:35 Compaq kernel: [    0.033786] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:26:35 Compaq kernel: [    1.100991] PM: Hibernation image not present or could not be loaded.
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:28:57 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:28:57 Compaq kernel: [    0.029787] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:28:57 Compaq kernel: [    1.101105] PM: Hibernation image not present or could not be loaded.
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:48:08 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:48:08 Compaq kernel: [    0.029789] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:48:08 Compaq kernel: [    0.988271] PM: Hibernation image not present or could not be loaded.
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:50:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:50:49 Compaq kernel: [    0.040495] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:50:49 Compaq kernel: [    1.087600] PM: Hibernation image not present or could not be loaded.
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:56:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:56:49 Compaq kernel: [    0.033782] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:56:49 Compaq kernel: [    1.109377] PM: Hibernation image not present or could not be loaded.
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 22:58:56 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 22:58:56 Compaq kernel: [    0.033771] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 22:58:56 Compaq kernel: [    1.038893] PM: Hibernation image not present or could not be loaded.
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 18 23:16:03 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 18 23:16:03 Compaq kernel: [    0.033781] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 18 23:16:03 Compaq kernel: [    0.976427] PM: Hibernation image not present or could not be loaded.
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:09:46 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:09:46 Compaq kernel: [    0.029799] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:09:46 Compaq kernel: [    0.968474] PM: Hibernation image not present or could not be loaded.
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:46:50 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:46:50 Compaq kernel: [    0.029787] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:46:50 Compaq kernel: [    0.963342] PM: Hibernation image not present or could not be loaded.
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:50:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:50:26 Compaq kernel: [    0.036423] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:50:26 Compaq kernel: [    1.103797] PM: Hibernation image not present or could not be loaded.
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 19 22:53:55 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 19 22:53:55 Compaq kernel: [    0.033789] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 19 22:53:55 Compaq kernel: [    1.107783] PM: Hibernation image not present or could not be loaded.
Sep 19 23:32:56 Compaq kernel: [ 2381.224499] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 19 23:32:56 Compaq kernel: [ 2381.224508] PM: Basic memory bitmaps created
Sep 20 11:35:25 Compaq kernel: [ 2381.224512] PM: Syncing filesystems ... done.
Sep 20 11:35:25 Compaq kernel: [ 2381.520178] PM: Preallocating image memory... done (allocated 136638 pages)
Sep 20 11:35:25 Compaq kernel: [ 2381.918437] PM: Allocated 546552 kbytes in 0.39 seconds (1401.41 MB/s)
Sep 20 11:35:25 Compaq kernel: [ 2382.201635] PM: freeze of drv:sd dev:0:0:0:0 complete after 268.586 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.201656] PM: freeze of drv:scsi dev:target0:0:0 complete after 268.590 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.201675] PM: freeze of drv:scsi dev:host0 complete after 263.757 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.201806] PM: freeze of drv:pata_ali dev:0000:00:10.0 complete after 223.181 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.227499] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 248.926 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.227511] PM: freeze of drv: dev:pci0000:00 complete after 245.532 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.227519] PM: freeze of devices complete after 294.801 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.228567] PM: late freeze of devices complete after 1.041 msecs
Sep 20 11:35:25 Compaq kernel: [ 2382.229225] PM: Saving platform NVS memory
Sep 20 11:35:25 Compaq kernel: [ 2382.229477] PM: Creating hibernation image:
Sep 20 11:35:25 Compaq kernel: [ 2382.232016] PM: Need to copy 96476 pages
Sep 20 11:35:25 Compaq kernel: [ 2382.232016] PM: Normal pages needed: 90695 + 1024, available pages: 136499
Sep 20 11:35:25 Compaq kernel: [ 2382.232016] PM: Restoring platform NVS memory
Sep 20 11:35:25 Compaq kernel: [ 2383.036851] PM: early restore of devices complete after 712.489 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.203951] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 124.240 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.233735] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 154.306 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.238068] PM: restore of drv: dev:platform complete after 159.160 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.312113] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 229.671 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.362918] PM: restore of drv:radeon dev:0000:01:05.0 complete after 280.392 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.401739] PM: restore of drv:battery dev:PNP0C0A:00 complete after 163.061 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.475888] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 112.167 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.496078] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 132.208 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504109] PM: restore of drv:hub dev:2-0:1.0 complete after 330.054 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504124] PM: restore of drv: dev:ep_00 complete after 265.089 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504133] PM: restore of drv:hub dev:3-0:1.0 complete after 191.890 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504147] PM: restore of drv: dev:ep_00 complete after 141.124 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504157] PM: restore of drv: dev:ep_81 complete after 266.273 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.504165] PM: restore of drv: dev:ep_81 complete after 141.150 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.552264] PM: restore of drv:usb dev:4-0:1.0 complete after 188.632 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.552273] PM: restore of drv: dev:ep_00 complete after 188.582 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.552282] PM: restore of drv: dev:ep_81 complete after 188.621 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.564063] PM: restore of drv:hub dev:5-0:1.0 complete after 200.272 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.564076] PM: restore of drv: dev:ep_00 complete after 200.233 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.564086] PM: restore of drv: dev:ep_81 complete after 200.270 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.600069] PM: restore of drv:hub dev:1-0:1.0 complete after 426.051 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.600083] PM: restore of drv: dev:ep_00 complete after 426.048 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.600117] PM: restore of drv: dev:ep_81 complete after 426.091 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.628084] PM: restore of drv:hub dev:6-0:1.0 complete after 264.135 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.628096] PM: restore of drv: dev:ep_00 complete after 264.092 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.628106] PM: restore of drv: dev:ep_81 complete after 264.129 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875126] PM: restore of drv:usb dev:1-1:1.0 complete after 512.040 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875176] PM: restore of drv: dev:ep_00 complete after 511.784 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875185] PM: restore of drv: dev:ep_83 complete after 512.073 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875194] PM: restore of drv: dev:ep_04 complete after 512.030 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875203] PM: restore of drv: dev:ep_05 complete after 512.011 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875213] PM: restore of drv: dev:ep_06 complete after 511.992 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875221] PM: restore of drv: dev:ep_07 complete after 511.972 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875230] PM: restore of drv: dev:ep_89 complete after 511.950 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875239] PM: restore of drv: dev:ep_0a complete after 511.928 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875248] PM: restore of drv: dev:ep_0b complete after 511.909 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.875257] PM: restore of drv: dev:ep_0c complete after 511.892 msecs
Sep 20 11:35:25 Compaq kernel: [ 2383.920044] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 840.957 msecs
Sep 20 11:35:25 Compaq kernel: [ 2384.004161] PM: restore of devices complete after 925.625 msecs
Sep 20 11:35:25 Compaq kernel: [ 2384.312813] PM: Image restored successfully.
Sep 20 11:35:25 Compaq kernel: [ 2384.373344] PM: Basic memory bitmaps freed
Sep 20 11:40:01 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:40:01 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:40:01 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:40:01 Compaq kernel: [    0.029790] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 20 11:40:01 Compaq kernel: [    1.104490] PM: Hibernation image not present or could not be loaded.
Sep 20 11:43:05 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:43:05 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:43:05 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:43:05 Compaq kernel: [    0.029788] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 20 11:43:05 Compaq kernel: [    1.101016] PM: Hibernation image not present or could not be loaded.
Sep 20 11:45:16 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:45:16 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:45:16 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:45:16 Compaq kernel: [    0.040539] PM: Registering ACPI NVS region at 3dff0c00 (46080 bytes)
Sep 20 11:45:16 Compaq kernel: [    1.108628] PM: Hibernation image not present or could not be loaded.
Sep 20 11:49:15 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:49:15 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:49:15 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:49:15 Compaq kernel: [    0.033784] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 11:49:15 Compaq kernel: [    1.115872] PM: Hibernation image not present or could not be loaded.
Sep 20 11:51:29 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:51:29 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:51:29 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:51:29 Compaq kernel: [    0.029779] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 11:51:29 Compaq kernel: [    1.099562] PM: Hibernation image not present or could not be loaded.
Sep 20 11:52:38 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:52:38 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:52:38 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:52:38 Compaq kernel: [    0.033783] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 11:52:38 Compaq kernel: [    1.039645] PM: Hibernation image not present or could not be loaded.
Sep 20 11:54:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 11:54:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 11:54:24 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 11:54:24 Compaq kernel: [    0.033779] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 11:54:24 Compaq kernel: [    0.971446] PM: Hibernation image not present or could not be loaded.
Sep 20 12:13:37 Compaq kernel: [ 1179.374911] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Sep 20 12:13:37 Compaq kernel: [ 1179.374921] PM: Basic memory bitmaps created
Sep 20 14:43:16 Compaq kernel: [ 1179.374924] PM: Syncing filesystems ... done.
Sep 20 14:43:16 Compaq kernel: [ 1179.616153] PM: Preallocating image memory... done (allocated 132180 pages)
Sep 20 14:43:16 Compaq kernel: [ 1180.303048] PM: Allocated 528720 kbytes in 0.68 seconds (777.52 MB/s)
Sep 20 14:43:16 Compaq kernel: [ 1180.493404] PM: freeze of drv:radeon dev:0000:01:05.0 complete after 113.340 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.623090] PM: freeze of drv:sd dev:0:0:0:0 complete after 254.795 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.623111] PM: freeze of drv:scsi dev:target0:0:0 complete after 254.799 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.623129] PM: freeze of drv:scsi dev:host0 complete after 251.061 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.623270] PM: freeze of drv:pata_ali dev:0000:00:10.0 complete after 199.114 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.711648] PM: freeze of drv:ehci_hcd dev:0000:00:12.2 complete after 289.854 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.711661] PM: freeze of drv: dev:pci0000:00 complete after 283.541 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.711669] PM: freeze of devices complete after 347.095 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.712720] PM: late freeze of devices complete after 1.044 msecs
Sep 20 14:43:16 Compaq kernel: [ 1180.713716] PM: Saving platform NVS memory
Sep 20 14:43:16 Compaq kernel: [ 1180.713969] PM: Creating hibernation image:
Sep 20 14:43:16 Compaq kernel: [ 1180.716016] PM: Need to copy 81995 pages
Sep 20 14:43:16 Compaq kernel: [ 1180.716016] PM: Normal pages needed: 79160 + 1024, available pages: 148034
Sep 20 14:43:16 Compaq kernel: [ 1180.716016] PM: Restoring platform NVS memory
Sep 20 14:43:16 Compaq kernel: [ 1181.520854] PM: early restore of devices complete after 712.494 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.680711] PM: restore of drv:ohci_hcd dev:0000:00:12.1 complete after 124.254 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.710492] PM: restore of drv:ohci_hcd dev:0000:00:12.0 complete after 154.076 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.710559] PM: restore of drv: dev:platform complete after 154.701 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.788620] PM: restore of drv:ehci_hcd dev:0000:00:12.2 complete after 229.402 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.818423] PM: restore of drv:ohci_hcd dev:0000:02:00.0 complete after 105.849 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.848210] PM: restore of drv:ohci_hcd dev:0000:02:00.1 complete after 135.433 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.899038] PM: restore of drv:radeon dev:0000:01:05.0 complete after 339.749 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.899276] PM: restore of drv:ehci_hcd dev:0000:02:00.2 complete after 186.281 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.937889] PM: restore of drv:battery dev:PNP0C0A:00 complete after 226.734 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.941818] PM: restore of drv:sd dev:0:0:0:0 complete after 229.370 msecs
Sep 20 14:43:16 Compaq kernel: [ 1181.941857] PM: restore of drv:scsi_device dev:0:0:0:0 complete after 229.309 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.016142] PM: restore of drv:hub dev:3-0:1.0 complete after 304.570 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.016157] PM: restore of drv: dev:ep_00 complete after 304.496 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.016165] PM: restore of drv:hub dev:2-0:1.0 complete after 365.357 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.016179] PM: restore of drv: dev:ep_00 complete after 304.676 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.016188] PM: restore of drv: dev:ep_81 complete after 304.559 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.016196] PM: restore of drv: dev:ep_81 complete after 305.642 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.028062] PM: restore of drv:hub dev:6-0:1.0 complete after 314.981 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.028075] PM: restore of drv: dev:ep_00 complete after 314.941 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.028083] PM: restore of drv: dev:ep_81 complete after 314.976 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.040073] PM: restore of drv:hub dev:4-0:1.0 complete after 327.380 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.040084] PM: restore of drv: dev:ep_00 complete after 327.336 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.040092] PM: restore of drv: dev:ep_81 complete after 327.373 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.080065] PM: restore of drv:hub dev:5-0:1.0 complete after 367.217 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.080078] PM: restore of drv: dev:ep_00 complete after 367.109 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.080086] PM: restore of drv: dev:ep_81 complete after 367.145 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.120061] PM: restore of drv:hub dev:1-0:1.0 complete after 469.288 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.120075] PM: restore of drv: dev:ep_00 complete after 469.285 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.120108] PM: restore of drv: dev:ep_81 complete after 469.326 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.380045] PM: restore of drv:snd_ali5451 dev:0000:00:06.0 complete after 824.059 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383379] PM: restore of drv:usb dev:1-1:1.0 complete after 671.662 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383427] PM: restore of drv: dev:ep_00 complete after 671.424 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383435] PM: restore of drv: dev:ep_83 complete after 671.693 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383443] PM: restore of drv: dev:ep_04 complete after 671.673 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383451] PM: restore of drv: dev:ep_05 complete after 671.653 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383458] PM: restore of drv: dev:ep_06 complete after 671.633 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383467] PM: restore of drv: dev:ep_07 complete after 671.614 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383476] PM: restore of drv: dev:ep_89 complete after 671.594 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383484] PM: restore of drv: dev:ep_0a complete after 671.574 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383493] PM: restore of drv: dev:ep_0b complete after 671.544 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.383501] PM: restore of drv: dev:ep_0c complete after 671.526 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.512151] PM: restore of devices complete after 956.636 msecs
Sep 20 14:43:16 Compaq kernel: [ 1182.801282] PM: Image restored successfully.
Sep 20 14:43:16 Compaq kernel: [ 1182.852841] PM: Basic memory bitmaps freed
Sep 20 14:48:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 14:48:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 14:48:26 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 14:48:26 Compaq kernel: [    0.036002] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 14:48:26 Compaq kernel: [    1.004052] PM: Hibernation image not present or could not be loaded.
Sep 20 14:49:41 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 14:49:41 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 14:49:41 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 14:49:41 Compaq kernel: [    0.036002] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 14:49:41 Compaq kernel: [    1.106349] PM: Hibernation image not present or could not be loaded.
Sep 20 14:52:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Sep 20 14:52:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Sep 20 14:52:49 Compaq kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Sep 20 14:52:49 Compaq kernel: [    0.036002] PM: Registering ACPI NVS region at 3bff0c00 (46080 bytes)
Sep 20 14:52:49 Compaq kernel: [    1.094709] PM: Hibernation image not present or could not be loaded.
```

---

### Post by Toz on 2013-09-20
> [    0.000000] Local APIC disabled by BIOS -- reenabling.
[    0.000000] Found and enabled local APIC!
The good news is that local apic is now enabled on your device.

The bad news is, still no suspend.

Can you try s2ram? Its an older alternative to kernel suspend. To do so, install the **uswsusp** package, then run:
```
sudo s2ram
```
...if you get a message about your system not being whitelisted, then run:
```
sudo s2ram -f
```
Lets see if s2ram works. If it doesn't, you can just uninstall it.

After your attempt, post back the log files again.

---

