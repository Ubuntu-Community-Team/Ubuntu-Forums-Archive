---
title: "Kernel panic"
date: 2014-05-30
forum: New to Ubuntu
---

### Post by viye3106 on 2014-05-30
Hi, 

Absolute linux noob here. I recently replaced Windows 8 with Ubuntu 14.04 on my laptop (Asus rog g750jw). It has been giving me this weird problem since yesterday: it just hangs up randomly, the screen freezes, the caps lock and num lock indicators go crazy and blink as if the laptop is having some sort of seizure. I don't find linux exactly beginner friendly,so I would really appreciate some help here. Thanks :)

---

### Post by mikewhatever on 2014-05-31
According to the symptoms, it's probably [kernel panic]('https://en.wikipedia.org/wiki/Kernel_panic'). In case you want someone to try and help, provide info on what causes it, and when it happans, hardware specs, logs, such as /var/log/dmesg.

---

### Post by q64ceo on 2014-05-31
Most likely it is a kernel panic

However one should not rule out overheating as a possible cause

---

### Post by viye3106 on 2014-06-01
The hang up happens randomly - it has no particular occasion. Last time, it happened while I was watching a youtube video on firefox and before that it happened while I was working with MATLAB. I am not sure what exactly causes it.

Here is the content of /var/log/dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-27-generic (buildd@akateko) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 (Ubuntu 3.13.0-27.50-generic 3.13.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic.efi.signed root=UUID=98252a17-dd23-4bd9-a2b4-3b00dd3f0fb8 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000004bb37fff] usable
[    0.000000] BIOS-e820: [mem 0x000000004bb38000-0x000000004bb3efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000004bb3f000-0x000000004c3a5fff] usable
[    0.000000] BIOS-e820: [mem 0x000000004c3a6000-0x000000004c628fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000004c629000-0x000000005b91dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000005b91e000-0x000000005bb23fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000005bb24000-0x000000005be6efff] usable
[    0.000000] BIOS-e820: [mem 0x000000005be6f000-0x000000005cb47fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000005cb48000-0x000000005cf4afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000005cf4b000-0x000000005cffefff] type 20
[    0.000000] BIOS-e820: [mem 0x000000005cfff000-0x000000005cffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000049f3fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI 2.0=0x5cb12000  ACPI=0x5cb12000  SMBIOS=0xf04c0  MPS=0xfd590
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x0000000000058000) (0MB)
[    0.000000] efi: mem02: type=0, attr=0xf, range=[0x0000000000058000-0x0000000000059000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000059000-0x000000000005f000) (0MB)
[    0.000000] efi: mem04: type=4, attr=0xf, range=[0x000000000005f000-0x0000000000060000) (0MB)
[    0.000000] efi: mem05: type=3, attr=0xf, range=[0x0000000000060000-0x000000000009f000) (0MB)
[    0.000000] efi: mem06: type=6, attr=0x800000000000000f, range=[0x000000000009f000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem07: type=2, attr=0xf, range=[0x0000000000100000-0x0000000001500000) (20MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x0000000001500000-0x0000000002000000) (11MB)
[    0.000000] efi: mem09: type=2, attr=0xf, range=[0x0000000002000000-0x0000000003400000) (20MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000003400000-0x00000000348bf000) (788MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x00000000348bf000-0x0000000048748000) (318MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x0000000048748000-0x000000004b830000) (48MB)
[    0.000000] efi: mem13: type=2, attr=0xf, range=[0x000000004b830000-0x000000004ba04000) (1MB)
[    0.000000] efi: mem14: type=1, attr=0xf, range=[0x000000004ba04000-0x000000004bb38000) (1MB)
[    0.000000] efi: mem15: type=10, attr=0xf, range=[0x000000004bb38000-0x000000004bb3f000) (0MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x000000004bb3f000-0x000000004bc92000) (1MB)
[    0.000000] efi: mem17: type=3, attr=0xf, range=[0x000000004bc92000-0x000000004c367000) (6MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x000000004c367000-0x000000004c383000) (0MB)
[    0.000000] efi: mem19: type=3, attr=0xf, range=[0x000000004c383000-0x000000004c39d000) (0MB)
[    0.000000] efi: mem20: type=4, attr=0xf, range=[0x000000004c39d000-0x000000004c3a6000) (0MB)
[    0.000000] efi: mem21: type=6, attr=0x800000000000000f, range=[0x000000004c3a6000-0x000000004c629000) (2MB)
[    0.000000] efi: mem22: type=4, attr=0xf, range=[0x000000004c629000-0x000000004c638000) (0MB)
[    0.000000] efi: mem23: type=7, attr=0xf, range=[0x000000004c638000-0x000000004c645000) (0MB)
[    0.000000] efi: mem24: type=2, attr=0xf, range=[0x000000004c645000-0x000000004c647000) (0MB)
[    0.000000] efi: mem25: type=7, attr=0xf, range=[0x000000004c647000-0x000000004f759000) (49MB)
[    0.000000] efi: mem26: type=4, attr=0xf, range=[0x000000004f759000-0x000000004f9ff000) (2MB)
[    0.000000] efi: mem27: type=7, attr=0xf, range=[0x000000004f9ff000-0x000000004fa61000) (0MB)
[    0.000000] efi: mem28: type=4, attr=0xf, range=[0x000000004fa61000-0x000000004fa81000) (0MB)
[    0.000000] efi: mem29: type=7, attr=0xf, range=[0x000000004fa81000-0x000000004fa91000) (0MB)
[    0.000000] efi: mem30: type=4, attr=0xf, range=[0x000000004fa91000-0x000000004fafb000) (0MB)
[    0.000000] efi: mem31: type=7, attr=0xf, range=[0x000000004fafb000-0x000000004fb0a000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x000000004fb0a000-0x000000004fb1d000) (0MB)
[    0.000000] efi: mem33: type=7, attr=0xf, range=[0x000000004fb1d000-0x000000004fb23000) (0MB)
[    0.000000] efi: mem34: type=4, attr=0xf, range=[0x000000004fb23000-0x000000004fb76000) (0MB)
[    0.000000] efi: mem35: type=7, attr=0xf, range=[0x000000004fb76000-0x000000004fcad000) (1MB)
[    0.000000] efi: mem36: type=4, attr=0xf, range=[0x000000004fcad000-0x000000004fe83000) (1MB)
[    0.000000] efi: mem37: type=7, attr=0xf, range=[0x000000004fe83000-0x000000004fe88000) (0MB)
[    0.000000] efi: mem38: type=4, attr=0xf, range=[0x000000004fe88000-0x000000004fece000) (0MB)
[    0.000000] efi: mem39: type=7, attr=0xf, range=[0x000000004fece000-0x000000004fed0000) (0MB)
[    0.000000] efi: mem40: type=4, attr=0xf, range=[0x000000004fed0000-0x000000004fee1000) (0MB)
[    0.000000] efi: mem41: type=7, attr=0xf, range=[0x000000004fee1000-0x000000004fee2000) (0MB)
[    0.000000] efi: mem42: type=4, attr=0xf, range=[0x000000004fee2000-0x000000005973b000) (152MB)
[    0.000000] efi: mem43: type=7, attr=0xf, range=[0x000000005973b000-0x000000005973d000) (0MB)
[    0.000000] efi: mem44: type=4, attr=0xf, range=[0x000000005973d000-0x0000000059761000) (0MB)
[    0.000000] efi: mem45: type=7, attr=0xf, range=[0x0000000059761000-0x0000000059766000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x0000000059766000-0x0000000059846000) (0MB)
[    0.000000] efi: mem47: type=7, attr=0xf, range=[0x0000000059846000-0x0000000059847000) (0MB)
[    0.000000] efi: mem48: type=4, attr=0xf, range=[0x0000000059847000-0x000000005ac56000) (20MB)
[    0.000000] efi: mem49: type=7, attr=0xf, range=[0x000000005ac56000-0x000000005b61a000) (9MB)
[    0.000000] efi: mem50: type=3, attr=0xf, range=[0x000000005b61a000-0x000000005b91e000) (3MB)
[    0.000000] efi: mem51: type=0, attr=0xf, range=[0x000000005b91e000-0x000000005b988000) (0MB)
[    0.000000] efi: mem52: type=0, attr=0xf, range=[0x000000005b988000-0x000000005bb24000) (1MB)
[    0.000000] efi: mem53: type=7, attr=0xf, range=[0x000000005bb24000-0x000000005be65000) (3MB)
[    0.000000] efi: mem54: type=2, attr=0xf, range=[0x000000005be65000-0x000000005be6f000) (0MB)
[    0.000000] efi: mem55: type=10, attr=0xf, range=[0x000000005be6f000-0x000000005cb30000) (12MB)
[    0.000000] efi: mem56: type=10, attr=0xf, range=[0x000000005cb30000-0x000000005cb34000) (0MB)
[    0.000000] efi: mem57: type=10, attr=0xf, range=[0x000000005cb34000-0x000000005cb48000) (0MB)
[    0.000000] efi: mem58: type=6, attr=0x800000000000000f, range=[0x000000005cb48000-0x000000005ce97000) (3MB)
[    0.000000] efi: mem59: type=6, attr=0x800000000000000f, range=[0x000000005ce97000-0x000000005ceac000) (0MB)
[    0.000000] efi: mem60: type=6, attr=0x800000000000000f, range=[0x000000005ceac000-0x000000005ceae000) (0MB)
[    0.000000] efi: mem61: type=6, attr=0x800000000000000f, range=[0x000000005ceae000-0x000000005cf4b000) (0MB)
[    0.000000] efi: mem62: type=5, attr=0x800000000000000f, range=[0x000000005cf4b000-0x000000005cf6f000) (0MB)
[    0.000000] efi: mem63: type=5, attr=0x800000000000000f, range=[0x000000005cf6f000-0x000000005cfff000) (0MB)
[    0.000000] efi: mem64: type=4, attr=0xf, range=[0x000000005cfff000-0x000000005d000000) (0MB)
[    0.000000] efi: mem65: type=7, attr=0xf, range=[0x0000000100000000-0x000000049f400000) (14836MB)
[    0.000000] efi: mem66: type=11, attr=0x8000000000000001, range=[0x00000000f0000000-0x00000000f8000000) (128MB)
[    0.000000] efi: mem67: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem68: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed04000) (0MB)
[    0.000000] efi: mem69: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem70: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem71: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: ASUSTeK COMPUTER INC. G750JW/G750JW, BIOS G750JW.207 05/23/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x49f400 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 0400000000 mask 7F80000000 write-back
[    0.000000]   2 base 0480000000 mask 7FE0000000 write-back
[    0.000000]   3 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   4 base 0060000000 mask 7FE0000000 uncachable
[    0.000000]   5 base 005FC00000 mask 7FFFC00000 uncachable
[    0.000000]   6 base 049F800000 mask 7FFF800000 uncachable
[    0.000000]   7 base 049F400000 mask 7FFFC00000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 2GB, type WB
[    0.000000] reg 2, base: 18GB, range: 512MB, type WB
[    0.000000] reg 3, base: 2GB, range: 2GB, type UC
[    0.000000] reg 4, base: 1536MB, range: 512MB, type UC
[    0.000000] reg 5, base: 1532MB, range: 4MB, type UC
[    0.000000] reg 6, base: 18936MB, range: 8MB, type UC
[    0.000000] reg 7, base: 18932MB, range: 4MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 9      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1GB, range: 512MB, type WB
[    0.000000] reg 2, base: 1532MB, range: 4MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 2GB, type WB
[    0.000000] reg 6, base: 18GB, range: 512MB, type WB
[    0.000000] reg 7, base: 18932MB, range: 4MB, type UC
[    0.000000] reg 8, base: 18936MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0x5fc00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x5d000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd880-0x000fd88f] mapped at [ffff8800000fd880]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fde000, 0x02fdefff] PGTABLE
[    0.000000] BRK [0x02fdf000, 0x02fdffff] PGTABLE
[    0.000000] BRK [0x02fe0000, 0x02fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x49f200000-0x49f3fffff]
[    0.000000]  [mem 0x49f200000-0x49f3fffff] page 2M
[    0.000000] BRK [0x02fe1000, 0x02fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x49c000000-0x49f1fffff]
[    0.000000]  [mem 0x49c000000-0x49f1fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x480000000-0x49bffffff]
[    0.000000]  [mem 0x480000000-0x49bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x4bb37fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x4b9fffff] page 2M
[    0.000000]  [mem 0x4ba00000-0x4bb37fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x4bb3f000-0x4c3a5fff]
[    0.000000]  [mem 0x4bb3f000-0x4bbfffff] page 4k
[    0.000000]  [mem 0x4bc00000-0x4c1fffff] page 2M
[    0.000000]  [mem 0x4c200000-0x4c3a5fff] page 4k
[    0.000000] BRK [0x02fe2000, 0x02fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x4c629000-0x5b91dfff]
[    0.000000]  [mem 0x4c629000-0x4c7fffff] page 4k
[    0.000000]  [mem 0x4c800000-0x5b7fffff] page 2M
[    0.000000]  [mem 0x5b800000-0x5b91dfff] page 4k
[    0.000000] BRK [0x02fe3000, 0x02fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x5bb24000-0x5be6efff]
[    0.000000]  [mem 0x5bb24000-0x5bbfffff] page 4k
[    0.000000]  [mem 0x5bc00000-0x5bdfffff] page 2M
[    0.000000]  [mem 0x5be00000-0x5be6efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x5cfff000-0x5cffffff]
[    0.000000]  [mem 0x5cfff000-0x5cffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x47fffffff]
[    0.000000]  [mem 0x100000000-0x47fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b86000-0x36dbafff]
[    0.000000] ACPI: RSDP 000000005cb12000 000024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 000000005cb12080 00008C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000005cb24598 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 000000005cb12228 01236D (v02 _ASUS_ Notebook 00000012 INTL 20111123)
[    0.000000] ACPI: FACS 000000005cb45080 000040
[    0.000000] ACPI: APIC 000000005cb246a8 000092 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 000000005cb24740 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: ECDT 000000005cb24788 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 000000005cb24850 00019D (v01  Intel    zpodd 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 000000005cb249f0 000539 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000005cb24f30 000AD8 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: MCFG 000000005cb25a08 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 000000005cb25a48 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 000000005cb25a80 000298 (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 000000005cb25d18 0056A0 (v01 SaSsdt  SaSsdt  00003000 INTL 20091112)
[    0.000000] ACPI: DMAR 000000005cb2b3b8 000070 (v01 INTEL      HSW  00000001 INTL 00000001)
[    0.000000] ACPI: MSDM 000000005bb22e18 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000049f3fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x49f3fffff]
[    0.000000]   NODE_DATA [mem 0x49f3f5000-0x49f3f9fff]
[    0.000000]  [ffffea0000000000-ffffea00127fffff] PMD -> [ffff88048ea00000-ffff88049e9fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x49f3fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00057fff]
[    0.000000]   node   0: [mem 0x00059000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x4bb37fff]
[    0.000000]   node   0: [mem 0x4bb3f000-0x4c3a5fff]
[    0.000000]   node   0: [mem 0x4c629000-0x5b91dfff]
[    0.000000]   node   0: [mem 0x5bb24000-0x5be6efff]
[    0.000000]   node   0: [mem 0x5cfff000-0x5cffffff]
[    0.000000]   node   0: [mem 0x100000000-0x49f3fffff]
[    0.000000] On node 0 totalpages: 4173181
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 26 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 5800 pages used for memmap
[    0.000000]   DMA32 zone: 371168 pages, LIFO batch:31
[    0.000000]   Normal zone: 59344 pages used for memmap
[    0.000000]   Normal zone: 3798016 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x4bb38000-0x4bb3efff]
[    0.000000] PM: Registered nosave memory: [mem 0x4c3a6000-0x4c628fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5b91e000-0x5bb23fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5be6f000-0x5cb47fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5cb48000-0x5cf4afff]
[    0.000000] PM: Registered nosave memory: [mem 0x5cf4b000-0x5cffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x5d000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x5d000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88049f000000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4107947
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic.efi.signed root=UUID=98252a17-dd23-4bd9-a2b4-3b00dd3f0fb8 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16133040K/16692724K available (7354K kernel code, 1142K rwdata, 3396K rodata, 1332K init, 1440K bss, 559684K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2394.607 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.21 BogoMIPS (lpj=9578428)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000598] Security Framework initialized
[    0.000610] AppArmor: AppArmor initialized
[    0.000611] Yama: becoming mindful.
[    0.001380] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.003614] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004555] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.004568] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.004746] Initializing cgroup subsys memory
[    0.004750] Initializing cgroup subsys devices
[    0.004751] Initializing cgroup subsys freezer
[    0.004752] Initializing cgroup subsys blkio
[    0.004753] Initializing cgroup subsys perf_event
[    0.004754] Initializing cgroup subsys hugetlb
[    0.004771] CPU: Physical Processor ID: 0
[    0.004772] CPU: Processor Core ID: 0
[    0.004775] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.004775] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.005532] mce: CPU supports 9 MCE banks
[    0.005543] CPU0: Thermal monitoring enabled (TM1)
[    0.005552] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.005552] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.005552] tlb_flushall_shift: 6
[    0.005631] Freeing SMP alternatives memory: 32K (ffffffff81e6c000 - ffffffff81e74000)
[    0.006339] ACPI: Core revision 20131115
[    0.014135] ACPI: All ACPI Tables successfully acquired
[    0.021208] ftrace: allocating 28458 entries in 112 pages
[    0.030015] dmar: Host address width 39
[    0.030017] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.030022] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.030023] dmar: RMRR base: 0x0000005baab000 end: 0x0000005bab7fff
[    0.030092] IOAPIC id 2 under DRHD base  0xfed90000 IOMMU 0
[    0.030093] HPET id 0 under DRHD base 0xfed90000
[    0.030151] Enabled IRQ remapping in x2apic mode
[    0.030152] Enabling x2apic
[    0.030153] Enabled x2apic
[    0.030163] Switched APIC routing to cluster x2apic.
[    0.030579] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070300] smpboot: CPU0: Intel(R) Core(TM) i7-4700HQ CPU @ 2.40GHz (fam: 06, model: 3c, stepping: 03)
[    0.070311] TSC deadline timer enabled
[    0.071641] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.071646] ... version:                3
[    0.071647] ... bit width:              48
[    0.071647] ... generic registers:      4
[    0.071648] ... value mask:             0000ffffffffffff
[    0.071649] ... max period:             0000ffffffffffff
[    0.071649] ... fixed-purpose events:   3
[    0.071650] ... event mask:             000000070000000f
[    0.072843] x86: Booting SMP configuration:
[    0.086754] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.072845] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.170229] x86: Booted up 1 node, 8 CPUs
[    0.170233] smpboot: Total of 8 processors activated (38313.71 BogoMIPS)
[    0.176390] devtmpfs: initialized
[    0.178082] EVM: security.selinux
[    0.178083] EVM: security.SMACK64
[    0.178083] EVM: security.ima
[    0.178084] EVM: security.capability
[    0.178111] PM: Registering ACPI NVS region [mem 0x4bb38000-0x4bb3efff] (28672 bytes)
[    0.178112] PM: Registering ACPI NVS region [mem 0x5be6f000-0x5cb47fff] (13471744 bytes)
[    0.178708] pinctrl core: initialized pinctrl subsystem
[    0.178744] regulator-dummy: no parameters
[    0.178774] RTC time: 22:13:50, date: 06/01/14
[    0.178795] NET: Registered protocol family 16
[    0.178859] cpuidle: using governor ladder
[    0.178860] cpuidle: using governor menu
[    0.178884] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.178885] ACPI: bus type PCI registered
[    0.178886] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.178924] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.178926] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.189257] PCI: Using configuration type 1 for base access
[    0.189912] bio: create slab <bio-0> at 0
[    0.190020] ACPI: Added _OSI(Module Device)
[    0.190021] ACPI: Added _OSI(Processor Device)
[    0.190022] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.190023] ACPI: Added _OSI(Processor Aggregator Device)
[    0.192089] ACPI : EC: EC description table is found, configuring boot EC
[    0.194233] ACPI: Executed 2 blocks of module-level executable AML code
[    0.200303] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.412191] ACPI: SSDT 000000005bb19c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.412877] ACPI: Dynamic OEM Table Load:
[    0.412879] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.416304] ACPI: SSDT 000000005bb19618 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.417054] ACPI: Dynamic OEM Table Load:
[    0.417055] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.424193] ACPI: SSDT 000000005bb18d98 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.424876] ACPI: Dynamic OEM Table Load:
[    0.424878] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.433267] ACPI: Interpreter enabled
[    0.433273] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.433277] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.433289] ACPI: (supports S0 S3 S4 S5)
[    0.433290] ACPI: Using IOAPIC for interrupt routing
[    0.433308] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.433463] ACPI: No dock devices found.
[    0.441127] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    0.441131] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.441273] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.441392] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.441818] PCI host bridge to bus 0000:00
[    0.441820] pci_bus 0000:00: root bus resource [bus 00-7e]
[    0.441821] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.441822] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.441823] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.441825] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.441826] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.441827] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.441828] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.441829] pci_bus 0000:00: root bus resource [mem 0x5fc00000-0xfeafffff]
[    0.441835] pci 0000:00:00.0: [8086:0c04] type 00 class 0x060000
[    0.441902] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.441927] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.441967] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.442016] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.442035] pci 0000:00:14.0: reg 0x10: [mem 0xdd600000-0xdd60ffff 64bit]
[    0.442088] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.442121] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.442149] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.442167] pci 0000:00:16.0: reg 0x10: [mem 0xdd618000-0xdd61800f 64bit]
[    0.442224] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.442289] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    0.442301] pci 0000:00:1b.0: reg 0x10: [mem 0xdd610000-0xdd613fff 64bit]
[    0.442359] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.442393] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.442418] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    0.442482] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.442518] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.442543] pci 0000:00:1c.2: [8086:8c14] type 01 class 0x060400
[    0.442608] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.442644] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.442667] pci 0000:00:1c.3: [8086:8c16] type 01 class 0x060400
[    0.442732] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.442768] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.442793] pci 0000:00:1c.4: [8086:8c18] type 01 class 0x060400
[    0.442857] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.442894] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.442923] pci 0000:00:1f.0: [8086:8c4b] type 00 class 0x060100
[    0.443067] pci 0000:00:1f.2: [8086:8c03] type 00 class 0x010601
[    0.443081] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.443088] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.443095] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.443101] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.443108] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.443115] pci 0000:00:1f.2: reg 0x24: [mem 0xdd616000-0xdd6167ff]
[    0.443148] pci 0000:00:1f.2: PME# supported from D3hot
[    0.443199] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.443212] pci 0000:00:1f.3: reg 0x10: [mem 0xdd615000-0xdd6150ff 64bit]
[    0.443230] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.443324] pci 0000:01:00.0: [10de:11e2] type 00 class 0x030000
[    0.443334] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.443345] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.443354] pci 0000:01:00.0: reg 0x1c: [mem 0xc0000000-0xc1ffffff 64bit pref]
[    0.443361] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.443369] pci 0000:01:00.0: reg 0x30: [mem 0xdd000000-0xdd07ffff pref]
[    0.443414] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.443437] pci 0000:01:00.1: [10de:0e0b] type 00 class 0x040300
[    0.443447] pci 0000:01:00.1: reg 0x10: [mem 0xdd080000-0xdd083fff]
[    0.448162] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.448165] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.448167] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.448171] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.448251] acpiphp: Slot [1] registered
[    0.448262] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.448403] pci 0000:03:00.0: [14e4:43b1] type 00 class 0x028000
[    0.448425] pci 0000:03:00.0: reg 0x10: [mem 0xdd400000-0xdd407fff 64bit]
[    0.448442] pci 0000:03:00.0: reg 0x18: [mem 0xdd200000-0xdd3fffff 64bit]
[    0.448528] pci 0000:03:00.0: supports D1 D2
[    0.448530] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.448562] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.456210] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.456215] pci 0000:00:1c.2:   bridge window [mem 0xdd200000-0xdd4fffff]
[    0.456582] pci 0000:04:00.0: [1969:10a1] type 00 class 0x020000
[    0.456836] pci 0000:04:00.0: reg 0x10: [mem 0xdd500000-0xdd53ffff 64bit]
[    0.456915] pci 0000:04:00.0: reg 0x18: [io  0xd000-0xd07f]
[    0.458406] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.458702] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.464288] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.464292] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.464295] pci 0000:00:1c.3:   bridge window [mem 0xdd500000-0xdd5fffff]
[    0.464374] acpiphp: Slot [1-1] registered
[    0.464391] pci 0000:00:1c.4: PCI bridge to [bus 05-3d]
[    0.464397] pci 0000:00:1c.4:   bridge window [mem 0xc4000000-0xdbffffff]
[    0.464403] pci 0000:00:1c.4:   bridge window [mem 0x80000000-0xafffffff 64bit pref]
[    0.464501] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.465563] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    0.465606] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 12)
[    0.465657] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 10 12)
[    0.465689] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 12)
[    0.465720] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.465752] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.465784] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 12)
[    0.465815] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.466256] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.466261] ACPI: \_SB_.PCI0: notify handler is installed
[    0.466320] Found 1 acpi root devices
[    0.466373] ACPI : EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.466433] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.466434] vgaarb: loaded
[    0.466435] vgaarb: bridge control possible 0000:01:00.0
[    0.466526] SCSI subsystem initialized
[    0.466556] libata version 3.00 loaded.
[    0.466568] ACPI: bus type USB registered
[    0.466576] usbcore: registered new interface driver usbfs
[    0.466580] usbcore: registered new interface driver hub
[    0.466602] usbcore: registered new device driver usb
[    0.466672] PCI: Using ACPI for IRQ routing
[    0.469418] PCI: pci_cache_line_size set to 64 bytes
[    0.469459] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.469460] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.469461] e820: reserve RAM buffer [mem 0x4bb38000-0x4bffffff]
[    0.469462] e820: reserve RAM buffer [mem 0x4c3a6000-0x4fffffff]
[    0.469463] e820: reserve RAM buffer [mem 0x5b91e000-0x5bffffff]
[    0.469464] e820: reserve RAM buffer [mem 0x5be6f000-0x5bffffff]
[    0.469465] e820: reserve RAM buffer [mem 0x5d000000-0x5fffffff]
[    0.469465] e820: reserve RAM buffer [mem 0x49f400000-0x49fffffff]
[    0.469512] NetLabel: Initializing
[    0.469513] NetLabel:  domain hash size = 128
[    0.469513] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.469521] NetLabel:  unlabeled traffic allowed by default
[    0.469554] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.469558] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.471585] Switched to clocksource hpet
[    0.474662] AppArmor: AppArmor Filesystem Enabled
[    0.474674] pnp: PnP ACPI init
[    0.474680] ACPI: bus type PNP registered
[    0.474724] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.474727] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.474789] pnp 00:01: [dma 4]
[    0.474797] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.474808] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.474868] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.474898] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.474972] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.474974] system 00:05: [io  0xffff] has been reserved
[    0.474975] system 00:05: [io  0xffff] has been reserved
[    0.474976] system 00:05: [io  0xffff] has been reserved
[    0.474977] system 00:05: [io  0x1c00-0x1cfe] has been reserved
[    0.474978] system 00:05: [io  0x1d00-0x1dfe] has been reserved
[    0.474979] system 00:05: [io  0x1e00-0x1efe] has been reserved
[    0.474981] system 00:05: [io  0x1f00-0x1ffe] has been reserved
[    0.474982] system 00:05: [io  0x1800-0x18fe] could not be reserved
[    0.474983] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.474984] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.475000] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.475026] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.475028] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.475055] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.475057] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.475074] system 00:09: [io  0x0240-0x0259] has been reserved
[    0.475075] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.475110] pnp 00:0a: Plug and Play ACPI device, IDs ETD010d SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.475134] pnp 00:0b: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.475376] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.475378] system 00:0c: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.475379] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.475380] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.475381] system 00:0c: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.475382] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.475384] system 00:0c: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.475385] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.475386] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.475388] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.475390] system 00:0c: [mem 0xeffef000-0xeffeffff] has been reserved
[    0.475391] system 00:0c: [mem 0xefff0000-0xefff0fff] has been reserved
[    0.475392] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.475438] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.475642] pnp: PnP ACPI: found 14 devices
[    0.475643] ACPI: bus type PNP unregistered
[    0.481359] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.481361] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.481363] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.481381] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 05-3d] add_size 1000
[    0.481384] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.481385] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.481386] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.481387] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.481390] pci 0000:00:1c.0: BAR 14: assigned [mem 0x5fc00000-0x5fdfffff]
[    0.481392] pci 0000:00:1c.0: BAR 15: assigned [mem 0x5fe00000-0x5fffffff 64bit pref]
[    0.481393] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.481395] pci 0000:00:1c.4: BAR 13: assigned [io  0x3000-0x3fff]
[    0.481397] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.481398] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.481400] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.481402] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.481405] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.481407] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.481411] pci 0000:00:1c.0:   bridge window [mem 0x5fc00000-0x5fdfffff]
[    0.481415] pci 0000:00:1c.0:   bridge window [mem 0x5fe00000-0x5fffffff 64bit pref]
[    0.481420] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.481424] pci 0000:00:1c.2:   bridge window [mem 0xdd200000-0xdd4fffff]
[    0.481430] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.481433] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.481437] pci 0000:00:1c.3:   bridge window [mem 0xdd500000-0xdd5fffff]
[    0.481444] pci 0000:00:1c.4: PCI bridge to [bus 05-3d]
[    0.481446] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.481450] pci 0000:00:1c.4:   bridge window [mem 0xc4000000-0xdbffffff]
[    0.481454] pci 0000:00:1c.4:   bridge window [mem 0x80000000-0xafffffff 64bit pref]
[    0.481459] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.481460] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.481462] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.481463] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.481464] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.481465] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.481466] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.481467] pci_bus 0000:00: resource 11 [mem 0x5fc00000-0xfeafffff]
[    0.481468] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.481469] pci_bus 0000:01: resource 1 [mem 0xdc000000-0xdd0fffff]
[    0.481470] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.481471] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.481472] pci_bus 0000:02: resource 1 [mem 0x5fc00000-0x5fdfffff]
[    0.481473] pci_bus 0000:02: resource 2 [mem 0x5fe00000-0x5fffffff 64bit pref]
[    0.481474] pci_bus 0000:03: resource 1 [mem 0xdd200000-0xdd4fffff]
[    0.481475] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.481476] pci_bus 0000:04: resource 1 [mem 0xdd500000-0xdd5fffff]
[    0.481477] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.481478] pci_bus 0000:05: resource 1 [mem 0xc4000000-0xdbffffff]
[    0.481479] pci_bus 0000:05: resource 2 [mem 0x80000000-0xafffffff 64bit pref]
[    0.481497] NET: Registered protocol family 2
[    0.481622] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.481774] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.481879] TCP: Hash tables configured (established 131072 bind 65536)
[    0.481890] TCP: reno registered
[    0.481903] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.481942] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.482001] NET: Registered protocol family 1
[    0.482169] pci 0000:01:00.0: Boot video device
[    0.482181] pci 0000:04:00.0: set MSI_INTX_DISABLE_BUG flag
[    0.482184] PCI: CLS 64 bytes, default 64
[    0.482216] Trying to unpack rootfs image as initramfs...
[    0.684433] Freeing initrd memory: 18644K (ffff880035b86000 - ffff880036dbb000)
[    0.684448] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.684449] software IO TLB [mem 0x47b38000-0x4bb38000] (64MB) mapped at [ffff880047b38000-ffff88004bb37fff]
[    0.684633] microcode: CPU0 sig=0x306c3, pf=0x20, revision=0x8
[    0.684638] microcode: CPU1 sig=0x306c3, pf=0x20, revision=0x8
[    0.684641] microcode: CPU2 sig=0x306c3, pf=0x20, revision=0x8
[    0.684646] microcode: CPU3 sig=0x306c3, pf=0x20, revision=0x8
[    0.684651] microcode: CPU4 sig=0x306c3, pf=0x20, revision=0x8
[    0.684655] microcode: CPU5 sig=0x306c3, pf=0x20, revision=0x8
[    0.684660] microcode: CPU6 sig=0x306c3, pf=0x20, revision=0x8
[    0.684664] microcode: CPU7 sig=0x306c3, pf=0x20, revision=0x8
[    0.684695] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.684696] Scanning for low memory corruption every 60 seconds
[    0.684872] Initialise system trusted keyring
[    0.684900] audit: initializing netlink socket (disabled)
[    0.684906] type=2000 audit(1401660829.476:1): initialized
[    0.703362] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.704273] zbud: loaded
[    0.704368] VFS: Disk quotas dquot_6.5.2
[    0.704393] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.704630] fuse init (API version 7.22)
[    0.704671] msgmni has been set to 31927
[    0.704701] Key type big_key registered
[    0.705056] Key type asymmetric registered
[    0.705057] Asymmetric key parser 'x509' registered
[    0.705073] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.705109] io scheduler noop registered
[    0.705111] io scheduler deadline registered (default)
[    0.705123] io scheduler cfq registered
[    0.705248] pcieport 0000:00:01.0: irq 41 for MSI/MSI-X
[    0.705567] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.705575] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.705598] efifb: probing for efifb
[    0.705770] efifb: framebuffer at 0xc1000000, mapped to 0xffffc90009c00000, using 1920k, total 1920k
[    0.705771] efifb: mode is 800x600x32, linelength=3200, pages=1
[    0.705772] efifb: scrolling: redraw
[    0.705773] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.706567] Console: switching to colour frame buffer device 100x37
[    0.707311] fb0: EFI VGA frame buffer device
[    0.707318] intel_idle: MWAIT substates: 0x42120
[    0.707319] intel_idle: v0.4 model 0x3C
[    0.707320] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.707430] ipmi message handler version 39.2
[    0.707489] ACPI: AC Adapter [AC0] (on-line)
[    0.707561] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.708223] ACPI: Lid Switch [LID]
[    0.708244] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.708247] ACPI: Sleep Button [SLPB]
[    0.708264] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.708265] ACPI: Power Button [PWRF]
[    0.708713] thermal LNXTHERM:00: registered as thermal_zone0
[    0.708715] ACPI: Thermal Zone [THRM] (66 C)
[    0.708731] GHES: HEST is not enabled!
[    0.708778] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.709789] Linux agpgart interface v0.103
[    0.710584] brd: module loaded
[    0.711005] loop: module loaded
[    0.711232] libphy: Fixed MDIO Bus: probed
[    0.711284] tun: Universal TUN/TAP device driver, 1.6
[    0.711285] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.711313] PPP generic driver version 2.4.2
[    0.711342] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.711344] ehci-pci: EHCI PCI platform driver
[    0.711350] ehci-platform: EHCI generic platform driver
[    0.711355] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.711356] ohci-pci: OHCI PCI platform driver
[    0.711360] ohci-platform: OHCI generic platform driver
[    0.711366] uhci_hcd: USB Universal Host Controller Interface driver
[    0.711471] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.711475] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.711594] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.711612] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    0.711674] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.711676] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.711677] usb usb1: Product: xHCI Host Controller
[    0.711678] usb usb1: Manufacturer: Linux 3.13.0-27-generic xhci_hcd
[    0.711679] usb usb1: SerialNumber: 0000:00:14.0
[    0.711751] hub 1-0:1.0: USB hub found
[    0.711777] hub 1-0:1.0: 14 ports detected
[    0.714067] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.714069] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.714105] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.714106] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.714107] usb usb2: Product: xHCI Host Controller
[    0.714108] usb usb2: Manufacturer: Linux 3.13.0-27-generic xhci_hcd
[    0.714109] usb usb2: SerialNumber: 0000:00:14.0
[    0.714160] hub 2-0:1.0: USB hub found
[    0.714173] hub 2-0:1.0: 6 ports detected
[    0.728475] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.728787] ACPI: Battery Slot [BAT0] (battery present)
[    0.732136] i8042: Detected active multiplexing controller, rev 1.1
[    0.734719] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.734722] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.734734] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.734753] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.734760] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.734946] mousedev: PS/2 mouse device common for all mice
[    0.735107] rtc_cmos 00:06: RTC can wake from S4
[    0.735233] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.735277] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.735318] device-mapper: uevent: version 1.0.3
[    0.735369] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.735373] ledtrig-cpu: registered to indicate activity on CPUs
[    0.735374] EFI Variables Facility v0.08 2004-May-17
[    0.737758] TCP: cubic registered
[    0.737803] NET: Registered protocol family 10
[    0.737898] NET: Registered protocol family 17
[    0.737906] Key type dns_resolver registered
[    0.738127] Loading compiled-in X.509 certificates
[    0.738659] Loaded X.509 cert 'Magrathea: Glacier signing key: 23984ac203784325ccf7b95b51f6c119380eb933'
[    0.738675] registered taskstats version 1
[    0.741209] Key type trusted registered
[    0.743207] Key type encrypted registered
[    0.745308] AppArmor: AppArmor sha1 policy hashing enabled
[    0.745310] IMA: No TPM chip found, activating TPM-bypass!
[    0.745671] regulator-dummy: disabling
[    0.745809]   Magic number: 2:576:248
[    0.745838] acpi device:5e: hash matches
[    0.745859] memory memory122: hash matches
[    0.745934] rtc_cmos 00:06: setting system clock to 2014-06-01 22:13:50 UTC (1401660830)
[    0.747179] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.747180] EDD information not available.
[    0.747213] PM: Hibernation image not present or could not be loaded.
[    0.747883] Freeing unused kernel memory: 1332K (ffffffff81d1f000 - ffffffff81e6c000)
[    0.747885] Write protecting the kernel read-only data: 12288k
[    0.749341] Freeing unused kernel memory: 828K (ffff880002731000 - ffff880002800000)
[    0.750409] Freeing unused kernel memory: 700K (ffff880002b51000 - ffff880002c00000)
[    0.761856] systemd-udevd[143]: starting version 204
[    0.775740] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.781309] ahci 0000:00:1f.2: version 3.0
[    0.781419] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    0.781477] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x14 impl SATA mode
[    0.781479] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst
[    0.783520] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [ac:22:0b:ab:fb:0b]
[    0.788248] scsi0 : ahci
[    0.788337] scsi1 : ahci
[    0.788401] scsi2 : ahci
[    0.788466] scsi3 : ahci
[    0.788534] scsi4 : ahci
[    0.788599] scsi5 : ahci
[    0.788640] ata1: DUMMY
[    0.788641] ata2: DUMMY
[    0.788644] ata3: SATA max UDMA/133 abar m2048@0xdd616000 port 0xdd616200 irq 43
[    0.788645] ata4: DUMMY
[    0.788647] ata5: SATA max UDMA/133 abar m2048@0xdd616000 port 0xdd616300 irq 43
[    0.788648] ata6: DUMMY
[    1.024089] usb 1-4: new full-speed USB device number 2 using xhci_hcd
[    1.042815] usb 1-4: New USB device found, idVendor=046d, idProduct=c52b
[    1.042819] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.042820] usb 1-4: Product: USB Receiver
[    1.042822] usb 1-4: Manufacturer: Logitech
[    1.045970] hidraw: raw HID events driver (C) Jiri Kosina
[    1.050740] usbcore: registered new interface driver usbhid
[    1.050743] usbhid: USB HID core driver
[    1.053192] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-4/input2
[    1.112192] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.112212] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.117222] ata3.00: ATAPI: Slimtype DVD A  DS8A9SH, EAA2, max UDMA/100
[    1.118333] ata3.00: configured for UDMA/100
[    1.118762] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.118765] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.118768] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.125179] ata5.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR20002, max UDMA/133
[    1.125182] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.129796] scsi 2:0:0:0: CD-ROM            Slimtype DVD A  DS8A9SH   EAA2 PQ: 0 ANSI: 5
[    1.131851] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.131855] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.131857] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.138200] ata5.00: configured for UDMA/133
[    1.145203] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.145207] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.145329] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.145401] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.145642] scsi 4:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2AR2 PQ: 0 ANSI: 5
[    1.145771] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.145807] sd 4:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.145810] sd 4:0:0:0: [sda] 4096-byte physical blocks
[    1.145948] sd 4:0:0:0: [sda] Write Protect is off
[    1.145951] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.146020] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.212306] usb 1-5: new full-speed USB device number 3 using xhci_hcd
[    1.214785]  sda: sda1 sda2 sda3 sda4
[    1.215406] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.234918] usb 1-5: New USB device found, idVendor=13d3, idProduct=3404
[    1.234922] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.234924] usb 1-5: Product: BCM20702A0
[    1.234927] usb 1-5: Manufacturer: Broadcom Corp
[    1.234929] usb 1-5: SerialNumber: 240A6407CF42
[    1.400447] usb 1-7: new high-speed USB device number 4 using xhci_hcd
[    1.522216] usb 1-7: New USB device found, idVendor=13d3, idProduct=5188
[    1.522219] usb 1-7: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.522221] usb 1-7: Product: USB2.0 UVC HD Webcam
[    1.522222] usb 1-7: Manufacturer: Azurewave
[    1.522224] usb 1-7: SerialNumber: NULL
[    1.523622] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x360f00)
[    1.538011] psmouse serio4: elantech: Synaptics capabilities query result 0x00, 0x16, 0x0c.
[    1.611585] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input11
[    1.684641] tsc: Refined TSC clocksource calibration: 2394.455 MHz
[    1.799837] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.799840] EXT4-fs (sda1): write access will be enabled during recovery
[    1.970302] random: nonblocking pool is initialized
[    2.685549] Switched to clocksource tsc
[    3.959107] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.959188] EXT4-fs (sda1): 4 orphan inodes deleted
[    3.959189] EXT4-fs (sda1): recovery complete
[    4.168757] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   14.453725] Adding 38773756k swap on /dev/sda4.  Priority:-1 extents:1 across:38773756k FS
[   14.522767] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.561058] systemd-udevd[350]: starting version 204
[   14.717433] lp: driver loaded but no devices found
[   14.721200] ppdev: user-space parallel port driver
[   14.730835] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   14.734758] wmi: Mapper loaded
[   14.744139] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \GPIS 1 (20131115/utaddress-251)
[   14.744145] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 2 (20131115/utaddress-251)
[   14.744149] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.744153] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   14.744155] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GP01 2 (20131115/utaddress-251)
[   14.744158] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 3 (20131115/utaddress-251)
[   14.744160] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.744161] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   14.744163] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GP01 2 (20131115/utaddress-251)
[   14.744166] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 3 (20131115/utaddress-251)
[   14.744168] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.744169] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.746433] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   14.747916] [drm] Initialized drm 1.1.0 20060810
[   14.750920] cfg80211: Calling CRDA to update world regulatory domain
[   14.751254] nvidia: module license 'NVIDIA' taints kernel.
[   14.751257] Disabling lock debugging due to kernel taint
[   14.752171] lib80211: common routines for IEEE802.11 drivers
[   14.752175] lib80211_crypt: registered algorithm 'NULL'
[   14.755900] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   14.761524] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   14.775280] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   14.775291] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.38  Wed Jan  8 19:32:30 PST 2014
[   14.775349] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   14.781300] lib80211_crypt: registered algorithm 'TKIP'
[   14.823608] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   14.827581] acpi device:5f: registered as cooling_device9
[   14.857223] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   14.866436] SKU: Nid=0x1d sku_cfg=0x4127bd05
[   14.866437] SKU: port_connectivity=0x1
[   14.866438] SKU: enable_pcbeep=0x0
[   14.866439] SKU: check_sum=0x00000007
[   14.866439] SKU: customization=0x000000bd
[   14.866440] SKU: external_amp=0x0
[   14.866441] SKU: platform_type=0x1
[   14.866441] SKU: swap=0x0
[   14.866442] SKU: override=0x1
[   14.866738] autoconfig: line_outs=2 (0x17/0x14/0x0/0x0/0x0) type:speaker
[   14.866739]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.866740]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   14.866741]    mono: mono_out=0x0
[   14.866741]    dig-out=0x1e/0x0
[   14.866742]    inputs:
[   14.866743]      Mic=0x18
[   14.866744]      Internal Mic=0x12
[   14.866745] realtek: No valid SSID, checking pincfg 0x4127bd05 for NID 0x1d
[   14.866745] realtek: Enabling init ASM_ID=0xbd05 CODEC_ID=10ec0282
[   14.871975] type=1400 audit(1401660844.610:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=787 comm="apparmor_parser"
[   14.871979] type=1400 audit(1401660844.610:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=787 comm="apparmor_parser"
[   14.871982] type=1400 audit(1401660844.610:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=787 comm="apparmor_parser"
[   14.872233] type=1400 audit(1401660844.610:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=787 comm="apparmor_parser"
[   14.872236] type=1400 audit(1401660844.610:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=787 comm="apparmor_parser"
[   14.872353] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   14.872365] type=1400 audit(1401660844.610:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=787 comm="apparmor_parser"
[   14.872410] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   14.872411] type=1400 audit(1401660844.610:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=789 comm="apparmor_parser"
[   14.872415] type=1400 audit(1401660844.610:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=789 comm="apparmor_parser"
[   14.872419] type=1400 audit(1401660844.610:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=789 comm="apparmor_parser"
[   14.872426] type=1400 audit(1401660844.610:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=788 comm="apparmor_parser"
[   14.872617] hda_intel: Disabling MSI
[   14.872621] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   14.872646] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   14.875918] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   14.893701] Linux video capture interface: v2.00
[   14.898284] uvcvideo: Found UVC 1.00 device USB2.0 UVC HD Webcam (13d3:5188)
[   14.903946] input: USB2.0 UVC HD Webcam as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input14
[   14.904092] usbcore: registered new interface driver uvcvideo
[   14.904094] USB Video Class driver (1.1.1)
[   14.911382] acpi device:62: registered as cooling_device10
[   14.911451] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:5c/LNXVIDEO:00/input/input15
[   14.917595] asus_wmi: ASUS WMI generic driver loaded
[   14.918679] asus_wmi: Initialization: 0x1
[   14.918700] asus_wmi: BIOS WMI version: 7.9
[   14.918722] asus_wmi: SFUN value: 0x4a0877
[   14.919400] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input16
[   14.927241] asus_wmi: Backlight controlled by ACPI video driver
[   15.186793] cfg80211: World regulatory domain updated:
[   15.186795] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.186797] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.186797] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.186798] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.186799] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.186800] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.283645] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input18
[   15.283715] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input17
[   16.775759] init: udev-fallback-graphics main process (1645) terminated with status 1
[   17.104459] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[   31.070257] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   31.526976] init: failsafe main process (1748) killed by TERM signal
[   31.875943] Bluetooth: Core ver 2.17
[   31.875955] NET: Registered protocol family 31
[   31.875956] Bluetooth: HCI device and connection manager initialized
[   31.875961] Bluetooth: HCI socket layer initialized
[   31.875963] Bluetooth: L2CAP socket layer initialized
[   31.875965] Bluetooth: SCO socket layer initialized
[   31.878349] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.878351] Bluetooth: BNEP filters: protocol multicast
[   31.878356] Bluetooth: BNEP socket layer initialized
[   31.878901] Bluetooth: RFCOMM TTY layer initialized
[   31.878908] Bluetooth: RFCOMM socket layer initialized
[   31.878911] Bluetooth: RFCOMM ver 1.11
[   31.903988] audit_printk_skb: 24 callbacks suppressed
[   31.903990] type=1400 audit(1401660861.626:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1899 comm="apparmor_parser"
[   31.903994] type=1400 audit(1401660861.626:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1899 comm="apparmor_parser"
[   31.904236] type=1400 audit(1401660861.626:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1899 comm="apparmor_parser"
[   31.967033] type=1400 audit(1401660861.690:23): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1915 comm="apparmor_parser"
[   31.967038] type=1400 audit(1401660861.690:24): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1915 comm="apparmor_parser"
[   31.967041] type=1400 audit(1401660861.690:25): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1915 comm="apparmor_parser"
[   31.967293] type=1400 audit(1401660861.690:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1915 comm="apparmor_parser"
[   31.967295] type=1400 audit(1401660861.690:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1915 comm="apparmor_parser"
[   31.967455] type=1400 audit(1401660861.690:28): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1914 comm="apparmor_parser"
[   31.967459] type=1400 audit(1401660861.690:29): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1914 comm="apparmor_parser"
[   32.112325] init: cups main process (1900) killed by HUP signal
[   32.112333] init: cups main process ended, respawning
[   32.452015] init: anacron main process (1994) terminated with status 1

```

Here is the result of lscpi:

```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
04:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)


```

Here are my complete hardware specs:

```

id:    
vineel-g750jw
description:     Notebook
product:     G750JW (ASUS-NotebookSKU)
vendor:     ASUSTeK COMPUTER INC.
version:     1.0
serial:     D7N0CY58461529D
width:     64 bits
capabilities:     smbios-2.7 dmi-2.7 vsyscall32
configuration:    
boot    =    normal
chassis    =    notebook
family    =    G
sku    =    ASUS-NotebookSKU
uuid    =    7ECCBCBE-AB4D-A0F0-89A7-AC220BABFB0B
id:    
core
description:     Motherboard
product:     G750JW
vendor:     ASUSTeK COMPUTER INC.
physical id:     
0
version:     1.0
serial:     BSN12345678901234567
slot:     MIDDLE
id:    
firmware
description:     BIOS
vendor:     American Megatrends Inc.
physical id:     
0
version:     G750JW.207
date:     05/23/2013
size:     64KiB
capacity:     6080KiB
capabilities:     pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
id:    
cpu
description:     CPU
product:     Intel(R) Core(TM) i7-4700HQ CPU @ 2.40GHz
vendor:     Intel Corp.
physical id:     
8
bus info:     
cpu@0
version:     Intel(R) Core(TM) i7-4700HQ CPU @ 2.40GHz
slot:     SOCKET 0
size:     800MHz
capacity:     3800MHz
width:     64 bits
clock:     100MHz
capabilities:     x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
configuration:    
cores    =    4
enabledcores    =    4
threads    =    8
id:    
cache:0
description:     L2 cache
physical id:     
9
slot:     CPU Internal L2
size:     1MiB
capacity:     1MiB
capabilities:     internal write-back unified
id:    
cache:1
description:     L1 cache
physical id:     
a
slot:     CPU Internal L1
size:     256KiB
capacity:     256KiB
capabilities:     internal write-back
id:    
cache:2
description:     L3 cache
physical id:     
b
slot:     CPU Internal L3
size:     6MiB
capacity:     6MiB
capabilities:     internal write-back unified
id:    
memory
description:     System Memory
physical id:     
c
slot:     System board or motherboard
size:     16GiB
id:    
bank:0
description:     DIMM [empty]
product:     [Empty]
vendor:     [Empty]
physical id:     
0
serial:     [Empty]
slot:     ChannelA-DIMM0
id:    
bank:1
description:     SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product:     M471B5173BH0-YK0
vendor:     Samsung
physical id:     
1
serial:     15211033
slot:     ChannelA-DIMM1
size:     4GiB
width:     64 bits
clock:     1600MHz (0.6ns)
id:    
bank:2
description:     SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
vendor:     AMD
physical id:     
2
serial:     00000000
slot:     ChannelB-DIMM0
size:     8GiB
width:     64 bits
clock:     1600MHz (0.6ns)
id:    
bank:3
description:     SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product:     M471B5173BH0-YK0
vendor:     Samsung
physical id:     
3
serial:     15211019
slot:     ChannelB-DIMM1
size:     4GiB
width:     64 bits
clock:     1600MHz (0.6ns)
id:    
pci
description:     Host bridge
product:     Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
vendor:     Intel Corporation
physical id:     
100
bus info:     
pci@0000:00:00.0
version:     06
width:     32 bits
clock:     33MHz
id:    
pci:0
description:     PCI bridge
product:     Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
vendor:     Intel Corporation
physical id:     
1
bus info:     
pci@0000:00:01.0
version:     06
width:     32 bits
clock:     33MHz
capabilities:     pci pm msi pciexpress normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    41
ioport    :    e000(size=4096)
memory    :    dc000000-dd0fffff
ioport    :    b0000000(size=301989888)
id:    
display
description:     VGA compatible controller
product:     GK106M [GeForce GTX 765M]
vendor:     NVIDIA Corporation
physical id:     
0
bus info:     
pci@0000:01:00.0
version:     a1
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress vga_controller bus_master cap_list rom
configuration:    
driver    =    nvidia
latency    =    0
resources:    
irq    :    47
memory    :    dc000000-dcffffff
memory    :    b0000000-bfffffff
memory    :    c0000000-c1ffffff
ioport    :    e000(size=128)
memory    :    dd000000-dd07ffff
id:    
multimedia
description:     Audio device
product:     GK106 HDMI Audio Controller
vendor:     NVIDIA Corporation
physical id:     
0.1
bus info:     
pci@0000:01:00.1
version:     a1
width:     32 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list
configuration:    
driver    =    snd_hda_intel
latency    =    0
resources:    
irq    :    17
memory    :    dd080000-dd083fff
id:    
usb
description:     USB controller
product:     8 Series/C220 Series Chipset Family USB xHCI
vendor:     Intel Corporation
physical id:     
14
bus info:     
pci@0000:00:14.0
version:     04
width:     64 bits
clock:     33MHz
capabilities:     pm msi xhci bus_master cap_list
configuration:    
driver    =    xhci_hcd
latency    =    0
resources:    
irq    :    42
memory    :    dd600000-dd60ffff
id:    
communication
description:     Communication controller
product:     8 Series/C220 Series Chipset Family MEI Controller #1
vendor:     Intel Corporation
physical id:     
16
bus info:     
pci@0000:00:16.0
version:     04
width:     64 bits
clock:     33MHz
capabilities:     pm msi bus_master cap_list
configuration:    
driver    =    mei_me
latency    =    0
resources:    
irq    :    44
memory    :    dd618000-dd61800f
id:    
multimedia
description:     Audio device
product:     8 Series/C220 Series Chipset High Definition Audio Controller
vendor:     Intel Corporation
physical id:     
1b
bus info:     
pci@0000:00:1b.0
version:     04
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list
configuration:    
driver    =    snd_hda_intel
latency    =    0
resources:    
irq    :    45
memory    :    dd610000-dd613fff
id:    
pci:1
description:     PCI bridge
product:     8 Series/C220 Series Chipset Family PCI Express Root Port #1
vendor:     Intel Corporation
physical id:     
1c
bus info:     
pci@0000:00:1c.0
version:     d4
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    16
ioport    :    2000(size=4096)
memory    :    5fc00000-5fdfffff
ioport    :    5fe00000(size=2097152)
id:    
pci:2
description:     PCI bridge
product:     8 Series/C220 Series Chipset Family PCI Express Root Port #3
vendor:     Intel Corporation
physical id:     
1c.2
bus info:     
pci@0000:00:1c.2
version:     d4
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    18
memory    :    dd200000-dd4fffff
id:    
network
description:     Wireless interface
product:     BCM4352 802.11ac Wireless Network Adapter
vendor:     Broadcom Corporation
physical id:     
0
bus info:     
pci@0000:03:00.0
logical name:     
wlan0
version:     03
serial:     24:0a:64:3a:67:31
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:    
broadcast    =    yes
driver    =    wl0
driverversion    =    6.30.223.141 (r415941)
ip    =    10.203.73.158
latency    =    0
multicast    =    yes
wireless    =    IEEE 802.11abg
resources:    
irq    :    18
memory    :    dd400000-dd407fff
memory    :    dd200000-dd3fffff
id:    
pci:3
description:     PCI bridge
product:     8 Series/C220 Series Chipset Family PCI Express Root Port #4
vendor:     Intel Corporation
physical id:     
1c.3
bus info:     
pci@0000:00:1c.3
version:     d4
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    19
ioport    :    d000(size=4096)
memory    :    dd500000-dd5fffff
id:    
network
description:     Ethernet interface
product:     QCA8171 Gigabit Ethernet
vendor:     Qualcomm Atheros
physical id:     
0
bus info:     
pci@0000:04:00.0
logical name:     
eth0
version:     10
serial:     ac:22:0b:ab:fb:0b
capacity:     1Gbit/s
width:     64 bits
clock:     33MHz
capabilities:     pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration:    
autonegotiation    =    on
broadcast    =    yes
driver    =    alx
latency    =    0
link    =    no
multicast    =    yes
port    =    twisted pair
resources:    
irq    :    46
memory    :    dd500000-dd53ffff
ioport    :    d000(size=128)
id:    
pci:4
description:     PCI bridge
product:     8 Series/C220 Series Chipset Family PCI Express Root Port #5
vendor:     Intel Corporation
physical id:     
1c.4
bus info:     
pci@0000:00:1c.4
version:     d4
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    16
ioport    :    3000(size=4096)
memory    :    c4000000-dbffffff
ioport    :    80000000(size=805306368)
id:    
isa
description:     ISA bridge
product:     HM87 Express LPC Controller
vendor:     Intel Corporation
physical id:     
1f
bus info:     
pci@0000:00:1f.0
version:     04
width:     32 bits
clock:     33MHz
capabilities:     isa bus_master cap_list
configuration:    
driver    =    lpc_ich
latency    =    0
resources:    
irq    :    0
id:    
storage
description:     SATA controller
product:     8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
vendor:     Intel Corporation
physical id:     
1f.2
bus info:     
pci@0000:00:1f.2
version:     04
width:     32 bits
clock:     66MHz
capabilities:     storage msi pm ahci_1.0 bus_master cap_list
configuration:    
driver    =    ahci
latency    =    0
resources:    
irq    :    43
ioport    :    f070(size=8)
ioport    :    f060(size=4)
ioport    :    f050(size=8)
ioport    :    f040(size=4)
ioport    :    f020(size=32)
memory    :    dd616000-dd6167ff
id:    
serial
description:     SMBus
product:     8 Series/C220 Series Chipset Family SMBus Controller
vendor:     Intel Corporation
physical id:     
1f.3
bus info:     
pci@0000:00:1f.3
version:     04
width:     64 bits
clock:     33MHz
configuration:    
latency    =    0
resources:    
memory    :    dd615000-dd6150ff
ioport    :    f000(size=32)
id:    
scsi:0
physical id:     
1
logical name:     
scsi2
capabilities:     emulated
id:    
cdrom
description:     DVD-RAM writer
product:     DVD A DS8A9SH
vendor:     Slimtype
physical id:     
0.0.0
bus info:     
scsi@2:0.0.0
logical name:     
/dev/cdrom
logical name:     
/dev/sr0
version:     EAA2
capabilities:     removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:    
ansiversion    =    5
status    =    nodisc
id:    
scsi:1
physical id:     
2
logical name:     
scsi4
capabilities:     emulated
id:    
disk
description:     ATA Disk
product:     ST1000LM024 HN-M
vendor:     Seagate
physical id:     
0.0.0
bus info:     
scsi@4:0.0.0
logical name:     
/dev/sda
version:     2AR2
serial:     S2Y4J9AD604481
size:     931GiB (1TB)
capabilities:     gpt-1.00 partitioned partitioned:gpt
configuration:    
ansiversion    =    5
guid    =    28f7f69a-6ea8-4c31-9347-498294b77bb4
sectorsize    =    4096
id:    
volume:0
description:     EXT4 volume
vendor:     Linux
physical id:     
1
bus info:     
scsi@4:0.0.0,1
logical name:     
/dev/sda1
logical name:     
/
version:     1.0
serial:     98252a17-dd23-4bd9-a2b4-3b00dd3f0fb8
size:     93GiB
capabilities:     journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
configuration:    
created    =    2014-05-27 12:15:17
filesystem    =    ext4
lastmountpoint    =    /
modified    =    2014-05-31 15:17:57
mount.fstype    =    ext4
mount.options    =    rw,noatime,nodiratime,discard,errors=remount-ro,data=ordered
mounted    =    2014-06-01 13:40:43
state    =    mounted
id:    
volume:1
description:     EXT4 volume
vendor:     Linux
physical id:     
2
bus info:     
scsi@4:0.0.0,2
logical name:     
/dev/sda2
logical name:     
/home
version:     1.0
serial:     9592983e-8c64-4f68-95ab-c8a8e4592497
size:     800GiB
capabilities:     journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration:    
created    =    2014-05-27 12:15:19
filesystem    =    ext4
lastmountpoint    =    /home
modified    =    2014-06-01 16:14:20
mount.fstype    =    ext4
mount.options    =    rw,relatime,data=ordered
mounted    =    2014-06-01 16:14:20
state    =    mounted
id:    
volume:2
description:     Windows FAT volume
vendor:     mkfs.fat
physical id:     
3
bus info:     
scsi@4:0.0.0,3
logical name:     
/dev/sda3
logical name:     
/boot/efi
version:     FAT32
serial:     3883-8063
size:     469MiB
capacity:     476MiB
capabilities:     boot fat initialized
configuration:    
FATs    =    2
filesystem    =    fat
mount.fstype    =    vfat
mount.options    =    rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
state    =    mounted
id:    
volume:3
description:     Linux swap volume
vendor:     Linux
physical id:     
4
bus info:     
scsi@4:0.0.0,4
logical name:     
/dev/sda4
version:     1
serial:     2894db67-189d-47f4-975f-cb98d68baeb3
size:     36GiB
capacity:     36GiB
capabilities:     nofs swap initialized
configuration:    
filesystem    =    swap
pagesize    =    4095


```

---

### Post by rahul4557 on 2014-06-02
are you using x86 Ubuntu on your laptop by any chance??
If yes switch to x64..

---

### Post by mörgæs on 2014-06-02
32 or 64 bit does not matter in this context.

---

### Post by viye3106 on 2014-06-02
I am pretty sure I am using x64

---

### Post by viye3106 on 2014-06-05
I recently replaced Windows 8 with Ubuntu 14.04 on my laptop (Asus rog g750jw). My system recently started freezing up for no apparent reason (the caps lock and num lock indicators blink indefinitely when that happens). A quick google search and replies to this post: [ http://ubuntuforums.org/showthread.php?t=2227134 ]( http://ubuntuforums.org/showthread.php?t=2227134 ) indicate that it might be kernel panic. I have no idea what might be causing it and how to fix it. Any help is appreciated. 

Here is the content of /var/log/dmesg:

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.13.0-27-generic (buildd@akateko) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #50-Ubuntu SMP Thu May 15 18:06:16 UTC 2014 (Ubuntu 3.13.0-27.50-generic 3.13.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic.efi.signed root=UUID=98252a17-dd23-4bd9-a2b4-3b00dd3f0fb8 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x0000000000057fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000058000-0x0000000000058fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000059000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000004bb37fff] usable
[    0.000000] BIOS-e820: [mem 0x000000004bb38000-0x000000004bb3efff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000004bb3f000-0x000000004c3a5fff] usable
[    0.000000] BIOS-e820: [mem 0x000000004c3a6000-0x000000004c628fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000004c629000-0x000000005b91dfff] usable
[    0.000000] BIOS-e820: [mem 0x000000005b91e000-0x000000005bb23fff] reserved
[    0.000000] BIOS-e820: [mem 0x000000005bb24000-0x000000005be6efff] usable
[    0.000000] BIOS-e820: [mem 0x000000005be6f000-0x000000005cb47fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000005cb48000-0x000000005cf4afff] reserved
[    0.000000] BIOS-e820: [mem 0x000000005cf4b000-0x000000005cffefff] type 20
[    0.000000] BIOS-e820: [mem 0x000000005cfff000-0x000000005cffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000049f3fffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI 2.0=0x5cb12000  ACPI=0x5cb12000  SMBIOS=0xf04c0  MPS=0xfd590 
[    0.000000] efi: mem00: type=3, attr=0xf, range=[0x0000000000000000-0x0000000000008000) (0MB)
[    0.000000] efi: mem01: type=7, attr=0xf, range=[0x0000000000008000-0x0000000000058000) (0MB)
[    0.000000] efi: mem02: type=0, attr=0xf, range=[0x0000000000058000-0x0000000000059000) (0MB)
[    0.000000] efi: mem03: type=7, attr=0xf, range=[0x0000000000059000-0x000000000005f000) (0MB)
[    0.000000] efi: mem04: type=4, attr=0xf, range=[0x000000000005f000-0x0000000000060000) (0MB)
[    0.000000] efi: mem05: type=3, attr=0xf, range=[0x0000000000060000-0x000000000009f000) (0MB)
[    0.000000] efi: mem06: type=6, attr=0x800000000000000f, range=[0x000000000009f000-0x00000000000a0000) (0MB)
[    0.000000] efi: mem07: type=2, attr=0xf, range=[0x0000000000100000-0x0000000001500000) (20MB)
[    0.000000] efi: mem08: type=7, attr=0xf, range=[0x0000000001500000-0x0000000002000000) (11MB)
[    0.000000] efi: mem09: type=2, attr=0xf, range=[0x0000000002000000-0x0000000003400000) (20MB)
[    0.000000] efi: mem10: type=7, attr=0xf, range=[0x0000000003400000-0x00000000348bf000) (788MB)
[    0.000000] efi: mem11: type=2, attr=0xf, range=[0x00000000348bf000-0x0000000048748000) (318MB)
[    0.000000] efi: mem12: type=7, attr=0xf, range=[0x0000000048748000-0x000000004b830000) (48MB)
[    0.000000] efi: mem13: type=2, attr=0xf, range=[0x000000004b830000-0x000000004ba04000) (1MB)
[    0.000000] efi: mem14: type=1, attr=0xf, range=[0x000000004ba04000-0x000000004bb38000) (1MB)
[    0.000000] efi: mem15: type=10, attr=0xf, range=[0x000000004bb38000-0x000000004bb3f000) (0MB)
[    0.000000] efi: mem16: type=4, attr=0xf, range=[0x000000004bb3f000-0x000000004bc92000) (1MB)
[    0.000000] efi: mem17: type=3, attr=0xf, range=[0x000000004bc92000-0x000000004c367000) (6MB)
[    0.000000] efi: mem18: type=4, attr=0xf, range=[0x000000004c367000-0x000000004c383000) (0MB)
[    0.000000] efi: mem19: type=3, attr=0xf, range=[0x000000004c383000-0x000000004c39d000) (0MB)
[    0.000000] efi: mem20: type=4, attr=0xf, range=[0x000000004c39d000-0x000000004c3a6000) (0MB)
[    0.000000] efi: mem21: type=6, attr=0x800000000000000f, range=[0x000000004c3a6000-0x000000004c629000) (2MB)
[    0.000000] efi: mem22: type=4, attr=0xf, range=[0x000000004c629000-0x000000004c638000) (0MB)
[    0.000000] efi: mem23: type=7, attr=0xf, range=[0x000000004c638000-0x000000004c645000) (0MB)
[    0.000000] efi: mem24: type=2, attr=0xf, range=[0x000000004c645000-0x000000004c647000) (0MB)
[    0.000000] efi: mem25: type=7, attr=0xf, range=[0x000000004c647000-0x000000004f759000) (49MB)
[    0.000000] efi: mem26: type=4, attr=0xf, range=[0x000000004f759000-0x000000004f9ff000) (2MB)
[    0.000000] efi: mem27: type=7, attr=0xf, range=[0x000000004f9ff000-0x000000004fa61000) (0MB)
[    0.000000] efi: mem28: type=4, attr=0xf, range=[0x000000004fa61000-0x000000004fa81000) (0MB)
[    0.000000] efi: mem29: type=7, attr=0xf, range=[0x000000004fa81000-0x000000004fa91000) (0MB)
[    0.000000] efi: mem30: type=4, attr=0xf, range=[0x000000004fa91000-0x000000004fafb000) (0MB)
[    0.000000] efi: mem31: type=7, attr=0xf, range=[0x000000004fafb000-0x000000004fb0a000) (0MB)
[    0.000000] efi: mem32: type=4, attr=0xf, range=[0x000000004fb0a000-0x000000004fb30000) (0MB)
[    0.000000] efi: mem33: type=7, attr=0xf, range=[0x000000004fb30000-0x000000004fb36000) (0MB)
[    0.000000] efi: mem34: type=4, attr=0xf, range=[0x000000004fb36000-0x000000004fb76000) (0MB)
[    0.000000] efi: mem35: type=7, attr=0xf, range=[0x000000004fb76000-0x000000004fcad000) (1MB)
[    0.000000] efi: mem36: type=4, attr=0xf, range=[0x000000004fcad000-0x000000004fe83000) (1MB)
[    0.000000] efi: mem37: type=7, attr=0xf, range=[0x000000004fe83000-0x000000004fe88000) (0MB)
[    0.000000] efi: mem38: type=4, attr=0xf, range=[0x000000004fe88000-0x000000004fece000) (0MB)
[    0.000000] efi: mem39: type=7, attr=0xf, range=[0x000000004fece000-0x000000004fed0000) (0MB)
[    0.000000] efi: mem40: type=4, attr=0xf, range=[0x000000004fed0000-0x000000004fee1000) (0MB)
[    0.000000] efi: mem41: type=7, attr=0xf, range=[0x000000004fee1000-0x000000004fee2000) (0MB)
[    0.000000] efi: mem42: type=4, attr=0xf, range=[0x000000004fee2000-0x0000000059761000) (152MB)
[    0.000000] efi: mem43: type=7, attr=0xf, range=[0x0000000059761000-0x0000000059766000) (0MB)
[    0.000000] efi: mem44: type=4, attr=0xf, range=[0x0000000059766000-0x0000000059846000) (0MB)
[    0.000000] efi: mem45: type=7, attr=0xf, range=[0x0000000059846000-0x0000000059847000) (0MB)
[    0.000000] efi: mem46: type=4, attr=0xf, range=[0x0000000059847000-0x000000005ac56000) (20MB)
[    0.000000] efi: mem47: type=7, attr=0xf, range=[0x000000005ac56000-0x000000005b61a000) (9MB)
[    0.000000] efi: mem48: type=3, attr=0xf, range=[0x000000005b61a000-0x000000005b91e000) (3MB)
[    0.000000] efi: mem49: type=0, attr=0xf, range=[0x000000005b91e000-0x000000005b988000) (0MB)
[    0.000000] efi: mem50: type=0, attr=0xf, range=[0x000000005b988000-0x000000005bb24000) (1MB)
[    0.000000] efi: mem51: type=7, attr=0xf, range=[0x000000005bb24000-0x000000005be65000) (3MB)
[    0.000000] efi: mem52: type=2, attr=0xf, range=[0x000000005be65000-0x000000005be6f000) (0MB)
[    0.000000] efi: mem53: type=10, attr=0xf, range=[0x000000005be6f000-0x000000005cb30000) (12MB)
[    0.000000] efi: mem54: type=10, attr=0xf, range=[0x000000005cb30000-0x000000005cb34000) (0MB)
[    0.000000] efi: mem55: type=10, attr=0xf, range=[0x000000005cb34000-0x000000005cb48000) (0MB)
[    0.000000] efi: mem56: type=6, attr=0x800000000000000f, range=[0x000000005cb48000-0x000000005ce97000) (3MB)
[    0.000000] efi: mem57: type=6, attr=0x800000000000000f, range=[0x000000005ce97000-0x000000005ceac000) (0MB)
[    0.000000] efi: mem58: type=6, attr=0x800000000000000f, range=[0x000000005ceac000-0x000000005ceae000) (0MB)
[    0.000000] efi: mem59: type=6, attr=0x800000000000000f, range=[0x000000005ceae000-0x000000005cf4b000) (0MB)
[    0.000000] efi: mem60: type=5, attr=0x800000000000000f, range=[0x000000005cf4b000-0x000000005cf6f000) (0MB)
[    0.000000] efi: mem61: type=5, attr=0x800000000000000f, range=[0x000000005cf6f000-0x000000005cfff000) (0MB)
[    0.000000] efi: mem62: type=4, attr=0xf, range=[0x000000005cfff000-0x000000005d000000) (0MB)
[    0.000000] efi: mem63: type=7, attr=0xf, range=[0x0000000100000000-0x000000049f400000) (14836MB)
[    0.000000] efi: mem64: type=11, attr=0x8000000000000001, range=[0x00000000f0000000-0x00000000f8000000) (128MB)
[    0.000000] efi: mem65: type=11, attr=0x8000000000000001, range=[0x00000000fec00000-0x00000000fec01000) (0MB)
[    0.000000] efi: mem66: type=11, attr=0x8000000000000001, range=[0x00000000fed00000-0x00000000fed04000) (0MB)
[    0.000000] efi: mem67: type=11, attr=0x8000000000000001, range=[0x00000000fed1c000-0x00000000fed20000) (0MB)
[    0.000000] efi: mem68: type=11, attr=0x8000000000000001, range=[0x00000000fee00000-0x00000000fee01000) (0MB)
[    0.000000] efi: mem69: type=11, attr=0x8000000000000001, range=[0x00000000ff000000-0x0000000100000000) (16MB)
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: ASUSTeK COMPUTER INC. G750JW/G750JW, BIOS G750JW.207 05/23/2013
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x49f400 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask 7C00000000 write-back
[    0.000000]   1 base 0400000000 mask 7F80000000 write-back
[    0.000000]   2 base 0480000000 mask 7FE0000000 write-back
[    0.000000]   3 base 0080000000 mask 7F80000000 uncachable
[    0.000000]   4 base 0060000000 mask 7FE0000000 uncachable
[    0.000000]   5 base 005FC00000 mask 7FFFC00000 uncachable
[    0.000000]   6 base 049F800000 mask 7FFF800000 uncachable
[    0.000000]   7 base 049F400000 mask 7FFFC00000 uncachable
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 2GB, type WB
[    0.000000] reg 2, base: 18GB, range: 512MB, type WB
[    0.000000] reg 3, base: 2GB, range: 2GB, type UC
[    0.000000] reg 4, base: 1536MB, range: 512MB, type UC
[    0.000000] reg 5, base: 1532MB, range: 4MB, type UC
[    0.000000] reg 6, base: 18936MB, range: 8MB, type UC
[    0.000000] reg 7, base: 18932MB, range: 4MB, type UC
[    0.000000] total RAM covered: 16368M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 16M     num_reg: 9      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1GB, range: 512MB, type WB
[    0.000000] reg 2, base: 1532MB, range: 4MB, type UC
[    0.000000] reg 3, base: 4GB, range: 4GB, type WB
[    0.000000] reg 4, base: 8GB, range: 8GB, type WB
[    0.000000] reg 5, base: 16GB, range: 2GB, type WB
[    0.000000] reg 6, base: 18GB, range: 512MB, type WB
[    0.000000] reg 7, base: 18932MB, range: 4MB, type UC
[    0.000000] reg 8, base: 18936MB, range: 8MB, type UC
[    0.000000] e820: update [mem 0x5fc00000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0x5d000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd880-0x000fd88f] mapped at [ffff8800000fd880]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000096000] 96000 size 24576
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x02fde000, 0x02fdefff] PGTABLE
[    0.000000] BRK [0x02fdf000, 0x02fdffff] PGTABLE
[    0.000000] BRK [0x02fe0000, 0x02fe0fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x49f200000-0x49f3fffff]
[    0.000000]  [mem 0x49f200000-0x49f3fffff] page 2M
[    0.000000] BRK [0x02fe1000, 0x02fe1fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x49c000000-0x49f1fffff]
[    0.000000]  [mem 0x49c000000-0x49f1fffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x480000000-0x49bffffff]
[    0.000000]  [mem 0x480000000-0x49bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0x4bb37fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x4b9fffff] page 2M
[    0.000000]  [mem 0x4ba00000-0x4bb37fff] page 4k
[    0.000000] init_memory_mapping: [mem 0x4bb3f000-0x4c3a5fff]
[    0.000000]  [mem 0x4bb3f000-0x4bbfffff] page 4k
[    0.000000]  [mem 0x4bc00000-0x4c1fffff] page 2M
[    0.000000]  [mem 0x4c200000-0x4c3a5fff] page 4k
[    0.000000] BRK [0x02fe2000, 0x02fe2fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x4c629000-0x5b91dfff]
[    0.000000]  [mem 0x4c629000-0x4c7fffff] page 4k
[    0.000000]  [mem 0x4c800000-0x5b7fffff] page 2M
[    0.000000]  [mem 0x5b800000-0x5b91dfff] page 4k
[    0.000000] BRK [0x02fe3000, 0x02fe3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x5bb24000-0x5be6efff]
[    0.000000]  [mem 0x5bb24000-0x5bbfffff] page 4k
[    0.000000]  [mem 0x5bc00000-0x5bdfffff] page 2M
[    0.000000]  [mem 0x5be00000-0x5be6efff] page 4k
[    0.000000] init_memory_mapping: [mem 0x5cfff000-0x5cffffff]
[    0.000000]  [mem 0x5cfff000-0x5cffffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x47fffffff]
[    0.000000]  [mem 0x100000000-0x47fffffff] page 1G
[    0.000000] RAMDISK: [mem 0x35b86000-0x36dbafff]
[    0.000000] ACPI: RSDP 000000005cb12000 000024 (v02 _ASUS_)
[    0.000000] ACPI: XSDT 000000005cb12080 00008C (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FACP 000000005cb24598 00010C (v05 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 000000005cb12228 01236D (v02 _ASUS_ Notebook 00000012 INTL 20111123)
[    0.000000] ACPI: FACS 000000005cb45080 000040
[    0.000000] ACPI: APIC 000000005cb246a8 000092 (v03 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 000000005cb24740 000044 (v01 _ASUS_ Notebook 01072009 AMI  00010013)
[    0.000000] ACPI: ECDT 000000005cb24788 0000C1 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 000000005cb24850 00019D (v01  Intel    zpodd 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 000000005cb249f0 000539 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 000000005cb24f30 000AD8 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: MCFG 000000005cb25a08 00003C (v01 _ASUS_ Notebook 01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 000000005cb25a48 000038 (v01 _ASUS_ Notebook 01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 000000005cb25a80 000298 (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 000000005cb25d18 0056A0 (v01 SaSsdt  SaSsdt  00003000 INTL 20091112)
[    0.000000] ACPI: DMAR 000000005cb2b3b8 000070 (v01 INTEL      HSW  00000001 INTL 00000001)
[    0.000000] ACPI: MSDM 000000005bb22e18 000055 (v03 _ASUS_ Notebook 00000000 ASUS 00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000049f3fffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x49f3fffff]
[    0.000000]   NODE_DATA [mem 0x49f3f5000-0x49f3f9fff]
[    0.000000]  [ffffea0000000000-ffffea00127fffff] PMD -> [ffff88048ea00000-ffff88049e9fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x49f3fffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x00057fff]
[    0.000000]   node   0: [mem 0x00059000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0x4bb37fff]
[    0.000000]   node   0: [mem 0x4bb3f000-0x4c3a5fff]
[    0.000000]   node   0: [mem 0x4c629000-0x5b91dfff]
[    0.000000]   node   0: [mem 0x5bb24000-0x5be6efff]
[    0.000000]   node   0: [mem 0x5cfff000-0x5cffffff]
[    0.000000]   node   0: [mem 0x100000000-0x49f3fffff]
[    0.000000] On node 0 totalpages: 4173181
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 26 pages reserved
[    0.000000]   DMA zone: 3997 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 5800 pages used for memmap
[    0.000000]   DMA32 zone: 371168 pages, LIFO batch:31
[    0.000000]   Normal zone: 59344 pages used for memmap
[    0.000000]   Normal zone: 3798016 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x00058000-0x00058fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x4bb38000-0x4bb3efff]
[    0.000000] PM: Registered nosave memory: [mem 0x4c3a6000-0x4c628fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5b91e000-0x5bb23fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5be6f000-0x5cb47fff]
[    0.000000] PM: Registered nosave memory: [mem 0x5cb48000-0x5cf4afff]
[    0.000000] PM: Registered nosave memory: [mem 0x5cf4b000-0x5cffefff]
[    0.000000] PM: Registered nosave memory: [mem 0x5d000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0x5d000000-0xefffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88049f000000 s86336 r8192 d24256 u262144
[    0.000000] pcpu-alloc: s86336 r8192 d24256 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4107947
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic.efi.signed root=UUID=98252a17-dd23-4bd9-a2b4-3b00dd3f0fb8 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 16133032K/16692724K available (7354K kernel code, 1142K rwdata, 3396K rodata, 1332K init, 1440K bss, 559692K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-7.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 67108864 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 2394.553 MHz processor
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4789.10 BogoMIPS (lpj=9578212)
[    0.000004] pid_max: default: 32768 minimum: 301
[    0.000675] Security Framework initialized
[    0.000689] AppArmor: AppArmor initialized
[    0.000689] Yama: becoming mindful.
[    0.001459] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.003693] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.004634] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.004648] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.004823] Initializing cgroup subsys memory
[    0.004827] Initializing cgroup subsys devices
[    0.004829] Initializing cgroup subsys freezer
[    0.004830] Initializing cgroup subsys blkio
[    0.004831] Initializing cgroup subsys perf_event
[    0.004832] Initializing cgroup subsys hugetlb
[    0.004848] CPU: Physical Processor ID: 0
[    0.004849] CPU: Processor Core ID: 0
[    0.004852] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.004852] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.005610] mce: CPU supports 9 MCE banks
[    0.005621] CPU0: Thermal monitoring enabled (TM1)
[    0.005630] Last level iTLB entries: 4KB 0, 2MB 0, 4MB 0
[    0.005630] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 0
[    0.005630] tlb_flushall_shift: 6
[    0.005709] Freeing SMP alternatives memory: 32K (ffffffff81e6c000 - ffffffff81e74000)
[    0.006421] ACPI: Core revision 20131115
[    0.014111] ACPI: All ACPI Tables successfully acquired
[    0.020763] ftrace: allocating 28458 entries in 112 pages
[    0.029586] dmar: Host address width 39
[    0.029587] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.029593] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap d2008c20660462 ecap f010da
[    0.029594] dmar: RMRR base: 0x0000005baab000 end: 0x0000005bab7fff
[    0.029658] IOAPIC id 2 under DRHD base  0xfed90000 IOMMU 0
[    0.029659] HPET id 0 under DRHD base 0xfed90000
[    0.029718] Enabled IRQ remapping in x2apic mode
[    0.029718] Enabling x2apic
[    0.029719] Enabled x2apic
[    0.029724] Switched APIC routing to cluster x2apic.
[    0.030126] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.069842] smpboot: CPU0: Intel(R) Core(TM) i7-4700HQ CPU @ 2.40GHz (fam: 06, model: 3c, stepping: 03)
[    0.069848] TSC deadline timer enabled
[    0.071175] Performance Events: PEBS fmt2+, 16-deep LBR, Haswell events, full-width counters, Intel PMU driver.
[    0.071180] ... version:                3
[    0.071181] ... bit width:              48
[    0.071181] ... generic registers:      4
[    0.071182] ... value mask:             0000ffffffffffff
[    0.071183] ... max period:             0000ffffffffffff
[    0.071183] ... fixed-purpose events:   3
[    0.071184] ... event mask:             000000070000000f
[    0.072380] x86: Booting SMP configuration:
[    0.086281] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.072381] .... node  #0, CPUs:      #1 #2 #3 #4 #5 #6 #7
[    0.169698] x86: Booted up 1 node, 8 CPUs
[    0.169701] smpboot: Total of 8 processors activated (38312.84 BogoMIPS)
[    0.175731] devtmpfs: initialized
[    0.177422] EVM: security.selinux
[    0.177423] EVM: security.SMACK64
[    0.177424] EVM: security.ima
[    0.177424] EVM: security.capability
[    0.177452] PM: Registering ACPI NVS region [mem 0x4bb38000-0x4bb3efff] (28672 bytes)
[    0.177453] PM: Registering ACPI NVS region [mem 0x5be6f000-0x5cb47fff] (13471744 bytes)
[    0.178051] pinctrl core: initialized pinctrl subsystem
[    0.178089] regulator-dummy: no parameters
[    0.178114] RTC time: 16:39:38, date: 06/05/14
[    0.178136] NET: Registered protocol family 16
[    0.178198] cpuidle: using governor ladder
[    0.178199] cpuidle: using governor menu
[    0.178223] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.178224] ACPI: bus type PCI registered
[    0.178225] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.178261] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
[    0.178262] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
[    0.188646] PCI: Using configuration type 1 for base access
[    0.189300] bio: create slab <bio-0> at 0
[    0.189407] ACPI: Added _OSI(Module Device)
[    0.189409] ACPI: Added _OSI(Processor Device)
[    0.189410] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.189411] ACPI: Added _OSI(Processor Aggregator Device)
[    0.191462] ACPI : EC: EC description table is found, configuring boot EC
[    0.193602] ACPI: Executed 2 blocks of module-level executable AML code
[    0.199647] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.415016] ACPI: SSDT 000000005bb19c18 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.415702] ACPI: Dynamic OEM Table Load:
[    0.415703] ACPI: SSDT           (null) 0003D3 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.423135] ACPI: SSDT 000000005bb19618 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.423885] ACPI: Dynamic OEM Table Load:
[    0.423887] ACPI: SSDT           (null) 0005AA (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.427019] ACPI: SSDT 000000005bb18d98 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.427702] ACPI: Dynamic OEM Table Load:
[    0.427704] ACPI: SSDT           (null) 000119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.436088] ACPI: Interpreter enabled
[    0.436095] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.436101] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
[    0.436116] ACPI: (supports S0 S3 S4 S5)
[    0.436117] ACPI: Using IOAPIC for interrupt routing
[    0.436141] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.436355] ACPI: No dock devices found.
[    0.443614] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7e])
[    0.443618] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.443760] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.443879] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.444289] PCI host bridge to bus 0000:00
[    0.444291] pci_bus 0000:00: root bus resource [bus 00-7e]
[    0.444292] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.444293] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.444294] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.444296] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.444297] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.444298] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.444299] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.444300] pci_bus 0000:00: root bus resource [mem 0x5fc00000-0xfeafffff]
[    0.444306] pci 0000:00:00.0: [8086:0c04] type 00 class 0x060000
[    0.444369] pci 0000:00:01.0: [8086:0c01] type 01 class 0x060400
[    0.444394] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.444434] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.444478] pci 0000:00:14.0: [8086:8c31] type 00 class 0x0c0330
[    0.444497] pci 0000:00:14.0: reg 0x10: [mem 0xdd600000-0xdd60ffff 64bit]
[    0.444550] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.444583] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.444606] pci 0000:00:16.0: [8086:8c3a] type 00 class 0x078000
[    0.444623] pci 0000:00:16.0: reg 0x10: [mem 0xdd618000-0xdd61800f 64bit]
[    0.444680] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.444741] pci 0000:00:1b.0: [8086:8c20] type 00 class 0x040300
[    0.444753] pci 0000:00:1b.0: reg 0x10: [mem 0xdd610000-0xdd613fff 64bit]
[    0.444811] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.444845] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.444864] pci 0000:00:1c.0: [8086:8c10] type 01 class 0x060400
[    0.444921] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.444957] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.444976] pci 0000:00:1c.2: [8086:8c14] type 01 class 0x060400
[    0.445034] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.445069] pci 0000:00:1c.2: System wakeup disabled by ACPI
[    0.445088] pci 0000:00:1c.3: [8086:8c16] type 01 class 0x060400
[    0.445145] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.445181] pci 0000:00:1c.3: System wakeup disabled by ACPI
[    0.445201] pci 0000:00:1c.4: [8086:8c18] type 01 class 0x060400
[    0.445265] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.445302] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.445327] pci 0000:00:1f.0: [8086:8c4b] type 00 class 0x060100
[    0.445467] pci 0000:00:1f.2: [8086:8c03] type 00 class 0x010601
[    0.445480] pci 0000:00:1f.2: reg 0x10: [io  0xf070-0xf077]
[    0.445487] pci 0000:00:1f.2: reg 0x14: [io  0xf060-0xf063]
[    0.445494] pci 0000:00:1f.2: reg 0x18: [io  0xf050-0xf057]
[    0.445501] pci 0000:00:1f.2: reg 0x1c: [io  0xf040-0xf043]
[    0.445507] pci 0000:00:1f.2: reg 0x20: [io  0xf020-0xf03f]
[    0.445514] pci 0000:00:1f.2: reg 0x24: [mem 0xdd616000-0xdd6167ff]
[    0.445547] pci 0000:00:1f.2: PME# supported from D3hot
[    0.445593] pci 0000:00:1f.3: [8086:8c22] type 00 class 0x0c0500
[    0.445606] pci 0000:00:1f.3: reg 0x10: [mem 0xdd615000-0xdd6150ff 64bit]
[    0.445624] pci 0000:00:1f.3: reg 0x20: [io  0xf000-0xf01f]
[    0.445714] pci 0000:01:00.0: [10de:11e2] type 00 class 0x030000
[    0.445725] pci 0000:01:00.0: reg 0x10: [mem 0xdc000000-0xdcffffff]
[    0.445735] pci 0000:01:00.0: reg 0x14: [mem 0xb0000000-0xbfffffff 64bit pref]
[    0.445745] pci 0000:01:00.0: reg 0x1c: [mem 0xc0000000-0xc1ffffff 64bit pref]
[    0.445752] pci 0000:01:00.0: reg 0x24: [io  0xe000-0xe07f]
[    0.445759] pci 0000:01:00.0: reg 0x30: [mem 0xdd000000-0xdd07ffff pref]
[    0.445805] pci 0000:01:00.0: System wakeup disabled by ACPI
[    0.445828] pci 0000:01:00.1: [10de:0e0b] type 00 class 0x040300
[    0.445837] pci 0000:01:00.1: reg 0x10: [mem 0xdd080000-0xdd083fff]
[    0.450987] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.450990] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.450992] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.450995] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.451059] acpiphp: Slot [1] registered
[    0.451065] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.451194] pci 0000:03:00.0: [14e4:43b1] type 00 class 0x028000
[    0.451216] pci 0000:03:00.0: reg 0x10: [mem 0xdd400000-0xdd407fff 64bit]
[    0.451232] pci 0000:03:00.0: reg 0x18: [mem 0xdd200000-0xdd3fffff 64bit]
[    0.451319] pci 0000:03:00.0: supports D1 D2
[    0.451320] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.451352] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.459030] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.459036] pci 0000:00:1c.2:   bridge window [mem 0xdd200000-0xdd4fffff]
[    0.459180] pci 0000:04:00.0: [1969:10a1] type 00 class 0x020000
[    0.459226] pci 0000:04:00.0: reg 0x10: [mem 0xdd500000-0xdd53ffff 64bit]
[    0.459271] pci 0000:04:00.0: reg 0x18: [io  0xd000-0xd07f]
[    0.459542] pci 0000:04:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.459633] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.467016] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.467020] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.467023] pci 0000:00:1c.3:   bridge window [mem 0xdd500000-0xdd5fffff]
[    0.467093] acpiphp: Slot [1-1] registered
[    0.467105] pci 0000:00:1c.4: PCI bridge to [bus 05-3d]
[    0.467111] pci 0000:00:1c.4:   bridge window [mem 0xc4000000-0xdbffffff]
[    0.467116] pci 0000:00:1c.4:   bridge window [mem 0x80000000-0xafffffff 64bit pref]
[    0.467177] acpi PNP0A08:00: Disabling ASPM (FADT indicates it is unsupported)
[    0.468127] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12)
[    0.468170] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 12)
[    0.468212] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 10 12)
[    0.468253] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 12)
[    0.468293] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.468334] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.468375] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 12)
[    0.468415] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 12) *0, disabled.
[    0.468972] ACPI: Enabled 5 GPEs in block 00 to 3F
[    0.468976] ACPI: \_SB_.PCI0: notify handler is installed
[    0.469036] Found 1 acpi root devices
[    0.469088] ACPI : EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[    0.469147] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.469148] vgaarb: loaded
[    0.469149] vgaarb: bridge control possible 0000:01:00.0
[    0.469240] SCSI subsystem initialized
[    0.469270] libata version 3.00 loaded.
[    0.469282] ACPI: bus type USB registered
[    0.469290] usbcore: registered new interface driver usbfs
[    0.469294] usbcore: registered new interface driver hub
[    0.469316] usbcore: registered new device driver usb
[    0.469387] PCI: Using ACPI for IRQ routing
[    0.472136] PCI: pci_cache_line_size set to 64 bytes
[    0.472178] e820: reserve RAM buffer [mem 0x00058000-0x0005ffff]
[    0.472179] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.472179] e820: reserve RAM buffer [mem 0x4bb38000-0x4bffffff]
[    0.472180] e820: reserve RAM buffer [mem 0x4c3a6000-0x4fffffff]
[    0.472181] e820: reserve RAM buffer [mem 0x5b91e000-0x5bffffff]
[    0.472182] e820: reserve RAM buffer [mem 0x5be6f000-0x5bffffff]
[    0.472183] e820: reserve RAM buffer [mem 0x5d000000-0x5fffffff]
[    0.472184] e820: reserve RAM buffer [mem 0x49f400000-0x49fffffff]
[    0.472230] NetLabel: Initializing
[    0.472231] NetLabel:  domain hash size = 128
[    0.472232] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.472239] NetLabel:  unlabeled traffic allowed by default
[    0.472272] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.472276] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.474303] Switched to clocksource hpet
[    0.477369] AppArmor: AppArmor Filesystem Enabled
[    0.477381] pnp: PnP ACPI init
[    0.477387] ACPI: bus type PNP registered
[    0.477432] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.477434] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.477498] pnp 00:01: [dma 4]
[    0.477506] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.477517] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.477577] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.477607] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.477680] system 00:05: [io  0x0680-0x069f] has been reserved
[    0.477682] system 00:05: [io  0xffff] has been reserved
[    0.477683] system 00:05: [io  0xffff] has been reserved
[    0.477684] system 00:05: [io  0xffff] has been reserved
[    0.477685] system 00:05: [io  0x1c00-0x1cfe] has been reserved
[    0.477686] system 00:05: [io  0x1d00-0x1dfe] has been reserved
[    0.477687] system 00:05: [io  0x1e00-0x1efe] has been reserved
[    0.477689] system 00:05: [io  0x1f00-0x1ffe] has been reserved
[    0.477690] system 00:05: [io  0x1800-0x18fe] could not be reserved
[    0.477691] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.477692] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.477709] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.477735] system 00:07: [io  0x1854-0x1857] has been reserved
[    0.477737] system 00:07: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.477765] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.477766] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.477783] system 00:09: [io  0x0240-0x0259] has been reserved
[    0.477784] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.477818] pnp 00:0a: Plug and Play ACPI device, IDs ETD010d SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)
[    0.477843] pnp 00:0b: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)
[    0.478084] system 00:0c: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.478086] system 00:0c: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.478087] system 00:0c: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.478088] system 00:0c: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.478089] system 00:0c: [mem 0xf0000000-0xf7ffffff] has been reserved
[    0.478090] system 00:0c: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.478092] system 00:0c: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.478093] system 00:0c: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.478094] system 00:0c: [mem 0xff000000-0xffffffff] has been reserved
[    0.478096] system 00:0c: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.478098] system 00:0c: [mem 0xeffef000-0xeffeffff] has been reserved
[    0.478099] system 00:0c: [mem 0xefff0000-0xefff0fff] has been reserved
[    0.478100] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.478146] system 00:0d: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.478349] pnp: PnP ACPI: found 14 devices
[    0.478350] ACPI: bus type PNP unregistered
[    0.484070] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 02] add_size 1000
[    0.484072] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000
[    0.484074] pci 0000:00:1c.0: bridge window [mem 0x00100000-0x000fffff] to [bus 02] add_size 200000
[    0.484092] pci 0000:00:1c.4: bridge window [io  0x1000-0x0fff] to [bus 05-3d] add_size 1000
[    0.484095] pci 0000:00:1c.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.484096] pci 0000:00:1c.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[    0.484098] pci 0000:00:1c.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.484099] pci 0000:00:1c.4: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.484101] pci 0000:00:1c.0: BAR 14: assigned [mem 0x5fc00000-0x5fdfffff]
[    0.484103] pci 0000:00:1c.0: BAR 15: assigned [mem 0x5fe00000-0x5fffffff 64bit pref]
[    0.484105] pci 0000:00:1c.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.484106] pci 0000:00:1c.4: BAR 13: assigned [io  0x3000-0x3fff]
[    0.484108] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.484109] pci 0000:00:01.0:   bridge window [io  0xe000-0xefff]
[    0.484112] pci 0000:00:01.0:   bridge window [mem 0xdc000000-0xdd0fffff]
[    0.484114] pci 0000:00:01.0:   bridge window [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.484116] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.484118] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.484122] pci 0000:00:1c.0:   bridge window [mem 0x5fc00000-0x5fdfffff]
[    0.484126] pci 0000:00:1c.0:   bridge window [mem 0x5fe00000-0x5fffffff 64bit pref]
[    0.484131] pci 0000:00:1c.2: PCI bridge to [bus 03]
[    0.484135] pci 0000:00:1c.2:   bridge window [mem 0xdd200000-0xdd4fffff]
[    0.484141] pci 0000:00:1c.3: PCI bridge to [bus 04]
[    0.484144] pci 0000:00:1c.3:   bridge window [io  0xd000-0xdfff]
[    0.484148] pci 0000:00:1c.3:   bridge window [mem 0xdd500000-0xdd5fffff]
[    0.484154] pci 0000:00:1c.4: PCI bridge to [bus 05-3d]
[    0.484156] pci 0000:00:1c.4:   bridge window [io  0x3000-0x3fff]
[    0.484160] pci 0000:00:1c.4:   bridge window [mem 0xc4000000-0xdbffffff]
[    0.484164] pci 0000:00:1c.4:   bridge window [mem 0x80000000-0xafffffff 64bit pref]
[    0.484169] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.484171] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.484172] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.484173] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    0.484174] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    0.484175] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    0.484176] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    0.484177] pci_bus 0000:00: resource 11 [mem 0x5fc00000-0xfeafffff]
[    0.484178] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.484179] pci_bus 0000:01: resource 1 [mem 0xdc000000-0xdd0fffff]
[    0.484180] pci_bus 0000:01: resource 2 [mem 0xb0000000-0xc1ffffff 64bit pref]
[    0.484181] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.484182] pci_bus 0000:02: resource 1 [mem 0x5fc00000-0x5fdfffff]
[    0.484183] pci_bus 0000:02: resource 2 [mem 0x5fe00000-0x5fffffff 64bit pref]
[    0.484184] pci_bus 0000:03: resource 1 [mem 0xdd200000-0xdd4fffff]
[    0.484186] pci_bus 0000:04: resource 0 [io  0xd000-0xdfff]
[    0.484187] pci_bus 0000:04: resource 1 [mem 0xdd500000-0xdd5fffff]
[    0.484188] pci_bus 0000:05: resource 0 [io  0x3000-0x3fff]
[    0.484189] pci_bus 0000:05: resource 1 [mem 0xc4000000-0xdbffffff]
[    0.484190] pci_bus 0000:05: resource 2 [mem 0x80000000-0xafffffff 64bit pref]
[    0.484207] NET: Registered protocol family 2
[    0.484332] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.484484] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.484598] TCP: Hash tables configured (established 131072 bind 65536)
[    0.484612] TCP: reno registered
[    0.484628] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.484672] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.484739] NET: Registered protocol family 1
[    0.484934] pci 0000:01:00.0: Boot video device
[    0.484947] pci 0000:04:00.0: set MSI_INTX_DISABLE_BUG flag
[    0.484950] PCI: CLS 64 bytes, default 64
[    0.484988] Trying to unpack rootfs image as initramfs...
[    0.687305] Freeing initrd memory: 18644K (ffff880035b86000 - ffff880036dbb000)
[    0.687319] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.687321] software IO TLB [mem 0x47b38000-0x4bb38000] (64MB) mapped at [ffff880047b38000-ffff88004bb37fff]
[    0.687507] microcode: CPU0 sig=0x306c3, pf=0x20, revision=0x8
[    0.687512] microcode: CPU1 sig=0x306c3, pf=0x20, revision=0x8
[    0.687516] microcode: CPU2 sig=0x306c3, pf=0x20, revision=0x8
[    0.687521] microcode: CPU3 sig=0x306c3, pf=0x20, revision=0x8
[    0.687525] microcode: CPU4 sig=0x306c3, pf=0x20, revision=0x8
[    0.687530] microcode: CPU5 sig=0x306c3, pf=0x20, revision=0x8
[    0.687534] microcode: CPU6 sig=0x306c3, pf=0x20, revision=0x8
[    0.687539] microcode: CPU7 sig=0x306c3, pf=0x20, revision=0x8
[    0.687569] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.687571] Scanning for low memory corruption every 60 seconds
[    0.687744] Initialise system trusted keyring
[    0.687771] audit: initializing netlink socket (disabled)
[    0.687778] type=2000 audit(1401986378.480:1): initialized
[    0.706219] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.707128] zbud: loaded
[    0.707223] VFS: Disk quotas dquot_6.5.2
[    0.707247] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.707484] fuse init (API version 7.22)
[    0.707526] msgmni has been set to 31927
[    0.707555] Key type big_key registered
[    0.707915] Key type asymmetric registered
[    0.707916] Asymmetric key parser 'x509' registered
[    0.707932] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.707969] io scheduler noop registered
[    0.707970] io scheduler deadline registered (default)
[    0.707983] io scheduler cfq registered
[    0.708108] pcieport 0000:00:01.0: irq 41 for MSI/MSI-X
[    0.708426] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.708434] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.708458] efifb: probing for efifb
[    0.708630] efifb: framebuffer at 0xc1000000, mapped to 0xffffc90009c00000, using 1920k, total 1920k
[    0.708631] efifb: mode is 800x600x32, linelength=3200, pages=1
[    0.708631] efifb: scrolling: redraw
[    0.708632] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.709419] Console: switching to colour frame buffer device 100x37
[    0.710153] fb0: EFI VGA frame buffer device
[    0.710160] intel_idle: MWAIT substates: 0x42120
[    0.710161] intel_idle: v0.4 model 0x3C
[    0.710162] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.710273] ipmi message handler version 39.2
[    0.710332] ACPI: AC Adapter [AC0] (on-line)
[    0.710403] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.711696] ACPI: Lid Switch [LID]
[    0.711717] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.711720] ACPI: Sleep Button [SLPB]
[    0.711736] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.711738] ACPI: Power Button [PWRF]
[    0.712184] thermal LNXTHERM:00: registered as thermal_zone0
[    0.712185] ACPI: Thermal Zone [THRM] (63 C)
[    0.712203] GHES: HEST is not enabled!
[    0.712248] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.713304] Linux agpgart interface v0.103
[    0.714198] brd: module loaded
[    0.714615] loop: module loaded
[    0.714825] libphy: Fixed MDIO Bus: probed
[    0.714870] tun: Universal TUN/TAP device driver, 1.6
[    0.714871] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.714931] PPP generic driver version 2.4.2
[    0.714959] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.714961] ehci-pci: EHCI PCI platform driver
[    0.714966] ehci-platform: EHCI generic platform driver
[    0.714970] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.714970] ohci-pci: OHCI PCI platform driver
[    0.714975] ohci-platform: OHCI generic platform driver
[    0.714978] uhci_hcd: USB Universal Host Controller Interface driver
[    0.715066] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.715071] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[    0.715187] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.715205] xhci_hcd 0000:00:14.0: irq 42 for MSI/MSI-X
[    0.715264] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.715265] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.715266] usb usb1: Product: xHCI Host Controller
[    0.715267] usb usb1: Manufacturer: Linux 3.13.0-27-generic xhci_hcd
[    0.715268] usb usb1: SerialNumber: 0000:00:14.0
[    0.715346] hub 1-0:1.0: USB hub found
[    0.715371] hub 1-0:1.0: 14 ports detected
[    0.717568] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.717570] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
[    0.717602] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
[    0.717603] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.717604] usb usb2: Product: xHCI Host Controller
[    0.717605] usb usb2: Manufacturer: Linux 3.13.0-27-generic xhci_hcd
[    0.717606] usb usb2: SerialNumber: 0000:00:14.0
[    0.717659] hub 2-0:1.0: USB hub found
[    0.717679] hub 2-0:1.0: 6 ports detected
[    0.728453] i8042: PNP: PS/2 Controller [PNP030b:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.730740] ACPI: Battery Slot [BAT0] (battery present)
[    0.733763] i8042: Detected active multiplexing controller, rev 1.1
[    0.735169] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.735173] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.735188] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.735196] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.735205] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.735376] mousedev: PS/2 mouse device common for all mice
[    0.735554] rtc_cmos 00:06: RTC can wake from S4
[    0.735679] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.735704] rtc_cmos 00:06: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.735735] device-mapper: uevent: version 1.0.3
[    0.735785] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.735789] ledtrig-cpu: registered to indicate activity on CPUs
[    0.735790] EFI Variables Facility v0.08 2004-May-17
[    0.737905] TCP: cubic registered
[    0.737950] NET: Registered protocol family 10
[    0.738047] NET: Registered protocol family 17
[    0.738053] Key type dns_resolver registered
[    0.738276] Loading compiled-in X.509 certificates
[    0.738868] Loaded X.509 cert 'Magrathea: Glacier signing key: 23984ac203784325ccf7b95b51f6c119380eb933'
[    0.738884] registered taskstats version 1
[    0.741383] Key type trusted registered
[    0.743675] Key type encrypted registered
[    0.745936] AppArmor: AppArmor sha1 policy hashing enabled
[    0.745939] IMA: No TPM chip found, activating TPM-bypass!
[    0.746315] regulator-dummy: disabling
[    0.746471]   Magic number: 2:205:691
[    0.746595] rtc_cmos 00:06: setting system clock to 2014-06-05 16:39:39 UTC (1401986379)
[    0.747850] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.747852] EDD information not available.
[    0.747899] PM: Hibernation image not present or could not be loaded.
[    0.748515] Freeing unused kernel memory: 1332K (ffffffff81d1f000 - ffffffff81e6c000)
[    0.748516] Write protecting the kernel read-only data: 12288k
[    0.749966] Freeing unused kernel memory: 828K (ffff880002731000 - ffff880002800000)
[    0.751062] Freeing unused kernel memory: 700K (ffff880002b51000 - ffff880002c00000)
[    0.762355] systemd-udevd[142]: starting version 204
[    0.775789] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.780003] ahci 0000:00:1f.2: version 3.0
[    0.780100] ahci 0000:00:1f.2: irq 43 for MSI/MSI-X
[    0.780137] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x14 impl SATA mode
[    0.780138] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[    0.786940] scsi0 : ahci
[    0.787023] scsi1 : ahci
[    0.787090] scsi2 : ahci
[    0.787154] scsi3 : ahci
[    0.787225] scsi4 : ahci
[    0.787284] scsi5 : ahci
[    0.787307] ata1: DUMMY
[    0.787308] ata2: DUMMY
[    0.787309] ata3: SATA max UDMA/133 abar m2048@0xdd616000 port 0xdd616200 irq 43
[    0.787310] ata4: DUMMY
[    0.787312] ata5: SATA max UDMA/133 abar m2048@0xdd616000 port 0xdd616300 irq 43
[    0.787313] ata6: DUMMY
[    0.790626] alx 0000:04:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [ac:22:0b:ab:fb:0b]
[    1.026843] usb 1-1: new low-speed USB device number 2 using xhci_hcd
[    1.047845] usb 1-1: New USB device found, idVendor=1050, idProduct=0010
[    1.047849] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.047851] usb 1-1: Product: Yubico Yubikey II
[    1.047852] usb 1-1: Manufacturer: Yubico
[    1.047972] usb 1-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[    1.050656] hidraw: raw HID events driver (C) Jiri Kosina
[    1.054232] usbcore: registered new interface driver usbhid
[    1.054234] usbhid: USB HID core driver
[    1.056193] input: Yubico Yubico Yubikey II as /devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/input/input12
[    1.056270] hid-generic 0003:1050:0010.0001: input,hidraw0: USB HID v1.11 Keyboard [Yubico Yubico Yubikey II] on usb-0000:00:14.0-1/input0
[    1.106900] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.106919] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.111064] ata3.00: ATAPI: Slimtype DVD A  DS8A9SH, EAA2, max UDMA/100
[    1.112647] ata3.00: configured for UDMA/100
[    1.113551] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.113555] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.113557] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.119972] ata5.00: ATA-8: ST1000LM024 HN-M101MBB, 2AR20002, max UDMA/133
[    1.119975] ata5.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.123735] scsi 2:0:0:0: CD-ROM            Slimtype DVD A  DS8A9SH   EAA2 PQ: 0 ANSI: 5
[    1.126644] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    1.126647] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    1.126650] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    1.133051] ata5.00: configured for UDMA/133
[    1.137249] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.137253] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.137403] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.137483] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.137687] scsi 4:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2AR2 PQ: 0 ANSI: 5
[    1.137827] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    1.137833] sd 4:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.137836] sd 4:0:0:0: [sda] 4096-byte physical blocks
[    1.137973] sd 4:0:0:0: [sda] Write Protect is off
[    1.137977] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.138038] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.201407]  sda: sda1 sda2 sda3 sda4
[    1.202025] sd 4:0:0:0: [sda] Attached SCSI disk
[    1.287031] usb 1-4: new full-speed USB device number 3 using xhci_hcd
[    1.305708] usb 1-4: New USB device found, idVendor=046d, idProduct=c52b
[    1.305711] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.305713] usb 1-4: Product: USB Receiver
[    1.305715] usb 1-4: Manufacturer: Logitech
[    1.312680] logitech-djreceiver 0003:046D:C52B.0004: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:14.0-4/input2
[    1.435287] input: Logitech Unifying Device. Wireless PID:4002 as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/0003:046D:C52B.0004/input/input13
[    1.435413] logitech-djdevice 0003:046D:C52B.0005: input,hidraw2: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:4002] on usb-0000:00:14.0-4:1
[    1.437117] input: Logitech Unifying Device. Wireless PID:4013 as /devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.2/0003:046D:C52B.0004/input/input14
[    1.437278] logitech-djdevice 0003:046D:C52B.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:4013] on usb-0000:00:14.0-4:2
[    1.475208] usb 1-5: new full-speed USB device number 4 using xhci_hcd
[    1.494106] usb 1-5: New USB device found, idVendor=13d3, idProduct=3404
[    1.494110] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.494112] usb 1-5: Product: BCM20702A0
[    1.494113] usb 1-5: Manufacturer: Broadcom Corp
[    1.494115] usb 1-5: SerialNumber: 240A6407CF42
[    1.526806] psmouse serio4: elantech: assuming hardware version 4 (with firmware version 0x360f00)
[    1.542261] psmouse serio4: elantech: Synaptics capabilities query result 0x00, 0x16, 0x0c.
[    1.615747] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio4/input/input11
[    1.659353] usb 1-7: new high-speed USB device number 5 using xhci_hcd
[    1.687339] tsc: Refined TSC clocksource calibration: 2394.455 MHz
[    1.780914] usb 1-7: New USB device found, idVendor=13d3, idProduct=5188
[    1.780917] usb 1-7: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    1.780919] usb 1-7: Product: USB2.0 UVC HD Webcam
[    1.780920] usb 1-7: Manufacturer: Azurewave
[    1.780921] usb 1-7: SerialNumber: NULL
[    2.014324] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.014327] EXT4-fs (sda1): write access will be enabled during recovery
[    2.103552] random: nonblocking pool is initialized
[    2.688298] Switched to clocksource tsc
[    2.702244] EXT4-fs (sda1): recovery complete
[    2.723309] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   12.325302] Adding 38773756k swap on /dev/sda4.  Priority:-1 extents:1 across:38773756k FS
[   12.378226] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.438456] systemd-udevd[350]: starting version 204
[   12.585646] lp: driver loaded but no devices found
[   12.589287] ppdev: user-space parallel port driver
[   12.597406] [drm] Initialized drm 1.1.0 20060810
[   12.597882] mei_me 0000:00:16.0: irq 44 for MSI/MSI-X
[   12.601486] nvidia: module license 'NVIDIA' taints kernel.
[   12.601490] Disabling lock debugging due to kernel taint
[   12.605148] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   12.606540] wmi: Mapper loaded
[   12.608735] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   12.612382] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   12.613143] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   12.613149] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.38  Wed Jan  8 19:32:30 PST 2014
[   12.630805] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \GPIS 1 (20131115/utaddress-251)
[   12.630811] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 2 (20131115/utaddress-251)
[   12.630815] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.630818] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   12.630821] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GP01 2 (20131115/utaddress-251)
[   12.630824] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 3 (20131115/utaddress-251)
[   12.630827] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.630828] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   12.630831] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GP01 2 (20131115/utaddress-251)
[   12.630834] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 3 (20131115/utaddress-251)
[   12.630837] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.630838] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   12.634655] cfg80211: Calling CRDA to update world regulatory domain
[   12.635682] lib80211: common routines for IEEE802.11 drivers
[   12.635685] lib80211_crypt: registered algorithm 'NULL'
[   12.644614] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   12.658537] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   12.658914] SKU: Nid=0x1d sku_cfg=0x4127bd05
[   12.658917] SKU: port_connectivity=0x1
[   12.658918] SKU: enable_pcbeep=0x0
[   12.658919] SKU: check_sum=0x00000007
[   12.658920] SKU: customization=0x000000bd
[   12.658921] SKU: external_amp=0x0
[   12.658922] SKU: platform_type=0x1
[   12.658923] SKU: swap=0x0
[   12.658924] SKU: override=0x1
[   12.659217] autoconfig: line_outs=2 (0x17/0x14/0x0/0x0/0x0) type:speaker
[   12.659219]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   12.659220]    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[   12.659222]    mono: mono_out=0x0
[   12.659223]    dig-out=0x1e/0x0
[   12.659224]    inputs:
[   12.659225]      Mic=0x18
[   12.659227]      Internal Mic=0x12
[   12.659228] realtek: No valid SSID, checking pincfg 0x4127bd05 for NID 0x1d
[   12.659230] realtek: Enabling init ASM_ID=0xbd05 CODEC_ID=10ec0282
[   12.661730] lib80211_crypt: registered algorithm 'TKIP'
[   12.665094] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   12.667804] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   12.668008] hda_intel: Disabling MSI
[   12.668013] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   12.668043] hda-intel 0000:01:00.1: Disabling 64bit DMA
[   12.672055] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[   12.700315] acpi device:5f: registered as cooling_device9
[   12.705676] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   12.737260] Linux video capture interface: v2.00
[   12.743649] uvcvideo: Found UVC 1.00 device USB2.0 UVC HD Webcam (13d3:5188)
[   12.747546] type=1400 audit(1401986391.485:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=734 comm="apparmor_parser"
[   12.747553] type=1400 audit(1401986391.485:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=734 comm="apparmor_parser"
[   12.747557] type=1400 audit(1401986391.485:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=734 comm="apparmor_parser"
[   12.747965] type=1400 audit(1401986391.485:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=734 comm="apparmor_parser"
[   12.747970] type=1400 audit(1401986391.485:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=734 comm="apparmor_parser"
[   12.748178] type=1400 audit(1401986391.485:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=734 comm="apparmor_parser"
[   12.749027] input: USB2.0 UVC HD Webcam as /devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input17
[   12.749160] usbcore: registered new interface driver uvcvideo
[   12.749162] USB Video Class driver (1.1.1)
[   12.749704] type=1400 audit(1401986391.489:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=769 comm="apparmor_parser"
[   12.749708] type=1400 audit(1401986391.489:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=769 comm="apparmor_parser"
[   12.749711] type=1400 audit(1401986391.489:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=769 comm="apparmor_parser"
[   12.749750] type=1400 audit(1401986391.489:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=818 comm="apparmor_parser"
[   12.770665] cfg80211: World regulatory domain updated:
[   12.770668] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.770669] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.770671] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.770673] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   12.770674] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.770676] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.780341] acpi device:62: registered as cooling_device10
[   12.780391] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:5c/LNXVIDEO:00/input/input18
[   12.783364] asus_wmi: ASUS WMI generic driver loaded
[   12.784162] asus_wmi: Initialization: 0x1
[   12.784190] asus_wmi: BIOS WMI version: 7.9
[   12.784213] asus_wmi: SFUN value: 0x4a0877
[   12.784850] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input19
[   12.792935] asus_wmi: Backlight controlled by ACPI video driver
[   12.799893] alx 0000:04:00.0: irq 46 for MSI/MSI-X
[   12.799946] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.800719] alx 0000:04:00.0 eth0: NIC Up: 100 Mbps Full
[   12.800934] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   13.072567] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input21
[   13.072665] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input20
[   14.386646] init: udev-fallback-graphics main process (1355) terminated with status 1
[   14.794064] EXT4-fs (sda1): re-mounted. Opts: discard,errors=remount-ro
[   29.199628] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   29.848036] init: failsafe main process (1457) killed by TERM signal
[   30.140406] Bluetooth: Core ver 2.17
[   30.140416] NET: Registered protocol family 31
[   30.140417] Bluetooth: HCI device and connection manager initialized
[   30.140423] Bluetooth: HCI socket layer initialized
[   30.140424] Bluetooth: L2CAP socket layer initialized
[   30.140426] Bluetooth: SCO socket layer initialized
[   30.142241] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.142243] Bluetooth: BNEP filters: protocol multicast
[   30.142248] Bluetooth: BNEP socket layer initialized
[   30.142625] Bluetooth: RFCOMM TTY layer initialized
[   30.142629] Bluetooth: RFCOMM socket layer initialized
[   30.142632] Bluetooth: RFCOMM ver 1.11
[   30.181264] audit_printk_skb: 24 callbacks suppressed
[   30.181266] type=1400 audit(1401986408.905:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1601 comm="apparmor_parser"
[   30.181270] type=1400 audit(1401986408.905:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1601 comm="apparmor_parser"
[   30.181535] type=1400 audit(1401986408.905:22): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1601 comm="apparmor_parser"
[   30.422130] type=1400 audit(1401986409.145:23): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1629 comm="apparmor_parser"
[   30.422944] type=1400 audit(1401986409.149:24): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=1624 comm="apparmor_parser"
[   30.422950] type=1400 audit(1401986409.149:25): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=1624 comm="apparmor_parser"
[   30.423000] type=1400 audit(1401986409.149:26): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1625 comm="apparmor_parser"
[   30.423006] type=1400 audit(1401986409.149:27): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1625 comm="apparmor_parser"
[   30.423010] type=1400 audit(1401986409.149:28): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1625 comm="apparmor_parser"
[   30.423200] type=1400 audit(1401986409.149:29): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=1624 comm="apparmor_parser"
[   30.439219] init: cups main process (1602) killed by HUP signal
[   30.439227] init: cups main process ended, respawning
[   30.649705] init: anacron main process (1692) terminated with status 1

```


Here is the result of lspci:

```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d4)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
03:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)
04:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)

```


Here are my complete hardware specs:

```

id:    
vineel-g750jw
description:     Notebook
product:     G750JW (ASUS-NotebookSKU)
vendor:     ASUSTeK COMPUTER INC.
version:     1.0
serial:     D7N0CY58461529D
width:     64 bits
capabilities:     smbios-2.7 dmi-2.7 vsyscall32
configuration:    
boot    =    normal
chassis    =    notebook
family    =    G
sku    =    ASUS-NotebookSKU
uuid    =    7ECCBCBE-AB4D-A0F0-89A7-AC220BABFB0B
id:    
core
description:     Motherboard
product:     G750JW
vendor:     ASUSTeK COMPUTER INC.
physical id:     
0
version:     1.0
serial:     BSN12345678901234567
slot:     MIDDLE
id:    
firmware
description:     BIOS
vendor:     American Megatrends Inc.
physical id:     
0
version:     G750JW.207
date:     05/23/2013
size:     64KiB
capacity:     6080KiB
capabilities:     pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification uefi
id:    
cpu
description:     CPU
product:     Intel(R) Core(TM) i7-4700HQ CPU @ 2.40GHz
vendor:     Intel Corp.
physical id:     
8
bus info:     
cpu@0
version:     Intel(R) Core(TM) i7-4700HQ CPU @ 2.40GHz
slot:     SOCKET 0
size:     800MHz
capacity:     3800MHz
width:     64 bits
clock:     100MHz
capabilities:     x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cpufreq
configuration:    
cores    =    4
enabledcores    =    4
threads    =    8
id:    
cache:0
description:     L2 cache
physical id:     
9
slot:     CPU Internal L2
size:     1MiB
capacity:     1MiB
capabilities:     internal write-back unified
id:    
cache:1
description:     L1 cache
physical id:     
a
slot:     CPU Internal L1
size:     256KiB
capacity:     256KiB
capabilities:     internal write-back
id:    
cache:2
description:     L3 cache
physical id:     
b
slot:     CPU Internal L3
size:     6MiB
capacity:     6MiB
capabilities:     internal write-back unified
id:    
memory
description:     System Memory
physical id:     
c
slot:     System board or motherboard
size:     16GiB
id:    
bank:0
description:     DIMM [empty]
product:     [Empty]
vendor:     [Empty]
physical id:     
0
serial:     [Empty]
slot:     ChannelA-DIMM0
id:    
bank:1
description:     SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product:     M471B5173BH0-YK0
vendor:     Samsung
physical id:     
1
serial:     15211033
slot:     ChannelA-DIMM1
size:     4GiB
width:     64 bits
clock:     1600MHz (0.6ns)
id:    
bank:2
description:     SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
vendor:     AMD
physical id:     
2
serial:     00000000
slot:     ChannelB-DIMM0
size:     8GiB
width:     64 bits
clock:     1600MHz (0.6ns)
id:    
bank:3
description:     SODIMM DDR3 Synchronous 1600 MHz (0.6 ns)
product:     M471B5173BH0-YK0
vendor:     Samsung
physical id:     
3
serial:     15211019
slot:     ChannelB-DIMM1
size:     4GiB
width:     64 bits
clock:     1600MHz (0.6ns)
id:    
pci
description:     Host bridge
product:     Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller
vendor:     Intel Corporation
physical id:     
100
bus info:     
pci@0000:00:00.0
version:     06
width:     32 bits
clock:     33MHz
id:    
pci:0
description:     PCI bridge
product:     Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller
vendor:     Intel Corporation
physical id:     
1
bus info:     
pci@0000:00:01.0
version:     06
width:     32 bits
clock:     33MHz
capabilities:     pci pm msi pciexpress normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    41
ioport    :    e000(size=4096)
memory    :    dc000000-dd0fffff
ioport    :    b0000000(size=301989888)
id:    
display
description:     VGA compatible controller
product:     GK106M [GeForce GTX 765M]
vendor:     NVIDIA Corporation
physical id:     
0
bus info:     
pci@0000:01:00.0
version:     a1
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress vga_controller bus_master cap_list rom
configuration:    
driver    =    nvidia
latency    =    0
resources:    
irq    :    47
memory    :    dc000000-dcffffff
memory    :    b0000000-bfffffff
memory    :    c0000000-c1ffffff
ioport    :    e000(size=128)
memory    :    dd000000-dd07ffff
id:    
multimedia
description:     Audio device
product:     GK106 HDMI Audio Controller
vendor:     NVIDIA Corporation
physical id:     
0.1
bus info:     
pci@0000:01:00.1
version:     a1
width:     32 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list
configuration:    
driver    =    snd_hda_intel
latency    =    0
resources:    
irq    :    17
memory    :    dd080000-dd083fff
id:    
usb
description:     USB controller
product:     8 Series/C220 Series Chipset Family USB xHCI
vendor:     Intel Corporation
physical id:     
14
bus info:     
pci@0000:00:14.0
version:     04
width:     64 bits
clock:     33MHz
capabilities:     pm msi xhci bus_master cap_list
configuration:    
driver    =    xhci_hcd
latency    =    0
resources:    
irq    :    42
memory    :    dd600000-dd60ffff
id:    
communication
description:     Communication controller
product:     8 Series/C220 Series Chipset Family MEI Controller #1
vendor:     Intel Corporation
physical id:     
16
bus info:     
pci@0000:00:16.0
version:     04
width:     64 bits
clock:     33MHz
capabilities:     pm msi bus_master cap_list
configuration:    
driver    =    mei_me
latency    =    0
resources:    
irq    :    44
memory    :    dd618000-dd61800f
id:    
multimedia
description:     Audio device
product:     8 Series/C220 Series Chipset High Definition Audio Controller
vendor:     Intel Corporation
physical id:     
1b
bus info:     
pci@0000:00:1b.0
version:     04
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list
configuration:    
driver    =    snd_hda_intel
latency    =    0
resources:    
irq    :    45
memory    :    dd610000-dd613fff
id:    
pci:1
description:     PCI bridge
product:     8 Series/C220 Series Chipset Family PCI Express Root Port #1
vendor:     Intel Corporation
physical id:     
1c
bus info:     
pci@0000:00:1c.0
version:     d4
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    16
ioport    :    2000(size=4096)
memory    :    5fc00000-5fdfffff
ioport    :    5fe00000(size=2097152)
id:    
pci:2
description:     PCI bridge
product:     8 Series/C220 Series Chipset Family PCI Express Root Port #3
vendor:     Intel Corporation
physical id:     
1c.2
bus info:     
pci@0000:00:1c.2
version:     d4
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    18
memory    :    dd200000-dd4fffff
id:    
network
description:     Wireless interface
product:     BCM4352 802.11ac Wireless Network Adapter
vendor:     Broadcom Corporation
physical id:     
0
bus info:     
pci@0000:03:00.0
logical name:     
wlan0
version:     03
serial:     24:0a:64:3a:67:31
width:     64 bits
clock:     33MHz
capabilities:     pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:    
broadcast    =    yes
driver    =    wl0
driverversion    =    6.30.223.141 (r415941)
ip    =    10.203.73.158
latency    =    0
multicast    =    yes
wireless    =    IEEE 802.11abg
resources:    
irq    :    18
memory    :    dd400000-dd407fff
memory    :    dd200000-dd3fffff
id:    
pci:3
description:     PCI bridge
product:     8 Series/C220 Series Chipset Family PCI Express Root Port #4
vendor:     Intel Corporation
physical id:     
1c.3
bus info:     
pci@0000:00:1c.3
version:     d4
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    19
ioport    :    d000(size=4096)
memory    :    dd500000-dd5fffff
id:    
network
description:     Ethernet interface
product:     QCA8171 Gigabit Ethernet
vendor:     Qualcomm Atheros
physical id:     
0
bus info:     
pci@0000:04:00.0
logical name:     
eth0
version:     10
serial:     ac:22:0b:ab:fb:0b
capacity:     1Gbit/s
width:     64 bits
clock:     33MHz
capabilities:     pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration:    
autonegotiation    =    on
broadcast    =    yes
driver    =    alx
latency    =    0
link    =    no
multicast    =    yes
port    =    twisted pair
resources:    
irq    :    46
memory    :    dd500000-dd53ffff
ioport    :    d000(size=128)
id:    
pci:4
description:     PCI bridge
product:     8 Series/C220 Series Chipset Family PCI Express Root Port #5
vendor:     Intel Corporation
physical id:     
1c.4
bus info:     
pci@0000:00:1c.4
version:     d4
width:     32 bits
clock:     33MHz
capabilities:     pci pciexpress msi pm normal_decode bus_master cap_list
configuration:    
driver    =    pcieport
resources:    
irq    :    16
ioport    :    3000(size=4096)
memory    :    c4000000-dbffffff
ioport    :    80000000(size=805306368)
id:    
isa
description:     ISA bridge
product:     HM87 Express LPC Controller
vendor:     Intel Corporation
physical id:     
1f
bus info:     
pci@0000:00:1f.0
version:     04
width:     32 bits
clock:     33MHz
capabilities:     isa bus_master cap_list
configuration:    
driver    =    lpc_ich
latency    =    0
resources:    
irq    :    0
id:    
storage
description:     SATA controller
product:     8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode]
vendor:     Intel Corporation
physical id:     
1f.2
bus info:     
pci@0000:00:1f.2
version:     04
width:     32 bits
clock:     66MHz
capabilities:     storage msi pm ahci_1.0 bus_master cap_list
configuration:    
driver    =    ahci
latency    =    0
resources:    
irq    :    43
ioport    :    f070(size=8)
ioport    :    f060(size=4)
ioport    :    f050(size=8)
ioport    :    f040(size=4)
ioport    :    f020(size=32)
memory    :    dd616000-dd6167ff
id:    
serial
description:     SMBus
product:     8 Series/C220 Series Chipset Family SMBus Controller
vendor:     Intel Corporation
physical id:     
1f.3
bus info:     
pci@0000:00:1f.3
version:     04
width:     64 bits
clock:     33MHz
configuration:    
latency    =    0
resources:    
memory    :    dd615000-dd6150ff
ioport    :    f000(size=32)
id:    
scsi:0
physical id:     
1
logical name:     
scsi2
capabilities:     emulated
id:    
cdrom
description:     DVD-RAM writer
product:     DVD A DS8A9SH
vendor:     Slimtype
physical id:     
0.0.0
bus info:     
scsi@2:0.0.0
logical name:     
/dev/cdrom
logical name:     
/dev/sr0
version:     EAA2
capabilities:     removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration:    
ansiversion    =    5
status    =    nodisc
id:    
scsi:1
physical id:     
2
logical name:     
scsi4
capabilities:     emulated
id:    
disk
description:     ATA Disk
product:     ST1000LM024 HN-M
vendor:     Seagate
physical id:     
0.0.0
bus info:     
scsi@4:0.0.0
logical name:     
/dev/sda
version:     2AR2
serial:     S2Y4J9AD604481
size:     931GiB (1TB)
capabilities:     gpt-1.00 partitioned partitioned:gpt
configuration:    
ansiversion    =    5
guid    =    28f7f69a-6ea8-4c31-9347-498294b77bb4
sectorsize    =    4096
id:    
volume:0
description:     EXT4 volume
vendor:     Linux
physical id:     
1
bus info:     
scsi@4:0.0.0,1
logical name:     
/dev/sda1
logical name:     
/
version:     1.0
serial:     98252a17-dd23-4bd9-a2b4-3b00dd3f0fb8
size:     93GiB
capabilities:     journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
configuration:    
created    =    2014-05-27 12:15:17
filesystem    =    ext4
lastmountpoint    =    /
modified    =    2014-05-31 15:17:57
mount.fstype    =    ext4
mount.options    =    rw,noatime,nodiratime,discard,errors=remount-ro,data=ordered
mounted    =    2014-06-01 13:40:43
state    =    mounted
id:    
volume:1
description:     EXT4 volume
vendor:     Linux
physical id:     
2
bus info:     
scsi@4:0.0.0,2
logical name:     
/dev/sda2
logical name:     
/home
version:     1.0
serial:     9592983e-8c64-4f68-95ab-c8a8e4592497
size:     800GiB
capabilities:     journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
configuration:    
created    =    2014-05-27 12:15:19
filesystem    =    ext4
lastmountpoint    =    /home
modified    =    2014-06-01 16:14:20
mount.fstype    =    ext4
mount.options    =    rw,relatime,data=ordered
mounted    =    2014-06-01 16:14:20
state    =    mounted
id:    
volume:2
description:     Windows FAT volume
vendor:     mkfs.fat
physical id:     
3
bus info:     
scsi@4:0.0.0,3
logical name:     
/dev/sda3
logical name:     
/boot/efi
version:     FAT32
serial:     3883-8063
size:     469MiB
capacity:     476MiB
capabilities:     boot fat initialized
configuration:    
FATs    =    2
filesystem    =    fat
mount.fstype    =    vfat
mount.options    =    rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
state    =    mounted
id:    
volume:3
description:     Linux swap volume
vendor:     Linux
physical id:     
4
bus info:     
scsi@4:0.0.0,4
logical name:     
/dev/sda4
version:     1
serial:     2894db67-189d-47f4-975f-cb98d68baeb3
size:     36GiB
capacity:     36GiB
capabilities:     nofs swap initialized
configuration:    
filesystem    =    swap
pagesize    =    4095

```

---

### Post by nadarockyraccoon on 2014-06-14
I would highly reccomend running a memtest. this can be found in the boot menu of almost all linux distros or live cd/flash menus. With ubuntu press escape on boot when you see press esc to load grub menu, or control+alt+delete during boot shoud force the grub menu on next boot, with the live image press escape when you see the little man equals keyboard and select memtest86. let it run until all test have 100% completed, no red lines is good ram, red error lines means it's bad, and that's your problem.

What you are describing does indeed sound like a kernel panic wich is likely caused by a bad secondary stick of ram. Usually if it's the primary ram slot you won't even make it through boot. Only way to know for sure is pulling the ram and replacing it if there is only one stick or running a memtest(best option since a lot of new laptops have the ram solders to the board, stupid). The other option would be a bad hard drive or sectors on the drive. Either way this is likely a hardware issue not software and ram sounds right as the proccesses you have described, flash player and matlab are both ram intensive. In my case I was able to pull the secondary stick and everything worked after that, run a memtest first though.

---

