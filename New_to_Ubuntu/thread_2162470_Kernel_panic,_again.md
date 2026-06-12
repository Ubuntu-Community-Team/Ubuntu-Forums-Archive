---
title: "Kernel panic, again"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by raen on 2013-07-14
I had a kernel panic the evening of Wednesday, July 10, and I had another kernel panic this afternoon, Sunday July 14.

Some rather lengthy cut-and-pastes from today follow. Any help would be appreciated.

Thanks.

====THE BLACK SCREEN OF DOOM====
```

[14691.411158]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
[14691.411299] CR0: 8005003b CR2: 00000000 CR3: 26a73000 CR4: 000007f0
[14691.411344] DR0: 00000000 DR1: 00000000 DR2: 00000000 DR3: 00000000
[14691.411344] DR6: ffff0ff0 DR7: 00000400
[14691.411344] Process swapper/1 (pid: 0, ti=f5cda000 task=f5cb99a0 task.ti=f5cb6000)
[14691.411344] Stack:
[14691.411344]  f5d433ff 0000b64c 00004188 f1546e01 f1580000 00000005 4101befc 00000002
[14691.411344]  f5cdbf48 f1546e0a f2590000 00004573 f6bf3900 f17e2000 f6bf3901 00000000
[14691.411344]  f36b2600 f6817800 f5cdbf7f f5cdbf64 f8cd7327 612d4573 f8698174 f8698170
[14691.411344] Call Trace:
[14691.411344]  [<f8cd7327>] wlc_bmac_txstatus+0x182/0x1e8 [w1]
[14691.411344]  [<f8cdb4ee>] wlc_dpc+0x79/0x287 [w1]
[14691.411344]  [<f8d70389>] wl_dpc+0x49/0xd0 [w1]
[14691.411344]  [<c10529a3>] tasklet_action+0x53/0xb0
[14691.411344]  [<c10525c3>] __do_softirq+0xa3/0x1b0
[14691.411344]  [<c1052520>] ? local_bh_enable+0x90/0x90
[14691.411344]  [<c1052520>] ? local_bh_enable+0x90/0x90
[14691.411344]  <IRQ>
[14691.411344]  [<c1052835>] ? irq_exit+0x95/0xa0
[14691.411344]  [<c161afbb>] ? do_IRQ+0x4b/0xc0
[14691.411344]  [<c10a250e>] ? tick_nohz_stop_idle+0x3e/0x50
[14691.411344]  [<c161adb3>] ? common_interrupt+0x33/0x38
[14691.411344]  [<c101007b>] ? hweight_long+0xb/0x10
[14691.411344]  [<c1078df4>] ? finish_task_switch+0x44/0xc0
[14691.411344]  [<c1612120>] ? __schedule+0x360/0x780
[14691.411344]  [<c10701d6>] ? hrtimer_start_range_ns+0x26/0x30
[14691.411344]  [<c10a29b7>] ? tick_nohz_idle_exit+0x117/0x190
[14691.411344]  [<c16127e3>] ? schedule+0x23/0x60
[14691.411344]  [<c101901a>] ? cpu_idle+0xda/0xe0
[14691.411344]  [<c160439d>] ? start_secondary+0x1d9/0x1df
[14691.411344] Code: 00 8b 53 04 8b 45 d4 89 55 c4 0f b7 40 02 83 e0 07 83 f8 05 89 45 c8 0f 87 09 07 00 00 8b 55 c8 8b 43 14 8b
 04 90 ba 02 00 00 00 <8b> 08 ff 51 34 89 45 e4 8b 03 8b 40 10 83 78 04 01 75 0f 80 7b
[14691.411344] EIP: [<f8c91c55>] wlc_dotxstatus+0x6a/0x781 [w1] SS:ESP 0068:f5cdbedc
[14691.411344] CR2: 0000000000000000
[14691.485811] Kernel panic - not syncing: Fatal exception in interrupt
[14691.488711] drm_kms_helper: panic occurred, switching back to text console

```
==== END BLACK SCREEN OF DOOM====

====COMMAND LINE OUTPUT====
```

$ uname -a
Linux blotter 3.8.0-26-generic #38-Ubuntu SMP Mon Jun 17 21:46:08 UTC 2013 i686 i686 i686 GNU/Linux




$ lspci -vv
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel


00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at 58280000 (32-bit, non-prefetchable) [size=512K]
    Region 1: I/O ports at 60f0 [size=8]
    Region 2: Memory at 40000000 (32-bit, prefetchable) [size=256M]
    Region 3: Memory at 58300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915


00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at 58200000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>


00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 45
    Region 0: Memory at 58340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel


00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 57100000-581fffff
    Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 56100000-570fffff
    Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00003fff
    Memory behind bridge: 55000000-560fffff
    Prefetchable memory behind bridge: 0000000052000000-0000000052ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 54000000-54ffffff
    Prefetchable memory behind bridge: 0000000053000000-0000000053ffffff
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at 60a0 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 4: I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 19
    Region 4: I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd


00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at 58344400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci-pci


00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: <access denied>


00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Capabilities: <access denied>
    Kernel driver in use: lpc_ich


00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 44
    Region 0: I/O ports at 60d8 [size=8]
    Region 1: I/O ports at 60fc [size=4]
    Region 2: I/O ports at 60d0 [size=8]
    Region 3: I/O ports at 60f8 [size=4]
    Region 4: I/O ports at 6020 [size=16]
    Region 5: Memory at 58344000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci


00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 11
    Region 4: I/O ports at 6000 [size=32]


01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
    Subsystem: Foxconn International, Inc. T77H106.00 Wireless Half-size Mini PCIe Card
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at 57100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl


03:00.0 Ethernet controller: Qualcomm Atheros AR8132 Fast Ethernet (rev c0)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 46
    Region 0: Memory at 55000000 (64-bit, non-prefetchable) [size=256K]
    Region 2: I/O ports at 2000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c

```
====END COMMAND LINE OUTPUT====



