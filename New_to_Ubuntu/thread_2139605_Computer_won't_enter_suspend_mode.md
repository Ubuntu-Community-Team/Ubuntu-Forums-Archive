---
title: "Computer won't enter suspend mode"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by shanepardue on 2013-04-27
I am running an intel DH67BL motherboard with the integrated graphics and my computer won't suspend. It turns off the monitors, but the computer stays powered. I don't have a problem in Debian Wheezy or Windows. Here's the portion of the system logs around the time of the issue. Thanks!

```
Apr 27 08:07:01 shane-desktop NetworkManager[1016]: <info> sleep requested (sleeping: no  enabled: yes)
Apr 27 08:07:01 shane-desktop NetworkManager[1016]: <info> sleeping or disabling...
Apr 27 08:07:01 shane-desktop NetworkManager[1016]: <info> (eth0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Apr 27 08:07:01 shane-desktop NetworkManager[1016]: <info> (eth0): deactivating device (reason 'sleeping') [37]
Apr 27 08:07:02 shane-desktop NetworkManager[1016]: <info> (eth0): canceled DHCP transaction, DHCP client pid 1116
Apr 27 08:07:02 shane-desktop avahi-daemon[993]: Withdrawing address record for 192.168.1.245 on eth0.
Apr 27 08:07:02 shane-desktop avahi-daemon[993]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.245.
Apr 27 08:07:02 shane-desktop avahi-daemon[993]: Interface eth0.IPv4 no longer relevant for mDNS.
Apr 27 08:07:02 shane-desktop NetworkManager[1016]: <warn> DNS: plugin dnsmasq update failed
Apr 27 08:07:02 shane-desktop NetworkManager[1016]: <info> Removing DNS information from /sbin/resolvconf
Apr 27 08:07:02 shane-desktop dnsmasq[1342]: setting upstream servers from DBus
Apr 27 08:07:02 shane-desktop NetworkManager[1016]: <info> (eth0): cleaning up...
Apr 27 08:07:02 shane-desktop NetworkManager[1016]: <info> (eth0): taking down device.
Apr 27 08:07:02 shane-desktop avahi-daemon[993]: Interface eth0.IPv6 no longer relevant for mDNS.
Apr 27 08:07:02 shane-desktop avahi-daemon[993]: Leaving mDNS multicast group on interface eth0.IPv6 with address fe80::e269:95ff:feeb:c2f4.
Apr 27 08:07:02 shane-desktop avahi-daemon[993]: Withdrawing address record for fe80::e269:95ff:feeb:c2f4 on eth0.
Apr 27 08:07:02 shane-desktop dbus[934]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 27 08:07:02 shane-desktop dbus[934]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 27 08:08:09 shane-desktop kernel: imklog 5.8.11, log source = /proc/kmsg started.
Apr 27 08:08:09 shane-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.11" x-pid="932" x-info="http://www.rsyslog.com"] start
Apr 27 08:08:09 shane-desktop rsyslogd: rsyslogd's groupid changed to 103
Apr 27 08:08:09 shane-desktop rsyslogd: rsyslogd's userid changed to 101
Apr 27 08:08:09 shane-desktop rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
```

---

### Post by Toz on 2013-04-27
Can you instead, post /var/log/pm-suspend.log:
```
pastebinit /var/log/pm-suspend.log
```
...post back the link that is generated,

and the results of this command:
```
cat /var/log/syslog | grep PM:
```

---

