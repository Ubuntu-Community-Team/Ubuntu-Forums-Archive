---
title: "Computers rebooting unexpectedly"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by PaulHA2 on 2011-11-13
I have two computers, both Dells, one  less than a year old, one 4 years old. Both running 10.10, the new one with libreOffice, the old one with OpenOffice. Today, they both started rebooting unexpectedly and returning me to the login screen. I did a complete reinstall of 10.10 on the older machine, and after an hour or so, same problem again. The problem only happens (so far) when I'm running the office software, and there are no temperature issues with either machine. It's incredibly frustrating, and weird--two different machines same problem out of the blue, even after a clean reinstall? 

The only new software I've installed recently is Banshee and gpodder. 

A buggy recent update?

Any ideas?

---

### Post by Cyclane on 2011-11-14
What are the last entries in /var/log/syslog before your system reboots?

---

### Post by PaulHA2 on 2011-11-14
Thanks for the reply. Can you tell me how to get that data?

---

### Post by Cyclane on 2011-11-14
```
less /var/log/syslog
```
match the times with the moment your system rebooted and copy/paste that between code tags in the forum.

---

### Post by PaulHA2 on 2011-11-14
Okay, got it. Don't know how much you need:

```
Nov 14 00:53:21 polarbear-Vostro-1400 NetworkManager[951]: <info> (eth1): device state change: 8 -> 3 (reason 38)
Nov 14 00:53:21 polarbear-Vostro-1400 NetworkManager[951]: <info> (eth1): deactivating device (reason: 38).
Nov 14 00:53:22 polarbear-Vostro-1400 NetworkManager[951]: <info> (eth1): canceled DHCP transaction, DHCP client pid 9456
Nov 14 00:53:23 polarbear-Vostro-1400 NetworkManager[951]: <error> [1321250003.13849] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Nov 14 00:53:23 polarbear-Vostro-1400 wpa_supplicant[1139]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 14 00:53:23 polarbear-Vostro-1400 avahi-daemon[29875]: Withdrawing address record for 192.168.1.69 on eth1.
Nov 14 00:53:23 polarbear-Vostro-1400 avahi-daemon[29875]: Leaving mDNS multicast group on interface eth1.IPv4 with address 192.168.1.69.
Nov 14 00:53:23 polarbear-Vostro-1400 avahi-daemon[29875]: Interface eth1.IPv4 no longer relevant for mDNS.
Nov 14 00:53:26 polarbear-Vostro-1400 acpid: client 9092[0:0] has disconnected
Nov 14 00:53:26 polarbear-Vostro-1400 acpid: client connected from 16825[0:0]
Nov 14 00:53:26 polarbear-Vostro-1400 acpid: 1 client rule loaded
Nov 14 00:53:26 polarbear-Vostro-1400 kernel: [24566.056191] Skipping EDID probe due to cached edid
Nov 14 00:53:26 polarbear-Vostro-1400 kernel: [24566.408111] Skipping EDID probe due to cached edid
Nov 14 00:53:28 polarbear-Vostro-1400 NetworkManager[951]: <error> [1321250008.271464] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Nov 14 00:53:29 polarbear-Vostro-1400 kernel: [24569.120196] Skipping EDID probe due to cached edid
Nov 14 00:53:29 polarbear-Vostro-1400 kernel: [24569.481208] Skipping EDID probe due to cached edid
Nov 14 00:53:30 polarbear-Vostro-1400 kernel: [24569.840216] Skipping EDID probe due to cached edid
Nov 14 00:53:30 polarbear-Vostro-1400 kernel: [24570.200215] Skipping EDID probe due to cached edid
Nov 14 00:53:32 polarbear-Vostro-1400 rtkit-daemon[1514]: Successfully made thread 16879 of process 16879 (n/a) owned by '113' high priority at nice level -11.
Nov 14 00:53:32 polarbear-Vostro-1400 rtkit-daemon[1514]: Supervising 1 threads of 1 processes of 1 users.
Nov 14 00:53:34 polarbear-Vostro-1400 gdm-simple-greeter[16872]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Nov 14 00:53:34 polarbear-Vostro-1400 rtkit-daemon[1514]: Successfully made thread 16881 of process 16879 (n/a) owned by '113' RT at priority 5.
Nov 14 00:53:34 polarbear-Vostro-1400 rtkit-daemon[1514]: Supervising 2 threads of 1 processes of 1 users.
Nov 14 00:53:34 polarbear-Vostro-1400 rtkit-daemon[1514]: Successfully made thread 16883 of process 16879 (n/a) owned by '113' RT at priority 5.
Nov 14 00:53:34 polarbear-Vostro-1400 rtkit-daemon[1514]: Supervising 3 threads of 1 processes of 1 users.
Nov 14 00:53:36 polarbear-Vostro-1400 gdm-simple-greeter[16872]: WARNING: Unable to lookup user name polarbea: Success
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 288.
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: snd_pcm_dump():
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: Soft volume PCM
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: Control: PCM Playback Volume
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: min_dB: -51
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: max_dB: 0
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: resolution: 256
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: Its setup is:
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   stream       : CAPTURE
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   format       : S16_LE
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   subformat    : STD
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   channels     : 2
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   rate         : 44100
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   msbits       : 16
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   buffer_size  : 88192
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   period_size  : 44096
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   period_time  : 999909
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   period_step  : 1
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   avail_min    : 87310
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   period_event : 0
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   start_threshold  : -1
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   stop_threshold   : 1444937728
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   silence_threshold: 0
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   silence_size : 0
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   boundary     : 1444937728
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c: Its setup is:
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   stream       : CAPTURE
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   format       : S16_LE
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   subformat    : STD
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   channels     : 2
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   rate         : 44100
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   msbits       : 16
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   buffer_size  : 88192
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   period_size  : 44096
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   period_time  : 999909
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   period_step  : 1
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   avail_min    : 87310
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   period_event : 0
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   start_threshold  : -1
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   stop_threshold   : 1444937728
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   silence_threshold: 0
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   silence_size : 0
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   boundary     : 1444937728
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   appl_ptr     : 87608
Nov 14 00:53:36 polarbear-Vostro-1400 pulseaudio[16879]: alsa-util.c:   hw_ptr       : 87608
Nov 14 00:53:37 polarbear-Vostro-1400 gdm-session-worker[16874]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Nov 14 00:53:45 polarbear-Vostro-1400 NetworkManager[951]: <error> [1321250025.750548] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Nov 14 00:53:45 polarbear-Vostro-1400 NetworkManager[951]: <error> [1321250025.807888] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
Nov 14 00:53:47 polarbear-Vostro-1400 kernel: [24586.861138] Skipping EDID probe due to cached edid
Nov 14 00:53:47 polarbear-Vostro-1400 kernel: [24587.221212] Skipping EDID probe due to cached edid
Nov 14 00:53:48 polarbear-Vostro-1400 kernel: [24587.581210] Skipping EDID probe due to cached edid
Nov 14 00:53:48 polarbear-Vostro-1400 kernel: [24587.940273] Skipping EDID probe due to cached edid
Nov 14 00:53:49 polarbear-Vostro-1400 rtkit-daemon[1514]: Successfully made thread 16977 of process 16977 (n/a) owned by '1000' high priority at nice level -11.
Nov 14 00:53:49 polarbear-Vostro-1400 rtkit-daemon[1514]: Supervising 4 threads of 2 processes of 2 users.
Nov 14 00:53:49 polarbear-Vostro-1400 pulseaudio[16977]: pid.c: Stale PID file, overwriting.
Nov 14 00:53:50 polarbear-Vostro-1400 rtkit-daemon[1514]: Successfully made thread 16992 of process 16977 (n/a) owned by '1000' RT at priority 5.
Nov 14 00:53:50 polarbear-Vostro-1400 rtkit-daemon[1514]: Supervising 5 threads of 2 processes of 2 users.
Nov 14 00:53:50 polarbear-Vostro-1400 rtkit-daemon[1514]: Successfully made thread 16994 of process 16977 (n/a) owned by '1000' RT at priority 5.
Nov 14 00:53:50 polarbear-Vostro-1400 rtkit-daemon[1514]: Supervising 6 threads of 2 processes of 2 users.
Nov 14 00:53:50 polarbear-Vostro-1400 rtkit-daemon[1514]: Successfully made thread 16997 of process 16997 (n/a) owned by '1000' high priority at nice level -11.
Nov 14 00:53:50 polarbear-Vostro-1400 rtkit-daemon[1514]: Supervising 7 threads of 3 processes of 2 users.
Nov 14 00:53:50 polarbear-Vostro-1400 pulseaudio[16997]: pid.c: Daemon already running.
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: snd_pcm_avail_delay() returned strange values: delay 0 is less than avail 128.
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: snd_pcm_dump():
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: Soft volume PCM
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: Control: PCM Playback Volume
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: min_dB: -51
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: max_dB: 0
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: resolution: 256
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: Its setup is:
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   stream       : CAPTURE
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   format       : S16_LE
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   subformat    : STD
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   channels     : 2
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   rate         : 44100
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   msbits       : 16
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   buffer_size  : 88192
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   period_size  : 44096
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   period_time  : 999909
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   period_step  : 1
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   avail_min    : 87310
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   period_event : 0
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   start_threshold  : -1
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   stop_threshold   : 1444937728
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   silence_threshold: 0
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   silence_size : 0
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   boundary     : 1444937728
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c: Its setup is:
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   stream       : CAPTURE
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   access       : MMAP_INTERLEAVED
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   format       : S16_LE
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   subformat    : STD
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   channels     : 2
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   rate         : 44100
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   exact rate   : 44100 (44100/1)
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   msbits       : 16
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   buffer_size  : 88192
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   period_size  : 44096
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   period_time  : 999909
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   tstamp_mode  : ENABLE
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   period_step  : 1
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   avail_min    : 87310
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   period_event : 0
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   start_threshold  : -1
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   stop_threshold   : 1444937728
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   silence_threshold: 0
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   silence_size : 0
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   boundary     : 1444937728
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   appl_ptr     : 87440
Nov 14 00:53:52 polarbear-Vostro-1400 pulseaudio[16977]: alsa-util.c:   hw_ptr       : 87440

```

---

### Post by PaulHA2 on 2011-11-14
Bump

---

### Post by PaulHA2 on 2011-11-14
Bump

---