====TEXT OF kern.log====
```

Jul 14 16:09:18 blotter kernel: imklog 5.8.11, log source = /proc/kmsg started.
Jul 14 16:09:18 blotter kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 14 16:09:18 blotter kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 14 16:09:18 blotter kernel: [    0.000000] Linux version 3.8.0-26-generic (buildd@lamiak) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #38-Ubuntu SMP Mon Jun 17 21:46:08 UTC 2013 (Ubuntu 3.8.0-26.38-generic 3.8.13.2)
Jul 14 16:09:18 blotter kernel: [    0.000000] KERNEL supported cpus:
Jul 14 16:09:18 blotter kernel: [    0.000000]   Intel GenuineIntel
Jul 14 16:09:18 blotter kernel: [    0.000000]   AMD AuthenticAMD
Jul 14 16:09:18 blotter kernel: [    0.000000]   NSC Geode by NSC
Jul 14 16:09:18 blotter kernel: [    0.000000]   Cyrix CyrixInstead
Jul 14 16:09:18 blotter kernel: [    0.000000]   Centaur CentaurHauls
Jul 14 16:09:18 blotter kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 14 16:09:18 blotter kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 14 16:09:18 blotter kernel: [    0.000000]   UMC UMC UMC UMC
Jul 14 16:09:18 blotter kernel: [    0.000000] Disabled fast string operations
Jul 14 16:09:18 blotter kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003f575fff] usable
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f576000-0x000000003f5befff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f5bf000-0x000000003f66cfff] usable
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f66d000-0x000000003f6befff] ACPI NVS
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6bf000-0x000000003f6edfff] usable
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6ee000-0x000000003f6fefff] ACPI data
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6ff000-0x000000003f6fffff] usable
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f700000-0x000000003fffffff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 14 16:09:18 blotter kernel: [    0.000000] SMBIOS 2.4 present.
Jul 14 16:09:18 blotter kernel: [    0.000000] DMI: Acer       Aspire one      /Aspire one      , BIOS V1.22 10/14/2009
Jul 14 16:09:18 blotter kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Jul 14 16:09:18 blotter kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 14 16:09:18 blotter kernel: [    0.000000] e820: last_pfn = 0x3f700 max_arch_pfn = 0x1000000
Jul 14 16:09:18 blotter kernel: [    0.000000] MTRR default type: uncachable
Jul 14 16:09:18 blotter kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 14 16:09:18 blotter kernel: [    0.000000]   00000-9FFFF write-back
Jul 14 16:09:18 blotter kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 14 16:09:18 blotter kernel: [    0.000000]   C0000-C7FFF write-protect
Jul 14 16:09:18 blotter kernel: [    0.000000]   C8000-EFFFF uncachable
Jul 14 16:09:18 blotter kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 14 16:09:18 blotter kernel: [    0.000000] MTRR variable ranges enabled:
Jul 14 16:09:18 blotter kernel: [    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
Jul 14 16:09:18 blotter kernel: [    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
Jul 14 16:09:18 blotter kernel: [    0.000000]   2 base 000000000 mask 0E0000000 write-back
Jul 14 16:09:18 blotter kernel: [    0.000000]   3 base 020000000 mask 0E0000000 write-back
Jul 14 16:09:18 blotter kernel: [    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
Jul 14 16:09:18 blotter kernel: [    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
Jul 14 16:09:18 blotter kernel: [    0.000000]   6 disabled
Jul 14 16:09:18 blotter kernel: [    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
Jul 14 16:09:18 blotter kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 14 16:09:18 blotter kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Jul 14 16:09:18 blotter kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul 14 16:09:18 blotter kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Jul 14 16:09:18 blotter kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Jul 14 16:09:18 blotter kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Jul 14 16:09:18 blotter kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Jul 14 16:09:18 blotter kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Jul 14 16:09:18 blotter kernel: [    0.000000] RAMDISK: [mem 0x36030000-0x3700ffff]
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: DSDT 3f6f0000 070CA (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: FACS 3f688000 00040
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: SLIC 3f6ef000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: BOOT 3f6ee000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 14 16:09:18 blotter kernel: [    0.000000] 123MB HIGHMEM available.
Jul 14 16:09:18 blotter kernel: [    0.000000] 891MB LOWMEM available.
Jul 14 16:09:18 blotter kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jul 14 16:09:18 blotter kernel: [    0.000000]   low ram: 0 - 37bfe000
Jul 14 16:09:18 blotter kernel: [    0.000000] Zone ranges:
Jul 14 16:09:18 blotter kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Jul 14 16:09:18 blotter kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Jul 14 16:09:18 blotter kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0x3f6fffff]
Jul 14 16:09:18 blotter kernel: [    0.000000] Movable zone start for each node
Jul 14 16:09:18 blotter kernel: [    0.000000] Early memory node ranges
Jul 14 16:09:18 blotter kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Jul 14 16:09:18 blotter kernel: [    0.000000]   node   0: [mem 0x00100000-0x3f575fff]
Jul 14 16:09:18 blotter kernel: [    0.000000]   node   0: [mem 0x3f5bf000-0x3f66cfff]
Jul 14 16:09:18 blotter kernel: [    0.000000]   node   0: [mem 0x3f6bf000-0x3f6edfff]
Jul 14 16:09:18 blotter kernel: [    0.000000]   node   0: [mem 0x3f6ff000-0x3f6fffff]
Jul 14 16:09:18 blotter kernel: [    0.000000] On node 0 totalpages: 259555
Jul 14 16:09:18 blotter kernel: [    0.000000] free_area_init_node: node 0, pgdat c18f5f40, node_mem_map f740d200
Jul 14 16:09:18 blotter kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 14 16:09:18 blotter kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 14 16:09:18 blotter kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul 14 16:09:18 blotter kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jul 14 16:09:18 blotter kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jul 14 16:09:18 blotter kernel: [    0.000000]   HighMem zone: 247 pages used for memmap
Jul 14 16:09:18 blotter kernel: [    0.000000]   HighMem zone: 31071 pages, LIFO batch:7
Jul 14 16:09:18 blotter kernel: [    0.000000] Using APIC driver default
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 14 16:09:18 blotter kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 14 16:09:18 blotter kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 14 16:09:18 blotter kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul 14 16:09:18 blotter kernel: [    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
Jul 14 16:09:18 blotter kernel: [    0.000000] nr_irqs_gsi: 40
Jul 14 16:09:18 blotter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 14 16:09:18 blotter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 14 16:09:18 blotter kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 14 16:09:18 blotter kernel: [    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
Jul 14 16:09:18 blotter kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 14 16:09:18 blotter kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jul 14 16:09:18 blotter kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f73ea000 s35008 r0 d22336 u57344
Jul 14 16:09:18 blotter kernel: [    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
Jul 14 16:09:18 blotter kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Jul 14 16:09:18 blotter kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257524
Jul 14 16:09:18 blotter kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-26-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7
Jul 14 16:09:18 blotter kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 14 16:09:18 blotter kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 14 16:09:18 blotter kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 14 16:09:18 blotter kernel: [    0.000000] __ex_table already sorted, skipping sort
Jul 14 16:09:18 blotter kernel: [    0.000000] Initializing CPU#0
Jul 14 16:09:18 blotter kernel: [    0.000000] allocated 2078592 bytes of page_cgroup
Jul 14 16:09:18 blotter kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 14 16:09:18 blotter kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0003f700)
Jul 14 16:09:18 blotter kernel: [    0.000000] Memory: 999872k/1039360k available (6255k kernel code, 38348k reserved, 2969k data, 788k init, 125272k highmem)
Jul 14 16:09:18 blotter kernel: [    0.000000] virtual kernel memory layout:
Jul 14 16:09:18 blotter kernel: [    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
Jul 14 16:09:18 blotter kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jul 14 16:09:18 blotter kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jul 14 16:09:18 blotter kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jul 14 16:09:18 blotter kernel: [    0.000000]       .init : 0xc1903000 - 0xc19c8000   ( 788 kB)
Jul 14 16:09:18 blotter kernel: [    0.000000]       .data : 0xc161bd30 - 0xc1902280   (2969 kB)
Jul 14 16:09:18 blotter kernel: [    0.000000]       .text : 0xc1000000 - 0xc161bd30   (6255 kB)
Jul 14 16:09:18 blotter kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 14 16:09:18 blotter kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jul 14 16:09:18 blotter kernel: [    0.000000] Hierarchical RCU implementation.
Jul 14 16:09:18 blotter kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul 14 16:09:18 blotter kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
Jul 14 16:09:18 blotter kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Jul 14 16:09:18 blotter kernel: [    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
Jul 14 16:09:18 blotter kernel: [    0.000000] Console: colour dummy device 80x25
Jul 14 16:09:18 blotter kernel: [    0.000000] console [tty0] enabled
Jul 14 16:09:18 blotter kernel: [    0.000000] hpet clockevent registered
Jul 14 16:09:18 blotter kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jul 14 16:09:18 blotter kernel: [    0.000000] tsc: Detected 1596.122 MHz processor
Jul 14 16:09:18 blotter kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.24 BogoMIPS (lpj=6384488)
Jul 14 16:09:18 blotter kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jul 14 16:09:18 blotter kernel: [    0.008066] Security Framework initialized
Jul 14 16:09:18 blotter kernel: [    0.008087] AppArmor: AppArmor initialized
Jul 14 16:09:18 blotter kernel: [    0.008092] Yama: becoming mindful.
Jul 14 16:09:18 blotter kernel: [    0.008209] Mount-cache hash table entries: 512
Jul 14 16:09:18 blotter kernel: [    0.008640] Initializing cgroup subsys cpuacct
Jul 14 16:09:18 blotter kernel: [    0.008648] Initializing cgroup subsys memory
Jul 14 16:09:18 blotter kernel: [    0.008666] Initializing cgroup subsys devices
Jul 14 16:09:18 blotter kernel: [    0.008672] Initializing cgroup subsys freezer
Jul 14 16:09:18 blotter kernel: [    0.008678] Initializing cgroup subsys blkio
Jul 14 16:09:18 blotter kernel: [    0.008683] Initializing cgroup subsys perf_event
Jul 14 16:09:18 blotter kernel: [    0.008691] Initializing cgroup subsys hugetlb
Jul 14 16:09:18 blotter kernel: [    0.008747] Disabled fast string operations
Jul 14 16:09:18 blotter kernel: [    0.008757] CPU: Physical Processor ID: 0
Jul 14 16:09:18 blotter kernel: [    0.008761] CPU: Processor Core ID: 0
Jul 14 16:09:18 blotter kernel: [    0.008767] mce: CPU supports 5 MCE banks
Jul 14 16:09:18 blotter kernel: [    0.008784] CPU0: Thermal monitoring enabled (TM2)
Jul 14 16:09:18 blotter kernel: [    0.008792] process: using mwait in idle threads
Jul 14 16:09:18 blotter kernel: [    0.008812] Last level iTLB entries: 4KB 32, 2MB 0, 4MB 0
Jul 14 16:09:18 blotter kernel: [    0.008812] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 8
Jul 14 16:09:18 blotter kernel: [    0.008812] tlb_flushall_shift: 6
Jul 14 16:09:18 blotter kernel: [    0.009206] Freeing SMP alternatives: 24k freed
Jul 14 16:09:18 blotter kernel: [    0.012984] ACPI: Core revision 20121018
Jul 14 16:09:18 blotter kernel: [    0.028026] ftrace: allocating 26123 entries in 52 pages
Jul 14 16:09:18 blotter kernel: [    0.048189] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 14 16:09:18 blotter kernel: [    0.052259] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 14 16:09:18 blotter kernel: [    0.091956] smpboot: CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz (fam: 06, model: 1c, stepping: 02)
Jul 14 16:09:18 blotter kernel: [    0.092000] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
Jul 14 16:09:18 blotter kernel: [    0.092000] ... version:                3
Jul 14 16:09:18 blotter kernel: [    0.092000] ... bit width:              40
Jul 14 16:09:18 blotter kernel: [    0.092000] ... generic registers:      2
Jul 14 16:09:18 blotter kernel: [    0.092000] ... value mask:             000000ffffffffff
Jul 14 16:09:18 blotter kernel: [    0.092000] ... max period:             000000007fffffff
Jul 14 16:09:18 blotter kernel: [    0.092000] ... fixed-purpose events:   3
Jul 14 16:09:18 blotter kernel: [    0.092000] ... event mask:             0000000700000003
Jul 14 16:09:18 blotter kernel: [    0.092000] CPU 1 irqstacks, hard=f5cd8000 soft=f5cda000
Jul 14 16:09:18 blotter kernel: [    0.092000] smpboot: Booting Node   0, Processors  #1 OK
Jul 14 16:09:18 blotter kernel: [    0.008000] Initializing CPU#1
Jul 14 16:09:18 blotter kernel: [    0.008000] Disabled fast string operations
Jul 14 16:09:18 blotter kernel: [    0.104060] Brought up 2 CPUs
Jul 14 16:09:18 blotter kernel: [    0.104075] smpboot: Total of 2 processors activated (6384.48 BogoMIPS)
Jul 14 16:09:18 blotter kernel: [    0.104261] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 14 16:09:18 blotter kernel: [    0.104874] devtmpfs: initialized
Jul 14 16:09:18 blotter kernel: [    0.104874] EVM: security.selinux
Jul 14 16:09:18 blotter kernel: [    0.104874] EVM: security.SMACK64
Jul 14 16:09:18 blotter kernel: [    0.104874] EVM: security.capability
Jul 14 16:09:18 blotter kernel: [    0.108136] PM: Registering ACPI NVS region [mem 0x3f66d000-0x3f6befff] (335872 bytes)
Jul 14 16:09:18 blotter kernel: [    0.108591] regulator-dummy: no parameters
Jul 14 16:09:18 blotter kernel: [    0.108742] NET: Registered protocol family 16
Jul 14 16:09:18 blotter kernel: [    0.109117] EISA bus registered
Jul 14 16:09:18 blotter kernel: [    0.109320] ACPI: bus type pci registered
Jul 14 16:09:18 blotter kernel: [    0.109487] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 14 16:09:18 blotter kernel: [    0.109496] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jul 14 16:09:18 blotter kernel: [    0.109500] PCI: Using MMCONFIG for extended config space
Jul 14 16:09:18 blotter kernel: [    0.109505] PCI: Using configuration type 1 for base access
Jul 14 16:09:18 blotter kernel: [    0.112630] bio: create slab <bio-0> at 0
Jul 14 16:09:18 blotter kernel: [    0.112630] ACPI: Added _OSI(Module Device)
Jul 14 16:09:18 blotter kernel: [    0.112630] ACPI: Added _OSI(Processor Device)
Jul 14 16:09:18 blotter kernel: [    0.112630] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 14 16:09:18 blotter kernel: [    0.112630] ACPI: Added _OSI(Processor Aggregator Device)
Jul 14 16:09:18 blotter kernel: [    0.116630] ACPI: EC: Look up EC in DSDT
Jul 14 16:09:18 blotter kernel: [    0.120274] ACPI: Executed 1 blocks of module-level executable AML code
Jul 14 16:09:18 blotter kernel: [    0.124157] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 14 16:09:18 blotter kernel: [    0.125218] ACPI: SSDT 3f5b7c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.126101] ACPI: Dynamic OEM Table Load:
Jul 14 16:09:18 blotter kernel: [    0.126109] ACPI: SSDT   (null) 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.126384] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.127218] ACPI: Dynamic OEM Table Load:
Jul 14 16:09:18 blotter kernel: [    0.127225] ACPI: SSDT   (null) 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.128041] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.128901] ACPI: Dynamic OEM Table Load:
Jul 14 16:09:18 blotter kernel: [    0.128908] ACPI: SSDT   (null) 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.129180] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.130029] ACPI: Dynamic OEM Table Load:
Jul 14 16:09:18 blotter kernel: [    0.130036] ACPI: SSDT   (null) 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Jul 14 16:09:18 blotter kernel: [    0.132769] ACPI: Interpreter enabled
Jul 14 16:09:18 blotter kernel: [    0.132785] ACPI: (supports S0 S3 S4 S5)
Jul 14 16:09:18 blotter kernel: [    0.132835] ACPI: Using IOAPIC for interrupt routing
Jul 14 16:09:18 blotter kernel: [    0.270244] ACPI: Power Resource [FN00] (on)
Jul 14 16:09:18 blotter kernel: [    0.271072] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Jul 14 16:09:18 blotter kernel: [    0.271419] ACPI: No dock devices found.
Jul 14 16:09:18 blotter kernel: [    0.271434] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 14 16:09:18 blotter kernel: [    0.272277] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 14 16:09:18 blotter kernel: [    0.272285] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 14 16:09:18 blotter kernel: [    0.272671] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dsfield-211)
Jul 14 16:09:18 blotter kernel: [    0.272687] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 14 16:09:18 blotter kernel: [    0.272705] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Jul 14 16:09:18 blotter kernel: [    0.274344] PCI host bridge to bus 0000:00
Jul 14 16:09:18 blotter kernel: [    0.274355] pci_bus 0000:00: root bus resource [bus 00-ff]
Jul 14 16:09:18 blotter kernel: [    0.274363] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jul 14 16:09:18 blotter kernel: [    0.274369] pci_bus 0000:00: root bus resource [io  0x0d00-0xefff]
Jul 14 16:09:18 blotter kernel: [    0.274376] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jul 14 16:09:18 blotter kernel: [    0.274382] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfebfffff]
Jul 14 16:09:18 blotter kernel: [    0.274406] pci 0000:00:00.0: [8086:27ac] type 00 class 0x060000
Jul 14 16:09:18 blotter kernel: [    0.274483] pci 0000:00:02.0: [8086:27ae] type 00 class 0x030000
Jul 14 16:09:18 blotter kernel: [    0.274503] pci 0000:00:02.0: reg 10: [mem 0x58280000-0x582fffff]
Jul 14 16:09:18 blotter kernel: [    0.274516] pci 0000:00:02.0: reg 14: [io  0x60f0-0x60f7]
Jul 14 16:09:18 blotter kernel: [    0.274528] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
Jul 14 16:09:18 blotter kernel: [    0.274540] pci 0000:00:02.0: reg 1c: [mem 0x58300000-0x5833ffff]
Jul 14 16:09:18 blotter kernel: [    0.274604] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
Jul 14 16:09:18 blotter kernel: [    0.274621] pci 0000:00:02.1: reg 10: [mem 0x58200000-0x5827ffff]
Jul 14 16:09:18 blotter kernel: [    0.274762] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
Jul 14 16:09:18 blotter kernel: [    0.274795] pci 0000:00:1b.0: reg 10: [mem 0x58340000-0x58343fff 64bit]
Jul 14 16:09:18 blotter kernel: [    0.274923] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 14 16:09:18 blotter kernel: [    0.274971] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
Jul 14 16:09:18 blotter kernel: [    0.275104] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 14 16:09:18 blotter kernel: [    0.275154] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
Jul 14 16:09:18 blotter kernel: [    0.275287] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jul 14 16:09:18 blotter kernel: [    0.275337] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
Jul 14 16:09:18 blotter kernel: [    0.275468] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jul 14 16:09:18 blotter kernel: [    0.275518] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
Jul 14 16:09:18 blotter kernel: [    0.275650] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul 14 16:09:18 blotter kernel: [    0.275701] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
Jul 14 16:09:18 blotter kernel: [    0.275770] pci 0000:00:1d.0: reg 20: [io  0x60a0-0x60bf]
Jul 14 16:09:18 blotter kernel: [    0.275831] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
Jul 14 16:09:18 blotter kernel: [    0.275900] pci 0000:00:1d.1: reg 20: [io  0x6080-0x609f]
Jul 14 16:09:18 blotter kernel: [    0.275961] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
Jul 14 16:09:18 blotter kernel: [    0.276048] pci 0000:00:1d.2: reg 20: [io  0x6060-0x607f]
Jul 14 16:09:18 blotter kernel: [    0.276110] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
Jul 14 16:09:18 blotter kernel: [    0.276179] pci 0000:00:1d.3: reg 20: [io  0x6040-0x605f]
Jul 14 16:09:18 blotter kernel: [    0.276254] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
Jul 14 16:09:18 blotter kernel: [    0.276287] pci 0000:00:1d.7: reg 10: [mem 0x58344400-0x583447ff]
Jul 14 16:09:18 blotter kernel: [    0.276414] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul 14 16:09:18 blotter kernel: [    0.276454] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
Jul 14 16:09:18 blotter kernel: [    0.276584] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
Jul 14 16:09:18 blotter kernel: [    0.276724] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
Jul 14 16:09:18 blotter kernel: [    0.276732] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
Jul 14 16:09:18 blotter kernel: [    0.276817] pci 0000:00:1f.2: [8086:27c5] type 00 class 0x010601
Jul 14 16:09:18 blotter kernel: [    0.276850] pci 0000:00:1f.2: reg 10: [io  0x60d8-0x60df]
Jul 14 16:09:18 blotter kernel: [    0.276868] pci 0000:00:1f.2: reg 14: [io  0x60fc-0x60ff]
Jul 14 16:09:18 blotter kernel: [    0.276886] pci 0000:00:1f.2: reg 18: [io  0x60d0-0x60d7]
Jul 14 16:09:18 blotter kernel: [    0.276904] pci 0000:00:1f.2: reg 1c: [io  0x60f8-0x60fb]
Jul 14 16:09:18 blotter kernel: [    0.276922] pci 0000:00:1f.2: reg 20: [io  0x6020-0x602f]
Jul 14 16:09:18 blotter kernel: [    0.276941] pci 0000:00:1f.2: reg 24: [mem 0x58344000-0x583443ff]
Jul 14 16:09:18 blotter kernel: [    0.277014] pci 0000:00:1f.2: PME# supported from D3hot
Jul 14 16:09:18 blotter kernel: [    0.277049] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
Jul 14 16:09:18 blotter kernel: [    0.277135] pci 0000:00:1f.3: reg 20: [io  0x6000-0x601f]
Jul 14 16:09:18 blotter kernel: [    0.277380] pci 0000:01:00.0: [14e4:4315] type 00 class 0x028000
Jul 14 16:09:18 blotter kernel: [    0.277460] pci 0000:01:00.0: reg 10: [mem 0x57100000-0x57103fff 64bit]
Jul 14 16:09:18 blotter kernel: [    0.277865] pci 0000:01:00.0: supports D1 D2
Jul 14 16:09:18 blotter kernel: [    0.278053] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jul 14 16:09:18 blotter kernel: [    0.278063] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Jul 14 16:09:18 blotter kernel: [    0.278073] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
Jul 14 16:09:18 blotter kernel: [    0.278087] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.278165] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jul 14 16:09:18 blotter kernel: [    0.278175] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jul 14 16:09:18 blotter kernel: [    0.278185] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
Jul 14 16:09:18 blotter kernel: [    0.278199] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.278404] pci 0000:03:00.0: [1969:1062] type 00 class 0x020000
Jul 14 16:09:18 blotter kernel: [    0.278532] pci 0000:03:00.0: reg 10: [mem 0x55000000-0x5503ffff 64bit]
Jul 14 16:09:18 blotter kernel: [    0.278596] pci 0000:03:00.0: reg 18: [io  0x2000-0x207f]
Jul 14 16:09:18 blotter kernel: [    0.279203] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 14 16:09:18 blotter kernel: [    0.284060] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jul 14 16:09:18 blotter kernel: [    0.284072] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
Jul 14 16:09:18 blotter kernel: [    0.284081] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
Jul 14 16:09:18 blotter kernel: [    0.284095] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.284180] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jul 14 16:09:18 blotter kernel: [    0.284190] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
Jul 14 16:09:18 blotter kernel: [    0.284200] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
Jul 14 16:09:18 blotter kernel: [    0.284213] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.284317] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)
Jul 14 16:09:18 blotter kernel: [    0.284337] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 14 16:09:18 blotter kernel: [    0.284344] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xefff] (subtractive decode)
Jul 14 16:09:18 blotter kernel: [    0.284350] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 14 16:09:18 blotter kernel: [    0.284357] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
Jul 14 16:09:18 blotter kernel: [    0.284400] pci_bus 0000:00: on NUMA node 0
Jul 14 16:09:18 blotter kernel: [    0.284504] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Jul 14 16:09:18 blotter kernel: [    0.284693] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Jul 14 16:09:18 blotter kernel: [    0.284822] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Jul 14 16:09:18 blotter kernel: [    0.284953] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Jul 14 16:09:18 blotter kernel: [    0.285254] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dsfield-211)
Jul 14 16:09:18 blotter kernel: [    0.285269] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 14 16:09:18 blotter kernel: [    0.285294]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
Jul 14 16:09:18 blotter kernel: [    0.285300]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
Jul 14 16:09:18 blotter kernel: [    0.287766] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Jul 14 16:09:18 blotter kernel: [    0.287925] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Jul 14 16:09:18 blotter kernel: [    0.288097] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Jul 14 16:09:18 blotter kernel: [    0.288251] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Jul 14 16:09:18 blotter kernel: [    0.288404] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 14 16:09:18 blotter kernel: [    0.288559] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 14 16:09:18 blotter kernel: [    0.288714] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 14 16:09:18 blotter kernel: [    0.288868] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 14 16:09:18 blotter kernel: [    0.289165] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jul 14 16:09:18 blotter kernel: [    0.289165] vgaarb: loaded
Jul 14 16:09:18 blotter kernel: [    0.289165] vgaarb: bridge control possible 0000:00:02.0
Jul 14 16:09:18 blotter kernel: [    0.289165] SCSI subsystem initialized
Jul 14 16:09:18 blotter kernel: [    0.289165] ACPI: bus type scsi registered
Jul 14 16:09:18 blotter kernel: [    0.289165] libata version 3.00 loaded.
Jul 14 16:09:18 blotter kernel: [    0.289165] ACPI: bus type usb registered
Jul 14 16:09:18 blotter kernel: [    0.289165] usbcore: registered new interface driver usbfs
Jul 14 16:09:18 blotter kernel: [    0.289165] usbcore: registered new interface driver hub
Jul 14 16:09:18 blotter kernel: [    0.289165] usbcore: registered new device driver usb
Jul 14 16:09:18 blotter kernel: [    0.289165] PCI: Using ACPI for IRQ routing
Jul 14 16:09:18 blotter kernel: [    0.299849] PCI: pci_cache_line_size set to 64 bytes
Jul 14 16:09:18 blotter kernel: [    0.300081] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Jul 14 16:09:18 blotter kernel: [    0.300088] e820: reserve RAM buffer [mem 0x3f576000-0x3fffffff]
Jul 14 16:09:18 blotter kernel: [    0.300094] e820: reserve RAM buffer [mem 0x3f66d000-0x3fffffff]
Jul 14 16:09:18 blotter kernel: [    0.300099] e820: reserve RAM buffer [mem 0x3f6ee000-0x3fffffff]
Jul 14 16:09:18 blotter kernel: [    0.300104] e820: reserve RAM buffer [mem 0x3f700000-0x3fffffff]
Jul 14 16:09:18 blotter kernel: [    0.300375] NetLabel: Initializing
Jul 14 16:09:18 blotter kernel: [    0.300381] NetLabel:  domain hash size = 128
Jul 14 16:09:18 blotter kernel: [    0.300384] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 14 16:09:18 blotter kernel: [    0.300410] NetLabel:  unlabeled traffic allowed by default
Jul 14 16:09:18 blotter kernel: [    0.300456] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 14 16:09:18 blotter kernel: [    0.300456] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 14 16:09:18 blotter kernel: [    0.300456] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jul 14 16:09:18 blotter kernel: [    0.304042] Switching to clocksource hpet
Jul 14 16:09:18 blotter kernel: [    0.319898] AppArmor: AppArmor Filesystem Enabled
Jul 14 16:09:18 blotter kernel: [    0.319977] pnp: PnP ACPI init
Jul 14 16:09:18 blotter kernel: [    0.320067] ACPI: bus type pnp registered
Jul 14 16:09:18 blotter kernel: [    0.384440] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x1000-0x1fff]
Jul 14 16:09:18 blotter kernel: [    0.384562] system 00:00: [io  0x0200-0x020f] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384571] system 00:00: [io  0x0600-0x060f] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384587] system 00:00: [io  0x0610] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384594] system 00:00: [io  0x0800-0x080f] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384602] system 00:00: [io  0x0400-0x047f] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384609] system 00:00: [io  0x0500-0x053f] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384616] system 00:00: [io  0xff2c-0xff2f] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384626] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384633] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384641] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384648] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384656] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384664] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 14 16:09:18 blotter kernel: [    0.384671] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 14 16:09:18 blotter kernel: [    0.384682] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 14 16:09:18 blotter kernel: [    0.384716] pnp 00:01: [dma 4]
Jul 14 16:09:18 blotter kernel: [    0.384769] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 14 16:09:18 blotter kernel: [    0.384884] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 14 16:09:18 blotter kernel: [    0.385132] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Jul 14 16:09:18 blotter kernel: [    0.385221] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 14 16:09:18 blotter kernel: [    0.385298] pnp 00:05: Plug and Play ACPI device, IDs INT0800 (active)
Jul 14 16:09:18 blotter kernel: [    0.385425] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 14 16:09:18 blotter kernel: [    0.385643] pnp 00:07: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
Jul 14 16:09:18 blotter kernel: [    0.386063] pnp: PnP ACPI: found 8 devices
Jul 14 16:09:18 blotter kernel: [    0.386069] ACPI: ACPI bus type pnp unregistered
Jul 14 16:09:18 blotter kernel: [    0.386076] PnPBIOS: Disabled by ACPI PNP
Jul 14 16:09:18 blotter kernel: [    0.426982] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jul 14 16:09:18 blotter kernel: [    0.426996] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Jul 14 16:09:18 blotter kernel: [    0.427008] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
Jul 14 16:09:18 blotter kernel: [    0.427019] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.427032] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jul 14 16:09:18 blotter kernel: [    0.427040] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jul 14 16:09:18 blotter kernel: [    0.427051] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
Jul 14 16:09:18 blotter kernel: [    0.427062] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.427074] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jul 14 16:09:18 blotter kernel: [    0.427082] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
Jul 14 16:09:18 blotter kernel: [    0.427094] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
Jul 14 16:09:18 blotter kernel: [    0.427104] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.427116] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jul 14 16:09:18 blotter kernel: [    0.427124] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
Jul 14 16:09:18 blotter kernel: [    0.427136] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
Jul 14 16:09:18 blotter kernel: [    0.427146] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.427159] pci 0000:00:1e.0: PCI bridge to [bus 05]
Jul 14 16:09:18 blotter kernel: [    0.427219] pci 0000:00:1c.1: enabling device (0000 -> 0003)
Jul 14 16:09:18 blotter kernel: [    0.427260] pci 0000:00:1c.3: enabling device (0000 -> 0003)
Jul 14 16:09:18 blotter kernel: [    0.427294] pci 0000:00:1e.0: setting latency timer to 64
Jul 14 16:09:18 blotter kernel: [    0.427304] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 14 16:09:18 blotter kernel: [    0.427311] pci_bus 0000:00: resource 5 [io  0x0d00-0xefff]
Jul 14 16:09:18 blotter kernel: [    0.427318] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 14 16:09:18 blotter kernel: [    0.427325] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
Jul 14 16:09:18 blotter kernel: [    0.427331] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
Jul 14 16:09:18 blotter kernel: [    0.427338] pci_bus 0000:01: resource 1 [mem 0x57100000-0x581fffff]
Jul 14 16:09:18 blotter kernel: [    0.427345] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.427352] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
Jul 14 16:09:18 blotter kernel: [    0.427358] pci_bus 0000:02: resource 1 [mem 0x56100000-0x570fffff]
Jul 14 16:09:18 blotter kernel: [    0.427365] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.427372] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
Jul 14 16:09:18 blotter kernel: [    0.427379] pci_bus 0000:03: resource 1 [mem 0x55000000-0x560fffff]
Jul 14 16:09:18 blotter kernel: [    0.427385] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.427392] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
Jul 14 16:09:18 blotter kernel: [    0.427399] pci_bus 0000:04: resource 1 [mem 0x54000000-0x54ffffff]
Jul 14 16:09:18 blotter kernel: [    0.427406] pci_bus 0000:04: resource 2 [mem 0x53000000-0x53ffffff 64bit pref]
Jul 14 16:09:18 blotter kernel: [    0.427413] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jul 14 16:09:18 blotter kernel: [    0.427419] pci_bus 0000:05: resource 5 [io  0x0d00-0xefff]
Jul 14 16:09:18 blotter kernel: [    0.427426] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jul 14 16:09:18 blotter kernel: [    0.427432] pci_bus 0000:05: resource 7 [mem 0x40000000-0xfebfffff]
Jul 14 16:09:18 blotter kernel: [    0.427511] NET: Registered protocol family 2
Jul 14 16:09:18 blotter kernel: [    0.427824] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Jul 14 16:09:18 blotter kernel: [    0.427887] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jul 14 16:09:18 blotter kernel: [    0.427947] TCP: Hash tables configured (established 8192 bind 8192)
Jul 14 16:09:18 blotter kernel: [    0.427993] TCP: reno registered
Jul 14 16:09:18 blotter kernel: [    0.428042] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul 14 16:09:18 blotter kernel: [    0.428062] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul 14 16:09:18 blotter kernel: [    0.428202] NET: Registered protocol family 1
Jul 14 16:09:18 blotter kernel: [    0.428238] pci 0000:00:02.0: Boot video device
Jul 14 16:09:18 blotter kernel: [    0.428618] PCI: CLS 0 bytes, default 64
Jul 14 16:09:18 blotter kernel: [    0.428742] Trying to unpack rootfs image as initramfs...
Jul 14 16:09:18 blotter kernel: [    1.137839] Freeing initrd memory: 16256k freed
Jul 14 16:09:18 blotter kernel: [    1.154632] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
Jul 14 16:09:18 blotter kernel: [    1.154643] Simple Boot Flag at 0x44 set to 0x1
Jul 14 16:09:18 blotter kernel: [    1.155314] Initialise module verification
Jul 14 16:09:18 blotter kernel: [    1.155417] audit: initializing netlink socket (disabled)
Jul 14 16:09:18 blotter kernel: [    1.155445] type=2000 audit(1373832533.152:1): initialized
Jul 14 16:09:18 blotter kernel: [    1.203500] bounce pool size: 64 pages
Jul 14 16:09:18 blotter kernel: [    1.203528] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 14 16:09:18 blotter kernel: [    1.207483] VFS: Disk quotas dquot_6.5.2
Jul 14 16:09:18 blotter kernel: [    1.207622] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 14 16:09:18 blotter kernel: [    1.209143] fuse init (API version 7.20)
Jul 14 16:09:18 blotter kernel: [    1.209383] msgmni has been set to 1740
Jul 14 16:09:18 blotter kernel: [    1.210580] Key type asymmetric registered
Jul 14 16:09:18 blotter kernel: [    1.210589] Asymmetric key parser 'x509' registered
Jul 14 16:09:18 blotter kernel: [    1.210703] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jul 14 16:09:18 blotter kernel: [    1.210782] io scheduler noop registered
Jul 14 16:09:18 blotter kernel: [    1.210790] io scheduler deadline registered (default)
Jul 14 16:09:18 blotter kernel: [    1.210816] io scheduler cfq registered
Jul 14 16:09:18 blotter kernel: [    1.211165] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Jul 14 16:09:18 blotter kernel: [    1.211360] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
Jul 14 16:09:18 blotter kernel: [    1.211544] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Jul 14 16:09:18 blotter kernel: [    1.211732] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
Jul 14 16:09:18 blotter kernel: [    1.211915] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 14 16:09:18 blotter kernel: [    1.211966] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 14 16:09:18 blotter kernel: [    1.212142] intel_idle: MWAIT substates: 0x20220
Jul 14 16:09:18 blotter kernel: [    1.212162] intel_idle: v0.4 model 0x1C
Jul 14 16:09:18 blotter kernel: [    1.212168] intel_idle: lapic_timer_reliable_states 0x2
Jul 14 16:09:18 blotter kernel: [    1.212175] tsc: Marking TSC unstable due to TSC halts in idle states deeper than C2
Jul 14 16:09:18 blotter kernel: [    1.340097] ACPI: AC Adapter [AC] (on-line)
Jul 14 16:09:18 blotter kernel: [    1.340267] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 14 16:09:18 blotter kernel: [    1.340279] ACPI: Power Button [PWRB]
Jul 14 16:09:18 blotter kernel: [    1.340383] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jul 14 16:09:18 blotter kernel: [    1.340425] ACPI: Lid Switch [LID0]
Jul 14 16:09:18 blotter kernel: [    1.340526] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jul 14 16:09:18 blotter kernel: [    1.340535] ACPI: Sleep Button [SLPB]
Jul 14 16:09:18 blotter kernel: [    1.340651] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jul 14 16:09:18 blotter kernel: [    1.340660] ACPI: Power Button [PWRF]
Jul 14 16:09:18 blotter kernel: [    1.340814] ACPI: Fan [FAN] (on)
Jul 14 16:09:18 blotter kernel: [    1.340949] ACPI: Requesting acpi_cpufreq
Jul 14 16:09:18 blotter kernel: [    1.475036] thermal LNXTHERM:00: registered as thermal_zone0
Jul 14 16:09:18 blotter kernel: [    1.475044] ACPI: Thermal Zone [THRM] (27 C)
Jul 14 16:09:18 blotter kernel: [    1.475138] GHES: HEST is not enabled!
Jul 14 16:09:18 blotter kernel: [    1.475313] isapnp: Scanning for PnP cards...
Jul 14 16:09:18 blotter kernel: [    1.476233] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 14 16:09:18 blotter kernel: [    1.829303] isapnp: No Plug & Play device found
Jul 14 16:09:18 blotter kernel: [    2.132261] ACPI: Battery Slot [BAT0] (battery present)
Jul 14 16:09:18 blotter kernel: [    2.132497] Linux agpgart interface v0.103
Jul 14 16:09:18 blotter kernel: [    2.132651] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Jul 14 16:09:18 blotter kernel: [    2.132821] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
Jul 14 16:09:18 blotter kernel: [    2.132984] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Jul 14 16:09:18 blotter kernel: [    2.133262] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
Jul 14 16:09:18 blotter kernel: [    2.137432] brd: module loaded
Jul 14 16:09:18 blotter kernel: [    2.139676] loop: module loaded
Jul 14 16:09:18 blotter kernel: [    2.140922] libphy: Fixed MDIO Bus: probed
Jul 14 16:09:18 blotter kernel: [    2.141154] tun: Universal TUN/TAP device driver, 1.6
Jul 14 16:09:18 blotter kernel: [    2.141159] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 14 16:09:18 blotter kernel: [    2.141324] PPP generic driver version 2.4.2
Jul 14 16:09:18 blotter kernel: [    2.141453] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 14 16:09:18 blotter kernel: [    2.141458] ehci-pci: EHCI PCI platform driver
Jul 14 16:09:18 blotter kernel: [    2.141535] ehci-pci 0000:00:1d.7: setting latency timer to 64
Jul 14 16:09:18 blotter kernel: [    2.141544] ehci-pci 0000:00:1d.7: EHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.141559] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul 14 16:09:18 blotter kernel: [    2.141586] ehci-pci 0000:00:1d.7: debug port 1
Jul 14 16:09:18 blotter kernel: [    2.145516] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
Jul 14 16:09:18 blotter kernel: [    2.145557] ehci-pci 0000:00:1d.7: irq 16, io mem 0x58344400
Jul 14 16:09:18 blotter kernel: [    2.156034] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul 14 16:09:18 blotter kernel: [    2.156117] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jul 14 16:09:18 blotter kernel: [    2.156125] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 16:09:18 blotter kernel: [    2.156131] usb usb1: Product: EHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.156137] usb usb1: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
Jul 14 16:09:18 blotter kernel: [    2.156143] usb usb1: SerialNumber: 0000:00:1d.7
Jul 14 16:09:18 blotter kernel: [    2.156448] hub 1-0:1.0: USB hub found
Jul 14 16:09:18 blotter kernel: [    2.156462] hub 1-0:1.0: 8 ports detected
Jul 14 16:09:18 blotter kernel: [    2.156808] ehci-platform: EHCI generic platform driver
Jul 14 16:09:18 blotter kernel: [    2.156839] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 14 16:09:18 blotter kernel: [    2.156888] uhci_hcd: USB Universal Host Controller Interface driver
Jul 14 16:09:18 blotter kernel: [    2.156946] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul 14 16:09:18 blotter kernel: [    2.156955] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.156969] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul 14 16:09:18 blotter kernel: [    2.157017] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
Jul 14 16:09:18 blotter kernel: [    2.157100] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Jul 14 16:09:18 blotter kernel: [    2.157108] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 16:09:18 blotter kernel: [    2.157114] usb usb2: Product: UHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.157120] usb usb2: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 14 16:09:18 blotter kernel: [    2.157126] usb usb2: SerialNumber: 0000:00:1d.0
Jul 14 16:09:18 blotter kernel: [    2.157412] hub 2-0:1.0: USB hub found
Jul 14 16:09:18 blotter kernel: [    2.157425] hub 2-0:1.0: 2 ports detected
Jul 14 16:09:18 blotter kernel: [    2.157606] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul 14 16:09:18 blotter kernel: [    2.157615] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.157629] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul 14 16:09:18 blotter kernel: [    2.157691] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
Jul 14 16:09:18 blotter kernel: [    2.157772] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jul 14 16:09:18 blotter kernel: [    2.157779] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 16:09:18 blotter kernel: [    2.157785] usb usb3: Product: UHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.157791] usb usb3: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 14 16:09:18 blotter kernel: [    2.157797] usb usb3: SerialNumber: 0000:00:1d.1
Jul 14 16:09:18 blotter kernel: [    2.158044] hub 3-0:1.0: USB hub found
Jul 14 16:09:18 blotter kernel: [    2.158061] hub 3-0:1.0: 2 ports detected
Jul 14 16:09:18 blotter kernel: [    2.158249] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul 14 16:09:18 blotter kernel: [    2.158258] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.158271] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul 14 16:09:18 blotter kernel: [    2.158331] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
Jul 14 16:09:18 blotter kernel: [    2.158413] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jul 14 16:09:18 blotter kernel: [    2.158420] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 16:09:18 blotter kernel: [    2.158426] usb usb4: Product: UHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.158432] usb usb4: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 14 16:09:18 blotter kernel: [    2.158438] usb usb4: SerialNumber: 0000:00:1d.2
Jul 14 16:09:18 blotter kernel: [    2.158683] hub 4-0:1.0: USB hub found
Jul 14 16:09:18 blotter kernel: [    2.158695] hub 4-0:1.0: 2 ports detected
Jul 14 16:09:18 blotter kernel: [    2.158872] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jul 14 16:09:18 blotter kernel: [    2.158881] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.158894] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jul 14 16:09:18 blotter kernel: [    2.158958] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
Jul 14 16:09:18 blotter kernel: [    2.159044] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jul 14 16:09:18 blotter kernel: [    2.159051] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 16:09:18 blotter kernel: [    2.159057] usb usb5: Product: UHCI Host Controller
Jul 14 16:09:18 blotter kernel: [    2.159063] usb usb5: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 14 16:09:18 blotter kernel: [    2.159069] usb usb5: SerialNumber: 0000:00:1d.3
Jul 14 16:09:18 blotter kernel: [    2.159357] hub 5-0:1.0: USB hub found
Jul 14 16:09:18 blotter kernel: [    2.159370] hub 5-0:1.0: 2 ports detected
Jul 14 16:09:18 blotter kernel: [    2.159783] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
Jul 14 16:09:18 blotter kernel: [    2.180351] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 14 16:09:18 blotter kernel: [    2.180371] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 14 16:09:18 blotter kernel: [    2.180753] mousedev: PS/2 mouse device common for all mice
Jul 14 16:09:18 blotter kernel: [    2.181300] rtc_cmos 00:02: RTC can wake from S4
Jul 14 16:09:18 blotter kernel: [    2.181545] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jul 14 16:09:18 blotter kernel: [    2.181595] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jul 14 16:09:18 blotter kernel: [    2.181834] device-mapper: uevent: version 1.0.3
Jul 14 16:09:18 blotter kernel: [    2.182005] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
Jul 14 16:09:18 blotter kernel: [    2.182056] EISA: Probing bus 0 at eisa.0
Jul 14 16:09:18 blotter kernel: [    2.182062] EISA: Cannot allocate resource for mainboard
Jul 14 16:09:18 blotter kernel: [    2.182069] Cannot allocate resource for EISA slot 1
Jul 14 16:09:18 blotter kernel: [    2.182074] Cannot allocate resource for EISA slot 2
Jul 14 16:09:18 blotter kernel: [    2.182079] Cannot allocate resource for EISA slot 3
Jul 14 16:09:18 blotter kernel: [    2.182084] Cannot allocate resource for EISA slot 4
Jul 14 16:09:18 blotter kernel: [    2.182088] Cannot allocate resource for EISA slot 5
Jul 14 16:09:18 blotter kernel: [    2.182093] Cannot allocate resource for EISA slot 6
Jul 14 16:09:18 blotter kernel: [    2.182098] Cannot allocate resource for EISA slot 7
Jul 14 16:09:18 blotter kernel: [    2.182103] Cannot allocate resource for EISA slot 8
Jul 14 16:09:18 blotter kernel: [    2.182107] EISA: Detected 0 cards.
Jul 14 16:09:18 blotter kernel: [    2.182126] cpufreq-nforce2: No nForce2 chipset.
Jul 14 16:09:18 blotter kernel: [    2.182225] cpuidle: using governor ladder
Jul 14 16:09:18 blotter kernel: [    2.182351] cpuidle: using governor menu
Jul 14 16:09:18 blotter kernel: [    2.182360] ledtrig-cpu: registered to indicate activity on CPUs
Jul 14 16:09:18 blotter kernel: [    2.182365] EFI Variables Facility v0.08 2004-May-17
Jul 14 16:09:18 blotter kernel: [    2.182974] ashmem: initialized
Jul 14 16:09:18 blotter kernel: [    2.183311] TCP: cubic registered
Jul 14 16:09:18 blotter kernel: [    2.183579] NET: Registered protocol family 10
Jul 14 16:09:18 blotter kernel: [    2.183998] NET: Registered protocol family 17
Jul 14 16:09:18 blotter kernel: [    2.184070] Key type dns_resolver registered
Jul 14 16:09:18 blotter kernel: [    2.184494] Using IPI No-Shortcut mode
Jul 14 16:09:18 blotter kernel: [    2.184818] Loading module verification certificates
Jul 14 16:09:18 blotter kernel: [    2.197275] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d1850ecb2327d153922b22332b63536822dc0add'
Jul 14 16:09:18 blotter kernel: [    2.197308] registered taskstats version 1
Jul 14 16:09:18 blotter kernel: [    2.204198] Key type trusted registered
Jul 14 16:09:18 blotter kernel: [    2.208730] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jul 14 16:09:18 blotter kernel: [    2.211305] Key type encrypted registered
Jul 14 16:09:18 blotter kernel: [    2.219282] rtc_cmos 00:02: setting system clock to 2013-07-14 20:08:55 UTC (1373832535)
Jul 14 16:09:18 blotter kernel: [    2.221065] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 14 16:09:18 blotter kernel: [    2.221071] EDD information not available.
Jul 14 16:09:18 blotter kernel: [    2.221450] Freeing unused kernel memory: 788k freed
Jul 14 16:09:18 blotter kernel: [    2.222104] Write protecting the kernel text: 6256k
Jul 14 16:09:18 blotter kernel: [    2.222237] Write protecting the kernel read-only data: 2432k
Jul 14 16:09:18 blotter kernel: [    2.222242] NX-protecting the kernel data: 3984k
Jul 14 16:09:18 blotter kernel: [    2.468136] usb 1-2: new high-speed USB device number 2 using ehci-pci
Jul 14 16:09:18 blotter kernel: [    2.634035] usb 1-2: New USB device found, idVendor=04f2, idProduct=b175
Jul 14 16:09:18 blotter kernel: [    2.634050] usb 1-2: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jul 14 16:09:18 blotter kernel: [    2.634059] usb 1-2: Product: CNF9011
Jul 14 16:09:18 blotter kernel: [    2.634067] usb 1-2: Manufacturer: Chicony Electronics Co., Ltd.
Jul 14 16:09:18 blotter kernel: [    2.634074] usb 1-2: SerialNumber: SN0001
Jul 14 16:09:18 blotter kernel: [    2.649401] Disabling lock debugging due to kernel taint
Jul 14 16:09:18 blotter kernel: [    2.651523] ahci 0000:00:1f.2: version 3.0
Jul 14 16:09:18 blotter kernel: [    2.651666] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
Jul 14 16:09:18 blotter kernel: [    2.651776] ahci: SSS flag set, parallel bus scan disabled
Jul 14 16:09:18 blotter kernel: [    2.651844] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
Jul 14 16:09:18 blotter kernel: [    2.651858] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
Jul 14 16:09:18 blotter kernel: [    2.651874] ahci 0000:00:1f.2: setting latency timer to 64
Jul 14 16:09:18 blotter kernel: [    2.654534] scsi0 : ahci
Jul 14 16:09:18 blotter kernel: [    2.654877] scsi1 : ahci
Jul 14 16:09:18 blotter kernel: [    2.659740] scsi2 : ahci
Jul 14 16:09:18 blotter kernel: [    2.660470] scsi3 : ahci
Jul 14 16:09:18 blotter kernel: [    2.660690] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 44
Jul 14 16:09:18 blotter kernel: [    2.660699] ata2: DUMMY
Jul 14 16:09:18 blotter kernel: [    2.660709] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 44
Jul 14 16:09:18 blotter kernel: [    2.660715] ata4: DUMMY
Jul 14 16:09:18 blotter kernel: [    2.672904] atl1c 0000:03:00.0: version 1.0.1.1-NAPI
Jul 14 16:09:18 blotter kernel: [    2.980176] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 14 16:09:18 blotter kernel: [    2.981427] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 14 16:09:18 blotter kernel: [    3.028126] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
Jul 14 16:09:18 blotter kernel: [    3.028142] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 14 16:09:18 blotter kernel: [    3.030042] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Jul 14 16:09:18 blotter kernel: [    3.030372] ata1.00: configured for UDMA/133
Jul 14 16:09:18 blotter kernel: [    3.030826] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
Jul 14 16:09:18 blotter kernel: [    3.031535] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jul 14 16:09:18 blotter kernel: [    3.031587] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 14 16:09:18 blotter kernel: [    3.031777] sd 0:0:0:0: [sda] Write Protect is off
Jul 14 16:09:18 blotter kernel: [    3.031788] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 14 16:09:18 blotter kernel: [    3.031904] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 14 16:09:18 blotter kernel: [    3.049603]  sda: sda1 sda2 < sda5 >
Jul 14 16:09:18 blotter kernel: [    3.050881] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 14 16:09:18 blotter kernel: [    3.352166] ata3: SATA link down (SStatus 0 SControl 300)
Jul 14 16:09:18 blotter kernel: [    3.665783] bio: create slab <bio-1> at 1
Jul 14 16:09:18 blotter kernel: [    3.992232] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
Jul 14 16:09:18 blotter kernel: [    3.992242] EXT4-fs (dm-0): write access will be enabled during recovery
Jul 14 16:09:18 blotter kernel: [    4.488611] EXT4-fs (dm-0): orphan cleanup on readonly fs
Jul 14 16:09:18 blotter kernel: [    4.512882] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4196651
Jul 14 16:09:18 blotter kernel: [    4.537315] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4196200
Jul 14 16:09:18 blotter kernel: [    4.558410] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4198616
Jul 14 16:09:18 blotter kernel: [    4.573670] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 796289
Jul 14 16:09:18 blotter kernel: [    4.573961] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4198433
Jul 14 16:09:18 blotter kernel: [    4.579123] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4197203
Jul 14 16:09:18 blotter kernel: [    4.619008] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 8655284
Jul 14 16:09:18 blotter kernel: [    4.631919] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 8659053
Jul 14 16:09:18 blotter kernel: [    4.632102] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 8659045
Jul 14 16:09:18 blotter kernel: [    4.663239] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 1310735
Jul 14 16:09:18 blotter kernel: [    4.663285] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 1310733
Jul 14 16:09:18 blotter kernel: [    4.663331] EXT4-fs (dm-0): 11 orphan inodes deleted
Jul 14 16:09:18 blotter kernel: [    4.663336] EXT4-fs (dm-0): recovery complete
Jul 14 16:09:18 blotter kernel: [    4.878190] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Jul 14 16:09:18 blotter kernel: [   14.610955] Adding 1040380k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:1040380k 
Jul 14 16:09:18 blotter kernel: [   14.900627] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 14 16:09:18 blotter kernel: [   15.468656] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Jul 14 16:09:18 blotter kernel: [   15.891449] wmi: Mapper loaded
Jul 14 16:09:18 blotter kernel: [   15.898679] type=1400 audit(1373832549.174:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=514 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   15.900425] type=1400 audit(1373832549.178:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=514 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   15.901311] type=1400 audit(1373832549.178:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=514 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   15.915332] type=1400 audit(1373832549.190:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=529 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   16.047302] cfg80211: Calling CRDA to update world regulatory domain
Jul 14 16:09:18 blotter kernel: [   16.055533] lp: driver loaded but no devices found
Jul 14 16:09:18 blotter kernel: [   16.224256] lib80211: common routines for IEEE802.11 drivers
Jul 14 16:09:18 blotter kernel: [   16.224269] lib80211_crypt: registered algorithm 'NULL'
Jul 14 16:09:18 blotter kernel: [   16.358006] [drm] Initialized drm 1.1.0 20060810
Jul 14 16:09:18 blotter kernel: [   16.408612] acpi device:24: registered as cooling_device3
Jul 14 16:09:18 blotter kernel: [   16.408769] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
Jul 14 16:09:18 blotter kernel: [   16.408963] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
Jul 14 16:09:18 blotter kernel: [   16.519403] intel_rng: FWH not detected
Jul 14 16:09:18 blotter kernel: [   16.772377] microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x212
Jul 14 16:09:18 blotter kernel: [   16.849895] wl: module license 'MIXED/Proprietary' taints kernel.
Jul 14 16:09:18 blotter kernel: [   16.966527] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Jul 14 16:09:18 blotter kernel: [   17.043892] lib80211_crypt: registered algorithm 'TKIP'
Jul 14 16:09:18 blotter kernel: [   17.172968] Linux video capture interface: v2.00
Jul 14 16:09:18 blotter kernel: [   17.368720] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
Jul 14 16:09:18 blotter kernel: [   17.481626] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMBA 1 (20121018/utaddress-251)
Jul 14 16:09:18 blotter kernel: [   17.481648] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 14 16:09:18 blotter kernel: [   17.481659] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Jul 14 16:09:18 blotter kernel: [   17.481673] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 14 16:09:18 blotter kernel: [   17.481680] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Jul 14 16:09:18 blotter kernel: [   17.481693] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 14 16:09:18 blotter kernel: [   17.481700] lpc_ich: Resource conflict(s) found affecting gpio_ich
Jul 14 16:09:18 blotter kernel: [   17.483269] microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x212
Jul 14 16:09:18 blotter kernel: [   17.561496] i915 0000:00:02.0: setting latency timer to 64
Jul 14 16:09:18 blotter kernel: [   17.563302] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul 14 16:09:18 blotter kernel: [   17.563310] [drm] Driver supports precise vblank timestamp query.
Jul 14 16:09:18 blotter kernel: [   17.563481] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jul 14 16:09:18 blotter kernel: [   17.579318] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 14 16:09:18 blotter kernel: [   17.596758] acer_wmi: Acer Laptop ACPI-WMI Extras
Jul 14 16:09:18 blotter kernel: [   17.734122] [drm] initialized overlay support
Jul 14 16:09:18 blotter kernel: [   17.760349] acer_wmi: Function bitmap for Communication Device: 0x1
Jul 14 16:09:18 blotter kernel: [   17.760376] acer_wmi: Brightness must be controlled by acpi video driver
Jul 14 16:09:18 blotter kernel: [   17.762629] input: Acer BMA150 accelerometer as /devices/virtual/input/input6
Jul 14 16:09:18 blotter kernel: [   17.832969] cfg80211: World regulatory domain updated:
Jul 14 16:09:18 blotter kernel: [   17.832982] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 14 16:09:18 blotter kernel: [   17.832991] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 14 16:09:18 blotter kernel: [   17.832999] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 14 16:09:18 blotter kernel: [   17.833007] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 14 16:09:18 blotter kernel: [   17.833014] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 14 16:09:18 blotter kernel: [   17.833022] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 14 16:09:18 blotter kernel: [   17.978918] leds_ss4200: no LED devices found
Jul 14 16:09:18 blotter kernel: [   18.051188] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)
Jul 14 16:09:18 blotter kernel: [   18.062461] fbcon: inteldrmfb (fb0) is primary device
Jul 14 16:09:18 blotter kernel: [   18.070334] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
Jul 14 16:09:18 blotter kernel: [   18.070929] usbcore: registered new interface driver uvcvideo
Jul 14 16:09:18 blotter kernel: [   18.070931] USB Video Class driver (1.1.1)
Jul 14 16:09:18 blotter kernel: [   18.436613] i915: fixme: max PWM is zero
Jul 14 16:09:18 blotter kernel: [   18.436795] Console: switching to colour frame buffer device 128x37
Jul 14 16:09:18 blotter kernel: [   18.446597] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Jul 14 16:09:18 blotter kernel: [   18.446606] i915 0000:00:02.0: registered panic notifier
Jul 14 16:09:18 blotter kernel: [   18.463440] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jul 14 16:09:18 blotter kernel: [   18.726598] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Jul 14 16:09:18 blotter kernel: [   18.784647] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000, board id: 3655, fw id: 511380
Jul 14 16:09:18 blotter kernel: [   18.797695] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
Jul 14 16:09:18 blotter kernel: [   18.798387] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jul 14 16:09:18 blotter kernel: [   18.869956] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
Jul 14 16:09:18 blotter kernel: [   25.051752] Bluetooth: Core ver 2.16
Jul 14 16:09:18 blotter kernel: [   25.051853] NET: Registered protocol family 31
Jul 14 16:09:18 blotter kernel: [   25.051860] Bluetooth: HCI device and connection manager initialized
Jul 14 16:09:18 blotter kernel: [   25.053752] Bluetooth: HCI socket layer initialized
Jul 14 16:09:18 blotter kernel: [   25.053771] Bluetooth: L2CAP socket layer initialized
Jul 14 16:09:18 blotter kernel: [   25.053809] Bluetooth: SCO socket layer initialized
Jul 14 16:09:18 blotter kernel: [   25.327233] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 14 16:09:18 blotter kernel: [   25.327245] Bluetooth: BNEP filters: protocol multicast
Jul 14 16:09:18 blotter kernel: [   25.327271] Bluetooth: BNEP socket layer initialized
Jul 14 16:09:18 blotter kernel: [   25.332431] Bluetooth: RFCOMM TTY layer initialized
Jul 14 16:09:18 blotter kernel: [   25.332470] Bluetooth: RFCOMM socket layer initialized
Jul 14 16:09:18 blotter kernel: [   25.332477] Bluetooth: RFCOMM ver 1.11
Jul 14 16:09:18 blotter kernel: [   25.483012] type=1400 audit(1373832558.758:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=946 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.485864] type=1400 audit(1373832558.762:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=947 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.486204] type=1400 audit(1373832558.762:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=946 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.501724] type=1400 audit(1373832558.778:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=947 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.502593] type=1400 audit(1373832558.778:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=947 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.537609] type=1400 audit(1373832558.814:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=951 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.552210] type=1400 audit(1373832558.830:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=955 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.554047] type=1400 audit(1373832558.830:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=955 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.573943] type=1400 audit(1373832558.850:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=956 comm="apparmor_parser"
Jul 14 16:09:18 blotter kernel: [   25.578153] type=1400 audit(1373832558.854:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=951 comm="apparmor_parser"
Jul 14 16:09:19 blotter kernel: [   26.138682] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
Jul 14 16:09:19 blotter kernel: [   26.154360] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 14 16:09:19 blotter kernel: [   26.180934] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 14 16:10:28 blotter kernel: [   95.680166] usb 1-1: new high-speed USB device number 3 using ehci-pci
Jul 14 16:10:29 blotter kernel: [   95.820320] usb 1-1: New USB device found, idVendor=13fe, idProduct=4100
Jul 14 16:10:29 blotter kernel: [   95.820335] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 14 16:10:29 blotter kernel: [   95.820345] usb 1-1: Product:                 
Jul 14 16:10:29 blotter kernel: [   95.820354] usb 1-1: Manufacturer:         
Jul 14 16:10:29 blotter kernel: [   95.820362] usb 1-1: SerialNumber: 0707322D023EF127
Jul 14 16:10:29 blotter kernel: [   95.889662] Initializing USB Mass Storage driver...
Jul 14 16:10:29 blotter kernel: [   95.890149] scsi4 : usb-storage 1-1:1.0
Jul 14 16:10:29 blotter kernel: [   95.890486] usbcore: registered new interface driver usb-storage
Jul 14 16:10:29 blotter kernel: [   95.890495] USB Mass Storage support registered.
Jul 14 16:10:30 blotter kernel: [   96.914779] scsi 4:0:0:0: Direct-Access                               PMAP PQ: 0 ANSI: 4
Jul 14 16:10:30 blotter kernel: [   96.919183] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jul 14 16:10:32 blotter kernel: [   99.123771] sd 4:0:0:0: [sdb] 62808064 512-byte logical blocks: (32.1 GB/29.9 GiB)
Jul 14 16:10:32 blotter kernel: [   99.126349] sd 4:0:0:0: [sdb] Write Protect is off
Jul 14 16:10:32 blotter kernel: [   99.126362] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jul 14 16:10:32 blotter kernel: [   99.129039] sd 4:0:0:0: [sdb] No Caching mode page present
Jul 14 16:10:32 blotter kernel: [   99.129060] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul 14 16:10:32 blotter kernel: [   99.140554] sd 4:0:0:0: [sdb] No Caching mode page present
Jul 14 16:10:32 blotter kernel: [   99.140581] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul 14 16:10:32 blotter kernel: [   99.169600]  sdb: sdb1
Jul 14 16:10:32 blotter kernel: [   99.179747] sd 4:0:0:0: [sdb] No Caching mode page present
Jul 14 16:10:32 blotter kernel: [   99.179775] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul 14 16:10:32 blotter kernel: [   99.179796] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```
====END TEXT OF kern.log====

