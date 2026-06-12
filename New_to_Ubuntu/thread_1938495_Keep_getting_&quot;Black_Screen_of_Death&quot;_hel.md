---
title: "Keep getting &quot;Black Screen of Death&quot; help me find out why?"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by hopelessone on 2012-03-09
Hi,

Computer keeps freezing more than once a day, I looked at the logs but can't figure out whats wrong and more importantly how can I fix it?

Here are the logs from where it happens;
```
Mar 10 10:59:48 oneiric kernel: [13017.115677] general protection fault: 0000 [#1] SMP 
Mar 10 10:59:48 oneiric kernel: [13017.115737] CPU 0 
Mar 10 10:59:48 oneiric kernel: [13017.115755] Modules linked in: bnep rfcomm bluetooth pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv binfmt_misc tda1004x saa7134_dvb videobuf_dvb dvb_core saa7134_alsa snd_hda_codec_via snd_usb_audio snd_usbmidi_lib uvcvideo ppdev tda827x snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi snd_rawmidi tda8290 snd_seq_midi_event snd_seq tuner serio_raw snd_timer snd_seq_device i915 snd parport_pc asus_atk0110 ir_lirc_codec lirc_dev ir_sony_decoder ir_jvc_decoder drm_kms_helper ir_rc6_decoder drm soundcore ir_rc5_decoder snd_page_alloc rc_asus_pc39 i2c_algo_bit video ir_nec_decoder saa7134 rc_core videobuf_dma_sg videobuf_core v4l2_common videodev v4l2_compat_ioctl32 tveeprom lp parport usbhid hid sata_sil r8169
Mar 10 10:59:48 oneiric kernel: [13017.116481] 
Mar 10 10:59:48 oneiric kernel: [13017.116498] Pid: 1284, comm: Xorg Not tainted 3.0.0-16-generic #28-Ubuntu System manufacturer System Product Name/P5G41C-M LX
Mar 10 10:59:48 oneiric kernel: [13017.116593] RIP: 0010:[<ffffffff81169889>]  [<ffffffff81169889>] fput+0x9/0x30
Mar 10 10:59:48 oneiric kernel: [13017.116659] RSP: 0018:ffff880102ee3988  EFLAGS: 00010282
Mar 10 10:59:48 oneiric kernel: [13017.116702] RAX: 0000000000000282 RBX: ffff8800d8432550 RCX: ffff8800d7ed6208
Mar 10 10:59:48 oneiric kernel: [13017.116757] RDX: ffff8800d7ed6208 RSI: 0000000000000282 RDI: 01bca192696e80ed
Mar 10 10:59:48 oneiric kernel: [13017.116812] RBP: ffff880102ee3988 R08: 0000000000000000 R09: ffff8801059e1ed8
Mar 10 10:59:48 oneiric kernel: [13017.116868] R10: 0000000000000001 R11: 0000000000000000 R12: fffffffffffffd40
Mar 10 10:59:48 oneiric kernel: [13017.116922] R13: ffff8800d84327d0 R14: ffff8800d8432810 R15: ffff8800d8432010
Mar 10 10:59:48 oneiric kernel: [13017.116978] FS:  00007ff5fe9058a0(0000) GS:ffff88011fc00000(0000) knlGS:0000000000000000
Mar 10 10:59:48 oneiric kernel: [13017.117041] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 10 10:59:48 oneiric kernel: [13017.117086] CR2: 00007f7cd40ecae8 CR3: 00000001029c5000 CR4: 00000000000406f0
Mar 10 10:59:48 oneiric kernel: [13017.117141] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 10 10:59:48 oneiric kernel: [13017.117196] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar 10 10:59:48 oneiric kernel: [13017.117252] Process Xorg (pid: 1284, threadinfo ffff880102ee2000, task ffff8801029ddc80)
Mar 10 10:59:48 oneiric kernel: [13017.119181] Stack:
Mar 10 10:59:48 oneiric kernel: [13017.119594]  ffff880102ee39d8 ffffffff8117add2 ffff880102ee39d8 ffff8800d8432000
Mar 10 10:59:48 oneiric kernel: [13017.119594]  ffff880102ee39d8 0000000000000036 0000000000000036 0040000000000000
Mar 10 10:59:48 oneiric kernel: [13017.119594]  003fffffffe0760a ffff8800ac29ab40 ffff880102ee3d68 ffffffff8117b907
Mar 10 10:59:48 oneiric kernel: [13017.119594] Call Trace:
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff8117add2>] poll_freewait+0xa2/0xe0
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff8117b907>] do_select+0x557/0x600
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff8117ae10>] ? poll_freewait+0xe0/0xe0
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff8117af00>] ? __pollwait+0xf0/0xf0
Mar 10 10:59:48 oneiric kernel: last message repeated 8 times
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff8117bb9c>] core_sys_select+0x1ec/0x370
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff81085cb0>] ? hrtimer_try_to_cancel+0x50/0xc0
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff81010fe9>] ? read_tsc+0x9/0x20
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff8108cbed>] ? ktime_get_ts+0xad/0xe0
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff8117bf70>] sys_select+0xc0/0x100
Mar 10 10:59:48 oneiric kernel: [13017.119594]  [<ffffffff815faac2>] system_call_fastpath+0x16/0x1b
Mar 10 10:59:48 oneiric kernel: [13017.119594] Code: 85 c0 0f 84 b7 fe ff ff 31 d2 48 89 de 83 cf ff ff d0 e9 9f fe ff ff 66 66 2e 0f 1f 84 00 00 00 00 00 55 48 89 e5 66 66 66 66 90 <f0> 48 ff 4f 30 0f 94 c0 84 c0 75 0b 5d c3 66 0f 1f 84 00 00 00 
Mar 10 10:59:48 oneiric kernel: [13017.119594] RIP  [<ffffffff81169889>] fput+0x9/0x30
Mar 10 10:59:48 oneiric kernel: [13017.119594]  RSP <ffff880102ee3988>
Mar 10 10:59:48 oneiric kernel: [13017.195412] ---[ end trace 7baa06c3bb86ecb9 ]---
Mar 10 10:59:49 oneiric gnome-session[1464]: WARNING: Client '/org/gnome/SessionManager/Client4' failed to reply before timeout
Mar 10 10:59:53 oneiric pulseaudio[7400]: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
Mar 10 10:59:53 oneiric pulseaudio[7401]: [pulseaudio] client-conf-x11.c: xcb_connection_has_error() returned true
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Successfully made thread 7404 of process 7404 (n/a) owned by '1000' high priority at nice level -11.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Supervising 1 threads of 1 processes of 1 users.
Mar 10 10:59:53 oneiric pulseaudio[7404]: [pulseaudio] pid.c: Stale PID file, overwriting.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Successfully made thread 7406 of process 7404 (n/a) owned by '1000' RT at priority 5.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Supervising 2 threads of 1 processes of 1 users.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Successfully made thread 7407 of process 7404 (n/a) owned by '1000' RT at priority 5.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Supervising 3 threads of 1 processes of 1 users.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Successfully made thread 7408 of process 7404 (n/a) owned by '1000' RT at priority 5.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Supervising 4 threads of 1 processes of 1 users.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Successfully made thread 7409 of process 7404 (n/a) owned by '1000' RT at priority 5.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Supervising 5 threads of 1 processes of 1 users.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Successfully made thread 7412 of process 7412 (n/a) owned by '1000' high priority at nice level -11.
Mar  9 23:59:53 oneiric rtkit-daemon[1780]: Supervising 6 threads of 2 processes of 1 users.
Mar 10 10:59:53 oneiric pulseaudio[7412]: [pulseaudio] pid.c: Daemon already running.
Mar 10 10:59:56 oneiric vdr: [2945] frontend 0/0 lost lock on channel 1, tp 177
Mar 10 10:59:57 oneiric vdr: [2945] frontend 0/0 regained lock on channel 1, tp 177
Mar 10 11:00:00 oneiric vdr: [2945] frontend 0/0 lost lock on channel 1, tp 177
Mar 10 11:00:00 oneiric vdr: [2945] frontend 0/0 regained lock on channel 1, tp 177
Mar 10 11:00:04 oneiric vdr: [2945] frontend 0/0 lost lock on channel 1, tp 177
Mar 10 11:00:04 oneiric vdr: [2945] frontend 0/0 regained lock on channel 1, tp 177
Mar 10 11:00:19 oneiric kernel: [13048.173768] BUG: unable to handle kernel NULL pointer dereference at 0000000000000610
Mar 10 11:00:19 oneiric kernel: [13048.174845] IP: [<ffffffff810329d9>] __ticket_spin_lock+0x9/0x20
Mar 10 11:00:19 oneiric kernel: [13048.175862] PGD 3640d067 PUD 366bc067 PMD 0 
Mar 10 11:00:19 oneiric kernel: [13048.176877] Oops: 0002 [#2] SMP 
Mar 10 11:00:19 oneiric kernel: [13048.177545] CPU 0 
Mar 10 11:00:19 oneiric kernel: [13048.177545] Modules linked in: bnep rfcomm bluetooth pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv binfmt_misc tda1004x saa7134_dvb videobuf_dvb dvb_core saa7134_alsa snd_hda_codec_via snd_usb_audio snd_usbmidi_lib uvcvideo ppdev tda827x snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi snd_rawmidi tda8290 snd_seq_midi_event snd_seq tuner serio_raw snd_timer snd_seq_device i915 snd parport_pc asus_atk0110 ir_lirc_codec lirc_dev ir_sony_decoder ir_jvc_decoder drm_kms_helper ir_rc6_decoder drm soundcore ir_rc5_decoder snd_page_alloc rc_asus_pc39 i2c_algo_bit video ir_nec_decoder saa7134 rc_core videobuf_dma_sg videobuf_core v4l2_common videodev v4l2_compat_ioctl32 tveeprom lp parport usbhid hid sata_sil r8169
Mar 10 11:00:19 oneiric kernel: [13048.178674] 
Mar 10 11:00:19 oneiric kernel: [13048.178674] Pid: 1658, comm: gnome-settings- Tainted: G      D     3.0.0-16-generic #28-Ubuntu System manufacturer System Product Name/P5G41C-M LX
Mar 10 11:00:19 oneiric kernel: [13048.178674] RIP: 0010:[<ffffffff810329d9>]  [<ffffffff810329d9>] __ticket_spin_lock+0x9/0x20
Mar 10 11:00:19 oneiric kernel: [13048.178674] RSP: 0018:ffff8800366a59e8  EFLAGS: 00010082
Mar 10 11:00:19 oneiric kernel: [13048.178674] RAX: 0000000000010000 RBX: 0000000000000082 RCX: 00000000000000c3
Mar 10 11:00:19 oneiric kernel: [13048.178674] RDX: 0000000000000001 RSI: 0000000000000082 RDI: 0000000000000610
Mar 10 11:00:19 oneiric kernel: [13048.178674] RBP: ffff8800366a59e8 R08: 00000000000000c3 R09: 0000000000000003
Mar 10 11:00:19 oneiric kernel: [13048.178674] R10: ffff88011f00c800 R11: 0000000000000293 R12: 0000000000000610
Mar 10 11:00:19 oneiric kernel: [13048.178674] R13: 0000000000000001 R14: 00000000000000c3 R15: 0000000000000001
Mar 10 11:00:19 oneiric kernel: [13048.178674] FS:  00007f1e6ffe9940(0000) GS:ffff88011fc00000(0000) knlGS:0000000000000000
Mar 10 11:00:19 oneiric kernel: [13048.178674] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 10 11:00:19 oneiric kernel: [13048.178674] CR2: 0000000000000610 CR3: 00000000366de000 CR4: 00000000000406f0
Mar 10 11:00:19 oneiric kernel: [13048.178674] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 10 11:00:19 oneiric kernel: [13048.178674] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar 10 11:00:19 oneiric kernel: [13048.178674] Process gnome-settings- (pid: 1658, threadinfo ffff8800366a4000, task ffff8800d8322e40)
Mar 10 11:00:19 oneiric kernel: [13048.178674] Stack:
Mar 10 11:00:19 oneiric kernel: [13048.178674]  ffff8800366a59f8 ffffffff81032a79 ffff8800366a5a18 ffffffff815f298e
Mar 10 11:00:19 oneiric kernel: [13048.178674]  0000000000000000 0000000000000610 ffff8800366a5a78 ffffffff81057259
Mar 10 11:00:19 oneiric kernel: [13048.178674]  0000000000000286 ffff8800366db000 ffff8800366a5a58 ffffffff81081dbd
Mar 10 11:00:19 oneiric kernel: [13048.178674] Call Trace:
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81032a79>] default_spin_lock_flags+0x9/0x10
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff815f298e>] _raw_spin_lock_irqsave+0x2e/0x40
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81057259>] try_to_wake_up+0x39/0x200
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81081dbd>] ? add_wait_queue+0x4d/0x60
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81057432>] default_wake_function+0x12/0x20
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff8117af66>] pollwake+0x66/0x70
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81057420>] ? try_to_wake_up+0x200/0x200
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81044b78>] __wake_up_common+0x58/0x90
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff810465b3>] __wake_up_sync_key+0x53/0x80
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff814cf1fe>] sock_def_readable+0x3e/0x70
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff8157247c>] unix_stream_sendmsg+0x2cc/0x470
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff814c9074>] do_sock_write.isra.11+0xd4/0xf0
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff814c90f3>] sock_aio_write+0x63/0x90
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff8103d38c>] ? ptep_set_access_flags+0x6c/0x70
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff814c9090>] ? do_sock_write.isra.11+0xf0/0xf0
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81168913>] do_sync_readv_writev+0xd3/0x110
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff8128421c>] ? security_file_permission+0x2c/0xb0
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81168011>] ? rw_verify_area+0x61/0xf0
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81168bcd>] do_readv_writev+0xcd/0x1d0
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff8104e6c9>] ? finish_task_switch+0x49/0xf0
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff815f01c4>] ? __schedule+0x3d4/0x700
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81168d0c>] vfs_writev+0x3c/0x50
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff81168e6a>] sys_writev+0x4a/0xb0
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff8117c376>] ? sys_poll+0x76/0x110
Mar 10 11:00:19 oneiric kernel: [13048.178674]  [<ffffffff815faac2>] system_call_fastpath+0x16/0x1b
Mar 10 11:00:19 oneiric kernel: [13048.178674] Code: 00 00 48 c7 c1 e1 27 03 81 48 c7 c2 de 27 03 81 e9 dd fe ff ff 90 90 90 90 90 90 90 90 90 90 90 90 90 55 b8 00 00 01 00 48 89 e5 <f0> 0f c1 07 0f b7 d0 c1 e8 10 39 c2 74 07 f3 90 0f b7 17 eb f5 
Mar 10 11:00:19 oneiric kernel: [13048.178674] RIP  [<ffffffff810329d9>] __ticket_spin_lock+0x9/0x20
Mar 10 11:00:19 oneiric kernel: [13048.178674]  RSP <ffff8800366a59e8>
Mar 10 11:00:19 oneiric kernel: [13048.178674] CR2: 0000000000000610
Mar 10 11:00:19 oneiric kernel: [13048.178674] ---[ end trace 7baa06c3bb86ecba ]---
Mar 10 11:00:49 oneiric kernel: [13078.148017] BUG: unable to handle kernel NULL pointer dereference at 0000000000000610
Mar 10 11:00:49 oneiric kernel: [13078.149502] IP: [<ffffffff810329d9>] __ticket_spin_lock+0x9/0x20
Mar 10 11:00:49 oneiric kernel: [13078.150978] PGD d8999067 PUD d88f7067 PMD 0 
Mar 10 11:00:49 oneiric kernel: [13078.151885] Oops: 0002 [#3] SMP 
Mar 10 11:00:49 oneiric kernel: [13078.151885] CPU 1 
Mar 10 11:00:49 oneiric kernel: [13078.151885] Modules linked in: bnep rfcomm bluetooth pci_stub vboxpci vboxnetadp vboxnetflt vboxdrv binfmt_misc tda1004x saa7134_dvb videobuf_dvb dvb_core saa7134_alsa snd_hda_codec_via snd_usb_audio snd_usbmidi_lib uvcvideo ppdev tda827x snd_hda_intel snd_hda_codec snd_hwdep snd_pcm psmouse snd_seq_midi snd_rawmidi tda8290 snd_seq_midi_event snd_seq tuner serio_raw snd_timer snd_seq_device i915 snd parport_pc asus_atk0110 ir_lirc_codec lirc_dev ir_sony_decoder ir_jvc_decoder drm_kms_helper ir_rc6_decoder drm soundcore ir_rc5_decoder snd_page_alloc rc_asus_pc39 i2c_algo_bit video ir_nec_decoder saa7134 rc_core videobuf_dma_sg videobuf_core v4l2_common videodev v4l2_compat_ioctl32 tveeprom lp parport usbhid hid sata_sil r8169
Mar 10 11:00:49 oneiric kernel: [13078.156564] 
Mar 10 11:00:49 oneiric kernel: [13078.156564] Pid: 1464, comm: gnome-session Tainted: G      D     3.0.0-16-generic #28-Ubuntu System manufacturer System Product Name/P5G41C-M LX
Mar 10 11:00:49 oneiric kernel: [13078.156564] RIP: 0010:[<ffffffff810329d9>]  [<ffffffff810329d9>] __ticket_spin_lock+0x9/0x20
Mar 10 11:00:49 oneiric kernel: [13078.156564] RSP: 0018:ffff8800d91379e8  EFLAGS: 00010082
Mar 10 11:00:49 oneiric kernel: [13078.156564] RAX: 0000000000010000 RBX: 0000000000000082 RCX: 00000000000000c3
Mar 10 11:00:49 oneiric kernel: [13078.156564] RDX: 0000000000000001 RSI: 0000000000000082 RDI: 0000000000000610
Mar 10 11:00:49 oneiric kernel: [13078.156564] RBP: ffff8800d91379e8 R08: 00000000000000c3 R09: 0000000000000003
Mar 10 11:00:49 oneiric kernel: [13078.156564] R10: ffff88011f00c800 R11: 0000000000000293 R12: 0000000000000610
Mar 10 11:00:49 oneiric kernel: [13078.156564] R13: 0000000000000001 R14: 00000000000000c3 R15: 0000000000000001
Mar 10 11:00:49 oneiric kernel: [13078.156564] FS:  00007fbad633a9a0(0000) GS:ffff88011fc80000(0000) knlGS:0000000000000000
Mar 10 11:00:49 oneiric kernel: [13078.156564] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Mar 10 11:00:49 oneiric kernel: [13078.156564] CR2: 0000000000000610 CR3: 00000000d8d1a000 CR4: 00000000000406e0
Mar 10 11:00:49 oneiric kernel: [13078.156564] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 10 11:00:49 oneiric kernel: [13078.156564] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar 10 11:00:49 oneiric kernel: [13078.156564] Process gnome-session (pid: 1464, threadinfo ffff8800d9136000, task ffff880036efc560)
Mar 10 11:00:49 oneiric kernel: [13078.156564] Stack:
Mar 10 11:00:49 oneiric kernel: [13078.156564]  ffff8800d91379f8 ffffffff81032a79 ffff8800d9137a18 ffffffff815f298e
Mar 10 11:00:49 oneiric kernel: [13078.156564]  0000000000000000 0000000000000610 ffff8800d9137a78 ffffffff81057259
Mar 10 11:00:49 oneiric kernel: [13078.156564]  0000000000000286 ffff880105b3b640 ffff8800d9137a58 ffffffff81081dbd
Mar 10 11:00:49 oneiric kernel: [13078.156564] Call Trace:
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81032a79>] default_spin_lock_flags+0x9/0x10
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff815f298e>] _raw_spin_lock_irqsave+0x2e/0x40
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81057259>] try_to_wake_up+0x39/0x200
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81081dbd>] ? add_wait_queue+0x4d/0x60
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81057432>] default_wake_function+0x12/0x20
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff8117af66>] pollwake+0x66/0x70
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81057420>] ? try_to_wake_up+0x200/0x200
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81044b78>] __wake_up_common+0x58/0x90
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff810465b3>] __wake_up_sync_key+0x53/0x80
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff814cf1fe>] sock_def_readable+0x3e/0x70
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff8157247c>] unix_stream_sendmsg+0x2cc/0x470
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff814c9074>] do_sock_write.isra.11+0xd4/0xf0
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff814c90f3>] sock_aio_write+0x63/0x90
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff8103d38c>] ? ptep_set_access_flags+0x6c/0x70
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff814c9090>] ? do_sock_write.isra.11+0xf0/0xf0
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81168913>] do_sync_readv_writev+0xd3/0x110
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff8128421c>] ? security_file_permission+0x2c/0xb0
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81168011>] ? rw_verify_area+0x61/0xf0
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81168bcd>] do_readv_writev+0xcd/0x1d0
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81010fe9>] ? read_tsc+0x9/0x20
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff8108cbed>] ? ktime_get_ts+0xad/0xe0
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81168d0c>] vfs_writev+0x3c/0x50
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff81168e6a>] sys_writev+0x4a/0xb0
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff8117c376>] ? sys_poll+0x76/0x110
Mar 10 11:00:49 oneiric kernel: [13078.156564]  [<ffffffff815faac2>] system_call_fastpath+0x16/0x1b
Mar 10 11:00:49 oneiric kernel: [13078.156564] Code: 00 00 48 c7 c1 e1 27 03 81 48 c7 c2 de 27 03 81 e9 dd fe ff ff 90 90 90 90 90 90 90 90 90 90 90 90 90 55 b8 00 00 01 00 48 89 e5 <f0> 0f c1 07 0f b7 d0 c1 e8 10 39 c2 74 07 f3 90 0f b7 17 eb f5 
Mar 10 11:00:49 oneiric kernel: [13078.156564] RIP  [<ffffffff810329d9>] __ticket_spin_lock+0x9/0x20
Mar 10 11:00:49 oneiric kernel: [13078.156564]  RSP <ffff8800d91379e8>
Mar 10 11:00:49 oneiric kernel: [13078.156564] CR2: 0000000000000610
Mar 10 11:00:49 oneiric kernel: [13078.156564] ---[ end trace 7baa06c3bb86ecbb ]---
Mar 10 11:00:53 oneiric vdr: [2945] frontend 0/0 lost lock on channel 11, tp 226
Mar 10 11:00:53 oneiric vdr: [2945] frontend 0/0 regained lock on channel 11, tp 226
Mar 10 11:00:56 oneiric vdr: [2945] frontend 0/0 lost lock on channel 11, tp 226
Mar 10 11:00:57 oneiric vdr: [2945] frontend 0/0 regained lock on channel 11, tp 226
Mar 10 11:01:00 oneiric vdr: [2945] frontend 0/0 lost lock on channel 11, tp 226
Mar 10 11:01:01 oneiric vdr: [2945] frontend 0/0 regained lock on channel 11, tp 226
Mar 10 11:01:04 oneiric vdr: [2945] frontend 0/0 lost lock on channel 11, tp 226
Mar 10 11:01:06 oneiric vdr: [2945] frontend 0/0 timed out while tuning to channel 11, tp 226
Mar 10 11:01:07 oneiric vdr: [2945] frontend 0/0 regained lock on channel 11, tp 226
Mar 10 11:01:19 oneiric vdr: [2945] frontend 0/0 timed out while tuning to channel 17, tp 536
Mar 10 11:01:19 oneiric acpid: client 1284[0:0] has disconnected
Mar 10 11:01:19 oneiric kernel: Kernel logging (proc) stopped.
Mar 10 11:01:19 oneiric rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="1109" x-info="http://www.rsyslog.com"] exiting on signal 15.
Mar 10 11:02:53 oneiric kernel: imklog 5.8.1, log source = /proc/kmsg started.
Mar 10 11:02:53 oneiric rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="1092" x-info="http://www.rsyslog.com"] start
Mar 10 11:02:53 oneiric rsyslogd: rsyslogd's groupid changed to 103
Mar 10 11:02:53 oneiric rsyslogd: rsyslogd's userid changed to 101
Mar 10 11:02:53 oneiric rsyslogd-2039: Could no open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Mar 10 11:02:53 oneiric polkitd[1111]: started daemon version 0.102 using authority implementation `local' version `0.102'
Mar 10 11:02:53 oneiric dbus[1094]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Mar 10 11:02:53 oneiric NetworkManager[1106]:    SCPlugin-Ifupdown: init!
Mar 10 11:02:53 oneiric NetworkManager[1106]:    SCPlugin-Ifupdown: update_system_hostname
Mar 10 11:02:53 oneiric NetworkManager[1106]:    SCPluginIfupdown: management mode: unmanaged
Mar 10 11:02:53 oneiric NetworkManager[1106]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0)
Mar 10 11:02:53 oneiric NetworkManager[1106]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 10 11:02:53 oneiric NetworkManager[1106]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 10 11:02:53 oneiric NetworkManager[1106]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 10 11:02:53 oneiric NetworkManager[1106]:    SCPlugin-Ifupdown: end _init.
Mar 10 11:02:53 oneiric NetworkManager[1106]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
```

Then the computer monitor turns black with the the above writing; computer has to be rebooted.

Please help me fix this frustrating problem..
Thanks in advance..

---

### Post by grahammechanical on 2012-03-09
What is this?

> Mar 10 11:00:53 oneiric vdr: [2945] frontend 0/0 lost lock on channel 11, tp 226
Mar 10 11:00:53 oneiric vdr: [2945] frontend 0/0 regained lock on channel 11, tp 226
Mar 10 11:00:56 oneiric vdr: [2945] frontend 0/0 lost lock on channel 11, tp 226
Mar 10 11:00:57 oneiric vdr: [2945] frontend 0/0 regained lock on channel 11, tp 226
Mar 10 11:01:00 oneiric vdr: [2945] frontend 0/0 lost lock on channel 11, tp 226
Mar 10 11:01:01 oneiric vdr: [2945] frontend 0/0 regained lock on channel 11, tp 226
Mar 10 11:01:04 oneiric vdr: [2945] frontend 0/0 lost lock on channel 11, tp 226
Mar 10 11:01:06 oneiric vdr: [2945] frontend 0/0 timed out while tuning to channel 11, tp 226
Mar 10 11:01:07 oneiric vdr: [2945] frontend 0/0 regained lock on channel 11, tp 226[FONT=monospace]

Are you running something that has a time setting like a screen saver has a time to activate or the way power saving activates after a time. I am guessing that it is Internet related.

Are you running some application that takes over the computer and then stops working but does not give you a desktop?

The word vdr and frontend indicate a Video Disk Recorder. Is this something to do with MythTV or Mythbuntu?

Is there not some key combination that you press to switch to a desktop?

Regards.

[/FONT]

---

### Post by hopelessone on 2012-03-10
Hi,

I have a TV Tuner card, and use VDR with XBMC as a media center.

I tried to switch using Ctrl+Alt+F Keys and cant switch.

It freezes while using different programs, so i know its not specific, or a power setting.

---

