---
title: "Ubuntu 14 - Dosemu - Cups"
date: 2017-12-26
forum: New to Ubuntu
---

### Post by plozano on 2017-12-26
[COLOR=#555555][FONT=sans-serif]My dos program works perfectly in dosemu and in ubuntu 12, not until recently I upgrade it into ubuntu 14 64 bit, It can still print regular documents but not on my dos program. My printer is LQ-310.[/FONT][/COLOR]
[COLOR=#555555][FONT=sans-serif]P.S - Before in ubuntu 12 I simply install cups and will print directly.

Boot.log 

[/FONT][/COLOR]
CONF: config variable parser_version_3 set
CONF: config variable c_system set
CONF: Parsing built-in dosemu.conf file.
CONF: config variable version_3_style_used set
CONF: Parsing built-in global.conf file.
CONF: config variable version_3_style_used unset
CONF: config variable version_3_style_used set
CONF: opened include file /etc/dosemu/dosemu.conf
CONF: closed include file /etc/dosemu/dosemu.conf
CONF: mapping driver = 'auto'
debug flags: -a+cw
CONF: Disabling use of pentium timer
CONF: dosbanner on
CONF: timer freq=18, update=54925
CONF: CPU set to 586
CONF: JIT CPUEMU set to 0 for 586
CONF: 8192k bytes EMS memory
CONF: EMS-frame = 0xe400
CONF: DPMI-Server on (0x5000)
CONF: DPMI base addr = 0xffffffff
CONF: PM DOS API Translator on
CONF: No DJGPP NULL deref checks: off
CONF: 8192k bytes XMS memory
CONF: dosemu not running on console
CONF: time mode = 'bios'
SER: directory /var/lock namestub LCK.. binary No
MOUSE: no device specified, type 0 using internaldriver: yes, emulate3buttons: no baudrate: 0
CONF: Keyboard-layout keyb-user
CONF: **** Warning: floppy /dev/fd0 not accessible, disabled
CONF: fastfloppy = 1
CONF: IPX support off
CONF(LPT0) f: (null)   c: lpr -l  t: 20  port: 0
CONF(LPT1) f: (null)   c: lpr -l -P lpt2  t: 20  port: 0
CONF: not allowing speaker port access
CONF: Packet Driver enabled.
device: /home/it/.dosemu/drives/c type 4 h: -1  s: -1   t: -1 drive C:
device: /home/it/.dosemu/drives/d type 4 h: -1  s: -1   t: -1 drive D:
CONF: cdrom MSCD0001 on /dev/cdrom
CONF: config variable c_system unset
debug flags: 9+p
Linux kernel 4.4.0; CPU speed is 3200000000 Hz
CPU-EMU speed is 3200 MHz
CONF: mostly running as USER: uid=1000 (cached 1000) gid=1000 (cached 1000)
DBG_FD already set
DOSEMU-1.4.0.8 is coming up on Linux version 4.4.0-31-generic #50~14.04.1-Ubuntu SMP Wed Jul 13 01:07:32 UTC 2016 x86_64
Compiled with GCC version 4.7.2 -m64
WARN: vm86plus service not available in your kernel
WARN: using CPU emulation for vm86()
CONF: reserving 640Kb at 0x00000 for 'd' (Base DOS memory (first 640K))
CONF: reserving 48Kb at 0xF4000 for 'r' (Dosemu reserved area)
CONF: reserving 128Kb at 0xA0000 for 'v' (Video memory)
PKT: Cannot open raw sockets: Operation not permitted
WARN: using non-zero memory base address 0x10f000.
WARN: You can use the better-tested zero based setup using
WARN: sysctl -w vm.mmap_min_addr=0
WARN: as root, or by changing the vm.mmap_min_addr setting in
WARN: /etc/sysctl.conf or a file in /etc/sysctl.d/ to 0.
CONF: reserving 8256Kb at 0x100000 for 'x' (Extended memory (HMA+XMS))
Registering HWRAM, type=e base=0x40704000 size=0x400000
CONF: reserving 4096Kb at 0x40704000 for 'e' (VGAEMU LFB)
CONF: reserving 12Kb at 0xC0000 for 'V' (VGAEMU Video BIOS)
SERIAL $Id$
LPT: initializing printer <<NODEV>>
LPT: initializing printer <<NODEV>>
LPT: initializing printer <<NODEV>>
CONF: detected layout is "us"
CONF: detected alternate layout: us
CONF: reserving 16Kb at 0xE4000 for 'E' (EMS page frame)
CONF: reserving 16Kb at 0xE8000 for 'E' (EMS page frame)
CONF: reserving 16Kb at 0xEC000 for 'E' (EMS page frame)
CONF: reserving 16Kb at 0xF0000 for 'E' (EMS page frame)
CONF: reserving 132Kb at 0xC3000 for 'U' (Upper Memory Block (UMB, XMS 3.0))
TIME: using 9154 usec for updating ALRM timer
======================= ENTER CPU-EMU ===============


LPT0: Reading control byte 0xc
LPT0: Writing control byte 0x8
LPT0: Writing control byte 0xc
LPT0: Reading status byte 0xdc
LPT1: Reading control byte 0xc
LPT1: Writing control byte 0x8
LPT1: Writing control byte 0xc
LPT1: Reading status byte 0xdc
ERROR: MFS: couldn't find root path /media/CDROM
*	Fault out of DOSEMU code, cs:eip=33:4a5601, cr2=11cf, fault_cnt=1
*	Fault out of DOSEMU code, cs:eip=33:4a5601, cr2=11cf, fault_cnt=1
*	Fault out of DOSEMU code, cs:eip=33:4a5601, cr2=11cf, fault_cnt=1
*	Fault out of DOSEMU code, cs:eip=33:4a5601, cr2=11cf, fault_cnt=1
*	Fault out of DOSEMU code, cs:eip=33:4a5601, cr2=11cf, fault_cnt=1
*	Fault out of DOSEMU code, cs:eip=33:4a5601, cr2=11cf, fault_cnt=1
*	Fault out of DOSEMU code, cs:eip=33:4a5601, cr2=11cf, fault_cnt=1
*	Fault out of DOSEMU code, cs:eip=33:4a5601, cr2=11cf, 


LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc
LPT0: Reading status byte 0xdc




DOS termination requested
leavedos(dos_helper|530) called - shutting down
======================= LEAVE CPU-EMU ===============


LPT: closing printer 0 (<<NODEV>>)
LPT: closing printer 0, <<NODEV>>
LPT: closing printer 1 (<<NODEV>>)
LPT: closing printer 1, <<NODEV>>
LPT: closing printer 2 (<<NODEV>>)

---

