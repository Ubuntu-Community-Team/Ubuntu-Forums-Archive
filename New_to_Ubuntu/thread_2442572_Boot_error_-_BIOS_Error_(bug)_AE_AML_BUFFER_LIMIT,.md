---
title: "Boot error - BIOS Error (bug): AE_AML_BUFFER_LIMIT, Field [CAP1] at bit offset/length"
date: 2020-05-04
forum: New to Ubuntu
---

### Post by sgryphon on 2020-05-04
I get some errors showing every time I boot, although everything seems to work.


This is a recent HP Z-Book Studio x360 Workstation G5 with NVidia Quadro P2000 (4GB), with i7-9850H, 32 GB RAM, running Ubuntu 20.04.

Doesn't really bother me, as everything seems to work, but it may be of interest to a developer to work out and fix the bug. Happy to help diagnostics etc if needed, [email]sly@gamertheory.net[/email].

Messages from journalctl -b


May 05 12:41:51 Nyjora kernel: ACPI: 22 ACPI AML tables successfully acquired and loaded
May 05 12:41:51 Nyjora kernel: ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
May 05 12:41:51 Nyjora kernel: ACPI: Dynamic OEM Table Load:
May 05 12:41:51 Nyjora kernel: ACPI: SSDT 0xFFFF89A1B7454900 0000F4 (v02 PmRef  Cpu0Psd  00003000 INTL 20160527)
May 05 12:41:51 Nyjora kernel: ACPI: \_SB_.PR00: _OSC native thermal LVT Acked
May 05 12:41:51 Nyjora kernel: ACPI BIOS Error (bug): AE_AML_BUFFER_LIMIT, Field [CAP1] at bit offset/length 64/32 exceeds size of target Buffer (64 bits) (20190816/dsopcode-198)
May 05 12:41:51 Nyjora kernel: fbcon: Taking over console
May 05 12:41:51 Nyjora kernel: No Local Variables are initialized for Method [_OSC]
May 05 12:41:51 Nyjora kernel: Initialized Arguments for Method [_OSC]:  (4 arguments defined for method invocation)
May 05 12:41:51 Nyjora kernel:   Arg0:   00000000a0bc87ac <Obj>           Buffer(16) 6E B0 11 08 27 4A F9 44
May 05 12:41:51 Nyjora kernel:   Arg1:   00000000e53125d3 <Obj>           Integer 0000000000000001
May 05 12:41:51 Nyjora kernel:   Arg2:   000000000c8d909c <Obj>           Integer 0000000000000002
May 05 12:41:51 Nyjora kernel:   Arg3:   000000008de722f4 <Obj>           Buffer(8) 01 00 00 00 FF 10 00 00
May 05 12:41:51 Nyjora kernel: ACPI Error: Aborting method \_SB._OSC due to previous error (AE_AML_BUFFER_LIMIT) (20190816/psparse-529)
May 05 12:41:51 Nyjora kernel: ACPI: Dynamic OEM Table Load:
May 05 12:41:51 Nyjora kernel: ACPI: SSDT 0xFFFF89A1B745AC00 000400 (v02 PmRef  Cpu0Cst  00003001 INTL 20160527)
May 05 12:41:51 Nyjora kernel: ACPI: Dynamic OEM Table Load:


...
Some other errors (may not be related; I don't see these in the boot screen)


May 05 12:41:51 Nyjora kernel: ACPI: Thermal Zone [LOCZ] (38 C)
May 05 12:41:51 Nyjora kernel: thermal LNXTHERM:05: registered as thermal_zone5
May 05 12:41:51 Nyjora kernel: ACPI: Thermal Zone [BATZ] (30 C)
May 05 12:41:51 Nyjora kernel: ACPI BIOS Error (bug): AE_AML_PACKAGE_LIMIT, Index (0x000000005) is beyond end of object (length 0x5) (20190816/exoparg2-393)
May 05 12:41:51 Nyjora kernel: 
                               Initialized Local Variables for Method [GETP]:
May 05 12:41:51 Nyjora kernel:   Local0: 00000000203efe8a <Obj>           Integer 0000000000000003
May 05 12:41:51 Nyjora kernel: Initialized Arguments for Method [GETP]:  (2 arguments defined for method invocation)
May 05 12:41:51 Nyjora kernel:   Arg0:   000000004be9d0d9 <Obj>           Integer 0000000000000005
May 05 12:41:51 Nyjora kernel:   Arg1:   000000004e4bdfc8 <Obj>           Integer 0000000000000003
May 05 12:41:51 Nyjora kernel: ACPI Error: Aborting method \_TZ.GETP due to previous error (AE_AML_PACKAGE_LIMIT) (20190816/psparse-529)
May 05 12:41:51 Nyjora kernel: ACPI Error: Aborting method \_TZ.CHGZ._CRT due to previous error (AE_AML_PACKAGE_LIMIT) (20190816/psparse-529)
May 05 12:41:51 Nyjora kernel: ACPI BIOS Error (bug): AE_AML_PACKAGE_LIMIT, Index (0x000000005) is beyond end of object (length 0x5) (20190816/exoparg2-393)
May 05 12:41:51 Nyjora kernel: 
                               Initialized Local Variables for Method [GETP]:
May 05 12:41:51 Nyjora kernel:   Local0: 000000004e4bdfc8 <Obj>           Integer 0000000000000003
May 05 12:41:51 Nyjora kernel: Initialized Arguments for Method [GETP]:  (2 arguments defined for method invocation)
May 05 12:41:51 Nyjora kernel:   Arg0:   000000004be9d0d9 <Obj>           Integer 0000000000000005
May 05 12:41:51 Nyjora kernel:   Arg1:   00000000a8987dca <Obj>           Integer 0000000000000003
May 05 12:41:51 Nyjora kernel: ACPI Error: Aborting method \_TZ.GETP due to previous error (AE_AML_PACKAGE_LIMIT) (20190816/psparse-529)
May 05 12:41:51 Nyjora kernel: ACPI Error: Aborting method \_TZ.CHGZ._CRT due to previous error (AE_AML_PACKAGE_LIMIT) (20190816/psparse-529)
May 05 12:41:51 Nyjora kernel: [Firmware Bug]: No valid trip found
May 05 12:41:51 Nyjora kernel: thermal LNXTHERM:07: registered as thermal_zone6
May 05 12:41:51 Nyjora kernel: ACPI: Thermal Zone [PCHZ] (0 C)
May 05 12:41:51 Nyjora kernel: Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled

---

### Post by dino99 on 2020-05-05
Request a bios upgrade (if not yet available) via hp support
You can also report againt 'linux' to get a fixed kernel related to that acpi problem

[https://bugzilla.kernel.org/](https://bugzilla.kernel.org/)

---

