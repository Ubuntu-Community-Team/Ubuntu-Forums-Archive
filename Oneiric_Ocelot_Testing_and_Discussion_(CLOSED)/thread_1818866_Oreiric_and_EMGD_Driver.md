---
title: "Oreiric and EMGD Driver"
date: 2011-08-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fjgaude on 2011-08-05
Hello, Luca and all!

I was unable to do a fresh install of Alpha 3 so I took the Alpha 2 install with the psb-gfx driver you recommended sometime ago I had on my Dell 10n and replaced the old repository with the emgd one.

I know I needed to do more than that but I didn't. I booted and installed your emgd driver and all went well, except I had to use the poulsbo dummy=1 at the kernel line.

The emgd works good in Unity 2D and logs into 3D but without launcher or icons in the panel. Things work but not as they should.

What could you recommend in terms of me purging things and starting over but with the same totally updated Alpha 2 install?

---

### Post by lucazade on 2011-08-05
> **fjgaude said:**
> Hello, Luca and all!

I was unable to do a fresh install of Alpha 3 so I took the Alpha 2 install with the psb-gfx driver you recommended sometime ago I had on my Dell 10n and replaced the old repository with the emgd one.

I know I needed to do more than that but I didn't. I booted and installed your emgd driver and all went well, except I had to use the poulsbo dummy=1 at the kernel line.

The emgd works good in Unity 2D and logs into 3D but without launcher or icons in the panel. Things work but not as they should.

What could you recommend in terms of me purging things and starting over but with the same totally updated Alpha 2 install?

you could make poulsbo.dummy=1 or psb_gfx.dummy=1 permanent by blacklisting these kernel modules

echo "blacklist poulsbo" | sudo tee -a /etc/modprobe.d/blacklist.conf
echo "blacklist psb_gfx" | sudo tee -a /etc/modprobe.d/blacklist.conf

about reinstalling Oneiric I would not suggest you, not strictly necessary, if both psb_gfx and/or emgd work like you said. the errors you experienced will remain also in a new install, i get them as well. :)

---

### Post by lucazade on 2011-08-05
this is a little script I made to automatize emgd 1.8 installation process in Oneiric and to add necessary work arounds and fixes
(suspend and backlight still have issues btw, look at other thread)


```
#!/bin/bash
# emgd 1.8 installation script for oneiric


# add repository, install drivers and related tools, setup emgd xorg.conf via auto tool
add-apt-repository ppa:gma500/emgd-1.8
apt-get update
apt-get install xorg-emgd emgd-dkms emgdbl emgdui mplayer emgd-xorg-conf
emgd-xorg-conf


# fix plymouth splash screen and virtual terminals resolution
echo "echo insmod 915resolution
echo 915resolution 58 1366 768 32" | tee /etc/grub.d/01_915resolution
chmod +x /etc/grub.d/01_915resolution

echo "GRUB_GFXMODE=1366x768x32
GRUB_GFXPAYLOAD_LINUX=1366x768x32" | tee -a /etc/default/grub


# fix backlight hotkeys support
echo "emgdbl" | tee -a /etc/modules
sed -i 's/GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="acpi_backlight=vendor"/g' /etc/default/grub

echo "#blacklist poulsbo
blacklist acer_wmi" | tee -a /etc/modprobe.d/blacklist.conf


# fix for suspend
mv /usr/lib/pm-utils/sleep.d/99video /usr/lib/pm-utils/99video


# fix for emgd control panel
wget http://dl.dropbox.com/u/1338581/gma500/resources/emgdgui -O /usr/bin/emgdui


# finalize installation
update-grub
update-initramfs -u
```

save as "emgd-oneiric.sh"
and execute as "sudo sh emgd-oneiric.sh"

---

### Post by fjgaude on 2011-08-05
Yes, yes... I did everything you suggested. Here's the story: in 3D still have no tray icons but moving the mouse over the areas I get drop-down menus... no launcher. Seems slow, didn't try sleep. Shading shows at the bottom of the top tray, like compiz is loaded. <smile>

Now log into 2D everything works, even suspend! Speedy! Can relocate the launcher icons. So the latest Unity updates are there.

Will keep updating as time goes by.

As always, thank you!

---

### Post by lucazade on 2011-08-05
> **fjgaude said:**
> Yes, yes... I did everything you suggested. Here's the story: in 3D still have no tray icons but moving the mouse over the areas I get drop-down menus... no launcher. Seems slow, didn't try sleep. Shading shows at the bottom of the top tray, like compiz is loaded. <smile>

Now log into 2D everything works, even suspend! Speedy! Can relocate the launcher icons. So the latest Unity updates are there.

Will keep updating as time goes by.

As always, thank you!

wait wait wait!
does suspend work for you?!!?

so it is related to acer751h only... which is your netbook, dell mini 10n?

could you please paste your dmesg ? :)

---

### Post by fjgaude on 2011-08-05
dmsg.conf

```
# dbus - D-Bus system message bus
#
# The D-Bus system message bus allows system daemons and user applications
# to communicate.

description	"D-Bus system message bus"

start on local-filesystems
stop on deconfiguring-networking

expect fork
respawn

pre-start script
    mkdir -p /var/run/dbus
    chown messagebus:messagebus /var/run/dbus

    exec dbus-uuidgen --ensure
end script

exec dbus-daemon --system --fork --activation=upstart

post-start exec kill -USR1 1
```
###

Dmesg link

```
#!/bin/sh -e
# upstart-job
#
# Symlink target for initscripts that have been converted to Upstart.

set -e

INITSCRIPT="$(basename "$0")"
JOB="${INITSCRIPT%.sh}"

if [ "$JOB" = "upstart-job" ]; then
    if [ -z "$1" ]; then
        echo "Usage: upstart-job JOB COMMAND" 1>&2
	exit 1
    fi

    JOB="$1"
    INITSCRIPT="$1"
    shift
else
    if [ -z "$1" ]; then
        echo "Usage: $0 COMMAND" 1>&2
	exit 1
    fi
fi

COMMAND="$1"
shift


if [ -z "$DPKG_MAINTSCRIPT_PACKAGE" ]; then
	ECHO=echo
else
	ECHO=:
fi

$ECHO "Rather than invoking init scripts through /etc/init.d, use the service(8)"
$ECHO "utility, e.g. service $INITSCRIPT $COMMAND"

case $COMMAND in
status)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    $COMMAND "$JOB"
    ;;
start|stop)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    if status "$JOB" 2>/dev/null | grep -q ' start/'; then
        RUNNING=1
    fi
    if [ -z "$RUNNING" ] && [ "$COMMAND" = "stop" ]; then
        exit 0
    elif [ -n "$RUNNING" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    fi
    $COMMAND "$JOB"
    ;;
restart)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the stop(8) and then start(8) utilities,"
    $ECHO "e.g. stop $JOB ; start $JOB. The restart(8) utility is also available."
    if status "$JOB" 2>/dev/null | grep -q ' start/'; then
        RUNNING=1
    fi
    if [ -n "$RUNNING" ] ; then
        stop "$JOB"
    fi
    start "$JOB"
    ;;
reload|force-reload)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the reload(8) utility, e.g. reload $JOB"
    reload "$JOB"
    ;;
*)
    $ECHO
    $ECHO "The script you are attempting to invoke has been converted to an Upstart" 1>&2
    $ECHO "job, but $COMMAND is not supported for Upstart jobs." 1>&2
    exit 1
esac
```
###

Not sure what you wanted.

If these are no help tell me exactly the full file path.

---

### Post by fjgaude on 2011-08-05
```
# dmesg - save kernel messages
#
# This task saves the initial kernel message log.

description	"save kernel messages"

start on runlevel [2345]

task
script
    savelog -q -p -c 5 /var/log/dmesg
    dmesg -s 524288 > /var/log/dmesg
    chgrp adm /var/log/dmesg
end script
```

---

