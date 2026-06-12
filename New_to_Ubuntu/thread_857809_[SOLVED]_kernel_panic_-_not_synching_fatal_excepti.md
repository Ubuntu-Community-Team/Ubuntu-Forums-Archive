---
title: "[SOLVED] kernel panic - not synching fatal: exception in interrupt"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by victorbrca on 2008-07-12
Hi guys,


  One of my machines crashed after copying a few gigs of files over nautilus via SSH. I was able to reboot it via ssh, but upon coming up I got the msg:

> kernel panic - not synching fatal: exception in interrupt

  Tried booting into XP (dual boot) and it crashed after a couple of minutes

  Tried in recovery mode and got the same msg. Then I tried booting up with no apic, lapic and acpi and it came up, but froze again. I'm not even able to change tty.

  Any ideas?


Thanks,

Vic.

---

### Post by victorbrca on 2008-07-12
Just adding more info. This is what dmesg is showing when the system locks:

```
[ 43.295201 ] [<c03e3a85>] start_kernel +0x53/0xe0
[ 43.295281 ] [<c03e31f0>] unknown_bootoption +0x0/0x260
[ 43.295259 ] ===========================
[ 43.295401 ] Code: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 <00> 00 00
 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[ 43.297528 ] EIP: [<ec3d5a93>] 0xec3d5a93 SS :ESP 0068 :c03dfe48
[ 43.297640 ] Kernel panic - not syncing: Fatal exception in interrupt
```


Vic.

---

### Post by victorbrca on 2008-07-25
Looks like it might have been my motherboard!!

---

