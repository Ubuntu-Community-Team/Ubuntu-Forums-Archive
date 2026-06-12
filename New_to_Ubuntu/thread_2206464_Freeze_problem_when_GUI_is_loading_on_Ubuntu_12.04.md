---
title: "Freeze problem when GUI is loading on Ubuntu 12.04; a fglrx driver issue?"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by Caio_Martins on 2014-02-19
Hello, everyone.

I have a Dell Latitude 3540 with an AMD Radeon HD 8850m video card and with Ubuntu 12.04 installed. The thing is: everytime I restart my notebook almost invariably I get corrupted loading screen and there's a chance I'll also get a freeze when the GUI is still loading.
I got this feeling this is related to the fglrx driver, which is installed on my machine. 
For instance, when I type the command fglrxinfo on the terminal I get this:
```

display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 8800M Series  
OpenGL version string: 4.3.12682 Compatibility Profile Context 13.30

```
With help (help that I got here:[http://ubuntuforums.org/showthread.php?t=2206363](http://ubuntuforums.org/showthread.php?t=2206363)), I was finally able to get a dmesg which I think might be relevant when I tried nomodeset on my default kernel. I also tried single user mode and got another dmesg.
I'm not sure whether they've captured what my problem really is... I hope they do.
Here is what I got with single user mode:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-36-generic (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #52~precise1-Ubuntu SMP Mon Feb 3 21:54:46 UTC 2014 (Ubuntu 3.8.0-36.52~precise1-generic 3.8.13.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-36-generic.efi.signed root=UUID=bdb52052-ce62-4bc1-9385-0536a3a121e8 ro quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000006efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000006f000-0x000000000006ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000070000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000c6d5ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c6d60000-0x00000000c7d5ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c7d60000-0x00000000cc36efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cc36f000-0x00000000ccebefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ccebf000-0x00000000ccfbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ccfbf000-0x00000000ccffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ccfff000-0x00000000ccffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cd000000-0x00000000cf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe101000-0x00000000fe112fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022f5fffff] usable
[    0.000000] e820: update [mem 0xc5d3f018-0xc5d4f057] usable ==> usable
[    0.000000] e820: update [mem 0xc5d31018-0xc5d3e057] usable ==> usable
[    0.000000] e820: update [mem 0xc5d21018-0xc5d30257] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000006efff] usable
[    0.000000] reserve setup_data: [mem 0x000000000006f000-0x000000000006ffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000070000-0x0000000000087fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x00000000c5d21017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d21018-0x00000000c5d30257] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d30258-0x00000000c5d31017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d31018-0x00000000c5d3e057] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d3e058-0x00000000c5d3f017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d3f018-0x00000000c5d4f057] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d4f058-0x00000000c6d5ffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c6d60000-0x00000000c7d5ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c7d60000-0x00000000cc36efff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cc36f000-0x00000000ccebefff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ccebf000-0x00000000ccfbefff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x00000000ccfbf000-0x00000000ccffefff] ACPI data
[    0.000000] reserve setup_data: [mem 0x00000000ccfff000-0x00000000ccffffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cd000000-0x00000000cf9fffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fe101000-0x00000000fe112fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000feb00000-0x00000000feb0ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000022f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0xccffe000  ACPI 2.0=0xccffe014  SMBIOS=0xccebef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=2, attr=0xf, range=[0x0000000000001000-0x0000000000004000) (0MB)
[    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000004000-0x000000000006f000) (0MB)
[    0.000000] efi: mem03: type=0, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem04: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000088000) (0MB)
[    0.000000] efi: mem05: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x000000000009f000) (0MB)
[    0.000000] efi: mem06: type=0, attr=0xf, range=[0x000000000009f000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000000100000-0x0000000001000000) (15MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000001000000-0x0000000002349000) (19MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000002349000-0x000000003f074000) (973MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x000000003f074000-0x0000000040000000) (15MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000040000000-0x00000000932a2000) (1330MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x00000000932a2000-0x00000000c4d70000) (794MB)
[    0.000000] efi: mem13: type=4, attr=0xf, range=[0x00000000c4d70000-0x00000000c4d90000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x00000000c4d90000-0x00000000c5d21000) (15MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x00000000c5d21000-0x00000000c5e13000) (0MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x00000000c5e13000-0x00000000c5e14000) (0MB)
[    0.000000] efi: mem17: type=2, attr=0xf, range=[0x00000000c5e14000-0x00000000c5e15000) (0MB)
[    0.000000] efi: mem18: type=7, attr=0xf, range=[0x00000000c5e15000-0x00000000c5e18000) (0MB)
[    0.000000] efi: mem19: type=2, attr=0xf, range=[0x00000000c5e18000-0x00000000c5e19000) (0MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x00000000c5e19000-0x00000000c5e1a000) (0MB)
[    0.000000] efi: mem21: type=2, attr=0xf, range=[0x00000000c5e1a000-0x00000000c5e1d000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x00000000c5e1d000-0x00000000c5e1f000) (0MB)
[    0.000000] efi: mem23: type=2, attr=0xf, range=[0x00000000c5e1f000-0x00000000c5ee1000) (0MB)
[    0.000000] efi: mem24: type=4, attr=0xf, range=[0x00000000c5ee1000-0x00000000c6d60000) (14MB)
[    0.000000] efi: mem25: type=0, attr=0xf, range=[0x00000000c6d60000-0x00000000c7d60000) (16MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x00000000c7d60000-0x00000000c7d63000) (0MB)
[    0.000000] efi: mem27: type=2, attr=0xf, range=[0x00000000c7d63000-0x00000000c7d65000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000c7d65000-0x00000000c7d67000) (0MB)
[    0.000000] efi: mem29: type=2, attr=0xf, range=[0x00000000c7d67000-0x00000000c7d68000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000c7d68000-0x00000000c7d6b000) (0MB)
[    0.000000] efi: mem31: type=2, attr=0xf, range=[0x00000000c7d6b000-0x00000000c7d6c000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x00000000c7d6c000-0x00000000c7d6d000) (0MB)
[    0.000000] efi: mem33: type=2, attr=0xf, range=[0x00000000c7d6d000-0x00000000c7d6f000) (0MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x00000000c7d6f000-0x00000000c7e3b000) (0MB)
[    0.000000] efi: mem35: type=1, attr=0xf, range=[0x00000000c7e3b000-0x00000000c7f6f000) (1MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x00000000c7f6f000-0x00000000c8c57000) (12MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x00000000c8c57000-0x00000000c8c58000) (0MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x00000000c8c58000-0x00000000c8d75000) (1MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x00000000c8d75000-0x00000000c8d7f000) (0MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x00000000c8d7f000-0x00000000c8da3000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x00000000c8da3000-0x00000000c8dda000) (0MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x00000000c8dda000-0x00000000c8ddb000) (0MB)
[    0.000000] efi: mem43: type=4, attr=0xf, range=[0x00000000c8ddb000-0x00000000c9c6d000) (14MB)
[    0.000000] efi: mem44: type=7, attr=0xf, range=[0x00000000c9c6d000-0x00000000c9c6e000) (0MB)
[    0.000000] efi: mem45: type=4, attr=0xf, range=[0x00000000c9c6e000-0x00000000c9e00000) (1MB)
[    0.000000] efi: mem46: type=3, attr=0xf, range=[0x00000000c9e00000-0x00000000c9e0d000) (0MB)
[    0.000000] efi: mem47: type=4, attr=0xf, range=[0x00000000c9e0d000-0x00000000c9e19000) (0MB)
[    0.000000] efi: mem48: type=3, attr=0xf, range=[0x00000000c9e19000-0x00000000c9e21000) (0MB)
[    0.000000] efi: mem49: type=4, attr=0xf, range=[0x00000000c9e21000-0x00000000c9e37000) (0MB)
[    0.000000] efi: mem50: type=7, attr=0xf, range=[0x00000000c9e37000-0x00000000c9e3a000) (0MB)
[    0.000000] efi: mem51: type=4, attr=0xf, range=[0x00000000c9e3a000-0x00000000c9e5a000) (0MB)
[    0.000000] efi: mem52: type=3, attr=0xf, range=[0x00000000c9e5a000-0x00000000c9ed5000) (0MB)
[    0.000000] efi: mem53: type=4, attr=0xf, range=[0x00000000c9ed5000-0x00000000c9ee8000) (0MB)
[    0.000000] efi: mem54: type=7, attr=0xf, range=[0x00000000c9ee8000-0x00000000c9ee9000) (0MB)
[    0.000000] efi: mem55: type=4, attr=0xf, range=[0x00000000c9ee9000-0x00000000c9ef5000) (0MB)
[    0.000000] efi: mem56: type=7, attr=0xf, range=[0x00000000c9ef5000-0x00000000c9ef7000) (0MB)
[    0.000000] efi: mem57: type=4, attr=0xf, range=[0x00000000c9ef7000-0x00000000cbf6f000) (32MB)
[    0.000000] efi: mem58: type=3, attr=0xf, range=[0x00000000cbf6f000-0x00000000cc36f000) (4MB)
[    0.000000] efi: mem59: type=5, attr=0x800000000000000f, range=[0x00000000cc36f000-0x00000000cc56f000) (2MB)
[    0.000000] efi: mem60: type=6, attr=0x800000000000000f, range=[0x00000000cc56f000-0x00000000ccabf000) (5MB)
[    0.000000] efi: mem61: type=0, attr=0xf, range=[0x00000000ccabf000-0x00000000ccebf000) (4MB)
[    0.000000] efi: mem62: type=10, attr=0xf, range=[0x00000000ccebf000-0x00000000ccfbf000) (1MB)
[    0.000000] efi: mem63: type=9, attr=0xf, range=[0x00000000ccfbf000-0x00000000ccfff000) (0MB)
[    0.000000] efi: mem64: type=4, attr=0xf, range=[0x00000000ccfff000-0x00000000cd000000) (0MB)
[    0.000000] efi: mem65: type=7, attr=0xf, range=[0x0000000100000000-0x000000022f600000) (4854MB)
[    0.000000] efi: mem66: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem67: type=0, attr=0x0, range=[0x00000000cd000000-0x00000000cfa00000) (42MB)
[    0.000000] efi: mem68: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
[    0.000000] efi: mem69: type=0, attr=0x0, range=[0x00000000fe101000-0x00000000fe113000) (0MB)
[    0.000000] efi: mem70: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb10000) (0MB)
[    0.000000] efi: mem71: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem72: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed1c000) (0MB)
[    0.000000] efi: mem73: type=11, attr=0x8000000000000000, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem74: type=11, attr=0x8000000000000001, range=[0x00000000fed20000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem75: type=11, attr=0x8000000000000000, range=[0x00000000ffc00000-0x0000000100000000) (4MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Latitude 3540/09HY4K, BIOS A04 11/12/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x22f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 0080000000 mask 7FC0000000 write-back
[    0.000000]   2 base 00C0000000 mask 7FF8000000 write-back
[    0.000000]   3 base 00C8000000 mask 7FFC000000 write-back
[    0.000000]   4 base 00CC000000 mask 7FFF000000 write-back
[    0.000000]   5 base 00FFC00000 mask 7FFFC00000 write-protect
[    0.000000]   6 base 0100000000 mask 7F00000000 write-back
[    0.000000]   7 base 0200000000 mask 7FC0000000 write-back
[    0.000000]   8 base 022F600000 mask 7FFFE00000 uncachable
[    0.000000]   9 base 022F800000 mask 7FFF800000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xcd000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000082000] 82000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xccffffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xccffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xccffffff @ [mem 0x1fffe000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x22f5fffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000]  [mem 0x200000000-0x22f5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x22f5fffff @ [mem 0xc9ef5000-0xc9ef6fff]
[    0.000000] RAMDISK: [mem 0x3f074000-0x3fffafff]
[    0.000000] ACPI: RSDP 00000000ccffe014 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000ccffe210 000B4 (v01 DELL    CL09    00000001      01000013)
[    0.000000] ACPI: FACP 00000000ccff7000 0010C (v05 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI Error: Gpe0Block - 32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS struct - 255 bits max, truncating (20121018/tbfadt-201)
[    0.000000] ACPI BIOS Bug: Warning: 32/64X length mismatch in FADT/Gpe0Block: 256/255 (20121018/tbfadt-567)
[    0.000000] ACPI: DSDT 00000000ccfe8000 0B8A5 (v01 DELL    CL09    00000000 ASL  00040000)
[    0.000000] ACPI: FACS 00000000ccfb8000 00040
[    0.000000] ACPI: SLIC 00000000ccffd000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: UEFI 00000000ccffc000 00236 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: FPDT 00000000ccffa000 00044 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MSDM 00000000ccff9000 00055 (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASF! 00000000ccff8000 000A5 (v32 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: HPET 00000000ccff6000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: APIC 00000000ccff5000 0008C (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MCFG 00000000ccff4000 0003C (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000ccfe7000 006FE (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000ccfe5000 00028 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASPT 00000000ccfe3000 00034 (v07 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DBGP 00000000ccfe2000 00034 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000ccfdc000 00539 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000ccfdb000 00AD8 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000ccfd7000 03517 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000ccfd4000 01E3D (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BGRT 00000000ccfd6000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22f5fffff]
[    0.000000]   NODE_DATA [mem 0x22f5fb000-0x22f5fffff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880226c00000-ffff88022ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0006efff]
[    0.000000]   node   0: [mem 0x00070000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0xc6d5ffff]
[    0.000000]   node   0: [mem 0xc7d60000-0xcc36efff]
[    0.000000]   node   0: [mem 0xccfff000-0xccffffff]
[    0.000000]   node   0: [mem 0x100000000-0x22f5fffff]
[    0.000000] On node 0 totalpages: 2074855
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3889 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12942 pages used for memmap
[    0.000000]   DMA32 zone: 815330 pages, LIFO batch:31
[    0.000000]   Normal zone: 19416 pages used for memmap
[    0.000000]   Normal zone: 1223208 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 56
[    0.000000] PM: Registered nosave memory: 000000000006f000 - 0000000000070000
[    0.000000] PM: Registered nosave memory: 0000000000088000 - 00000000000c0000
[    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000c5d21000 - 00000000c5d22000
[    0.000000] PM: Registered nosave memory: 00000000c5d30000 - 00000000c5d31000
[    0.000000] PM: Registered nosave memory: 00000000c5d31000 - 00000000c5d32000
[    0.000000] PM: Registered nosave memory: 00000000c5d3e000 - 00000000c5d3f000
[    0.000000] PM: Registered nosave memory: 00000000c5d3f000 - 00000000c5d40000
[    0.000000] PM: Registered nosave memory: 00000000c5d4f000 - 00000000c5d50000
[    0.000000] PM: Registered nosave memory: 00000000c6d60000 - 00000000c7d60000
[    0.000000] PM: Registered nosave memory: 00000000cc36f000 - 00000000ccebf000
[    0.000000] PM: Registered nosave memory: 00000000ccebf000 - 00000000ccfbf000
[    0.000000] PM: Registered nosave memory: 00000000ccfbf000 - 00000000ccfff000
[    0.000000] PM: Registered nosave memory: 00000000cd000000 - 00000000cfa00000
[    0.000000] PM: Registered nosave memory: 00000000cfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fe101000
[    0.000000] PM: Registered nosave memory: 00000000fe101000 - 00000000fe113000
[    0.000000] PM: Registered nosave memory: 00000000fe113000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb10000
[    0.000000] PM: Registered nosave memory: 00000000feb10000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] e820: [mem 0xcfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022f200000 s84928 r8192 d21568 u262144
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2042427
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-36-generic.efi.signed root=UUID=bdb52052-ce62-4bc1-9385-0536a3a121e8 ro quiet splash acpi_backlight=vendor vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7999392k/9164800k available (7175k kernel code, 865380k absent, 300028k reserved, 6068k data, 1016k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:1016 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2394.463 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.92 BogoMIPS (lpj=9577852)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.045836] Security Framework initialized
[    0.045846] AppArmor: AppArmor initialized
[    0.045848] Yama: becoming mindful.
[    0.046485] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.048236] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.048949] Mount-cache hash table entries: 256
[    0.049134] Initializing cgroup subsys cpuacct
[    0.049136] Initializing cgroup subsys memory
[    0.049143] Initializing cgroup subsys devices
[    0.049145] Initializing cgroup subsys freezer
[    0.049146] Initializing cgroup subsys blkio
[    0.049148] Initializing cgroup subsys perf_event
[    0.049151] Initializing cgroup subsys hugetlb
[    0.049178] CPU: Physical Processor ID: 0
[    0.049179] CPU: Processor Core ID: 0
[    0.049184] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.049184] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.050368] mce: CPU supports 7 MCE banks
[    0.050385] CPU0: Thermal monitoring enabled (TM1)
[    0.050396] process: using mwait in idle threads
[    0.050399] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.050399] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.050399] tlb_flushall_shift: 6
[    0.050563] Freeing SMP alternatives: 24k freed
[    0.052671] ACPI: Core revision 20121018
[    0.070850] ftrace: allocating 29401 entries in 115 pages
[    0.087380] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.127006] smpboot: CPU0: Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz (fam: 06, model: 45, stepping: 01)
[    0.127015] TSC deadline timer enabled
[    0.127018] Performance Events: no PEBS fmt2+, generic architected perfmon, Intel PMU driver.
[    0.127024] ... version:                3
[    0.127025] ... bit width:              48
[    0.127027] ... generic registers:      4
[    0.127028] ... value mask:             0000ffffffffffff
[    0.127029] ... max period:             000000007fffffff
[    0.127030] ... fixed-purpose events:   3
[    0.127032] ... event mask:             000000070000000f
[    0.142902] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.128329] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.171688] Brought up 4 CPUs
[    0.171692] smpboot: Total of 4 processors activated (19155.70 BogoMIPS)
[    0.177651] devtmpfs: initialized
[    0.178879] EVM: security.selinux
[    0.178881] EVM: security.SMACK64
[    0.178882] EVM: security.capability
[    0.178937] PM: Registering ACPI NVS region [mem 0xccebf000-0xccfbefff] (1048576 bytes)
[    0.179756] regulator-dummy: no parameters
[    0.179805] NET: Registered protocol family 16
[    0.179983] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.179985] ACPI: bus type pci registered
[    0.180053] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.180056] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.193059] PCI: Using configuration type 1 for base access
[    0.193211] dmi type 0xB1 record - unknown flag
[    0.194197] bio: create slab <bio-0> at 0
[    0.194285] ACPI: Added _OSI(Module Device)
[    0.194287] ACPI: Added _OSI(Processor Device)
[    0.194291] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.194292] ACPI: Added _OSI(Processor Aggregator Device)
[    0.196831] ACPI: EC: Look up EC in DSDT
[    0.199547] ACPI: Executed 1 blocks of module-level executable AML code
[    0.203689] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.204697] ACPI: SSDT 00000000cce7dc18 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.205335] ACPI: Dynamic OEM Table Load:
[    0.205337] ACPI: SSDT           (null) 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.205694] ACPI: SSDT 00000000cce7d618 005AA (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.206425] ACPI: Dynamic OEM Table Load:
[    0.206428] ACPI: SSDT           (null) 005AA (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.206588] ACPI: SSDT 00000000cce7cd98 00119 (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.207225] ACPI: Dynamic OEM Table Load:
[    0.207227] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.325292] ACPI: Interpreter enabled
[    0.325297] ACPI: (supports S0 S3 S4 S5)
[    0.325330] ACPI: Using IOAPIC for interrupt routing
[    0.450654] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.450851] ACPI: No dock devices found.
[    0.450855] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.451006] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.451008] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.451583] PCI host bridge to bus 0000:00
[    0.451587] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.451589] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.451591] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.451593] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.451595] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.451597] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.451599] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.451601] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.451603] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.451605] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.451606] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.451608] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.451610] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.451612] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.451614] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.451616] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.451617] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.451619] pci_bus 0000:00: root bus resource [mem 0xcfa00000-0xfeafffff]
[    0.451629] pci 0000:00:00.0: [8086:0a04] type 00 class 0x060000
[    0.451675] pci 0000:00:02.0: [8086:0a16] type 00 class 0x030000
[    0.451689] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.451698] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.451704] pci 0000:00:02.0: reg 20: [io  0x5000-0x503f]
[    0.451762] pci 0000:00:14.0: [8086:9c31] type 00 class 0x0c0330
[    0.451781] pci 0000:00:14.0: reg 10: [mem 0xf0800000-0xf080ffff 64bit]
[    0.451844] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.451865] pci 0000:00:16.0: [8086:9c3a] type 00 class 0x078000
[    0.451888] pci 0000:00:16.0: reg 10: [mem 0xf0814000-0xf081401f 64bit]
[    0.451961] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.451993] pci 0000:00:1b.0: [8086:9c20] type 00 class 0x040300
[    0.452008] pci 0000:00:1b.0: reg 10: [mem 0xf0810000-0xf0813fff 64bit]
[    0.452075] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.452095] pci 0000:00:1c.0: [8086:9c14] type 01 class 0x060400
[    0.452163] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.452188] pci 0000:00:1c.3: [8086:9c16] type 01 class 0x060400
[    0.452256] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.452277] pci 0000:00:1c.4: [8086:9c18] type 01 class 0x060400
[    0.452345] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.452375] pci 0000:00:1d.0: [8086:9c26] type 00 class 0x0c0320
[    0.453302] pci 0000:00:1d.0: reg 10: [mem 0xf0818000-0xf08183ff]
[    0.458749] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.458776] pci 0000:00:1f.0: [8086:9c43] type 00 class 0x060100
[    0.458911] pci 0000:00:1f.2: [8086:9c03] type 00 class 0x010601
[    0.458927] pci 0000:00:1f.2: reg 10: [io  0x5088-0x508f]
[    0.458935] pci 0000:00:1f.2: reg 14: [io  0x5094-0x5097]
[    0.458942] pci 0000:00:1f.2: reg 18: [io  0x5080-0x5087]
[    0.458950] pci 0000:00:1f.2: reg 1c: [io  0x5090-0x5093]
[    0.458958] pci 0000:00:1f.2: reg 20: [io  0x5060-0x507f]
[    0.458966] pci 0000:00:1f.2: reg 24: [mem 0xf0817000-0xf08177ff]
[    0.459005] pci 0000:00:1f.2: PME# supported from D3hot
[    0.459019] pci 0000:00:1f.3: [8086:9c22] type 00 class 0x0c0500
[    0.459034] pci 0000:00:1f.3: reg 10: [mem 0xf0815000-0xf08150ff 64bit]
[    0.459056] pci 0000:00:1f.3: reg 20: [io  0x5040-0x505f]
[    0.459137] pci 0000:01:00.0: [10ec:8168] type 00 class 0x020000
[    0.459154] pci 0000:01:00.0: reg 10: [io  0x4000-0x40ff]
[    0.459184] pci 0000:01:00.0: reg 18: [mem 0xf0700000-0xf0700fff 64bit]
[    0.459203] pci 0000:01:00.0: reg 20: [mem 0xf0400000-0xf0403fff 64bit pref]
[    0.459282] pci 0000:01:00.0: supports D1 D2
[    0.459284] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.465376] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.465380] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.465384] pci 0000:00:1c.0:   bridge window [mem 0xf0700000-0xf07fffff]
[    0.465389] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.465456] pci 0000:02:00.0: [168c:0036] type 00 class 0x028000
[    0.465489] pci 0000:02:00.0: reg 10: [mem 0xf0600000-0xf067ffff 64bit]
[    0.465568] pci 0000:02:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.465649] pci 0000:02:00.0: supports D1 D2
[    0.465650] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.473383] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.473388] pci 0000:00:1c.3:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.473450] pci 0000:03:00.0: [1002:6823] type 00 class 0x030000
[    0.473475] pci 0000:03:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.473496] pci 0000:03:00.0: reg 18: [mem 0xf0500000-0xf053ffff 64bit]
[    0.473509] pci 0000:03:00.0: reg 20: [io  0x3000-0x30ff]
[    0.473534] pci 0000:03:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.473611] pci 0000:03:00.0: supports D1 D2
[    0.473613] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.481368] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.481372] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.481375] pci 0000:00:1c.4:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.481381] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.481444] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.481497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.481546] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.481720]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.482126]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.483510] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483557] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483599] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483644] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483687] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483732] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483776] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483818] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483915] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.483923] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=none,locks=none
[    0.483924] vgaarb: loaded
[    0.483926] vgaarb: bridge control possible 0000:03:00.0
[    0.483927] vgaarb: no bridge control possible 0000:00:02.0
[    0.484096] SCSI subsystem initialized
[    0.484098] ACPI: bus type scsi registered
[    0.484133] libata version 3.00 loaded.
[    0.484151] ACPI: bus type usb registered
[    0.484167] usbcore: registered new interface driver usbfs
[    0.484175] usbcore: registered new interface driver hub
[    0.484196] usbcore: registered new device driver usb
[    0.484281] PCI: Using ACPI for IRQ routing
[    0.485732] PCI: pci_cache_line_size set to 64 bytes
[    0.485784] e820: reserve RAM buffer [mem 0x0006f000-0x0006ffff]
[    0.485786] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    0.485788] e820: reserve RAM buffer [mem 0xc5d21018-0xc7ffffff]
[    0.485790] e820: reserve RAM buffer [mem 0xc5d31018-0xc7ffffff]
[    0.485792] e820: reserve RAM buffer [mem 0xc5d3f018-0xc7ffffff]
[    0.485794] e820: reserve RAM buffer [mem 0xc6d60000-0xc7ffffff]
[    0.485795] e820: reserve RAM buffer [mem 0xcc36f000-0xcfffffff]
[    0.485797] e820: reserve RAM buffer [mem 0xcd000000-0xcfffffff]
[    0.485799] e820: reserve RAM buffer [mem 0x22f600000-0x22fffffff]
[    0.485879] NetLabel: Initializing
[    0.485881] NetLabel:  domain hash size = 128
[    0.485882] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.485893] NetLabel:  unlabeled traffic allowed by default
[    0.485951] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.485958] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.487964] Switching to clocksource hpet
[    0.493271] AppArmor: AppArmor Filesystem Enabled
[    0.493292] pnp: PnP ACPI init
[    0.493305] ACPI: bus type pnp registered
[    0.493340] pnp 00:00: [dma 4]
[    0.493360] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.493378] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.493497] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.493538] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.493541] system 00:03: [io  0xfd60-0xfd63] has been reserved
[    0.493543] system 00:03: [io  0xffff] has been reserved
[    0.493545] system 00:03: [io  0xffff] has been reserved
[    0.493547] system 00:03: [io  0xffff] has been reserved
[    0.493549] system 00:03: [io  0x1800-0x18fe] has been reserved
[    0.493551] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.493554] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.493600] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.493643] system 00:05: [io  0x1854-0x1857] has been reserved
[    0.493646] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.493697] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.493725] pnp 00:07: Plug and Play ACPI device, IDs DLL0609 PNP0f13 (active)
[    0.552045] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.552048] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.552050] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.552052] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.552055] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.552057] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.552059] system 00:08: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.552061] system 00:08: [mem 0xff000000-0xff000fff] has been reserved
[    0.552064] system 00:08: [mem 0xff010000-0xffffffff] could not be reserved
[    0.552066] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.552068] system 00:08: [mem 0xcfa22000-0xcfa22fff] has been reserved
[    0.552071] system 00:08: [mem 0xcfa10000-0xcfa1ffff] has been reserved
[    0.552074] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.552679] pnp: PnP ACPI: found 9 devices
[    0.552681] ACPI: ACPI bus type pnp unregistered
[    0.558730] pci 0000:02:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.558733] pci 0000:03:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.558767] pci 0000:00:1c.3: BAR 15: assigned [mem 0xcfb00000-0xcfbfffff pref]
[    0.558770] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.558773] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.558778] pci 0000:00:1c.0:   bridge window [mem 0xf0700000-0xf07fffff]
[    0.558782] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.558789] pci 0000:02:00.0: BAR 6: assigned [mem 0xcfb00000-0xcfb0ffff pref]
[    0.558791] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.558796] pci 0000:00:1c.3:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.558799] pci 0000:00:1c.3:   bridge window [mem 0xcfb00000-0xcfbfffff pref]
[    0.558806] pci 0000:03:00.0: BAR 6: assigned [mem 0xf0540000-0xf055ffff pref]
[    0.558808] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.558811] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.558815] pci 0000:00:1c.4:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.558819] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.558850] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.558852] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.558854] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.558856] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.558858] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.558860] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.558862] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.558863] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.558865] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.558867] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.558869] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.558871] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.558873] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.558875] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.558876] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.558878] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.558880] pci_bus 0000:00: resource 20 [mem 0xcfa00000-0xfeafffff]
[    0.558882] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.558884] pci_bus 0000:01: resource 1 [mem 0xf0700000-0xf07fffff]
[    0.558886] pci_bus 0000:01: resource 2 [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.558889] pci_bus 0000:02: resource 1 [mem 0xf0600000-0xf06fffff]
[    0.558890] pci_bus 0000:02: resource 2 [mem 0xcfb00000-0xcfbfffff pref]
[    0.558892] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.558894] pci_bus 0000:03: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.558896] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.558928] NET: Registered protocol family 2
[    0.559118] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.559324] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.559454] TCP: Hash tables configured (established 65536 bind 65536)
[    0.559472] TCP: reno registered
[    0.559486] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.559518] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.559586] NET: Registered protocol family 1
[    0.559598] pci 0000:00:02.0: Boot video device
[    0.575885] PCI: CLS 64 bytes, default 64
[    0.575924] Trying to unpack rootfs image as initramfs...
[    0.900607] Freeing initrd memory: 15900k freed
[    0.902763] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.902768] software IO TLB [mem 0xc0d70000-0xc4d70000] (64MB) mapped at [ffff8800c0d70000-ffff8800c4d6ffff]
[    0.902809] Simple Boot Flag at 0x44 set to 0x1
[    0.903146] Initialise module verification
[    0.903187] audit: initializing netlink socket (disabled)
[    0.903200] type=2000 audit(1392773396.868:1): initialized
[    0.942893] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.944389] VFS: Disk quotas dquot_6.5.2
[    0.944431] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.944867] fuse init (API version 7.20)
[    0.944932] msgmni has been set to 15791
[    0.945290] Key type asymmetric registered
[    0.945293] Asymmetric key parser 'x509' registered
[    0.945330] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.945353] io scheduler noop registered
[    0.945355] io scheduler deadline registered (default)
[    0.945360] io scheduler cfq registered
[    0.945477] pcieport 0000:00:1c.0: irq 56 for MSI/MSI-X
[    0.945567] pcieport 0000:00:1c.3: irq 57 for MSI/MSI-X
[    0.945650] pcieport 0000:00:1c.4: irq 58 for MSI/MSI-X
[    0.945723] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.945725] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.945729] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.945744] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.945746] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.945750] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.945766] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.945768] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.945772] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.945783] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.945796] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.945851] efifb: probing for efifb
[    0.947678] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90009500000, using 8100k, total 8100k
[    0.947680] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    0.947681] efifb: scrolling: redraw
[    0.947683] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.953057] Console: switching to colour frame buffer device 240x67
[    0.958329] fb0: EFI VGA frame buffer device
[    0.958335] intel_idle: MWAIT substates: 0x11142120
[    0.958336] intel_idle: v0.4 model 0x45
[    0.958337] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.958339] intel_idle: unaware of model 0x45 MWAIT 5 please contact lenb@kernel.org
[    0.958340] intel_idle: unaware of model 0x45 MWAIT 6 please contact lenb@kernel.org
[    0.958342] intel_idle: unaware of model 0x45 MWAIT 7 please contact lenb@kernel.org
[    0.958430] ACPI: AC Adapter [ACAD] (on-line)
[    0.958547] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0D:00/input/input0
[    0.958578] ACPI: Lid Switch [LID0]
[    0.958607] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input1
[    0.958612] ACPI: Power Button [PWRB]
[    0.958650] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.958653] ACPI: Power Button [PWRF]
[    0.958731] ACPI: Requesting acpi_cpufreq
[    1.081569] GHES: HEST is not enabled!
[    1.081640] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.139003] ACPI: Battery Slot [BAT1] (battery absent)
[    1.139115] Linux agpgart interface v0.103
[    1.140191] brd: module loaded
[    1.140814] loop: module loaded
[    1.141106] libphy: Fixed MDIO Bus: probed
[    1.141164] tun: Universal TUN/TAP device driver, 1.6
[    1.141166] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.141209] PPP generic driver version 2.4.2
[    1.141251] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.141253] ehci-pci: EHCI PCI platform driver
[    1.141296] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.141300] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.141305] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.141318] ehci-pci 0000:00:1d.0: debug port 2
[    1.145203] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.145218] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf0818000
[    1.154975] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.154994] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.154996] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.154998] usb usb1: Product: EHCI Host Controller
[    1.155000] usb usb1: Manufacturer: Linux 3.8.0-36-generic ehci_hcd
[    1.155002] usb usb1: SerialNumber: 0000:00:1d.0
[    1.155132] hub 1-0:1.0: USB hub found
[    1.155137] hub 1-0:1.0: 2 ports detected
[    1.155238] ehci-platform: EHCI generic platform driver
[    1.155246] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.155258] uhci_hcd: USB Universal Host Controller Interface driver
[    1.155309] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.155312] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.155317] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.155391] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.155427] xhci_hcd 0000:00:14.0: irq 59 for MSI/MSI-X
[    1.155470] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.155472] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.155474] usb usb2: Product: xHCI Host Controller
[    1.155476] usb usb2: Manufacturer: Linux 3.8.0-36-generic xhci_hcd
[    1.155477] usb usb2: SerialNumber: 0000:00:14.0
[    1.155548] xHCI xhci_add_endpoint called for root hub
[    1.155550] xHCI xhci_check_bandwidth called for root hub
[    1.155568] hub 2-0:1.0: USB hub found
[    1.155577] hub 2-0:1.0: 9 ports detected
[    1.156935] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.156939] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.156959] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    1.156961] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.156963] usb usb3: Product: xHCI Host Controller
[    1.156964] usb usb3: Manufacturer: Linux 3.8.0-36-generic xhci_hcd
[    1.156966] usb usb3: SerialNumber: 0000:00:14.0
[    1.157034] xHCI xhci_add_endpoint called for root hub
[    1.157035] xHCI xhci_check_bandwidth called for root hub
[    1.157055] hub 3-0:1.0: USB hub found
[    1.157061] hub 3-0:1.0: 4 ports detected
[    1.157665] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.185950] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.185954] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.186063] mousedev: PS/2 mouse device common for all mice
[    1.187806] rtc_cmos 00:04: RTC can wake from S4
[    1.187928] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.187955] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.188032] device-mapper: uevent: version 1.0.3
[    1.188091] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.188179] cpuidle: using governor ladder
[    1.188276] cpuidle: using governor menu
[    1.188281] ledtrig-cpu: registered to indicate activity on CPUs
[    1.188283] EFI Variables Facility v0.08 2004-May-17
[    1.217094] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.466536] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.541565] ashmem: initialized
[    1.541688] TCP: cubic registered
[    1.541775] NET: Registered protocol family 10
[    1.541929] NET: Registered protocol family 17
[    1.541944] Key type dns_resolver registered
[    1.542171] Loading module verification certificates
[    1.543142] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 65309af67f6c263a4d5f1db346570b5bfb944cad'
[    1.543152] registered taskstats version 1
[    1.545296] Key type trusted registered
[    1.547082] Key type encrypted registered
[    1.549173] rtc_cmos 00:04: setting system clock to 2014-02-19 01:29:57 UTC (1392773397)
[    1.550127] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.550129] EDD information not available.
[    1.551930] Freeing unused kernel memory: 1016k freed
[    1.552054] Write protecting the kernel read-only data: 12288k
[    1.555242] Freeing unused kernel memory: 1004k freed
[    1.558265] Freeing unused kernel memory: 952k freed
[    1.573610] udevd[107]: starting version 175
[    1.598696] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.598702] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.598992] hub 1-1:1.0: USB hub found
[    1.599066] hub 1-1:1.0: 8 ports detected
[    1.599784] Disabling lock debugging due to kernel taint
[    1.600231] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.600737] ahci 0000:00:1f.2: version 3.0
[    1.600795] ahci 0000:00:1f.2: irq 60 for MSI/MSI-X
[    1.606684] r8169 0000:01:00.0: irq 61 for MSI/MSI-X
[    1.606971] r8169 0000:01:00.0 eth0: RTL8168g/8111g at 0xffffc9000003c000, a4:1f:72:f7:a5:90, XID 0c000800 IRQ 61
[    1.606976] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.614294] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 3 ports 6 Gbps 0x3 impl SATA mode
[    1.614303] ahci 0000:00:1f.2: flags: 64bit ncq led clo only pio slum part deso sadm sds apst 
[    1.614309] ahci 0000:00:1f.2: setting latency timer to 64
[    1.616124] scsi0 : ahci
[    1.617062] scsi1 : ahci
[    1.618403] scsi2 : ahci
[    1.618500] ata1: SATA max UDMA/133 abar m2048@0xf0817000 port 0xf0817100 irq 60
[    1.618504] ata2: SATA max UDMA/133 abar m2048@0xf0817000 port 0xf0817180 irq 60
[    1.618506] ata3: DUMMY
[    1.870077] usb 1-1.3: new low-speed USB device number 3 using ehci-pci
[    1.897879] tsc: Refined TSC clocksource calibration: 2394.457 MHz
[    1.897885] Switching to clocksource tsc
[    1.937826] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.937846] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.938686] ata1.00: ATA-9: WDC WD7500BPVX-75JC3T0, 01.01A01, max UDMA/133
[    1.938690] ata1.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.939587] ata1.00: configured for UDMA/133
[    1.939791] scsi 0:0:0:0: Direct-Access     ATA      WDC WD7500BPVX-7 01.0 PQ: 0 ANSI: 5
[    1.939973] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.939977] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.939982] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.940113] sd 0:0:0:0: [sda] Write Protect is off
[    1.940116] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.940213] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.948038] ata2.00: ATAPI: PLDS DVD+/-RW DU-8A5HH, SD12, max UDMA/100
[    1.948804] ata2.00: configured for UDMA/100
[    1.957046] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DU-8A5HH SD12 PQ: 0 ANSI: 5
[    1.965554] usb 1-1.3: New USB device found, idVendor=15d9, idProduct=0a4e
[    1.965559] usb 1-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.965561] usb 1-1.3: Product:  USB OPTICAL MOUSE
[    1.965978] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.965983] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.966091] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.966270] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.970423] usbcore: registered new interface driver usbhid
[    1.970426] usbhid: USB HID core driver
[    1.972096] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input4
[    1.972200] hid-generic 0003:15D9:0A4E.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.3/input0
[    2.001695]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    2.002406] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.037770] usb 1-1.5: new full-speed USB device number 4 using ehci-pci
[    2.130640] usb 1-1.5: New USB device found, idVendor=0cf3, idProduct=0036
[    2.130645] usb 1-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.201516] usb 1-1.7: new high-speed USB device number 5 using ehci-pci
[    2.294123] usb 1-1.7: New USB device found, idVendor=0bda, idProduct=0129
[    2.294128] usb 1-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.294130] usb 1-1.7: Product: USB2.0-CRW
[    2.294132] usb 1-1.7: Manufacturer: Generic
[    2.294134] usb 1-1.7: SerialNumber: 20100201396000000
[    2.365317] usb 1-1.8: new high-speed USB device number 6 using ehci-pci
[    2.522179] usb 1-1.8: New USB device found, idVendor=0c45, idProduct=64ad
[    2.522183] usb 1-1.8: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    2.522185] usb 1-1.8: Product: Laptop_Integrated_Webcam_HD
[    2.522187] usb 1-1.8: Manufacturer: CN0Y3PX8724873C3A06XA01
[    3.306276] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[    4.504472] init: ureadahead main process (288) terminated with status 5
[    5.926539] Adding 9764860k swap on /dev/sda7.  Priority:-1 extents:1 across:9764860k 
[    6.599842] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.999782] udevd[366]: starting version 175
[    8.022460] lp: driver loaded but no devices found
[    8.173688] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x17
[    8.222204] cfg80211: Calling CRDA to update world regulatory domain
[    8.245726] Bluetooth: Core ver 2.16
[    8.245747] NET: Registered protocol family 31
[    8.245749] Bluetooth: HCI device and connection manager initialized
[    8.245757] Bluetooth: HCI socket layer initialized
[    8.245760] Bluetooth: L2CAP socket layer initialized
[    8.245767] Bluetooth: SCO socket layer initialized
[    8.324262] wmi: Mapper loaded
[    8.327951] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    8.327972] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.327977] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPRL 1 (20121018/utaddress-251)
[    8.327983] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPR_ 2 (20121018/utaddress-251)
[    8.327988] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.327991] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPRL 1 (20121018/utaddress-251)
[    8.327996] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPR_ 2 (20121018/utaddress-251)
[    8.328001] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \IO_D 3 (20121018/utaddress-251)
[    8.328006] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.328008] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.341640] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[    8.341644] AMD IOMMUv2 functionality not available on this system
[    8.413865] Linux video capture interface: v2.00
[    8.443573] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x17
[    8.444764] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x17
[    8.445929] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x17
[    8.447217] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.485231] usbcore: registered new interface driver btusb
[    8.513847] [drm] Initialized drm 1.1.0 20060810
[    8.517383] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[    8.520850] scsi3 : SCSI emulation for RTS5139 USB card reader
[    8.520971] usbcore: registered new interface driver rts5139
[    8.521007] scsi 3:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[    8.521619] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    8.524206] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[    8.611204] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.635326] ath: EEPROM regdomain: 0x60
[    8.635329] ath: EEPROM indicates we should expect a direct regpair map
[    8.635332] ath: Country alpha2 being used: 00
[    8.635333] ath: Regpair used: 0x60
[    8.674526] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[    8.674945] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffc9000a900000, irq=19
[    8.733089] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0c45:64ad)
[    8.771859] usbcore: registered new interface driver ath3k
[    8.773448] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.8/1-1.8:1.0/input/input5
[    8.773533] usbcore: registered new interface driver uvcvideo
[    8.773536] USB Video Class driver (1.1.1)
[    8.814757] usb 1-1.5: USB disconnect, device number 4
[    8.852570] input: Dell WMI hotkeys as /devices/virtual/input/input6
[    9.005086] [drm] Memory usable by graphics device = 2048M
[    9.005090] checking generic (e0000000 7e9000) vs hw (e0000000 10000000)
[    9.005092] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[    9.005123] Console: switching to colour dummy device 80x25
[    9.005231] i915 0000:00:02.0: setting latency timer to 64
[    9.015576] usb 1-1.5: new full-speed USB device number 7 using ehci-pci
[    9.061545] [drm:i915_write32] *ERROR* Unknown unclaimed register before writing to a090
[    9.061792] i915 0000:00:02.0: irq 62 for MSI/MSI-X
[    9.061804] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    9.061805] [drm] Driver supports precise vblank timestamp query.
[    9.061842] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    9.061844] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:03:00.0
[    9.180516] fbcon: inteldrmfb (fb0) is primary device
[    9.615679] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00, board id: 2382, fw id: 1238635
[    9.721713] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   10.054469] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   10.062998] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7667 MBytes.
[   10.063206] <6>[fglrx]   vendor: 1002 device: 6823 count: 1
[   10.063471] <6>[fglrx] ioport: bar 4, base 0x3000, size: 0x100
[   10.063478] pci 0000:03:00.0: enabling device (0000 -> 0003)
[   10.063568] <6>[fglrx] Kernel PAT support is enabled
[   10.063585] <6>[fglrx] module loaded - fglrx 13.30.1 [Jan  8 2014] with 1 minors
[   10.748281] [drm:intel_dp_set_link_train] *ERROR* Timed out waiting for DP idle patterns
[   10.748283] [drm:i915_write32] *ERROR* Unknown unclaimed register before writing to 64040
[   10.796322] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   10.804314] Console: switching to colour frame buffer device 240x67
[   10.809634] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   10.809635] i915 0000:00:02.0: registered panic notifier
[   10.811202] i915 0000:00:02.0: More than 8 outputs detected
[   10.811310] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   10.812770] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   10.812825] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2e/LNXVIDEO:00/input/input8
[   10.814421] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   10.814470] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   10.814541] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   10.814581] mei 0000:00:16.0: setting latency timer to 64
[   10.814652] mei 0000:00:16.0: irq 63 for MSI/MSI-X
[   11.107821] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   11.159346] type=1400 audit(1392773407.120:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=796 comm="apparmor_parser"
[   11.159360] type=1400 audit(1392773407.120:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=795 comm="apparmor_parser"
[   11.159370] type=1400 audit(1392773407.120:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=794 comm="apparmor_parser"
[   11.159854] type=1400 audit(1392773407.124:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=796 comm="apparmor_parser"
[   11.159900] type=1400 audit(1392773407.124:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=794 comm="apparmor_parser"
[   11.159908] type=1400 audit(1392773407.124:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=795 comm="apparmor_parser"
[   11.160136] type=1400 audit(1392773407.124:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=796 comm="apparmor_parser"
[   11.160199] type=1400 audit(1392773407.124:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=794 comm="apparmor_parser"
[   11.160207] type=1400 audit(1392773407.124:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=795 comm="apparmor_parser"
[   13.790737] init: failsafe main process (925) killed by TERM signal
[   14.100299] usb 1-1.5: New USB device found, idVendor=0cf3, idProduct=0036
[   14.100303] usb 1-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   15.705759] type=1400 audit(1392773411.676:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=985 comm="apparmor_parser"
[   17.087493] init: alsa-restore main process (1029) terminated with status 19
[   17.428150] ppdev: user-space parallel port driver
[   17.600072] audit_printk_skb: 51 callbacks suppressed
[   17.600076] type=1400 audit(1392773413.572:29): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1134 comm="apparmor_parser"
[   17.600483] type=1400 audit(1392773413.572:30): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1134 comm="apparmor_parser"
[   17.801468] mei 0000:00:16.0: init hw failure.
[   17.801534] mei 0000:00:16.0: initialization failed.
[   17.801643] snd_hda_intel 0000:00:1b.0: irq 63 for MSI/MSI-X
[   17.852271] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.854164] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.854168] Bluetooth: BNEP filters: protocol multicast
[   17.854175] Bluetooth: BNEP socket layer initialized
[   17.896140] Bluetooth: RFCOMM TTY layer initialized
[   17.896152] Bluetooth: RFCOMM socket layer initialized
[   17.896154] Bluetooth: RFCOMM ver 1.11
[   20.966140] r8169 0000:01:00.0 eth0: link down
[   20.966193] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.966464] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.976545] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.979694] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.283383] fglrx_pci 0000:03:00.0: irq 64 for MSI/MSI-X
[   22.284027] <6>[fglrx] Firegl kernel thread PID: 1345
[   22.284107] <6>[fglrx] Firegl kernel thread PID: 1346
[   22.284184] <6>[fglrx] Firegl kernel thread PID: 1347
[   22.284282] <6>[fglrx] IRQ 64 Enabled
[   22.297713] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.297716] <6>[fglrx] Reserved FB block: Unshared offset:f878000, size:4000 
[   22.297718] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   22.297720] <6>[fglrx] Reserved FB block: Unshared offset:7fff4000, size:c000 
[   23.828915] wlan0: authenticate with bc:f6:85:e2:fb:d6
[   23.836715] wlan0: send auth to bc:f6:85:e2:fb:d6 (try 1/3)
[   23.840744] wlan0: authenticated
[   23.844207] wlan0: associate with bc:f6:85:e2:fb:d6 (try 1/3)
[   23.848015] wlan0: RX AssocResp from bc:f6:85:e2:fb:d6 (capab=0x411 status=0 aid=2)
[   23.848056] wlan0: associated
[   23.848066] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

And here's what I got with nomodeset:
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-36-generic (buildd@aatxe) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #52~precise1-Ubuntu SMP Mon Feb 3 21:54:46 UTC 2014 (Ubuntu 3.8.0-36.52~precise1-generic 3.8.13.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-36-generic.efi.signed root=UUID=bdb52052-ce62-4bc1-9385-0536a3a121e8 ro quiet splash nomodeset
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000006efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000006f000-0x000000000006ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000070000-0x0000000000087fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000c6d5ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000c6d60000-0x00000000c7d5ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000c7d60000-0x00000000cc36efff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cc36f000-0x00000000ccebefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ccebf000-0x00000000ccfbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000ccfbf000-0x00000000ccffefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ccfff000-0x00000000ccffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cd000000-0x00000000cf9fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fe101000-0x00000000fe112fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022f5fffff] usable
[    0.000000] e820: update [mem 0xc5d3f018-0xc5d4f057] usable ==> usable
[    0.000000] e820: update [mem 0xc5d31018-0xc5d3e057] usable ==> usable
[    0.000000] e820: update [mem 0xc5d21018-0xc5d30257] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000006efff] usable
[    0.000000] reserve setup_data: [mem 0x000000000006f000-0x000000000006ffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000070000-0x0000000000087fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000000088000-0x00000000000bffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x00000000c5d21017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d21018-0x00000000c5d30257] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d30258-0x00000000c5d31017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d31018-0x00000000c5d3e057] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d3e058-0x00000000c5d3f017] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d3f018-0x00000000c5d4f057] usable
[    0.000000] reserve setup_data: [mem 0x00000000c5d4f058-0x00000000c6d5ffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000c6d60000-0x00000000c7d5ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000c7d60000-0x00000000cc36efff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cc36f000-0x00000000ccebefff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ccebf000-0x00000000ccfbefff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x00000000ccfbf000-0x00000000ccffefff] ACPI data
[    0.000000] reserve setup_data: [mem 0x00000000ccfff000-0x00000000ccffffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cd000000-0x00000000cf9fffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fe101000-0x00000000fe112fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000feb00000-0x00000000feb0ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000022f5fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by INSYDE Corp.
[    0.000000] efi:  ACPI=0xccffe000  ACPI 2.0=0xccffe014  SMBIOS=0xccebef98 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000001000) (0MB)
[    0.000000] efi: mem01: type=2, attr=0xf, range=[0x0000000000001000-0x0000000000004000) (0MB)
[    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000004000-0x000000000006f000) (0MB)
[    0.000000] efi: mem03: type=0, attr=0xf, range=[0x000000000006f000-0x0000000000070000) (0MB)
[    0.000000] efi: mem04: type=7, attr=0xf, range=[0x0000000000070000-0x0000000000088000) (0MB)
[    0.000000] efi: mem05: type=6, attr=0x800000000000000f, range=[0x0000000000088000-0x000000000009f000) (0MB)
[    0.000000] efi: mem06: type=0, attr=0xf, range=[0x000000000009f000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem07: type=7, attr=0xf, range=[0x0000000000100000-0x0000000001000000) (15MB)
[    0.000000] efi: mem08: type=2, attr=0xf, range=[0x0000000001000000-0x0000000002349000) (19MB)
[    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000002349000-0x000000003f074000) (973MB)
[    0.000000] efi: mem10: type=2, attr=0xf, range=[0x000000003f074000-0x0000000040000000) (15MB)
[    0.000000] efi: mem11: type=7, attr=0xf, range=[0x0000000040000000-0x00000000932a2000) (1330MB)
[    0.000000] efi: mem12: type=2, attr=0xf, range=[0x00000000932a2000-0x00000000c4d70000) (794MB)
[    0.000000] efi: mem13: type=4, attr=0xf, range=[0x00000000c4d70000-0x00000000c4d90000) (0MB)
[    0.000000] efi: mem14: type=7, attr=0xf, range=[0x00000000c4d90000-0x00000000c5d21000) (15MB)
[    0.000000] efi: mem15: type=2, attr=0xf, range=[0x00000000c5d21000-0x00000000c5e13000) (0MB)
[    0.000000] efi: mem16: type=7, attr=0xf, range=[0x00000000c5e13000-0x00000000c5e14000) (0MB)
[    0.000000] efi: mem17: type=2, attr=0xf, range=[0x00000000c5e14000-0x00000000c5e15000) (0MB)
[    0.000000] efi: mem18: type=7, attr=0xf, range=[0x00000000c5e15000-0x00000000c5e18000) (0MB)
[    0.000000] efi: mem19: type=2, attr=0xf, range=[0x00000000c5e18000-0x00000000c5e19000) (0MB)
[    0.000000] efi: mem20: type=7, attr=0xf, range=[0x00000000c5e19000-0x00000000c5e1a000) (0MB)
[    0.000000] efi: mem21: type=2, attr=0xf, range=[0x00000000c5e1a000-0x00000000c5e1d000) (0MB)
[    0.000000] efi: mem22: type=7, attr=0xf, range=[0x00000000c5e1d000-0x00000000c5e1f000) (0MB)
[    0.000000] efi: mem23: type=2, attr=0xf, range=[0x00000000c5e1f000-0x00000000c5ee1000) (0MB)
[    0.000000] efi: mem24: type=4, attr=0xf, range=[0x00000000c5ee1000-0x00000000c6d60000) (14MB)
[    0.000000] efi: mem25: type=0, attr=0xf, range=[0x00000000c6d60000-0x00000000c7d60000) (16MB)
[    0.000000] efi: mem26: type=7, attr=0xf, range=[0x00000000c7d60000-0x00000000c7d63000) (0MB)
[    0.000000] efi: mem27: type=2, attr=0xf, range=[0x00000000c7d63000-0x00000000c7d65000) (0MB)
[    0.000000] efi: mem28: type=7, attr=0xf, range=[0x00000000c7d65000-0x00000000c7d67000) (0MB)
[    0.000000] efi: mem29: type=2, attr=0xf, range=[0x00000000c7d67000-0x00000000c7d68000) (0MB)
[    0.000000] efi: mem30: type=7, attr=0xf, range=[0x00000000c7d68000-0x00000000c7d6b000) (0MB)
[    0.000000] efi: mem31: type=2, attr=0xf, range=[0x00000000c7d6b000-0x00000000c7d6c000) (0MB)
[    0.000000] efi: mem32: type=7, attr=0xf, range=[0x00000000c7d6c000-0x00000000c7d6d000) (0MB)
[    0.000000] efi: mem33: type=2, attr=0xf, range=[0x00000000c7d6d000-0x00000000c7d6f000) (0MB)
[    0.000000] efi: mem34: type=7, attr=0xf, range=[0x00000000c7d6f000-0x00000000c7e3b000) (0MB)
[    0.000000] efi: mem35: type=1, attr=0xf, range=[0x00000000c7e3b000-0x00000000c7f6f000) (1MB)
[    0.000000] efi: mem36: type=7, attr=0xf, range=[0x00000000c7f6f000-0x00000000c8c57000) (12MB)
[    0.000000] efi: mem37: type=4, attr=0xf, range=[0x00000000c8c57000-0x00000000c8c58000) (0MB)
[    0.000000] efi: mem38: type=7, attr=0xf, range=[0x00000000c8c58000-0x00000000c8d75000) (1MB)
[    0.000000] efi: mem39: type=4, attr=0xf, range=[0x00000000c8d75000-0x00000000c8d7f000) (0MB)
[    0.000000] efi: mem40: type=7, attr=0xf, range=[0x00000000c8d7f000-0x00000000c8da3000) (0MB)
[    0.000000] efi: mem41: type=4, attr=0xf, range=[0x00000000c8da3000-0x00000000c8dda000) (0MB)
[    0.000000] efi: mem42: type=7, attr=0xf, range=[0x00000000c8dda000-0x00000000c8ddb000) (0MB)
[    0.000000] efi: mem43: type=4, attr=0xf, range=[0x00000000c8ddb000-0x00000000c9c6d000) (14MB)
[    0.000000] efi: mem44: type=7, attr=0xf, range=[0x00000000c9c6d000-0x00000000c9c6e000) (0MB)
[    0.000000] efi: mem45: type=4, attr=0xf, range=[0x00000000c9c6e000-0x00000000c9e00000) (1MB)
[    0.000000] efi: mem46: type=3, attr=0xf, range=[0x00000000c9e00000-0x00000000c9e0d000) (0MB)
[    0.000000] efi: mem47: type=4, attr=0xf, range=[0x00000000c9e0d000-0x00000000c9e19000) (0MB)
[    0.000000] efi: mem48: type=3, attr=0xf, range=[0x00000000c9e19000-0x00000000c9e21000) (0MB)
[    0.000000] efi: mem49: type=4, attr=0xf, range=[0x00000000c9e21000-0x00000000c9e37000) (0MB)
[    0.000000] efi: mem50: type=7, attr=0xf, range=[0x00000000c9e37000-0x00000000c9e3a000) (0MB)
[    0.000000] efi: mem51: type=4, attr=0xf, range=[0x00000000c9e3a000-0x00000000c9e5a000) (0MB)
[    0.000000] efi: mem52: type=3, attr=0xf, range=[0x00000000c9e5a000-0x00000000c9ed5000) (0MB)
[    0.000000] efi: mem53: type=4, attr=0xf, range=[0x00000000c9ed5000-0x00000000c9ee8000) (0MB)
[    0.000000] efi: mem54: type=7, attr=0xf, range=[0x00000000c9ee8000-0x00000000c9ee9000) (0MB)
[    0.000000] efi: mem55: type=4, attr=0xf, range=[0x00000000c9ee9000-0x00000000c9ef5000) (0MB)
[    0.000000] efi: mem56: type=7, attr=0xf, range=[0x00000000c9ef5000-0x00000000c9ef6000) (0MB)
[    0.000000] efi: mem57: type=4, attr=0xf, range=[0x00000000c9ef6000-0x00000000cbf6f000) (32MB)
[    0.000000] efi: mem58: type=3, attr=0xf, range=[0x00000000cbf6f000-0x00000000cc36f000) (4MB)
[    0.000000] efi: mem59: type=5, attr=0x800000000000000f, range=[0x00000000cc36f000-0x00000000cc56f000) (2MB)
[    0.000000] efi: mem60: type=6, attr=0x800000000000000f, range=[0x00000000cc56f000-0x00000000ccabf000) (5MB)
[    0.000000] efi: mem61: type=0, attr=0xf, range=[0x00000000ccabf000-0x00000000ccebf000) (4MB)
[    0.000000] efi: mem62: type=10, attr=0xf, range=[0x00000000ccebf000-0x00000000ccfbf000) (1MB)
[    0.000000] efi: mem63: type=9, attr=0xf, range=[0x00000000ccfbf000-0x00000000ccfff000) (0MB)
[    0.000000] efi: mem64: type=4, attr=0xf, range=[0x00000000ccfff000-0x00000000cd000000) (0MB)
[    0.000000] efi: mem65: type=7, attr=0xf, range=[0x0000000100000000-0x000000022f600000) (4854MB)
[    0.000000] efi: mem66: type=0, attr=0x0, range=[0x00000000000a0000-0x00000000000c0000) (0MB)
[    0.000000] efi: mem67: type=0, attr=0x0, range=[0x00000000cd000000-0x00000000cfa00000) (42MB)
[    0.000000] efi: mem68: type=11, attr=0x8000000000000001, range=[0x00000000f8000000-0x00000000fc000000) (64MB)
[    0.000000] efi: mem69: type=0, attr=0x0, range=[0x00000000fe101000-0x00000000fe113000) (0MB)
[    0.000000] efi: mem70: type=11, attr=0x8000000000000001, range=[0x00000000feb00000-0x00000000feb10000) (0MB)
[    0.000000] efi: mem71: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem72: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed1c000) (0MB)
[    0.000000] efi: mem73: type=11, attr=0x8000000000000000, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem74: type=11, attr=0x8000000000000001, range=[0x00000000fed20000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem75: type=11, attr=0x8000000000000000, range=[0x00000000ffc00000-0x0000000100000000) (4MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Dell Inc. Latitude 3540/09HY4K, BIOS A04 11/12/2013
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x22f600 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-E7FFF write-protect
[    0.000000]   E8000-EFFFF write-combining
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7F80000000 write-back
[    0.000000]   1 base 0080000000 mask 7FC0000000 write-back
[    0.000000]   2 base 00C0000000 mask 7FF8000000 write-back
[    0.000000]   3 base 00C8000000 mask 7FFC000000 write-back
[    0.000000]   4 base 00CC000000 mask 7FFF000000 write-back
[    0.000000]   5 base 00FFC00000 mask 7FFFC00000 write-protect
[    0.000000]   6 base 0100000000 mask 7F00000000 write-back
[    0.000000]   7 base 0200000000 mask 7FC0000000 write-back
[    0.000000]   8 base 022F600000 mask 7FFFE00000 uncachable
[    0.000000]   9 base 022F800000 mask 7FFF800000 uncachable
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xcd000 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped: [mem 0x00000000-0x1fffffff]
[    0.000000] Base memory trampoline at [ffff880000082000] 82000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0xccffffff]
[    0.000000]  [mem 0x00000000-0xbfffffff] page 1G
[    0.000000]  [mem 0xc0000000-0xccffffff] page 2M
[    0.000000] kernel direct mapping tables up to 0xccffffff @ [mem 0x1fffe000-0x1fffffff]
[    0.000000] init_memory_mapping: [mem 0x100000000-0x22f5fffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 1G
[    0.000000]  [mem 0x200000000-0x22f5fffff] page 2M
[    0.000000] kernel direct mapping tables up to 0x22f5fffff @ [mem 0xc9e38000-0xc9e39fff]
[    0.000000] RAMDISK: [mem 0x3f074000-0x3fffafff]
[    0.000000] ACPI: RSDP 00000000ccffe014 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000ccffe210 000B4 (v01 DELL    CL09    00000001      01000013)
[    0.000000] ACPI: FACP 00000000ccff7000 0010C (v05 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI Error: Gpe0Block - 32-bit FADT register is too long (32 bytes, 256 bits) to convert to GAS struct - 255 bits max, truncating (20121018/tbfadt-201)
[    0.000000] ACPI BIOS Bug: Warning: 32/64X length mismatch in FADT/Gpe0Block: 256/255 (20121018/tbfadt-567)
[    0.000000] ACPI: DSDT 00000000ccfe8000 0B8A5 (v01 DELL    CL09    00000000 ASL  00040000)
[    0.000000] ACPI: FACS 00000000ccfb8000 00040
[    0.000000] ACPI: SLIC 00000000ccffd000 00176 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: UEFI 00000000ccffc000 00236 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: FPDT 00000000ccffa000 00044 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MSDM 00000000ccff9000 00055 (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASF! 00000000ccff8000 000A5 (v32 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: HPET 00000000ccff6000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: APIC 00000000ccff5000 0008C (v03 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: MCFG 00000000ccff4000 0003C (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000ccfe7000 006FE (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BOOT 00000000ccfe5000 00028 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: ASPT 00000000ccfe3000 00034 (v07 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: DBGP 00000000ccfe2000 00034 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: SSDT 00000000ccfdc000 00539 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000ccfdb000 00AD8 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000ccfd7000 03517 (v01 COMPAL CRV ORB  00003000 ACPI 00040000)
[    0.000000] ACPI: SSDT 00000000ccfd4000 01E3D (v01 COMPAL CRV ORB  00001000 ACPI 00040000)
[    0.000000] ACPI: BGRT 00000000ccfd6000 00038 (v01 DELL    CL09    00000001 ASL  00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000022f5fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x22f5fffff]
[    0.000000]   NODE_DATA [mem 0x22f5fb000-0x22f5fffff]
[    0.000000]  [ffffea0000000000-ffffea0008bfffff] PMD -> [ffff880226c00000-ffff88022ebfffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x22f5fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0006efff]
[    0.000000]   node   0: [mem 0x00070000-0x00087fff]
[    0.000000]   node   0: [mem 0x00100000-0xc6d5ffff]
[    0.000000]   node   0: [mem 0xc7d60000-0xcc36efff]
[    0.000000]   node   0: [mem 0xccfff000-0xccffffff]
[    0.000000]   node   0: [mem 0x100000000-0x22f5fffff]
[    0.000000] On node 0 totalpages: 2074855
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 6 pages reserved
[    0.000000]   DMA zone: 3889 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12942 pages used for memmap
[    0.000000]   DMA32 zone: 815330 pages, LIFO batch:31
[    0.000000]   Normal zone: 19416 pages used for memmap
[    0.000000]   Normal zone: 1223208 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-39
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] nr_irqs_gsi: 56
[    0.000000] PM: Registered nosave memory: 000000000006f000 - 0000000000070000
[    0.000000] PM: Registered nosave memory: 0000000000088000 - 00000000000c0000
[    0.000000] PM: Registered nosave memory: 00000000000c0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000c5d21000 - 00000000c5d22000
[    0.000000] PM: Registered nosave memory: 00000000c5d30000 - 00000000c5d31000
[    0.000000] PM: Registered nosave memory: 00000000c5d31000 - 00000000c5d32000
[    0.000000] PM: Registered nosave memory: 00000000c5d3e000 - 00000000c5d3f000
[    0.000000] PM: Registered nosave memory: 00000000c5d3f000 - 00000000c5d40000
[    0.000000] PM: Registered nosave memory: 00000000c5d4f000 - 00000000c5d50000
[    0.000000] PM: Registered nosave memory: 00000000c6d60000 - 00000000c7d60000
[    0.000000] PM: Registered nosave memory: 00000000cc36f000 - 00000000ccebf000
[    0.000000] PM: Registered nosave memory: 00000000ccebf000 - 00000000ccfbf000
[    0.000000] PM: Registered nosave memory: 00000000ccfbf000 - 00000000ccfff000
[    0.000000] PM: Registered nosave memory: 00000000cd000000 - 00000000cfa00000
[    0.000000] PM: Registered nosave memory: 00000000cfa00000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fe101000
[    0.000000] PM: Registered nosave memory: 00000000fe101000 - 00000000fe113000
[    0.000000] PM: Registered nosave memory: 00000000fe113000 - 00000000feb00000
[    0.000000] PM: Registered nosave memory: 00000000feb00000 - 00000000feb10000
[    0.000000] PM: Registered nosave memory: 00000000feb10000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fed00000
[    0.000000] PM: Registered nosave memory: 00000000fed00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000ffc00000
[    0.000000] PM: Registered nosave memory: 00000000ffc00000 - 0000000100000000
[    0.000000] e820: [mem 0xcfa00000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88022f200000 s84928 r8192 d21568 u262144
[    0.000000] pcpu-alloc: s84928 r8192 d21568 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2042427
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-36-generic.efi.signed root=UUID=bdb52052-ce62-4bc1-9385-0536a3a121e8 ro quiet splash nomodeset
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 7999388k/9164800k available (7175k kernel code, 865380k absent, 300032k reserved, 6068k data, 1016k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000] NR_IRQS:16640 nr_irqs:1016 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2394.446 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 4788.89 BogoMIPS (lpj=9577784)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.046632] Security Framework initialized
[    0.046643] AppArmor: AppArmor initialized
[    0.046644] Yama: becoming mindful.
[    0.047282] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.049034] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.049759] Mount-cache hash table entries: 256
[    0.049947] Initializing cgroup subsys cpuacct
[    0.049950] Initializing cgroup subsys memory
[    0.049957] Initializing cgroup subsys devices
[    0.049958] Initializing cgroup subsys freezer
[    0.049960] Initializing cgroup subsys blkio
[    0.049962] Initializing cgroup subsys perf_event
[    0.049964] Initializing cgroup subsys hugetlb
[    0.049992] CPU: Physical Processor ID: 0
[    0.049993] CPU: Processor Core ID: 0
[    0.049998] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.049998] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.051167] mce: CPU supports 7 MCE banks
[    0.051185] CPU0: Thermal monitoring enabled (TM1)
[    0.051195] process: using mwait in idle threads
[    0.051199] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.051199] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.051199] tlb_flushall_shift: 6
[    0.051359] Freeing SMP alternatives: 24k freed
[    0.053460] ACPI: Core revision 20121018
[    0.070263] ftrace: allocating 29401 entries in 115 pages
[    0.086793] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.126419] smpboot: CPU0: Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz (fam: 06, model: 45, stepping: 01)
[    0.126427] TSC deadline timer enabled
[    0.126430] Performance Events: no PEBS fmt2+, generic architected perfmon, Intel PMU driver.
[    0.126437] ... version:                3
[    0.126438] ... bit width:              48
[    0.126439] ... generic registers:      4
[    0.126440] ... value mask:             0000ffffffffffff
[    0.126441] ... max period:             000000007fffffff
[    0.126443] ... fixed-purpose events:   3
[    0.126444] ... event mask:             000000070000000f
[    0.142352] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.127745] smpboot: Booting Node   0, Processors  #1 #2 #3
[    0.171139] Brought up 4 CPUs
[    0.171143] smpboot: Total of 4 processors activated (19155.56 BogoMIPS)
[    0.177101] devtmpfs: initialized
[    0.178322] EVM: security.selinux
[    0.178324] EVM: security.SMACK64
[    0.178325] EVM: security.capability
[    0.178376] PM: Registering ACPI NVS region [mem 0xccebf000-0xccfbefff] (1048576 bytes)
[    0.179196] regulator-dummy: no parameters
[    0.179245] NET: Registered protocol family 16
[    0.179414] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.179416] ACPI: bus type pci registered
[    0.179484] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.179487] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.192490] PCI: Using configuration type 1 for base access
[    0.192642] dmi type 0xB1 record - unknown flag
[    0.193625] bio: create slab <bio-0> at 0
[    0.193712] ACPI: Added _OSI(Module Device)
[    0.193714] ACPI: Added _OSI(Processor Device)
[    0.193718] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.193719] ACPI: Added _OSI(Processor Aggregator Device)
[    0.196257] ACPI: EC: Look up EC in DSDT
[    0.198974] ACPI: Executed 1 blocks of module-level executable AML code
[    0.203117] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.204121] ACPI: SSDT 00000000cce7dc18 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.204759] ACPI: Dynamic OEM Table Load:
[    0.204762] ACPI: SSDT           (null) 003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20130117)
[    0.205117] ACPI: SSDT 00000000cce7d618 005AA (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.205847] ACPI: Dynamic OEM Table Load:
[    0.205850] ACPI: SSDT           (null) 005AA (v01  PmRef    ApIst 00003000 INTL 20130117)
[    0.206006] ACPI: SSDT 00000000cce7cd98 00119 (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.206643] ACPI: Dynamic OEM Table Load:
[    0.206645] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20130117)
[    0.324745] ACPI: Interpreter enabled
[    0.324749] ACPI: (supports S0 S3 S4 S5)
[    0.324783] ACPI: Using IOAPIC for interrupt routing
[    0.450111] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
[    0.450307] ACPI: No dock devices found.
[    0.450312] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.450464] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.450466] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.451042] PCI host bridge to bus 0000:00
[    0.451045] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.451048] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.451050] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.451052] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.451054] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.451056] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.451057] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.451059] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff]
[    0.451061] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.451063] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.451065] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.451067] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.451068] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.451070] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.451072] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.451074] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.451076] pci_bus 0000:00: root bus resource [mem 0x000f0000-0x000fffff]
[    0.451078] pci_bus 0000:00: root bus resource [mem 0xcfa00000-0xfeafffff]
[    0.451088] pci 0000:00:00.0: [8086:0a04] type 00 class 0x060000
[    0.451133] pci 0000:00:02.0: [8086:0a16] type 00 class 0x030000
[    0.451148] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf03fffff 64bit]
[    0.451156] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.451162] pci 0000:00:02.0: reg 20: [io  0x5000-0x503f]
[    0.451220] pci 0000:00:14.0: [8086:9c31] type 00 class 0x0c0330
[    0.451240] pci 0000:00:14.0: reg 10: [mem 0xf0800000-0xf080ffff 64bit]
[    0.451304] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.451325] pci 0000:00:16.0: [8086:9c3a] type 00 class 0x078000
[    0.451347] pci 0000:00:16.0: reg 10: [mem 0xf0814000-0xf081401f 64bit]
[    0.451421] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.451453] pci 0000:00:1b.0: [8086:9c20] type 00 class 0x040300
[    0.451468] pci 0000:00:1b.0: reg 10: [mem 0xf0810000-0xf0813fff 64bit]
[    0.451535] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.451555] pci 0000:00:1c.0: [8086:9c14] type 01 class 0x060400
[    0.451623] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.451648] pci 0000:00:1c.3: [8086:9c16] type 01 class 0x060400
[    0.451716] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.451738] pci 0000:00:1c.4: [8086:9c18] type 01 class 0x060400
[    0.451805] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.451835] pci 0000:00:1d.0: [8086:9c26] type 00 class 0x0c0320
[    0.452764] pci 0000:00:1d.0: reg 10: [mem 0xf0818000-0xf08183ff]
[    0.458225] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.458251] pci 0000:00:1f.0: [8086:9c43] type 00 class 0x060100
[    0.458386] pci 0000:00:1f.2: [8086:9c03] type 00 class 0x010601
[    0.458402] pci 0000:00:1f.2: reg 10: [io  0x5088-0x508f]
[    0.458410] pci 0000:00:1f.2: reg 14: [io  0x5094-0x5097]
[    0.458418] pci 0000:00:1f.2: reg 18: [io  0x5080-0x5087]
[    0.458426] pci 0000:00:1f.2: reg 1c: [io  0x5090-0x5093]
[    0.458434] pci 0000:00:1f.2: reg 20: [io  0x5060-0x507f]
[    0.458442] pci 0000:00:1f.2: reg 24: [mem 0xf0817000-0xf08177ff]
[    0.458481] pci 0000:00:1f.2: PME# supported from D3hot
[    0.458495] pci 0000:00:1f.3: [8086:9c22] type 00 class 0x0c0500
[    0.458511] pci 0000:00:1f.3: reg 10: [mem 0xf0815000-0xf08150ff 64bit]
[    0.458532] pci 0000:00:1f.3: reg 20: [io  0x5040-0x505f]
[    0.458613] pci 0000:01:00.0: [10ec:8168] type 00 class 0x020000
[    0.458631] pci 0000:01:00.0: reg 10: [io  0x4000-0x40ff]
[    0.458661] pci 0000:01:00.0: reg 18: [mem 0xf0700000-0xf0700fff 64bit]
[    0.458680] pci 0000:01:00.0: reg 20: [mem 0xf0400000-0xf0403fff 64bit pref]
[    0.458758] pci 0000:01:00.0: supports D1 D2
[    0.458760] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.464847] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.464851] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.464855] pci 0000:00:1c.0:   bridge window [mem 0xf0700000-0xf07fffff]
[    0.464861] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.464927] pci 0000:02:00.0: [168c:0036] type 00 class 0x028000
[    0.464960] pci 0000:02:00.0: reg 10: [mem 0xf0600000-0xf067ffff 64bit]
[    0.465038] pci 0000:02:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.465119] pci 0000:02:00.0: supports D1 D2
[    0.465121] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.472842] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.472847] pci 0000:00:1c.3:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.472910] pci 0000:03:00.0: [1002:6823] type 00 class 0x030000
[    0.472935] pci 0000:03:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.472955] pci 0000:03:00.0: reg 18: [mem 0xf0500000-0xf053ffff 64bit]
[    0.472968] pci 0000:03:00.0: reg 20: [io  0x3000-0x30ff]
[    0.472994] pci 0000:03:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.473071] pci 0000:03:00.0: supports D1 D2
[    0.473073] pci 0000:03:00.0: PME# supported from D1 D2 D3hot
[    0.480829] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.480833] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.480836] pci 0000:00:1c.4:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.480842] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.480905] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.480958] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.481007] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.481181]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.481585]  pci0000:00: ACPI _OSC control (0x1d) granted
[    0.482971] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483017] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483060] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483105] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483147] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483192] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483236] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483278] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.483375] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.483381] vgaarb: device added: PCI:0000:03:00.0,decodes=io+mem,owns=none,locks=none
[    0.483383] vgaarb: loaded
[    0.483384] vgaarb: bridge control possible 0000:03:00.0
[    0.483385] vgaarb: no bridge control possible 0000:00:02.0
[    0.483550] SCSI subsystem initialized
[    0.483553] ACPI: bus type scsi registered
[    0.483592] libata version 3.00 loaded.
[    0.483613] ACPI: bus type usb registered
[    0.483631] usbcore: registered new interface driver usbfs
[    0.483639] usbcore: registered new interface driver hub
[    0.483666] usbcore: registered new device driver usb
[    0.483752] PCI: Using ACPI for IRQ routing
[    0.485204] PCI: pci_cache_line_size set to 64 bytes
[    0.485257] e820: reserve RAM buffer [mem 0x0006f000-0x0006ffff]
[    0.485258] e820: reserve RAM buffer [mem 0x00088000-0x0008ffff]
[    0.485260] e820: reserve RAM buffer [mem 0xc5d21018-0xc7ffffff]
[    0.485262] e820: reserve RAM buffer [mem 0xc5d31018-0xc7ffffff]
[    0.485264] e820: reserve RAM buffer [mem 0xc5d3f018-0xc7ffffff]
[    0.485266] e820: reserve RAM buffer [mem 0xc6d60000-0xc7ffffff]
[    0.485268] e820: reserve RAM buffer [mem 0xcc36f000-0xcfffffff]
[    0.485270] e820: reserve RAM buffer [mem 0xcd000000-0xcfffffff]
[    0.485272] e820: reserve RAM buffer [mem 0x22f600000-0x22fffffff]
[    0.485354] NetLabel: Initializing
[    0.485355] NetLabel:  domain hash size = 128
[    0.485356] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.485366] NetLabel:  unlabeled traffic allowed by default
[    0.485419] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.485426] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.487432] Switching to clocksource hpet
[    0.492724] AppArmor: AppArmor Filesystem Enabled
[    0.492746] pnp: PnP ACPI init
[    0.492757] ACPI: bus type pnp registered
[    0.492792] pnp 00:00: [dma 4]
[    0.492813] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.492832] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.492950] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.492992] system 00:03: [io  0x0680-0x069f] has been reserved
[    0.492994] system 00:03: [io  0xfd60-0xfd63] has been reserved
[    0.492996] system 00:03: [io  0xffff] has been reserved
[    0.492998] system 00:03: [io  0xffff] has been reserved
[    0.493000] system 00:03: [io  0xffff] has been reserved
[    0.493003] system 00:03: [io  0x1800-0x18fe] has been reserved
[    0.493005] system 00:03: [io  0x164e-0x164f] has been reserved
[    0.493007] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.493054] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.493097] system 00:05: [io  0x1854-0x1857] has been reserved
[    0.493100] system 00:05: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.493149] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.493177] pnp 00:07: Plug and Play ACPI device, IDs DLL0609 PNP0f13 (active)
[    0.551515] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.551518] system 00:08: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.551521] system 00:08: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.551523] system 00:08: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.551525] system 00:08: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.551527] system 00:08: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.551529] system 00:08: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.551532] system 00:08: [mem 0xff000000-0xff000fff] has been reserved
[    0.551534] system 00:08: [mem 0xff010000-0xffffffff] could not be reserved
[    0.551536] system 00:08: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.551538] system 00:08: [mem 0xcfa22000-0xcfa22fff] has been reserved
[    0.551541] system 00:08: [mem 0xcfa10000-0xcfa1ffff] has been reserved
[    0.551543] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.552150] pnp: PnP ACPI: found 9 devices
[    0.552151] ACPI: ACPI bus type pnp unregistered
[    0.558200] pci 0000:02:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.558203] pci 0000:03:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.558236] pci 0000:00:1c.3: BAR 15: assigned [mem 0xcfb00000-0xcfbfffff pref]
[    0.558239] pci 0000:00:1c.0: PCI bridge to [bus 01]
[    0.558242] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.558247] pci 0000:00:1c.0:   bridge window [mem 0xf0700000-0xf07fffff]
[    0.558252] pci 0000:00:1c.0:   bridge window [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.558258] pci 0000:02:00.0: BAR 6: assigned [mem 0xcfb00000-0xcfb0ffff pref]
[    0.558261] pci 0000:00:1c.3: PCI bridge to [bus 02]
[    0.558266] pci 0000:00:1c.3:   bridge window [mem 0xf0600000-0xf06fffff]
[    0.558269] pci 0000:00:1c.3:   bridge window [mem 0xcfb00000-0xcfbfffff pref]
[    0.558276] pci 0000:03:00.0: BAR 6: assigned [mem 0xf0540000-0xf055ffff pref]
[    0.558278] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.558281] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.558285] pci 0000:00:1c.4:   bridge window [mem 0xf0500000-0xf05fffff]
[    0.558289] pci 0000:00:1c.4:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.558320] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.558322] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.558324] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.558326] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.558328] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.558330] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.558332] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.558333] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
[    0.558335] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
[    0.558337] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
[    0.558339] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
[    0.558341] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
[    0.558343] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
[    0.558345] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
[    0.558347] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
[    0.558349] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
[    0.558351] pci_bus 0000:00: resource 20 [mem 0xcfa00000-0xfeafffff]
[    0.558353] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.558355] pci_bus 0000:01: resource 1 [mem 0xf0700000-0xf07fffff]
[    0.558357] pci_bus 0000:01: resource 2 [mem 0xf0400000-0xf04fffff 64bit pref]
[    0.558359] pci_bus 0000:02: resource 1 [mem 0xf0600000-0xf06fffff]
[    0.558361] pci_bus 0000:02: resource 2 [mem 0xcfb00000-0xcfbfffff pref]
[    0.558363] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.558365] pci_bus 0000:03: resource 1 [mem 0xf0500000-0xf05fffff]
[    0.558366] pci_bus 0000:03: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.558398] NET: Registered protocol family 2
[    0.558591] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.558798] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.558929] TCP: Hash tables configured (established 65536 bind 65536)
[    0.558947] TCP: reno registered
[    0.558961] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.558993] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.559062] NET: Registered protocol family 1
[    0.559073] pci 0000:00:02.0: Boot video device
[    0.575353] PCI: CLS 64 bytes, default 64
[    0.575390] Trying to unpack rootfs image as initramfs...
[    0.900437] Freeing initrd memory: 15900k freed
[    0.902592] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.902597] software IO TLB [mem 0xc0d70000-0xc4d70000] (64MB) mapped at [ffff8800c0d70000-ffff8800c4d6ffff]
[    0.902634] Simple Boot Flag at 0x44 set to 0x1
[    0.902969] Initialise module verification
[    0.903012] audit: initializing netlink socket (disabled)
[    0.903021] type=2000 audit(1392770901.876:1): initialized
[    0.942555] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.944070] VFS: Disk quotas dquot_6.5.2
[    0.944110] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.944546] fuse init (API version 7.20)
[    0.944610] msgmni has been set to 15791
[    0.944958] Key type asymmetric registered
[    0.944961] Asymmetric key parser 'x509' registered
[    0.944991] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.945014] io scheduler noop registered
[    0.945016] io scheduler deadline registered (default)
[    0.945022] io scheduler cfq registered
[    0.945141] pcieport 0000:00:1c.0: irq 56 for MSI/MSI-X
[    0.945234] pcieport 0000:00:1c.3: irq 57 for MSI/MSI-X
[    0.945318] pcieport 0000:00:1c.4: irq 58 for MSI/MSI-X
[    0.945390] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
[    0.945392] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
[    0.945396] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
[    0.945411] pcieport 0000:00:1c.3: Signaling PME through PCIe PME interrupt
[    0.945413] pci 0000:02:00.0: Signaling PME through PCIe PME interrupt
[    0.945417] pcie_pme 0000:00:1c.3:pcie01: service driver pcie_pme loaded
[    0.945432] pcieport 0000:00:1c.4: Signaling PME through PCIe PME interrupt
[    0.945434] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
[    0.945437] pcie_pme 0000:00:1c.4:pcie01: service driver pcie_pme loaded
[    0.945448] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.945462] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.945512] efifb: probing for efifb
[    0.947340] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90009500000, using 8100k, total 8100k
[    0.947342] efifb: mode is 1920x1080x32, linelength=7680, pages=1
[    0.947343] efifb: scrolling: redraw
[    0.947345] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.952700] Console: switching to colour frame buffer device 240x67
[    0.957970] fb0: EFI VGA frame buffer device
[    0.957976] intel_idle: MWAIT substates: 0x11142120
[    0.957977] intel_idle: v0.4 model 0x45
[    0.957978] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.957980] intel_idle: unaware of model 0x45 MWAIT 5 please contact lenb@kernel.org
[    0.957981] intel_idle: unaware of model 0x45 MWAIT 6 please contact lenb@kernel.org
[    0.957982] intel_idle: unaware of model 0x45 MWAIT 7 please contact lenb@kernel.org
[    0.958073] ACPI: AC Adapter [ACAD] (on-line)
[    0.958179] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0D:00/input/input0
[    0.958209] ACPI: Lid Switch [LID0]
[    0.958240] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input1
[    0.958244] ACPI: Power Button [PWRB]
[    0.958283] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.958286] ACPI: Power Button [PWRF]
[    0.958362] ACPI: Requesting acpi_cpufreq
[    1.081041] GHES: HEST is not enabled!
[    1.081115] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.138471] ACPI: Battery Slot [BAT1] (battery absent)
[    1.138582] Linux agpgart interface v0.103
[    1.139668] brd: module loaded
[    1.140244] loop: module loaded
[    1.140535] libphy: Fixed MDIO Bus: probed
[    1.140591] tun: Universal TUN/TAP device driver, 1.6
[    1.140593] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.140625] PPP generic driver version 2.4.2
[    1.140664] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.140665] ehci-pci: EHCI PCI platform driver
[    1.140705] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.140708] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.140714] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.140726] ehci-pci 0000:00:1d.0: debug port 2
[    1.144614] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.144629] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf0818000
[    1.154441] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.154462] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.154464] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.154466] usb usb1: Product: EHCI Host Controller
[    1.154468] usb usb1: Manufacturer: Linux 3.8.0-36-generic ehci_hcd
[    1.154470] usb usb1: SerialNumber: 0000:00:1d.0
[    1.154567] hub 1-0:1.0: USB hub found
[    1.154570] hub 1-0:1.0: 2 ports detected
[    1.154671] ehci-platform: EHCI generic platform driver
[    1.154678] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.154692] uhci_hcd: USB Universal Host Controller Interface driver
[    1.154742] xhci_hcd 0000:00:14.0: setting latency timer to 64
[    1.154744] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.154749] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    1.154824] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    1.154860] xhci_hcd 0000:00:14.0: irq 59 for MSI/MSI-X
[    1.154901] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.154903] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.154905] usb usb2: Product: xHCI Host Controller
[    1.154907] usb usb2: Manufacturer: Linux 3.8.0-36-generic xhci_hcd
[    1.154909] usb usb2: SerialNumber: 0000:00:14.0
[    1.154972] xHCI xhci_add_endpoint called for root hub
[    1.154974] xHCI xhci_check_bandwidth called for root hub
[    1.154991] hub 2-0:1.0: USB hub found
[    1.155001] hub 2-0:1.0: 9 ports detected
[    1.156341] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    1.156345] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    1.156364] usb usb3: New USB device found, idVendor=1d6b, idProduct=0003
[    1.156366] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.156368] usb usb3: Product: xHCI Host Controller
[    1.156370] usb usb3: Manufacturer: Linux 3.8.0-36-generic xhci_hcd
[    1.156371] usb usb3: SerialNumber: 0000:00:14.0
[    1.156429] xHCI xhci_add_endpoint called for root hub
[    1.156430] xHCI xhci_check_bandwidth called for root hub
[    1.156448] hub 3-0:1.0: USB hub found
[    1.156454] hub 3-0:1.0: 4 ports detected
[    1.157060] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.183073] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.183080] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.183207] mousedev: PS/2 mouse device common for all mice
[    1.185605] rtc_cmos 00:04: RTC can wake from S4
[    1.185721] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.185748] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.185831] device-mapper: uevent: version 1.0.3
[    1.185881] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    1.185955] cpuidle: using governor ladder
[    1.186053] cpuidle: using governor menu
[    1.186058] ledtrig-cpu: registered to indicate activity on CPUs
[    1.186060] EFI Variables Facility v0.08 2004-May-17
[    1.214869] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.465973] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.525589] ashmem: initialized
[    1.525714] TCP: cubic registered
[    1.525804] NET: Registered protocol family 10
[    1.525970] NET: Registered protocol family 17
[    1.525979] Key type dns_resolver registered
[    1.526198] Loading module verification certificates
[    1.527162] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 65309af67f6c263a4d5f1db346570b5bfb944cad'
[    1.527172] registered taskstats version 1
[    1.529272] Key type trusted registered
[    1.531024] Key type encrypted registered
[    1.533111] rtc_cmos 00:04: setting system clock to 2014-02-19 00:48:22 UTC (1392770902)
[    1.534076] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.534078] EDD information not available.
[    1.535850] Freeing unused kernel memory: 1016k freed
[    1.535972] Write protecting the kernel read-only data: 12288k
[    1.539193] Freeing unused kernel memory: 1004k freed
[    1.542264] Freeing unused kernel memory: 952k freed
[    1.557681] udevd[107]: starting version 175
[    1.585520] Disabling lock debugging due to kernel taint
[    1.586277] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.591248] ahci 0000:00:1f.2: version 3.0
[    1.591299] ahci 0000:00:1f.2: irq 60 for MSI/MSI-X
[    1.594268] r8169 0000:01:00.0: irq 61 for MSI/MSI-X
[    1.594508] r8169 0000:01:00.0 eth0: RTL8168g/8111g at 0xffffc9000003c000, a4:1f:72:f7:a5:90, XID 0c000800 IRQ 61
[    1.594513] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.598107] usb 1-1: New USB device found, idVendor=8087, idProduct=8000
[    1.598113] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.598394] hub 1-1:1.0: USB hub found
[    1.598477] hub 1-1:1.0: 8 ports detected
[    1.605765] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 3 ports 6 Gbps 0x3 impl SATA mode
[    1.605772] ahci 0000:00:1f.2: flags: 64bit ncq led clo only pio slum part deso sadm sds apst 
[    1.605779] ahci 0000:00:1f.2: setting latency timer to 64
[    1.606112] scsi0 : ahci
[    1.606183] scsi1 : ahci
[    1.606237] scsi2 : ahci
[    1.606285] ata1: SATA max UDMA/133 abar m2048@0xf0817000 port 0xf0817100 irq 60
[    1.606287] ata2: SATA max UDMA/133 abar m2048@0xf0817000 port 0xf0817180 irq 60
[    1.606289] ata3: DUMMY
[    1.869483] usb 1-1.3: new low-speed USB device number 3 using ehci-pci
[    1.897346] tsc: Refined TSC clocksource calibration: 2394.457 MHz
[    1.897352] Switching to clocksource tsc
[    1.925311] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.925332] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.926117] ata1.00: ATA-9: WDC WD7500BPVX-75JC3T0, 01.01A01, max UDMA/133
[    1.926122] ata1.00: 1465149168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.926970] ata1.00: configured for UDMA/133
[    1.927202] scsi 0:0:0:0: Direct-Access     ATA      WDC WD7500BPVX-7 01.0 PQ: 0 ANSI: 5
[    1.927402] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.927408] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.927413] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.927478] sd 0:0:0:0: [sda] Write Protect is off
[    1.927482] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.927511] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.930801] ata2.00: ATAPI: PLDS DVD+/-RW DU-8A5HH, SD12, max UDMA/100
[    1.931476] ata2.00: configured for UDMA/100
[    1.933281] scsi 1:0:0:0: CD-ROM            PLDS     DVD+-RW DU-8A5HH SD12 PQ: 0 ANSI: 5
[    1.935999] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.936002] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.936107] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.936180] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.965341] usb 1-1.3: New USB device found, idVendor=15d9, idProduct=0a4e
[    1.965345] usb 1-1.3: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[    1.965347] usb 1-1.3: Product:  USB OPTICAL MOUSE
[    1.970087] usbcore: registered new interface driver usbhid
[    1.970090] usbhid: USB HID core driver
[    1.971729] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input4
[    1.971846] hid-generic 0003:15D9:0A4E.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.3/input0
[    2.025423]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7 sda8
[    2.026517] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.037187] usb 1-1.5: new full-speed USB device number 4 using ehci-pci
[    2.130307] usb 1-1.5: New USB device found, idVendor=0cf3, idProduct=0036
[    2.130312] usb 1-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.200926] usb 1-1.7: new high-speed USB device number 5 using ehci-pci
[    2.293576] usb 1-1.7: New USB device found, idVendor=0bda, idProduct=0129
[    2.293581] usb 1-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.293583] usb 1-1.7: Product: USB2.0-CRW
[    2.293585] usb 1-1.7: Manufacturer: Generic
[    2.293586] usb 1-1.7: SerialNumber: 20100201396000000
[    2.364715] usb 1-1.8: new high-speed USB device number 6 using ehci-pci
[    2.521434] usb 1-1.8: New USB device found, idVendor=0c45, idProduct=64ad
[    2.521438] usb 1-1.8: New USB device strings: Mfr=2, Product=1, SerialNumber=0
[    2.521441] usb 1-1.8: Product: Laptop_Integrated_Webcam_HD
[    2.521443] usb 1-1.8: Manufacturer: CN0Y3PX8724873C3A06XA01
[    3.776297] EXT4-fs (sda8): INFO: recovery required on readonly filesystem
[    3.776301] EXT4-fs (sda8): write access will be enabled during recovery
[    4.501563] EXT4-fs (sda8): recovery complete
[    4.510169] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[    5.533034] init: ureadahead main process (298) terminated with status 5
[    6.998457] Adding 9764860k swap on /dev/sda7.  Priority:-1 extents:1 across:9764860k 
[    7.861358] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.996149] udevd[376]: starting version 175
[    8.952415] lp: driver loaded but no devices found
[    9.291087] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20121018/utaddress-251)
[    9.291097] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.291103] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPRL 1 (20121018/utaddress-251)
[    9.291108] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPR_ 2 (20121018/utaddress-251)
[    9.291113] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.291115] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPRL 1 (20121018/utaddress-251)
[    9.291120] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPR_ 2 (20121018/utaddress-251)
[    9.291124] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \IO_D 3 (20121018/utaddress-251)
[    9.291129] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    9.291131] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    9.386830] wmi: Mapper loaded
[    9.393192] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[    9.393196] AMD IOMMUv2 functionality not available on this system
[    9.463476] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    9.479438] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x17
[    9.562630] Bluetooth: Core ver 2.16
[    9.562652] NET: Registered protocol family 31
[    9.562654] Bluetooth: HCI device and connection manager initialized
[    9.562662] Bluetooth: HCI socket layer initialized
[    9.562665] Bluetooth: L2CAP socket layer initialized
[    9.562672] Bluetooth: SCO socket layer initialized
[    9.604540] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x17
[    9.605819] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x17
[    9.607138] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x17
[    9.608371] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.896761] [drm] Initialized drm 1.1.0 20060810
[    9.906096] cfg80211: Calling CRDA to update world regulatory domain
[    9.945750] usbcore: registered new interface driver btusb
[    9.992078] input: Dell WMI hotkeys as /devices/virtual/input/input5
[   10.110499] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   10.114941] scsi3 : SCSI emulation for RTS5139 USB card reader
[   10.115099] scsi 3:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   10.115161] usbcore: registered new interface driver rts5139
[   10.115705] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   10.118674] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   10.327719] Linux video capture interface: v2.00
[   10.440784] snd_hda_intel 0000:00:1b.0: irq 62 for MSI/MSI-X
[   10.615401] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   10.649861] ath: EEPROM regdomain: 0x60
[   10.649864] ath: EEPROM indicates we should expect a direct regpair map
[   10.649867] ath: Country alpha2 being used: 00
[   10.649868] ath: Regpair used: 0x60
[   10.664128] [drm:drm_pci_agp_init] *ERROR* Cannot initialize the agpgart module.
[   10.664166] DRM: Fill_in_dev failed.
[   10.807563] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   10.813852] mei 0000:00:16.0: setting latency timer to 64
[   10.813915] mei 0000:00:16.0: irq 63 for MSI/MSI-X
[   10.816151] <6>[fglrx] Maximum main memory to use for locked dma buffers: 7667 MBytes.
[   10.816361] <6>[fglrx]   vendor: 1002 device: 6823 count: 1
[   10.816625] <6>[fglrx] ioport: bar 4, base 0x3000, size: 0x100
[   10.816632] pci 0000:03:00.0: enabling device (0000 -> 0003)
[   10.816722] <6>[fglrx] Kernel PAT support is enabled
[   10.816738] <6>[fglrx] module loaded - fglrx 13.30.1 [Jan  8 2014] with 1 minors
[   10.821724] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_HD (0c45:64ad)
[   10.851584] usbcore: registered new interface driver ath3k
[   10.859033] usb 1-1.5: USB disconnect, device number 4
[   10.862201] input: Laptop_Integrated_Webcam_HD as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.8/1-1.8:1.0/input/input7
[   10.862390] usbcore: registered new interface driver uvcvideo
[   10.862393] USB Video Class driver (1.1.1)
[   10.919746] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.920035] ieee80211 phy0: Atheros AR9565 Rev:1 mem=0xffffc9000aa00000, irq=19
[   11.041752] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00, board id: 2382, fw id: 1238635
[   11.059355] usb 1-1.5: new full-speed USB device number 7 using ehci-pci
[   11.140285] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[   11.152478] usb 1-1.5: New USB device found, idVendor=0cf3, idProduct=0036
[   11.152482] usb 1-1.5: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   12.461157] EXT4-fs (sda8): re-mounted. Opts: errors=remount-ro
[   13.117185] type=1400 audit(1392770914.098:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=759 comm="apparmor_parser"
[   13.117270] type=1400 audit(1392770914.098:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=789 comm="apparmor_parser"
[   13.117280] type=1400 audit(1392770914.098:4): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=739 comm="apparmor_parser"
[   13.117528] type=1400 audit(1392770914.098:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=759 comm="apparmor_parser"
[   13.117720] type=1400 audit(1392770914.098:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=759 comm="apparmor_parser"
[   13.117795] type=1400 audit(1392770914.098:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=789 comm="apparmor_parser"
[   13.117802] type=1400 audit(1392770914.098:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=739 comm="apparmor_parser"
[   13.118093] type=1400 audit(1392770914.098:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=789 comm="apparmor_parser"
[   13.118099] type=1400 audit(1392770914.098:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=739 comm="apparmor_parser"
[   14.924581] init: failsafe main process (932) killed by TERM signal
[   16.038736] type=1400 audit(1392770917.022:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=991 comm="apparmor_parser"
[   17.131461] ppdev: user-space parallel port driver
[   17.800929] mei 0000:00:16.0: init hw failure.
[   17.801014] mei 0000:00:16.0: initialization failed.
[   18.439019] Bluetooth: RFCOMM TTY layer initialized
[   18.439031] Bluetooth: RFCOMM socket layer initialized
[   18.439033] Bluetooth: RFCOMM ver 1.11
[   18.650994] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.650999] Bluetooth: BNEP filters: protocol multicast
[   18.651014] Bluetooth: BNEP socket layer initialized
[   21.001546] r8169 0000:01:00.0 eth0: link down
[   21.001589] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.001866] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.014706] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.017795] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.272696] fglrx_pci 0000:03:00.0: irq 63 for MSI/MSI-X
[   22.273350] <6>[fglrx] Firegl kernel thread PID: 1343
[   22.273451] <6>[fglrx] Firegl kernel thread PID: 1344
[   22.273529] <6>[fglrx] Firegl kernel thread PID: 1345
[   22.273630] <6>[fglrx] IRQ 63 Enabled
[   22.287031] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   22.287034] <6>[fglrx] Reserved FB block: Unshared offset:f878000, size:4000 
[   22.287035] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   22.287037] <6>[fglrx] Reserved FB block: Unshared offset:7fff4000, size:c000 
[   22.639595] init: lightdm main process (1285) terminated with status 1
[   23.840761] wlan0: authenticate with bc:f6:85:e2:fb:d6
[   23.848217] wlan0: send auth to bc:f6:85:e2:fb:d6 (try 1/3)
[   23.850178] wlan0: authenticated
[   23.851686] wlan0: associate with bc:f6:85:e2:fb:d6 (try 1/3)
[   23.855099] wlan0: RX AssocResp from bc:f6:85:e2:fb:d6 (capab=0x411 status=0 aid=2)
[   23.855137] wlan0: associated
[   23.855146] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   37.718896] init: failsafe-x main process (1349) terminated with status 1
```

Finally a sample of what I get when GUI is already loaded:
```
[   23.028572] fglrx_pci 0000:03:00.0: irq 64 for MSI/MSI-X
[   23.029004] <6>[fglrx] Firegl kernel thread PID: 1352
[   23.029065] <6>[fglrx] Firegl kernel thread PID: 1353
[   23.029120] <6>[fglrx] Firegl kernel thread PID: 1354
[   23.029214] <6>[fglrx] IRQ 64 Enabled
[   23.040003] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   23.040005] <6>[fglrx] Reserved FB block: Unshared offset:f878000, size:4000 
[   23.040007] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
[   23.040008] <6>[fglrx] Reserved FB block: Unshared offset:7fff4000, size:c000 
[   24.821789] [drm:intel_dp_set_link_train] *ERROR* Timed out waiting for DP idle patterns
[   24.821795] [drm:i915_write32] *ERROR* Unknown unclaimed register before writing to 64040
[   84.223838] wlan0: authenticate with 00:1c:f0:89:b3:d7
[   84.227426] wlan0: send auth to 00:1c:f0:89:b3:d7 (try 1/3)
[   84.229428] wlan0: authenticated
[   84.230776] wlan0: associate with 00:1c:f0:89:b3:d7 (try 1/3)
[   84.233390] wlan0: RX AssocResp from 00:1c:f0:89:b3:d7 (capab=0x421 status=0 aid=85)
[   84.233849] wlan0: associated
[   84.233864] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  299.381000] mce: [Hardware Error]: Machine check events logged
[  901.211663] type=1400 audit(1392665665.547:31): apparmor="DENIED" operation="capable" parent=1 profile="/usr/sbin/cupsd" pid=1094 comm="cupsd" pid=1094 comm="cupsd" capability=36  capname="block_suspend"
[ 1110.691873] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
[ 1300.043412] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
[ 1885.177378] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
[ 5249.225545] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
[ 5269.821669] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
[ 5269.932188] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
[ 5308.301247] wlan0: authenticate with 00:19:5b:ee:0e:b4
[ 5308.305842] wlan0: direct probe to 00:19:5b:ee:0e:b4 (try 1/3)
[ 5308.305922] cfg80211: Calling CRDA for country: US
[ 5308.577271] wlan0: send auth to 00:19:5b:ee:0e:b4 (try 2/3)
[ 5308.579330] wlan0: authenticated
[ 5313.301906] wlan0: deauthenticating from 00:1c:f0:89:b3:d7 by local choice (reason=3)
[ 5313.681777] wlan0: authenticate with 00:1f:c9:fd:99:c0
[ 5313.689784] wlan0: direct probe to 00:1f:c9:fd:99:c0 (try 1/3)
[ 5313.892616] wlan0: direct probe to 00:1f:c9:fd:99:c0 (try 2/3)
[ 5314.096200] wlan0: send auth to 00:1f:c9:fd:99:c0 (try 3/3)
[ 5314.105413] wlan0: authenticated
[ 5314.108210] wlan0: associate with 00:1f:c9:fd:99:c0 (try 1/3)
[ 5314.113406] wlan0: RX AssocResp from 00:1f:c9:fd:99:c0 (capab=0x421 status=0 aid=3)
[ 5314.113866] wlan0: associated
[ 5314.327889] wlan0: deauthenticated from 00:1f:c9:fd:99:c0 (Reason: 2)
[ 5314.328439] cfg80211: Calling CRDA to update world regulatory domain
[ 5314.552466] wlan0: authenticate with 00:1c:f0:89:b3:dd
[ 5314.560765] wlan0: send auth to 00:1c:f0:89:b3:dd (try 1/3)
[ 5314.562732] wlan0: authenticated
[ 5314.563527] wlan0: associate with 00:1c:f0:89:b3:dd (try 1/3)
[ 5314.566199] wlan0: RX AssocResp from 00:1c:f0:89:b3:dd (capab=0x421 status=0 aid=132)
[ 5314.566647] wlan0: associated
[ 5321.783633] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
[ 5357.571183] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
[ 5358.331017] <3>[fglrx:KAS_Mutex_Release] *ERROR* Mutex released without holding it.
```

I'm sorry for posting this much code... it's just that I don't know what's important for the debugging.
Again, many thanks.

---