### Post by fjgaude on 2011-08-05
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-7-generic (buildd@vernadsky) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-5ubuntu2) ) #9-Ubuntu SMP Fri Jul 29 21:24:57 UTC 2011 (Ubuntu 3.0.0-7.9-generic 3.0.0)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 0000000000097000 (usable)
[    0.000000]  BIOS-e820: 0000000000097000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f6b0000 (usable)
[    0.000000]  BIOS-e820: 000000003f6b0000 - 000000003f6c0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6c0000 - 000000003f6c3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f6c3000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection cannot be enabled in hardware: non-PAE kernel!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI present.
[    0.000000] DMI: Dell Inc. Inspiron 1010   /0R990K, BIOS A07 07/23/2009
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x3f6b0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask 0C0000000 write-back
[    0.000000]   1 base 03F700000 mask 0FFF00000 uncachable
[    0.000000]   2 base 03F800000 mask 0FF800000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] total RAM covered: 1015M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K 	chunk_size: 16M 	num_reg: 3  	lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 1GB, type WB
[    0.000000] reg 1, base: 1015MB, range: 1MB, type UC
[    0.000000] reg 2, base: 1016MB, range: 8MB, type UC
[    0.000000] found SMP MP-table at [c00f7dd0] f7dd0
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c0093000] 93000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 2ec60000 - 2f944000
[    0.000000] ACPI: RSDP 000f7d40 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 3f6bb184 00074 (v01 DELL    CL09    06040000  LTP 00000000)
[    0.000000] ACPI: FACP 3f6bfbca 000F4 (v03 DELL   M09      06040000 INTC 00000032)
[    0.000000] ACPI: DSDT 3f6bc06f 03AE7 (v01 DELL    M09     06040000 INTL 20060608)
[    0.000000] ACPI: FACS 3f6c2fc0 00040
[    0.000000] ACPI: HPET 3f6bfcbe 00038 (v01 DELL   M09      06040000 INTC 00000032)
[    0.000000] ACPI: MCFG 3f6bfcf6 0003C (v01 DELL   M09      06040000 INTC 00000032)
[    0.000000] ACPI: TCPA 3f6bfd32 00032 (v01 PTLTD  CALISTGA 06040000  PTL 00000001)
[    0.000000] ACPI: TMOR 3f6bfd64 00026 (v01 DELL   M09      06040000 PTL  00000003)
[    0.000000] ACPI: OSFR 3f6bfd8a 00070 (v01 DELL   M09      06040000 ASL  00000061)
[    0.000000] ACPI: APIC 3f6bfdfa 00068 (v01 DELL   M09      06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 3f6bfe62 00028 (v01 DELL   M09      06040000  LTP 00000001)
[    0.000000] ACPI: SLIC 3f6bfe8a 00176 (v01 DELL    CL09    06040000  LTP 00000000)
[    0.000000] ACPI: SSDT 3f6bb1f8 004DC (v02  DELL     CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 126MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0003f6b0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x00000097
[    0.000000]     0: 0x00000100 -> 0x0003f6b0
[    0.000000] On node 0 totalpages: 259639
[    0.000000] free_area_init_node: node 0, pgdat c17af240, node_mem_map f700d200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3943 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 254 pages used for memmap
[    0.000000]   HighMem zone: 32180 pages, LIFO batch:7
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 0000000000097000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[    0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 40000000:a0000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 12 pages/cpu @f6c00000 s26240 r0 d22912 u2097152
[    0.000000] pcpu-alloc: s26240 r0 d22912 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 257609
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-7-generic root=UUID=6ae204c2-0c3a-4298-8a5a-40b23368c625 ro acpi_backlight=vendor quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4155904 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0003f6b0)
[    0.000000] Memory: 1002716k/1039040k available (5326k kernel code, 35840k reserved, 2584k data, 696k init, 129736k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc17ba000 - 0xc1868000   ( 696 kB)
[    0.000000]       .data : 0xc1533bc4 - 0xc17b9e40   (2584 kB)
[    0.000000]       .text : 0xc1000000 - 0xc1533bc4   (5326 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f6408000 soft=f640a000
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1330.034 MHz processor.
[    0.008007] Calibrating delay loop (skipped), value calculated using timer frequency.. 2660.06 BogoMIPS (lpj=5320136)
[    0.008021] pid_max: default: 32768 minimum: 301
[    0.008086] Security Framework initialized
[    0.008131] AppArmor: AppArmor initialized
[    0.008137] Yama: becoming mindful.
[    0.008287] Mount-cache hash table entries: 512
[    0.008634] Initializing cgroup subsys cpuacct
[    0.008653] Initializing cgroup subsys memory
[    0.008678] Initializing cgroup subsys devices
[    0.008685] Initializing cgroup subsys freezer
[    0.008692] Initializing cgroup subsys net_cls
[    0.008699] Initializing cgroup subsys blkio
[    0.008722] Initializing cgroup subsys perf_event
[    0.008796] CPU: Physical Processor ID: 0
[    0.008802] CPU: Processor Core ID: 0
[    0.008811] mce: CPU supports 5 MCE banks
[    0.008833] CPU0: Thermal monitoring enabled (TM1)
[    0.008844] using mwait in idle threads.
[    0.013250] ACPI: Core revision 20110413
[    0.022723] ftrace: allocating 24983 entries in 49 pages
[    0.024136] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.024481] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066974] CPU0: Intel(R) Atom(TM) CPU Z520   @ 1.33GHz stepping 02
[    0.068003] Performance Events: PEBS fmt0+, Atom events, Intel PMU driver.
[    0.068003] ... version:                3
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] CPU 1 irqstacks, hard=f64a4000 soft=f64a6000
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 93000
[    0.012000] Initializing CPU#1
[    0.160047] Brought up 2 CPUs
[    0.160057] Total of 2 processors activated (5320.01 BogoMIPS).
[    0.160627] devtmpfs: initialized
[    0.160627] PM: Registering ACPI NVS region at 3f6c0000 (12288 bytes)
[    0.165172] print_constraints: dummy: 
[    0.165209] Time: 17:42:16  Date: 08/05/11
[    0.165337] NET: Registered protocol family 16
[    0.165468] Trying to unpack rootfs image as initramfs...
[    0.165974] EISA bus registered
[    0.166009] ACPI: bus type pci registered
[    0.166261] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.166276] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.166284] PCI: Using MMCONFIG for extended config space
[    0.166292] PCI: Using configuration type 1 for base access
[    0.171744] bio: create slab <bio-0> at 0
[    0.175805] ACPI: EC: Look up EC in DSDT
[    0.184511] ACPI: SSDT 3f6bbd98 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.185480] ACPI: Dynamic OEM Table Load:
[    0.185495] ACPI: SSDT   (null) 00203 (v02  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.186094] ACPI: SSDT 3f6bb6d4 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.186989] ACPI: Dynamic OEM Table Load:
[    0.187004] ACPI: SSDT   (null) 0063F (v02  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.188091] ACPI: SSDT 3f6bbf9b 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.189042] ACPI: Dynamic OEM Table Load:
[    0.189057] ACPI: SSDT   (null) 000D4 (v02  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.189496] ACPI: SSDT 3f6bbd13 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.190398] ACPI: Dynamic OEM Table Load:
[    0.190412] ACPI: SSDT   (null) 00085 (v02  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.192233] ACPI: Interpreter enabled
[    0.192250] ACPI: (supports S0 S3 S4 S5)
[    0.192325] ACPI: Using IOAPIC for interrupt routing
[    0.250067] ACPI: EC: GPE = 0xd, I/O: command/status = 0x66, data = 0x62
[    0.250642] ACPI: No dock devices found.
[    0.250652] HEST: Table not found.
[    0.250665] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.251290] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.252478] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.252492] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.252504] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.252516] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000dffff]
[    0.252527] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000effff]
[    0.252538] pci_root PNP0A08:00: host bridge window [mem 0x000f0000-0x000fffff]
[    0.252550] pci_root PNP0A08:00: host bridge window [mem 0x3f800000-0x3fffffff]
[    0.252561] pci_root PNP0A08:00: host bridge window [mem 0x40000000-0xfebfffff]
[    0.252584] pci_root PNP0A08:00: address space collision: host bridge window [mem 0x000c0000-0x000dffff] conflicts with reserved [mem 0x000d0000-0x000fffff]
[    0.252627] pci 0000:00:00.0: [8086:8100] type 0 class 0x000600
[    0.252742] pci 0000:00:02.0: [8086:8108] type 0 class 0x000300
[    0.252779] pci 0000:00:02.0: reg 10: [mem 0xd8100000-0xd817ffff]
[    0.252801] pci 0000:00:02.0: reg 14: [io  0x1800-0x1807]
[    0.252822] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xd7ffffff]
[    0.252843] pci 0000:00:02.0: reg 1c: [mem 0xd8380000-0xd839ffff]
[    0.252995] pci 0000:00:1b.0: [8086:811b] type 0 class 0x000403
[    0.253029] pci 0000:00:1b.0: reg 10: [mem 0xd83a0000-0xd83a3fff 64bit]
[    0.253119] pci 0000:00:1b.0: PME# supported from D0 D3hot
[    0.253133] pci 0000:00:1b.0: PME# disabled
[    0.253177] pci 0000:00:1c.0: [8086:8110] type 1 class 0x000604
[    0.253267] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.253280] pci 0000:00:1c.0: PME# disabled
[    0.253330] pci 0000:00:1c.1: [8086:8112] type 1 class 0x000604
[    0.253425] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.253441] pci 0000:00:1c.1: PME# disabled
[    0.253497] pci 0000:00:1d.0: [8086:8114] type 0 class 0x000c03
[    0.253563] pci 0000:00:1d.0: reg 20: [io  0x1820-0x183f]
[    0.253625] pci 0000:00:1d.1: [8086:8115] type 0 class 0x000c03
[    0.253691] pci 0000:00:1d.1: reg 20: [io  0x1840-0x185f]
[    0.253749] pci 0000:00:1d.2: [8086:8116] type 0 class 0x000c03
[    0.253815] pci 0000:00:1d.2: reg 20: [io  0x1860-0x187f]
[    0.253895] pci 0000:00:1d.7: [8086:8117] type 0 class 0x000c03
[    0.253938] pci 0000:00:1d.7: reg 10: [mem 0xd83a4000-0xd83a43ff]
[    0.254073] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.254087] pci 0000:00:1d.7: PME# disabled
[    0.254129] pci 0000:00:1f.0: [8086:8119] type 0 class 0x000601
[    0.254244] pci 0000:00:1f.1: [8086:811a] type 0 class 0x000101
[    0.254309] pci 0000:00:1f.1: reg 20: [io  0x1810-0x181f]
[    0.254454] pci 0000:02:00.0: [10ec:8136] type 0 class 0x000200
[    0.254492] pci 0000:02:00.0: reg 10: [io  0x2000-0x20ff]
[    0.254543] pci 0000:02:00.0: reg 18: [mem 0xd8410000-0xd8410fff 64bit pref]
[    0.254578] pci 0000:02:00.0: reg 20: [mem 0xd8400000-0xd840ffff 64bit pref]
[    0.254604] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.254669] pci 0000:02:00.0: supports D1 D2
[    0.254678] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.254692] pci 0000:02:00.0: PME# disabled
[    0.260094] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.260112] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.260127] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.260142] pci 0000:00:1c.0:   bridge window [mem 0xd8400000-0xd84fffff pref]
[    0.260268] pci 0000:03:00.0: [14e4:4315] type 0 class 0x000280
[    0.260314] pci 0000:03:00.0: reg 10: [mem 0xd8000000-0xd8003fff 64bit]
[    0.260457] pci 0000:03:00.0: supports D1 D2
[    0.260467] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.260481] pci 0000:03:00.0: PME# disabled
[    0.268111] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.268128] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.268145] pci 0000:00:1c.1:   bridge window [mem 0xd8000000-0xd80fffff]
[    0.268159] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.268191] pci_bus 0000:00: on NUMA node 0
[    0.268213] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.268731] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.268949] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.269319]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.269335]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.269344] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.280288] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 5 6 *7 10 12 14 15)
[    0.280526] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 5 6 7 *11 12 14 15)
[    0.280739] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 5 6 7 10 12 14 15)
[    0.280951] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 *5 6 7 11 12 14 15)
[    0.281162] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 5 6 7 10 12 14 15) *0, disabled.
[    0.281410] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 5 6 7 *11 12 14 15)
[    0.281661] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 5 6 7 *10 12 14 15)
[    0.281893] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 5 6 7 11 12 14 15) *10
[    0.282321] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.282351] vgaarb: loaded
[    0.282357] vgaarb: bridge control possible 0000:00:02.0
[    0.283474] SCSI subsystem initialized
[    0.283757] libata version 3.00 loaded.
[    0.283989] usbcore: registered new interface driver usbfs
[    0.284083] usbcore: registered new interface driver hub
[    0.284223] usbcore: registered new device driver usb
[    0.284681] PCI: Using ACPI for IRQ routing
[    0.294259] PCI: pci_cache_line_size set to 64 bytes
[    0.294394] reserve RAM buffer: 0000000000097000 - 000000000009ffff 
[    0.294406] reserve RAM buffer: 000000003f6b0000 - 000000003fffffff 
[    0.294886] NetLabel: Initializing
[    0.294897] NetLabel:  domain hash size = 128
[    0.294903] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.294944] NetLabel:  unlabeled traffic allowed by default
[    0.295158] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.295173] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.295191] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.301147] Switching to clocksource hpet
[    0.302700] Switched to NOHz mode on CPU #0
[    0.302805] Switched to NOHz mode on CPU #1
[    0.326590] AppArmor: AppArmor Filesystem Enabled
[    0.326700] pnp: PnP ACPI init
[    0.326765] ACPI: bus type pnp registered
[    0.327369] pnp 00:00: [bus 00-ff]
[    0.327383] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.327393] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.327403] pnp 00:00: [io  0x0d00-0xffff window]
[    0.327414] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.327425] pnp 00:00: [mem 0x000c0000-0x000dffff window]
[    0.327435] pnp 00:00: [mem 0x000e0000-0x000effff window]
[    0.327445] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.327456] pnp 00:00: [mem 0x3f800000-0x3fffffff window]
[    0.327467] pnp 00:00: [mem 0x40000000-0xfebfffff window]
[    0.327487] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.327718] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.327915] pnp 00:01: [mem 0xfd000000-0xfd003fff]
[    0.327928] pnp 00:01: [mem 0xe0000000-0xefffffff]
[    0.327938] pnp 00:01: [mem 0xfed00000-0xfed3ffff]
[    0.327948] pnp 00:01: [mem 0xfed40000-0xfed44fff]
[    0.327957] pnp 00:01: [mem 0xfed45000-0xfed4bfff]
[    0.328188] system 00:01: [mem 0xfd000000-0xfd003fff] has been reserved
[    0.328202] system 00:01: [mem 0xe0000000-0xefffffff] has been reserved
[    0.328215] system 00:01: [mem 0xfed00000-0xfed3ffff] could not be reserved
[    0.328228] system 00:01: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.328240] system 00:01: [mem 0xfed45000-0xfed4bfff] has been reserved
[    0.328255] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.329052] pnp 00:02: [io  0x0000-0x001f]
[    0.329065] pnp 00:02: [io  0x0081-0x0091]
[    0.329076] pnp 00:02: [io  0x0093-0x009f]
[    0.329085] pnp 00:02: [io  0x00c0-0x00df]
[    0.329095] pnp 00:02: [dma 4]
[    0.329287] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.329337] pnp 00:03: [mem 0xff000000-0xffffffff]
[    0.329493] pnp 00:03: Plug and Play ACPI device, IDs INT0800 (active)
[    0.329642] pnp 00:04: [irq 0 disabled]
[    0.329673] pnp 00:04: [irq 8]
[    0.329683] pnp 00:04: [mem 0xfed00000-0xfed003ff]
[    0.329889] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.329905] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.329959] pnp 00:05: [io  0x00f0]
[    0.329978] pnp 00:05: [irq 13]
[    0.330131] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.330193] pnp 00:06: [io  0x002e-0x002f]
[    0.330204] pnp 00:06: [io  0x004e-0x004f]
[    0.330214] pnp 00:06: [io  0x0061]
[    0.330223] pnp 00:06: [io  0x0063]
[    0.330232] pnp 00:06: [io  0x0065]
[    0.330242] pnp 00:06: [io  0x0067]
[    0.330250] pnp 00:06: [io  0x0070]
[    0.330258] pnp 00:06: [io  0x0080]
[    0.330267] pnp 00:06: [io  0x0092]
[    0.330276] pnp 00:06: [io  0x00b2-0x00b3]
[    0.330285] pnp 00:06: [io  0x0680-0x069f]
[    0.330294] pnp 00:06: [io  0x8080]
[    0.330304] pnp 00:06: [io  0x1000-0x107f]
[    0.330313] pnp 00:06: [io  0x1180-0x11bf]
[    0.330323] pnp 00:06: [io  0x1640-0x164f]
[    0.330333] pnp 00:06: [io  0x0050-0x0052]
[    0.330342] pnp 00:06: [io  0x0068]
[    0.330351] pnp 00:06: [io  0x006c]
[    0.330361] pnp 00:06: [io  0x0074-0x0077]
[    0.330370] pnp 00:06: [io  0x0374-0x0375]
[    0.330379] pnp 00:06: [io  0x03f4-0x03f5]
[    0.330643] system 00:06: [io  0x0680-0x069f] has been reserved
[    0.330657] system 00:06: [io  0x8080] has been reserved
[    0.330669] system 00:06: [io  0x1000-0x107f] has been reserved
[    0.330680] system 00:06: [io  0x1180-0x11bf] has been reserved
[    0.330692] system 00:06: [io  0x1640-0x164f] has been reserved
[    0.330705] system 00:06: [io  0x0374-0x0375] has been reserved
[    0.330717] system 00:06: [io  0x03f4-0x03f5] has been reserved
[    0.330732] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.330859] pnp 00:07: [io  0x0070-0x0073]
[    0.331020] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.348202] pnp 00:08: [io  0x0060]
[    0.348215] pnp 00:08: [io  0x0064]
[    0.348247] pnp 00:08: [irq 1]
[    0.348495] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.348564] pnp 00:09: [irq 12]
[    0.348759] pnp 00:09: Plug and Play ACPI device, IDs SYN0601 SYN0600 SYN0002 PNP0f13 (active)
[    0.348819] pnp: PnP ACPI: found 10 devices
[    0.348827] ACPI: ACPI bus type pnp unregistered
[    0.348838] PnPBIOS: Disabled by ACPI PNP
[    0.391498] PCI: max bus depth: 1 pci_try_num: 2
[    0.391552] pci 0000:00:1c.0: BAR 14: assigned [mem 0x40000000-0x400fffff]
[    0.391570] pci 0000:00:1c.1: BAR 15: assigned [mem 0x40100000-0x402fffff pref]
[    0.391587] pci 0000:00:1c.1: BAR 13: assigned [io  0x3000-0x3fff]
[    0.391603] pci 0000:02:00.0: BAR 6: assigned [mem 0xd8420000-0xd843ffff pref]
[    0.391615] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.391627] pci 0000:00:1c.0:   bridge window [io  0x2000-0x2fff]
[    0.391642] pci 0000:00:1c.0:   bridge window [mem 0x40000000-0x400fffff]
[    0.391656] pci 0000:00:1c.0:   bridge window [mem 0xd8400000-0xd84fffff pref]
[    0.391673] pci 0000:00:1c.1: PCI bridge to [bus 03-03]
[    0.391684] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.391699] pci 0000:00:1c.1:   bridge window [mem 0xd8000000-0xd80fffff]
[    0.391713] pci 0000:00:1c.1:   bridge window [mem 0x40100000-0x402fffff pref]
[    0.391788] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.391807] pci 0000:00:1c.0: setting latency timer to 64
[    0.391846] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.391860] pci 0000:00:1c.1: setting latency timer to 64
[    0.391874] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.391884] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.391895] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.391906] pci_bus 0000:00: resource 7 [mem 0x000e0000-0x000effff]
[    0.391917] pci_bus 0000:00: resource 8 [mem 0x000f0000-0x000fffff]
[    0.391929] pci_bus 0000:00: resource 9 [mem 0x3f800000-0x3fffffff]
[    0.391940] pci_bus 0000:00: resource 10 [mem 0x40000000-0xfebfffff]
[    0.391951] pci_bus 0000:02: resource 0 [io  0x2000-0x2fff]
[    0.391962] pci_bus 0000:02: resource 1 [mem 0x40000000-0x400fffff]
[    0.391973] pci_bus 0000:02: resource 2 [mem 0xd8400000-0xd84fffff pref]
[    0.391984] pci_bus 0000:03: resource 0 [io  0x3000-0x3fff]
[    0.391995] pci_bus 0000:03: resource 1 [mem 0xd8000000-0xd80fffff]
[    0.392047] pci_bus 0000:03: resource 2 [mem 0x40100000-0x402fffff pref]
[    0.392203] NET: Registered protocol family 2
[    0.392441] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.393513] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.395080] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.395833] TCP: Hash tables configured (established 131072 bind 65536)
[    0.395844] TCP reno registered
[    0.395861] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.395899] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.396410] NET: Registered protocol family 1
[    0.396481] pci 0000:00:02.0: Boot video device
[    0.396642] PCI: CLS 64 bytes, default 64
[    0.396656] Simple Boot Flag at 0x36 set to 0x1
[    0.397979] audit: initializing netlink socket (disabled)
[    0.398014] type=2000 audit(1312566136.396:1): initialized
[    0.470217] highmem bounce pool size: 64 pages
[    0.470243] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.485914] VFS: Disk quotas dquot_6.5.2
[    0.486185] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.489363] fuse init (API version 7.16)
[    0.489799] msgmni has been set to 1705
[    0.490882] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.491009] io scheduler noop registered
[    0.491019] io scheduler deadline registered
[    0.491089] io scheduler cfq registered (default)
[    0.491750] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.491873] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.492161] intel_idle: MWAIT substates: 0x3020220
[    0.492185] intel_idle: v0.4 model 0x1C
[    0.492193] intel_idle: lapic_timer_reliable_states 0x2
[    0.492217] Marking TSC unstable due to TSC halts in idle states deeper than C2
[    0.492739] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.493202] ACPI: AC Adapter [ACAD] (on-line)
[    0.493463] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.493532] ACPI: Lid Switch [LID0]
[    0.493707] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.493725] ACPI: Power Button [PWRB]
[    0.493938] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.493954] ACPI: Power Button [PWRF]
[    0.493969] ACPI Error: Could not enable PowerButton event (20110413/evxfevnt-198)
[    0.493986] ACPI Warning: Could not enable fixed event 0x2 (20110413/evxface-197)
[    0.512284] button: probe of LNXPWRBN:00 failed with error -22
[    0.512417] ACPI: acpi_idle yielding to intel_idle
[    0.536621] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.536710] ERST: Table is not found!
[    0.536979] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.537903] isapnp: Scanning for PnP cards...
[    0.894441] isapnp: No Plug & Play device found
[    1.041548] ACPI: Battery Slot [BAT1] (battery present)
[    1.051333] Freeing initrd memory: 13200k freed
[    1.088236] Linux agpgart interface v0.103
[    1.092164] brd: module loaded
[    1.094060] loop: module loaded
[    1.094638] pata_acpi 0000:00:1f.1: setting latency timer to 64
[    1.095800] Fixed MDIO Bus: probed
[    1.095897] PPP generic driver version 2.4.2
[    1.096120] tun: Universal TUN/TAP device driver, 1.6
[    1.096127] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.096386] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.096463] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    1.096504] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.096514] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.096624] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.096688] ehci_hcd 0000:00:1d.7: debug port 1
[    1.100589] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.100632] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xd83a4000
[    1.116076] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.116535] hub 1-0:1.0: USB hub found
[    1.116550] hub 1-0:1.0: 8 ports detected
[    1.116747] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.116788] uhci_hcd: USB Universal Host Controller Interface driver
[    1.116901] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.116918] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.116926] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.117048] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.117112] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001820
[    1.117480] hub 2-0:1.0: USB hub found
[    1.117495] hub 2-0:1.0: 2 ports detected
[    1.117665] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.117681] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.117689] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.117823] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.117882] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840
[    1.118255] hub 3-0:1.0: USB hub found
[    1.118269] hub 3-0:1.0: 2 ports detected
[    1.118434] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.118450] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.118458] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.118587] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.118651] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    1.118996] hub 4-0:1.0: USB hub found
[    1.119009] hub 4-0:1.0: 2 ports detected
[    1.119299] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.141322] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.141350] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.141734] mousedev: PS/2 mouse device common for all mice
[    1.142096] rtc_cmos 00:07: RTC can wake from S4
[    1.142273] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    1.142312] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.142622] device-mapper: uevent: version 1.0.3
[    1.142873] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    1.143107] device-mapper: multipath: version 1.3.0 loaded
[    1.143118] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.143443] EISA: Probing bus 0 at eisa.0
[    1.143451] EISA: Cannot allocate resource for mainboard
[    1.143459] Cannot allocate resource for EISA slot 1
[    1.143466] Cannot allocate resource for EISA slot 2
[    1.143473] Cannot allocate resource for EISA slot 3
[    1.143480] Cannot allocate resource for EISA slot 4
[    1.143486] Cannot allocate resource for EISA slot 5
[    1.143493] Cannot allocate resource for EISA slot 6
[    1.143499] Cannot allocate resource for EISA slot 7
[    1.143506] Cannot allocate resource for EISA slot 8
[    1.143512] EISA: Detected 0 cards.
[    1.143532] cpufreq-nforce2: No nForce2 chipset.
[    1.143782] cpuidle: using governor ladder
[    1.144240] cpuidle: using governor menu
[    1.144247] EFI Variables Facility v0.08 2004-May-17
[    1.145035] TCP cubic registered
[    1.145470] NET: Registered protocol family 10
[    1.147025] NET: Registered protocol family 17
[    1.147083] Registering the dns_resolver key type
[    1.147144] Using IPI No-Shortcut mode
[    1.147498] PM: Hibernation image not present or could not be loaded.
[    1.147530] registered taskstats version 1
[    1.150887]   Magic number: 7:873:743
[    1.151036] rtc_cmos 00:07: setting system clock to 2011-08-05 17:42:17 UTC (1312566137)
[    1.152208] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.152215] EDD information not available.
[    1.152505] Freeing unused kernel memory: 696k freed
[    1.153148] Write protecting the kernel text: 5328k
[    1.153257] Write protecting the kernel read-only data: 2180k
[    1.163483] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.208845] udevd[62]: starting version 172
[    1.473494] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.473569] r8169 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.473655] r8169 0000:02:00.0: setting latency timer to 64
[    1.473767] r8169 0000:02:00.0: irq 40 for MSI/MSI-X
[    1.475720] r8169 0000:02:00.0: eth0: RTL8102e at 0xf800e000, 00:24:e8:bb:dc:c5, XID 04c00000 IRQ 40
[    1.484105] usb 1-6: new high speed USB device number 3 using ehci_hcd
[    1.497968] pata_sch 0000:00:1f.1: version 0.2
[    1.498077] pata_sch 0000:00:1f.1: setting latency timer to 64
[    1.514311] scsi0 : pata_sch
[    1.517606] scsi1 : pata_sch
[    1.518758] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[    1.518772] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[    1.682495] ata1.00: ATA-8: SAMSUNG HM160HI, HH100-14, max UDMA7
[    1.682516] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.698656] ata1.00: configured for UDMA/100
[    1.699302] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM160HI  HH10 PQ: 0 ANSI: 5
[    1.699848] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.699997] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.700200] sd 0:0:0:0: [sda] Write Protect is off
[    1.700214] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.700498] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.767351]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7 >
[    1.769528] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.776307] usb 1-7: new high speed USB device number 4 using ehci_hcd
[    1.934794] usbcore: registered new interface driver uas
[    1.937827] Initializing USB Mass Storage driver...
[    1.938423] usbcore: registered new interface driver usb-storage
[    1.938434] USB Mass Storage support registered.
[    1.942084] scsi2 : usb-storage 1-7:1.0
[    1.942478] usbcore: registered new interface driver ums-realtek
[    2.168142] usb 3-2: new low speed USB device number 2 using uhci_hcd
[    2.405524] input: 2.4G Wireless Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-2/3-2:1.0/input/input4
[    2.406600] generic-usb 0003:040B:2011.0001: input,hiddev0,hidraw0: USB HID v1.10 Mouse [2.4G Wireless Mouse] on usb-0000:00:1d.1-2/input0
[    2.406681] usbcore: registered new interface driver usbhid
[    2.406690] usbhid: USB HID core driver
[    2.662254] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.943409] scsi 2:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    3.009057] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.013417] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[   17.758856] udevd[246]: starting version 172
[   17.837875] Adding 1031164k swap on /dev/sda7.  Priority:-1 extents:1 across:1031164k 
[   17.851896] lp: driver loaded but no devices found
[   17.866005] ------------[ cut here ]------------
[   17.866034] WARNING: at /build/buildd/linux-3.0.0/drivers/video/backlight/backlight.c:314 backlight_device_register+0x193/0x1c0()
[   17.866046] Hardware name: Inspiron 1010   
[   17.866053] emgd_psb: invalid backlight type
[   17.866060] Modules linked in: emgdbl(+) lp parport usbhid hid ums_realtek usb_storage uas pata_sch r8169
[   17.866099] Pid: 257, comm: modprobe Not tainted 3.0.0-7-generic #9-Ubuntu
[   17.866110] Call Trace:
[   17.866131]  [<c1047832>] warn_slowpath_common+0x72/0xa0
[   17.866147]  [<c12c73c3>] ? backlight_device_register+0x193/0x1c0
[   17.866161]  [<c12c73c3>] ? backlight_device_register+0x193/0x1c0
[   17.866175]  [<c1047903>] warn_slowpath_fmt+0x33/0x40
[   17.866189]  [<c12c73c3>] backlight_device_register+0x193/0x1c0
[   17.866208]  [<f801815a>] emgdbl_probe+0x6a/0xac [emgdbl]
[   17.866225]  [<c133ca41>] platform_drv_probe+0x11/0x20
[   17.866240]  [<c133b5dd>] really_probe+0x4d/0x150
[   17.866255]  [<c1343a49>] ? pm_runtime_barrier+0x49/0xb0
[   17.866269]  [<c133b81a>] driver_probe_device+0x3a/0x60
[   17.866283]  [<c133b921>] __device_attach+0x41/0x50
[   17.866295]  [<c133b8e0>] ? __driver_attach+0xa0/0xa0
[   17.866307]  [<c133a6a9>] bus_for_each_drv+0x49/0x70
[   17.866319]  [<c133b7aa>] device_attach+0x8a/0xa0
[   17.866331]  [<c133b8e0>] ? __driver_attach+0xa0/0xa0
[   17.866344]  [<c133aed5>] bus_probe_device+0x25/0x40
[   17.866356]  [<c13394ec>] device_add+0x28c/0x380
[   17.866370]  [<c1280ba3>] ? kvasprintf+0x43/0x60
[   17.866384]  [<c1276e5a>] ? kobject_set_name_vargs+0x4a/0x60
[   17.866399]  [<c1276e5a>] ? kobject_set_name_vargs+0x4a/0x60
[   17.866413]  [<c133d157>] platform_device_add+0xd7/0x1b0
[   17.866428]  [<c133d4fa>] platform_device_register_resndata+0x5a/0x80
[   17.866445]  [<f8035045>] emgdbl_init+0x45/0x1000 [emgdbl]
[   17.866461]  [<c1001125>] do_one_initcall+0x35/0x170
[   17.866475]  [<f8035000>] ? 0xf8034fff
[   17.866491]  [<c108262d>] sys_init_module+0xad/0x210
[   17.866506]  [<c11253b5>] ? sys_close+0x75/0xd0
[   17.866522]  [<c152bd34>] syscall_call+0x7/0xb
[   17.866532] ---[ end trace 91ee092a63660365 ]---
[   18.075068] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[   18.388720] init: plymouth-log main process (378) terminated with status 1
[   18.581621] type=1400 audit(1312566154.927:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=414 comm="apparmor_parser"
[   18.593712] init: plymouth-upstart-bridge main process (406) terminated with status 1
[   18.594005] type=1400 audit(1312566154.939:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=414 comm="apparmor_parser"
[   18.595017] type=1400 audit(1312566154.939:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=414 comm="apparmor_parser"
[   19.071674] r8169 0000:02:00.0: eth0: link down
[   19.072689] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.272072] Linux video capture interface: v2.00
[   19.274846] uvcvideo: Found UVC 1.00 device Integrated Webcam (064e:a129)
[   19.318963] input: Integrated Webcam as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input5
[   19.319665] usbcore: registered new interface driver uvcvideo
[   19.319677] USB Video Class driver (v1.1.0)
[   19.417133] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.417253] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.495276] hda_codec: ALC269: BIOS auto-probing.
[   19.508950] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   19.540817] input: HDA Intel MID HDMI/DP as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   19.541542] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   19.542250] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   19.588507] psmouse serio1: ID: 10 00 64
[   19.772379] elantech: assuming hardware version 2, firmware version 2.8.1
[   19.786348] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   19.815428] compal_laptop: Identified laptop model 'Dell Mini 10'
[   19.827075] compal_laptop: Driver 0.2.7 successfully loaded
[   19.830812] dell_laptop: Blacklisted hardware detected - not enabling rfkill
[   19.846833] elantech: Synaptics capabilities query result 0x08, 0x13, 0x0d.
[   20.062862] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input9
[   20.246434] type=1400 audit(1312566156.591:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=650 comm="apparmor_parser"
[   20.248152] type=1400 audit(1312566156.591:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=650 comm="apparmor_parser"
[   20.249704] type=1400 audit(1312566156.595:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=650 comm="apparmor_parser"
[   20.287579] type=1400 audit(1312566156.631:8): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=651 comm="apparmor_parser"
[   20.300838] type=1400 audit(1312566156.647:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=654 comm="apparmor_parser"
[   20.302594] type=1400 audit(1312566156.647:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=654 comm="apparmor_parser"
[   20.318265] type=1400 audit(1312566156.663:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=651 comm="apparmor_parser"
[   21.220042] init: plymouth-stop pre-start process (802) terminated with status 1
[   21.232803] init: udev-fallback-graphics main process (797) terminated with status 1
[   21.271871] ppdev: user-space parallel port driver

```

Yes,I have a Dell mini 10n with 1366x768 screen. Works good.
'

---

### Post by cariboo on 2011-08-05
If you type:

```
dmesg
```

in a terminal, you'll get a listing of the boot process. To create a text file use the following command:

```
dmesg > dmesg.txt
```

This is just the last 10 lines of my dmesg, your's should look similar, except a lot longer :)

> dmesg | tail -n10
[   17.200420] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card1/input9
[   17.336032] init: plymouth-stop pre-start process (1182) terminated with status 1
[   17.352435] ppdev: user-space parallel port driver
[   17.360850] init: udev-fallback-graphics main process (1180) terminated with status 1
[   17.372705] init: plymouth-splash main process (1211) terminated with status 1
[   19.527240] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   19.718332] EXT4-fs (sda3): re-mounted. Opts: commit=0
[   22.657786] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   26.410029] eth0: no IPv6 routers present
[  127.846289] exe (1894): /proc/1894/oom_adj is deprecated, please use /proc/1894/oom_score_adj instead.


---

### Post by fjgaude on 2011-08-05
Thanks,man!

I think the dmesg.txt file is attached.

---

### Post by lucazade on 2011-08-05
@fjgaude

/var/log/dmesg is the correct path, anyway you already attached it.
I'll look it in depth to figure out differences.

could you paste also
/var/log/pm-suspend.log
/var/log/pm-powersave.log 

and the output of:
lsmod > lsmod.txt
(this will paste the output in a .txt file so take the content!)

@cariboo907
thanks for support! 


maybe it is some different kernel module employed in acer and not correctly unloaded when suspending, or maybe acpi is not working on my machine.
fixing suspend is always a mess :)

---

### Post by fjgaude on 2011-08-05
```
Initial commandline parameters: 
Fri Aug  5 10:13:06 PDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux cutie 3.0.0-7-generic #9-Ubuntu SMP Fri Jul 29 21:24:57 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
emgd                  457785  5 
drm_kms_helper         32889  1 emgd
drm                   192017  7 emgd,drm_kms_helper
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13519  0 
compal_laptop          19315  0 
sch_gpio               12960  0 
i2c_isch               12662  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14098  1 dell_laptop
psmouse                73636  0 
serio_raw              12990  0 
soundcore              12600  1 snd
lpc_sch                12653  0 
video                  18908  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
emgdbl                 12673  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
pata_sch               12703  2 
r8169                  43104  0 
             total       used       free     shared    buffers     cached
Mem:       1016612     541396     475216          0      34888     249656
-/+ buffers/cache:     256852     759760
Swap:      1031164          0    1031164

[code]/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
No quirk database entry for this system, using default.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Aug  5 10:13:10 PDT 2011: performing suspend
Fri Aug  5 10:13:22 PDT 2011: Awake.
Fri Aug  5 10:13:22 PDT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
Saving last known working quirks: --quirk-vbe-post --quirk-dpms-on 
                            --quirk-dpms-suspend --quirk-vbestate-restore
			    --quirk-vbemode-restore --quirk-vga-mode-3

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Aug  5 10:13:25 PDT 2011: Finished.
Initial commandline parameters: 
Fri Aug  5 10:33:02 PDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux cutie 3.0.0-7-generic #9-Ubuntu SMP Fri Jul 29 21:24:57 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
emgd                  457785  5 
drm_kms_helper         32889  1 emgd
drm                   192017  7 emgd,drm_kms_helper
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13519  0 
compal_laptop          19315  0 
sch_gpio               12960  0 
i2c_isch               12662  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14098  1 dell_laptop
psmouse                73636  0 
serio_raw              12990  0 
soundcore              12600  1 snd
lpc_sch                12653  0 
video                  18908  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
emgdbl                 12673  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
pata_sch               12703  3 
r8169                  43104  0 
             total       used       free     shared    buffers     cached
Mem:       1016612     586440     430172          0      35376     278900
-/+ buffers/cache:     272164     744448
Swap:      1031164      19176    1011988

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Using last known working set of quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Aug  5 10:33:05 PDT 2011: performing suspend
Fri Aug  5 10:33:24 PDT 2011: Awake.
Fri Aug  5 10:33:24 PDT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Aug  5 10:33:27 PDT 2011: Finished.
Initial commandline parameters: 
Fri Aug  5 11:24:48 PDT 2011: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux cutie 3.0.0-7-generic #9-Ubuntu SMP Fri Jul 29 21:24:57 UTC 2011 i686 i686 i386 GNU/Linux
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
emgd                  457785  5 
drm_kms_helper         32889  1 emgd
drm                   192017  7 emgd,drm_kms_helper
parport_pc             32114  0 
ppdev                  12849  0 
sch_gpio               12960  0 
i2c_isch               12662  0 
dell_laptop            13519  0 
compal_laptop          19315  0 
dcdbas                 14098  1 dell_laptop
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
joydev                 17393  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
psmouse                73636  0 
snd_seq_midi           13132  0 
serio_raw              12990  0 
snd_rawmidi            25241  1 snd_seq_midi
lpc_sch                12653  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
binfmt_misc            17292  1 
video                  18908  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
emgdbl                 12673  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ums_realtek            13096  0 
usb_storage            44173  1 ums_realtek
uas                    17699  0 
pata_sch               12703  2 
r8169                  43104  0 
             total       used       free     shared    buffers     cached
Mem:       1016612     782132     234480          0      54476     340664
-/+ buffers/cache:     386992     629620
Swap:      1031164          0    1031164

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Using last known working set of quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Fri Aug  5 11:24:52 PDT 2011: performing suspend
Fri Aug  5 11:32:48 PDT 2011: Awake.
Fri Aug  5 11:32:48 PDT 2011: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/49bluetooth resume suspend:

/usr/lib/pm-utils/sleep.d/49bluetooth resume suspend: not applicable.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend:
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> Welcome to PulseAudio! Use "help" for usage information.
>>> >>> 
/usr/lib/pm-utils/sleep.d/01PulseAudio resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Fri Aug  5 11:32:51 PDT 2011: Finished.
```
###


Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:
start: Job is already running: anacron

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:
start: Job is already running: anacron

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/fc5b0167-f421-40e6-b38f-48bce323cc09 to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.
Setting journal commit time for /media/fc5b0167-f421-40e6-b38f-48bce323cc09 to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.
Setting readahead for /dev/sda3 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.
Running hook /usr/lib/pm-utils/power.d/95hdparm-apm false:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/power.d/95hdparm-apm false: success.
Running hook /usr/lib/pm-utils/power.d/anacron false:

/usr/lib/pm-utils/power.d/anacron false: success.
Running hook /usr/lib/pm-utils/power.d/disable_wol false:

/usr/lib/pm-utils/power.d/disable_wol false: not applicable.
Running hook /usr/lib/pm-utils/power.d/hal-cd-polling false:

/usr/lib/pm-utils/power.d/hal-cd-polling false: not applicable.
Running hook /usr/lib/pm-utils/power.d/intel-audio-powersave false:
Setting power savings for snd_hda_intel to 0...Done.

/usr/lib/pm-utils/power.d/intel-audio-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/journal-commit false:
Setting journal commit time for / to 0...Done.

/usr/lib/pm-utils/power.d/journal-commit false: success.
Running hook /usr/lib/pm-utils/power.d/laptop-mode false:
Laptop mode disabled.

/usr/lib/pm-utils/power.d/laptop-mode false: success.
Running hook /usr/lib/pm-utils/power.d/pcie_aspm false:

/usr/lib/pm-utils/power.d/pcie_aspm false: success.
Running hook /usr/lib/pm-utils/power.d/readahead false:
Setting readahead for /dev/sda6 to 256...Done.

/usr/lib/pm-utils/power.d/readahead false: success.
Running hook /usr/lib/pm-utils/power.d/sata_alpm false:

/usr/lib/pm-utils/power.d/sata_alpm false: success.
Running hook /usr/lib/pm-utils/power.d/sched-powersave false:
**sched policy powersave OFF

/usr/lib/pm-utils/power.d/sched-powersave false: success.
Running hook /usr/lib/pm-utils/power.d/wireless false:

/usr/lib/pm-utils/power.d/wireless false: success.
Running hook /usr/lib/pm-utils/power.d/xfs_buffer false:

/usr/lib/pm-utils/power.d/xfs_buffer false: not applicable.[/code]

---

### Post by fjgaude on 2011-08-05
Here's the lsmod file... hope it shows what is different between you and me.

I left the Dell in suspend mode three times now, once for many minutes and it all works, come out of sleep.

---

### Post by computingchap on 2011-08-05
I'm having great trouble with suspend on toshiba sat pro a120 Ubuntu 11.04 32-bit (fan stays on and then everything locks up - have to do cold reboot)

sudo cat /var/log/pm-suspend.log | egrep -i "fail|error" | head ======
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

sudo cat /var/log/pm-powersave.log | egrep -i "fail|error" | head =====
Turning powersave for wlan0 off...Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Failed.

sudo cat /var/log/dmesg | egrep -i "fail|error" | head =======
[   22.867098] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   24.194729] iwl3945 0000:02:00.0: Error setting Tx power (-5).


THIS IS DRIVING ME CRAZY -- I WANT TO BE ABLE TO SUSPEND. Help :)

---

### Post by Starks on 2011-08-05
I feel sorry for Poulsbo owners.

---

### Post by fjgaude on 2011-08-05
> **Starks said:**
> I feel sorry for Poulsbo owners.

Well, it's been interesting... nothing to be sorry about. These netbooks rock. My prime boot is with Ubuntu 10.10 and it works perfectly. Soon it will also with 11.10, because of folks like Luca and Sista, along with Alan Fox, etc.

---

### Post by Starks on 2011-08-05
Do you have 3D?

---

### Post by fjgaude on 2011-08-05
> **Starks said:**
> Do you have 3D?

Sorta, with Oneiric and EMGD... it doesn't fully support Unity but it is close. We'll have to see how the release goes and what Tista and Luca provide. I'm patience.

---

### Post by lucazade on 2011-08-06
@Starks
:) Unfortunately poulsbo owners are not A-Class customers and don't receive (never) a great support from upstream Intel for both Linux and Windows.
Anyway we're are lucky there are a lot of passionate people around the web that put love in it.
For me it is a matter of principle to have it working with every linux release and a great gym where to learn everytime something new.
2D could be enough for me, I use the netbook mostly for web browsing but I imagine for others also the other features are important.

@computingchap
Lucky you, this is a support thread for Intel Gma500 users, you have another graphic card so, maybe, your issue with suspend is probably different.
I suggest you to open another thread.



Tried yesterday to play with suspend and make some confrontation between fjgaude logs and mine and some trials of suspending but without luck.
The bad thing is that I've to remove power cord and battery every time suspend fails and it is really frustating.
I'll try again..

---

### Post by Starks on 2011-08-06
Hopefully Medfield isn't going to be the same mess as Poulsbo was.

---

### Post by fjgaude on 2011-08-06
Luca: "Tried yesterday to play with suspend and make some confrontation between fjgaude logs and mine and some trials of suspending but without luck.
The bad thing is that I've to remove power cord and battery every time suspend fails and it is really frustating.
I'll try again."

No joy, eh? When my netbook didn't suspend or come out of suspension I'd just hold down the power button for 4-seconds and the machine would stop. Yours must not follow the standards.

---

### Post by lucazade on 2011-08-06
> **fjgaude said:**
> 
No joy, eh? When my netbook didn't suspend or come out of suspension I'd just hold down the power button for 4-seconds and the machine would stop. Yours must not follow the standards.

yep, no joy yet.
looking at your and mine logs I haven't found any interesting bits atm.
i'm trying to catch dmesg output to see pm-suspend unloading kernel modules before going to sleep and loading them up at resume, in order to confrontate it with natty's one (which after resuming is available), but it seems hard to get it.

i tried with:
```
watch 'dmesg | tail -10'
```
to print out dmesg to terminal

and 
```
watch 'dmesg >> dmesgdump.log | tail -10'
```
to redirect dmesg continuously to a text file (with a bit of risk because hd should spin down during sleep routine :D)

but both doesn't give me this output i get in natty
```
[   89.333083] PM: Syncing filesystems ... done.
[   89.337257] PM: Preparing system for mem sleep
[   89.837242] Freezing user space processes ... (elapsed 0.01 seconds) done.
[   89.852432] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[   89.868452] PM: Entering mem sleep
[   89.868536] Suspending console(s) (use no_console_suspend to debug)
[   90.012322] PM: suspend of drv:drm dev:card0 complete after 143.195 msecs
[   90.016797] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[   90.017135] sd 0:0:0:0: [sda] Stopping disk
[   90.072984] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[   90.072995] ehci_hcd 0000:00:1d.7: PCI INT D disabled
[   90.073011] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[   90.073018] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[   90.073096] poulsbo 0000:00:02.0: PCI INT A disabled
[   90.177249] HDA Intel 0000:00:1b.0: PCI INT A disabled
[   90.192707] HDA Intel 0000:00:1b.0: power state changed by ACPI to D3
[   90.192730] PM: suspend of drv:HDA Intel dev:0000:00:1b.0 complete after 119.686 msecs
[   90.534588] PM: suspend of drv:sd dev:0:0:0:0 complete after 517.797 msecs
[   90.534696] PM: suspend of drv:scsi dev:target0:0:0 complete after 517.468 msecs
[   90.534867] PM: suspend of drv:scsi dev:host0 complete after 517.296 msecs
[   90.535283] PM: suspend of drv:pata_sch dev:0000:00:1f.1 complete after 462.352 msecs
[   90.535357] PM: suspend of drv: dev:pci0000:00 complete after 462.261 msecs
[   90.535414] PM: suspend of devices complete after 666.314 msecs
[   90.535425] PM: suspend devices took 0.664 seconds
[   90.552429] r8169 0000:02:00.0: PME# enabled
[   90.552485] r8169 0000:02:00.0: wake-up capability enabled by ACPI
[   90.584611] PM: late suspend of devices complete after 49.162 msecs
[   90.584658] ACPI: Preparing to enter system sleep state S3
[   90.585792] PM: Saving platform NVS memory
[   90.585938] Disabling non-boot CPUs ...
[   90.688330] CPU 1 is now offline
[   90.689534] Extended CMOS year: 2000
[   90.689534] Back to C!
[   90.689534] PM: Restoring platform NVS memory
[   90.689534] Extended CMOS year: 2000
[   90.689534] Enabling non-boot CPUs ...
[   90.689534] Booting Node 0 Processor 1 APIC 0x1
[   90.587604] Initializing CPU#1
[   90.784074] Switched to NOHz mode on CPU #1
[   90.784318] CPU1 is up
[   90.784829] ACPI: Waking up from system sleep state S3
[   90.936745] poulsbo 0000:00:02.0: restoring config space at offset 0x1 (was 0x100007, writing 0x100003)
[   90.936800] HDA Intel 0000:00:1b.0: restoring config space at offset 0x4 (was 0xfef00004, writing 0xb0050004)
[   90.936812] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[   90.936825] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[   90.936868] pcieport 0000:00:1c.0: restoring config space at offset 0x9 (was 0x0, writing 0xd010d010)
[   90.936879] pcieport 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0x80308000)
[   90.936890] pcieport 0000:00:1c.0: restoring config space at offset 0x7 (was 0x0, writing 0x2020)
[   90.936905] pcieport 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[   90.936917] pcieport 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[   90.936965] pcieport 0000:00:1c.1: restoring config space at offset 0x9 (was 0x0, writing 0x80508040)
[   90.936976] pcieport 0000:00:1c.1: restoring config space at offset 0x8 (was 0x0, writing 0xd000d000)
[   90.936988] pcieport 0000:00:1c.1: restoring config space at offset 0x7 (was 0x0, writing 0x3030)
[   90.937002] pcieport 0000:00:1c.1: restoring config space at offset 0x3 (was 0x10000, writing 0x10010)
[   90.937015] pcieport 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)
[   90.937063] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x5, writing 0x1)
[   90.937102] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x5, writing 0x1)
[   90.937141] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x5, writing 0x1)
[   90.937200] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[   90.937331] r8169 0000:02:00.0: restoring config space at offset 0x8 (was 0xc, writing 0xd010000c)
[   90.937345] r8169 0000:02:00.0: restoring config space at offset 0x6 (was 0xc, writing 0xd011000c)
[   90.937359] r8169 0000:02:00.0: restoring config space at offset 0x4 (was 0x1, writing 0x2001)
[   90.937371] r8169 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[   90.937385] r8169 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100407)
[   90.937490] ath5k 0000:03:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xd0000004)
[   90.937502] ath5k 0000:03:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[   90.937516] ath5k 0000:03:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[   90.938010] PM: early resume of devices complete after 1.444 msecs
[   90.938262] poulsbo 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   90.938280] poulsbo 0000:00:02.0: setting latency timer to 64
[   90.938524] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   90.938541] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   90.938579] usb usb2: root hub lost power or was reset
[   90.938618] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   90.938634] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   90.938669] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   90.938675] usb usb3: root hub lost power or was reset
[   90.938686] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   90.938754] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   90.938771] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   90.938805] usb usb4: root hub lost power or was reset
[   90.938853] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   90.939168] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[   90.939187] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   90.939234] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   90.939256] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   90.939307] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   90.939375] pata_sch 0000:00:1f.1: setting latency timer to 64
[   90.939463] r8169 0000:02:00.0: wake-up capability disabled by ACPI
[   90.939480] r8169 0000:02:00.0: PME# disabled
[   90.941882] sd 0:0:0:0: [sda] Starting disk
[   91.056410] PM: resume of drv:usb dev:usb3 complete after 116.970 msecs
[   91.056495] PM: resume of drv:hub dev:3-0:1.0 complete after 117.022 msecs
[   91.056608] PM: resume of drv: dev:ep_00 complete after 116.999 msecs
[   91.056619] PM: resume of drv: dev:ep_81 complete after 117.085 msecs
[   91.144485] PM: resume of drv:ac dev:ACPI0003:00 complete after 206.091 msecs
[   91.160704] PM: resume of drv:usb dev:usb2 complete after 221.560 msecs
[   91.160745] PM: resume of drv:hub dev:2-0:1.0 complete after 221.466 msecs
[   91.160774] PM: resume of drv: dev:ep_00 complete after 221.390 msecs
[   91.160852] PM: resume of drv: dev:ep_81 complete after 221.492 msecs
[   91.164269] PM: resume of drv:usb dev:usb4 complete after 224.599 msecs
[   91.164306] PM: resume of drv:hub dev:4-0:1.0 complete after 224.565 msecs
[   91.164332] PM: resume of drv: dev:ep_00 complete after 224.458 msecs
[   91.164350] PM: resume of drv: dev:ep_81 complete after 224.543 msecs
[   91.188310] PM: resume of drv:usb dev:usb1 complete after 249.445 msecs
[   91.188438] PM: resume of drv: dev:ep_00 complete after 249.537 msecs
[   91.188456] PM: resume of drv:hub dev:1-0:1.0 complete after 249.562 msecs
[   91.188554] PM: resume of drv: dev:ep_81 complete after 249.664 msecs
[   91.300310] usb 1-4: reset high speed USB device using ehci_hcd and address 3
[   91.486076] PM: resume of drv:usb dev:1-4 complete after 546.117 msecs
[   91.486162] PM: resume of drv:uvcvideo dev:1-4:1.0 complete after 546.041 msecs
[   91.486280] PM: resume of drv: dev:ep_00 complete after 544.488 msecs
[   91.486318] PM: resume of drv:uvcvideo dev:1-4:1.1 complete after 544.578 msecs
[   91.486357] PM: resume of drv: dev:ep_83 complete after 544.707 msecs
[   91.544313] usb 2-2: reset full speed USB device using uhci_hcd and address 2
[   91.705533] PM: resume of drv:usb dev:2-2 complete after 763.497 msecs
[   91.705623] PM: resume of drv:usbhid dev:2-2:1.0 complete after 763.498 msecs
[   91.705771] PM: resume of drv: dev:ep_00 complete after 763.084 msecs
[   91.705794] PM: resume of drv:usbhid dev:2-2:1.1 complete after 763.426 msecs
[   91.705854] PM: resume of drv: dev:ep_82 complete after 763.408 msecs
[   91.705866] PM: resume of drv:usbhid dev:2-2:1.2 complete after 763.335 msecs
[   91.705914] PM: resume of drv: dev:ep_81 complete after 763.672 msecs
[   91.706015] PM: resume of drv: dev:ep_83 complete after 763.422 msecs
[   91.796310] usb 4-1: reset full speed USB device using uhci_hcd and address 2
[   91.946509] btusb 4-1:1.0: no reset_resume for driver btusb?
[   91.946528] btusb 4-1:1.1: no reset_resume for driver btusb?
[   92.196816] PM: resume of drv:usb dev:4-1 complete after 1254.044 msecs
[   92.196904] PM: resume of drv:usb dev:4-1:1.0 complete after 1254.030 msecs
[   92.196915] PM: resume of drv:usb dev:4-1:1.3 complete after 1253.062 msecs
[   92.196948] PM: resume of drv: dev:ep_00 complete after 1252.997 msecs
[   92.196959] PM: resume of drv:usb dev:4-1:1.1 complete after 1253.624 msecs
[   92.197070] PM: resume of drv: dev:ep_83 complete after 1253.636 msecs
[   92.197081] PM: resume of drv:usb dev:4-1:1.2 complete after 1253.480 msecs
[   92.197098] PM: resume of drv: dev:ep_03 complete after 1253.572 msecs
[   92.197130] PM: resume of drv: dev:ep_84 complete after 1253.454 msecs
[   92.197140] PM: resume of drv: dev:ep_81 complete after 1254.148 msecs
[   92.197156] PM: resume of drv: dev:ep_04 complete after 1253.402 msecs
[   92.197167] PM: resume of drv: dev:ep_82 complete after 1254.062 msecs
[   92.197196] PM: resume of drv: dev:ep_02 complete after 1253.959 msecs
[   93.064704] ata1.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[   93.064717] ata1.00: ACPI cmd ef/03:44:00:00:00:a0 (SET FEATURES) filtered out
[   93.089040] ata1.00: configured for UDMA/100
[   93.114364] PM: resume of drv:sd dev:0:0:0:0 complete after 2172.468 msecs
[   93.114474] PM: resume of drv:scsi_device dev:0:0:0:0 complete after 2172.554 msecs
[   93.114545] PM: resume of drv:scsi_disk dev:0:0:0:0 complete after 1948.284 msecs
[   93.188304] poulsbo 0000:00:02.0: setting latency timer to 64
[   93.211545] PM: resume of devices complete after 2273.362 msecs
[   93.212500] PM: resume devices took 2.276 seconds
[   93.212594] PM: Finishing wakeup.
[   93.212599] Restarting tasks ... done.
[   93.360566] video LNXVIDEO:00: Restoring backlight state
[   94.741235] r8169 0000:02:00.0: eth0: link down
[   94.742130] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   94.757251] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   97.460453] wlan0: authenticate with 00:14:c1:24:7d:4f (try 1)
[   97.461855] wlan0: authenticated
[   97.461970] wlan0: associate with 00:14:c1:24:7d:4f (try 1)
[   97.471639] wlan0: RX AssocResp from 00:14:c1:24:7d:4f (capab=0x431 status=0 aid=1)
[   97.471654] wlan0: associated
[   97.474260] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   97.474477] cfg80211: Calling CRDA for country: NL
[   97.492787] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   97.492805] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.492817] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   97.492830] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.492841] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   97.492854] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.492865] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   97.492878] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.492888] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   97.492902] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.492913] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   97.492926] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.492937] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   97.492950] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.492961] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   97.492975] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.492986] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   97.492998] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.493010] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   97.493024] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.493035] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   97.493048] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.493060] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   97.493073] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.493085] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   97.493099] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   97.493109] cfg80211: Disabling freq 2484 MHz
[   97.493125] cfg80211: Regulatory domain changed to country: NL
[   97.493134] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   97.493147] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   97.493160] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   97.493172] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   97.493185] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   98.520031] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x014f000e
[   99.524089] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x014f000e
[  100.957053] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
[  100.978427] EXT4-fs (sda6): re-mounted. Opts: commit=0
[  107.888243] wlan0: no IPv6 routers present
```

i wonder why I'm not able to see this suspend/resume stuff in oneiric.. arg!
any hints are welcome :)

i could recompile kernel and enable some debug, but it is not funny.
i'll see, still haven't lost hopes.

---

### Post by fjgaude on 2011-08-06
I had mine on suspend overnight and this morning it just popped out, as it should.

I'll go over your log and see if I see anything strange versus mine.

Likely it going to be something in the BIOS and hardware. <ugh>

---

### Post by fjgaude on 2011-08-07
Okay, onto something that might be useful.

On the Dell mini with Oneiric which doesn't have a wireless driver for the built-in STA Broadcom BCM43xx card I have been using hardwire, LAN to the router.

Today I decided to use a USB Asus N13 WiFi 802.11b/g/n to go wireless with the little Dell. It wouldn't suspend with wireless! It did without the wireless active.

I did an update to Oneiric and there were massive changes, ending with no real desktop, just Nautilus, which is going through much fixing. So... lately everything came back to normal. I did notice that with RT2800 kernel driver for the wireless USB the power button on the panel, right, no longer has an item for suspend!

---

### Post by lucazade on 2011-08-08
> **fjgaude said:**
> Okay, onto something that might be useful.

On the Dell mini with Oneiric which doesn't have a wireless driver for the built-in STA Broadcom BCM43xx card I have been using hardwire, LAN to the router.

Today I decided to use a USB Asus N13 WiFi 802.11b/g/n to go wireless with the little Dell. It wouldn't suspend with wireless! It did without the wireless active.

I did an update to Oneiric and there were massive changes, ending with no real desktop, just Nautilus, which is going through much fixing. So... lately everything came back to normal. I did notice that with RT2800 kernel driver for the wireless USB the power button on the panel, right, no longer has an item for suspend!

nice idea, thanks for sharing ;)

tried to blacklist a bunch of modules to replicate your situation but without luck.
Now i'm trying to figure out if is a problem with kernel 3.0.x, acpi or pm-tools.
if you notice something else let me know...

what a pity Oneiric which doesn't have a wireless driver for the built-in STA Broadcom BCM43xx card :S

---

### Post by fjgaude on 2011-08-08
Good to read you are making headway in getting to the suspend/resume issue.

After this morning oneiric update and reboot my suspend is back to normal even when running wireless with the RT2800 kernel driver. So...

I must say that oneiric is going through so many changes it may be worthwhile to wait until Beta1 to understand where things are.

---