====TEXT OF kern.log.1====
```

Jul  7 11:14:28 blotter kernel: [ 3951.692208] usb 1-1: new high-speed USB device number 3 using ehci-pci
Jul  7 11:14:29 blotter kernel: [ 3951.832182] usb 1-1: New USB device found, idVendor=13fe, idProduct=4100
Jul  7 11:14:29 blotter kernel: [ 3951.832203] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul  7 11:14:29 blotter kernel: [ 3951.832217] usb 1-1: Product:                 
Jul  7 11:14:29 blotter kernel: [ 3951.832229] usb 1-1: Manufacturer:         
Jul  7 11:14:29 blotter kernel: [ 3951.832241] usb 1-1: SerialNumber: 0707322D023EF127
Jul  7 11:14:30 blotter kernel: [ 3953.330024] Initializing USB Mass Storage driver...
Jul  7 11:14:30 blotter kernel: [ 3953.330489] scsi4 : usb-storage 1-1:1.0
Jul  7 11:14:30 blotter kernel: [ 3953.330997] usbcore: registered new interface driver usb-storage
Jul  7 11:14:30 blotter kernel: [ 3953.331008] USB Mass Storage support registered.
Jul  7 11:14:31 blotter kernel: [ 3954.354912] scsi 4:0:0:0: Direct-Access                               PMAP PQ: 0 ANSI: 4
Jul  7 11:14:31 blotter kernel: [ 3954.359192] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jul  7 11:14:33 blotter kernel: [ 3956.660536] sd 4:0:0:0: [sdb] 62808064 512-byte logical blocks: (32.1 GB/29.9 GiB)
Jul  7 11:14:33 blotter kernel: [ 3956.663255] sd 4:0:0:0: [sdb] Write Protect is off
Jul  7 11:14:33 blotter kernel: [ 3956.663279] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jul  7 11:14:33 blotter kernel: [ 3956.666031] sd 4:0:0:0: [sdb] No Caching mode page present
Jul  7 11:14:33 blotter kernel: [ 3956.666050] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul  7 11:14:33 blotter kernel: [ 3956.676532] sd 4:0:0:0: [sdb] No Caching mode page present
Jul  7 11:14:33 blotter kernel: [ 3956.676553] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul  7 11:14:33 blotter kernel: [ 3956.705742]  sdb: sdb1
Jul  7 11:14:33 blotter kernel: [ 3956.714466] sd 4:0:0:0: [sdb] No Caching mode page present
Jul  7 11:14:33 blotter kernel: [ 3956.714478] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul  7 11:14:33 blotter kernel: [ 3956.714487] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jul  7 11:16:52 blotter kernel: [ 4095.420772] sdb: detected capacity change from 32157728768 to 0
Jul  7 11:16:56 blotter kernel: [ 4099.546665] usb 1-1: USB disconnect, device number 3
Jul 10 10:15:24 blotter kernel: imklog 5.8.11, log source = /proc/kmsg started.
Jul 10 10:15:24 blotter kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 10 10:15:24 blotter kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 10 10:15:24 blotter kernel: [    0.000000] Linux version 3.8.0-26-generic (buildd@lamiak) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #38-Ubuntu SMP Mon Jun 17 21:46:08 UTC 2013 (Ubuntu 3.8.0-26.38-generic 3.8.13.2)
Jul 10 10:15:24 blotter kernel: [    0.000000] KERNEL supported cpus:
Jul 10 10:15:24 blotter kernel: [    0.000000]   Intel GenuineIntel
Jul 10 10:15:24 blotter kernel: [    0.000000]   AMD AuthenticAMD
Jul 10 10:15:24 blotter kernel: [    0.000000]   NSC Geode by NSC
Jul 10 10:15:24 blotter kernel: [    0.000000]   Cyrix CyrixInstead
Jul 10 10:15:24 blotter kernel: [    0.000000]   Centaur CentaurHauls
Jul 10 10:15:24 blotter kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 10 10:15:24 blotter kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 10 10:15:24 blotter kernel: [    0.000000]   UMC UMC UMC UMC
Jul 10 10:15:24 blotter kernel: [    0.000000] Disabled fast string operations
Jul 10 10:15:24 blotter kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003f575fff] usable
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f576000-0x000000003f5befff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f5bf000-0x000000003f66cfff] usable
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f66d000-0x000000003f6befff] ACPI NVS
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6bf000-0x000000003f6edfff] usable
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6ee000-0x000000003f6fefff] ACPI data
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6ff000-0x000000003f6fffff] usable
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f700000-0x000000003fffffff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 10 10:15:24 blotter kernel: [    0.000000] SMBIOS 2.4 present.
Jul 10 10:15:24 blotter kernel: [    0.000000] DMI: Acer       Aspire one      /Aspire one      , BIOS V1.22 10/14/2009
Jul 10 10:15:24 blotter kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Jul 10 10:15:24 blotter kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 10 10:15:24 blotter kernel: [    0.000000] e820: last_pfn = 0x3f700 max_arch_pfn = 0x1000000
Jul 10 10:15:24 blotter kernel: [    0.000000] MTRR default type: uncachable
Jul 10 10:15:24 blotter kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 10 10:15:24 blotter kernel: [    0.000000]   00000-9FFFF write-back
Jul 10 10:15:24 blotter kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 10 10:15:24 blotter kernel: [    0.000000]   C0000-C7FFF write-protect
Jul 10 10:15:24 blotter kernel: [    0.000000]   C8000-EFFFF uncachable
Jul 10 10:15:24 blotter kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 10 10:15:24 blotter kernel: [    0.000000] MTRR variable ranges enabled:
Jul 10 10:15:24 blotter kernel: [    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
Jul 10 10:15:24 blotter kernel: [    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
Jul 10 10:15:24 blotter kernel: [    0.000000]   2 base 000000000 mask 0E0000000 write-back
Jul 10 10:15:24 blotter kernel: [    0.000000]   3 base 020000000 mask 0E0000000 write-back
Jul 10 10:15:24 blotter kernel: [    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
Jul 10 10:15:24 blotter kernel: [    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
Jul 10 10:15:24 blotter kernel: [    0.000000]   6 disabled
Jul 10 10:15:24 blotter kernel: [    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
Jul 10 10:15:24 blotter kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 10 10:15:24 blotter kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Jul 10 10:15:24 blotter kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul 10 10:15:24 blotter kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Jul 10 10:15:24 blotter kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Jul 10 10:15:24 blotter kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Jul 10 10:15:24 blotter kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Jul 10 10:15:24 blotter kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Jul 10 10:15:24 blotter kernel: [    0.000000] RAMDISK: [mem 0x36030000-0x3700ffff]
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: DSDT 3f6f0000 070CA (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: FACS 3f688000 00040
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: SLIC 3f6ef000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: BOOT 3f6ee000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 10 10:15:24 blotter kernel: [    0.000000] 123MB HIGHMEM available.
Jul 10 10:15:24 blotter kernel: [    0.000000] 891MB LOWMEM available.
Jul 10 10:15:24 blotter kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jul 10 10:15:24 blotter kernel: [    0.000000]   low ram: 0 - 37bfe000
Jul 10 10:15:24 blotter kernel: [    0.000000] Zone ranges:
Jul 10 10:15:24 blotter kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Jul 10 10:15:24 blotter kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Jul 10 10:15:24 blotter kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0x3f6fffff]
Jul 10 10:15:24 blotter kernel: [    0.000000] Movable zone start for each node
Jul 10 10:15:24 blotter kernel: [    0.000000] Early memory node ranges
Jul 10 10:15:24 blotter kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Jul 10 10:15:24 blotter kernel: [    0.000000]   node   0: [mem 0x00100000-0x3f575fff]
Jul 10 10:15:24 blotter kernel: [    0.000000]   node   0: [mem 0x3f5bf000-0x3f66cfff]
Jul 10 10:15:24 blotter kernel: [    0.000000]   node   0: [mem 0x3f6bf000-0x3f6edfff]
Jul 10 10:15:24 blotter kernel: [    0.000000]   node   0: [mem 0x3f6ff000-0x3f6fffff]
Jul 10 10:15:24 blotter kernel: [    0.000000] On node 0 totalpages: 259555
Jul 10 10:15:24 blotter kernel: [    0.000000] free_area_init_node: node 0, pgdat c18f5f40, node_mem_map f740d200
Jul 10 10:15:24 blotter kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 10 10:15:24 blotter kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 10 10:15:24 blotter kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul 10 10:15:24 blotter kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jul 10 10:15:24 blotter kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jul 10 10:15:24 blotter kernel: [    0.000000]   HighMem zone: 247 pages used for memmap
Jul 10 10:15:24 blotter kernel: [    0.000000]   HighMem zone: 31071 pages, LIFO batch:7
Jul 10 10:15:24 blotter kernel: [    0.000000] Using APIC driver default
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 10 10:15:24 blotter kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 10 10:15:24 blotter kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 10 10:15:24 blotter kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul 10 10:15:24 blotter kernel: [    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
Jul 10 10:15:24 blotter kernel: [    0.000000] nr_irqs_gsi: 40
Jul 10 10:15:24 blotter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 10 10:15:24 blotter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 10 10:15:24 blotter kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 10 10:15:24 blotter kernel: [    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
Jul 10 10:15:24 blotter kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 10 10:15:24 blotter kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jul 10 10:15:24 blotter kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f73ea000 s35008 r0 d22336 u57344
Jul 10 10:15:24 blotter kernel: [    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
Jul 10 10:15:24 blotter kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Jul 10 10:15:24 blotter kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257524
Jul 10 10:15:24 blotter kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-26-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7
Jul 10 10:15:24 blotter kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 10 10:15:24 blotter kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 10 10:15:24 blotter kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 10 10:15:24 blotter kernel: [    0.000000] __ex_table already sorted, skipping sort
Jul 10 10:15:24 blotter kernel: [    0.000000] Initializing CPU#0
Jul 10 10:15:24 blotter kernel: [    0.000000] allocated 2078592 bytes of page_cgroup
Jul 10 10:15:24 blotter kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 10 10:15:24 blotter kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0003f700)
Jul 10 10:15:24 blotter kernel: [    0.000000] Memory: 999872k/1039360k available (6255k kernel code, 38348k reserved, 2969k data, 788k init, 125272k highmem)
Jul 10 10:15:24 blotter kernel: [    0.000000] virtual kernel memory layout:
Jul 10 10:15:24 blotter kernel: [    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
Jul 10 10:15:24 blotter kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jul 10 10:15:24 blotter kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jul 10 10:15:24 blotter kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jul 10 10:15:24 blotter kernel: [    0.000000]       .init : 0xc1903000 - 0xc19c8000   ( 788 kB)
Jul 10 10:15:24 blotter kernel: [    0.000000]       .data : 0xc161bd30 - 0xc1902280   (2969 kB)
Jul 10 10:15:24 blotter kernel: [    0.000000]       .text : 0xc1000000 - 0xc161bd30   (6255 kB)
Jul 10 10:15:24 blotter kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 10 10:15:24 blotter kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jul 10 10:15:24 blotter kernel: [    0.000000] Hierarchical RCU implementation.
Jul 10 10:15:24 blotter kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul 10 10:15:24 blotter kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
Jul 10 10:15:24 blotter kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Jul 10 10:15:24 blotter kernel: [    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
Jul 10 10:15:24 blotter kernel: [    0.000000] Console: colour dummy device 80x25
Jul 10 10:15:24 blotter kernel: [    0.000000] console [tty0] enabled
Jul 10 10:15:24 blotter kernel: [    0.000000] hpet clockevent registered
Jul 10 10:15:24 blotter kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jul 10 10:15:24 blotter kernel: [    0.000000] tsc: Detected 1596.156 MHz processor
Jul 10 10:15:24 blotter kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.31 BogoMIPS (lpj=6384624)
Jul 10 10:15:24 blotter kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jul 10 10:15:24 blotter kernel: [    0.004093] Security Framework initialized
Jul 10 10:15:24 blotter kernel: [    0.004113] AppArmor: AppArmor initialized
Jul 10 10:15:24 blotter kernel: [    0.004118] Yama: becoming mindful.
Jul 10 10:15:24 blotter kernel: [    0.004234] Mount-cache hash table entries: 512
Jul 10 10:15:24 blotter kernel: [    0.004665] Initializing cgroup subsys cpuacct
Jul 10 10:15:24 blotter kernel: [    0.004673] Initializing cgroup subsys memory
Jul 10 10:15:24 blotter kernel: [    0.004692] Initializing cgroup subsys devices
Jul 10 10:15:24 blotter kernel: [    0.004698] Initializing cgroup subsys freezer
Jul 10 10:15:24 blotter kernel: [    0.004703] Initializing cgroup subsys blkio
Jul 10 10:15:24 blotter kernel: [    0.004709] Initializing cgroup subsys perf_event
Jul 10 10:15:24 blotter kernel: [    0.004717] Initializing cgroup subsys hugetlb
Jul 10 10:15:24 blotter kernel: [    0.004772] Disabled fast string operations
Jul 10 10:15:24 blotter kernel: [    0.004782] CPU: Physical Processor ID: 0
Jul 10 10:15:24 blotter kernel: [    0.004786] CPU: Processor Core ID: 0
Jul 10 10:15:24 blotter kernel: [    0.004792] mce: CPU supports 5 MCE banks
Jul 10 10:15:24 blotter kernel: [    0.004809] CPU0: Thermal monitoring enabled (TM2)
Jul 10 10:15:24 blotter kernel: [    0.004817] process: using mwait in idle threads
Jul 10 10:15:24 blotter kernel: [    0.004836] Last level iTLB entries: 4KB 32, 2MB 0, 4MB 0
Jul 10 10:15:24 blotter kernel: [    0.004836] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 8
Jul 10 10:15:24 blotter kernel: [    0.004836] tlb_flushall_shift: 6
Jul 10 10:15:24 blotter kernel: [    0.005230] Freeing SMP alternatives: 24k freed
Jul 10 10:15:24 blotter kernel: [    0.011236] ACPI: Core revision 20121018
Jul 10 10:15:24 blotter kernel: [    0.024029] ftrace: allocating 26123 entries in 52 pages
Jul 10 10:15:24 blotter kernel: [    0.044190] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 10 10:15:24 blotter kernel: [    0.044700] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 10 10:15:24 blotter kernel: [    0.087474] smpboot: CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz (fam: 06, model: 1c, stepping: 02)
Jul 10 10:15:24 blotter kernel: [    0.088000] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
Jul 10 10:15:24 blotter kernel: [    0.088000] ... version:                3
Jul 10 10:15:24 blotter kernel: [    0.088000] ... bit width:              40
Jul 10 10:15:24 blotter kernel: [    0.088000] ... generic registers:      2
Jul 10 10:15:24 blotter kernel: [    0.088000] ... value mask:             000000ffffffffff
Jul 10 10:15:24 blotter kernel: [    0.088000] ... max period:             000000007fffffff
Jul 10 10:15:24 blotter kernel: [    0.088000] ... fixed-purpose events:   3
Jul 10 10:15:24 blotter kernel: [    0.088000] ... event mask:             0000000700000003
Jul 10 10:15:24 blotter kernel: [    0.088000] CPU 1 irqstacks, hard=f5cd8000 soft=f5cda000
Jul 10 10:15:24 blotter kernel: [    0.088000] smpboot: Booting Node   0, Processors  #1 OK
Jul 10 10:15:24 blotter kernel: [    0.008000] Initializing CPU#1
Jul 10 10:15:24 blotter kernel: [    0.008000] Disabled fast string operations
Jul 10 10:15:24 blotter kernel: [    0.100059] Brought up 2 CPUs
Jul 10 10:15:24 blotter kernel: [    0.100074] smpboot: Total of 2 processors activated (6384.62 BogoMIPS)
Jul 10 10:15:24 blotter kernel: [    0.100257] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 10 10:15:24 blotter kernel: [    0.100869] devtmpfs: initialized
Jul 10 10:15:24 blotter kernel: [    0.100869] EVM: security.selinux
Jul 10 10:15:24 blotter kernel: [    0.100869] EVM: security.SMACK64
Jul 10 10:15:24 blotter kernel: [    0.100869] EVM: security.capability
Jul 10 10:15:24 blotter kernel: [    0.104136] PM: Registering ACPI NVS region [mem 0x3f66d000-0x3f6befff] (335872 bytes)
Jul 10 10:15:24 blotter kernel: [    0.104586] regulator-dummy: no parameters
Jul 10 10:15:24 blotter kernel: [    0.104739] NET: Registered protocol family 16
Jul 10 10:15:24 blotter kernel: [    0.105113] EISA bus registered
Jul 10 10:15:24 blotter kernel: [    0.105318] ACPI: bus type pci registered
Jul 10 10:15:24 blotter kernel: [    0.105487] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 10 10:15:24 blotter kernel: [    0.105496] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jul 10 10:15:24 blotter kernel: [    0.105500] PCI: Using MMCONFIG for extended config space
Jul 10 10:15:24 blotter kernel: [    0.105504] PCI: Using configuration type 1 for base access
Jul 10 10:15:24 blotter kernel: [    0.108624] bio: create slab <bio-0> at 0
Jul 10 10:15:24 blotter kernel: [    0.108624] ACPI: Added _OSI(Module Device)
Jul 10 10:15:24 blotter kernel: [    0.108624] ACPI: Added _OSI(Processor Device)
Jul 10 10:15:24 blotter kernel: [    0.108624] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 10 10:15:24 blotter kernel: [    0.108624] ACPI: Added _OSI(Processor Aggregator Device)
Jul 10 10:15:24 blotter kernel: [    0.112622] ACPI: EC: Look up EC in DSDT
Jul 10 10:15:24 blotter kernel: [    0.116267] ACPI: Executed 1 blocks of module-level executable AML code
Jul 10 10:15:24 blotter kernel: [    0.120151] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 10 10:15:24 blotter kernel: [    0.121208] ACPI: SSDT 3f5b7c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.122090] ACPI: Dynamic OEM Table Load:
Jul 10 10:15:24 blotter kernel: [    0.122098] ACPI: SSDT   (null) 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.122374] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.123207] ACPI: Dynamic OEM Table Load:
Jul 10 10:15:24 blotter kernel: [    0.123214] ACPI: SSDT   (null) 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.124032] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.124892] ACPI: Dynamic OEM Table Load:
Jul 10 10:15:24 blotter kernel: [    0.124900] ACPI: SSDT   (null) 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.125171] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.126020] ACPI: Dynamic OEM Table Load:
Jul 10 10:15:24 blotter kernel: [    0.126027] ACPI: SSDT   (null) 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Jul 10 10:15:24 blotter kernel: [    0.128766] ACPI: Interpreter enabled
Jul 10 10:15:24 blotter kernel: [    0.128783] ACPI: (supports S0 S3 S4 S5)
Jul 10 10:15:24 blotter kernel: [    0.128833] ACPI: Using IOAPIC for interrupt routing
Jul 10 10:15:24 blotter kernel: [    0.266234] ACPI: Power Resource [FN00] (on)
Jul 10 10:15:24 blotter kernel: [    0.267059] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Jul 10 10:15:24 blotter kernel: [    0.267408] ACPI: No dock devices found.
Jul 10 10:15:24 blotter kernel: [    0.267422] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 10 10:15:24 blotter kernel: [    0.268264] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 10 10:15:24 blotter kernel: [    0.268273] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 10 10:15:24 blotter kernel: [    0.268659] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dsfield-211)
Jul 10 10:15:24 blotter kernel: [    0.268675] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 10 10:15:24 blotter kernel: [    0.268692] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Jul 10 10:15:24 blotter kernel: [    0.270332] PCI host bridge to bus 0000:00
Jul 10 10:15:24 blotter kernel: [    0.270343] pci_bus 0000:00: root bus resource [bus 00-ff]
Jul 10 10:15:24 blotter kernel: [    0.270350] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jul 10 10:15:24 blotter kernel: [    0.270357] pci_bus 0000:00: root bus resource [io  0x0d00-0xefff]
Jul 10 10:15:24 blotter kernel: [    0.270363] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jul 10 10:15:24 blotter kernel: [    0.270370] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfebfffff]
Jul 10 10:15:24 blotter kernel: [    0.270394] pci 0000:00:00.0: [8086:27ac] type 00 class 0x060000
Jul 10 10:15:24 blotter kernel: [    0.270470] pci 0000:00:02.0: [8086:27ae] type 00 class 0x030000
Jul 10 10:15:24 blotter kernel: [    0.270490] pci 0000:00:02.0: reg 10: [mem 0x58280000-0x582fffff]
Jul 10 10:15:24 blotter kernel: [    0.270503] pci 0000:00:02.0: reg 14: [io  0x60f0-0x60f7]
Jul 10 10:15:24 blotter kernel: [    0.270515] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
Jul 10 10:15:24 blotter kernel: [    0.270527] pci 0000:00:02.0: reg 1c: [mem 0x58300000-0x5833ffff]
Jul 10 10:15:24 blotter kernel: [    0.270591] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
Jul 10 10:15:24 blotter kernel: [    0.270608] pci 0000:00:02.1: reg 10: [mem 0x58200000-0x5827ffff]
Jul 10 10:15:24 blotter kernel: [    0.270747] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
Jul 10 10:15:24 blotter kernel: [    0.270779] pci 0000:00:1b.0: reg 10: [mem 0x58340000-0x58343fff 64bit]
Jul 10 10:15:24 blotter kernel: [    0.270902] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 10 10:15:24 blotter kernel: [    0.270949] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
Jul 10 10:15:24 blotter kernel: [    0.271078] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 10 10:15:24 blotter kernel: [    0.271126] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
Jul 10 10:15:24 blotter kernel: [    0.271253] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jul 10 10:15:24 blotter kernel: [    0.271302] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
Jul 10 10:15:24 blotter kernel: [    0.271429] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jul 10 10:15:24 blotter kernel: [    0.271478] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
Jul 10 10:15:24 blotter kernel: [    0.271605] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul 10 10:15:24 blotter kernel: [    0.271654] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
Jul 10 10:15:24 blotter kernel: [    0.271722] pci 0000:00:1d.0: reg 20: [io  0x60a0-0x60bf]
Jul 10 10:15:24 blotter kernel: [    0.271780] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
Jul 10 10:15:24 blotter kernel: [    0.271847] pci 0000:00:1d.1: reg 20: [io  0x6080-0x609f]
Jul 10 10:15:24 blotter kernel: [    0.271906] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
Jul 10 10:15:24 blotter kernel: [    0.271973] pci 0000:00:1d.2: reg 20: [io  0x6060-0x607f]
Jul 10 10:15:24 blotter kernel: [    0.272051] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
Jul 10 10:15:24 blotter kernel: [    0.272119] pci 0000:00:1d.3: reg 20: [io  0x6040-0x605f]
Jul 10 10:15:24 blotter kernel: [    0.272192] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
Jul 10 10:15:24 blotter kernel: [    0.272224] pci 0000:00:1d.7: reg 10: [mem 0x58344400-0x583447ff]
Jul 10 10:15:24 blotter kernel: [    0.272348] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul 10 10:15:24 blotter kernel: [    0.272386] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
Jul 10 10:15:24 blotter kernel: [    0.272513] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
Jul 10 10:15:24 blotter kernel: [    0.272650] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
Jul 10 10:15:24 blotter kernel: [    0.272659] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
Jul 10 10:15:24 blotter kernel: [    0.272741] pci 0000:00:1f.2: [8086:27c5] type 00 class 0x010601
Jul 10 10:15:24 blotter kernel: [    0.272773] pci 0000:00:1f.2: reg 10: [io  0x60d8-0x60df]
Jul 10 10:15:24 blotter kernel: [    0.272791] pci 0000:00:1f.2: reg 14: [io  0x60fc-0x60ff]
Jul 10 10:15:24 blotter kernel: [    0.272809] pci 0000:00:1f.2: reg 18: [io  0x60d0-0x60d7]
Jul 10 10:15:24 blotter kernel: [    0.272826] pci 0000:00:1f.2: reg 1c: [io  0x60f8-0x60fb]
Jul 10 10:15:24 blotter kernel: [    0.272844] pci 0000:00:1f.2: reg 20: [io  0x6020-0x602f]
Jul 10 10:15:24 blotter kernel: [    0.272862] pci 0000:00:1f.2: reg 24: [mem 0x58344000-0x583443ff]
Jul 10 10:15:24 blotter kernel: [    0.272932] pci 0000:00:1f.2: PME# supported from D3hot
Jul 10 10:15:24 blotter kernel: [    0.272967] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
Jul 10 10:15:24 blotter kernel: [    0.273051] pci 0000:00:1f.3: reg 20: [io  0x6000-0x601f]
Jul 10 10:15:24 blotter kernel: [    0.273291] pci 0000:01:00.0: [14e4:4315] type 00 class 0x028000
Jul 10 10:15:24 blotter kernel: [    0.273369] pci 0000:01:00.0: reg 10: [mem 0x57100000-0x57103fff 64bit]
Jul 10 10:15:24 blotter kernel: [    0.273768] pci 0000:01:00.0: supports D1 D2
Jul 10 10:15:24 blotter kernel: [    0.273954] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jul 10 10:15:24 blotter kernel: [    0.273964] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Jul 10 10:15:24 blotter kernel: [    0.273974] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
Jul 10 10:15:24 blotter kernel: [    0.273987] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.274063] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jul 10 10:15:24 blotter kernel: [    0.274073] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jul 10 10:15:24 blotter kernel: [    0.274083] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
Jul 10 10:15:24 blotter kernel: [    0.274096] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.274201] pci 0000:03:00.0: [1969:1062] type 00 class 0x020000
Jul 10 10:15:24 blotter kernel: [    0.274241] pci 0000:03:00.0: reg 10: [mem 0x55000000-0x5503ffff 64bit]
Jul 10 10:15:24 blotter kernel: [    0.274264] pci 0000:03:00.0: reg 18: [io  0x2000-0x207f]
Jul 10 10:15:24 blotter kernel: [    0.274426] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 10 10:15:24 blotter kernel: [    0.280040] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jul 10 10:15:24 blotter kernel: [    0.280051] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
Jul 10 10:15:24 blotter kernel: [    0.280061] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
Jul 10 10:15:24 blotter kernel: [    0.280074] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.280156] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jul 10 10:15:24 blotter kernel: [    0.280166] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
Jul 10 10:15:24 blotter kernel: [    0.280176] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
Jul 10 10:15:24 blotter kernel: [    0.280189] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.280294] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)
Jul 10 10:15:24 blotter kernel: [    0.280315] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 10 10:15:24 blotter kernel: [    0.280321] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xefff] (subtractive decode)
Jul 10 10:15:24 blotter kernel: [    0.280328] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 10 10:15:24 blotter kernel: [    0.280334] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
Jul 10 10:15:24 blotter kernel: [    0.280375] pci_bus 0000:00: on NUMA node 0
Jul 10 10:15:24 blotter kernel: [    0.280480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Jul 10 10:15:24 blotter kernel: [    0.280669] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Jul 10 10:15:24 blotter kernel: [    0.280798] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Jul 10 10:15:24 blotter kernel: [    0.280929] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Jul 10 10:15:24 blotter kernel: [    0.281229] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dsfield-211)
Jul 10 10:15:24 blotter kernel: [    0.281245] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 10 10:15:24 blotter kernel: [    0.281270]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
Jul 10 10:15:24 blotter kernel: [    0.281276]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
Jul 10 10:15:24 blotter kernel: [    0.283740] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Jul 10 10:15:24 blotter kernel: [    0.283899] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Jul 10 10:15:24 blotter kernel: [    0.284072] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Jul 10 10:15:24 blotter kernel: [    0.284226] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Jul 10 10:15:24 blotter kernel: [    0.284380] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 10 10:15:24 blotter kernel: [    0.284535] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 10 10:15:24 blotter kernel: [    0.284690] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 10 10:15:24 blotter kernel: [    0.284845] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 10 10:15:24 blotter kernel: [    0.285139] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jul 10 10:15:24 blotter kernel: [    0.285139] vgaarb: loaded
Jul 10 10:15:24 blotter kernel: [    0.285139] vgaarb: bridge control possible 0000:00:02.0
Jul 10 10:15:24 blotter kernel: [    0.285139] SCSI subsystem initialized
Jul 10 10:15:24 blotter kernel: [    0.285139] ACPI: bus type scsi registered
Jul 10 10:15:24 blotter kernel: [    0.285139] libata version 3.00 loaded.
Jul 10 10:15:24 blotter kernel: [    0.285139] ACPI: bus type usb registered
Jul 10 10:15:24 blotter kernel: [    0.285139] usbcore: registered new interface driver usbfs
Jul 10 10:15:24 blotter kernel: [    0.285139] usbcore: registered new interface driver hub
Jul 10 10:15:24 blotter kernel: [    0.285139] usbcore: registered new device driver usb
Jul 10 10:15:24 blotter kernel: [    0.285139] PCI: Using ACPI for IRQ routing
Jul 10 10:15:24 blotter kernel: [    0.295309] PCI: pci_cache_line_size set to 64 bytes
Jul 10 10:15:24 blotter kernel: [    0.295498] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Jul 10 10:15:24 blotter kernel: [    0.295505] e820: reserve RAM buffer [mem 0x3f576000-0x3fffffff]
Jul 10 10:15:24 blotter kernel: [    0.295511] e820: reserve RAM buffer [mem 0x3f66d000-0x3fffffff]
Jul 10 10:15:24 blotter kernel: [    0.295516] e820: reserve RAM buffer [mem 0x3f6ee000-0x3fffffff]
Jul 10 10:15:24 blotter kernel: [    0.295521] e820: reserve RAM buffer [mem 0x3f700000-0x3fffffff]
Jul 10 10:15:24 blotter kernel: [    0.295792] NetLabel: Initializing
Jul 10 10:15:24 blotter kernel: [    0.295798] NetLabel:  domain hash size = 128
Jul 10 10:15:24 blotter kernel: [    0.295801] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 10 10:15:24 blotter kernel: [    0.295827] NetLabel:  unlabeled traffic allowed by default
Jul 10 10:15:24 blotter kernel: [    0.296082] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 10 10:15:24 blotter kernel: [    0.296098] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 10 10:15:24 blotter kernel: [    0.296109] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jul 10 10:15:24 blotter kernel: [    0.300042] Switching to clocksource hpet
Jul 10 10:15:24 blotter kernel: [    0.315899] AppArmor: AppArmor Filesystem Enabled
Jul 10 10:15:24 blotter kernel: [    0.315976] pnp: PnP ACPI init
Jul 10 10:15:24 blotter kernel: [    0.316066] ACPI: bus type pnp registered
Jul 10 10:15:24 blotter kernel: [    0.380440] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x1000-0x1fff]
Jul 10 10:15:24 blotter kernel: [    0.380561] system 00:00: [io  0x0200-0x020f] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380571] system 00:00: [io  0x0600-0x060f] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380587] system 00:00: [io  0x0610] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380595] system 00:00: [io  0x0800-0x080f] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380602] system 00:00: [io  0x0400-0x047f] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380609] system 00:00: [io  0x0500-0x053f] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380617] system 00:00: [io  0xff2c-0xff2f] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380626] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380634] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380641] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380649] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380656] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380664] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 10 10:15:24 blotter kernel: [    0.380672] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 10 10:15:24 blotter kernel: [    0.380683] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 10 10:15:24 blotter kernel: [    0.380717] pnp 00:01: [dma 4]
Jul 10 10:15:24 blotter kernel: [    0.380771] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 10 10:15:24 blotter kernel: [    0.380885] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 10 10:15:24 blotter kernel: [    0.381132] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Jul 10 10:15:24 blotter kernel: [    0.381222] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 10 10:15:24 blotter kernel: [    0.381299] pnp 00:05: Plug and Play ACPI device, IDs INT0800 (active)
Jul 10 10:15:24 blotter kernel: [    0.381426] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 10 10:15:24 blotter kernel: [    0.381645] pnp 00:07: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
Jul 10 10:15:24 blotter kernel: [    0.382064] pnp: PnP ACPI: found 8 devices
Jul 10 10:15:24 blotter kernel: [    0.382070] ACPI: ACPI bus type pnp unregistered
Jul 10 10:15:24 blotter kernel: [    0.382078] PnPBIOS: Disabled by ACPI PNP
Jul 10 10:15:24 blotter kernel: [    0.422933] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jul 10 10:15:24 blotter kernel: [    0.422946] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Jul 10 10:15:24 blotter kernel: [    0.422959] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
Jul 10 10:15:24 blotter kernel: [    0.422969] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.422982] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jul 10 10:15:24 blotter kernel: [    0.422990] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jul 10 10:15:24 blotter kernel: [    0.423001] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
Jul 10 10:15:24 blotter kernel: [    0.423011] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.423024] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jul 10 10:15:24 blotter kernel: [    0.423032] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
Jul 10 10:15:24 blotter kernel: [    0.423043] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
Jul 10 10:15:24 blotter kernel: [    0.423053] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.423065] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jul 10 10:15:24 blotter kernel: [    0.423073] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
Jul 10 10:15:24 blotter kernel: [    0.423084] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
Jul 10 10:15:24 blotter kernel: [    0.423094] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.423107] pci 0000:00:1e.0: PCI bridge to [bus 05]
Jul 10 10:15:24 blotter kernel: [    0.423165] pci 0000:00:1c.1: enabling device (0000 -> 0003)
Jul 10 10:15:24 blotter kernel: [    0.423206] pci 0000:00:1c.3: enabling device (0000 -> 0003)
Jul 10 10:15:24 blotter kernel: [    0.423239] pci 0000:00:1e.0: setting latency timer to 64
Jul 10 10:15:24 blotter kernel: [    0.423250] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 10 10:15:24 blotter kernel: [    0.423257] pci_bus 0000:00: resource 5 [io  0x0d00-0xefff]
Jul 10 10:15:24 blotter kernel: [    0.423263] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 10 10:15:24 blotter kernel: [    0.423270] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
Jul 10 10:15:24 blotter kernel: [    0.423277] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
Jul 10 10:15:24 blotter kernel: [    0.423283] pci_bus 0000:01: resource 1 [mem 0x57100000-0x581fffff]
Jul 10 10:15:24 blotter kernel: [    0.423290] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.423297] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
Jul 10 10:15:24 blotter kernel: [    0.423304] pci_bus 0000:02: resource 1 [mem 0x56100000-0x570fffff]
Jul 10 10:15:24 blotter kernel: [    0.423311] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.423317] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
Jul 10 10:15:24 blotter kernel: [    0.423324] pci_bus 0000:03: resource 1 [mem 0x55000000-0x560fffff]
Jul 10 10:15:24 blotter kernel: [    0.423331] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.423338] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
Jul 10 10:15:24 blotter kernel: [    0.423344] pci_bus 0000:04: resource 1 [mem 0x54000000-0x54ffffff]
Jul 10 10:15:24 blotter kernel: [    0.423351] pci_bus 0000:04: resource 2 [mem 0x53000000-0x53ffffff 64bit pref]
Jul 10 10:15:24 blotter kernel: [    0.423358] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jul 10 10:15:24 blotter kernel: [    0.423365] pci_bus 0000:05: resource 5 [io  0x0d00-0xefff]
Jul 10 10:15:24 blotter kernel: [    0.423371] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jul 10 10:15:24 blotter kernel: [    0.423378] pci_bus 0000:05: resource 7 [mem 0x40000000-0xfebfffff]
Jul 10 10:15:24 blotter kernel: [    0.423458] NET: Registered protocol family 2
Jul 10 10:15:24 blotter kernel: [    0.423772] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Jul 10 10:15:24 blotter kernel: [    0.423836] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jul 10 10:15:24 blotter kernel: [    0.423895] TCP: Hash tables configured (established 8192 bind 8192)
Jul 10 10:15:24 blotter kernel: [    0.423941] TCP: reno registered
Jul 10 10:15:24 blotter kernel: [    0.423949] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul 10 10:15:24 blotter kernel: [    0.423967] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul 10 10:15:24 blotter kernel: [    0.424145] NET: Registered protocol family 1
Jul 10 10:15:24 blotter kernel: [    0.424183] pci 0000:00:02.0: Boot video device
Jul 10 10:15:24 blotter kernel: [    0.424545] PCI: CLS 0 bytes, default 64
Jul 10 10:15:24 blotter kernel: [    0.424672] Trying to unpack rootfs image as initramfs...
Jul 10 10:15:24 blotter kernel: [    1.133647] Freeing initrd memory: 16256k freed
Jul 10 10:15:24 blotter kernel: [    1.150423] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
Jul 10 10:15:24 blotter kernel: [    1.150433] Simple Boot Flag at 0x44 set to 0x1
Jul 10 10:15:24 blotter kernel: [    1.151111] Initialise module verification
Jul 10 10:15:24 blotter kernel: [    1.151216] audit: initializing netlink socket (disabled)
Jul 10 10:15:24 blotter kernel: [    1.151244] type=2000 audit(1373465707.148:1): initialized
Jul 10 10:15:24 blotter kernel: [    1.199294] bounce pool size: 64 pages
Jul 10 10:15:24 blotter kernel: [    1.199322] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 10 10:15:24 blotter kernel: [    1.203270] VFS: Disk quotas dquot_6.5.2
Jul 10 10:15:24 blotter kernel: [    1.203409] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 10 10:15:24 blotter kernel: [    1.204924] fuse init (API version 7.20)
Jul 10 10:15:24 blotter kernel: [    1.205163] msgmni has been set to 1740
Jul 10 10:15:24 blotter kernel: [    1.206340] Key type asymmetric registered
Jul 10 10:15:24 blotter kernel: [    1.206348] Asymmetric key parser 'x509' registered
Jul 10 10:15:24 blotter kernel: [    1.206464] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jul 10 10:15:24 blotter kernel: [    1.206545] io scheduler noop registered
Jul 10 10:15:24 blotter kernel: [    1.206552] io scheduler deadline registered (default)
Jul 10 10:15:24 blotter kernel: [    1.206579] io scheduler cfq registered
Jul 10 10:15:24 blotter kernel: [    1.206920] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Jul 10 10:15:24 blotter kernel: [    1.207111] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
Jul 10 10:15:24 blotter kernel: [    1.207291] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Jul 10 10:15:24 blotter kernel: [    1.207474] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
Jul 10 10:15:24 blotter kernel: [    1.207655] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 10 10:15:24 blotter kernel: [    1.207707] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 10 10:15:24 blotter kernel: [    1.207835] intel_idle: MWAIT substates: 0x20220
Jul 10 10:15:24 blotter kernel: [    1.207856] intel_idle: v0.4 model 0x1C
Jul 10 10:15:24 blotter kernel: [    1.207861] intel_idle: lapic_timer_reliable_states 0x2
Jul 10 10:15:24 blotter kernel: [    1.207868] tsc: Marking TSC unstable due to TSC halts in idle states deeper than C2
Jul 10 10:15:24 blotter kernel: [    1.332096] ACPI: AC Adapter [AC] (on-line)
Jul 10 10:15:24 blotter kernel: [    1.332266] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 10 10:15:24 blotter kernel: [    1.332278] ACPI: Power Button [PWRB]
Jul 10 10:15:24 blotter kernel: [    1.332383] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jul 10 10:15:24 blotter kernel: [    1.332425] ACPI: Lid Switch [LID0]
Jul 10 10:15:24 blotter kernel: [    1.332526] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jul 10 10:15:24 blotter kernel: [    1.332535] ACPI: Sleep Button [SLPB]
Jul 10 10:15:24 blotter kernel: [    1.332651] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jul 10 10:15:24 blotter kernel: [    1.332660] ACPI: Power Button [PWRF]
Jul 10 10:15:24 blotter kernel: [    1.332813] ACPI: Fan [FAN] (on)
Jul 10 10:15:24 blotter kernel: [    1.332948] ACPI: Requesting acpi_cpufreq
Jul 10 10:15:24 blotter kernel: [    1.467035] thermal LNXTHERM:00: registered as thermal_zone0
Jul 10 10:15:24 blotter kernel: [    1.467044] ACPI: Thermal Zone [THRM] (27 C)
Jul 10 10:15:24 blotter kernel: [    1.467137] GHES: HEST is not enabled!
Jul 10 10:15:24 blotter kernel: [    1.467297] isapnp: Scanning for PnP cards...
Jul 10 10:15:24 blotter kernel: [    1.468250] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 10 10:15:24 blotter kernel: [    1.821358] isapnp: No Plug & Play device found
Jul 10 10:15:24 blotter kernel: [    2.124262] ACPI: Battery Slot [BAT0] (battery present)
Jul 10 10:15:24 blotter kernel: [    2.124499] Linux agpgart interface v0.103
Jul 10 10:15:24 blotter kernel: [    2.124651] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Jul 10 10:15:24 blotter kernel: [    2.124822] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
Jul 10 10:15:24 blotter kernel: [    2.124984] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Jul 10 10:15:24 blotter kernel: [    2.125264] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
Jul 10 10:15:24 blotter kernel: [    2.129464] brd: module loaded
Jul 10 10:15:24 blotter kernel: [    2.131645] loop: module loaded
Jul 10 10:15:24 blotter kernel: [    2.132886] libphy: Fixed MDIO Bus: probed
Jul 10 10:15:24 blotter kernel: [    2.133115] tun: Universal TUN/TAP device driver, 1.6
Jul 10 10:15:24 blotter kernel: [    2.133120] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 10 10:15:24 blotter kernel: [    2.133284] PPP generic driver version 2.4.2
Jul 10 10:15:24 blotter kernel: [    2.133438] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 10 10:15:24 blotter kernel: [    2.133444] ehci-pci: EHCI PCI platform driver
Jul 10 10:15:24 blotter kernel: [    2.133521] ehci-pci 0000:00:1d.7: setting latency timer to 64
Jul 10 10:15:24 blotter kernel: [    2.133531] ehci-pci 0000:00:1d.7: EHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.133545] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul 10 10:15:24 blotter kernel: [    2.133572] ehci-pci 0000:00:1d.7: debug port 1
Jul 10 10:15:24 blotter kernel: [    2.137497] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
Jul 10 10:15:24 blotter kernel: [    2.137538] ehci-pci 0000:00:1d.7: irq 16, io mem 0x58344400
Jul 10 10:15:24 blotter kernel: [    2.148049] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul 10 10:15:24 blotter kernel: [    2.148114] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jul 10 10:15:24 blotter kernel: [    2.148121] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 10 10:15:24 blotter kernel: [    2.148128] usb usb1: Product: EHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.148134] usb usb1: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
Jul 10 10:15:24 blotter kernel: [    2.148139] usb usb1: SerialNumber: 0000:00:1d.7
Jul 10 10:15:24 blotter kernel: [    2.148483] hub 1-0:1.0: USB hub found
Jul 10 10:15:24 blotter kernel: [    2.148497] hub 1-0:1.0: 8 ports detected
Jul 10 10:15:24 blotter kernel: [    2.148841] ehci-platform: EHCI generic platform driver
Jul 10 10:15:24 blotter kernel: [    2.148872] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 10 10:15:24 blotter kernel: [    2.148922] uhci_hcd: USB Universal Host Controller Interface driver
Jul 10 10:15:24 blotter kernel: [    2.148975] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul 10 10:15:24 blotter kernel: [    2.148984] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.148998] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul 10 10:15:24 blotter kernel: [    2.149044] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
Jul 10 10:15:24 blotter kernel: [    2.149128] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Jul 10 10:15:24 blotter kernel: [    2.149136] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 10 10:15:24 blotter kernel: [    2.149142] usb usb2: Product: UHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.149148] usb usb2: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 10 10:15:24 blotter kernel: [    2.149153] usb usb2: SerialNumber: 0000:00:1d.0
Jul 10 10:15:24 blotter kernel: [    2.149429] hub 2-0:1.0: USB hub found
Jul 10 10:15:24 blotter kernel: [    2.149443] hub 2-0:1.0: 2 ports detected
Jul 10 10:15:24 blotter kernel: [    2.149624] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul 10 10:15:24 blotter kernel: [    2.149632] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.149646] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul 10 10:15:24 blotter kernel: [    2.149718] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
Jul 10 10:15:24 blotter kernel: [    2.149800] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jul 10 10:15:24 blotter kernel: [    2.149807] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 10 10:15:24 blotter kernel: [    2.149813] usb usb3: Product: UHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.149819] usb usb3: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 10 10:15:24 blotter kernel: [    2.149825] usb usb3: SerialNumber: 0000:00:1d.1
Jul 10 10:15:24 blotter kernel: [    2.150075] hub 3-0:1.0: USB hub found
Jul 10 10:15:24 blotter kernel: [    2.150087] hub 3-0:1.0: 2 ports detected
Jul 10 10:15:24 blotter kernel: [    2.150262] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul 10 10:15:24 blotter kernel: [    2.150271] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.150285] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul 10 10:15:24 blotter kernel: [    2.150350] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
Jul 10 10:15:24 blotter kernel: [    2.150430] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jul 10 10:15:24 blotter kernel: [    2.150438] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 10 10:15:24 blotter kernel: [    2.150444] usb usb4: Product: UHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.150450] usb usb4: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 10 10:15:24 blotter kernel: [    2.150456] usb usb4: SerialNumber: 0000:00:1d.2
Jul 10 10:15:24 blotter kernel: [    2.150701] hub 4-0:1.0: USB hub found
Jul 10 10:15:24 blotter kernel: [    2.150713] hub 4-0:1.0: 2 ports detected
Jul 10 10:15:24 blotter kernel: [    2.150899] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jul 10 10:15:24 blotter kernel: [    2.150907] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.150921] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jul 10 10:15:24 blotter kernel: [    2.150981] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
Jul 10 10:15:24 blotter kernel: [    2.151061] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jul 10 10:15:24 blotter kernel: [    2.151069] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 10 10:15:24 blotter kernel: [    2.151075] usb usb5: Product: UHCI Host Controller
Jul 10 10:15:24 blotter kernel: [    2.151081] usb usb5: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 10 10:15:24 blotter kernel: [    2.151087] usb usb5: SerialNumber: 0000:00:1d.3
Jul 10 10:15:24 blotter kernel: [    2.151360] hub 5-0:1.0: USB hub found
Jul 10 10:15:24 blotter kernel: [    2.151373] hub 5-0:1.0: 2 ports detected
Jul 10 10:15:24 blotter kernel: [    2.151776] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
Jul 10 10:15:24 blotter kernel: [    2.172477] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 10 10:15:24 blotter kernel: [    2.172498] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 10 10:15:24 blotter kernel: [    2.172851] mousedev: PS/2 mouse device common for all mice
Jul 10 10:15:24 blotter kernel: [    2.173403] rtc_cmos 00:02: RTC can wake from S4
Jul 10 10:15:24 blotter kernel: [    2.173639] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jul 10 10:15:24 blotter kernel: [    2.173689] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jul 10 10:15:24 blotter kernel: [    2.173932] device-mapper: uevent: version 1.0.3
Jul 10 10:15:24 blotter kernel: [    2.174110] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
Jul 10 10:15:24 blotter kernel: [    2.174161] EISA: Probing bus 0 at eisa.0
Jul 10 10:15:24 blotter kernel: [    2.174167] EISA: Cannot allocate resource for mainboard
Jul 10 10:15:24 blotter kernel: [    2.174173] Cannot allocate resource for EISA slot 1
Jul 10 10:15:24 blotter kernel: [    2.174178] Cannot allocate resource for EISA slot 2
Jul 10 10:15:24 blotter kernel: [    2.174183] Cannot allocate resource for EISA slot 3
Jul 10 10:15:24 blotter kernel: [    2.174188] Cannot allocate resource for EISA slot 4
Jul 10 10:15:24 blotter kernel: [    2.174193] Cannot allocate resource for EISA slot 5
Jul 10 10:15:24 blotter kernel: [    2.174198] Cannot allocate resource for EISA slot 6
Jul 10 10:15:24 blotter kernel: [    2.174203] Cannot allocate resource for EISA slot 7
Jul 10 10:15:24 blotter kernel: [    2.174208] Cannot allocate resource for EISA slot 8
Jul 10 10:15:24 blotter kernel: [    2.174211] EISA: Detected 0 cards.
Jul 10 10:15:24 blotter kernel: [    2.174230] cpufreq-nforce2: No nForce2 chipset.
Jul 10 10:15:24 blotter kernel: [    2.174325] cpuidle: using governor ladder
Jul 10 10:15:24 blotter kernel: [    2.174450] cpuidle: using governor menu
Jul 10 10:15:24 blotter kernel: [    2.174459] ledtrig-cpu: registered to indicate activity on CPUs
Jul 10 10:15:24 blotter kernel: [    2.174464] EFI Variables Facility v0.08 2004-May-17
Jul 10 10:15:24 blotter kernel: [    2.175050] ashmem: initialized
Jul 10 10:15:24 blotter kernel: [    2.175390] TCP: cubic registered
Jul 10 10:15:24 blotter kernel: [    2.175658] NET: Registered protocol family 10
Jul 10 10:15:24 blotter kernel: [    2.176125] NET: Registered protocol family 17
Jul 10 10:15:24 blotter kernel: [    2.176177] Key type dns_resolver registered
Jul 10 10:15:24 blotter kernel: [    2.176623] Using IPI No-Shortcut mode
Jul 10 10:15:24 blotter kernel: [    2.176954] Loading module verification certificates
Jul 10 10:15:24 blotter kernel: [    2.189368] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d1850ecb2327d153922b22332b63536822dc0add'
Jul 10 10:15:24 blotter kernel: [    2.189407] registered taskstats version 1
Jul 10 10:15:24 blotter kernel: [    2.196441] Key type trusted registered
Jul 10 10:15:24 blotter kernel: [    2.200767] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jul 10 10:15:24 blotter kernel: [    2.203560] Key type encrypted registered
Jul 10 10:15:24 blotter kernel: [    2.213303] rtc_cmos 00:02: setting system clock to 2013-07-10 14:15:08 UTC (1373465708)
Jul 10 10:15:24 blotter kernel: [    2.215045] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 10 10:15:24 blotter kernel: [    2.215050] EDD information not available.
Jul 10 10:15:24 blotter kernel: [    2.215431] Freeing unused kernel memory: 788k freed
Jul 10 10:15:24 blotter kernel: [    2.216148] Write protecting the kernel text: 6256k
Jul 10 10:15:24 blotter kernel: [    2.216342] Write protecting the kernel read-only data: 2432k
Jul 10 10:15:24 blotter kernel: [    2.216349] NX-protecting the kernel data: 3984k
Jul 10 10:15:24 blotter kernel: [    2.460090] usb 1-2: new high-speed USB device number 2 using ehci-pci
Jul 10 10:15:24 blotter kernel: [    2.626252] usb 1-2: New USB device found, idVendor=04f2, idProduct=b175
Jul 10 10:15:24 blotter kernel: [    2.626268] usb 1-2: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jul 10 10:15:24 blotter kernel: [    2.626278] usb 1-2: Product: CNF9011
Jul 10 10:15:24 blotter kernel: [    2.626287] usb 1-2: Manufacturer: Chicony Electronics Co., Ltd.
Jul 10 10:15:24 blotter kernel: [    2.626296] usb 1-2: SerialNumber: SN0001
Jul 10 10:15:24 blotter kernel: [    2.640659] Disabling lock debugging due to kernel taint
Jul 10 10:15:24 blotter kernel: [    2.644492] ahci 0000:00:1f.2: version 3.0
Jul 10 10:15:24 blotter kernel: [    2.644651] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
Jul 10 10:15:24 blotter kernel: [    2.644762] ahci: SSS flag set, parallel bus scan disabled
Jul 10 10:15:24 blotter kernel: [    2.644831] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
Jul 10 10:15:24 blotter kernel: [    2.644844] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
Jul 10 10:15:24 blotter kernel: [    2.644859] ahci 0000:00:1f.2: setting latency timer to 64
Jul 10 10:15:24 blotter kernel: [    2.646924] scsi0 : ahci
Jul 10 10:15:24 blotter kernel: [    2.649142] atl1c 0000:03:00.0: version 1.0.1.1-NAPI
Jul 10 10:15:24 blotter kernel: [    2.651511] scsi1 : ahci
Jul 10 10:15:24 blotter kernel: [    2.653705] scsi2 : ahci
Jul 10 10:15:24 blotter kernel: [    2.657412] scsi3 : ahci
Jul 10 10:15:24 blotter kernel: [    2.657646] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 44
Jul 10 10:15:24 blotter kernel: [    2.657656] ata2: DUMMY
Jul 10 10:15:24 blotter kernel: [    2.657666] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 44
Jul 10 10:15:24 blotter kernel: [    2.657673] ata4: DUMMY
Jul 10 10:15:24 blotter kernel: [    2.976166] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 10 10:15:24 blotter kernel: [    2.977436] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 10 10:15:24 blotter kernel: [    3.017924] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
Jul 10 10:15:24 blotter kernel: [    3.017940] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 10 10:15:24 blotter kernel: [    3.019819] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Jul 10 10:15:24 blotter kernel: [    3.020129] ata1.00: configured for UDMA/133
Jul 10 10:15:24 blotter kernel: [    3.020593] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
Jul 10 10:15:24 blotter kernel: [    3.021099] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jul 10 10:15:24 blotter kernel: [    3.021252] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 10 10:15:24 blotter kernel: [    3.021441] sd 0:0:0:0: [sda] Write Protect is off
Jul 10 10:15:24 blotter kernel: [    3.021453] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 10 10:15:24 blotter kernel: [    3.021621] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 10 10:15:24 blotter kernel: [    3.039403]  sda: sda1 sda2 < sda5 >
Jul 10 10:15:24 blotter kernel: [    3.040696] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 10 10:15:24 blotter kernel: [    3.340161] ata3: SATA link down (SStatus 0 SControl 300)
Jul 10 10:15:24 blotter kernel: [    3.616367] bio: create slab <bio-1> at 1
Jul 10 10:15:24 blotter kernel: [    4.011429] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Jul 10 10:15:24 blotter kernel: [   13.700367] Adding 1040380k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:1040380k 
Jul 10 10:15:24 blotter kernel: [   13.849511] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 10 10:15:24 blotter kernel: [   14.490298] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Jul 10 10:15:24 blotter kernel: [   14.602984] lp: driver loaded but no devices found
Jul 10 10:15:24 blotter kernel: [   14.740374] acpi device:24: registered as cooling_device3
Jul 10 10:15:24 blotter kernel: [   14.740540] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
Jul 10 10:15:24 blotter kernel: [   14.740899] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
Jul 10 10:15:24 blotter kernel: [   14.746029] wmi: Mapper loaded
Jul 10 10:15:24 blotter kernel: [   15.044492] intel_rng: FWH not detected
Jul 10 10:15:24 blotter kernel: [   15.167444] type=1400 audit(1373465721.448:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=502 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   15.169056] type=1400 audit(1373465721.452:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=502 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   15.169913] type=1400 audit(1373465721.452:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=502 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   15.184069] type=1400 audit(1373465721.468:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=505 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   15.295151] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMBA 1 (20121018/utaddress-251)
Jul 10 10:15:24 blotter kernel: [   15.295173] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 10 10:15:24 blotter kernel: [   15.295185] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Jul 10 10:15:24 blotter kernel: [   15.295199] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 10 10:15:24 blotter kernel: [   15.295206] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Jul 10 10:15:24 blotter kernel: [   15.295220] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 10 10:15:24 blotter kernel: [   15.295226] lpc_ich: Resource conflict(s) found affecting gpio_ich
Jul 10 10:15:24 blotter kernel: [   15.403910] microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x212
Jul 10 10:15:24 blotter kernel: [   15.794307] leds_ss4200: no LED devices found
Jul 10 10:15:24 blotter kernel: [   15.973681] [drm] Initialized drm 1.1.0 20060810
Jul 10 10:15:24 blotter kernel: [   15.985352] cfg80211: Calling CRDA to update world regulatory domain
Jul 10 10:15:24 blotter kernel: [   16.120926] lib80211: common routines for IEEE802.11 drivers
Jul 10 10:15:24 blotter kernel: [   16.120936] lib80211_crypt: registered algorithm 'NULL'
Jul 10 10:15:24 blotter kernel: [   16.151157] Linux video capture interface: v2.00
Jul 10 10:15:24 blotter kernel: [   16.276856] microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x212
Jul 10 10:15:24 blotter kernel: [   16.306838] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 10 10:15:24 blotter kernel: [   16.345827] acer_wmi: Acer Laptop ACPI-WMI Extras
Jul 10 10:15:24 blotter kernel: [   16.528867] acer_wmi: Function bitmap for Communication Device: 0x1
Jul 10 10:15:24 blotter kernel: [   16.528888] acer_wmi: Brightness must be controlled by acpi video driver
Jul 10 10:15:24 blotter kernel: [   16.529441] input: Acer BMA150 accelerometer as /devices/virtual/input/input6
Jul 10 10:15:24 blotter kernel: [   16.549896] wl: module license 'MIXED/Proprietary' taints kernel.
Jul 10 10:15:24 blotter kernel: [   16.572766] cfg80211: World regulatory domain updated:
Jul 10 10:15:24 blotter kernel: [   16.572777] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 10 10:15:24 blotter kernel: [   16.572785] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 10 10:15:24 blotter kernel: [   16.572792] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 10 10:15:24 blotter kernel: [   16.572800] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 10 10:15:24 blotter kernel: [   16.572806] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 10 10:15:24 blotter kernel: [   16.572813] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 10 10:15:24 blotter kernel: [   16.582855] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Jul 10 10:15:24 blotter kernel: [   16.670388] lib80211_crypt: registered algorithm 'TKIP'
Jul 10 10:15:24 blotter kernel: [   16.742647] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)
Jul 10 10:15:24 blotter kernel: [   16.798005] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
Jul 10 10:15:24 blotter kernel: [   16.798895] usbcore: registered new interface driver uvcvideo
Jul 10 10:15:24 blotter kernel: [   16.798906] USB Video Class driver (1.1.1)
Jul 10 10:15:24 blotter kernel: [   16.810477] i915 0000:00:02.0: setting latency timer to 64
Jul 10 10:15:24 blotter kernel: [   16.848200] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul 10 10:15:24 blotter kernel: [   16.848210] [drm] Driver supports precise vblank timestamp query.
Jul 10 10:15:24 blotter kernel: [   16.848409] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jul 10 10:15:24 blotter kernel: [   17.026274] [drm] initialized overlay support
Jul 10 10:15:24 blotter kernel: [   17.040755] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
Jul 10 10:15:24 blotter kernel: [   17.244945] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000, board id: 3655, fw id: 511380
Jul 10 10:15:24 blotter kernel: [   17.335613] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jul 10 10:15:24 blotter kernel: [   17.352636] fbcon: inteldrmfb (fb0) is primary device
Jul 10 10:15:24 blotter kernel: [   17.764068] i915: fixme: max PWM is zero
Jul 10 10:15:24 blotter kernel: [   17.764249] Console: switching to colour frame buffer device 128x37
Jul 10 10:15:24 blotter kernel: [   17.773588] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Jul 10 10:15:24 blotter kernel: [   17.773593] i915 0000:00:02.0: registered panic notifier
Jul 10 10:15:24 blotter kernel: [   17.773611] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jul 10 10:15:24 blotter kernel: [   17.773909] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Jul 10 10:15:24 blotter kernel: [   18.133088] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jul 10 10:15:24 blotter kernel: [   18.136288] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jul 10 10:15:24 blotter kernel: [   18.203247] type=1400 audit(1373465724.484:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=807 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   18.229082] type=1400 audit(1373465724.512:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=807 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   18.249999] type=1400 audit(1373465724.532:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=806 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   18.251206] type=1400 audit(1373465724.532:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=806 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   18.263857] type=1400 audit(1373465724.544:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=807 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   18.358928] type=1400 audit(1373465724.640:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=818 comm="apparmor_parser"
Jul 10 10:15:24 blotter kernel: [   18.478808] Bluetooth: Core ver 2.16
Jul 10 10:15:24 blotter kernel: [   18.479931] NET: Registered protocol family 31
Jul 10 10:15:24 blotter kernel: [   18.479948] Bluetooth: HCI device and connection manager initialized
Jul 10 10:15:24 blotter kernel: [   18.482302] Bluetooth: HCI socket layer initialized
Jul 10 10:15:24 blotter kernel: [   18.482319] Bluetooth: L2CAP socket layer initialized
Jul 10 10:15:24 blotter kernel: [   18.482351] Bluetooth: SCO socket layer initialized
Jul 10 10:15:25 blotter kernel: [   18.768672] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 10 10:15:25 blotter kernel: [   18.768683] Bluetooth: BNEP filters: protocol multicast
Jul 10 10:15:25 blotter kernel: [   18.768709] Bluetooth: BNEP socket layer initialized
Jul 10 10:15:25 blotter kernel: [   18.785133] Bluetooth: RFCOMM TTY layer initialized
Jul 10 10:15:25 blotter kernel: [   18.785170] Bluetooth: RFCOMM socket layer initialized
Jul 10 10:15:25 blotter kernel: [   18.785178] Bluetooth: RFCOMM ver 1.11
Jul 10 10:15:27 blotter kernel: [   20.747224] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
Jul 10 10:15:27 blotter kernel: [   20.770042] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 10 10:15:27 blotter kernel: [   20.778361] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 13 10:15:10 blotter kernel: imklog 5.8.11, log source = /proc/kmsg started.
Jul 13 10:15:10 blotter kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 13 10:15:10 blotter kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 13 10:15:10 blotter kernel: [    0.000000] Linux version 3.8.0-26-generic (buildd@lamiak) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #38-Ubuntu SMP Mon Jun 17 21:46:08 UTC 2013 (Ubuntu 3.8.0-26.38-generic 3.8.13.2)
Jul 13 10:15:10 blotter kernel: [    0.000000] KERNEL supported cpus:
Jul 13 10:15:10 blotter kernel: [    0.000000]   Intel GenuineIntel
Jul 13 10:15:10 blotter kernel: [    0.000000]   AMD AuthenticAMD
Jul 13 10:15:10 blotter kernel: [    0.000000]   NSC Geode by NSC
Jul 13 10:15:10 blotter kernel: [    0.000000]   Cyrix CyrixInstead
Jul 13 10:15:10 blotter kernel: [    0.000000]   Centaur CentaurHauls
Jul 13 10:15:10 blotter kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 13 10:15:10 blotter kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 13 10:15:10 blotter kernel: [    0.000000]   UMC UMC UMC UMC
Jul 13 10:15:10 blotter kernel: [    0.000000] Disabled fast string operations
Jul 13 10:15:10 blotter kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003f575fff] usable
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f576000-0x000000003f5befff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f5bf000-0x000000003f66cfff] usable
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f66d000-0x000000003f6befff] ACPI NVS
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6bf000-0x000000003f6edfff] usable
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6ee000-0x000000003f6fefff] ACPI data
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6ff000-0x000000003f6fffff] usable
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f700000-0x000000003fffffff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 13 10:15:10 blotter kernel: [    0.000000] SMBIOS 2.4 present.
Jul 13 10:15:10 blotter kernel: [    0.000000] DMI: Acer       Aspire one      /Aspire one      , BIOS V1.22 10/14/2009
Jul 13 10:15:10 blotter kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Jul 13 10:15:10 blotter kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 13 10:15:10 blotter kernel: [    0.000000] e820: last_pfn = 0x3f700 max_arch_pfn = 0x1000000
Jul 13 10:15:10 blotter kernel: [    0.000000] MTRR default type: uncachable
Jul 13 10:15:10 blotter kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 13 10:15:10 blotter kernel: [    0.000000]   00000-9FFFF write-back
Jul 13 10:15:10 blotter kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 13 10:15:10 blotter kernel: [    0.000000]   C0000-C7FFF write-protect
Jul 13 10:15:10 blotter kernel: [    0.000000]   C8000-EFFFF uncachable
Jul 13 10:15:10 blotter kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 13 10:15:10 blotter kernel: [    0.000000] MTRR variable ranges enabled:
Jul 13 10:15:10 blotter kernel: [    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
Jul 13 10:15:10 blotter kernel: [    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
Jul 13 10:15:10 blotter kernel: [    0.000000]   2 base 000000000 mask 0E0000000 write-back
Jul 13 10:15:10 blotter kernel: [    0.000000]   3 base 020000000 mask 0E0000000 write-back
Jul 13 10:15:10 blotter kernel: [    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
Jul 13 10:15:10 blotter kernel: [    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
Jul 13 10:15:10 blotter kernel: [    0.000000]   6 disabled
Jul 13 10:15:10 blotter kernel: [    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
Jul 13 10:15:10 blotter kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 13 10:15:10 blotter kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Jul 13 10:15:10 blotter kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul 13 10:15:10 blotter kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Jul 13 10:15:10 blotter kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Jul 13 10:15:10 blotter kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Jul 13 10:15:10 blotter kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Jul 13 10:15:10 blotter kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Jul 13 10:15:10 blotter kernel: [    0.000000] RAMDISK: [mem 0x36030000-0x3700ffff]
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: DSDT 3f6f0000 070CA (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: FACS 3f688000 00040
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: SLIC 3f6ef000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: BOOT 3f6ee000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 13 10:15:10 blotter kernel: [    0.000000] 123MB HIGHMEM available.
Jul 13 10:15:10 blotter kernel: [    0.000000] 891MB LOWMEM available.
Jul 13 10:15:10 blotter kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jul 13 10:15:10 blotter kernel: [    0.000000]   low ram: 0 - 37bfe000
Jul 13 10:15:10 blotter kernel: [    0.000000] Zone ranges:
Jul 13 10:15:10 blotter kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Jul 13 10:15:10 blotter kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Jul 13 10:15:10 blotter kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0x3f6fffff]
Jul 13 10:15:10 blotter kernel: [    0.000000] Movable zone start for each node
Jul 13 10:15:10 blotter kernel: [    0.000000] Early memory node ranges
Jul 13 10:15:10 blotter kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Jul 13 10:15:10 blotter kernel: [    0.000000]   node   0: [mem 0x00100000-0x3f575fff]
Jul 13 10:15:10 blotter kernel: [    0.000000]   node   0: [mem 0x3f5bf000-0x3f66cfff]
Jul 13 10:15:10 blotter kernel: [    0.000000]   node   0: [mem 0x3f6bf000-0x3f6edfff]
Jul 13 10:15:10 blotter kernel: [    0.000000]   node   0: [mem 0x3f6ff000-0x3f6fffff]
Jul 13 10:15:10 blotter kernel: [    0.000000] On node 0 totalpages: 259555
Jul 13 10:15:10 blotter kernel: [    0.000000] free_area_init_node: node 0, pgdat c18f5f40, node_mem_map f740d200
Jul 13 10:15:10 blotter kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 13 10:15:10 blotter kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 13 10:15:10 blotter kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul 13 10:15:10 blotter kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jul 13 10:15:10 blotter kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jul 13 10:15:10 blotter kernel: [    0.000000]   HighMem zone: 247 pages used for memmap
Jul 13 10:15:10 blotter kernel: [    0.000000]   HighMem zone: 31071 pages, LIFO batch:7
Jul 13 10:15:10 blotter kernel: [    0.000000] Using APIC driver default
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 13 10:15:10 blotter kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 13 10:15:10 blotter kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 13 10:15:10 blotter kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul 13 10:15:10 blotter kernel: [    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
Jul 13 10:15:10 blotter kernel: [    0.000000] nr_irqs_gsi: 40
Jul 13 10:15:10 blotter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 13 10:15:10 blotter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 13 10:15:10 blotter kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 13 10:15:10 blotter kernel: [    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
Jul 13 10:15:10 blotter kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 13 10:15:10 blotter kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jul 13 10:15:10 blotter kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f73ea000 s35008 r0 d22336 u57344
Jul 13 10:15:10 blotter kernel: [    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
Jul 13 10:15:10 blotter kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Jul 13 10:15:10 blotter kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257524
Jul 13 10:15:10 blotter kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-26-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7
Jul 13 10:15:10 blotter kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 13 10:15:10 blotter kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 13 10:15:10 blotter kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 13 10:15:10 blotter kernel: [    0.000000] __ex_table already sorted, skipping sort
Jul 13 10:15:10 blotter kernel: [    0.000000] Initializing CPU#0
Jul 13 10:15:10 blotter kernel: [    0.000000] allocated 2078592 bytes of page_cgroup
Jul 13 10:15:10 blotter kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 13 10:15:10 blotter kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0003f700)
Jul 13 10:15:10 blotter kernel: [    0.000000] Memory: 999872k/1039360k available (6255k kernel code, 38348k reserved, 2969k data, 788k init, 125272k highmem)
Jul 13 10:15:10 blotter kernel: [    0.000000] virtual kernel memory layout:
Jul 13 10:15:10 blotter kernel: [    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
Jul 13 10:15:10 blotter kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jul 13 10:15:10 blotter kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jul 13 10:15:10 blotter kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jul 13 10:15:10 blotter kernel: [    0.000000]       .init : 0xc1903000 - 0xc19c8000   ( 788 kB)
Jul 13 10:15:10 blotter kernel: [    0.000000]       .data : 0xc161bd30 - 0xc1902280   (2969 kB)
Jul 13 10:15:10 blotter kernel: [    0.000000]       .text : 0xc1000000 - 0xc161bd30   (6255 kB)
Jul 13 10:15:10 blotter kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 13 10:15:10 blotter kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jul 13 10:15:10 blotter kernel: [    0.000000] Hierarchical RCU implementation.
Jul 13 10:15:10 blotter kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul 13 10:15:10 blotter kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
Jul 13 10:15:10 blotter kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Jul 13 10:15:10 blotter kernel: [    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
Jul 13 10:15:10 blotter kernel: [    0.000000] Console: colour dummy device 80x25
Jul 13 10:15:10 blotter kernel: [    0.000000] console [tty0] enabled
Jul 13 10:15:10 blotter kernel: [    0.000000] hpet clockevent registered
Jul 13 10:15:10 blotter kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jul 13 10:15:10 blotter kernel: [    0.000000] tsc: Detected 1596.180 MHz processor
Jul 13 10:15:10 blotter kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.36 BogoMIPS (lpj=6384720)
Jul 13 10:15:10 blotter kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jul 13 10:15:10 blotter kernel: [    0.004092] Security Framework initialized
Jul 13 10:15:10 blotter kernel: [    0.004113] AppArmor: AppArmor initialized
Jul 13 10:15:10 blotter kernel: [    0.004117] Yama: becoming mindful.
Jul 13 10:15:10 blotter kernel: [    0.004234] Mount-cache hash table entries: 512
Jul 13 10:15:10 blotter kernel: [    0.004665] Initializing cgroup subsys cpuacct
Jul 13 10:15:10 blotter kernel: [    0.004673] Initializing cgroup subsys memory
Jul 13 10:15:10 blotter kernel: [    0.004692] Initializing cgroup subsys devices
Jul 13 10:15:10 blotter kernel: [    0.004697] Initializing cgroup subsys freezer
Jul 13 10:15:10 blotter kernel: [    0.004703] Initializing cgroup subsys blkio
Jul 13 10:15:10 blotter kernel: [    0.004709] Initializing cgroup subsys perf_event
Jul 13 10:15:10 blotter kernel: [    0.004717] Initializing cgroup subsys hugetlb
Jul 13 10:15:10 blotter kernel: [    0.004772] Disabled fast string operations
Jul 13 10:15:10 blotter kernel: [    0.004782] CPU: Physical Processor ID: 0
Jul 13 10:15:10 blotter kernel: [    0.004787] CPU: Processor Core ID: 0
Jul 13 10:15:10 blotter kernel: [    0.004792] mce: CPU supports 5 MCE banks
Jul 13 10:15:10 blotter kernel: [    0.004809] CPU0: Thermal monitoring enabled (TM2)
Jul 13 10:15:10 blotter kernel: [    0.004817] process: using mwait in idle threads
Jul 13 10:15:10 blotter kernel: [    0.004836] Last level iTLB entries: 4KB 32, 2MB 0, 4MB 0
Jul 13 10:15:10 blotter kernel: [    0.004836] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 8
Jul 13 10:15:10 blotter kernel: [    0.004836] tlb_flushall_shift: 6
Jul 13 10:15:10 blotter kernel: [    0.005231] Freeing SMP alternatives: 24k freed
Jul 13 10:15:10 blotter kernel: [    0.011455] ACPI: Core revision 20121018
Jul 13 10:15:10 blotter kernel: [    0.024029] ftrace: allocating 26123 entries in 52 pages
Jul 13 10:15:10 blotter kernel: [    0.044192] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 13 10:15:10 blotter kernel: [    0.044701] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 13 10:15:10 blotter kernel: [    0.087797] smpboot: CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz (fam: 06, model: 1c, stepping: 02)
Jul 13 10:15:10 blotter kernel: [    0.088000] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
Jul 13 10:15:10 blotter kernel: [    0.088000] ... version:                3
Jul 13 10:15:10 blotter kernel: [    0.088000] ... bit width:              40
Jul 13 10:15:10 blotter kernel: [    0.088000] ... generic registers:      2
Jul 13 10:15:10 blotter kernel: [    0.088000] ... value mask:             000000ffffffffff
Jul 13 10:15:10 blotter kernel: [    0.088000] ... max period:             000000007fffffff
Jul 13 10:15:10 blotter kernel: [    0.088000] ... fixed-purpose events:   3
Jul 13 10:15:10 blotter kernel: [    0.088000] ... event mask:             0000000700000003
Jul 13 10:15:10 blotter kernel: [    0.088000] CPU 1 irqstacks, hard=f5cd8000 soft=f5cda000
Jul 13 10:15:10 blotter kernel: [    0.088000] smpboot: Booting Node   0, Processors  #1 OK
Jul 13 10:15:10 blotter kernel: [    0.008000] Initializing CPU#1
Jul 13 10:15:10 blotter kernel: [    0.008000] Disabled fast string operations
Jul 13 10:15:10 blotter kernel: [    0.100060] Brought up 2 CPUs
Jul 13 10:15:10 blotter kernel: [    0.100075] smpboot: Total of 2 processors activated (6384.72 BogoMIPS)
Jul 13 10:15:10 blotter kernel: [    0.100257] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 13 10:15:10 blotter kernel: [    0.100867] devtmpfs: initialized
Jul 13 10:15:10 blotter kernel: [    0.100867] EVM: security.selinux
Jul 13 10:15:10 blotter kernel: [    0.100867] EVM: security.SMACK64
Jul 13 10:15:10 blotter kernel: [    0.100867] EVM: security.capability
Jul 13 10:15:10 blotter kernel: [    0.104136] PM: Registering ACPI NVS region [mem 0x3f66d000-0x3f6befff] (335872 bytes)
Jul 13 10:15:10 blotter kernel: [    0.104591] regulator-dummy: no parameters
Jul 13 10:15:10 blotter kernel: [    0.104741] NET: Registered protocol family 16
Jul 13 10:15:10 blotter kernel: [    0.105114] EISA bus registered
Jul 13 10:15:10 blotter kernel: [    0.105320] ACPI: bus type pci registered
Jul 13 10:15:10 blotter kernel: [    0.105489] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 13 10:15:10 blotter kernel: [    0.105498] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jul 13 10:15:10 blotter kernel: [    0.105501] PCI: Using MMCONFIG for extended config space
Jul 13 10:15:10 blotter kernel: [    0.105506] PCI: Using configuration type 1 for base access
Jul 13 10:15:10 blotter kernel: [    0.108629] bio: create slab <bio-0> at 0
Jul 13 10:15:10 blotter kernel: [    0.108629] ACPI: Added _OSI(Module Device)
Jul 13 10:15:10 blotter kernel: [    0.108629] ACPI: Added _OSI(Processor Device)
Jul 13 10:15:10 blotter kernel: [    0.108629] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 13 10:15:10 blotter kernel: [    0.108629] ACPI: Added _OSI(Processor Aggregator Device)
Jul 13 10:15:10 blotter kernel: [    0.112623] ACPI: EC: Look up EC in DSDT
Jul 13 10:15:10 blotter kernel: [    0.116266] ACPI: Executed 1 blocks of module-level executable AML code
Jul 13 10:15:10 blotter kernel: [    0.120154] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 13 10:15:10 blotter kernel: [    0.121219] ACPI: SSDT 3f5b7c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.122103] ACPI: Dynamic OEM Table Load:
Jul 13 10:15:10 blotter kernel: [    0.122111] ACPI: SSDT   (null) 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.122387] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.123220] ACPI: Dynamic OEM Table Load:
Jul 13 10:15:10 blotter kernel: [    0.123227] ACPI: SSDT   (null) 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.124045] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.124905] ACPI: Dynamic OEM Table Load:
Jul 13 10:15:10 blotter kernel: [    0.124913] ACPI: SSDT   (null) 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.125184] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.126033] ACPI: Dynamic OEM Table Load:
Jul 13 10:15:10 blotter kernel: [    0.126041] ACPI: SSDT   (null) 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Jul 13 10:15:10 blotter kernel: [    0.128768] ACPI: Interpreter enabled
Jul 13 10:15:10 blotter kernel: [    0.128785] ACPI: (supports S0 S3 S4 S5)
Jul 13 10:15:10 blotter kernel: [    0.128834] ACPI: Using IOAPIC for interrupt routing
Jul 13 10:15:10 blotter kernel: [    0.266236] ACPI: Power Resource [FN00] (on)
Jul 13 10:15:10 blotter kernel: [    0.267061] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Jul 13 10:15:10 blotter kernel: [    0.267410] ACPI: No dock devices found.
Jul 13 10:15:10 blotter kernel: [    0.267424] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 13 10:15:10 blotter kernel: [    0.268265] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 13 10:15:10 blotter kernel: [    0.268274] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 13 10:15:10 blotter kernel: [    0.268660] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dsfield-211)
Jul 13 10:15:10 blotter kernel: [    0.268676] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 13 10:15:10 blotter kernel: [    0.268694] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Jul 13 10:15:10 blotter kernel: [    0.270333] PCI host bridge to bus 0000:00
Jul 13 10:15:10 blotter kernel: [    0.270345] pci_bus 0000:00: root bus resource [bus 00-ff]
Jul 13 10:15:10 blotter kernel: [    0.270352] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jul 13 10:15:10 blotter kernel: [    0.270359] pci_bus 0000:00: root bus resource [io  0x0d00-0xefff]
Jul 13 10:15:10 blotter kernel: [    0.270365] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jul 13 10:15:10 blotter kernel: [    0.270372] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfebfffff]
Jul 13 10:15:10 blotter kernel: [    0.270396] pci 0000:00:00.0: [8086:27ac] type 00 class 0x060000
Jul 13 10:15:10 blotter kernel: [    0.270472] pci 0000:00:02.0: [8086:27ae] type 00 class 0x030000
Jul 13 10:15:10 blotter kernel: [    0.270492] pci 0000:00:02.0: reg 10: [mem 0x58280000-0x582fffff]
Jul 13 10:15:10 blotter kernel: [    0.270505] pci 0000:00:02.0: reg 14: [io  0x60f0-0x60f7]
Jul 13 10:15:10 blotter kernel: [    0.270517] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
Jul 13 10:15:10 blotter kernel: [    0.270529] pci 0000:00:02.0: reg 1c: [mem 0x58300000-0x5833ffff]
Jul 13 10:15:10 blotter kernel: [    0.270593] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
Jul 13 10:15:10 blotter kernel: [    0.270609] pci 0000:00:02.1: reg 10: [mem 0x58200000-0x5827ffff]
Jul 13 10:15:10 blotter kernel: [    0.270748] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
Jul 13 10:15:10 blotter kernel: [    0.270780] pci 0000:00:1b.0: reg 10: [mem 0x58340000-0x58343fff 64bit]
Jul 13 10:15:10 blotter kernel: [    0.270903] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 13 10:15:10 blotter kernel: [    0.270950] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
Jul 13 10:15:10 blotter kernel: [    0.271079] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 13 10:15:10 blotter kernel: [    0.271128] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
Jul 13 10:15:10 blotter kernel: [    0.271256] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jul 13 10:15:10 blotter kernel: [    0.271304] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
Jul 13 10:15:10 blotter kernel: [    0.271432] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jul 13 10:15:10 blotter kernel: [    0.271481] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
Jul 13 10:15:10 blotter kernel: [    0.271608] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul 13 10:15:10 blotter kernel: [    0.271658] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
Jul 13 10:15:10 blotter kernel: [    0.271725] pci 0000:00:1d.0: reg 20: [io  0x60a0-0x60bf]
Jul 13 10:15:10 blotter kernel: [    0.271784] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
Jul 13 10:15:10 blotter kernel: [    0.271851] pci 0000:00:1d.1: reg 20: [io  0x6080-0x609f]
Jul 13 10:15:10 blotter kernel: [    0.271909] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
Jul 13 10:15:10 blotter kernel: [    0.271976] pci 0000:00:1d.2: reg 20: [io  0x6060-0x607f]
Jul 13 10:15:10 blotter kernel: [    0.272054] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
Jul 13 10:15:10 blotter kernel: [    0.272122] pci 0000:00:1d.3: reg 20: [io  0x6040-0x605f]
Jul 13 10:15:10 blotter kernel: [    0.272195] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
Jul 13 10:15:10 blotter kernel: [    0.272227] pci 0000:00:1d.7: reg 10: [mem 0x58344400-0x583447ff]
Jul 13 10:15:10 blotter kernel: [    0.272351] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul 13 10:15:10 blotter kernel: [    0.272389] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
Jul 13 10:15:10 blotter kernel: [    0.272515] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
Jul 13 10:15:10 blotter kernel: [    0.272652] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
Jul 13 10:15:10 blotter kernel: [    0.272661] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
Jul 13 10:15:10 blotter kernel: [    0.272743] pci 0000:00:1f.2: [8086:27c5] type 00 class 0x010601
Jul 13 10:15:10 blotter kernel: [    0.272775] pci 0000:00:1f.2: reg 10: [io  0x60d8-0x60df]
Jul 13 10:15:10 blotter kernel: [    0.272793] pci 0000:00:1f.2: reg 14: [io  0x60fc-0x60ff]
Jul 13 10:15:10 blotter kernel: [    0.272810] pci 0000:00:1f.2: reg 18: [io  0x60d0-0x60d7]
Jul 13 10:15:10 blotter kernel: [    0.272828] pci 0000:00:1f.2: reg 1c: [io  0x60f8-0x60fb]
Jul 13 10:15:10 blotter kernel: [    0.272846] pci 0000:00:1f.2: reg 20: [io  0x6020-0x602f]
Jul 13 10:15:10 blotter kernel: [    0.272864] pci 0000:00:1f.2: reg 24: [mem 0x58344000-0x583443ff]
Jul 13 10:15:10 blotter kernel: [    0.272934] pci 0000:00:1f.2: PME# supported from D3hot
Jul 13 10:15:10 blotter kernel: [    0.272969] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
Jul 13 10:15:10 blotter kernel: [    0.273053] pci 0000:00:1f.3: reg 20: [io  0x6000-0x601f]
Jul 13 10:15:10 blotter kernel: [    0.273293] pci 0000:01:00.0: [14e4:4315] type 00 class 0x028000
Jul 13 10:15:10 blotter kernel: [    0.273372] pci 0000:01:00.0: reg 10: [mem 0x57100000-0x57103fff 64bit]
Jul 13 10:15:10 blotter kernel: [    0.273771] pci 0000:01:00.0: supports D1 D2
Jul 13 10:15:10 blotter kernel: [    0.273957] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jul 13 10:15:10 blotter kernel: [    0.273967] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Jul 13 10:15:10 blotter kernel: [    0.273976] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
Jul 13 10:15:10 blotter kernel: [    0.273990] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.274066] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jul 13 10:15:10 blotter kernel: [    0.274076] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jul 13 10:15:10 blotter kernel: [    0.274086] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
Jul 13 10:15:10 blotter kernel: [    0.274099] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.274205] pci 0000:03:00.0: [1969:1062] type 00 class 0x020000
Jul 13 10:15:10 blotter kernel: [    0.274245] pci 0000:03:00.0: reg 10: [mem 0x55000000-0x5503ffff 64bit]
Jul 13 10:15:10 blotter kernel: [    0.274268] pci 0000:03:00.0: reg 18: [io  0x2000-0x207f]
Jul 13 10:15:10 blotter kernel: [    0.274430] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 13 10:15:10 blotter kernel: [    0.280040] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jul 13 10:15:10 blotter kernel: [    0.280051] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
Jul 13 10:15:10 blotter kernel: [    0.280061] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
Jul 13 10:15:10 blotter kernel: [    0.280074] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.280156] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jul 13 10:15:10 blotter kernel: [    0.280166] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
Jul 13 10:15:10 blotter kernel: [    0.280176] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
Jul 13 10:15:10 blotter kernel: [    0.280189] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.280295] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)
Jul 13 10:15:10 blotter kernel: [    0.280315] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 13 10:15:10 blotter kernel: [    0.280322] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xefff] (subtractive decode)
Jul 13 10:15:10 blotter kernel: [    0.280328] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 13 10:15:10 blotter kernel: [    0.280335] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
Jul 13 10:15:10 blotter kernel: [    0.280376] pci_bus 0000:00: on NUMA node 0
Jul 13 10:15:10 blotter kernel: [    0.280480] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Jul 13 10:15:10 blotter kernel: [    0.280670] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Jul 13 10:15:10 blotter kernel: [    0.280799] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Jul 13 10:15:10 blotter kernel: [    0.280930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Jul 13 10:15:10 blotter kernel: [    0.281232] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dsfield-211)
Jul 13 10:15:10 blotter kernel: [    0.281247] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 13 10:15:10 blotter kernel: [    0.281272]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
Jul 13 10:15:10 blotter kernel: [    0.281278]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
Jul 13 10:15:10 blotter kernel: [    0.283743] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Jul 13 10:15:10 blotter kernel: [    0.283902] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Jul 13 10:15:10 blotter kernel: [    0.284075] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Jul 13 10:15:10 blotter kernel: [    0.284229] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Jul 13 10:15:10 blotter kernel: [    0.284383] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 13 10:15:10 blotter kernel: [    0.284538] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 13 10:15:10 blotter kernel: [    0.284693] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 13 10:15:10 blotter kernel: [    0.284849] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 13 10:15:10 blotter kernel: [    0.285145] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jul 13 10:15:10 blotter kernel: [    0.285145] vgaarb: loaded
Jul 13 10:15:10 blotter kernel: [    0.285145] vgaarb: bridge control possible 0000:00:02.0
Jul 13 10:15:10 blotter kernel: [    0.285145] SCSI subsystem initialized
Jul 13 10:15:10 blotter kernel: [    0.285145] ACPI: bus type scsi registered
Jul 13 10:15:10 blotter kernel: [    0.285145] libata version 3.00 loaded.
Jul 13 10:15:10 blotter kernel: [    0.285145] ACPI: bus type usb registered
Jul 13 10:15:10 blotter kernel: [    0.285145] usbcore: registered new interface driver usbfs
Jul 13 10:15:10 blotter kernel: [    0.285145] usbcore: registered new interface driver hub
Jul 13 10:15:10 blotter kernel: [    0.285145] usbcore: registered new device driver usb
Jul 13 10:15:10 blotter kernel: [    0.285145] PCI: Using ACPI for IRQ routing
Jul 13 10:15:10 blotter kernel: [    0.295300] PCI: pci_cache_line_size set to 64 bytes
Jul 13 10:15:10 blotter kernel: [    0.295487] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Jul 13 10:15:10 blotter kernel: [    0.295494] e820: reserve RAM buffer [mem 0x3f576000-0x3fffffff]
Jul 13 10:15:10 blotter kernel: [    0.295500] e820: reserve RAM buffer [mem 0x3f66d000-0x3fffffff]
Jul 13 10:15:10 blotter kernel: [    0.295505] e820: reserve RAM buffer [mem 0x3f6ee000-0x3fffffff]
Jul 13 10:15:10 blotter kernel: [    0.295510] e820: reserve RAM buffer [mem 0x3f700000-0x3fffffff]
Jul 13 10:15:10 blotter kernel: [    0.295782] NetLabel: Initializing
Jul 13 10:15:10 blotter kernel: [    0.295788] NetLabel:  domain hash size = 128
Jul 13 10:15:10 blotter kernel: [    0.295792] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 13 10:15:10 blotter kernel: [    0.295817] NetLabel:  unlabeled traffic allowed by default
Jul 13 10:15:10 blotter kernel: [    0.296074] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 13 10:15:10 blotter kernel: [    0.296091] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 13 10:15:10 blotter kernel: [    0.296102] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jul 13 10:15:10 blotter kernel: [    0.300043] Switching to clocksource hpet
Jul 13 10:15:10 blotter kernel: [    0.315903] AppArmor: AppArmor Filesystem Enabled
Jul 13 10:15:10 blotter kernel: [    0.315980] pnp: PnP ACPI init
Jul 13 10:15:10 blotter kernel: [    0.316069] ACPI: bus type pnp registered
Jul 13 10:15:10 blotter kernel: [    0.380438] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x1000-0x1fff]
Jul 13 10:15:10 blotter kernel: [    0.380560] system 00:00: [io  0x0200-0x020f] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380579] system 00:00: [io  0x0600-0x060f] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380587] system 00:00: [io  0x0610] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380594] system 00:00: [io  0x0800-0x080f] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380601] system 00:00: [io  0x0400-0x047f] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380609] system 00:00: [io  0x0500-0x053f] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380616] system 00:00: [io  0xff2c-0xff2f] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380626] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380633] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380641] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380648] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380656] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380664] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 13 10:15:10 blotter kernel: [    0.380671] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 13 10:15:10 blotter kernel: [    0.380683] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 13 10:15:10 blotter kernel: [    0.380716] pnp 00:01: [dma 4]
Jul 13 10:15:10 blotter kernel: [    0.380770] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 13 10:15:10 blotter kernel: [    0.380885] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 13 10:15:10 blotter kernel: [    0.381134] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Jul 13 10:15:10 blotter kernel: [    0.381223] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 13 10:15:10 blotter kernel: [    0.381300] pnp 00:05: Plug and Play ACPI device, IDs INT0800 (active)
Jul 13 10:15:10 blotter kernel: [    0.381426] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 13 10:15:10 blotter kernel: [    0.381645] pnp 00:07: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
Jul 13 10:15:10 blotter kernel: [    0.382064] pnp: PnP ACPI: found 8 devices
Jul 13 10:15:10 blotter kernel: [    0.382070] ACPI: ACPI bus type pnp unregistered
Jul 13 10:15:10 blotter kernel: [    0.382077] PnPBIOS: Disabled by ACPI PNP
Jul 13 10:15:10 blotter kernel: [    0.422930] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jul 13 10:15:10 blotter kernel: [    0.422944] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Jul 13 10:15:10 blotter kernel: [    0.422956] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
Jul 13 10:15:10 blotter kernel: [    0.422967] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.422979] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jul 13 10:15:10 blotter kernel: [    0.422987] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jul 13 10:15:10 blotter kernel: [    0.422998] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
Jul 13 10:15:10 blotter kernel: [    0.423008] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.423021] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jul 13 10:15:10 blotter kernel: [    0.423029] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
Jul 13 10:15:10 blotter kernel: [    0.423040] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
Jul 13 10:15:10 blotter kernel: [    0.423050] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.423062] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jul 13 10:15:10 blotter kernel: [    0.423070] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
Jul 13 10:15:10 blotter kernel: [    0.423081] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
Jul 13 10:15:10 blotter kernel: [    0.423091] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.423104] pci 0000:00:1e.0: PCI bridge to [bus 05]
Jul 13 10:15:10 blotter kernel: [    0.423163] pci 0000:00:1c.1: enabling device (0000 -> 0003)
Jul 13 10:15:10 blotter kernel: [    0.423204] pci 0000:00:1c.3: enabling device (0000 -> 0003)
Jul 13 10:15:10 blotter kernel: [    0.423237] pci 0000:00:1e.0: setting latency timer to 64
Jul 13 10:15:10 blotter kernel: [    0.423248] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 13 10:15:10 blotter kernel: [    0.423255] pci_bus 0000:00: resource 5 [io  0x0d00-0xefff]
Jul 13 10:15:10 blotter kernel: [    0.423261] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 13 10:15:10 blotter kernel: [    0.423268] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
Jul 13 10:15:10 blotter kernel: [    0.423275] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
Jul 13 10:15:10 blotter kernel: [    0.423282] pci_bus 0000:01: resource 1 [mem 0x57100000-0x581fffff]
Jul 13 10:15:10 blotter kernel: [    0.423288] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.423295] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
Jul 13 10:15:10 blotter kernel: [    0.423302] pci_bus 0000:02: resource 1 [mem 0x56100000-0x570fffff]
Jul 13 10:15:10 blotter kernel: [    0.423309] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.423316] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
Jul 13 10:15:10 blotter kernel: [    0.423322] pci_bus 0000:03: resource 1 [mem 0x55000000-0x560fffff]
Jul 13 10:15:10 blotter kernel: [    0.423329] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.423336] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
Jul 13 10:15:10 blotter kernel: [    0.423342] pci_bus 0000:04: resource 1 [mem 0x54000000-0x54ffffff]
Jul 13 10:15:10 blotter kernel: [    0.423349] pci_bus 0000:04: resource 2 [mem 0x53000000-0x53ffffff 64bit pref]
Jul 13 10:15:10 blotter kernel: [    0.423356] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jul 13 10:15:10 blotter kernel: [    0.423363] pci_bus 0000:05: resource 5 [io  0x0d00-0xefff]
Jul 13 10:15:10 blotter kernel: [    0.423369] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jul 13 10:15:10 blotter kernel: [    0.423376] pci_bus 0000:05: resource 7 [mem 0x40000000-0xfebfffff]
Jul 13 10:15:10 blotter kernel: [    0.423455] NET: Registered protocol family 2
Jul 13 10:15:10 blotter kernel: [    0.423771] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Jul 13 10:15:10 blotter kernel: [    0.423834] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jul 13 10:15:10 blotter kernel: [    0.423893] TCP: Hash tables configured (established 8192 bind 8192)
Jul 13 10:15:10 blotter kernel: [    0.423940] TCP: reno registered
Jul 13 10:15:10 blotter kernel: [    0.423948] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul 13 10:15:10 blotter kernel: [    0.423966] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul 13 10:15:10 blotter kernel: [    0.424151] NET: Registered protocol family 1
Jul 13 10:15:10 blotter kernel: [    0.424190] pci 0000:00:02.0: Boot video device
Jul 13 10:15:10 blotter kernel: [    0.424555] PCI: CLS 0 bytes, default 64
Jul 13 10:15:10 blotter kernel: [    0.424681] Trying to unpack rootfs image as initramfs...
Jul 13 10:15:10 blotter kernel: [    1.133725] Freeing initrd memory: 16256k freed
Jul 13 10:15:10 blotter kernel: [    1.150504] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
Jul 13 10:15:10 blotter kernel: [    1.150514] Simple Boot Flag at 0x44 set to 0x1
Jul 13 10:15:10 blotter kernel: [    1.151197] Initialise module verification
Jul 13 10:15:10 blotter kernel: [    1.151310] audit: initializing netlink socket (disabled)
Jul 13 10:15:10 blotter kernel: [    1.151338] type=2000 audit(1373724885.148:1): initialized
Jul 13 10:15:10 blotter kernel: [    1.199386] bounce pool size: 64 pages
Jul 13 10:15:10 blotter kernel: [    1.199415] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 13 10:15:10 blotter kernel: [    1.203363] VFS: Disk quotas dquot_6.5.2
Jul 13 10:15:10 blotter kernel: [    1.203503] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 13 10:15:10 blotter kernel: [    1.205027] fuse init (API version 7.20)
Jul 13 10:15:10 blotter kernel: [    1.205265] msgmni has been set to 1740
Jul 13 10:15:10 blotter kernel: [    1.206451] Key type asymmetric registered
Jul 13 10:15:10 blotter kernel: [    1.206460] Asymmetric key parser 'x509' registered
Jul 13 10:15:10 blotter kernel: [    1.206576] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jul 13 10:15:10 blotter kernel: [    1.206651] io scheduler noop registered
Jul 13 10:15:10 blotter kernel: [    1.206659] io scheduler deadline registered (default)
Jul 13 10:15:10 blotter kernel: [    1.206685] io scheduler cfq registered
Jul 13 10:15:10 blotter kernel: [    1.207025] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Jul 13 10:15:10 blotter kernel: [    1.207216] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
Jul 13 10:15:10 blotter kernel: [    1.207396] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Jul 13 10:15:10 blotter kernel: [    1.207580] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
Jul 13 10:15:10 blotter kernel: [    1.207760] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 13 10:15:10 blotter kernel: [    1.207811] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 13 10:15:10 blotter kernel: [    1.207940] intel_idle: MWAIT substates: 0x20220
Jul 13 10:15:10 blotter kernel: [    1.207961] intel_idle: v0.4 model 0x1C
Jul 13 10:15:10 blotter kernel: [    1.207966] intel_idle: lapic_timer_reliable_states 0x2
Jul 13 10:15:10 blotter kernel: [    1.207973] tsc: Marking TSC unstable due to TSC halts in idle states deeper than C2
Jul 13 10:15:10 blotter kernel: [    1.336097] ACPI: AC Adapter [AC] (on-line)
Jul 13 10:15:10 blotter kernel: [    1.336267] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 13 10:15:10 blotter kernel: [    1.336279] ACPI: Power Button [PWRB]
Jul 13 10:15:10 blotter kernel: [    1.336383] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jul 13 10:15:10 blotter kernel: [    1.336426] ACPI: Lid Switch [LID0]
Jul 13 10:15:10 blotter kernel: [    1.336527] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jul 13 10:15:10 blotter kernel: [    1.336537] ACPI: Sleep Button [SLPB]
Jul 13 10:15:10 blotter kernel: [    1.336653] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jul 13 10:15:10 blotter kernel: [    1.336661] ACPI: Power Button [PWRF]
Jul 13 10:15:10 blotter kernel: [    1.336815] ACPI: Fan [FAN] (on)
Jul 13 10:15:10 blotter kernel: [    1.336950] ACPI: Requesting acpi_cpufreq
Jul 13 10:15:10 blotter kernel: [    1.471033] thermal LNXTHERM:00: registered as thermal_zone0
Jul 13 10:15:10 blotter kernel: [    1.471042] ACPI: Thermal Zone [THRM] (27 C)
Jul 13 10:15:10 blotter kernel: [    1.471134] GHES: HEST is not enabled!
Jul 13 10:15:10 blotter kernel: [    1.471292] isapnp: Scanning for PnP cards...
Jul 13 10:15:10 blotter kernel: [    1.472252] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 13 10:15:10 blotter kernel: [    1.825576] isapnp: No Plug & Play device found
Jul 13 10:15:10 blotter kernel: [    2.128259] ACPI: Battery Slot [BAT0] (battery present)
Jul 13 10:15:10 blotter kernel: [    2.128498] Linux agpgart interface v0.103
Jul 13 10:15:10 blotter kernel: [    2.128651] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Jul 13 10:15:10 blotter kernel: [    2.128821] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
Jul 13 10:15:10 blotter kernel: [    2.128985] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Jul 13 10:15:10 blotter kernel: [    2.129262] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
Jul 13 10:15:10 blotter kernel: [    2.133453] brd: module loaded
Jul 13 10:15:10 blotter kernel: [    2.135635] loop: module loaded
Jul 13 10:15:10 blotter kernel: [    2.136877] libphy: Fixed MDIO Bus: probed
Jul 13 10:15:10 blotter kernel: [    2.137107] tun: Universal TUN/TAP device driver, 1.6
Jul 13 10:15:10 blotter kernel: [    2.137112] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 13 10:15:10 blotter kernel: [    2.137276] PPP generic driver version 2.4.2
Jul 13 10:15:10 blotter kernel: [    2.137433] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 13 10:15:10 blotter kernel: [    2.137438] ehci-pci: EHCI PCI platform driver
Jul 13 10:15:10 blotter kernel: [    2.137514] ehci-pci 0000:00:1d.7: setting latency timer to 64
Jul 13 10:15:10 blotter kernel: [    2.137524] ehci-pci 0000:00:1d.7: EHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.137538] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul 13 10:15:10 blotter kernel: [    2.137565] ehci-pci 0000:00:1d.7: debug port 1
Jul 13 10:15:10 blotter kernel: [    2.141502] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
Jul 13 10:15:10 blotter kernel: [    2.141544] ehci-pci 0000:00:1d.7: irq 16, io mem 0x58344400
Jul 13 10:15:10 blotter kernel: [    2.152034] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul 13 10:15:10 blotter kernel: [    2.152113] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jul 13 10:15:10 blotter kernel: [    2.152121] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 13 10:15:10 blotter kernel: [    2.152127] usb usb1: Product: EHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.152133] usb usb1: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
Jul 13 10:15:10 blotter kernel: [    2.152139] usb usb1: SerialNumber: 0000:00:1d.7
Jul 13 10:15:10 blotter kernel: [    2.152443] hub 1-0:1.0: USB hub found
Jul 13 10:15:10 blotter kernel: [    2.152457] hub 1-0:1.0: 8 ports detected
Jul 13 10:15:10 blotter kernel: [    2.152824] ehci-platform: EHCI generic platform driver
Jul 13 10:15:10 blotter kernel: [    2.152856] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 13 10:15:10 blotter kernel: [    2.152905] uhci_hcd: USB Universal Host Controller Interface driver
Jul 13 10:15:10 blotter kernel: [    2.152957] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul 13 10:15:10 blotter kernel: [    2.152965] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.152979] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul 13 10:15:10 blotter kernel: [    2.153028] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
Jul 13 10:15:10 blotter kernel: [    2.153113] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Jul 13 10:15:10 blotter kernel: [    2.153120] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 13 10:15:10 blotter kernel: [    2.153126] usb usb2: Product: UHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.153132] usb usb2: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 13 10:15:10 blotter kernel: [    2.153138] usb usb2: SerialNumber: 0000:00:1d.0
Jul 13 10:15:10 blotter kernel: [    2.153418] hub 2-0:1.0: USB hub found
Jul 13 10:15:10 blotter kernel: [    2.153431] hub 2-0:1.0: 2 ports detected
Jul 13 10:15:10 blotter kernel: [    2.153609] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul 13 10:15:10 blotter kernel: [    2.153618] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.153632] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul 13 10:15:10 blotter kernel: [    2.153697] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
Jul 13 10:15:10 blotter kernel: [    2.153787] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jul 13 10:15:10 blotter kernel: [    2.153794] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 13 10:15:10 blotter kernel: [    2.153800] usb usb3: Product: UHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.153806] usb usb3: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 13 10:15:10 blotter kernel: [    2.153812] usb usb3: SerialNumber: 0000:00:1d.1
Jul 13 10:15:10 blotter kernel: [    2.154065] hub 3-0:1.0: USB hub found
Jul 13 10:15:10 blotter kernel: [    2.154077] hub 3-0:1.0: 2 ports detected
Jul 13 10:15:10 blotter kernel: [    2.154252] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul 13 10:15:10 blotter kernel: [    2.154261] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.154275] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul 13 10:15:10 blotter kernel: [    2.154337] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
Jul 13 10:15:10 blotter kernel: [    2.154422] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jul 13 10:15:10 blotter kernel: [    2.154430] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 13 10:15:10 blotter kernel: [    2.154436] usb usb4: Product: UHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.154442] usb usb4: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 13 10:15:10 blotter kernel: [    2.154447] usb usb4: SerialNumber: 0000:00:1d.2
Jul 13 10:15:10 blotter kernel: [    2.154705] hub 4-0:1.0: USB hub found
Jul 13 10:15:10 blotter kernel: [    2.154718] hub 4-0:1.0: 2 ports detected
Jul 13 10:15:10 blotter kernel: [    2.154892] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jul 13 10:15:10 blotter kernel: [    2.154901] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.154915] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jul 13 10:15:10 blotter kernel: [    2.154976] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
Jul 13 10:15:10 blotter kernel: [    2.155058] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jul 13 10:15:10 blotter kernel: [    2.155066] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 13 10:15:10 blotter kernel: [    2.155072] usb usb5: Product: UHCI Host Controller
Jul 13 10:15:10 blotter kernel: [    2.155078] usb usb5: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 13 10:15:10 blotter kernel: [    2.155084] usb usb5: SerialNumber: 0000:00:1d.3
Jul 13 10:15:10 blotter kernel: [    2.155359] hub 5-0:1.0: USB hub found
Jul 13 10:15:10 blotter kernel: [    2.155372] hub 5-0:1.0: 2 ports detected
Jul 13 10:15:10 blotter kernel: [    2.155779] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
Jul 13 10:15:10 blotter kernel: [    2.176626] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 13 10:15:10 blotter kernel: [    2.176645] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 13 10:15:10 blotter kernel: [    2.177038] mousedev: PS/2 mouse device common for all mice
Jul 13 10:15:10 blotter kernel: [    2.178100] rtc_cmos 00:02: RTC can wake from S4
Jul 13 10:15:10 blotter kernel: [    2.178340] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jul 13 10:15:10 blotter kernel: [    2.178388] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jul 13 10:15:10 blotter kernel: [    2.178628] device-mapper: uevent: version 1.0.3
Jul 13 10:15:10 blotter kernel: [    2.178811] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
Jul 13 10:15:10 blotter kernel: [    2.178863] EISA: Probing bus 0 at eisa.0
Jul 13 10:15:10 blotter kernel: [    2.178869] EISA: Cannot allocate resource for mainboard
Jul 13 10:15:10 blotter kernel: [    2.178875] Cannot allocate resource for EISA slot 1
Jul 13 10:15:10 blotter kernel: [    2.178881] Cannot allocate resource for EISA slot 2
Jul 13 10:15:10 blotter kernel: [    2.178885] Cannot allocate resource for EISA slot 3
Jul 13 10:15:10 blotter kernel: [    2.178890] Cannot allocate resource for EISA slot 4
Jul 13 10:15:10 blotter kernel: [    2.178895] Cannot allocate resource for EISA slot 5
Jul 13 10:15:10 blotter kernel: [    2.178900] Cannot allocate resource for EISA slot 6
Jul 13 10:15:10 blotter kernel: [    2.178905] Cannot allocate resource for EISA slot 7
Jul 13 10:15:10 blotter kernel: [    2.178910] Cannot allocate resource for EISA slot 8
Jul 13 10:15:10 blotter kernel: [    2.178914] EISA: Detected 0 cards.
Jul 13 10:15:10 blotter kernel: [    2.178933] cpufreq-nforce2: No nForce2 chipset.
Jul 13 10:15:10 blotter kernel: [    2.179027] cpuidle: using governor ladder
Jul 13 10:15:10 blotter kernel: [    2.179152] cpuidle: using governor menu
Jul 13 10:15:10 blotter kernel: [    2.179161] ledtrig-cpu: registered to indicate activity on CPUs
Jul 13 10:15:10 blotter kernel: [    2.179165] EFI Variables Facility v0.08 2004-May-17
Jul 13 10:15:10 blotter kernel: [    2.179745] ashmem: initialized
Jul 13 10:15:10 blotter kernel: [    2.180099] TCP: cubic registered
Jul 13 10:15:10 blotter kernel: [    2.180388] NET: Registered protocol family 10
Jul 13 10:15:10 blotter kernel: [    2.180821] NET: Registered protocol family 17
Jul 13 10:15:10 blotter kernel: [    2.180859] Key type dns_resolver registered
Jul 13 10:15:10 blotter kernel: [    2.181287] Using IPI No-Shortcut mode
Jul 13 10:15:10 blotter kernel: [    2.181653] Loading module verification certificates
Jul 13 10:15:10 blotter kernel: [    2.194078] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d1850ecb2327d153922b22332b63536822dc0add'
Jul 13 10:15:10 blotter kernel: [    2.194111] registered taskstats version 1
Jul 13 10:15:10 blotter kernel: [    2.201181] Key type trusted registered
Jul 13 10:15:10 blotter kernel: [    2.206703] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jul 13 10:15:10 blotter kernel: [    2.209584] Key type encrypted registered
Jul 13 10:15:10 blotter kernel: [    2.218376] rtc_cmos 00:02: setting system clock to 2013-07-13 14:14:46 UTC (1373724886)
Jul 13 10:15:10 blotter kernel: [    2.220283] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 13 10:15:10 blotter kernel: [    2.220289] EDD information not available.
Jul 13 10:15:10 blotter kernel: [    2.220665] Freeing unused kernel memory: 788k freed
Jul 13 10:15:10 blotter kernel: [    2.221296] Write protecting the kernel text: 6256k
Jul 13 10:15:10 blotter kernel: [    2.221427] Write protecting the kernel read-only data: 2432k
Jul 13 10:15:10 blotter kernel: [    2.221432] NX-protecting the kernel data: 3984k
Jul 13 10:15:10 blotter kernel: [    2.464131] usb 1-2: new high-speed USB device number 2 using ehci-pci
Jul 13 10:15:10 blotter kernel: [    2.630130] usb 1-2: New USB device found, idVendor=04f2, idProduct=b175
Jul 13 10:15:10 blotter kernel: [    2.630144] usb 1-2: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jul 13 10:15:10 blotter kernel: [    2.630154] usb 1-2: Product: CNF9011
Jul 13 10:15:10 blotter kernel: [    2.630164] usb 1-2: Manufacturer: Chicony Electronics Co., Ltd.
Jul 13 10:15:10 blotter kernel: [    2.630172] usb 1-2: SerialNumber: SN0001
Jul 13 10:15:10 blotter kernel: [    2.645163] Disabling lock debugging due to kernel taint
Jul 13 10:15:10 blotter kernel: [    2.647282] ahci 0000:00:1f.2: version 3.0
Jul 13 10:15:10 blotter kernel: [    2.647428] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
Jul 13 10:15:10 blotter kernel: [    2.647536] ahci: SSS flag set, parallel bus scan disabled
Jul 13 10:15:10 blotter kernel: [    2.647600] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
Jul 13 10:15:10 blotter kernel: [    2.647614] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
Jul 13 10:15:10 blotter kernel: [    2.647628] ahci 0000:00:1f.2: setting latency timer to 64
Jul 13 10:15:10 blotter kernel: [    2.652889] atl1c 0000:03:00.0: version 1.0.1.1-NAPI
Jul 13 10:15:10 blotter kernel: [    2.653798] scsi0 : ahci
Jul 13 10:15:10 blotter kernel: [    2.656158] scsi1 : ahci
Jul 13 10:15:10 blotter kernel: [    2.659760] scsi2 : ahci
Jul 13 10:15:10 blotter kernel: [    2.662380] scsi3 : ahci
Jul 13 10:15:10 blotter kernel: [    2.662604] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 44
Jul 13 10:15:10 blotter kernel: [    2.662613] ata2: DUMMY
Jul 13 10:15:10 blotter kernel: [    2.662623] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 44
Jul 13 10:15:10 blotter kernel: [    2.662630] ata4: DUMMY
Jul 13 10:15:10 blotter kernel: [    2.980172] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 13 10:15:10 blotter kernel: [    2.981435] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 13 10:15:10 blotter kernel: [    3.029025] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
Jul 13 10:15:10 blotter kernel: [    3.029041] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 13 10:15:10 blotter kernel: [    3.030931] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Jul 13 10:15:10 blotter kernel: [    3.031260] ata1.00: configured for UDMA/133
Jul 13 10:15:10 blotter kernel: [    3.031716] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
Jul 13 10:15:10 blotter kernel: [    3.032349] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jul 13 10:15:10 blotter kernel: [    3.032373] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 13 10:15:10 blotter kernel: [    3.032594] sd 0:0:0:0: [sda] Write Protect is off
Jul 13 10:15:10 blotter kernel: [    3.032606] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 13 10:15:10 blotter kernel: [    3.032762] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 13 10:15:10 blotter kernel: [    3.050541]  sda: sda1 sda2 < sda5 >
Jul 13 10:15:10 blotter kernel: [    3.051814] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 13 10:15:10 blotter kernel: [    3.352160] ata3: SATA link down (SStatus 0 SControl 300)
Jul 13 10:15:10 blotter kernel: [    3.656534] bio: create slab <bio-1> at 1
Jul 13 10:15:10 blotter kernel: [    3.992890] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
Jul 13 10:15:10 blotter kernel: [    3.992900] EXT4-fs (dm-0): write access will be enabled during recovery
Jul 13 10:15:10 blotter kernel: [    5.601418] EXT4-fs (dm-0): orphan cleanup on readonly fs
Jul 13 10:15:10 blotter kernel: [    5.627857] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4198616
Jul 13 10:15:10 blotter kernel: [    5.638621] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4194350
Jul 13 10:15:10 blotter kernel: [    5.638817] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4196223
Jul 13 10:15:10 blotter kernel: [    5.649313] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 795222
Jul 13 10:15:10 blotter kernel: [    5.649472] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4198132
Jul 13 10:15:10 blotter kernel: [    5.694291] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 4196321
Jul 13 10:15:10 blotter kernel: [    5.710779] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 8658959
Jul 13 10:15:10 blotter kernel: [    5.710924] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 8658958
Jul 13 10:15:10 blotter kernel: [    5.739771] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 8658412
Jul 13 10:15:10 blotter kernel: [    5.739843] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 1310735
Jul 13 10:15:10 blotter kernel: [    5.739871] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 1310733
Jul 13 10:15:10 blotter kernel: [    5.739909] EXT4-fs (dm-0): 11 orphan inodes deleted
Jul 13 10:15:10 blotter kernel: [    5.739914] EXT4-fs (dm-0): recovery complete
Jul 13 10:15:10 blotter kernel: [    5.957607] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Jul 13 10:15:10 blotter kernel: [   15.712781] Adding 1040380k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:1040380k 
Jul 13 10:15:10 blotter kernel: [   15.881103] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 13 10:15:10 blotter kernel: [   16.139442] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Jul 13 10:15:10 blotter kernel: [   17.037667] type=1400 audit(1373724901.317:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=540 comm="apparmor_parser"
Jul 13 10:15:10 blotter kernel: [   17.046023] type=1400 audit(1373724901.325:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=540 comm="apparmor_parser"
Jul 13 10:15:10 blotter kernel: [   17.046982] type=1400 audit(1373724901.325:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=540 comm="apparmor_parser"
Jul 13 10:15:10 blotter kernel: [   17.059999] type=1400 audit(1373724901.337:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=541 comm="apparmor_parser"
Jul 13 10:15:10 blotter kernel: [   17.196610] cfg80211: Calling CRDA to update world regulatory domain
Jul 13 10:15:10 blotter kernel: [   17.355635] lib80211: common routines for IEEE802.11 drivers
Jul 13 10:15:10 blotter kernel: [   17.355648] lib80211_crypt: registered algorithm 'NULL'
Jul 13 10:15:10 blotter kernel: [   17.596278] lp: driver loaded but no devices found
Jul 13 10:15:10 blotter kernel: [   17.600550] microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x212
Jul 13 10:15:10 blotter kernel: [   17.713727] acpi device:24: registered as cooling_device3
Jul 13 10:15:10 blotter kernel: [   17.713889] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
Jul 13 10:15:10 blotter kernel: [   17.714074] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
Jul 13 10:15:10 blotter kernel: [   17.726298] wmi: Mapper loaded
Jul 13 10:15:10 blotter kernel: [   17.806967] intel_rng: FWH not detected
Jul 13 10:15:10 blotter kernel: [   17.850176] Linux video capture interface: v2.00
Jul 13 10:15:10 blotter kernel: [   18.044292] wl: module license 'MIXED/Proprietary' taints kernel.
Jul 13 10:15:10 blotter kernel: [   18.211361] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Jul 13 10:15:10 blotter kernel: [   18.293954] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMBA 1 (20121018/utaddress-251)
Jul 13 10:15:10 blotter kernel: [   18.293976] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 13 10:15:10 blotter kernel: [   18.293988] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Jul 13 10:15:10 blotter kernel: [   18.294003] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 13 10:15:10 blotter kernel: [   18.294012] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Jul 13 10:15:10 blotter kernel: [   18.294026] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 13 10:15:10 blotter kernel: [   18.294032] lpc_ich: Resource conflict(s) found affecting gpio_ich
Jul 13 10:15:10 blotter kernel: [   18.300477] microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x212
Jul 13 10:15:10 blotter kernel: [   18.367048] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 13 10:15:10 blotter kernel: [   18.596365] cfg80211: World regulatory domain updated:
Jul 13 10:15:10 blotter kernel: [   18.596374] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 13 10:15:10 blotter kernel: [   18.596381] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 13 10:15:10 blotter kernel: [   18.596386] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 13 10:15:10 blotter kernel: [   18.596392] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 13 10:15:10 blotter kernel: [   18.596397] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 13 10:15:10 blotter kernel: [   18.596402] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 13 10:15:10 blotter kernel: [   18.627265] acer_wmi: Acer Laptop ACPI-WMI Extras
Jul 13 10:15:10 blotter kernel: [   18.668574] leds_ss4200: no LED devices found
Jul 13 10:15:10 blotter kernel: [   18.729145] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)
Jul 13 10:15:10 blotter kernel: [   18.731138] lib80211_crypt: registered algorithm 'TKIP'
Jul 13 10:15:10 blotter kernel: [   18.784673] [drm] Initialized drm 1.1.0 20060810
Jul 13 10:15:10 blotter kernel: [   18.821406] acer_wmi: Function bitmap for Communication Device: 0x1
Jul 13 10:15:10 blotter kernel: [   18.821427] acer_wmi: Brightness must be controlled by acpi video driver
Jul 13 10:15:10 blotter kernel: [   18.823797] input: Acer BMA150 accelerometer as /devices/virtual/input/input6
Jul 13 10:15:10 blotter kernel: [   18.846788] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
Jul 13 10:15:10 blotter kernel: [   18.856111] usbcore: registered new interface driver uvcvideo
Jul 13 10:15:10 blotter kernel: [   18.856121] USB Video Class driver (1.1.1)
Jul 13 10:15:10 blotter kernel: [   18.958821] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
Jul 13 10:15:10 blotter kernel: [   19.151170] i915 0000:00:02.0: setting latency timer to 64
Jul 13 10:15:10 blotter kernel: [   19.152929] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul 13 10:15:10 blotter kernel: [   19.152940] [drm] Driver supports precise vblank timestamp query.
Jul 13 10:15:10 blotter kernel: [   19.153181] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jul 13 10:15:10 blotter kernel: [   19.163811] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000, board id: 3655, fw id: 511380
Jul 13 10:15:10 blotter kernel: [   19.249637] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jul 13 10:15:10 blotter kernel: [   19.309908] [drm] initialized overlay support
Jul 13 10:15:10 blotter kernel: [   19.646320] fbcon: inteldrmfb (fb0) is primary device
Jul 13 10:15:10 blotter kernel: [   20.056123] i915: fixme: max PWM is zero
Jul 13 10:15:10 blotter kernel: [   20.056359] Console: switching to colour frame buffer device 128x37
Jul 13 10:15:10 blotter kernel: [   20.064387] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Jul 13 10:15:10 blotter kernel: [   20.064395] i915 0000:00:02.0: registered panic notifier
Jul 13 10:15:10 blotter kernel: [   20.064411] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jul 13 10:15:10 blotter kernel: [   20.064818] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Jul 13 10:15:10 blotter kernel: [   20.419280] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jul 13 10:15:10 blotter kernel: [   20.419839] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jul 13 10:15:10 blotter kernel: [   25.873266] ACPI Error: [_T_0] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dswload2-330)
Jul 13 10:15:10 blotter kernel: [   25.873290] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20121018/psloop-259)
Jul 13 10:15:10 blotter kernel: [   25.873303] ACPI Error: Method parse/execution failed [\_SB_.PCI0.WMID.WMBA] (Node f5c2f528), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 13 10:15:10 blotter kernel: [   25.880358] ACPI: Marking method WMBA as Serialized because of AE_ALREADY_EXISTS error
Jul 13 10:15:11 blotter kernel: [   26.887260] type=1400 audit(1373724911.165:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=937 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   26.890932] type=1400 audit(1373724911.169:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=936 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   26.892947] type=1400 audit(1373724911.173:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=937 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   26.893820] type=1400 audit(1373724911.173:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=937 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   26.896504] type=1400 audit(1373724911.177:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=936 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   26.956812] type=1400 audit(1373724911.237:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=953 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   26.958661] type=1400 audit(1373724911.237:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=953 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   26.974188] type=1400 audit(1373724911.253:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=948 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   26.984939] type=1400 audit(1373724911.265:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=956 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   27.006514] type=1400 audit(1373724911.285:15): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=958 comm="apparmor_parser"
Jul 13 10:15:11 blotter kernel: [   27.097286] Bluetooth: Core ver 2.16
Jul 13 10:15:11 blotter kernel: [   27.097395] NET: Registered protocol family 31
Jul 13 10:15:11 blotter kernel: [   27.097403] Bluetooth: HCI device and connection manager initialized
Jul 13 10:15:11 blotter kernel: [   27.098514] Bluetooth: HCI socket layer initialized
Jul 13 10:15:11 blotter kernel: [   27.098533] Bluetooth: L2CAP socket layer initialized
Jul 13 10:15:11 blotter kernel: [   27.098567] Bluetooth: SCO socket layer initialized
Jul 13 10:15:11 blotter kernel: [   27.301963] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 13 10:15:11 blotter kernel: [   27.301973] Bluetooth: BNEP filters: protocol multicast
Jul 13 10:15:11 blotter kernel: [   27.301995] Bluetooth: BNEP socket layer initialized
Jul 13 10:15:11 blotter kernel: [   27.324201] Bluetooth: RFCOMM TTY layer initialized
Jul 13 10:15:11 blotter kernel: [   27.324239] Bluetooth: RFCOMM socket layer initialized
Jul 13 10:15:11 blotter kernel: [   27.324247] Bluetooth: RFCOMM ver 1.11
Jul 13 10:15:12 blotter kernel: [   28.442409] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
Jul 13 10:15:12 blotter kernel: [   28.457956] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 13 10:15:12 blotter kernel: [   28.464987] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 13 10:16:25 blotter kernel: [  102.392250] usb 1-1: new high-speed USB device number 3 using ehci-pci
Jul 13 10:16:25 blotter kernel: [  102.532110] usb 1-1: New USB device found, idVendor=13fe, idProduct=4100
Jul 13 10:16:25 blotter kernel: [  102.532135] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Jul 13 10:16:25 blotter kernel: [  102.532154] usb 1-1: Product:                 
Jul 13 10:16:25 blotter kernel: [  102.532170] usb 1-1: Manufacturer:         
Jul 13 10:16:25 blotter kernel: [  102.532186] usb 1-1: SerialNumber: 0707322D023EF127
Jul 13 10:16:25 blotter kernel: [  102.610719] Initializing USB Mass Storage driver...
Jul 13 10:16:25 blotter kernel: [  102.612733] scsi4 : usb-storage 1-1:1.0
Jul 13 10:16:25 blotter kernel: [  102.614701] usbcore: registered new interface driver usb-storage
Jul 13 10:16:25 blotter kernel: [  102.614714] USB Mass Storage support registered.
Jul 13 10:16:26 blotter kernel: [  103.638813] scsi 4:0:0:0: Direct-Access                               PMAP PQ: 0 ANSI: 4
Jul 13 10:16:26 blotter kernel: [  103.651899] sd 4:0:0:0: Attached scsi generic sg1 type 0
Jul 13 10:16:28 blotter kernel: [  105.937321] sd 4:0:0:0: [sdb] 62808064 512-byte logical blocks: (32.1 GB/29.9 GiB)
Jul 13 10:16:28 blotter kernel: [  105.940095] sd 4:0:0:0: [sdb] Write Protect is off
Jul 13 10:16:28 blotter kernel: [  105.940121] sd 4:0:0:0: [sdb] Mode Sense: 23 00 00 00
Jul 13 10:16:28 blotter kernel: [  105.942954] sd 4:0:0:0: [sdb] No Caching mode page present
Jul 13 10:16:28 blotter kernel: [  105.942982] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul 13 10:16:28 blotter kernel: [  105.959150] sd 4:0:0:0: [sdb] No Caching mode page present
Jul 13 10:16:28 blotter kernel: [  105.959163] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul 13 10:16:28 blotter kernel: [  105.988414]  sdb: sdb1
Jul 13 10:16:28 blotter kernel: [  106.000188] sd 4:0:0:0: [sdb] No Caching mode page present
Jul 13 10:16:28 blotter kernel: [  106.000204] sd 4:0:0:0: [sdb] Assuming drive cache: write through
Jul 13 10:16:28 blotter kernel: [  106.000216] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Jul 13 19:55:40 blotter kernel: [34857.297697] sdb: detected capacity change from 32157728768 to 0
Jul 13 19:55:44 blotter kernel: [34861.565240] usb 1-1: USB disconnect, device number 3
Jul 14 10:00:37 blotter kernel: imklog 5.8.11, log source = /proc/kmsg started.
Jul 14 10:00:37 blotter kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul 14 10:00:37 blotter kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 14 10:00:37 blotter kernel: [    0.000000] Linux version 3.8.0-26-generic (buildd@lamiak) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #38-Ubuntu SMP Mon Jun 17 21:46:08 UTC 2013 (Ubuntu 3.8.0-26.38-generic 3.8.13.2)
Jul 14 10:00:37 blotter kernel: [    0.000000] KERNEL supported cpus:
Jul 14 10:00:37 blotter kernel: [    0.000000]   Intel GenuineIntel
Jul 14 10:00:37 blotter kernel: [    0.000000]   AMD AuthenticAMD
Jul 14 10:00:37 blotter kernel: [    0.000000]   NSC Geode by NSC
Jul 14 10:00:37 blotter kernel: [    0.000000]   Cyrix CyrixInstead
Jul 14 10:00:37 blotter kernel: [    0.000000]   Centaur CentaurHauls
Jul 14 10:00:37 blotter kernel: [    0.000000]   Transmeta GenuineTMx86
Jul 14 10:00:37 blotter kernel: [    0.000000]   Transmeta TransmetaCPU
Jul 14 10:00:37 blotter kernel: [    0.000000]   UMC UMC UMC UMC
Jul 14 10:00:37 blotter kernel: [    0.000000] Disabled fast string operations
Jul 14 10:00:37 blotter kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009fbff] usable
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000000009fc00-0x000000000009ffff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003f575fff] usable
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f576000-0x000000003f5befff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f5bf000-0x000000003f66cfff] usable
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f66d000-0x000000003f6befff] ACPI NVS
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6bf000-0x000000003f6edfff] usable
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6ee000-0x000000003f6fefff] ACPI data
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f6ff000-0x000000003f6fffff] usable
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x000000003f700000-0x000000003fffffff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed14000-0x00000000fed19fff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 14 10:00:37 blotter kernel: [    0.000000] SMBIOS 2.4 present.
Jul 14 10:00:37 blotter kernel: [    0.000000] DMI: Acer       Aspire one      /Aspire one      , BIOS V1.22 10/14/2009
Jul 14 10:00:37 blotter kernel: [    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
Jul 14 10:00:37 blotter kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 14 10:00:37 blotter kernel: [    0.000000] e820: last_pfn = 0x3f700 max_arch_pfn = 0x1000000
Jul 14 10:00:37 blotter kernel: [    0.000000] MTRR default type: uncachable
Jul 14 10:00:37 blotter kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 14 10:00:37 blotter kernel: [    0.000000]   00000-9FFFF write-back
Jul 14 10:00:37 blotter kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 14 10:00:37 blotter kernel: [    0.000000]   C0000-C7FFF write-protect
Jul 14 10:00:37 blotter kernel: [    0.000000]   C8000-EFFFF uncachable
Jul 14 10:00:37 blotter kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 14 10:00:37 blotter kernel: [    0.000000] MTRR variable ranges enabled:
Jul 14 10:00:37 blotter kernel: [    0.000000]   0 base 0FFF00000 mask 0FFF00000 write-protect
Jul 14 10:00:37 blotter kernel: [    0.000000]   1 base 0FFFC0000 mask 0FFFE0000 uncachable
Jul 14 10:00:37 blotter kernel: [    0.000000]   2 base 000000000 mask 0E0000000 write-back
Jul 14 10:00:37 blotter kernel: [    0.000000]   3 base 020000000 mask 0E0000000 write-back
Jul 14 10:00:37 blotter kernel: [    0.000000]   4 base 03F800000 mask 0FF800000 uncachable
Jul 14 10:00:37 blotter kernel: [    0.000000]   5 base 03F700000 mask 0FFF00000 uncachable
Jul 14 10:00:37 blotter kernel: [    0.000000]   6 disabled
Jul 14 10:00:37 blotter kernel: [    0.000000]   7 base 000000000 mask 0FFFE0000 uncachable
Jul 14 10:00:37 blotter kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Jul 14 10:00:37 blotter kernel: [    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
Jul 14 10:00:37 blotter kernel: [    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
Jul 14 10:00:37 blotter kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
Jul 14 10:00:37 blotter kernel: [    0.000000]  [mem 0x00000000-0x001fffff] page 4k
Jul 14 10:00:37 blotter kernel: [    0.000000]  [mem 0x00200000-0x379fffff] page 2M
Jul 14 10:00:37 blotter kernel: [    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
Jul 14 10:00:37 blotter kernel: [    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
Jul 14 10:00:37 blotter kernel: [    0.000000] RAMDISK: [mem 0x36030000-0x3700ffff]
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: XSDT 3f6fe120 00064 (v01 ACRSYS ACRPRDCT 00000001      01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: FACP 3f6fc000 000F4 (v04 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: DSDT 3f6f0000 070CA (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: FACS 3f688000 00040
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: SSDT 3f6fd000 004C4 (v02  PmRef    CpuPm 00003000 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: HPET 3f6fb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: APIC 3f6fa000 00068 (v02 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: MCFG 3f6f9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: ASF! 3f6f8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: SLIC 3f6ef000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: BOOT 3f6ee000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 01000013)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 14 10:00:37 blotter kernel: [    0.000000] 123MB HIGHMEM available.
Jul 14 10:00:37 blotter kernel: [    0.000000] 891MB LOWMEM available.
Jul 14 10:00:37 blotter kernel: [    0.000000]   mapped low ram: 0 - 37bfe000
Jul 14 10:00:37 blotter kernel: [    0.000000]   low ram: 0 - 37bfe000
Jul 14 10:00:37 blotter kernel: [    0.000000] Zone ranges:
Jul 14 10:00:37 blotter kernel: [    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
Jul 14 10:00:37 blotter kernel: [    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
Jul 14 10:00:37 blotter kernel: [    0.000000]   HighMem  [mem 0x37bfe000-0x3f6fffff]
Jul 14 10:00:37 blotter kernel: [    0.000000] Movable zone start for each node
Jul 14 10:00:37 blotter kernel: [    0.000000] Early memory node ranges
Jul 14 10:00:37 blotter kernel: [    0.000000]   node   0: [mem 0x00010000-0x0009efff]
Jul 14 10:00:37 blotter kernel: [    0.000000]   node   0: [mem 0x00100000-0x3f575fff]
Jul 14 10:00:37 blotter kernel: [    0.000000]   node   0: [mem 0x3f5bf000-0x3f66cfff]
Jul 14 10:00:37 blotter kernel: [    0.000000]   node   0: [mem 0x3f6bf000-0x3f6edfff]
Jul 14 10:00:37 blotter kernel: [    0.000000]   node   0: [mem 0x3f6ff000-0x3f6fffff]
Jul 14 10:00:37 blotter kernel: [    0.000000] On node 0 totalpages: 259555
Jul 14 10:00:37 blotter kernel: [    0.000000] free_area_init_node: node 0, pgdat c18f5f40, node_mem_map f740d200
Jul 14 10:00:37 blotter kernel: [    0.000000]   DMA zone: 32 pages used for memmap
Jul 14 10:00:37 blotter kernel: [    0.000000]   DMA zone: 0 pages reserved
Jul 14 10:00:37 blotter kernel: [    0.000000]   DMA zone: 3951 pages, LIFO batch:0
Jul 14 10:00:37 blotter kernel: [    0.000000]   Normal zone: 1752 pages used for memmap
Jul 14 10:00:37 blotter kernel: [    0.000000]   Normal zone: 222502 pages, LIFO batch:31
Jul 14 10:00:37 blotter kernel: [    0.000000]   HighMem zone: 247 pages used for memmap
Jul 14 10:00:37 blotter kernel: [    0.000000]   HighMem zone: 31071 pages, LIFO batch:7
Jul 14 10:00:37 blotter kernel: [    0.000000] Using APIC driver default
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x408
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
Jul 14 10:00:37 blotter kernel: [    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: IRQ2 used by override.
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 14 10:00:37 blotter kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 14 10:00:37 blotter kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jul 14 10:00:37 blotter kernel: [    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
Jul 14 10:00:37 blotter kernel: [    0.000000] nr_irqs_gsi: 40
Jul 14 10:00:37 blotter kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jul 14 10:00:37 blotter kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Jul 14 10:00:37 blotter kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Jul 14 10:00:37 blotter kernel: [    0.000000] e820: [mem 0x40000000-0xdfffffff] available for PCI devices
Jul 14 10:00:37 blotter kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 14 10:00:37 blotter kernel: [    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
Jul 14 10:00:37 blotter kernel: [    0.000000] PERCPU: Embedded 14 pages/cpu @f73ea000 s35008 r0 d22336 u57344
Jul 14 10:00:37 blotter kernel: [    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
Jul 14 10:00:37 blotter kernel: [    0.000000] pcpu-alloc: [0] 0 [0] 1 
Jul 14 10:00:37 blotter kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257524
Jul 14 10:00:37 blotter kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.8.0-26-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash vt.handoff=7
Jul 14 10:00:37 blotter kernel: [    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
Jul 14 10:00:37 blotter kernel: [    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jul 14 10:00:37 blotter kernel: [    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jul 14 10:00:37 blotter kernel: [    0.000000] __ex_table already sorted, skipping sort
Jul 14 10:00:37 blotter kernel: [    0.000000] Initializing CPU#0
Jul 14 10:00:37 blotter kernel: [    0.000000] allocated 2078592 bytes of page_cgroup
Jul 14 10:00:37 blotter kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Jul 14 10:00:37 blotter kernel: [    0.000000] Initializing HighMem for node 0 (00037bfe:0003f700)
Jul 14 10:00:37 blotter kernel: [    0.000000] Memory: 999872k/1039360k available (6255k kernel code, 38348k reserved, 2969k data, 788k init, 125272k highmem)
Jul 14 10:00:37 blotter kernel: [    0.000000] virtual kernel memory layout:
Jul 14 10:00:37 blotter kernel: [    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
Jul 14 10:00:37 blotter kernel: [    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jul 14 10:00:37 blotter kernel: [    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
Jul 14 10:00:37 blotter kernel: [    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
Jul 14 10:00:37 blotter kernel: [    0.000000]       .init : 0xc1903000 - 0xc19c8000   ( 788 kB)
Jul 14 10:00:37 blotter kernel: [    0.000000]       .data : 0xc161bd30 - 0xc1902280   (2969 kB)
Jul 14 10:00:37 blotter kernel: [    0.000000]       .text : 0xc1000000 - 0xc161bd30   (6255 kB)
Jul 14 10:00:37 blotter kernel: [    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jul 14 10:00:37 blotter kernel: [    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jul 14 10:00:37 blotter kernel: [    0.000000] Hierarchical RCU implementation.
Jul 14 10:00:37 blotter kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Jul 14 10:00:37 blotter kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
Jul 14 10:00:37 blotter kernel: [    0.000000] NR_IRQS:2304 nr_irqs:512 16
Jul 14 10:00:37 blotter kernel: [    0.000000] CPU 0 irqstacks, hard=f5c08000 soft=f5c0a000
Jul 14 10:00:37 blotter kernel: [    0.000000] Console: colour dummy device 80x25
Jul 14 10:00:37 blotter kernel: [    0.000000] console [tty0] enabled
Jul 14 10:00:37 blotter kernel: [    0.000000] hpet clockevent registered
Jul 14 10:00:37 blotter kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Jul 14 10:00:37 blotter kernel: [    0.000000] tsc: Detected 1596.167 MHz processor
Jul 14 10:00:37 blotter kernel: [    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3192.33 BogoMIPS (lpj=6384668)
Jul 14 10:00:37 blotter kernel: [    0.004013] pid_max: default: 32768 minimum: 301
Jul 14 10:00:37 blotter kernel: [    0.004093] Security Framework initialized
Jul 14 10:00:37 blotter kernel: [    0.004113] AppArmor: AppArmor initialized
Jul 14 10:00:37 blotter kernel: [    0.004118] Yama: becoming mindful.
Jul 14 10:00:37 blotter kernel: [    0.004235] Mount-cache hash table entries: 512
Jul 14 10:00:37 blotter kernel: [    0.004664] Initializing cgroup subsys cpuacct
Jul 14 10:00:37 blotter kernel: [    0.004673] Initializing cgroup subsys memory
Jul 14 10:00:37 blotter kernel: [    0.004691] Initializing cgroup subsys devices
Jul 14 10:00:37 blotter kernel: [    0.004697] Initializing cgroup subsys freezer
Jul 14 10:00:37 blotter kernel: [    0.004703] Initializing cgroup subsys blkio
Jul 14 10:00:37 blotter kernel: [    0.004708] Initializing cgroup subsys perf_event
Jul 14 10:00:37 blotter kernel: [    0.004717] Initializing cgroup subsys hugetlb
Jul 14 10:00:37 blotter kernel: [    0.004772] Disabled fast string operations
Jul 14 10:00:37 blotter kernel: [    0.004782] CPU: Physical Processor ID: 0
Jul 14 10:00:37 blotter kernel: [    0.004787] CPU: Processor Core ID: 0
Jul 14 10:00:37 blotter kernel: [    0.004792] mce: CPU supports 5 MCE banks
Jul 14 10:00:37 blotter kernel: [    0.004809] CPU0: Thermal monitoring enabled (TM2)
Jul 14 10:00:37 blotter kernel: [    0.004818] process: using mwait in idle threads
Jul 14 10:00:37 blotter kernel: [    0.004837] Last level iTLB entries: 4KB 32, 2MB 0, 4MB 0
Jul 14 10:00:37 blotter kernel: [    0.004837] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 8
Jul 14 10:00:37 blotter kernel: [    0.004837] tlb_flushall_shift: 6
Jul 14 10:00:37 blotter kernel: [    0.005231] Freeing SMP alternatives: 24k freed
Jul 14 10:00:37 blotter kernel: [    0.011671] ACPI: Core revision 20121018
Jul 14 10:00:37 blotter kernel: [    0.024028] ftrace: allocating 26123 entries in 52 pages
Jul 14 10:00:37 blotter kernel: [    0.044190] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jul 14 10:00:37 blotter kernel: [    0.044700] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 14 10:00:37 blotter kernel: [    0.086714] smpboot: CPU0: Intel(R) Atom(TM) CPU N270   @ 1.60GHz (fam: 06, model: 1c, stepping: 02)
Jul 14 10:00:37 blotter kernel: [    0.088000] Performance Events: PEBS fmt0+, LBR disabled due to erratumAtom events, Intel PMU driver.
Jul 14 10:00:37 blotter kernel: [    0.088000] ... version:                3
Jul 14 10:00:37 blotter kernel: [    0.088000] ... bit width:              40
Jul 14 10:00:37 blotter kernel: [    0.088000] ... generic registers:      2
Jul 14 10:00:37 blotter kernel: [    0.088000] ... value mask:             000000ffffffffff
Jul 14 10:00:37 blotter kernel: [    0.088000] ... max period:             000000007fffffff
Jul 14 10:00:37 blotter kernel: [    0.088000] ... fixed-purpose events:   3
Jul 14 10:00:37 blotter kernel: [    0.088000] ... event mask:             0000000700000003
Jul 14 10:00:37 blotter kernel: [    0.088000] CPU 1 irqstacks, hard=f5cd8000 soft=f5cda000
Jul 14 10:00:37 blotter kernel: [    0.088000] smpboot: Booting Node   0, Processors  #1 OK
Jul 14 10:00:37 blotter kernel: [    0.008000] Initializing CPU#1
Jul 14 10:00:37 blotter kernel: [    0.008000] Disabled fast string operations
Jul 14 10:00:37 blotter kernel: [    0.100059] Brought up 2 CPUs
Jul 14 10:00:37 blotter kernel: [    0.100075] smpboot: Total of 2 processors activated (6384.66 BogoMIPS)
Jul 14 10:00:37 blotter kernel: [    0.100258] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Jul 14 10:00:37 blotter kernel: [    0.100870] devtmpfs: initialized
Jul 14 10:00:37 blotter kernel: [    0.100870] EVM: security.selinux
Jul 14 10:00:37 blotter kernel: [    0.100870] EVM: security.SMACK64
Jul 14 10:00:37 blotter kernel: [    0.100870] EVM: security.capability
Jul 14 10:00:37 blotter kernel: [    0.104137] PM: Registering ACPI NVS region [mem 0x3f66d000-0x3f6befff] (335872 bytes)
Jul 14 10:00:37 blotter kernel: [    0.104603] regulator-dummy: no parameters
Jul 14 10:00:37 blotter kernel: [    0.104753] NET: Registered protocol family 16
Jul 14 10:00:37 blotter kernel: [    0.105126] EISA bus registered
Jul 14 10:00:37 blotter kernel: [    0.105334] ACPI: bus type pci registered
Jul 14 10:00:37 blotter kernel: [    0.105502] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Jul 14 10:00:37 blotter kernel: [    0.105511] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
Jul 14 10:00:37 blotter kernel: [    0.105515] PCI: Using MMCONFIG for extended config space
Jul 14 10:00:37 blotter kernel: [    0.105519] PCI: Using configuration type 1 for base access
Jul 14 10:00:37 blotter kernel: [    0.108643] bio: create slab <bio-0> at 0
Jul 14 10:00:37 blotter kernel: [    0.108643] ACPI: Added _OSI(Module Device)
Jul 14 10:00:37 blotter kernel: [    0.108643] ACPI: Added _OSI(Processor Device)
Jul 14 10:00:37 blotter kernel: [    0.108643] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 14 10:00:37 blotter kernel: [    0.108643] ACPI: Added _OSI(Processor Aggregator Device)
Jul 14 10:00:37 blotter kernel: [    0.112640] ACPI: EC: Look up EC in DSDT
Jul 14 10:00:37 blotter kernel: [    0.116284] ACPI: Executed 1 blocks of module-level executable AML code
Jul 14 10:00:37 blotter kernel: [    0.120169] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 14 10:00:37 blotter kernel: [    0.121237] ACPI: SSDT 3f5b7c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.122121] ACPI: Dynamic OEM Table Load:
Jul 14 10:00:37 blotter kernel: [    0.122129] ACPI: SSDT   (null) 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.122404] ACPI: SSDT 3f5b6e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.123238] ACPI: Dynamic OEM Table Load:
Jul 14 10:00:37 blotter kernel: [    0.123245] ACPI: SSDT   (null) 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.124063] ACPI: SSDT 3f5b7f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.124923] ACPI: Dynamic OEM Table Load:
Jul 14 10:00:37 blotter kernel: [    0.124930] ACPI: SSDT   (null) 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.125201] ACPI: SSDT 3f5b5f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.126049] ACPI: Dynamic OEM Table Load:
Jul 14 10:00:37 blotter kernel: [    0.126056] ACPI: SSDT   (null) 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
Jul 14 10:00:37 blotter kernel: [    0.128769] ACPI: Interpreter enabled
Jul 14 10:00:37 blotter kernel: [    0.128785] ACPI: (supports S0 S3 S4 S5)
Jul 14 10:00:37 blotter kernel: [    0.128834] ACPI: Using IOAPIC for interrupt routing
Jul 14 10:00:37 blotter kernel: [    0.266238] ACPI: Power Resource [FN00] (on)
Jul 14 10:00:37 blotter kernel: [    0.267064] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
Jul 14 10:00:37 blotter kernel: [    0.267412] ACPI: No dock devices found.
Jul 14 10:00:37 blotter kernel: [    0.267427] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 14 10:00:37 blotter kernel: [    0.268270] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Jul 14 10:00:37 blotter kernel: [    0.268278] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jul 14 10:00:37 blotter kernel: [    0.268665] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dsfield-211)
Jul 14 10:00:37 blotter kernel: [    0.268681] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 14 10:00:37 blotter kernel: [    0.268698] ACPI: Marking method _OSC as Serialized because of AE_ALREADY_EXISTS error
Jul 14 10:00:37 blotter kernel: [    0.270341] PCI host bridge to bus 0000:00
Jul 14 10:00:37 blotter kernel: [    0.270353] pci_bus 0000:00: root bus resource [bus 00-ff]
Jul 14 10:00:37 blotter kernel: [    0.270360] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
Jul 14 10:00:37 blotter kernel: [    0.270367] pci_bus 0000:00: root bus resource [io  0x0d00-0xefff]
Jul 14 10:00:37 blotter kernel: [    0.270373] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Jul 14 10:00:37 blotter kernel: [    0.270380] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfebfffff]
Jul 14 10:00:37 blotter kernel: [    0.270404] pci 0000:00:00.0: [8086:27ac] type 00 class 0x060000
Jul 14 10:00:37 blotter kernel: [    0.270480] pci 0000:00:02.0: [8086:27ae] type 00 class 0x030000
Jul 14 10:00:37 blotter kernel: [    0.270500] pci 0000:00:02.0: reg 10: [mem 0x58280000-0x582fffff]
Jul 14 10:00:37 blotter kernel: [    0.270513] pci 0000:00:02.0: reg 14: [io  0x60f0-0x60f7]
Jul 14 10:00:37 blotter kernel: [    0.270525] pci 0000:00:02.0: reg 18: [mem 0x40000000-0x4fffffff pref]
Jul 14 10:00:37 blotter kernel: [    0.270537] pci 0000:00:02.0: reg 1c: [mem 0x58300000-0x5833ffff]
Jul 14 10:00:37 blotter kernel: [    0.270601] pci 0000:00:02.1: [8086:27a6] type 00 class 0x038000
Jul 14 10:00:37 blotter kernel: [    0.270618] pci 0000:00:02.1: reg 10: [mem 0x58200000-0x5827ffff]
Jul 14 10:00:37 blotter kernel: [    0.270757] pci 0000:00:1b.0: [8086:27d8] type 00 class 0x040300
Jul 14 10:00:37 blotter kernel: [    0.270789] pci 0000:00:1b.0: reg 10: [mem 0x58340000-0x58343fff 64bit]
Jul 14 10:00:37 blotter kernel: [    0.270912] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jul 14 10:00:37 blotter kernel: [    0.270959] pci 0000:00:1c.0: [8086:27d0] type 01 class 0x060400
Jul 14 10:00:37 blotter kernel: [    0.271087] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jul 14 10:00:37 blotter kernel: [    0.271136] pci 0000:00:1c.1: [8086:27d2] type 01 class 0x060400
Jul 14 10:00:37 blotter kernel: [    0.271264] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jul 14 10:00:37 blotter kernel: [    0.271312] pci 0000:00:1c.2: [8086:27d4] type 01 class 0x060400
Jul 14 10:00:37 blotter kernel: [    0.271440] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
Jul 14 10:00:37 blotter kernel: [    0.271488] pci 0000:00:1c.3: [8086:27d6] type 01 class 0x060400
Jul 14 10:00:37 blotter kernel: [    0.271616] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
Jul 14 10:00:37 blotter kernel: [    0.271665] pci 0000:00:1d.0: [8086:27c8] type 00 class 0x0c0300
Jul 14 10:00:37 blotter kernel: [    0.271732] pci 0000:00:1d.0: reg 20: [io  0x60a0-0x60bf]
Jul 14 10:00:37 blotter kernel: [    0.271791] pci 0000:00:1d.1: [8086:27c9] type 00 class 0x0c0300
Jul 14 10:00:37 blotter kernel: [    0.271858] pci 0000:00:1d.1: reg 20: [io  0x6080-0x609f]
Jul 14 10:00:37 blotter kernel: [    0.271917] pci 0000:00:1d.2: [8086:27ca] type 00 class 0x0c0300
Jul 14 10:00:37 blotter kernel: [    0.271984] pci 0000:00:1d.2: reg 20: [io  0x6060-0x607f]
Jul 14 10:00:37 blotter kernel: [    0.272062] pci 0000:00:1d.3: [8086:27cb] type 00 class 0x0c0300
Jul 14 10:00:37 blotter kernel: [    0.272130] pci 0000:00:1d.3: reg 20: [io  0x6040-0x605f]
Jul 14 10:00:37 blotter kernel: [    0.272203] pci 0000:00:1d.7: [8086:27cc] type 00 class 0x0c0320
Jul 14 10:00:37 blotter kernel: [    0.272235] pci 0000:00:1d.7: reg 10: [mem 0x58344400-0x583447ff]
Jul 14 10:00:37 blotter kernel: [    0.272359] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jul 14 10:00:37 blotter kernel: [    0.272397] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
Jul 14 10:00:37 blotter kernel: [    0.272523] pci 0000:00:1f.0: [8086:27b9] type 00 class 0x060100
Jul 14 10:00:37 blotter kernel: [    0.272660] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
Jul 14 10:00:37 blotter kernel: [    0.272669] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0068 (mask 0007)
Jul 14 10:00:37 blotter kernel: [    0.272751] pci 0000:00:1f.2: [8086:27c5] type 00 class 0x010601
Jul 14 10:00:37 blotter kernel: [    0.272783] pci 0000:00:1f.2: reg 10: [io  0x60d8-0x60df]
Jul 14 10:00:37 blotter kernel: [    0.272800] pci 0000:00:1f.2: reg 14: [io  0x60fc-0x60ff]
Jul 14 10:00:37 blotter kernel: [    0.272818] pci 0000:00:1f.2: reg 18: [io  0x60d0-0x60d7]
Jul 14 10:00:37 blotter kernel: [    0.272836] pci 0000:00:1f.2: reg 1c: [io  0x60f8-0x60fb]
Jul 14 10:00:37 blotter kernel: [    0.272853] pci 0000:00:1f.2: reg 20: [io  0x6020-0x602f]
Jul 14 10:00:37 blotter kernel: [    0.272872] pci 0000:00:1f.2: reg 24: [mem 0x58344000-0x583443ff]
Jul 14 10:00:37 blotter kernel: [    0.272942] pci 0000:00:1f.2: PME# supported from D3hot
Jul 14 10:00:37 blotter kernel: [    0.272977] pci 0000:00:1f.3: [8086:27da] type 00 class 0x0c0500
Jul 14 10:00:37 blotter kernel: [    0.273061] pci 0000:00:1f.3: reg 20: [io  0x6000-0x601f]
Jul 14 10:00:37 blotter kernel: [    0.273302] pci 0000:01:00.0: [14e4:4315] type 00 class 0x028000
Jul 14 10:00:37 blotter kernel: [    0.273380] pci 0000:01:00.0: reg 10: [mem 0x57100000-0x57103fff 64bit]
Jul 14 10:00:37 blotter kernel: [    0.273779] pci 0000:01:00.0: supports D1 D2
Jul 14 10:00:37 blotter kernel: [    0.273965] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jul 14 10:00:37 blotter kernel: [    0.273974] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Jul 14 10:00:37 blotter kernel: [    0.273984] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
Jul 14 10:00:37 blotter kernel: [    0.273998] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.274074] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jul 14 10:00:37 blotter kernel: [    0.274083] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jul 14 10:00:37 blotter kernel: [    0.274093] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
Jul 14 10:00:37 blotter kernel: [    0.274106] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.274212] pci 0000:03:00.0: [1969:1062] type 00 class 0x020000
Jul 14 10:00:37 blotter kernel: [    0.274252] pci 0000:03:00.0: reg 10: [mem 0x55000000-0x5503ffff 64bit]
Jul 14 10:00:37 blotter kernel: [    0.274275] pci 0000:03:00.0: reg 18: [io  0x2000-0x207f]
Jul 14 10:00:37 blotter kernel: [    0.274438] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 14 10:00:37 blotter kernel: [    0.280040] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jul 14 10:00:37 blotter kernel: [    0.280052] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
Jul 14 10:00:37 blotter kernel: [    0.280061] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
Jul 14 10:00:37 blotter kernel: [    0.280075] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.280157] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jul 14 10:00:37 blotter kernel: [    0.280167] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
Jul 14 10:00:37 blotter kernel: [    0.280177] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
Jul 14 10:00:37 blotter kernel: [    0.280190] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.280297] pci 0000:00:1e.0: PCI bridge to [bus 05] (subtractive decode)
Jul 14 10:00:37 blotter kernel: [    0.280317] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
Jul 14 10:00:37 blotter kernel: [    0.280324] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xefff] (subtractive decode)
Jul 14 10:00:37 blotter kernel: [    0.280331] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Jul 14 10:00:37 blotter kernel: [    0.280337] pci 0000:00:1e.0:   bridge window [mem 0x40000000-0xfebfffff] (subtractive decode)
Jul 14 10:00:37 blotter kernel: [    0.280378] pci_bus 0000:00: on NUMA node 0
Jul 14 10:00:37 blotter kernel: [    0.280483] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
Jul 14 10:00:37 blotter kernel: [    0.280673] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
Jul 14 10:00:37 blotter kernel: [    0.280802] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
Jul 14 10:00:37 blotter kernel: [    0.280933] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
Jul 14 10:00:37 blotter kernel: [    0.281233] ACPI Error: [CAPB] Namespace lookup failure, AE_ALREADY_EXISTS (20121018/dsfield-211)
Jul 14 10:00:37 blotter kernel: [    0.281249] ACPI Error: Method parse/execution failed [\_SB_.PCI0._OSC] (Node f5c2aa68), AE_ALREADY_EXISTS (20121018/psparse-537)
Jul 14 10:00:37 blotter kernel: [    0.281274]  pci0000:00: ACPI _OSC support notification failed, disabling PCIe ASPM
Jul 14 10:00:37 blotter kernel: [    0.281280]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x08)
Jul 14 10:00:37 blotter kernel: [    0.283745] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
Jul 14 10:00:37 blotter kernel: [    0.283904] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
Jul 14 10:00:37 blotter kernel: [    0.284078] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
Jul 14 10:00:37 blotter kernel: [    0.284231] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
Jul 14 10:00:37 blotter kernel: [    0.284385] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 14 10:00:37 blotter kernel: [    0.284540] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 14 10:00:37 blotter kernel: [    0.284694] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 14 10:00:37 blotter kernel: [    0.284850] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
Jul 14 10:00:37 blotter kernel: [    0.285143] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
Jul 14 10:00:37 blotter kernel: [    0.285143] vgaarb: loaded
Jul 14 10:00:37 blotter kernel: [    0.285143] vgaarb: bridge control possible 0000:00:02.0
Jul 14 10:00:37 blotter kernel: [    0.285143] SCSI subsystem initialized
Jul 14 10:00:37 blotter kernel: [    0.285143] ACPI: bus type scsi registered
Jul 14 10:00:37 blotter kernel: [    0.285143] libata version 3.00 loaded.
Jul 14 10:00:37 blotter kernel: [    0.285143] ACPI: bus type usb registered
Jul 14 10:00:37 blotter kernel: [    0.285143] usbcore: registered new interface driver usbfs
Jul 14 10:00:37 blotter kernel: [    0.285143] usbcore: registered new interface driver hub
Jul 14 10:00:37 blotter kernel: [    0.285143] usbcore: registered new device driver usb
Jul 14 10:00:37 blotter kernel: [    0.285143] PCI: Using ACPI for IRQ routing
Jul 14 10:00:37 blotter kernel: [    0.295280] PCI: pci_cache_line_size set to 64 bytes
Jul 14 10:00:37 blotter kernel: [    0.295468] e820: reserve RAM buffer [mem 0x0009fc00-0x0009ffff]
Jul 14 10:00:37 blotter kernel: [    0.295475] e820: reserve RAM buffer [mem 0x3f576000-0x3fffffff]
Jul 14 10:00:37 blotter kernel: [    0.295481] e820: reserve RAM buffer [mem 0x3f66d000-0x3fffffff]
Jul 14 10:00:37 blotter kernel: [    0.295486] e820: reserve RAM buffer [mem 0x3f6ee000-0x3fffffff]
Jul 14 10:00:37 blotter kernel: [    0.295491] e820: reserve RAM buffer [mem 0x3f700000-0x3fffffff]
Jul 14 10:00:37 blotter kernel: [    0.295763] NetLabel: Initializing
Jul 14 10:00:37 blotter kernel: [    0.295770] NetLabel:  domain hash size = 128
Jul 14 10:00:37 blotter kernel: [    0.295773] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 14 10:00:37 blotter kernel: [    0.295799] NetLabel:  unlabeled traffic allowed by default
Jul 14 10:00:37 blotter kernel: [    0.296055] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
Jul 14 10:00:37 blotter kernel: [    0.296072] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jul 14 10:00:37 blotter kernel: [    0.296083] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
Jul 14 10:00:37 blotter kernel: [    0.300043] Switching to clocksource hpet
Jul 14 10:00:37 blotter kernel: [    0.315900] AppArmor: AppArmor Filesystem Enabled
Jul 14 10:00:37 blotter kernel: [    0.315977] pnp: PnP ACPI init
Jul 14 10:00:37 blotter kernel: [    0.316066] ACPI: bus type pnp registered
Jul 14 10:00:37 blotter kernel: [    0.380438] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.3 BAR 13 [io  0x1000-0x1fff]
Jul 14 10:00:37 blotter kernel: [    0.380559] system 00:00: [io  0x0200-0x020f] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380577] system 00:00: [io  0x0600-0x060f] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380584] system 00:00: [io  0x0610] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380592] system 00:00: [io  0x0800-0x080f] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380599] system 00:00: [io  0x0400-0x047f] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380606] system 00:00: [io  0x0500-0x053f] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380614] system 00:00: [io  0xff2c-0xff2f] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380624] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380631] system 00:00: [mem 0xfed1c000-0xfed1ffff] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380639] system 00:00: [mem 0xfed14000-0xfed17fff] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380646] system 00:00: [mem 0xfed18000-0xfed18fff] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380654] system 00:00: [mem 0xfed19000-0xfed19fff] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380662] system 00:00: [mem 0xfec00000-0xfec00fff] could not be reserved
Jul 14 10:00:37 blotter kernel: [    0.380669] system 00:00: [mem 0xfee00000-0xfee00fff] has been reserved
Jul 14 10:00:37 blotter kernel: [    0.380681] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 14 10:00:37 blotter kernel: [    0.380714] pnp 00:01: [dma 4]
Jul 14 10:00:37 blotter kernel: [    0.380768] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
Jul 14 10:00:37 blotter kernel: [    0.380883] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 14 10:00:37 blotter kernel: [    0.381131] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
Jul 14 10:00:37 blotter kernel: [    0.381220] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
Jul 14 10:00:37 blotter kernel: [    0.381297] pnp 00:05: Plug and Play ACPI device, IDs INT0800 (active)
Jul 14 10:00:37 blotter kernel: [    0.381423] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 14 10:00:37 blotter kernel: [    0.381642] pnp 00:07: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
Jul 14 10:00:37 blotter kernel: [    0.382060] pnp: PnP ACPI: found 8 devices
Jul 14 10:00:37 blotter kernel: [    0.382066] ACPI: ACPI bus type pnp unregistered
Jul 14 10:00:37 blotter kernel: [    0.382073] PnPBIOS: Disabled by ACPI PNP
Jul 14 10:00:37 blotter kernel: [    0.422931] pci 0000:00:1c.0: PCI bridge to [bus 01]
Jul 14 10:00:37 blotter kernel: [    0.422945] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
Jul 14 10:00:37 blotter kernel: [    0.422957] pci 0000:00:1c.0:   bridge window [mem 0x57100000-0x581fffff]
Jul 14 10:00:37 blotter kernel: [    0.422968] pci 0000:00:1c.0:   bridge window [mem 0x50000000-0x50ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.422981] pci 0000:00:1c.1: PCI bridge to [bus 02]
Jul 14 10:00:37 blotter kernel: [    0.422989] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
Jul 14 10:00:37 blotter kernel: [    0.423000] pci 0000:00:1c.1:   bridge window [mem 0x56100000-0x570fffff]
Jul 14 10:00:37 blotter kernel: [    0.423010] pci 0000:00:1c.1:   bridge window [mem 0x51000000-0x51ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.423023] pci 0000:00:1c.2: PCI bridge to [bus 03]
Jul 14 10:00:37 blotter kernel: [    0.423031] pci 0000:00:1c.2:   bridge window [io  0x2000-0x3fff]
Jul 14 10:00:37 blotter kernel: [    0.423042] pci 0000:00:1c.2:   bridge window [mem 0x55000000-0x560fffff]
Jul 14 10:00:37 blotter kernel: [    0.423052] pci 0000:00:1c.2:   bridge window [mem 0x52000000-0x52ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.423064] pci 0000:00:1c.3: PCI bridge to [bus 04]
Jul 14 10:00:37 blotter kernel: [    0.423072] pci 0000:00:1c.3:   bridge window [io  0x1000-0x1fff]
Jul 14 10:00:37 blotter kernel: [    0.423083] pci 0000:00:1c.3:   bridge window [mem 0x54000000-0x54ffffff]
Jul 14 10:00:37 blotter kernel: [    0.423093] pci 0000:00:1c.3:   bridge window [mem 0x53000000-0x53ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.423105] pci 0000:00:1e.0: PCI bridge to [bus 05]
Jul 14 10:00:37 blotter kernel: [    0.423165] pci 0000:00:1c.1: enabling device (0000 -> 0003)
Jul 14 10:00:37 blotter kernel: [    0.423205] pci 0000:00:1c.3: enabling device (0000 -> 0003)
Jul 14 10:00:37 blotter kernel: [    0.423238] pci 0000:00:1e.0: setting latency timer to 64
Jul 14 10:00:37 blotter kernel: [    0.423249] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
Jul 14 10:00:37 blotter kernel: [    0.423255] pci_bus 0000:00: resource 5 [io  0x0d00-0xefff]
Jul 14 10:00:37 blotter kernel: [    0.423262] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
Jul 14 10:00:37 blotter kernel: [    0.423269] pci_bus 0000:00: resource 7 [mem 0x40000000-0xfebfffff]
Jul 14 10:00:37 blotter kernel: [    0.423276] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
Jul 14 10:00:37 blotter kernel: [    0.423282] pci_bus 0000:01: resource 1 [mem 0x57100000-0x581fffff]
Jul 14 10:00:37 blotter kernel: [    0.423289] pci_bus 0000:01: resource 2 [mem 0x50000000-0x50ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.423296] pci_bus 0000:02: resource 0 [io  0x4000-0x4fff]
Jul 14 10:00:37 blotter kernel: [    0.423303] pci_bus 0000:02: resource 1 [mem 0x56100000-0x570fffff]
Jul 14 10:00:37 blotter kernel: [    0.423310] pci_bus 0000:02: resource 2 [mem 0x51000000-0x51ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.423316] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
Jul 14 10:00:37 blotter kernel: [    0.423323] pci_bus 0000:03: resource 1 [mem 0x55000000-0x560fffff]
Jul 14 10:00:37 blotter kernel: [    0.423330] pci_bus 0000:03: resource 2 [mem 0x52000000-0x52ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.423336] pci_bus 0000:04: resource 0 [io  0x1000-0x1fff]
Jul 14 10:00:37 blotter kernel: [    0.423343] pci_bus 0000:04: resource 1 [mem 0x54000000-0x54ffffff]
Jul 14 10:00:37 blotter kernel: [    0.423350] pci_bus 0000:04: resource 2 [mem 0x53000000-0x53ffffff 64bit pref]
Jul 14 10:00:37 blotter kernel: [    0.423357] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7]
Jul 14 10:00:37 blotter kernel: [    0.423363] pci_bus 0000:05: resource 5 [io  0x0d00-0xefff]
Jul 14 10:00:37 blotter kernel: [    0.423370] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff]
Jul 14 10:00:37 blotter kernel: [    0.423377] pci_bus 0000:05: resource 7 [mem 0x40000000-0xfebfffff]
Jul 14 10:00:37 blotter kernel: [    0.423456] NET: Registered protocol family 2
Jul 14 10:00:37 blotter kernel: [    0.423770] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Jul 14 10:00:37 blotter kernel: [    0.423833] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
Jul 14 10:00:37 blotter kernel: [    0.423893] TCP: Hash tables configured (established 8192 bind 8192)
Jul 14 10:00:37 blotter kernel: [    0.423940] TCP: reno registered
Jul 14 10:00:37 blotter kernel: [    0.423948] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul 14 10:00:37 blotter kernel: [    0.423967] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul 14 10:00:37 blotter kernel: [    0.424151] NET: Registered protocol family 1
Jul 14 10:00:37 blotter kernel: [    0.424190] pci 0000:00:02.0: Boot video device
Jul 14 10:00:37 blotter kernel: [    0.424555] PCI: CLS 0 bytes, default 64
Jul 14 10:00:37 blotter kernel: [    0.424680] Trying to unpack rootfs image as initramfs...
Jul 14 10:00:37 blotter kernel: [    1.133726] Freeing initrd memory: 16256k freed
Jul 14 10:00:37 blotter kernel: [    1.150506] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
Jul 14 10:00:37 blotter kernel: [    1.150517] Simple Boot Flag at 0x44 set to 0x1
Jul 14 10:00:37 blotter kernel: [    1.151198] Initialise module verification
Jul 14 10:00:37 blotter kernel: [    1.151303] audit: initializing netlink socket (disabled)
Jul 14 10:00:37 blotter kernel: [    1.151330] type=2000 audit(1373810419.148:1): initialized
Jul 14 10:00:37 blotter kernel: [    1.199376] bounce pool size: 64 pages
Jul 14 10:00:37 blotter kernel: [    1.199405] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 14 10:00:37 blotter kernel: [    1.203353] VFS: Disk quotas dquot_6.5.2
Jul 14 10:00:37 blotter kernel: [    1.203492] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jul 14 10:00:37 blotter kernel: [    1.205014] fuse init (API version 7.20)
Jul 14 10:00:37 blotter kernel: [    1.205253] msgmni has been set to 1740
Jul 14 10:00:37 blotter kernel: [    1.206358] Key type asymmetric registered
Jul 14 10:00:37 blotter kernel: [    1.206367] Asymmetric key parser 'x509' registered
Jul 14 10:00:37 blotter kernel: [    1.206485] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Jul 14 10:00:37 blotter kernel: [    1.206557] io scheduler noop registered
Jul 14 10:00:37 blotter kernel: [    1.206565] io scheduler deadline registered (default)
Jul 14 10:00:37 blotter kernel: [    1.206584] io scheduler cfq registered
Jul 14 10:00:37 blotter kernel: [    1.206916] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
Jul 14 10:00:37 blotter kernel: [    1.207113] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
Jul 14 10:00:37 blotter kernel: [    1.207293] pcieport 0000:00:1c.2: irq 42 for MSI/MSI-X
Jul 14 10:00:37 blotter kernel: [    1.207472] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
Jul 14 10:00:37 blotter kernel: [    1.207651] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 14 10:00:37 blotter kernel: [    1.207703] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 14 10:00:37 blotter kernel: [    1.207836] intel_idle: MWAIT substates: 0x20220
Jul 14 10:00:37 blotter kernel: [    1.207857] intel_idle: v0.4 model 0x1C
Jul 14 10:00:37 blotter kernel: [    1.207861] intel_idle: lapic_timer_reliable_states 0x2
Jul 14 10:00:37 blotter kernel: [    1.207867] tsc: Marking TSC unstable due to TSC halts in idle states deeper than C2
Jul 14 10:00:37 blotter kernel: [    1.332096] ACPI: AC Adapter [AC] (on-line)
Jul 14 10:00:37 blotter kernel: [    1.332318] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
Jul 14 10:00:37 blotter kernel: [    1.332331] ACPI: Power Button [PWRB]
Jul 14 10:00:37 blotter kernel: [    1.332437] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
Jul 14 10:00:37 blotter kernel: [    1.332480] ACPI: Lid Switch [LID0]
Jul 14 10:00:37 blotter kernel: [    1.332581] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
Jul 14 10:00:37 blotter kernel: [    1.332590] ACPI: Sleep Button [SLPB]
Jul 14 10:00:37 blotter kernel: [    1.332711] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jul 14 10:00:37 blotter kernel: [    1.332720] ACPI: Power Button [PWRF]
Jul 14 10:00:37 blotter kernel: [    1.332867] ACPI: Fan [FAN] (on)
Jul 14 10:00:37 blotter kernel: [    1.333001] ACPI: Requesting acpi_cpufreq
Jul 14 10:00:37 blotter kernel: [    1.467035] thermal LNXTHERM:00: registered as thermal_zone0
Jul 14 10:00:37 blotter kernel: [    1.467044] ACPI: Thermal Zone [THRM] (27 C)
Jul 14 10:00:37 blotter kernel: [    1.467139] GHES: HEST is not enabled!
Jul 14 10:00:37 blotter kernel: [    1.467311] isapnp: Scanning for PnP cards...
Jul 14 10:00:37 blotter kernel: [    1.467484] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 14 10:00:37 blotter kernel: [    1.821343] isapnp: No Plug & Play device found
Jul 14 10:00:37 blotter kernel: [    2.124257] ACPI: Battery Slot [BAT0] (battery present)
Jul 14 10:00:37 blotter kernel: [    2.124496] Linux agpgart interface v0.103
Jul 14 10:00:37 blotter kernel: [    2.124640] agpgart-intel 0000:00:00.0: Intel 945GME Chipset
Jul 14 10:00:37 blotter kernel: [    2.124810] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
Jul 14 10:00:37 blotter kernel: [    2.124974] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
Jul 14 10:00:37 blotter kernel: [    2.125252] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
Jul 14 10:00:37 blotter kernel: [    2.129461] brd: module loaded
Jul 14 10:00:37 blotter kernel: [    2.131647] loop: module loaded
Jul 14 10:00:37 blotter kernel: [    2.132897] libphy: Fixed MDIO Bus: probed
Jul 14 10:00:37 blotter kernel: [    2.133126] tun: Universal TUN/TAP device driver, 1.6
Jul 14 10:00:37 blotter kernel: [    2.133131] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 14 10:00:37 blotter kernel: [    2.133295] PPP generic driver version 2.4.2
Jul 14 10:00:37 blotter kernel: [    2.133447] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 14 10:00:37 blotter kernel: [    2.133452] ehci-pci: EHCI PCI platform driver
Jul 14 10:00:37 blotter kernel: [    2.133533] ehci-pci 0000:00:1d.7: setting latency timer to 64
Jul 14 10:00:37 blotter kernel: [    2.133543] ehci-pci 0000:00:1d.7: EHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.133558] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
Jul 14 10:00:37 blotter kernel: [    2.133585] ehci-pci 0000:00:1d.7: debug port 1
Jul 14 10:00:37 blotter kernel: [    2.137525] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
Jul 14 10:00:37 blotter kernel: [    2.137567] ehci-pci 0000:00:1d.7: irq 16, io mem 0x58344400
Jul 14 10:00:37 blotter kernel: [    2.148048] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
Jul 14 10:00:37 blotter kernel: [    2.148117] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Jul 14 10:00:37 blotter kernel: [    2.148124] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 10:00:37 blotter kernel: [    2.148131] usb usb1: Product: EHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.148137] usb usb1: Manufacturer: Linux 3.8.0-26-generic ehci_hcd
Jul 14 10:00:37 blotter kernel: [    2.148142] usb usb1: SerialNumber: 0000:00:1d.7
Jul 14 10:00:37 blotter kernel: [    2.148487] hub 1-0:1.0: USB hub found
Jul 14 10:00:37 blotter kernel: [    2.148501] hub 1-0:1.0: 8 ports detected
Jul 14 10:00:37 blotter kernel: [    2.148845] ehci-platform: EHCI generic platform driver
Jul 14 10:00:37 blotter kernel: [    2.148876] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 14 10:00:37 blotter kernel: [    2.148926] uhci_hcd: USB Universal Host Controller Interface driver
Jul 14 10:00:37 blotter kernel: [    2.148978] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Jul 14 10:00:37 blotter kernel: [    2.148987] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.149006] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
Jul 14 10:00:37 blotter kernel: [    2.149051] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000060a0
Jul 14 10:00:37 blotter kernel: [    2.149136] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
Jul 14 10:00:37 blotter kernel: [    2.149143] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 10:00:37 blotter kernel: [    2.149149] usb usb2: Product: UHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.149155] usb usb2: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 14 10:00:37 blotter kernel: [    2.149161] usb usb2: SerialNumber: 0000:00:1d.0
Jul 14 10:00:37 blotter kernel: [    2.149444] hub 2-0:1.0: USB hub found
Jul 14 10:00:37 blotter kernel: [    2.149457] hub 2-0:1.0: 2 ports detected
Jul 14 10:00:37 blotter kernel: [    2.149646] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Jul 14 10:00:37 blotter kernel: [    2.149654] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.149668] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
Jul 14 10:00:37 blotter kernel: [    2.149737] uhci_hcd 0000:00:1d.1: irq 17, io base 0x00006080
Jul 14 10:00:37 blotter kernel: [    2.149819] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
Jul 14 10:00:37 blotter kernel: [    2.149826] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 10:00:37 blotter kernel: [    2.149833] usb usb3: Product: UHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.149838] usb usb3: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 14 10:00:37 blotter kernel: [    2.149844] usb usb3: SerialNumber: 0000:00:1d.1
Jul 14 10:00:37 blotter kernel: [    2.150095] hub 3-0:1.0: USB hub found
Jul 14 10:00:37 blotter kernel: [    2.150107] hub 3-0:1.0: 2 ports detected
Jul 14 10:00:37 blotter kernel: [    2.150285] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Jul 14 10:00:37 blotter kernel: [    2.150293] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.150307] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
Jul 14 10:00:37 blotter kernel: [    2.150368] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00006060
Jul 14 10:00:37 blotter kernel: [    2.150452] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Jul 14 10:00:37 blotter kernel: [    2.150460] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 10:00:37 blotter kernel: [    2.150466] usb usb4: Product: UHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.150472] usb usb4: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 14 10:00:37 blotter kernel: [    2.150477] usb usb4: SerialNumber: 0000:00:1d.2
Jul 14 10:00:37 blotter kernel: [    2.150722] hub 4-0:1.0: USB hub found
Jul 14 10:00:37 blotter kernel: [    2.150734] hub 4-0:1.0: 2 ports detected
Jul 14 10:00:37 blotter kernel: [    2.150912] uhci_hcd 0000:00:1d.3: setting latency timer to 64
Jul 14 10:00:37 blotter kernel: [    2.150921] uhci_hcd 0000:00:1d.3: UHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.150935] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
Jul 14 10:00:37 blotter kernel: [    2.150996] uhci_hcd 0000:00:1d.3: irq 19, io base 0x00006040
Jul 14 10:00:37 blotter kernel: [    2.151077] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Jul 14 10:00:37 blotter kernel: [    2.151084] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Jul 14 10:00:37 blotter kernel: [    2.151090] usb usb5: Product: UHCI Host Controller
Jul 14 10:00:37 blotter kernel: [    2.151096] usb usb5: Manufacturer: Linux 3.8.0-26-generic uhci_hcd
Jul 14 10:00:37 blotter kernel: [    2.151102] usb usb5: SerialNumber: 0000:00:1d.3
Jul 14 10:00:37 blotter kernel: [    2.151375] hub 5-0:1.0: USB hub found
Jul 14 10:00:37 blotter kernel: [    2.151387] hub 5-0:1.0: 2 ports detected
Jul 14 10:00:37 blotter kernel: [    2.151793] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
Jul 14 10:00:37 blotter kernel: [    2.172085] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 14 10:00:37 blotter kernel: [    2.172109] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 14 10:00:37 blotter kernel: [    2.172471] mousedev: PS/2 mouse device common for all mice
Jul 14 10:00:37 blotter kernel: [    2.173012] rtc_cmos 00:02: RTC can wake from S4
Jul 14 10:00:37 blotter kernel: [    2.173257] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Jul 14 10:00:37 blotter kernel: [    2.173307] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
Jul 14 10:00:37 blotter kernel: [    2.173541] device-mapper: uevent: version 1.0.3
Jul 14 10:00:37 blotter kernel: [    2.173725] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
Jul 14 10:00:37 blotter kernel: [    2.173776] EISA: Probing bus 0 at eisa.0
Jul 14 10:00:37 blotter kernel: [    2.173783] EISA: Cannot allocate resource for mainboard
Jul 14 10:00:37 blotter kernel: [    2.173788] Cannot allocate resource for EISA slot 1
Jul 14 10:00:37 blotter kernel: [    2.173794] Cannot allocate resource for EISA slot 2
Jul 14 10:00:37 blotter kernel: [    2.173799] Cannot allocate resource for EISA slot 3
Jul 14 10:00:37 blotter kernel: [    2.173803] Cannot allocate resource for EISA slot 4
Jul 14 10:00:37 blotter kernel: [    2.173808] Cannot allocate resource for EISA slot 5
Jul 14 10:00:37 blotter kernel: [    2.173813] Cannot allocate resource for EISA slot 6
Jul 14 10:00:37 blotter kernel: [    2.173818] Cannot allocate resource for EISA slot 7
Jul 14 10:00:37 blotter kernel: [    2.173823] Cannot allocate resource for EISA slot 8
Jul 14 10:00:37 blotter kernel: [    2.173827] EISA: Detected 0 cards.
Jul 14 10:00:37 blotter kernel: [    2.173846] cpufreq-nforce2: No nForce2 chipset.
Jul 14 10:00:37 blotter kernel: [    2.173942] cpuidle: using governor ladder
Jul 14 10:00:37 blotter kernel: [    2.174067] cpuidle: using governor menu
Jul 14 10:00:37 blotter kernel: [    2.174076] ledtrig-cpu: registered to indicate activity on CPUs
Jul 14 10:00:37 blotter kernel: [    2.174080] EFI Variables Facility v0.08 2004-May-17
Jul 14 10:00:37 blotter kernel: [    2.174677] ashmem: initialized
Jul 14 10:00:37 blotter kernel: [    2.175026] TCP: cubic registered
Jul 14 10:00:37 blotter kernel: [    2.175292] NET: Registered protocol family 10
Jul 14 10:00:37 blotter kernel: [    2.175733] NET: Registered protocol family 17
Jul 14 10:00:37 blotter kernel: [    2.175768] Key type dns_resolver registered
Jul 14 10:00:37 blotter kernel: [    2.176218] Using IPI No-Shortcut mode
Jul 14 10:00:37 blotter kernel: [    2.176525] Loading module verification certificates
Jul 14 10:00:37 blotter kernel: [    2.188867] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: d1850ecb2327d153922b22332b63536822dc0add'
Jul 14 10:00:37 blotter kernel: [    2.188898] registered taskstats version 1
Jul 14 10:00:37 blotter kernel: [    2.195844] Key type trusted registered
Jul 14 10:00:37 blotter kernel: [    2.200124] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Jul 14 10:00:37 blotter kernel: [    2.203075] Key type encrypted registered
Jul 14 10:00:37 blotter kernel: [    2.213766] rtc_cmos 00:02: setting system clock to 2013-07-14 14:00:21 UTC (1373810421)
Jul 14 10:00:37 blotter kernel: [    2.215485] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 14 10:00:37 blotter kernel: [    2.215491] EDD information not available.
Jul 14 10:00:37 blotter kernel: [    2.215866] Freeing unused kernel memory: 788k freed
Jul 14 10:00:37 blotter kernel: [    2.216621] Write protecting the kernel text: 6256k
Jul 14 10:00:37 blotter kernel: [    2.216755] Write protecting the kernel read-only data: 2432k
Jul 14 10:00:37 blotter kernel: [    2.216761] NX-protecting the kernel data: 3984k
Jul 14 10:00:37 blotter kernel: [    2.460140] usb 1-2: new high-speed USB device number 2 using ehci-pci
Jul 14 10:00:37 blotter kernel: [    2.606643] Disabling lock debugging due to kernel taint
Jul 14 10:00:37 blotter kernel: [    2.626039] usb 1-2: New USB device found, idVendor=04f2, idProduct=b175
Jul 14 10:00:37 blotter kernel: [    2.626053] usb 1-2: New USB device strings: Mfr=2, Product=1, SerialNumber=3
Jul 14 10:00:37 blotter kernel: [    2.626062] usb 1-2: Product: CNF9011
Jul 14 10:00:37 blotter kernel: [    2.626071] usb 1-2: Manufacturer: Chicony Electronics Co., Ltd.
Jul 14 10:00:37 blotter kernel: [    2.626079] usb 1-2: SerialNumber: SN0001
Jul 14 10:00:37 blotter kernel: [    2.628887] atl1c 0000:03:00.0: version 1.0.1.1-NAPI
Jul 14 10:00:37 blotter kernel: [    2.630127] ahci 0000:00:1f.2: version 3.0
Jul 14 10:00:37 blotter kernel: [    2.630276] ahci 0000:00:1f.2: irq 44 for MSI/MSI-X
Jul 14 10:00:37 blotter kernel: [    2.630385] ahci: SSS flag set, parallel bus scan disabled
Jul 14 10:00:37 blotter kernel: [    2.630452] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0x5 impl SATA mode
Jul 14 10:00:37 blotter kernel: [    2.630467] ahci 0000:00:1f.2: flags: 64bit ncq ilck stag pm led clo pio slum part 
Jul 14 10:00:37 blotter kernel: [    2.630481] ahci 0000:00:1f.2: setting latency timer to 64
Jul 14 10:00:37 blotter kernel: [    2.635659] scsi0 : ahci
Jul 14 10:00:37 blotter kernel: [    2.639110] scsi1 : ahci
Jul 14 10:00:37 blotter kernel: [    2.640282] scsi2 : ahci
Jul 14 10:00:37 blotter kernel: [    2.640637] scsi3 : ahci
Jul 14 10:00:37 blotter kernel: [    2.640843] ata1: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344100 irq 44
Jul 14 10:00:37 blotter kernel: [    2.640853] ata2: DUMMY
Jul 14 10:00:37 blotter kernel: [    2.640863] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq 44
Jul 14 10:00:37 blotter kernel: [    2.640870] ata4: DUMMY
Jul 14 10:00:37 blotter kernel: [    2.960166] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 14 10:00:37 blotter kernel: [    2.961439] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
Jul 14 10:00:37 blotter kernel: [    3.008816] ata1.00: ATA-8: WDC WD1600BEVT-22ZCT0, 11.01A11, max UDMA/133
Jul 14 10:00:37 blotter kernel: [    3.008832] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Jul 14 10:00:37 blotter kernel: [    3.010713] ata1.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
Jul 14 10:00:37 blotter kernel: [    3.011028] ata1.00: configured for UDMA/133
Jul 14 10:00:37 blotter kernel: [    3.011484] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVT-2 11.0 PQ: 0 ANSI: 5
Jul 14 10:00:37 blotter kernel: [    3.011984] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
Jul 14 10:00:37 blotter kernel: [    3.012174] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jul 14 10:00:37 blotter kernel: [    3.012354] sd 0:0:0:0: [sda] Write Protect is off
Jul 14 10:00:37 blotter kernel: [    3.012365] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 14 10:00:37 blotter kernel: [    3.012476] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 14 10:00:37 blotter kernel: [    3.030297]  sda: sda1 sda2 < sda5 >
Jul 14 10:00:37 blotter kernel: [    3.031575] sd 0:0:0:0: [sda] Attached SCSI disk
Jul 14 10:00:37 blotter kernel: [    3.332165] ata3: SATA link down (SStatus 0 SControl 300)
Jul 14 10:00:37 blotter kernel: [    3.620136] bio: create slab <bio-1> at 1
Jul 14 10:00:37 blotter kernel: [    4.024335] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
Jul 14 10:00:37 blotter kernel: [   13.991466] Adding 1040380k swap on /dev/mapper/lubuntu--vg-swap_1.  Priority:-1 extents:1 across:1040380k 
Jul 14 10:00:37 blotter kernel: [   14.141384] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 14 10:00:37 blotter kernel: [   14.726404] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
Jul 14 10:00:37 blotter kernel: [   14.960792] lp: driver loaded but no devices found
Jul 14 10:00:37 blotter kernel: [   15.120407] acpi device:24: registered as cooling_device3
Jul 14 10:00:37 blotter kernel: [   15.120569] ACPI: Video Device [OVGA] (multi-head: yes  rom: yes  post: no)
Jul 14 10:00:37 blotter kernel: [   15.120935] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
Jul 14 10:00:37 blotter kernel: [   15.129417] wmi: Mapper loaded
Jul 14 10:00:37 blotter kernel: [   15.487271] type=1400 audit(1373810434.767:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=498 comm="apparmor_parser"
Jul 14 10:00:37 blotter kernel: [   15.489268] type=1400 audit(1373810434.771:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=498 comm="apparmor_parser"
Jul 14 10:00:37 blotter kernel: [   15.490110] type=1400 audit(1373810434.771:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=498 comm="apparmor_parser"
Jul 14 10:00:37 blotter kernel: [   15.517049] type=1400 audit(1373810434.799:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/ntpd" pid=499 comm="apparmor_parser"
Jul 14 10:00:37 blotter kernel: [   15.572512] cfg80211: Calling CRDA to update world regulatory domain
Jul 14 10:00:37 blotter kernel: [   15.661731] lib80211: common routines for IEEE802.11 drivers
Jul 14 10:00:37 blotter kernel: [   15.661743] lib80211_crypt: registered algorithm 'NULL'
Jul 14 10:00:37 blotter kernel: [   15.728265] intel_rng: FWH not detected
Jul 14 10:00:37 blotter kernel: [   15.741142] [drm] Initialized drm 1.1.0 20060810
Jul 14 10:00:37 blotter kernel: [   15.885060] microcode: CPU0 sig=0x106c2, pf=0x4, revision=0x212
Jul 14 10:00:37 blotter kernel: [   15.920236] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \PMBA 1 (20121018/utaddress-251)
Jul 14 10:00:37 blotter kernel: [   15.920256] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 14 10:00:37 blotter kernel: [   15.920266] ACPI Warning: 0x00000530-0x0000053f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Jul 14 10:00:37 blotter kernel: [   15.920279] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 14 10:00:37 blotter kernel: [   15.920286] ACPI Warning: 0x00000500-0x0000052f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
Jul 14 10:00:37 blotter kernel: [   15.920298] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Jul 14 10:00:37 blotter kernel: [   15.920304] lpc_ich: Resource conflict(s) found affecting gpio_ich
Jul 14 10:00:37 blotter kernel: [   16.458512] leds_ss4200: no LED devices found
Jul 14 10:00:37 blotter kernel: [   16.493453] microcode: CPU1 sig=0x106c2, pf=0x4, revision=0x212
Jul 14 10:00:37 blotter kernel: [   16.511589] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 14 10:00:37 blotter kernel: [   16.674966] acer_wmi: Acer Laptop ACPI-WMI Extras
Jul 14 10:00:37 blotter kernel: [   16.730332] Linux video capture interface: v2.00
Jul 14 10:00:37 blotter kernel: [   16.731577] i915 0000:00:02.0: setting latency timer to 64
Jul 14 10:00:37 blotter kernel: [   16.732457] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
Jul 14 10:00:37 blotter kernel: [   16.732467] [drm] Driver supports precise vblank timestamp query.
Jul 14 10:00:37 blotter kernel: [   16.732643] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
Jul 14 10:00:37 blotter kernel: [   16.842388] cfg80211: World regulatory domain updated:
Jul 14 10:00:37 blotter kernel: [   16.842398] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jul 14 10:00:37 blotter kernel: [   16.842405] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 14 10:00:37 blotter kernel: [   16.842411] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 14 10:00:37 blotter kernel: [   16.842416] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jul 14 10:00:37 blotter kernel: [   16.842421] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 14 10:00:37 blotter kernel: [   16.842426] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jul 14 10:00:37 blotter kernel: [   16.853977] acer_wmi: Function bitmap for Communication Device: 0x1
Jul 14 10:00:37 blotter kernel: [   16.853997] acer_wmi: Brightness must be controlled by acpi video driver
Jul 14 10:00:37 blotter kernel: [   16.854987] input: Acer BMA150 accelerometer as /devices/virtual/input/input6
Jul 14 10:00:37 blotter kernel: [   16.886301] [drm] initialized overlay support
Jul 14 10:00:37 blotter kernel: [   16.997273] wl: module license 'MIXED/Proprietary' taints kernel.
Jul 14 10:00:37 blotter kernel: [   17.110693] INFO @wl_cfg80211_attach : Registered CFG80211 phy
Jul 14 10:00:37 blotter kernel: [   17.214624] lib80211_crypt: registered algorithm 'TKIP'
Jul 14 10:00:37 blotter kernel: [   17.223412] fbcon: inteldrmfb (fb0) is primary device
Jul 14 10:00:37 blotter kernel: [   17.529386] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
Jul 14 10:00:37 blotter kernel: [   17.611284] uvcvideo: Found UVC 1.00 device CNF9011 (04f2:b175)
Jul 14 10:00:37 blotter kernel: [   17.628890] input: CNF9011 as /devices/pci0000:00/0000:00:1d.7/usb1/1-2/1-2:1.0/input/input7
Jul 14 10:00:37 blotter kernel: [   17.629521] usbcore: registered new interface driver uvcvideo
Jul 14 10:00:37 blotter kernel: [   17.629523] USB Video Class driver (1.1.1)
Jul 14 10:00:37 blotter kernel: [   17.633484] i915: fixme: max PWM is zero
Jul 14 10:00:37 blotter kernel: [   17.633662] Console: switching to colour frame buffer device 128x37
Jul 14 10:00:37 blotter kernel: [   17.643302] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
Jul 14 10:00:37 blotter kernel: [   17.643307] i915 0000:00:02.0: registered panic notifier
Jul 14 10:00:37 blotter kernel: [   17.644079] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jul 14 10:00:37 blotter kernel: [   17.644352] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
Jul 14 10:00:37 blotter kernel: [   17.684072] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04773/0xa40000/0xa0000, board id: 3655, fw id: 511380
Jul 14 10:00:37 blotter kernel: [   17.764396] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
Jul 14 10:00:37 blotter kernel: [   17.905953] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
Jul 14 10:00:37 blotter kernel: [   17.906389] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Jul 14 10:00:37 blotter kernel: [   18.170343] Bluetooth: Core ver 2.16
Jul 14 10:00:37 blotter kernel: [   18.170605] NET: Registered protocol family 31
Jul 14 10:00:37 blotter kernel: [   18.170613] Bluetooth: HCI device and connection manager initialized
Jul 14 10:00:37 blotter kernel: [   18.172173] Bluetooth: HCI socket layer initialized
Jul 14 10:00:37 blotter kernel: [   18.172192] Bluetooth: L2CAP socket layer initialized
Jul 14 10:00:37 blotter kernel: [   18.172242] Bluetooth: SCO socket layer initialized
Jul 14 10:00:38 blotter kernel: [   18.720557] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jul 14 10:00:38 blotter kernel: [   18.720569] Bluetooth: BNEP filters: protocol multicast
Jul 14 10:00:38 blotter kernel: [   18.720599] Bluetooth: BNEP socket layer initialized
Jul 14 10:00:38 blotter kernel: [   19.116425] Bluetooth: RFCOMM TTY layer initialized
Jul 14 10:00:38 blotter kernel: [   19.116465] Bluetooth: RFCOMM socket layer initialized
Jul 14 10:00:38 blotter kernel: [   19.116472] Bluetooth: RFCOMM ver 1.11
Jul 14 10:00:39 blotter kernel: [   20.673201] type=1400 audit(1373810439.955:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=835 comm="apparmor_parser"
Jul 14 10:00:39 blotter kernel: [   20.674444] type=1400 audit(1373810439.955:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=835 comm="apparmor_parser"
Jul 14 10:00:39 blotter kernel: [   20.690005] type=1400 audit(1373810439.971:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=836 comm="apparmor_parser"
Jul 14 10:00:39 blotter kernel: [   20.691603] type=1400 audit(1373810439.971:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=836 comm="apparmor_parser"
Jul 14 10:00:39 blotter kernel: [   20.692947] type=1400 audit(1373810439.975:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=836 comm="apparmor_parser"
Jul 14 10:00:40 blotter kernel: [   20.737612] type=1400 audit(1373810440.019:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=839 comm="apparmor_parser"
Jul 14 10:00:40 blotter kernel: [   20.748951] type=1400 audit(1373810440.031:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=839 comm="apparmor_parser"
Jul 14 10:00:40 blotter kernel: [   20.767345] type=1400 audit(1373810440.047:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=837 comm="apparmor_parser"
Jul 14 10:00:40 blotter kernel: [   20.782635] type=1400 audit(1373810440.063:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/ntpd" pid=841 comm="apparmor_parser"
Jul 14 10:00:40 blotter kernel: [   20.794726] type=1400 audit(1373810440.075:15): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince//sanitized_helper" pid=837 comm="apparmor_parser"
Jul 14 10:00:40 blotter kernel: [   21.338806] atl1c 0000:03:00.0: irq 46 for MSI/MSI-X
Jul 14 10:00:40 blotter kernel: [   21.353987] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 14 10:00:40 blotter kernel: [   21.388384] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready

```
====END TEXT OF kern.log.1====

---

### Post by mathias3004 on 2013-09-02
Hi,

I'm having a similar problem, exactly the same two error lines:

"Kernel panic - not syncing: Fatal exception in interrupt "
drm_kms_helper: panic occurred, switching back to text console" 

I have a dual boot Windows 7 and Ubuntu and I recently formatted my hard drive and reinstalled both of them, while upgrading Ubuntu from 12.04 to 13.04. Ever since, I've got this black screen appearing after some minutes. I've already tried loading an older linux kernel, but this doesn't help either. Windows is working fine. 
Did you find any solution to this problem? All help is welcome! Thanks!

---

### Post by Mephisto Pheles on 2013-09-12
I had the same problem on xubuntu turns out it was the nouveau drivers, so I installed the latest nvidia drivers and problem solved.
I should be so lucky ;)

---