### Post by shanepardue on 2013-04-27
[http://paste.ubuntu.com/5608652/](http://paste.ubuntu.com/5608652/)

```
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da85a000 - 00000000da8a4000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da8a4000 - 00000000da8ac000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da8ac000 - 00000000dabda000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dabda000 - 00000000dabe8000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dabe8000 - 00000000dac10000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dac10000 - 00000000dac53000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dac53000 - 00000000dae8e000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000db800000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000db800000 - 00000000dfa00000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000fed1c000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
Apr 27 07:56:10 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Apr 27 07:56:10 shane-desktop kernel: [    0.333249] PM: Registering ACPI NVS region [mem 0xda85a000-0xda8a3fff] (303104 bytes)
Apr 27 07:56:10 shane-desktop kernel: [    0.333253] PM: Registering ACPI NVS region [mem 0xdabda000-0xdabe7fff] (57344 bytes)
Apr 27 07:56:10 shane-desktop kernel: [    0.333254] PM: Registering ACPI NVS region [mem 0xdac10000-0xdac52fff] (274432 bytes)
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da85a000 - 00000000da8a4000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da8a4000 - 00000000da8ac000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da8ac000 - 00000000dabda000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dabda000 - 00000000dabe8000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dabe8000 - 00000000dac10000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dac10000 - 00000000dac53000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dac53000 - 00000000dae8e000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000db800000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000db800000 - 00000000dfa00000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000fed1c000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
Apr 27 08:05:26 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Apr 27 08:05:26 shane-desktop kernel: [    0.332800] PM: Registering ACPI NVS region [mem 0xda85a000-0xda8a3fff] (303104 bytes)
Apr 27 08:05:26 shane-desktop kernel: [    0.332804] PM: Registering ACPI NVS region [mem 0xdabda000-0xdabe7fff] (57344 bytes)
Apr 27 08:05:26 shane-desktop kernel: [    0.332805] PM: Registering ACPI NVS region [mem 0xdac10000-0xdac52fff] (274432 bytes)
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da85a000 - 00000000da8a4000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da8a4000 - 00000000da8ac000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000da8ac000 - 00000000dabda000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dabda000 - 00000000dabe8000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dabe8000 - 00000000dac10000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dac10000 - 00000000dac53000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dac53000 - 00000000dae8e000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000db800000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000db800000 - 00000000dfa00000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000fed1c000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
Apr 27 08:08:09 shane-desktop kernel: [    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
Apr 27 08:08:09 shane-desktop kernel: [    0.332714] PM: Registering ACPI NVS region [mem 0xda85a000-0xda8a3fff] (303104 bytes)
Apr 27 08:08:09 shane-desktop kernel: [    0.332718] PM: Registering ACPI NVS region [mem 0xdabda000-0xdabe7fff] (57344 bytes)
Apr 27 08:08:09 shane-desktop kernel: [    0.332719] PM: Registering ACPI NVS region [mem 0xdac10000-0xdac52fff] (274432 bytes)

```

---

### Post by Toz on 2013-04-27
Nothings showing up in those log files. Can you click on the "Kernel Suspend" link in my signature and follow the "resume-trace" debugging procedure? Make sure you read the notes carefully to understand what will happen and what you need to do.

Perhaps this will help identify what is preventing the suspend.

---

### Post by shanepardue on 2013-04-27
Just a reminder that it doesn't seem to enter sleep. The light on my computer doesn't go to a blink like it does when it suspends. I'm not seeing magic number or hash matches in this file.

```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-19-generic (buildd@allspice) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #29-Ubuntu SMP Wed Apr 17 18:16:28 UTC 2013 (Ubuntu 3.8.0-19.29-generic 3.8.8)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=1e1fd88a-2dc4-4309-89fb-9ee5b1bcfe52 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x000000003fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040000000-0x00000000401fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040200000-0x00000000da859fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000da85a000-0x00000000da8a3fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000da8a4000-0x00000000da8abfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000da8ac000-0x00000000dabd9fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dabda000-0x00000000dabe7fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dabe8000-0x00000000dac0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dac10000-0x00000000dac52fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000dac53000-0x00000000dae8dfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000dae8e000-0x00000000daffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000db800000-0x00000000df9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000021fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI:                  /DH67BL, BIOS BLH6710H.86A.0160.2012.1204.1156 12/04/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x21fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-E7FFF uncachable
[    0.000000]   E8000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask E00000000 write-back
[    0.000000]   1 base 200000000 mask FE0000000 write-back
[    0.000000]   2 base 0DB800000 mask FFF800000 uncachable
[    0.000000]   3 base 0DC000000 mask FFC000000 uncachable
[    0.000000]   4 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   5 base 21FE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 8GB, type WB
[    0.000000] reg 1, base: 8GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 3, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 4, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 5, base: 8702MB, range: 2MB, type UC
[    0.000000] total RAM covered: 8118M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 128M 	num_reg: 8  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 3512MB, range: 8MB, type UC
[    0.000000] reg 4, base: 3520MB, range: 64MB, type UC
[    0.000000] reg 5, base: 4GB, range: 4GB, type WB
[    0.000000] reg 6, base: 8GB, range: 512MB, type WB
[    0.000000] reg 7, base: 8702MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xdb800000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xdb000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fcea0-0x000fceaf] mapped at [ffff8800000fcea0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] reserving inaccessible SNB gfx pages
[    0.000000] init_memory_mapping: [mem 0x00000000-0xdaffffff]
[    0.000000]  [mem 0x00000000-0xdaffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xdaffffff @ [mem 0x1fffb000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x21fdfffff]
[    0.000000]  [mem 0x100000000-0x21fdfffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x21fdfffff @ [mem 0xdaffa000-0xdaffffff]
[    0.000000] RAMDISK: [mem 0x36120000-0x37087fff]
[    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02  INTEL)
[    0.000000] ACPI: XSDT 00000000da8a4068 0004C (v01 INTEL  DH67BL   01072009 AMI  00010013)
[    0.000000] ACPI: FACP 00000000da8ab460 000F4 (v04 INTEL  DH67BL   01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 00000000da8a4140 07319 (v02 INTEL  DH67BL   00000012 INTL 20051117)
[    0.000000] ACPI: FACS 00000000dabdff80 00040
[    0.000000] ACPI: APIC 00000000da8ab558 00072 (v03 INTEL  DH67BL   01072009 AMI  00010013)
[    0.000000] ACPI: SSDT 00000000da8ab5d0 00102 (v01 INTEL  DH67BL   00000001 MSFT 03000001)
[    0.000000] ACPI: MCFG 00000000da8ab6d8 0003C (v01 INTEL  DH67BL   01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000da8ab718 00038 (v01 INTEL  DH67BL   01072009 AMI. 00000004)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000021fdfffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x21fdfffff]
[    0.000000]   NODE_DATA [mem 0x21fdfb000-0x21fdfffff]
[    0.000000]  [ffffea0000000000-ffffea00087fffff] PMD -> [ffff880217400000-ffff88021f3fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x21fdfffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009cfff]
[    0.000000]   node   0: [mem 0x00100000-0x1fffffff]
[    0.000000]   node   0: [mem 0x20200000-0x3fffffff]
[    0.000000]   node   0: [mem 0x40200000-0xda859fff]
[    0.000000]   node   0: [mem 0xdae8e000-0xdaffffff]
[    0.000000]   node   0: [mem 0x100000000-0x21fdfffff]
[    0.000000] On node 0 totalpages: 2073433
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 141 pages reserved
[    0.000000]   DMA zone: 3776 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13912 pages used for memmap
[    0.000000]   DMA32 zone: 876404 pages, LIFO batch:31
[    0.000000]   Normal zone: 18424 pages used for memmap
[    0.000000]   Normal zone: 1160712 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x00] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 0000000020000000 - 0000000020200000
[    0.000000] PM: Registered nosave memory: 0000000040000000 - 0000000040200000
[    0.000000] PM: Registered nosave memory: 00000000da85a000 - 00000000da8a4000
[    0.000000] PM: Registered nosave memory: 00000000da8a4000 - 00000000da8ac000
[    0.000000] PM: Registered nosave memory: 00000000da8ac000 - 00000000dabda000
[    0.000000] PM: Registered nosave memory: 00000000dabda000 - 00000000dabe8000
[    0.000000] PM: Registered nosave memory: 00000000dabe8000 - 00000000dac10000
[    0.000000] PM: Registered nosave memory: 00000000dac10000 - 00000000dac53000
[    0.000000] PM: Registered nosave memory: 00000000dac53000 - 00000000dae8e000
[    0.000000] PM: Registered nosave memory: 00000000db000000 - 00000000db800000
[    0.000000] PM: Registered nosave memory: 00000000db800000 - 00000000dfa00000
[    0.000000] PM: Registered nosave memory: 00000000dfa00000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000ff000000
[    0.000000] PM: Registered nosave memory: 00000000ff000000 - 0000000100000000
[    0.000000] e820: [mem 0xdfa00000-0xfed1bfff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88021fa00000 s85056 r8192 d21440 u524288
[    0.000000] pcpu-alloc: s85056 r8192 d21440 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2040892
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=1e1fd88a-2dc4-4309-89fb-9ee5b1bcfe52 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8063992k/8910848k available (7006k kernel code, 617116k absent, 229740k reserved, 6238k data, 992k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 3292.398 MHz processor
[    0.000001] Calibrating delay loop (skipped), value calculated using timer frequency.. 6584.79 BogoMIPS (lpj=13169592)
[    0.000003] pid_max: default: 32768 minimum: 301
[    0.000019] Security Framework initialized
[    0.000027] AppArmor: AppArmor initialized
[    0.000027] Yama: becoming mindful.
[    0.000406] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.001608] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.002114] Mount-cache hash table entries: 256
[    0.002227] Initializing cgroup subsys cpuacct
[    0.002228] Initializing cgroup subsys memory
[    0.002233] Initializing cgroup subsys devices
[    0.002234] Initializing cgroup subsys freezer
[    0.002235] Initializing cgroup subsys blkio
[    0.002236] Initializing cgroup subsys perf_event
[    0.002238] Initializing cgroup subsys hugetlb
[    0.002255] CPU: Physical Processor ID: 0
[    0.002255] CPU: Processor Core ID: 0
[    0.002259] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.002259] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.002261] mce: CPU supports 9 MCE banks
[    0.002271] CPU0: Thermal monitoring enabled (TM1)
[    0.002278] process: using mwait in idle threads
[    0.002280] Last level iTLB entries: 4KB 512, 2MB 0, 4MB 0
[    0.002280] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.002280] tlb_flushall_shift: 5
[    0.002386] Freeing SMP alternatives: 24k freed
[    0.004222] ACPI: Core revision 20121018
[    0.239594] ftrace: allocating 26689 entries in 105 pages
[    0.249939] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.289621] smpboot: CPU0: Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz (fam: 06, model: 2a, stepping: 07)
[    0.289627] TSC deadline timer enabled
[    0.289630] Performance Events: PEBS fmt1+, 16-deep LBR, SandyBridge events, Intel PMU driver.
[    0.289635] ... version:                3
[    0.289635] ... bit width:              48
[    0.289636] ... generic registers:      8
[    0.289637] ... value mask:             0000ffffffffffff
[    0.289638] ... max period:             000000007fffffff
[    0.289638] ... fixed-purpose events:   3
[    0.289639] ... event mask:             00000007000000ff
[    0.303378] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.290298] smpboot: Booting Node   0, Processors  #1 #2 #3 OK
[    0.329776] Brought up 4 CPUs
[    0.329779] smpboot: Total of 4 processors activated (26339.18 BogoMIPS)
[    0.332363] devtmpfs: initialized
[    0.333054] EVM: security.selinux
[    0.333056] EVM: security.SMACK64
[    0.333056] EVM: security.capability
[    0.333086] PM: Registering ACPI NVS region [mem 0xda85a000-0xda8a3fff] (303104 bytes)
[    0.333090] PM: Registering ACPI NVS region [mem 0xdabda000-0xdabe7fff] (57344 bytes)
[    0.333092] PM: Registering ACPI NVS region [mem 0xdac10000-0xdac52fff] (274432 bytes)
[    0.333620] regulator-dummy: no parameters
[    0.333650] NET: Registered protocol family 16
[    0.333749] ACPI: bus type pci registered
[    0.333785] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.333787] PCI: not using MMCONFIG
[    0.333788] PCI: Using configuration type 1 for base access
[    0.334354] bio: create slab <bio-0> at 0
[    0.334408] ACPI: Added _OSI(Module Device)
[    0.334409] ACPI: Added _OSI(Processor Device)
[    0.334410] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.334411] ACPI: Added _OSI(Processor Aggregator Device)
[    0.335109] ACPI: EC: Look up EC in DSDT
[    0.335904] ACPI: Executed 1 blocks of module-level executable AML code
[    0.337601] ACPI: SSDT 00000000dabde918 003E0 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.337806] ACPI: Dynamic OEM Table Load:
[    0.337807] ACPI: SSDT           (null) 003E0 (v01    AMI      IST 00000001 MSFT 03000001)
[    0.337833] ACPI: SSDT 00000000dabddd98 00120 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.338005] ACPI: Dynamic OEM Table Load:
[    0.338006] ACPI: SSDT           (null) 00120 (v01    AMI      CST 00000001 MSFT 03000001)
[    0.338319] ACPI: Interpreter enabled
[    0.338321] ACPI: (supports S0 S3 S4 S5)
[    0.338330] ACPI: Using IOAPIC for interrupt routing
[    0.338343] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.338377] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in ACPI motherboard resources
[    0.343530] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.346047] ACPI: No dock devices found.
[    0.346050] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.346140] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.346142] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.346344] pci_root PNP0A08:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-3f] only partially covers this bridge
[    0.346357] PCI host bridge to bus 0000:00
[    0.346359] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.346360] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
[    0.346362] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
[    0.346363] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
[    0.346364] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.346365] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.346367] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
[    0.346368] pci_bus 0000:00: root bus resource [mem 0xdfa00000-0xffffffff]
[    0.346374] pci 0000:00:00.0: [8086:0100] type 00 class 0x060000
[    0.346403] pci 0000:00:02.0: [8086:0102] type 00 class 0x030000
[    0.346411] pci 0000:00:02.0: reg 10: [mem 0xfe000000-0xfe3fffff 64bit]
[    0.346416] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.346419] pci 0000:00:02.0: reg 20: [io  0xf000-0xf03f]
[    0.346465] pci 0000:00:16.0: [8086:1c3a] type 00 class 0x078000
[    0.346486] pci 0000:00:16.0: reg 10: [mem 0xfe529000-0xfe52900f 64bit]
[    0.346558] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.346587] pci 0000:00:19.0: [8086:1503] type 00 class 0x020000
[    0.346604] pci 0000:00:19.0: reg 10: [mem 0xfe500000-0xfe51ffff]
[    0.346613] pci 0000:00:19.0: reg 14: [mem 0xfe528000-0xfe528fff]
[    0.346621] pci 0000:00:19.0: reg 18: [io  0xf080-0xf09f]
[    0.346680] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.346706] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.346725] pci 0000:00:1a.0: reg 10: [mem 0xfe527000-0xfe5273ff]
[    0.346811] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.346836] pci 0000:00:1b.0: [8086:1c20] type 00 class 0x040300
[    0.346850] pci 0000:00:1b.0: reg 10: [mem 0xfe520000-0xfe523fff 64bit]
[    0.346914] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.346936] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.347011] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.347036] pci 0000:00:1c.3: [8086:1c16] type 01 class 0x060400
[    0.347110] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.347140] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.347160] pci 0000:00:1d.0: reg 10: [mem 0xfe526000-0xfe5263ff]
[    0.347245] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.347269] pci 0000:00:1f.0: [8086:1c4a] type 00 class 0x060100
[    0.347388] pci 0000:00:1f.2: [8086:1c02] type 00 class 0x010601
[    0.347405] pci 0000:00:1f.2: reg 10: [io  0xf0d0-0xf0d7]
[    0.347412] pci 0000:00:1f.2: reg 14: [io  0xf0c0-0xf0c3]
[    0.347420] pci 0000:00:1f.2: reg 18: [io  0xf0b0-0xf0b7]
[    0.347427] pci 0000:00:1f.2: reg 1c: [io  0xf0a0-0xf0a3]
[    0.347435] pci 0000:00:1f.2: reg 20: [io  0xf060-0xf07f]
[    0.347442] pci 0000:00:1f.2: reg 24: [mem 0xfe525000-0xfe5257ff]
[    0.347485] pci 0000:00:1f.2: PME# supported from D3hot
[    0.347501] pci 0000:00:1f.3: [8086:1c22] type 00 class 0x0c0500
[    0.347515] pci 0000:00:1f.3: reg 10: [mem 0xfe524000-0xfe5240ff 64bit]
[    0.347535] pci 0000:00:1f.3: reg 20: [io  0xf040-0xf05f]
[    0.347628] pci 0000:01:00.0: [1283:8892] type 01 class 0x060401
[    0.347815] pci 0000:01:00.0: supports D1 D2
[    0.347817] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.347845] pci 0000:00:1c.0: PCI bridge to [bus 01-02]
[    0.348034] pci 0000:01:00.0: PCI bridge to [bus 02] (subtractive decode)
[    0.348066] pci 0000:01:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.348067] pci 0000:01:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.348068] pci 0000:01:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.348069] pci 0000:01:00.0:   bridge window [??? 0x00000000 flags 0x0] (subtractive decode)
[    0.348150] pci 0000:03:00.0: [1033:0194] type 00 class 0x0c0330
[    0.348175] pci 0000:03:00.0: reg 10: [mem 0xfe400000-0xfe401fff 64bit]
[    0.348309] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.356210] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.356220] pci 0000:00:1c.3:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.356295] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.356313] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0.BR21._PRT]
[    0.356340] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.356404]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.356478]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.356826] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.356854] ACPI: PCI Interrupt Link [LNKB] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.356881] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.356907] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 *4 5 6 10 11 12 14 15)
[    0.356933] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.356959] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0
[    0.356985] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.357011] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.357070] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.357072] vgaarb: loaded
[    0.357073] vgaarb: bridge control possible 0000:00:02.0
[    0.357172] SCSI subsystem initialized
[    0.357173] ACPI: bus type scsi registered
[    0.357189] libata version 3.00 loaded.
[    0.357199] ACPI: bus type usb registered
[    0.357211] usbcore: registered new interface driver usbfs
[    0.357216] usbcore: registered new interface driver hub
[    0.357227] usbcore: registered new device driver usb
[    0.357275] PCI: Using ACPI for IRQ routing
[    0.358743] PCI: pci_cache_line_size set to 64 bytes
[    0.358785] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
[    0.358787] e820: reserve RAM buffer [mem 0xda85a000-0xdbffffff]
[    0.358788] e820: reserve RAM buffer [mem 0xdb000000-0xdbffffff]
[    0.358789] e820: reserve RAM buffer [mem 0x21fe00000-0x21fffffff]
[    0.358839] NetLabel: Initializing
[    0.358840] NetLabel:  domain hash size = 128
[    0.358841] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.358847] NetLabel:  unlabeled traffic allowed by default
[    0.358880] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.358883] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.360894] Switching to clocksource hpet
[    0.364121] AppArmor: AppArmor Filesystem Enabled
[    0.364137] pnp: PnP ACPI init
[    0.364145] ACPI: bus type pnp registered
[    0.364220] system 00:00: [mem 0xfed10000-0xfed19fff] has been reserved
[    0.364221] system 00:00: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.364223] system 00:00: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.364224] system 00:00: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.364226] system 00:00: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.364228] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.364308] system 00:01: [io  0x0290-0x029f] has been reserved
[    0.364310] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.364490] pnp 00:02: [dma 4]
[    0.364501] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.364522] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.364532] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.364559] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.364561] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.364575] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.364675] system 00:07: [io  0x0400-0x0453] has been reserved
[    0.364677] system 00:07: [io  0x0458-0x047f] has been reserved
[    0.364678] system 00:07: [io  0x1180-0x119f] has been reserved
[    0.364680] system 00:07: [io  0x0500-0x057f] has been reserved
[    0.364681] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.364683] system 00:07: [mem 0xfec00000-0xfecfffff] could not be reserved
[    0.364684] system 00:07: [mem 0xfed08000-0xfed08fff] has been reserved
[    0.364686] system 00:07: [mem 0xff000000-0xffffffff] has been reserved
[    0.364687] system 00:07: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.364717] system 00:08: [io  0x0454-0x0457] has been reserved
[    0.364719] system 00:08: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.364795] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.364878] pnp: PnP ACPI: found 10 devices
[    0.364879] ACPI: ACPI bus type pnp unregistered
[    0.370607] pci 0000:01:00.0: PCI bridge to [bus 02]
[    0.370636] pci 0000:00:1c.0: PCI bridge to [bus 01-02]
[    0.370646] pci 0000:00:1c.3: PCI bridge to [bus 03]
[    0.370651] pci 0000:00:1c.3:   bridge window [mem 0xfe400000-0xfe4fffff]
[    0.370683] pci 0000:01:00.0: setting latency timer to 64
[    0.370694] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
[    0.370695] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
[    0.370696] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
[    0.370698] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
[    0.370699] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
[    0.370700] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
[    0.370701] pci_bus 0000:00: resource 10 [mem 0xdfa00000-0xffffffff]
[    0.370703] pci_bus 0000:03: resource 1 [mem 0xfe400000-0xfe4fffff]
[    0.370720] NET: Registered protocol family 2
[    0.370839] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.370996] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.371112] TCP: Hash tables configured (established 65536 bind 65536)
[    0.371125] TCP: reno registered
[    0.371133] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.371155] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.371200] NET: Registered protocol family 1
[    0.371539] pci 0000:00:02.0: BIOS left Intel GPU interrupts enabled; disabling
[    0.371549] pci 0000:00:02.0: Boot video device
[    0.371657] PCI: CLS 64 bytes, default 64
[    0.371682] Trying to unpack rootfs image as initramfs...
[    0.555361] Freeing initrd memory: 15776k freed
[    0.556796] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.556800] software IO TLB [mem 0xd685a000-0xda85a000] (64MB) mapped at [ffff8800d685a000-ffff8800da859fff]
[    0.557110] Initialise module verification
[    0.557137] audit: initializing netlink socket (disabled)
[    0.557148] type=2000 audit(1367057185.324:1): initialized
[    0.576146] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.577091] VFS: Disk quotas dquot_6.5.2
[    0.577115] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.577395] fuse init (API version 7.20)
[    0.577440] msgmni has been set to 15780
[    0.577746] Key type asymmetric registered
[    0.577747] Asymmetric key parser 'x509' registered
[    0.577766] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.577783] io scheduler noop registered
[    0.577784] io scheduler deadline registered (default)
[    0.577787] io scheduler cfq registered
[    0.577886] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.577978] pcieport 0000:00:1c.3: irq 41 for MSI/MSI-X
[    0.578045] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.578047] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.578051] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.578064] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.578066] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.578069] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.578076] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.578084] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.578107] intel_idle: MWAIT substates: 0x1120
[    0.578108] intel_idle: v0.4 model 0x2A
[    0.578109] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.578153] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.578157] ACPI: Power Button [PWRB]
[    0.578178] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.578180] ACPI: Power Button [PWRF]
[    0.578227] ACPI: Requesting acpi_cpufreq
[    0.580665] GHES: HEST is not enabled!
[    0.580712] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.581537] Linux agpgart interface v0.103
[    0.582231] brd: module loaded
[    0.582595] loop: module loaded
[    0.582771] libphy: Fixed MDIO Bus: probed
[    0.582805] tun: Universal TUN/TAP device driver, 1.6
[    0.582806] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.582826] PPP generic driver version 2.4.2
[    0.582848] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.582849] ehci-pci: EHCI PCI platform driver
[    0.582875] ehci-pci 0000:00:1a.0: setting latency timer to 64
[    0.582879] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.582882] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.582894] ehci-pci 0000:00:1a.0: debug port 2
[    0.586775] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.586787] ehci-pci 0000:00:1a.0: irq 16, io mem 0xfe527000
[    0.596917] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.596941] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.596944] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.596947] usb usb1: Product: EHCI Host Controller
[    0.596950] usb usb1: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    0.596952] usb usb1: SerialNumber: 0000:00:1a.0
[    0.597035] hub 1-0:1.0: USB hub found
[    0.597038] hub 1-0:1.0: 2 ports detected
[    0.597096] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    0.597099] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.597103] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.597113] ehci-pci 0000:00:1d.0: debug port 2
[    0.600995] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.601005] ehci-pci 0000:00:1d.0: irq 23, io mem 0xfe526000
[    0.612913] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.612928] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.612931] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.612933] usb usb2: Product: EHCI Host Controller
[    0.612936] usb usb2: Manufacturer: Linux 3.8.0-19-generic ehci_hcd
[    0.612938] usb usb2: SerialNumber: 0000:00:1d.0
[    0.613021] hub 2-0:1.0: USB hub found
[    0.613023] hub 2-0:1.0: 2 ports detected
[    0.613066] ehci-platform: EHCI generic platform driver
[    0.613071] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.613079] uhci_hcd: USB Universal Host Controller Interface driver
[    0.613103] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    0.613106] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 3
[    0.613309] xhci_hcd 0000:03:00.0: irq 42 for MSI/MSI-X
[    0.613313] xhci_hcd 0000:03:00.0: irq 43 for MSI/MSI-X
[    0.613316] xhci_hcd 0000:03:00.0: irq 44 for MSI/MSI-X
[    0.613320] xhci_hcd 0000:03:00.0: irq 45 for MSI/MSI-X
[    0.613323] xhci_hcd 0000:03:00.0: irq 46 for MSI/MSI-X
[    0.613416] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.613418] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.613419] usb usb3: Product: xHCI Host Controller
[    0.613420] usb usb3: Manufacturer: Linux 3.8.0-19-generic xhci_hcd
[    0.613421] usb usb3: SerialNumber: 0000:03:00.0
[    0.613458] xHCI xhci_add_endpoint called for root hub
[    0.613459] xHCI xhci_check_bandwidth called for root hub
[    0.613469] hub 3-0:1.0: USB hub found
[    0.613476] hub 3-0:1.0: 2 ports detected
[    0.613513] xhci_hcd 0000:03:00.0: xHCI Host Controller
[    0.613515] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 4
[    0.616693] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.616694] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.616695] usb usb4: Product: xHCI Host Controller
[    0.616697] usb usb4: Manufacturer: Linux 3.8.0-19-generic xhci_hcd
[    0.616698] usb usb4: SerialNumber: 0000:03:00.0
[    0.616730] xHCI xhci_add_endpoint called for root hub
[    0.616731] xHCI xhci_check_bandwidth called for root hub
[    0.616740] hub 4-0:1.0: USB hub found
[    0.616746] hub 4-0:1.0: 2 ports detected
[    0.616846] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.619767] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.619772] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.619823] mousedev: PS/2 mouse device common for all mice
[    0.619897] rtc_cmos 00:03: RTC can wake from S4
[    0.620000] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.620027] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.620073] device-mapper: uevent: version 1.0.3
[    0.620106] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    0.620145] cpuidle: using governor ladder
[    0.620192] cpuidle: using governor menu
[    0.620194] ledtrig-cpu: registered to indicate activity on CPUs
[    0.620195] EFI Variables Facility v0.08 2004-May-17
[    0.620307] ashmem: initialized
[    0.620379] TCP: cubic registered
[    0.620432] NET: Registered protocol family 10
[    0.620531] NET: Registered protocol family 17
[    0.620536] Key type dns_resolver registered
[    0.620678] Loading module verification certificates
[    0.621317] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d490763cc418e29de79f40a5aa7d97747ec8882c'
[    0.621323] registered taskstats version 1
[    0.623217] Key type trusted registered
[    0.624699] Key type encrypted registered
[    0.626719] rtc_cmos 00:03: setting system clock to 2013-04-27 10:06:25 UTC (1367057185)
[    0.627132] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.627133] EDD information not available.
[    0.628153] Freeing unused kernel memory: 992k freed
[    0.628243] Write protecting the kernel read-only data: 12288k
[    0.630507] Freeing unused kernel memory: 1176k freed
[    0.632503] Freeing unused kernel memory: 1080k freed
[    0.640445] udevd[107]: starting version 175
[    0.654108] Disabling lock debugging due to kernel taint
[    0.654468] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    0.654470] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    0.654501] e1000e 0000:00:19.0: setting latency timer to 64
[    0.654548] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.654577] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[    0.908917] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    0.915132] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) e0:69:95:eb:c2:f4
[    0.915134] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    0.915176] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    0.915236] ahci 0000:00:1f.2: version 3.0
[    0.915316] ahci 0000:00:1f.2: irq 48 for MSI/MSI-X
[    0.928951] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    0.928957] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems sxs apst 
[    0.928964] ahci 0000:00:1f.2: setting latency timer to 64
[    0.969321] scsi0 : ahci
[    0.969489] scsi1 : ahci
[    0.969661] scsi2 : ahci
[    0.969817] scsi3 : ahci
[    0.969964] scsi4 : ahci
[    0.970071] scsi5 : ahci
[    0.970115] ata1: SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525100 irq 48
[    0.970118] ata2: SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525180 irq 48
[    0.970120] ata3: SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525200 irq 48
[    0.970122] ata4: SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525280 irq 48
[    0.970123] ata5: SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525300 irq 48
[    0.970125] ata6: SATA max UDMA/133 abar m2048@0xfe525000 port 0xfe525380 irq 48
[    1.041363] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.041368] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.041738] hub 1-1:1.0: USB hub found
[    1.041840] hub 1-1:1.0: 6 ports detected
[    1.152946] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.285341] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.285346] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.285602] hub 2-1:1.0: USB hub found
[    1.285705] hub 2-1:1.0: 8 ports detected
[    1.288912] ata4: SATA link down (SStatus 0 SControl 300)
[    1.288939] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.288960] ata2: SATA link down (SStatus 0 SControl 300)
[    1.288983] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.289028] ata6: SATA link down (SStatus 0 SControl 300)
[    1.289048] ata5: SATA link down (SStatus 0 SControl 300)
[    1.289389] ata3.00: ATAPI: ASUS    BC-12B1ST, 1.01, max UDMA/100
[    1.289995] ata3.00: configured for UDMA/100
[    1.291141] ata1.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.291144] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.293524] ata1.00: configured for UDMA/133
[    1.293769] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.293876] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.293936] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.293946] sd 0:0:0:0: [sda] Write Protect is off
[    1.293948] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.293958] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.294649] scsi 2:0:0:0: CD-ROM            ASUS     BC-12B1ST        1.01 PQ: 0 ANSI: 5
[    1.296874] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.296890] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.297053] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.297108] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.339512]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    1.339948] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.396934] usb 3-1: new full-speed USB device number 2 using xhci_hcd
[    1.436797] usb 3-1: config 1 interface 0 altsetting 0 endpoint 0x1 has an invalid bInterval 0, changing to 32
[    1.436803] usb 3-1: config 1 interface 0 altsetting 0 endpoint 0x82 has an invalid bInterval 0, changing to 32
[    1.462786] usb 3-1: New USB device found, idVendor=1784, idProduct=0008
[    1.462791] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.462794] usb 3-1: Product: eHome Infrared Transceiver
[    1.462797] usb 3-1: Manufacturer: Topseed Technology Corp.
[    1.462799] usb 3-1: SerialNumber: TS000Hkw
[    1.536948] usb 1-1.3: new low-speed USB device number 3 using ehci-pci
[    1.552903] tsc: Refined TSC clocksource calibration: 3292.521 MHz
[    1.552909] Switching to clocksource tsc
[    1.616194] EXT4-fs (sda5): INFO: recovery required on readonly filesystem
[    1.616197] EXT4-fs (sda5): write access will be enabled during recovery
[    1.635170] usb 1-1.3: New USB device found, idVendor=046d, idProduct=c505
[    1.635174] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.635177] usb 1-1.3: Product: USB Receiver
[    1.635179] usb 1-1.3: Manufacturer: Logitech
[    1.649213] usbcore: registered new interface driver usbhid
[    1.649216] usbhid: USB HID core driver
[    1.651087] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input2
[    1.651231] hid-generic 0003:046D:C505.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1a.0-1.3/input0
[    1.651375] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.1/input/input3
[    1.651442] hid-generic 0003:046D:C505.0002: input,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.3/input1
[    1.704952] usb 1-1.4: new high-speed USB device number 4 using ehci-pci
[    1.799790] usb 1-1.4: New USB device found, idVendor=2040, idProduct=c200
[    1.799795] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.799798] usb 1-1.4: Product: Hauppauge Device
[    1.799800] usb 1-1.4: Manufacturer: Hauppauge
[    1.799802] usb 1-1.4: SerialNumber: 0011182426
[    1.876946] usb 1-1.6: new low-speed USB device number 5 using ehci-pci
[    1.976659] usb 1-1.6: New USB device found, idVendor=046e, idProduct=55a5
[    1.976664] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.976667] usb 1-1.6: Product: USB Multimedia Keyboard
[    1.976669] usb 1-1.6: Manufacturer: BTC
[    1.980317] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input4
[    1.980431] hid-generic 0003:046E:55A5.0003: input,hidraw2: USB HID v1.10 Keyboard [BTC USB Multimedia Keyboard] on usb-0000:00:1a.0-1.6/input0
[    1.988709] input: BTC USB Multimedia Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input5
[    1.988876] hid-generic 0003:046E:55A5.0004: input,hiddev0,hidraw3: USB HID v1.10 Device [BTC USB Multimedia Keyboard] on usb-0000:00:1a.0-1.6/input1
[    2.060908] usb 2-1.1: new high-speed USB device number 3 using ehci-pci
[    2.154887] usb 2-1.1: New USB device found, idVendor=058f, idProduct=6362
[    2.154889] usb 2-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.154891] usb 2-1.1: Product: Mass Storage Device
[    2.154892] usb 2-1.1: Manufacturer: Generic
[    2.154893] usb 2-1.1: SerialNumber: 058F63626376
[    2.156485] Initializing USB Mass Storage driver...
[    2.156586] scsi6 : usb-storage 2-1.1:1.0
[    2.156636] usbcore: registered new interface driver usb-storage
[    2.156638] USB Mass Storage support registered.
[    3.153892] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    3.154496] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    3.155040] scsi 6:0:0:2: Direct-Access     Generic  USB xD/SM Reader 1.02 PQ: 0 ANSI: 0
[    3.155665] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    3.156194] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.156281] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    3.156363] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    3.156471] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    3.174627] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    3.175375] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    3.175999] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    3.176750] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    3.785624] EXT4-fs (sda5): orphan cleanup on readonly fs
[    3.785630] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 541332
[    3.785663] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 530377
[    3.785670] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 530376
[    3.841814] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 530366
[    3.841845] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 530365
[    3.881510] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529435
[    3.926912] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 527256
[    3.939238] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 525210
[    3.952356] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1049858
[    3.969628] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 678761
[    3.988166] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677784
[    3.988201] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677783
[    3.988219] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677521
[    4.013516] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 678638
[    4.013537] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 530363
[    4.017620] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 530362
[    4.017642] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 530361
[    4.035420] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 403786
[    4.044364] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677792
[    4.044381] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677552
[    4.044397] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 678038
[    4.044413] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 678044
[    4.066595] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 678053
[    4.066627] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 678065
[    4.066652] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 678063
[    4.066676] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1050132
[    4.066693] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1050131
[    4.066700] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1050130
[    4.066706] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1050129
[    4.066714] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677876
[    4.066720] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1050128
[    4.066727] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1050127
[    4.066734] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1050126
[    4.066741] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1049995
[    4.066747] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 1049860
[    4.066754] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677806
[    4.066763] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529562
[    4.066771] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529561
[    4.066777] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529560
[    4.090739] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 786672
[    4.109013] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529559
[    4.109038] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529558
[    4.109064] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677501
[    4.122375] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677505
[    4.122410] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677507
[    4.122431] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677512
[    4.122437] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677509
[    4.122444] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 677488
[    4.132607] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 673075
[    4.132639] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529555
[    4.132655] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529554
[    4.132670] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529553
[    4.132684] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529552
[    4.132705] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 529551
[    4.144765] EXT4-fs (sda5): ext4_orphan_cleanup: deleting unreferenced inode 670975
[    4.144795] EXT4-fs (sda5): 55 orphan inodes deleted
[    4.144798] EXT4-fs (sda5): recovery complete
[    4.384970] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    6.619848] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.990925] udevd[428]: starting version 175
[    7.185660] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[    7.708013] lp: driver loaded but no devices found
[    7.914502] microcode: CPU0 sig=0x206a7, pf=0x2, revision=0x28
[    7.949971] mei 0000:00:16.0: setting latency timer to 64
[    7.950018] mei 0000:00:16.0: irq 49 for MSI/MSI-X
[    8.003451] gpio_ich: GPIO from 180 to 255 on gpio_ich
[    8.017711] microcode: CPU1 sig=0x206a7, pf=0x2, revision=0x28
[    8.018551] microcode: CPU2 sig=0x206a7, pf=0x2, revision=0x28
[    8.019238] microcode: CPU3 sig=0x206a7, pf=0x2, revision=0x28
[    8.020054] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.144053] [drm] Initialized drm 1.1.0 20060810
[    8.505680] [drm] Memory usable by graphics device = 2048M
[    8.505685] i915 0000:00:02.0: setting latency timer to 64
[    8.528772] i915 0000:00:02.0: irq 50 for MSI/MSI-X
[    8.528778] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    8.528779] [drm] Driver supports precise vblank timestamp query.
[    8.528802] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    9.038857] type=1400 audit(1367075193.907:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=759 comm="apparmor_parser"
[    9.038864] type=1400 audit(1367075193.907:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=808 comm="apparmor_parser"
[    9.039098] type=1400 audit(1367075193.907:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=759 comm="apparmor_parser"
[    9.039105] type=1400 audit(1367075193.907:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=808 comm="apparmor_parser"
[    9.039231] type=1400 audit(1367075193.907:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=759 comm="apparmor_parser"
[    9.039238] type=1400 audit(1367075193.907:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=808 comm="apparmor_parser"
[    9.314345] Linux video capture interface: v2.00
[    9.360686] Registered IR keymap rc-rc6-mce
[    9.360788] input: Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) as /devices/pci0000:00/0000:00:1c.3/0000:03:00.0/usb3/3-1/3-1:1.0/rc/rc0/input6
[    9.360897] rc0: Media Center Ed. eHome Infrared Remote Transceiver (1784:0008) as /devices/pci0000:00/0000:00:1c.3/0000:03:00.0/usb3/3-1/3-1:1.0/rc/rc0
[    9.368642] fbcon: inteldrmfb (fb0) is primary device
[    9.385571] IR NEC protocol handler initialized
[    9.413862] IR RC5(x) protocol handler initialized
[    9.477476] IR RC6 protocol handler initialized
[    9.504710] mceusb 3-1:1.0: Registered Topseed Technology Corp. eHome Infrared Transceiver with mce emulator interface version 1
[    9.504712] mceusb 3-1:1.0: 2 tx ports (0x0 cabled) and 2 rx sensors (0x0 active)
[    9.504755] usbcore: registered new interface driver mceusb
[    9.528585] IR JVC protocol handler initialized
[    9.535264] cx231xx #0: New device Hauppauge Hauppauge Device @ 480 Mbps (2040:c200) with 5 interfaces
[    9.535265] cx231xx #0: registering interface 1
[    9.536655] cx231xx #0: can't change interface 3 alt no. to 3: Max. Pkt size = 0
[    9.537805] cx231xx #0: can't change interface 4 alt no. to 1: Max. Pkt size = 0
[    9.538922] cx231xx #0: Identified as Hauppauge USB Live 2 (card=9)
[    9.578469] IR Sony protocol handler initialized
[    9.609699] IR SANYO protocol handler initialized
[    9.624818] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[    9.630743] input: MCE IR Keyboard/Mouse (mceusb) as /devices/virtual/input/input7
[    9.630800] IR MCE Keyboard/mouse protocol handler initialized
[    9.654447] lirc_dev: IR Remote Control driver registered, major 250 
[    9.655480] rc rc0: lirc_dev: driver ir-lirc-codec (mceusb) registered at minor = 0
[    9.655480] IR LIRC bridge handler initialized
[    9.742282] cx25840 8-0044: cx23102 A/V decoder found @ 0x88 (cx231xx #0)
[    9.760480] cx25840 8-0044:  Firmware download size changed to 16 bytes max length
[    9.840766] Console: switching to colour frame buffer device 180x56
[    9.842917] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    9.842918] i915 0000:00:02.0: registered panic notifier
[    9.842931] i915: No ACPI video bus found
[    9.842954] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.843043] snd_hda_intel 0000:00:1b.0: irq 51 for MSI/MSI-X
[    9.951945] init: failsafe main process (864) killed by TERM signal
[   10.000775] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   10.000833] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   10.000873] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.000909] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.000951] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   10.000988] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   10.001024] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   10.001060] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   10.028916] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   10.501104] Bluetooth: Core ver 2.16
[   10.501120] NET: Registered protocol family 31
[   10.501121] Bluetooth: HCI device and connection manager initialized
[   10.501127] Bluetooth: HCI socket layer initialized
[   10.501129] Bluetooth: L2CAP socket layer initialized
[   10.501132] Bluetooth: SCO socket layer initialized
[   10.599538] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   10.599540] Bluetooth: BNEP filters: protocol multicast
[   10.599546] Bluetooth: BNEP socket layer initialized
[   10.603815] Bluetooth: RFCOMM TTY layer initialized
[   10.603821] Bluetooth: RFCOMM socket layer initialized
[   10.603822] Bluetooth: RFCOMM ver 1.11
[   10.647401] init: avahi-cups-reload main process (1015) terminated with status 1
[   10.781493] ppdev: user-space parallel port driver
[   11.745717] cx25840 8-0044: loaded v4l-cx231xx-avcore-01.fw firmware (16382 bytes)
[   11.780213] cx231xx #0: cx231xx #0: v4l2 driver version 0.0.2
[   11.803088] cx231xx #0: cx231xx_dif_set_standard: setStandard to ffffffff
[   11.847836] cx231xx #0: video_mux : 0
[   11.847840] cx231xx #0: do_mode_ctrl_overrides : 0xb000
[   11.848585] cx231xx #0: do_mode_ctrl_overrides NTSC
[   11.855243] cx231xx #0: cx231xx #0/0: registered device video0 [v4l2]
[   11.855301] cx231xx #0: cx231xx #0/0: registered device vbi0
[   11.855303] cx231xx #0: V4L2 device registered as video0 and vbi0
[   11.855304] cx231xx #0: EndPoint Addr 0x84, Alternate settings: 5
[   11.855313] cx231xx #0: Alternate setting 0, max size= 512
[   11.855314] cx231xx #0: Alternate setting 1, max size= 184
[   11.855315] cx231xx #0: Alternate setting 2, max size= 728
[   11.855316] cx231xx #0: Alternate setting 3, max size= 2892
[   11.855317] cx231xx #0: Alternate setting 4, max size= 1800
[   11.855318] cx231xx #0: EndPoint Addr 0x85, Alternate settings: 2
[   11.855319] cx231xx #0: Alternate setting 0, max size= 512
[   11.855320] cx231xx #0: Alternate setting 1, max size= 512
[   11.855321] cx231xx #0: EndPoint Addr 0x86, Alternate settings: 2
[   11.855322] cx231xx #0: Alternate setting 0, max size= 512
[   11.855322] cx231xx #0: Alternate setting 1, max size= 576
[   11.855369] usbcore: registered new interface driver cx231xx
[   11.872934] cx231xx #0: cx231xx-audio.c: probing for cx231xx non standard usbaudio
[   11.873021] cx231xx #0: EndPoint Addr 0x83, Alternate settings: 3
[   11.873022] cx231xx #0: Alternate setting 0, max size= 512
[   11.873023] cx231xx #0: Alternate setting 1, max size= 28
[   11.873024] cx231xx #0: Alternate setting 2, max size= 52
[   11.873025] cx231xx: Cx231xx Audio Extension initialized
[   11.877013] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8
[   13.588309] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   13.688673] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   13.688775] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.688939] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.219388] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   15.219392] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[   15.219423] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.042611] audit_printk_skb: 12 callbacks suppressed
[   16.042614] type=1400 audit(1367075200.911:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1114 comm="apparmor_parser"
[   16.042861] type=1400 audit(1367075200.911:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1114 comm="apparmor_parser"
[   16.042994] type=1400 audit(1367075200.911:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1114 comm="apparmor_parser"
[   16.129158] type=1400 audit(1367075200.999:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1111 comm="apparmor_parser"
[   16.129276] type=1400 audit(1367075200.999:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1112 comm="apparmor_parser"
[   16.129352] type=1400 audit(1367075200.999:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1111 comm="apparmor_parser"
[   16.129456] type=1400 audit(1367075200.999:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1112 comm="apparmor_parser"
[   16.131945] type=1400 audit(1367075200.999:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1119 comm="apparmor_parser"
[   16.132225] type=1400 audit(1367075200.999:18): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1119 comm="apparmor_parser"
[   16.135332] type=1400 audit(1367075201.003:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1113 comm="apparmor_parser"
[   28.846759] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   28.847033] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   28.847394] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   28.848060] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   28.848282] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   28.848591] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   28.891322] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   28.891531] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   28.891894] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   28.892558] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   28.892781] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   28.893197] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   29.054818] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   29.055044] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   29.342840] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   29.343422] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   29.343641] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   29.343966] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   29.344543] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   29.344766] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   29.345074] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   29.345667] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   29.345891] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   29.346211] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   29.346792] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   29.347016] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   29.347432] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   29.349553] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   29.349766] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   29.353767] cx231xx #0: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
[   34.161745] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.181850] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.182045] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.182405] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.183071] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.183294] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.183627] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.184194] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.184418] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.184764] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.185444] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.185669] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.186081] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.187833] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.188044] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.189862] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.190446] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.190670] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.190986] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.191569] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.191794] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.192103] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.192693] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.192918] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.193252] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.193942] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.194169] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.194620] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   36.196578] cx231xx #0: cx231xx_initialize_stream_xfer: Audio enter HANC
[   36.196794] cx231xx #0: cx231xx_start_stream():: ep_mask = 4
[   36.200794] cx231xx #0: cx231xx_init_audio_isoc: Starting ISO AUDIO transfers
[   41.386570] cx231xx #0: cx231xx_stop_stream():: ep_mask = 4
[   70.598714] cx231xx #0:  setPowerMode::mode = 48, No Change req.
[   70.599941] cx231xx #0: cx231xx_stop_stream():: ep_mask = 8
```

---

### Post by Toz on 2013-04-27
Hmmmm.

You seem to have a usb 3 port. Can you try following the instructions at[ this site]("http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug") to unbind the usb 3 devices on suspend and rebind on resume and see if it works? Is anything connected to the usb 3 port?
```
lsusb
```

---

### Post by shanepardue on 2013-04-28
This guide didn't seem to change my results. What's odd is that usually when this computer suspends on other operating systems, there is a lot of disk activity for a couple seconds before suspending. With Ubuntu, there is none. Also, there is a dialog that asks me if I want to submit a bug report, but doesn't let me copy and paste the details of the error. It might help with troubleshooting the KernelOops I'm experiencing. [IMG]http://img.photobucket.com/albums/v330/shanepardue/screenshot_zpsd93ea8c6.png[/IMG]

Here's the output of lsusb. I don't use the 3.0 ports most of the time, but I'd like to have them available. Thanks for your help with this!

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 1784:0008 TopSeed Technology Corp. eHome Infrared Transceiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 005: ID 2040:c200 Hauppauge 
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
```

---

### Post by Toz on 2013-04-29
Interesting that nothing is showing up in /var/log/pm-suspend.log. The error report seems to indicate a kernel crash.

Can you try and extended debug of the suspend process using this procedure:
```

sudo bash
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.BAK
export PM_DEBUG=true
pm-suspend
```
When you recover, post back the extended suspend log:
```
pastebinit /var/log/pm-suspend.log
```

You might also want to try booting with a previous kernel to see if the issue is present there as well.

---

### Post by shanepardue on 2013-04-29
[http://paste.ubuntu.com/5617763/](http://paste.ubuntu.com/5617763/)

To install a previous kernel, I believe I'd have to compile one since ubuntu's repos don't have older kenels available. Am I mistaken?

---

### Post by Toz on 2013-04-29
Interesting. There is nothing in your log files to indicate a kernel crash.

To boot a previous kernel, hold down the shift key while the computer is booting to display the grub screen. Select the "Advanced Options for Ubuntu" entry and it will display a list of previous kernels. Select one to boot with it and test suspend again.

---

### Post by shanepardue on 2013-04-30
This was a fresh install and therefore has no previous kernels in that list.

---

### Post by Toz on 2013-04-30
> **shanepardue said:**
> This guide didn't seem to change my results. What's odd is that usually when this computer suspends on other operating systems, there is a lot of disk activity for a couple seconds before suspending. With Ubuntu, there is none. Also, there is a dialog that asks me if I want to submit a bug report, but doesn't let me copy and paste the details of the error. It might help with troubleshooting the KernelOops I'm experiencing. [IMG]http://img.photobucket.com/albums/v330/shanepardue/screenshot_zpsd93ea8c6.png[/IMG]

Perhaps it is best to submit this bug report and follow that procedure. I'm not sure exactly what is happening here.

---

### Post by shanepardue on 2013-05-01
Excuse my ignorance, but is it more effective to do anything other than send the report from within Ubuntu's Launchpad (or whatever it is) dialog? Thanks for trying to help me with this. I really hope it can get resolved in the future as I want to save power when I'm not using my computer. I'm a little surprised a complete Intel setup has issues, but it is what it is.

---

### Post by Toz on 2013-05-02
As seems to be indicated by the error dialog above, you appear to be suffering a kernel crash during suspend. This is out of the ordinary, hence the suggestion to create a launchpad bug report. The other suggestion, one which will probably be repeated by the bug triage team, will be to try a different kernel to see if it solves the problem.

You could try booting from the live CD/USB and trying to suspend to see if the problem persists. Compare the kernel versions. Though I believe they will be the same.

You could also try the mainline kernel to help troubleshoot/resolve the issue. More information about mainline kernels can be found [here]("https://wiki.ubuntu.com/Kernel/MainlineBuilds").

Unfortunately, we cannot find any messages in any of the log files to help give us a hint as to what is happening.

---

### Post by DenHeldert on 2013-05-02
Having the exact same issue here.
Should I post here or start a new (duplicate?) thread?

---

### Post by Toz on 2013-05-02
> **DenHeldert said:**
> Having the exact same issue here.
Should I post here or start a new (duplicate?) thread?

Probably best to create a new thread. Be sure to include the following information:

- detailed explanation of problem
- make/model of computer
- results of the following command line queries:
```
cat /proc/cmdline
lsmod
```
- contents of the two following log files:
```
pastebinit /var/log/pm-suspend.log
pastebinit /var/log/dmesg
```

Also, have a look a the "Kernel Suspend" link in my signature for more troubleshooting steps.

---

### Post by Toz on 2013-05-02
@shanepardue,
One more suggestion. Can you try the **acpi_sleep=nonvs** kernel parameter?
> nonvs  - prevents the kernel from saving/restoring the
ACPI NVS memory during suspend/hibernation and resume.
Reference: [https://www.kernel.org/doc/Documentation/kernel-parameters.txt]("https://www.kernel.org/doc/Documentation/kernel-parameters.txt")

---

### Post by shanepardue on 2013-05-03
> **Toz said:**
> @shanepardue,
One more suggestion. Can you try the **acpi_sleep=nonvs** kernel parameter?

Reference: [https://www.kernel.org/doc/Documentation/kernel-parameters.txt]("https://www.kernel.org/doc/Documentation/kernel-parameters.txt")

That kernel parameter didn't change anything. I also tried many different mainline kernels including 3.3 from Precise and a nightly from the intel-experimental branch.

---

### Post by shanepardue on 2013-05-05
I unplugged an IR Receiver that was plugged into the USB3 port and suspend is working now. Should've tried this earlier when you mentioned that port being a possible culprit, but oh well. Does this mean the machine can't sleep when USB3 devices are plugged in?

---

### Post by Toz on 2013-05-06
> **shanepardue said:**
> I unplugged an IR Receiver that was plugged into the USB3 port and suspend is working now. Should've tried this earlier when you mentioned that port being a possible culprit, but oh well. Does this mean the machine can't sleep when USB3 devices are plugged in?

Does the ir receiver load a module? If so, we can automatically unload it. Compare the results of "lsmod" before and after inserting the receiver.

Also, run the following command:
```
tail -f /var/log/syslog
```
...insert the receiver, and post back any messages that appear.

---

