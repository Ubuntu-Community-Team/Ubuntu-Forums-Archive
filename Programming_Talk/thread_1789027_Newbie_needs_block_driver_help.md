---
title: "Newbie needs block driver help"
date: 2011-06-23
forum: Programming Talk
---

### Post by pauldemet on 2011-06-23
I am writing my first block driver and everything appears OK. After initialization, I do get this annoying warning message for add_disk. Would like to resolve this issue. All help is appreciated.
 
```

[ 326.427370] $Id: ssd.c, v 1.0 2011-06-20 paul Exp $
[ 326.432040] SSD - Base I/O Address = 0210
[ 326.434845] SSD - Major number 251 assigned
[ 326.437764] ------------[ cut here ]------------
[ 326.437780] WARNING: at /build/buildd/linux-2.6.32/block/genhd.c:527 add_disk+0x10d/0x150()
[ 326.437786] Hardware name: EPX-C380 SBC
[ 326.437790] Modules linked in: ssd(+) uio48 snd_hda_codec_via fbcon tileblit font bitblit softcursor vga16fb vgastate snd_hda_intel snd_hda_codec snd_hwdep snd_pcm i915 snd_timer drm_kms_helper snd drm i2c_algo_bit soundcore intel_agp serio_raw video snd_page_alloc output agpgart lp parport usb_storage usbhid hid e1000e [last unloaded: ssd]
[ 326.437850] Pid: 1230, comm: modprobe Tainted: G W 2.6.32-31-generic #61-Ubuntu
[ 326.437855] Call Trace:
[ 326.437866] [<c014cf92>] warn_slowpath_common+0x72/0xa0
[ 326.437875] [<c034380d>] ? add_disk+0x10d/0x150
[ 326.437882] [<c034380d>] ? add_disk+0x10d/0x150
[ 326.437890] [<c014cfda>] warn_slowpath_null+0x1a/0x20
[ 326.437897] [<c034380d>] add_disk+0x10d/0x150
[ 326.437907] [<f87a91b1>] ssd_init+0x1b1/0x1ed [ssd]
[ 326.437915] [<c0101131>] do_one_initcall+0x31/0x190
[ 326.437923] [<f87a9000>] ? ssd_init+0x0/0x1ed [ssd]
[ 326.437932] [<c01830a0>] sys_init_module+0xb0/0x210
[ 326.437940] [<c01033ec>] syscall_call+0x7/0xb
[ 326.437949] [<c0590000>] ? do_debug+0x130/0x160
[ 326.437954] ---[ end trace 874b2931712055bf ]---

```

---

