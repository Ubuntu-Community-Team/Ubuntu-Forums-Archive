---
title: "Hibernate doesn't power off"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by Wadcutter on 2011-10-04
I tried following D Slender's similar problem in his post in General Help, May 30 2011, but was afraid to try some of the suggestions since his system and mine are different.That thread seems to have died, so I am posting anew.

I'm running 64-bit Ubuntu 10.04 on a homemade desktop computer.(AMD Athlon 64-3700, 2 GB memory, 2-250 GB WD HDs, EVGA GeForce 8400GS video) It has two hard drives with dual boot option- Ubuntu on one drive and Windows on the other. Windows hibernates correctly and powers down the computer. However, Ubuntu hibernates, but only blackens and dims the monitor, completely shuts off the mouse and keyboard, but leaves the computer running (power supply & light on, fans running). To resume, I have to hit the reset button, which goes to re-boot, then gives me the log-in window (user name shown-asks for password) and then I am returned to where I left off. So it seems to be saving everything to the swap file (actually a 6 GB swap partition on the same drive), but it just doesn't power down.

The May 30 thread suggested issues with ACPI (I'm ignorant what that is) and attempts to tweak it seemed to have negative consequences with  mice, touchpads, power buttons etc.

I will be grateful for anyone interested in walking me thru some diagnostics and tweaking with the goal of getting hibernate to also power off the box without destroying anything else. I'm a novice Ubuntu user, but not a novice computer user; the Linux commands make me a little nervous since I don't know what they mean or how they are likely to affect my system. I'm happy to try any that are easily reversible but would be more comfortable if I could actually diagnose the problem before applying a cure. I hope that doesn't make me appear fussy or ungrateful for any help that might come- I will be appreciative.

---

### Post by audiomick on 2011-10-04
Here is a Wiki page about ACPI

[http://en.wikipedia.org/wiki/Acpi](http://en.wikipedia.org/wiki/Acpi)

To find out what commands do, you can always look at the man pages

[https://help.ubuntu.com/community/man](https://help.ubuntu.com/community/man)

If some says do 
```
some_cryptic_command
```

you can find out what it does with

```
man some_cryptic_command
```

The man pages themselves are often a bit cryptic too, but you can usually figure out what the gist of it is. Don't be scared of the terminal. It is your friend. ;)

Sorry I can't help you more specifically.

---

### Post by Toz on 2011-10-04
Also, have a look at the **/var/log/pm-suspend.log** file. It may provide some hints.

In addition, running the following command in a terminal may yield some diagnostic information:
```
cat /var/log/dmesg* | grep PM:
```

---

### Post by Wadcutter on 2011-10-05
The ACPI discussion was interesting, but a little too advanced for me to make any use of. The info about commands will be very useful for the future and is something that I didn't know. Thanks.

I found the suspend log, but don't know enough for it to help me. It did seem to show a lot of "hibernate-success" so I think it is telling me that my computer hibernates just fine -in the sense that it saves and shuts down operating but it just doesn't power off the power supply. There also seems to be little difference on my computer between "suspend" and "hibernate" Both of them blank and dim the monitor and shut down the keyboard and mouse, but the power still stays on. With "suspend", I just have to reboot from the beginning to resume. It's almost like it didn't exist. Hibernate reboots partially but takes me back to programs that were running when I hibernated.

The command you mentioned seemed to give info more about memory than anything else.

Thanks for suggestions.

---

### Post by Toz on 2011-10-05
Sorry, try the following command instead:
```
cat /var/log/syslog | grep PM:
```
Perhaps you can post back the results.

---

### Post by Wadcutter on 2011-10-06
> **Toz said:**
> Sorry, try the following command instead:
```
cat /var/log/syslog | grep PM:
```
Perhaps you can post back the results.
I don't get anything from "cat /var/log/syslog | grep PM:" Did I miss something?

---

### Post by Toz on 2011-10-06
How about:
```
cat /var/log/syslog* | grep PM:
```
(in case the log file rotated)

If still nothing, try another hibernate then check the command. Also post back the contents of /var/log/pm-suspend.log for a quick view.

---

### Post by Wadcutter on 2011-10-08
Here is what is have in response to [cat /var/log/syslog* | grep PM:]

qilmo@qilmo-desktop:~$ cat /var/log/syslog* | grep PM:
Oct  7 15:20:22 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct  7 15:20:22 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Oct  7 15:20:22 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Oct  7 15:20:22 qilmo-desktop kernel: [    0.571132] PM: Resume from disk failed.
Oct  7 15:20:22 qilmo-desktop kernel: [    3.766141] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Oct  7 15:20:22 qilmo-desktop kernel: [    3.766145] PM: Basic memory bitmaps created
Oct  7 15:20:22 qilmo-desktop kernel: [    3.776973] PM: Basic memory bitmaps freed
Oct  7 20:49:15 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct  7 20:49:15 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Oct  7 20:49:15 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Oct  7 20:49:15 qilmo-desktop kernel: [    0.560565] PM: Resume from disk failed.
Oct  7 20:49:15 qilmo-desktop kernel: [    2.793014] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Oct  7 20:49:15 qilmo-desktop kernel: [    2.793018] PM: Basic memory bitmaps created
Oct  7 20:49:15 qilmo-desktop kernel: [    3.466710] PM: Basic memory bitmaps freed
Oct  7 10:30:27 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Oct  7 10:30:27 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Oct  7 10:30:27 qilmo-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Oct  7 10:30:28 qilmo-desktop kernel: [    0.570593] PM: Resume from disk failed.
Oct  7 10:30:28 qilmo-desktop kernel: [    3.695790] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
Oct  7 10:30:28 qilmo-desktop kernel: [    3.695795] PM: Basic memory bitmaps created
Oct  7 10:30:28 qilmo-desktop kernel: [    3.706552] PM: Basic memory bitmaps freed
qilmo@qilmo-desktop:~$ 

And for [ /var/log/pm-suspend.log ] it shows this:

bash: /var/log/pm-suspend.log: Permission denied

---

### Post by Toz on 2011-10-08
> And for [ /var/log/pm-suspend.log ] it shows this:
bash: /var/log/pm-suspend.log: Permission denied
Can you post back the contents of that file. The easiest way is to:
```
gedit /var/log/pm-suspend.log
```
...then copy/paste the contents here using code tags.

Also, using a similar procedure, can you post back the contents of **/etc/fstab** and **/etc/initramfs-tools/conf.d/resume**, as well as the results of running the command:
```
sudo blkid
```

---

### Post by Wadcutter on 2011-10-08
I apologize for not using code tags. I didn't know what they were until you mentioned it. I knew my last post didn't look right. After a little research, I think I may have figured it out. If it still isn't right, please bear with me or hit me on the knuckles and tell me what I should do.( Aren't the boxes supposed to just say "Code:" instead of "HTML Code:"? 

Here is what I got in response to your [gedit /var/log/pm-suspend.log] suggestion:


[HTML]Initial commandline parameters: 
Mon Oct  3 14:05:25 PDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux qilmo-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  2 
aes_generic            27607  1 aes_x86_64
xts                     2623  1 
gf128mul                8503  1 xts
dm_crypt               13043  1 
binfmt_misc             7960  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
ip6table_filter         1712  1 
ip6_tables             19428  1 ip6table_filter
snd_emu10k1_synth       6036  0 
snd_emux_synth         37399  1 snd_emu10k1_synth
nf_nat_irc              1577  0 
nf_conntrack_irc        4429  1 nf_nat_irc
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
nf_nat_ftp              2513  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      12742  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_mpu401              6875  0 
snd_mpu401_uart         6857  1 snd_mpu401
snd_seq_dummy           1782  0 
snd_emu10k1           149161  3 snd_emu10k1_synth
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_oss            31191  0 
iptable_filter          1841  1 
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_seq_midi            5829  0 
snd_pcm_oss            41394  0 
ip_tables              18201  1 iptable_filter
snd_rawmidi            23420  4 snd_seq_virmidi,snd_mpu401_uart,snd_emu10k1,snd_seq_midi
snd_mixer_oss          16299  1 snd_pcm_oss
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
nvidia              10832442  38 
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
font                    8053  1 fbcon
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_emu10k1,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             29958  1 
bitblit                 5811  1 fbcon
ns558                   3704  0 
emu10k1_gp              1964  0 
asus_atk0110           10033  0 
softcursor              1565  1 bitblit
gameport               10966  4 ns558,emu10k1_gp
snd                    71283  19 snd_emux_synth,snd_seq_virmidi,snd_mpu401,snd_mpu401_uart,snd_emu10k1,snd_seq_oss,snd_ac97_codec,snd_pcm_oss,snd_rawmidi,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_hwdep,snd_seq_device
soundcore               8052  1 snd
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
k8temp                  4040  0 
i2c_nforce2             6099  0 
edac_core              45423  0 
edac_mce_amd            9278  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41116  2 
hid                    83888  1 usbhid
skge                   41878  0 
ohci1394               30260  0 
sata_sil                8895  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
sata_nv                23714  3 
pata_amd               11962  0 
floppy                 63156  0 
             total       used       free     shared    buffers     cached
Mem:       2058008    1443820     614188          0     157976     589296
-/+ buffers/cache:     696548    1361460
Swap:      5911912          0    5911912
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Mon Oct  3 14:05:26 PDT 2011: performing suspend
Initial commandline parameters: 
Mon Oct  3 16:12:24 PDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux qilmo-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
usb_storage            50377  0 
cryptd                  8116  0 
aes_x86_64              7912  0 
aes_generic            27607  1 aes_x86_64
xts                     2623  0 
gf128mul                8503  1 xts
dm_crypt               13043  0 
binfmt_misc             7960  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37399  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
snd_emu10k1           149161  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_pcm_oss            41394  0 
ip6table_filter         1712  1 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_mpu401              6875  0 
ip6_tables             19428  1 ip6table_filter
snd_mpu401_uart         6857  1 snd_mpu401
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
nf_nat_irc              1577  0 
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
nf_conntrack_irc        4429  1 nf_nat_irc
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
nf_nat_ftp              2513  0 
snd_seq_dummy           1782  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            31191  0 
nf_conntrack_ipv4      12742  9 nf_nat
snd_seq_midi            5829  0 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_rawmidi            23420  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
font                    8053  1 fbcon
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          1841  1 
bitblit                 5811  1 fbcon
snd                    71283  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
nvidia              10832442  38 
ip_tables              18201  1 iptable_filter
vga16fb                12757  1 
edac_core              45423  0 
edac_mce_amd            9278  0 
ppdev                   6375  0 
vgastate                9857  1 vga16fb
k8temp                  4040  0 
soundcore               8052  1 snd
lp                      9336  0 
emu10k1_gp              1964  0 
ns558                   3704  0 
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
i2c_nforce2             6099  0 
asus_atk0110           10033  0 
parport_pc             29958  1 
gameport               10966  4 emu10k1_gp,ns558
parport                37160  3 ppdev,lp,parport_pc
usbhid                 41116  2 
hid                    83888  1 usbhid
skge                   41878  0 
ohci1394               30260  0 
sata_sil                8895  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
sata_nv                23714  3 
pata_amd               11962  0 
floppy                 63156  0 
             total       used       free     shared    buffers     cached
Mem:       2058008    1109776     948232          0     100868     551548
-/+ buffers/cache:     457360    1600648
Swap:      5911912          0    5911912
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Mon Oct  3 16:12:26 PDT 2011: performing hibernate
Mon Oct  3 21:04:48 PDT 2011: Awake.
Mon Oct  3 21:04:50 PDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.186 -> dest=:1.185 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Mon Oct  3 21:05:11 PDT 2011: Finished.
Initial commandline parameters: 
Mon Oct  3 21:50:23 PDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux qilmo-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
usb_storage            50377  0 
cryptd                  8116  0 
aes_x86_64              7912  2 
aes_generic            27607  1 aes_x86_64
xts                     2623  1 
gf128mul                8503  1 xts
dm_crypt               13043  1 
binfmt_misc             7960  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37399  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
snd_emu10k1           149161  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_pcm_oss            41394  0 
ip6table_filter         1712  1 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_mpu401              6875  0 
ip6_tables             19428  1 ip6table_filter
snd_mpu401_uart         6857  1 snd_mpu401
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
nf_nat_irc              1577  0 
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
nf_conntrack_irc        4429  1 nf_nat_irc
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
nf_nat_ftp              2513  0 
snd_seq_dummy           1782  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            31191  0 
nf_conntrack_ipv4      12742  9 nf_nat
snd_seq_midi            5829  0 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_rawmidi            23420  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
font                    8053  1 fbcon
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          1841  1 
bitblit                 5811  1 fbcon
snd                    71283  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
nvidia              10832442  42 
ip_tables              18201  1 iptable_filter
vga16fb                12757  1 
edac_core              45423  0 
edac_mce_amd            9278  0 
ppdev                   6375  0 
vgastate                9857  1 vga16fb
k8temp                  4040  0 
soundcore               8052  1 snd
lp                      9336  0 
emu10k1_gp              1964  0 
ns558                   3704  0 
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
i2c_nforce2             6099  0 
asus_atk0110           10033  0 
parport_pc             29958  1 
gameport               10966  4 emu10k1_gp,ns558
parport                37160  3 ppdev,lp,parport_pc
usbhid                 41116  2 
hid                    83888  1 usbhid
skge                   41878  0 
ohci1394               30260  0 
sata_sil                8895  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
sata_nv                23714  5 
pata_amd               11962  0 
floppy                 63156  0 
             total       used       free     shared    buffers     cached
Mem:       2058008     965940    1092068          0      61140     321048
-/+ buffers/cache:     583752    1474256
Swap:      5911912     170552    5741360
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Mon Oct  3 21:50:24 PDT 2011: performing hibernate
Tue Oct  4 08:53:27 PDT 2011: Awake.
Tue Oct  4 08:53:29 PDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.266 -> dest=:1.265 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Tue Oct  4 08:53:41 PDT 2011: Finished.
Initial commandline parameters: 
Tue Oct  4 12:42:04 PDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux qilmo-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
usb_storage            50377  0 
cryptd                  8116  0 
aes_x86_64              7912  0 
aes_generic            27607  1 aes_x86_64
xts                     2623  0 
gf128mul                8503  1 xts
dm_crypt               13043  0 
binfmt_misc             7960  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37399  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
snd_emu10k1           149161  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_pcm_oss            41394  0 
ip6table_filter         1712  1 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_mpu401              6875  0 
ip6_tables             19428  1 ip6table_filter
snd_mpu401_uart         6857  1 snd_mpu401
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
nf_nat_irc              1577  0 
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
nf_conntrack_irc        4429  1 nf_nat_irc
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
nf_nat_ftp              2513  0 
snd_seq_dummy           1782  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            31191  0 
nf_conntrack_ipv4      12742  9 nf_nat
snd_seq_midi            5829  0 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_rawmidi            23420  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
font                    8053  1 fbcon
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          1841  1 
bitblit                 5811  1 fbcon
snd                    71283  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
nvidia              10832442  42 
ip_tables              18201  1 iptable_filter
vga16fb                12757  1 
edac_core              45423  0 
edac_mce_amd            9278  0 
ppdev                   6375  0 
vgastate                9857  1 vga16fb
k8temp                  4040  0 
soundcore               8052  1 snd
lp                      9336  0 
emu10k1_gp              1964  0 
ns558                   3704  0 
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
i2c_nforce2             6099  0 
asus_atk0110           10033  0 
parport_pc             29958  1 
gameport               10966  4 emu10k1_gp,ns558
parport                37160  3 ppdev,lp,parport_pc
usbhid                 41116  2 
hid                    83888  1 usbhid
skge                   41878  0 
ohci1394               30260  0 
sata_sil                8895  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
sata_nv                23714  3 
pata_amd               11962  0 
floppy                 63156  0 
             total       used       free     shared    buffers     cached
Mem:       2058008     860952    1197056          0     142160     422352
-/+ buffers/cache:     296440    1761568
Swap:      5911912     261268    5650644
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Tue Oct  4 12:42:05 PDT 2011: performing hibernate
Tue Oct  4 14:46:02 PDT 2011: Awake.
Tue Oct  4 14:46:02 PDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.571 -> dest=:1.570 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Tue Oct  4 14:46:08 PDT 2011: Finished.
Initial commandline parameters: 
Tue Oct  4 16:24:36 PDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux qilmo-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
nls_iso8859_1           4633  0 
nls_cp437               6351  0 
vfat                   10866  0 
fat                    55350  1 vfat
usb_storage            50377  0 
cryptd                  8116  0 
aes_x86_64              7912  2 
aes_generic            27607  1 aes_x86_64
xts                     2623  1 
gf128mul                8503  1 xts
dm_crypt               13043  1 
binfmt_misc             7960  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37399  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
snd_emu10k1           149161  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_pcm_oss            41394  0 
ip6table_filter         1712  1 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_mpu401              6875  0 
ip6_tables             19428  1 ip6table_filter
snd_mpu401_uart         6857  1 snd_mpu401
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
nf_nat_irc              1577  0 
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
nf_conntrack_irc        4429  1 nf_nat_irc
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
nf_nat_ftp              2513  0 
snd_seq_dummy           1782  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            31191  0 
nf_conntrack_ipv4      12742  9 nf_nat
snd_seq_midi            5829  0 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_rawmidi            23420  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
tileblit                2487  1 fbcon
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
font                    8053  1 fbcon
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          1841  1 
bitblit                 5811  1 fbcon
snd                    71283  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
softcursor              1565  1 bitblit
nvidia              10832442  42 
ip_tables              18201  1 iptable_filter
vga16fb                12757  1 
edac_core              45423  0 
edac_mce_amd            9278  0 
ppdev                   6375  0 
vgastate                9857  1 vga16fb
k8temp                  4040  0 
soundcore               8052  1 snd
lp                      9336  0 
emu10k1_gp              1964  0 
ns558                   3704  0 
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
i2c_nforce2             6099  0 
asus_atk0110           10033  0 
parport_pc             29958  1 
gameport               10966  4 emu10k1_gp,ns558
parport                37160  3 ppdev,lp,parport_pc
usbhid                 41116  2 
hid                    83888  1 usbhid
skge                   41878  0 
ohci1394               30260  0 
sata_sil                8895  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
sata_nv                23714  3 
pata_amd               11962  0 
floppy                 63156  0 
             total       used       free     shared    buffers     cached
Mem:       2058008     973008    1085000          0      67672     329316
-/+ buffers/cache:     576020    1481988
Swap:      5911912     183044    5728868
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Tue Oct  4 16:24:37 PDT 2011: performing suspend
Initial commandline parameters: 
Wed Oct  5 18:51:05 PDT 2011: Running hooks for hibernate.
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:Linux qilmo-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  2 
aes_generic            27607  1 aes_x86_64
xts                     2623  1 
gf128mul                8503  1 xts
dm_crypt               13043  1 
binfmt_misc             7960  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37399  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
snd_emu10k1           149161  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
ip6table_filter         1712  1 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
ip6_tables             19428  1 ip6table_filter
snd_mpu401              6875  0 
snd_mpu401_uart         6857  1 snd_mpu401
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
nf_nat_irc              1577  0 
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
nf_conntrack_irc        4429  1 nf_nat_irc
nf_nat_ftp              2513  0 
snd_seq_dummy           1782  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            31191  0 
nf_conntrack_ipv4      12742  9 nf_nat
snd_seq_midi            5829  0 
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_rawmidi            23420  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
iptable_filter          1841  1 
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              18201  1 iptable_filter
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ppdev                   6375  0 
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia              10832442  38 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
ns558                   3704  0 
asus_atk0110           10033  0 
parport_pc             29958  1 
edac_core              45423  0 
edac_mce_amd            9278  0 
k8temp                  4040  0 
snd                    71283  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
emu10k1_gp              1964  0 
soundcore               8052  1 snd
gameport               10966  4 ns558,emu10k1_gp
i2c_nforce2             6099  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41116  2 
hid                    83888  1 usbhid
skge                   41878  0 
ohci1394               30260  0 
sata_sil                8895  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
pata_amd               11962  0 
sata_nv                23714  3 
floppy                 63156  0 
             total       used       free     shared    buffers     cached
Mem:       2058008    1272224     785784          0      80740     370976
-/+ buffers/cache:     820508    1237500
Swap:      5911912          0    5911912
success.
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:success.
/etc/pm/sleep.d/10_grub-common hibernate hibernate:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:success.
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:success.
/etc/pm/sleep.d/action_wpa hibernate hibernate:success.
Wed Oct  5 18:51:06 PDT 2011: performing hibernate
Wed Oct  5 18:53:56 PDT 2011: Awake.
Wed Oct  5 18:54:02 PDT 2011: Running hooks for thaw
/etc/pm/sleep.d/action_wpa thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:method return sender=:1.134 -> dest=:1.133 reply_serial=2
success.
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:not applicable.
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:not applicable.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:success.
/etc/pm/sleep.d/10_grub-common thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:success.
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:success.
Wed Oct  5 18:54:32 PDT 2011: Finished.
Initial commandline parameters: 
Fri Oct  7 18:26:20 PDT 2011: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:success.
/usr/lib/pm-utils/sleep.d/00logging suspend suspend:Linux qilmo-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  0 
aes_generic            27607  1 aes_x86_64
xts                     2623  0 
gf128mul                8503  1 xts
dm_crypt               13043  0 
binfmt_misc             7960  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37399  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
snd_emu10k1           149161  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_pcm_oss            41394  0 
snd_mpu401              6875  0 
snd_mpu401_uart         6857  1 snd_mpu401
snd_mixer_oss          16299  1 snd_pcm_oss
ip6table_filter         1712  1 
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
ip6_tables             19428  1 ip6table_filter
snd_seq_dummy           1782  0 
nf_nat_irc              1577  0 
nf_conntrack_irc        4429  1 nf_nat_irc
snd_seq_oss            31191  0 
nf_nat_ftp              2513  0 
snd_seq_midi            5829  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_rawmidi            23420  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
nf_conntrack_ipv4      12742  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
nf_conntrack_ftp        7126  1 nf_nat_ftp
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter          1841  1 
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ip_tables              18201  1 iptable_filter
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
ppdev                   6375  0 
edac_core              45423  0 
emu10k1_gp              1964  0 
snd                    71283  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mpu401,snd_mpu401_uart,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usblp                  12407  0 
ns558                   3704  0 
nvidia              10832442  38 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
edac_mce_amd            9278  0 
k8temp                  4040  0 
soundcore               8052  1 snd
gameport               10966  4 emu10k1_gp,ns558
parport_pc             29958  1 
asus_atk0110           10033  0 
i2c_nforce2             6099  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41116  2 
hid                    83888  1 usbhid
skge                   41878  0 
ohci1394               30260  0 
sata_sil                8895  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
sata_nv                23714  3 
pata_amd               11962  0 
floppy                 63156  0 
             total       used       free     shared    buffers     cached
Mem:       2058008     765348    1292660          0      79008     320456
-/+ buffers/cache:     365884    1692124
Swap:      5911912          0    5911912
success.
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend:success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:success.
/etc/pm/sleep.d/10_grub-common suspend suspend:success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend:success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend:stop: Unknown instance: 
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend:not applicable.
/usr/lib/pm-utils/sleep.d/95packagekit suspend suspend:success.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend:kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend:success.
Fri Oct  7 18:26:22 PDT 2011: performing suspend[/HTML]

Then I have for [gedit /etc/fstab]:

[HTML]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb2 during installation
UUID=65bca8ed-b19d-420c-a7d5-e81f1ac59624 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=621562f9-c2c0-4e53-ac4c-67a2c71e17f7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/HTML]


[gedit /etc/initramfs-tools/conf.d/resume] shows the following:


[HTML]RESUME=UUID=621562f9-c2c0-4e53-ac4c-67a2c71e17f7[/HTML]


And finally, [sudo blkid] shows this:[HTML]/dev/sda1: UUID="0E50559E50558D79" TYPE="ntfs" 
/dev/sda5: LABEL="Backup" UUID="01C9F5B36C2E1400" TYPE="ntfs" 
/dev/sdb1: UUID="65bca8ed-b19d-420c-a7d5-e81f1ac59624" TYPE="ext4" 
/dev/sdb2: UUID="621562f9-c2c0-4e53-ac4c-67a2c71e17f7" TYPE="swap" 
/dev/sdb5: LABEL="Win Backup" UUID="01CAF13443E931F0" TYPE="ntfs" 
/dev/mapper/truecrypt11: UUID="B65C48935C485073" TYPE="ntfs[/HTML]

---

### Post by Toz on 2011-10-08
Everything looks good there. Lets look elsewhere. 

Type in the following commands in a terminal window:
```
sudo bash -c "echo shutdown > /sys/power/disk
sudo bash -c "echo disk > /sys/power/state"
```
The system should hibernate and shutdown. Can you confirm that it works?

Can you also please post the contents of the file **/etc/default/acpi-support**?

---

### Post by Wadcutter on 2011-10-10
> Type in the following commands in a terminal window:sudo bash -c "echo shutdown > /sys/power/disk
sudo bash -c "echo disk > /sys/power/state"

The first command resulted in nothing and following with the second resulted in the same. Then I noticed that while the second command was enclosed with " " marks, the first one lacked one at the end. I added that and it gave me a command prompt again. When I used the second command, it went to hibernate (same as always, blank screen, but computer still powered on). When I tried to restore, it hung up on a blank screen, but with the mouse lighted up. I had to re-boot (power re-set button) to get back and then it was like a cold boot-all open programs & work had been shut down.

> Can you also please post the contents of the file /etc/default/acpi-support?

Here it is. I read it but was far too technical for me. Seemed to pertain to mostly laptops. Remember, I'm trying to do this on a desktop.

```
#
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 
```

I'm going to really owe you for spending this much time on my little problem.

---

### Post by Toz on 2011-10-11
> Then I noticed that while the second command was enclosed with " " marks, the first one lacked one at the end. I added that and it gave me a command prompt again
Sorry about that. Nice catch though.

Try these commands instead:
```
sudo bash -c "echo platform > /sys/power/disk"
sudo bash -c "echo disk > /sys/power/state"
```

---

### Post by Wadcutter on 2011-10-12
> sudo bash -c "echo platform > /sys/power/disk"
sudo bash -c "echo disk > /sys/power/state"

Those commands resulted in the same as the previous two, i.e., the monitor went dark, mouse light off, keyboard off, computer box still on, fans running, power light on. I hit the reset switch to come back and it resulted in the mouse and keyboard lights coming on, it did a partial reboot, got a blinking cursor, the cursor disappeared and I was hung on a darkened screen (no mouse cursor). I hit the reset again and went into a full re-boot and when I got to my regular screen, all the programs which had been open were now closed. So the second boot apparently canceled any hibernation that was going on. But I had to do it because it was stalled.

---

### Post by Toz on 2011-10-12
Ok - a couple of thoughts. 

First, is there possibly anything in your bios that allows you to specify how the system behaves during a sleep/hibernate cycle? Possibly in an acpi section?

And secondly, let's try getting a more complete log file to see whats going on when you try to suspend.

1. Become root:
```
sudo -i
```

2. Backup the existing log file:
```
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.bak
```

3. Create new log file:
```
touch /var/log/pm-suspend.log
```

4. Enable greater debugging:
```
export PM_DEBUG=true
```

5. Manually run hibernate:
```
pm-hibernate
```

6. After you get your system back, post back the contents of the /var/log/pm-suspend.log file.

---

### Post by Wadcutter on 2011-10-12
My bios has some power settings. It gives 3 choices for "ACPI Suspend Type"  They are

```
S1(Pos) ( )
S3(STR)( )
S1 and S3(.)
```

Mine is set to S1 and S3 as shown and hasn't changed since I've had the computer. 

The other ACPI setting is for "ACPI Support" The choices there are "enabled" or "disabled". Mine has always been "enabled".

I don't think the bios settings are the culprit since the computer hibernates and powers down when doing it in Windows and nothing has changed in the bios.


> 6. After you get your system back, post back the contents of the /var/log/pm-suspend.log file.

It says this:

```
+ log Initial commandline parameters: 
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Initial commandline parameters:  = -n ]
+ printf %s\n Initial commandline parameters: 
Initial commandline parameters: 
+ load_hook_blacklist
+ [   ]
+ local hook
+ load_hook_parameters
+ [   ]
+ remove_parameters
+ local p
+ [  = all ]
+ echo 
+ grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
+ cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
+ [   ]
+ add_parameters
+ remove_parameters
+ local p
+ [  = all ]
+ echo 
+ grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
+ cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ date
+ log Wed Oct 12 18:26:10 PDT 2011: Running hooks for hibernate.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Wed Oct 12 18:26:10 PDT 2011: Running hooks for hibernate. = -n ]
+ printf %s\n Wed Oct 12 18:26:10 PDT 2011: Running hooks for hibernate.
Wed Oct 12 18:26:10 PDT 2011: Running hooks for hibernate.
+ run_hooks sleep hibernate hibernate
+ _run_hooks sleep hibernate hibernate
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [  = reverse ]
+ IFS= 	

+ uniq
+ sort
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/action_wpa ]
+ echo action_wpa
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/95packagekit ]
+ echo 95packagekit
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [  -a  = reverse -a  ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change hibernate hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 000kernel-change ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00logging hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ [ -n /var/log/pm-suspend.log ]
+ /bin/uname -a
Linux qilmo-desktop 2.6.32-34-generic #77-Ubuntu SMP Tue Sep 13 19:39:17 UTC 2011 x86_64 GNU/Linux
+ lsmod
Module                  Size  Used by
cryptd                  8116  0 
aes_x86_64              7912  2 
aes_generic            27607  1 aes_x86_64
xts                     2623  1 
gf128mul                8503  1 xts
dm_crypt               13043  1 
binfmt_misc             7960  1 
ipt_REJECT              2384  1 
ipt_LOG                 5370  5 
xt_limit                2180  7 
xt_tcpudp               2667  7 
ipt_addrtype            2055  4 
xt_state                1490  7 
snd_emu10k1_synth       6036  0 
snd_emux_synth         37399  1 snd_emu10k1_synth
snd_seq_virmidi         5269  1 snd_emux_synth
snd_seq_midi_emul       6975  1 snd_emux_synth
snd_emu10k1           149161  3 snd_emu10k1_synth
snd_ac97_codec        125394  1 snd_emu10k1
ac97_bus                1450  1 snd_ac97_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          8500  2 snd_emu10k1,snd_pcm
snd_util_mem            3818  2 snd_emux_synth,snd_emu10k1
snd_hwdep               6924  2 snd_emux_synth,snd_emu10k1
ip6table_filter         1712  1 
ip6_tables             19428  1 ip6table_filter
nf_nat_irc              1577  0 
snd_mpu401              6875  0 
snd_mpu401_uart         6857  1 snd_mpu401
nf_conntrack_irc        4429  1 nf_nat_irc
nf_nat_ftp              2513  0 
snd_seq_dummy           1782  0 
nf_nat                 19286  2 nf_nat_irc,nf_nat_ftp
snd_seq_oss            31191  0 
nf_conntrack_ipv4      12742  9 nf_nat
nf_defrag_ipv4          1481  1 nf_conntrack_ipv4
snd_seq_midi            5829  0 
nf_conntrack_ftp        7126  1 nf_nat_ftp
nf_conntrack           73326  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_rawmidi            23420  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi
iptable_filter          1841  1 
snd_seq_midi_event      7267  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                57481  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ppdev                   6375  0 
ip_tables              18201  1 iptable_filter
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
snd_timer              23649  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6888  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
asus_atk0110           10033  0 
parport_pc             29958  1 
ns558                   3704  0 
x_tables               22361  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
nvidia              10832442  42 
edac_core              45423  0 
snd                    71283  19 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  4040  0 
edac_mce_amd            9278  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
emu10k1_gp              1964  0 
gameport               10966  4 ns558,emu10k1_gp
soundcore               8052  1 snd
i2c_nforce2             6099  0 
lp                      9336  0 
parport                37160  3 ppdev,parport_pc,lp
usbhid                 41116  2 
hid                    83888  1 usbhid
skge                   41878  0 
ohci1394               30260  0 
sata_sil                8895  0 
ieee1394               94771  1 ohci1394
forcedeth              55624  0 
sata_nv                23714  3 
pata_amd               11962  0 
floppy                 63156  0 
+ free
             total       used       free     shared    buffers     cached
Mem:       2058008     739532    1318476          0      27428     170156
-/+ buffers/cache:     541948    1516060
Swap:      5911912      78384    5833528
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00logging ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave false
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=kernel
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=false
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/00sleep_module ]
+ [  ]
+ [  ]
+ [  ]
+ [  ]
+ set -a
+ . /etc/pm/config.d/00sleep_module
+ SUSPEND_MODULES= 
+ HOOK_BLACKLIST= 
+ ADD_PARAMETERS= 
+ DROP_PARAMETERS= 
+ set +a
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ is_set true
+ return 0
+ set -x
+ command_exists service
+ type service
+ return 0
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ kernel = auto ]
+ mod=/usr/lib/pm-utils/module.d/kernel
+ [ -f /usr/lib/pm-utils/module.d/kernel ]
+ . /usr/lib/pm-utils/module.d/kernel
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ [ false = true -o false = false ]
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 00powersave ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:
/usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ suspend_pulse
+ get_pulse_users
+ test_pulse_system
+ awk -F: {print $3}
+ getent passwd pulse
+ PULSE_SYSTEM_USER=111
+ [ -z 111 ]
+ sed s/111//
+ tr -d  
+ ps -C pulseaudio -o uid=
+ cut -f1 -d:
+ getent passwd 1000
+ THIS_USER=qilmo
+ su qilmo -l -c -- ck-list-sessions | grep "active = TRUE"
+ save_pulse_state_and_mute sink qilmo
+ su qilmo -l -c -- pacmd list-${1}s | \
        sed -n "s/^[[:space:]*]*//; /\(index\|mute\)/p" | \
        (index="";
            while read field value; do
                if [ ${field%:} = "index" ]; then
                    index=${value}
                else
                    savestate pulse:"${2}":${1}${index} ${value}
                    pacmd set-${1}-mute ${index} yes
                fi
            done)
+ save_pulse_state_and_mute source qilmo
+ su qilmo -l -c -- pacmd list-${1}s | \
        sed -n "s/^[[:space:]*]*//; /\(index\|mute\)/p" | \
        (index="";
            while read field value; do
                if [ ${field%:} = "index" ]; then
                    index=${value}
                else
                    savestate pulse:"${2}":${1}${index} ${value}
                    pacmd set-${1}-mute ${index} yes
                fi
            done)
+ su qilmo -l -c -- pacmd suspend true
+ break
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 01PulseAudio ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common hibernate hibernate
+ _run_hook /etc/pm/sleep.d/10_grub-common hibernate hibernate
+ log -n /etc/pm/sleep.d/10_grub-common hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate:+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common hibernate hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_grub-common ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate
+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 10_unattended-upgrades-hibernate ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:
/usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 49bluetooth ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:
/usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ suspend_nm
+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.sleep
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 55NetworkManager ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ suspend_modules
+ [ -z   ]
+ return 0
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 75modules ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ is_set 
+ return 2
+ exit 254
+ hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 90clock ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ [ -d /sys/devices/system/cpu/ ]
+ hibernate_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -L cpu0/cpufreq ]
+ gov=cpu0/cpufreq/scaling_governor
+ [ -f cpu0/cpufreq/scaling_governor ]
+ continue
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 94cpufreq ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate
stop: Unknown instance: 
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95anacron ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led hibernate hibernate
+ hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95led ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95packagekit ]
+ [ -f /usr/lib/pm-utils/sleep.d/95packagekit ]
+ hook=/usr/lib/pm-utils/sleep.d/95packagekit
+ run_hook /usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/95packagekit
+ local hook=95packagekit
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95packagekit ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:packagekit ]
+ [ -x /usr/lib/pm-utils/sleep.d/95packagekit ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95packagekit hibernate hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95packagekit
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 95packagekit ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate
++ command_exists service
++ type service
++ return 0
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@347(): precache_dmivars
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@170(precache_dmivars): local p q f
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@107(dmisysget): _dmisysget bios_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='ASUS A8N-SLI DELUXE ACPI BIOS Revision 1805'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='ASUS A8N-SLI DELUXE ACPI BIOS Revision 1805'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@106(dmisysget): _dmisysget bios_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='Phoenix Technologies, LTD'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='Phoenix Technologies, LTD'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.firmware.release_date
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.release_date =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.firmware.release_date* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.firmware.release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@108(dmisysget): _dmisysget bios_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/bios_date ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=09/29/2006
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=09/29/2006
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_firmware_release_date
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@109(dmisysget): _dmisysget sys_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/sys_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='System manufacturer'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='System manufacturer'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@110(dmisysget): _dmisysget product_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='System Product Name'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='System Product Name'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@111(dmisysget): _dmisysget product_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/product_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='System Version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='System Version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@112(dmisysget): _dmisysget board_name
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_name ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='A8N-SLI DELUXE'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='A8N-SLI DELUXE'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@113(dmisysget): _dmisysget board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_version ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=1.XX
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=1.XX
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.board.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.board.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.board.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.board.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@114(dmisysget): _dmisysget board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@100(_dmisysget): [[ -r /sys/class/dmi/id/board_vendor ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@101(_dmisysget): read RES
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES='ASUSTeK Computer INC.'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES='ASUSTeK Computer INC.'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_board_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.vendor
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.vendor =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.vendor* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@115(dmisysget): videoget vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x058000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0310 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:06.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:06.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x01018a = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:07.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:07.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010185 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010185 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:09.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:09.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x068000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): cat /sys/bus/pci/devices/0000:01:00.0/vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@71(videoget): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x10de
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_vendor
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.product
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.product =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.product* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@116(dmisysget): videoget device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x058000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0310 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:06.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:06.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x01018a = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:07.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:07.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010185 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010185 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:09.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:09.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x068000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): cat /sys/bus/pci/devices/0000:01:00.0/device
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@72(videoget): RES=0x06e4
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=0x06e4
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=0x06e4
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_product
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.driver
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.driver =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.driver* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@117(dmisysget): videoget driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x058000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0310 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:06.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:06.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x01018a = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:07.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:07.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010185 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010185 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:09.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:09.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x068000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@74(videoget): [[ -L /sys/bus/pci/devices/0000:01:00.0/driver ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): readlink /sys/bus/pci/devices/0000:01:00.0/driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@75(videoget): RES=../../../../bus/pci/drivers/nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@76(videoget): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_driver
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.hardware.primary_video.using_kms
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.hardware.primary_video.using_kms =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.hardware.primary_video.using_kms* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.hardware.primary_video.using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@118(dmisysget): videoget using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@65(videoget): local dev pci
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@66(videoget): pci=/sys/bus/pci/devices
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x058000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060100 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:01.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:01.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0500 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0310 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:02.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:02.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x0c0320 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:06.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:06.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x01018a = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:07.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:07.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010185 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:08.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:08.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x010185 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:09.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:09.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060401 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0a.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0a.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x068000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0b.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0b.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0c.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0c.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0d.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0d.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:0e.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:0e.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060400 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.1/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.1/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.2/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.2/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:00:18.3/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:00:18.3/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x060000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): continue
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@67(videoget): for dev in '"$pci"/*'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@68(videoget): [[ -f /sys/bus/pci/devices/0000:01:00.0/class ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): cat /sys/bus/pci/devices/0000:01:00.0/class
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@69(videoget): [[ 0x030000 = \0\x\0\3\0\0\0\0 ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@70(videoget): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@84(videoget): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@87(videoget): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@91(videoget): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=false
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_hardware_primary_video_using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@171(precache_dmivars): for q in '$possible_system_properties'
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): canonicalize_dmivar system.kernel.version
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.kernel.version =~ ^[a-z._-]+$ ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@163(canonicalize_dmivar): [[ system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version = *system.kernel.version* ]]
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@164(canonicalize_dmivar): echo system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@172(precache_dmivars): p=system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@173(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@174(precache_dmivars): for f in dmisysget halget dmidecodeget
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): dmisysget system.kernel.version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@105(dmisysget): case $1 in
//usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): uname -r
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@119(dmisysget): RES=2.6.32-34-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@175(precache_dmivars): break
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@177(precache_dmivars): RES=2.6.32-34-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@178(precache_dmivars): RES=2.6.32-34-generic
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@179(precache_dmivars): read system_kernel_version
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@181(precache_dmivars): RES=
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@352(): has_parameter --quirk-test
//usr/lib/pm-utils/functions@251(has_parameter): get_parameters
//usr/lib/pm-utils/functions@246(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@255(has_parameter): return 1
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@357(): using_kms
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@60(using_kms): grep -q -E '(nouveau|drm)fb' /proc/fb
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@361(): using_nvidia
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@54(using_nvidia): [[ -d /sys/module/nvidia ]]
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@363(): remove_parameters --quirk-dpms-on --quirk-dpms-suspend --quirk-s3-mode --quirk-s3-bios --quirk-vbe-post --quirk-vbe-post --quirk-vga-mode-3 --quirk-vbemode-restore --quirk-vbestate-restore --quirk-reset-brightness --quirk-radeon-off --quirk-no-fb --quirk-save-pci
/usr/lib/pm-utils/functions@222(remove_parameters): local p
/usr/lib/pm-utils/functions@223(remove_parameters): '[' --quirk-dpms-on = all ']'
/usr/lib/pm-utils/functions@226(remove_parameters): echo ''
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-dpms-on
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-dpms-suspend
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-s3-mode
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-s3-bios
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-vbe-post
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-vga-mode-3
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-vbemode-restore
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-vbestate-restore
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-reset-brightness
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-radeon-off
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-no-fb
/usr/lib/pm-utils/functions@227(remove_parameters): for p in '"$@"'
/usr/lib/pm-utils/functions@228(remove_parameters): echo --quirk-save-pci
/usr/lib/pm-utils/functions@231(remove_parameters): grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@233(remove_parameters): cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 98video-quirk-db-handler ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate
+ log -n /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video hibernate hibernate
+ command_exists service
+ type service
+ return 0
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ maybe_chvt
+ is_set 
+ return 2
+ savestate console
+ [ -n  ]
+ cat
+ fgconsole
+ chvt 63
+ is_set no
+ return 1
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [  -a  = reverse -a 99video ]
+ [ !  ]
+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/action_wpa ]
+ hook=/etc/pm/sleep.d/action_wpa
+ run_hook /etc/pm/sleep.d/action_wpa hibernate hibernate
+ _run_hook /etc/pm/sleep.d/action_wpa hibernate hibernate
+ log -n /etc/pm/sleep.d/action_wpa hibernate hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/action_wpa hibernate hibernate:
/etc/pm/sleep.d/action_wpa hibernate hibernate:+ hook_ok /etc/pm/sleep.d/action_wpa
+ local hook=action_wpa
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:action_wpa ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:action_wpa ]
+ [ -x /etc/pm/sleep.d/action_wpa ]
+ return 0
+ /etc/pm/sleep.d/action_wpa hibernate hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=action_wpa
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Wed Oct 12 18:26:12 PDT 2011: performing hibernate
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Wed Oct 12 18:26:12 PDT 2011: performing hibernate = -n ]
+ printf %s\n Wed Oct 12 18:26:12 PDT 2011: performing hibernate
Wed Oct 12 18:26:12 PDT 2011: performing hibernate
+ sync
+ do_hibernate
+ [ -n  ]
+ echo -n disk
+ date
+ log Wed Oct 12 18:34:10 PDT 2011: Awake.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Wed Oct 12 18:34:10 PDT 2011: Awake. = -n ]
+ printf %s\n Wed Oct 12 18:34:10 PDT 2011: Awake.
Wed Oct 12 18:34:10 PDT 2011: Awake.
+ date
+ log Wed Oct 12 18:34:10 PDT 2011: Running hooks for thaw
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Wed Oct 12 18:34:10 PDT 2011: Running hooks for thaw = -n ]
+ printf %s\n Wed Oct 12 18:34:10 PDT 2011: Running hooks for thaw
Wed Oct 12 18:34:10 PDT 2011: Running hooks for thaw
+ run_hooks sleep thaw hibernate reverse
+ _run_hooks sleep thaw hibernate reverse
+ local syshooks=/etc/pm/sleep.d
+ local phooks=/usr/lib/pm-utils/sleep.d
+ command_exists before_hooks
+ type before_hooks
+ return 0
+ before_hooks
+ [ -z  ]
+ return 0
+ local sort=sort
+ local base
+ local hook
+ local oifs= 	

+ local nifs=

+ IFS=

+ [ reverse = reverse ]
+ sort=sort -r
+ IFS= 	

+ sort -r
+ uniq
+ [ -O /etc/pm/sleep.d/10_grub-common ]
+ echo 10_grub-common
+ [ -O /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ echo 10_unattended-upgrades-hibernate
+ [ -O /etc/pm/sleep.d/action_wpa ]
+ echo action_wpa
+ [ -O /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ echo 000kernel-change
+ [ -O /usr/lib/pm-utils/sleep.d/00logging ]
+ echo 00logging
+ [ -O /usr/lib/pm-utils/sleep.d/00powersave ]
+ echo 00powersave
+ [ -O /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ echo 01PulseAudio
+ [ -O /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ echo 49bluetooth
+ [ -O /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ echo 55NetworkManager
+ [ -O /usr/lib/pm-utils/sleep.d/75modules ]
+ echo 75modules
+ [ -O /usr/lib/pm-utils/sleep.d/90clock ]
+ echo 90clock
+ [ -O /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ echo 94cpufreq
+ [ -O /usr/lib/pm-utils/sleep.d/95anacron ]
+ echo 95anacron
+ [ -O /usr/lib/pm-utils/sleep.d/95led ]
+ echo 95led
+ [ -O /usr/lib/pm-utils/sleep.d/95packagekit ]
+ echo 95packagekit
+ [ -O /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ echo 98video-quirk-db-handler
+ [ -O /usr/lib/pm-utils/sleep.d/99video ]
+ echo 99video
+ IFS= 	

+ [ reverse -a reverse = reverse -a action_wpa ]
+ [ action_wpa > action_wpa ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/action_wpa ]
+ hook=/etc/pm/sleep.d/action_wpa
+ run_hook /etc/pm/sleep.d/action_wpa thaw hibernate
+ _run_hook /etc/pm/sleep.d/action_wpa thaw hibernate
+ log -n /etc/pm/sleep.d/action_wpa thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/action_wpa thaw hibernate:
/etc/pm/sleep.d/action_wpa thaw hibernate:+ hook_ok /etc/pm/sleep.d/action_wpa
+ local hook=action_wpa
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:action_wpa ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:action_wpa ]
+ [ -x /etc/pm/sleep.d/action_wpa ]
+ return 0
+ /etc/pm/sleep.d/action_wpa thaw hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=action_wpa
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a action_wpa ]
+ [ 99video > action_wpa ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/99video ]
+ [ -f /usr/lib/pm-utils/sleep.d/99video ]
+ hook=/usr/lib/pm-utils/sleep.d/99video
+ run_hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/99video thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/99video thaw hibernate:
/usr/lib/pm-utils/sleep.d/99video thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/99video
+ local hook=99video
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:99video ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video ]
+ [ -x /usr/lib/pm-utils/sleep.d/99video ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/99video thaw hibernate
+ command_exists service
+ type service
+ return 0
+ command_exists vbetool
+ type vbetool
+ return 0
+ command_exists radeontool
+ type radeontool
+ return 0
+ is_set no
+ return 1
+ maybe_deallocvt
+ state_exists console
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:console ]
+ restorestate console
+ state_exists console
+ [ -O /var/run/pm-utils/pm-suspend/storage/state:console ]
+ cat /var/run/pm-utils/pm-suspend/storage/state:console
+ chvt 7
+ deallocvt 63
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=99video
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 99video ]
+ [ 98video-quirk-db-handler > 99video ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/98video-quirk-db-handler ]
+ [ -f /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ hook=/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler
+ local hook=98video-quirk-db-handler
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:98video-quirk-db-handler ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:video-quirk-db-handler ]
+ [ -x /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler thaw hibernate
++ command_exists service
++ type service
++ return 0
+ [[ -n true ]]
+ export 'PS4=${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
+ PS4='${BASH_SOURCE}@${LINENO}(${FUNCNAME[0]}): '
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@10(): set -x
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@25(): possible_video_quirks=' --quirk-dpms-on
	   --quirk-dpms-suspend
	   --quirk-s3-mode
	   --quirk-s3-bios
	   --quirk-vbe-post
	   --quirk-vbe-post
	   --quirk-vga-mode-3
	   --quirk-vbemode-restore
	   --quirk-vbestate-restore
	   --quirk-reset-brightness
	   --quirk-radeon-off
	   --quirk-no-fb
	   --quirk-save-pci'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@40(): possible_system_properties='system.firmware.version 
        system.firmware.vendor
	system.firmware.release_date
        system.hardware.vendor
	system.hardware.product 
        system.hardware.version
	system.board.product 
        system.board.version 
        system.board.vendor
	system.hardware.primary_video.vendor
	system.hardware.primary_video.product
	system.hardware.primary_video.driver
	system.hardware.primary_video.using_kms
	system.kernel.version'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@343(): case $1 in
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@425(): state_exists video_quirks
/usr/lib/pm-utils/functions@196(state_exists): '[' -O /var/run/pm-utils/pm-suspend/storage/state:video_quirks ']'
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler@428(): has_parameter --store-quirks-as-lkw
//usr/lib/pm-utils/functions@251(has_parameter): get_parameters
//usr/lib/pm-utils/functions@246(get_parameters): cat /var/run/pm-utils/pm-suspend/storage/parameters
/usr/lib/pm-utils/functions@255(has_parameter): return 1
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=98video-quirk-db-handler
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 98video-quirk-db-handler ]
+ [ 95packagekit > 98video-quirk-db-handler ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95packagekit ]
+ [ -f /usr/lib/pm-utils/sleep.d/95packagekit ]
+ hook=/usr/lib/pm-utils/sleep.d/95packagekit
+ run_hook /usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:
/usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/95packagekit
+ local hook=95packagekit
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95packagekit ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:packagekit ]
+ [ -x /usr/lib/pm-utils/sleep.d/95packagekit ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95packagekit thaw hibernate
method return sender=:1.357 -> dest=:1.356 reply_serial=2
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95packagekit
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95packagekit ]
+ [ 95led > 95packagekit ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95led ]
+ [ -f /usr/lib/pm-utils/sleep.d/95led ]
+ hook=/usr/lib/pm-utils/sleep.d/95led
+ run_hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95led thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/95led thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95led thaw hibernate:
/usr/lib/pm-utils/sleep.d/95led thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/95led
+ local hook=95led
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95led ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:led ]
+ [ -x /usr/lib/pm-utils/sleep.d/95led ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95led thaw hibernate
+ hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=95led
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95led ]
+ [ 95anacron > 95led ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/95anacron ]
+ [ -f /usr/lib/pm-utils/sleep.d/95anacron ]
+ hook=/usr/lib/pm-utils/sleep.d/95anacron
+ run_hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:
/usr/lib/pm-utils/sleep.d/95anacron thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/95anacron
+ local hook=95anacron
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:95anacron ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:anacron ]
+ [ -x /usr/lib/pm-utils/sleep.d/95anacron ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/95anacron thaw hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=95anacron
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 95anacron ]
+ [ 94cpufreq > 95anacron ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/94cpufreq ]
+ [ -f /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ hook=/usr/lib/pm-utils/sleep.d/94cpufreq
+ run_hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/94cpufreq
+ local hook=94cpufreq
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:94cpufreq ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:cpufreq ]
+ [ -x /usr/lib/pm-utils/sleep.d/94cpufreq ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/94cpufreq thaw hibernate
+ command_exists service
+ type service
+ return 0
+ [ -d /sys/devices/system/cpu/ ]
+ thaw_cpufreq
+ cd /sys/devices/system/cpu/
+ [ -f cpu[0-9]*/cpufreq/scaling_governor ]
+ continue
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=94cpufreq
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 94cpufreq ]
+ [ 90clock > 94cpufreq ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/90clock ]
+ [ -f /usr/lib/pm-utils/sleep.d/90clock ]
+ hook=/usr/lib/pm-utils/sleep.d/90clock
+ run_hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/90clock thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/90clock thaw hibernate:
/usr/lib/pm-utils/sleep.d/90clock thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/90clock
+ local hook=90clock
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:90clock ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:clock ]
+ [ -x /usr/lib/pm-utils/sleep.d/90clock ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/90clock thaw hibernate
+ command_exists service
+ type service
+ return 0
+ is_set 
+ return 2
+ exit 254
+ hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=90clock
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 90clock ]
+ [ 75modules > 90clock ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/75modules ]
+ [ -f /usr/lib/pm-utils/sleep.d/75modules ]
+ hook=/usr/lib/pm-utils/sleep.d/75modules
+ run_hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/75modules thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/75modules thaw hibernate:
/usr/lib/pm-utils/sleep.d/75modules thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/75modules
+ local hook=75modules
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:75modules ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:modules ]
+ [ -x /usr/lib/pm-utils/sleep.d/75modules ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/75modules thaw hibernate
+ command_exists service
+ type service
+ return 0
+ resume_modules
+ modreload
+ [ -O /var/run/pm-utils/pm-suspend/storage/module:* ]
+ continue
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=75modules
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 75modules ]
+ [ 55NetworkManager > 75modules ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/55NetworkManager ]
+ [ -f /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ hook=/usr/lib/pm-utils/sleep.d/55NetworkManager
+ run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:
/usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/55NetworkManager
+ local hook=55NetworkManager
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:55NetworkManager ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:NetworkManager ]
+ [ -x /usr/lib/pm-utils/sleep.d/55NetworkManager ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/55NetworkManager thaw hibernate
+ command_exists service
+ type service
+ return 0
+ resume_nm
+ dbus_send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
+ command dbus-send --print-reply --system --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.NetworkManager.wake
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=55NetworkManager
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 55NetworkManager ]
+ [ 49bluetooth > 55NetworkManager ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/49bluetooth ]
+ [ -f /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ hook=/usr/lib/pm-utils/sleep.d/49bluetooth
+ run_hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:
/usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/49bluetooth
+ local hook=49bluetooth
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:49bluetooth ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:bluetooth ]
+ [ -x /usr/lib/pm-utils/sleep.d/49bluetooth ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/49bluetooth thaw hibernate
+ command_exists service
+ type service
+ return 0
+ [ -f /proc/acpi/ibm/bluetooth ]
+ exit 254
+ hook_exit_status 254
+ log not applicable.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ not applicable. = -n ]
+ printf %s\n not applicable.
not applicable.
+ LAST_HOOK=49bluetooth
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 49bluetooth ]
+ [ 10_unattended-upgrades-hibernate > 49bluetooth ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ hook=/etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate
+ _run_hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate
+ log -n /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate:+ hook_ok /etc/pm/sleep.d/10_unattended-upgrades-hibernate
+ local hook=10_unattended-upgrades-hibernate
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_unattended-upgrades-hibernate ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_unattended-upgrades-hibernate ]
+ [ -x /etc/pm/sleep.d/10_unattended-upgrades-hibernate ]
+ return 0
+ /etc/pm/sleep.d/10_unattended-upgrades-hibernate thaw hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_unattended-upgrades-hibernate
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 10_unattended-upgrades-hibernate ]
+ [ 10_grub-common > 10_unattended-upgrades-hibernate ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/10_grub-common ]
+ hook=/etc/pm/sleep.d/10_grub-common
+ run_hook /etc/pm/sleep.d/10_grub-common thaw hibernate
+ _run_hook /etc/pm/sleep.d/10_grub-common thaw hibernate
+ log -n /etc/pm/sleep.d/10_grub-common thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /etc/pm/sleep.d/10_grub-common thaw hibernate:
/etc/pm/sleep.d/10_grub-common thaw hibernate:+ hook_ok /etc/pm/sleep.d/10_grub-common
+ local hook=10_grub-common
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:10_grub-common ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:_grub-common ]
+ [ -x /etc/pm/sleep.d/10_grub-common ]
+ return 0
+ /etc/pm/sleep.d/10_grub-common thaw hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=10_grub-common
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 10_grub-common ]
+ [ 01PulseAudio > 10_grub-common ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/01PulseAudio ]
+ [ -f /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ hook=/usr/lib/pm-utils/sleep.d/01PulseAudio
+ run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/01PulseAudio
+ local hook=01PulseAudio
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:01PulseAudio ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:PulseAudio ]
+ [ -x /usr/lib/pm-utils/sleep.d/01PulseAudio ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate
+ command_exists service
+ type service
+ return 0
+ resume_pulse
+ get_pulse_users
+ test_pulse_system
+ getent passwd pulse
+ awk -F: {print $3}
+ PULSE_SYSTEM_USER=111
+ [ -z 111 ]
+ sed s/111//
+ tr -d  
+ ps -C pulseaudio -o uid=
+ getent passwd 1000
+ cut -f1 -d:
+ THIS_USER=qilmo
+ su qilmo -l -c -- ck-list-sessions | grep "active = TRUE"
+ restore_pulse_state sink qilmo
+ su qilmo -l -c -- pacmd list-${1}s | \
        sed -n "s/^[[:space:]*]*index: //p" | \
        while read index; do
            if state_exists pulse:"${2}":${1}${index}; then
                pacmd \
                    set-${1}-mute \
                    ${index} \
                    $(restorestate pulse:"${2}":${1}${index})
            fi
        done
+ restore_pulse_state source qilmo
+ su qilmo -l -c -- pacmd list-${1}s | \
        sed -n "s/^[[:space:]*]*index: //p" | \
        while read index; do
            if state_exists pulse:"${2}":${1}${index}; then
                pacmd \
                    set-${1}-mute \
                    ${index} \
                    $(restorestate pulse:"${2}":${1}${index})
            fi
        done
+ su qilmo -l -c -- pacmd suspend false
+ break
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=01PulseAudio
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 01PulseAudio ]
+ [ 00powersave > 01PulseAudio ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00powersave ]
+ [ -f /usr/lib/pm-utils/sleep.d/00powersave ]
+ hook=/usr/lib/pm-utils/sleep.d/00powersave
+ run_hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/00powersave
+ local hook=00powersave
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00powersave ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:powersave ]
+ [ -x /usr/lib/pm-utils/sleep.d/00powersave ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00powersave thaw hibernate
+ command_exists service
+ type service
+ return 0
+ command_exists pm-powersave
+ type pm-powersave
+ return 0
+ pm-powersave
+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-powersave.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-powersave/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=kernel
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-powersave/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-powersave/storage/inhibit
+ PM_CMDLINE=
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-powersave.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/00sleep_module ]
+ [  ]
+ [  ]
+ [  ]
+ [  ]
+ set -a
+ . /etc/pm/config.d/00sleep_module
+ SUSPEND_MODULES= 
+ HOOK_BLACKLIST= 
+ ADD_PARAMETERS= 
+ DROP_PARAMETERS= 
+ set +a
+ [ -f /etc/pm/pm-powersave.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ is_set true
+ return 0
+ set -x
+ command_exists service
+ type service
+ return 0
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ kernel = auto ]
+ mod=/usr/lib/pm-utils/module.d/kernel
+ [ -f /usr/lib/pm-utils/module.d/kernel ]
+ . /usr/lib/pm-utils/module.d/kernel
+ [ -z  ]
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=kernel
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ HIBERNATE_MODULE=kernel
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n kernel ]
+ check_hibernate
+ [ -n kernel ]
+ is_set no
+ return 1
+ SUSPEND_HYBRID_MODULE=kernel
+ try_lock pm-powersave.lock
+ local lock=/var/run/pm-utils/locks/pm-powersave.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-powersave.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_powersave_lock 0
+ mkdir -p /var/run/pm-utils/pm-powersave/storage
+ rm -f /var/run/pm-utils/pm-powersave/storage/inhibit
+ [  = true -o  = false ]
+ [ !  ]
+ init_logfile /var/log/pm-powersave.log
+ [ -z /var/log/pm-powersave.log ]
+ [ -h /var/log/pm-powersave.log ]
+ [ -f /var/log/pm-powersave.log -a ! -O /var/log/pm-powersave.log ]
+ export LOGGING=true
+ exec
+ exit 0
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00powersave
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 00powersave ]
+ [ 00logging > 00powersave ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/00logging ]
+ [ -f /usr/lib/pm-utils/sleep.d/00logging ]
+ hook=/usr/lib/pm-utils/sleep.d/00logging
+ run_hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/00logging thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/00logging thaw hibernate:
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/00logging
+ local hook=00logging
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:00logging ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:logging ]
+ [ -x /usr/lib/pm-utils/sleep.d/00logging ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/00logging thaw hibernate
+ command_exists service
+ type service
+ return 0
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=00logging
+ IFS=

+ IFS= 	

+ [ reverse -a reverse = reverse -a 00logging ]
+ [ 000kernel-change > 00logging ]
+ [ ! reverse ]
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ return
+ [ -f /etc/pm/sleep.d/000kernel-change ]
+ [ -f /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ hook=/usr/lib/pm-utils/sleep.d/000kernel-change
+ run_hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate
+ _run_hook /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate
+ log -n /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ -n = -n ]
+ fmt=%s
+ shift
+ printf %s /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:
/usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate:+ hook_ok /usr/lib/pm-utils/sleep.d/000kernel-change
+ local hook=000kernel-change
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:000kernel-change ]
+ [ -f /var/run/pm-utils/pm-suspend/storage/disable_hook:0kernel-change ]
+ [ -x /usr/lib/pm-utils/sleep.d/000kernel-change ]
+ return 0
+ /usr/lib/pm-utils/sleep.d/000kernel-change thaw hibernate
+ hook_exit_status 0
+ log success.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ success. = -n ]
+ printf %s\n success.
success.
+ LAST_HOOK=000kernel-change
+ IFS=

+ IFS= 	

+ inhibited
+ [ -f /var/run/pm-utils/pm-suspend/storage/inhibit ]
+ return 0
+ date
+ log Wed Oct 12 18:34:26 PDT 2011: Finished.
+ is_set true
+ return 0
+ local fmt=%s\n
+ [ Wed Oct 12 18:34:26 PDT 2011: Finished. = -n ]
+ printf %s\n Wed Oct 12 18:34:26 PDT 2011: Finished.
Wed Oct 12 18:34:26 PDT 2011: Finished.
+ exit 0
+ remove_suspend_lock
+ release_lock pm-suspend.lock
+ local lock=/var/run/pm-utils/locks/pm-suspend.lock
+ rm -f /var/run/pm-utils/locks/pm-suspend.lock
+ return 0
```

---

### Post by Toz on 2011-10-12
In your log file, you have a custom script running at the end of the hibernate phase: /etc/pm/sleep.d/action_wpa. Do you recall why it was placed there? Can you share the contents of that file?

---

### Post by Wadcutter on 2011-10-13
> In your log file, you have a custom script running at the end of the hibernate phase: /etc/pm/sleep.d/action_wpa. Do you recall why it was placed there? Can you share the contents of that file?

I don't know a thing about it--why it's there or what it means. Seems to have been written two years ago, which, to the best of my memory, is prior to my installing Ubuntu. So it probably came with the installation files??? But here it is:

```
#!/bin/sh

# Action script to enable/disable wpa-roam interfaces in reaction to
# pm-action or ifplugd events.
#
# Copyright: Copyright (c) 2008-2009, Kel Modderman <kel@otaku42.de>
# License:   GPL-2
#

PATH=/sbin:/usr/sbin:/bin:/usr/bin

if [ ! -x /sbin/wpa_action ]; then
	exit 0
fi

SELF=action_wpa
COMMAND=
IFPLUGD_IFACE=

# pm-action(8) - <action> <suspend method>
#
# On suspend|hibernate, disconnect any wpa-roam managed interfaces,
# reconnect it on resume.

case "${1}" in
        suspend|hibernate)
                COMMAND=disconnect
                ;;
        resume|thaw)
                COMMAND=reconnect
                ;;
esac

if [ -z "$COMMAND" ]; then
	# ifplugd(8) - <iface> <action>
	#
	# If an ifplugd managed interface is brought up, disconnect any
	# wpa-roam managed interfaces so that only one "roaming" interface
	# remains active on the system.

	IFPLUGD_IFACE="${1}"

	case "${2}" in
		up)
			COMMAND=disconnect
			;;
		down)
			COMMAND=reconnect
			;;
		*)
			echo "${SELF}: unknown $0 arguments: ${@}" >&2
			exit 1
			;;
        esac
fi

if [ -z "$COMMAND" ]; then
	echo "${SELF}: unknown arguments: ${@}" >&2
	exit 1
fi

for CTRL in /var/run/wpa_supplicant/*; do
	[ -S "${CTRL}" ] || continue

	IFACE="${CTRL#/var/run/wpa_supplicant/}"

	wpa_action "${IFACE}" check || continue

	if [ "${IFPLUGD_IFACE}" ] && [ "${IFPLUGD_IFACE}" = "${IFACE}" ]; then
		# if ifplugd is managing this interface (not likely but..)
		# do nothing
		continue
	fi

	wpa_cli -i "${IFACE}" "${COMMAND}"
done
```

---

### Post by Toz on 2011-10-13
What does the following return:
```
cat /sys/power/disk
```



Perhaps you can give uswsusp a try.
```
sudo apt-get install uswsusp
```
...then, when it's installed:
```
sudo update-initramfs -u
```
...then, 
```
sudo s2disk
```
...if you get an error about your system not being on the whitelist, try:
```
sudo s2disk -f
```

---

### Post by Wadcutter on 2011-10-13
> What does the following return:

```
cat /sys/power/disk
[platform] test testproc shutdown reboot 

```

> Perhaps you can give uswsusp a try.

I followed your commands. First it seemed to say that uswsusp was already installed and up-to-date. Then I followed everything up to the end, except the last command was not needed as it made no mention of a whitelist. I got a screen with a lot of text on it and then a black screen. Had to re-boot, but when I did, it came back up with all my previous programs running (just like hibernate should).I then tested hibernate to see if anything had changed. It had not other than it also came back up like above with previous programs intact. I did have to log-in with my PW.

Toz:

I just noticed with my last post that we are into 3 pages. Microsoft wouldn't spend this much time on my problem, nor would Google, HP, DISH Network or Toyota. If you want to call it quits, please feel free to do so. I'm game to try things as long as you are, but I don't want to ride a free horse to death. I can live with a balky computer that won't hibernate properly when asked to do so. Perhaps when I upgrade to a newer ver of Ubuntu, it will resolve itself (if I do a clean install). 

I do understand problem-solving challenges. When I get my teeth into a problem, I don't want to eat, sleep, or do much of anything else until I've fixed it. But in this case, you are doing all of the problem solving and I am just standing around handing you hammers and screwdrivers. So it's your call as to when it's time to punch out the timecard and go home for good.

---

### Post by Toz on 2011-10-13
No worries. I'm actually enjoying this. However, I am starting to run out of ideas. Can you try the uswsusp suggestion from post #21? I have an old Toshiba laptop and the only way I could get hibernate and suspend to work on it was to use uswsusp. Maybe you will have the same luck.

---

### Post by Wadcutter on 2011-10-13
I did try it. Go back before my last post about quitting. I posted the results, then got to thinking about how much time being spent chasing this problem, so I made the second post. In any case, it seemed uswsusp was already installed and running the other commands didn't shut down the power.

---

### Post by Toz on 2011-10-14
Sorry, I missed that previous post. 

My gut feeling is that this is some sort of acpi problem. I've been looking at kernel parameters ([http://www.kernel.org/doc/Documentation/kernel-parameters.txt]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt")) and researching some documents (eg. [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868")), and two of the parameters have caught my eye:

acpi=force
acpi_sleep=nonvs

Possibly try them temporarily by editing the kernel command line during boot.

---

### Post by Wadcutter on 2011-10-15
Sorry, Toz, I had to leave home suddenly yesterday and haven't had time to try your latest suggestions, but am back and will work on it now. I'm not sure how to edit the kernal command but I seem to remember something about editing acpi in the original thread that I followed before starting my own. I'm going to go re-read that, too. I'll post again when I have something to report.

I looked at the links in your last post. The first was beyond my comprehension but the bug description of the second link ([https://bugs.launchpad.net/ubuntu/+s...20/+bug/104868](https://bugs.launchpad.net/ubuntu/+s...20/+bug/104868)) got my attention. It said:

> The PC does not shut off and i have to push and hold the power button for >4 seconds.
 For hibernate (that basically works)

That got me thinking that all I need to do to make things the way I want is to hit the power button for 4 seconds after clicking "hibernate"- a WORKAROUND!?! So I tried it and it works fine. It shuts down the power on the box and when I hit the power again, it (slowly, but surely, with the added step of asking for my password) comes back up with all my open programs and work intact.

As best I remember, things didn't work that way when I started this thread. I believe that forcing shutdown wiped out all open programs/work and necessitated a cold boot. The computer re-started, but hibernation was gone. And that was a problem!

So I think rather than messing around with acpi (I read of others who did so and lost their mouse or keyboards), I think I would rather live with the simple workaround of holding the power button for 4 seconds to complete the hibernate process. I know that is more or less giving in to a balky operating system and wastes some of the time we spent on it, but it makes a lot of sense to me (who has history with messing up computers by trying things I didn't fully understand). We did, at least, solidify the operation of the "hibernate" part (saving work in the swap file/partition). Thank you for your time and effort.

---

### Post by Toz on 2011-10-16
> **Wadcutter said:**
> I'm not sure how to edit the kernal command 
Have a look at this link: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot")

---

### Post by Toz on 2011-10-16
> **Wadcutter said:**
> Thank you for your time and effort.
No worries.

---

### Post by Wadcutter on 2011-10-16
> Have a look at this link: [https://help.ubuntu.com/community/Gr...nu_During_Boot](https://help.ubuntu.com/community/Gr...nu_During_Boot)

Thanks for that link, Toz. I will read it when I get the chance. Originally I had to edit Grub to change my dual boot system from Windows to Ubuntu default, so I've had a little experience with editing it.

---

