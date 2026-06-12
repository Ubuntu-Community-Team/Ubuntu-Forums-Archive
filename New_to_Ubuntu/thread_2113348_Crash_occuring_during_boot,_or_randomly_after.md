---
title: "Crash occuring during boot, or randomly after"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by 5mon on 2013-02-07
I am having a hard time since yesterday with my computer crashing.

My windows partition crashes as well, so I guess the issue is hardware.

I removed the graphics card, now I use the intel integrated chipset which put the radeon out of the equation ...

I also made a memory test which passed, and I booted from another disk and the crash occured .
I tried to fsck (after starting in recovery mode), but the fsck command doesn't seem to do anything ... I get one line saying x files out of y, and that's all.

On the last segfault I got that :

Feb  7 11:22:29 poibuntu kernel: [  400.340775] double fault: 0000 [#1] SMP 
Feb  7 11:22:29 poibuntu kernel: [  400.340803] CPU 1 
Feb  7 11:22:29 poibuntu kernel: [  400.340814] Modules linked in: dm_crypt rfcomm bnep bluetooth arc4 binfmt_misc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi ath5k ath snd_rawmidi psmouse joydev snd_seq_midi_event mac80211 snd_seq snd_timer serio_raw snd_seq_device cfg80211 snd soundcore snd_page_alloc parport_pc mac_hid lp parport hid_logitech_dj usbhid hid firewire_ohci floppy firewire_core crc_itu_t i915 sky2 drm_kms_helper drm i2c_algo_bit video
Feb  7 11:22:29 poibuntu kernel: [  400.341045] 
Feb  7 11:22:29 poibuntu kernel: [  400.341054] Pid: 1082, comm: Xorg Not tainted 3.2.0-37-generic #58-Ubuntu Shuttle Inc SG31/FG31
Feb  7 11:22:29 poibuntu kernel: [  400.341091] RIP: 0033:[<00007f7d442e27d8>]  [<00007f7d442e27d8>] 0x7f7d442e27d7
Feb  7 11:22:29 poibuntu kernel: [  400.341125] RSP: 002b:00007ffff995f900  EFLAGS: 00013202
Feb  7 11:22:29 poibuntu kernel: [  400.341147] RAX: 00007f7dffd680a0 RBX: 00007f7d4a882e40 RCX: 00007f7d4a0a3890
Feb  7 11:22:29 poibuntu kernel: [  400.341175] RDX: 0000000000000000 RSI: 000000000000013d RDI: 00007f7d4a062750
Feb  7 11:22:29 poibuntu kernel: [  400.341202] RBP: 00007f7d4a0a3890 R08: 0000000000000139 R09: 00000000000000ef
Feb  7 11:22:29 poibuntu kernel: [  400.341230] R10: 00007ffff995fca8 R11: 0000000000000136 R12: 00007f7d4a8b45f0
Feb  7 11:22:29 poibuntu kernel: [  400.341258] R13: 00007ffff99603e0 R14: 0000000000000003 R15: 0000000000000012
Feb  7 11:22:29 poibuntu kernel: [  400.341286] FS:  00007f7d47ecb880(0000) GS:ffff88012fc80000(0000) knlGS:0000000000000000
Feb  7 11:22:29 poibuntu kernel: [  400.341319] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Feb  7 11:22:29 poibuntu kernel: [  400.341341] CR2: 00007f7dffd680a0 CR3: 0000000127cfd000 CR4: 00000000000406e0
Feb  7 11:22:29 poibuntu kernel: [  400.341369] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Feb  7 11:22:29 poibuntu kernel: [  400.341397] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Feb  7 11:22:29 poibuntu kernel: [  400.341425] Process Xorg (pid: 1082, threadinfo ffff8801283e8000, task ffff880123bddc00)
Feb  7 11:22:29 poibuntu kernel: [  400.341457] 
Feb  7 11:22:29 poibuntu kernel: [  400.341465] RIP  [<00007f7d442e27d8>] 0x7f7d442e27d7
Feb  7 11:22:29 poibuntu kernel: [  400.341488]  RSP <00007ffff995f900>
Feb  7 11:22:29 poibuntu kernel: [  400.406317] ---[ end trace c0bafc3bfcfbd5b6 ]---
Feb  7 11:22:30 poibuntu kernel: [  401.800482] show_signal_msg: 36 callbacks suppressed
Feb  7 11:22:30 poibuntu kernel: [  401.800489] pulseaudio[2563]: segfault at 7f5c81191f39 ip 00007f5c81191f39 sp 00007fffbf19f2e0 error 14 in libX11.so.6.3.0[7f5c81033000+200000]

---

### Post by 5mon on 2013-02-07
Here are the kern.log, dmesg & syslog

---

