---
title: "Network Unclaimed"
date: 2012-08-21
forum: New to Ubuntu
---

### Post by sholton on 2012-08-21
I'm reporting the same issue, with possible additional info 

This is on a box with (correctly functioning) on-board LAN and a set of additional 4-port LAN interfaces like:
                      product: ANA620xx/ANA69011A
                      vendor: Hynix Semiconductor (Hyundai Electronics)

The Linux kernel on the Ubuntu 11.10 **Desktop** CD (Ubuntu 3.0.0-12.20-generic 3.0.4) correctly identifies and initializes this hardware using the starfire driver. This is using the boot kernel on the install CD without installing.

The Linux kernel installed by the Ubuntu 11.10 **Server** CD (Ubuntu 3.0.0-24.40-generic-pae 3.0.38) fails to recognize the hardware.

A comparison of dmesg between the two systems shows some interesting stuff, notably:

[FONT=Courier New][SIZE=1][COLOR=Green]Desktop[/COLOR]: pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] 
[COLOR=Red]Server [/COLOR]:  pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff**f**][/SIZE][/FONT]

Later in boot:

[FONT=Courier New][SIZE=1][COLOR=Green]Desktop[/COLOR]: pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[/SIZE][/FONT] [FONT=Courier New][SIZE=1][COLOR=Red]Server [/COLOR]:   pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff**f**][/SIZE][/FONT]

After that, the [FONT=Courier New][SIZE=1][COLOR=Green]Desktop[/COLOR] [/SIZE][/FONT]boot sequence shows what looks like a normal initialization for this hardware:

[FONT=Courier New][SIZE=1] starfire.c:v1.03 7/26/2000  Written by Donald Becker <becker@scyld.com>* <snip>*
 starfire: polling (NAPI) enabled
 starfire 0000:08:04.0: PCI INT A -> GSI 48 (level, low) -> IRQ 48
*<snip>*
 starfire 0000:08:05.0: PCI INT A -> GSI 49 (level, low) -> IRQ 49
 eth1: Adaptec Starfire 6915 at f8200000, 00:00:d1:ef:f6:d2, IRQ 49.
*<snip>*
 eth1: MII PHY found at address 1, status 0x7809 advertising 0x01e1.
 eth1: scatter-gather and hardware TCP cksumming enabled.
 starfire 0000:08:06.0: PCI INT A -> GSI 50 (level, low) -> IRQ 50
 eth3: Adaptec Starfire 6915 at f8300000, 00:00:d1:ef:f6:d3, IRQ 50.
 eth3: MII PHY found at address 1, status 0x7809 advertising 0x01e1.
 eth3: scatter-gather and hardware TCP cksumming enabled.
 starfire 0000:08:07.0: PCI INT A -> GSI 51 (level, low) -> IRQ 51
 eth4: Adaptec Starfire 6915 at f8400000, 00:00:d1:ef:f6:d4, IRQ 51.
*<and so on...>*
[/SIZE][/FONT]
The [FONT=Courier New][SIZE=1][COLOR=Red]Server[/COLOR][/SIZE][/FONT] boot sequence at this point begins to show trouble:[FONT=Courier New]
 
[/FONT][FONT=Courier New][SIZE=1] starfire.c:v1.03 7/26/2000  Written by Donald Becker <becker@scyld.com>* <snip>*
 starfire: polling (NAPI) enabled
 starfire 0000:08:04.0: PCI INT A -> GSI 48 (level, low) -> IRQ 48
[COLOR=Red] ioremap: invalid physical address fffffffffe480000[/COLOR]
 ------------[ cut here ]------------
 WARNING: at /build/buildd/linux-3.0.0/arch/x86/mm/ioremap.c:83 __ioremap_caller+0x415/0x460()
 Hardware name:
 Modules linked in: starfire(+) floppy(+)
 Pid: 200, comm: modprobe Not tainted 3.0.0-24-generic-pae #40-Ubuntu
 Call Trace:
  [<c154b459>] ? printk+0x2d/0x2f
  [<c1050212>] warn_slowpath_common+0x72/0xa0
  [<c102eec5>] ? __ioremap_caller+0x415/0x460
  [<c102eec5>] ? __ioremap_caller+0x415/0x460
  [<c1050262>] warn_slowpath_null+0x22/0x30
  [<c102eec5>] __ioremap_caller+0x415/0x460
  [<c12ae48f>] ? __pci_request_selected_regions+0x3f/0x80
  [<f8414974>] ? starfire_init_one+0x10e/0x58b [starfire]
  [<c102ef8f>] ioremap_nocache+0x1f/0x30
  [<f8414974>] ? starfire_init_one+0x10e/0x58b [starfire]
  [<f8414974>] starfire_init_one+0x10e/0x58b [starfire]
  [<c102e048>] ? default_spin_lock_flags+0x8/0x10
  [<c155f45d>] ? _raw_spin_lock_irqsave+0x2d/0x40
*<snip>*
  [<c12aead7>] local_pci_probe+0x47/0xb0
  [<c12aff28>] pci_device_probe+0x68/0x90
  [<c1193f17>] ? sysfs_create_link+0x17/0x20
  [<c136224d>] really_probe+0x4d/0x150
  [<c136a699>] ? pm_runtime_barrier+0x49/0xb0
  [<c136248a>] driver_probe_device+0x3a/0x60
  [<c1362541>] __driver_attach+0x91/0xa0
  [<c13624b0>] ? driver_probe_device+0x60/0x60
  [<c13615c9>] bus_for_each_dev+0x49/0x70
  [<c1362081>] driver_attach+0x21/0x30
  [<c13624b0>] ? driver_probe_device+0x60/0x60
  [<c1361d5f>] bus_add_driver+0x17f/0x260
  [<c12aff50>] ? pci_device_probe+0x90/0x90
  [<c1362a16>] driver_register+0x66/0x110
  [<c12afcd3>] __pci_register_driver+0x43/0xc0
  [<f8419030>] starfire_init+0x30/0x1000 [starfire]
  [<c1003035>] do_one_initcall+0x35/0x170
  [<f8419000>] ? 0xf8418fff
  [<c108b9ed>] sys_init_module+0xad/0x210
  [<c155f644>] syscall_call+0x7/0xb
 ---[ end trace 1a4de1e3102c90d4 ]---
[COLOR=Red] starfire 0: cannot remap 0x80000 @ 0xfe480000, aborting[/COLOR]
 aic79xx 0000:04:03.0: PCI INT A -> GSI 26 (level, low) -> IRQ 26
 starfire 0000:08:05.0: PCI INT A -> GSI 49 (level, low) -> IRQ 49
[COLOR=Red] ioremap: invalid physical address fffffffffe380000[/COLOR]
[COLOR=Red] starfire 1: cannot remap 0x80000 @ 0xfe380000, aborting[/COLOR]
 starfire 0000:08:06.0: PCI INT A -> GSI 50 (level, low) -> IRQ 50
[COLOR=Red] ioremap: invalid physical address fffffffffe300000
 starfire 2: cannot remap 0x80000 @ 0xfe300000, aborting[/COLOR]
 starfire 0000:08:07.0: PCI INT A -> GSI 51 (level, low) -> IRQ 51
[COLOR=Red] ioremap: invalid physical address fffffffffe200000
 starfire 3: cannot remap 0x80000 @ 0xfe200000, aborting[/COLOR]
*<and so on...>*[/SIZE][/FONT]

My main question (for kernel hackers) is: what is "bridge window" and why is it being calculated differently for the same hardware between two similar kernels?

---

### Post by oldos2er on 2012-08-21
Post moved to its own thread.

---

