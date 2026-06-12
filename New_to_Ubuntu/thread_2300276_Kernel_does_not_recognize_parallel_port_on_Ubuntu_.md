---
title: "Kernel does not recognize parallel port on Ubuntu 14.04"
date: 2015-10-24
forum: New to Ubuntu
---

### Post by Chance_Hudson on 2015-10-24
I have a 64 bit dual boot machine running Windows
7 and *Ubuntu 14.04*.  The kernel does not recognize the parallel port
and there is no /dev/lp* or /dev/parport 0.

I could find only one previous posting with a
problem similar to mine, but it goes back to 2009-05-02 and is
entitled “[parallel port lpt not detected by ubuntu]("http://hplipopensource.com/node/217")”.  The the
solution was to add the following lines to
/etc/modprobe.d/alsa-base.conf: 

> alias parport_lowlevel parport_pc 
options parport_pc io=0x378 irq=auto 

This did not work for me.  I also placed these
lines in /etc/modprobe.d/modprobe.conf instead, with no change in the
outputs of “dmesg | grep par” and “lspci -v” (see below). 

The other posts, which at first appeared to me
to have a problem similar to mine, actually reported command output
indicating they had */dev/lp** and */dev/parport0* files.  Some were
using USB ports.  So theirs was a problem of printer recognition.  I
too may have that problem if I ever solve this parallel port
recognition problem.

My one year old computer would not normally have
come with a parallel port, but I have an *HP LaserJet 4300 Series*
printer, which works well on the second *Windows 7* system, where it is
connected to LPT3 - Device type: ports (COM & LPT). 

I am trying to move to Ubuntu Linux as permanent
platform, since it now appears all of my work can be done on Linux. 

Under my ASUS BIOS, under “PCH Express
Configuration”, the parallel port settings are minimal: 
*PCE-E Speed = Aut, Gen 1 or Gen 2*.  --- It is set to *Auto*.

TESTS FOR PORT FUNCTIONALlTY Under HPLIP CONFIGURATION, *'hp-check -t'* shows
parallel port functionality is enabled (“*pp-build=yes*”). 

Here are a few standard commands with outputs,
entered with the printer powered on: 

~$ lsmod | grep lp 
```
drm_kms_helper         55071  1 nouveau 
drm                   303102  3
ttm,drm_kms_helper,nouveau 
glue_helper            13990  1 aesni_intel 
ablk_helper            13597  1 aesni_intel 
cryptd                 20359  3
ghash_clmulni_intel,aesni_intel,ablk_helper 
lp                     17759  0 
parport                42348  3
lp,ppdev,parport_pc 
```

~$ lsmod | grep ppdev 
```
ppdev                  17671  0 
parport                42348  3
lp,ppdev,parport_pc 
```

~$ lsmod | grep parport_pc 
```
parport_pc             32701  0 
parport                42348  3
lp,ppdev,parport_pc 
```

At one point, I installed *lp0, lp1* and *lp2* with
MAKEDEV, changed the permissions to 666, and added $USER (myself) to
the lp user group.  But of course the “*echo “Hello” > lp0*"
etc yielded no output.  And these device files disappear in any case
upon rebooting. 

THE “dmesg | grep par” COMMAND I find only two instances where the parallel
port is mentioned, and the entry “parallel bus scan disabled”,
looks interesting.

~$ dmesg | grep par 
```
[    0.000000] Booting paravirtualized kernel on
bare hardware 
[    0.167553] regulator-dummy: no parameters 
[    0.252924] hpet0: 8 comparators, 64-bit
14.318180 MHz counter 
[    0.479362] Asymmetric key parser 'x509'
registered 
[    0.581328] ahci 0000:00:1f.2: flags: 64bit
ncq led clo pio slum part ems apst 
[    0.603981] ahci 0000:05:00.0: SSS flag set,
parallel bus scan disabled 
[    0.604019] ahci 0000:05:00.0: flags: 64bit
ncq sntf stag led clo pmp pio slum part ccc sxs 
[    7.114606] ppdev: user-space parallel port
driver 
[    8.568870] type=1400
audit(1445551635.496:2): apparmor="STATUS"
operation="profile_load" profile="unconfined"
name="/sbin/dhclient" pid=548 comm="apparmor_parser"
[    8.568873] type=1400
audit(1445551635.496:3): apparmor="STATUS"
operation="profile_load" profile="unconfined"
name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=548 comm="apparmor_parser" 
[    8.568875] type=1400
audit(1445551635.496:4): apparmor="STATUS"
operation="profile_load" profile="unconfined"
name="/usr/lib/connman/scripts/dhclient-script" pid=548
comm="apparmor_parser" 
[    8.568880] type=1400
audit(1445551635.496:5): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/sbin/dhclient" pid=547 comm="apparmor_parser"
[    8.568883] type=1400
audit(1445551635.496:6): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=547 comm="apparmor_parser" 
[    8.568885] type=1400
audit(1445551635.496:7): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/connman/scripts/dhclient-script" pid=547
comm="apparmor_parser" 
[    8.569067] type=1400
audit(1445551635.496:8): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=548 comm="apparmor_parser" 
[    8.569069] type=1400
audit(1445551635.496:9): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/connman/scripts/dhclient-script" pid=548
comm="apparmor_parser" 
[    8.569078] type=1400
audit(1445551635.496:10): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=547 comm="apparmor_parser" 
[    8.569080] type=1400
audit(1445551635.496:11): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/connman/scripts/dhclient-script" pid=547
comm="apparmor_parser" 
[   17.199014] type=1400
audit(1445551644.112:14): apparmor="STATUS"
operation="profile_load" profile="unconfined"
name="/usr/lib/cups/backend/cups-pdf" pid=850
comm="apparmor_parser" 
[   17.199016] type=1400
audit(1445551644.112:15): apparmor="STATUS"
operation="profile_load" profile="unconfined"
name="/usr/sbin/cupsd" pid=850 comm="apparmor_parser"
[   17.199194] type=1400
audit(1445551644.112:16): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/sbin/cupsd" pid=850 comm="apparmor_parser"
[   17.790795] type=1400
audit(1445551644.704:17): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/sbin/dhclient" pid=936 comm="apparmor_parser"
[   17.790799] type=1400
audit(1445551644.704:18): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=936 comm="apparmor_parser" 
[   17.790801] type=1400
audit(1445551644.704:19): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/connman/scripts/dhclient-script" pid=936
comm="apparmor_parser" 
[   17.790943] type=1400
audit(1445551644.704:20): apparmor="STATUS"
operation="profile_load" profile="unconfined"
name="/usr/lib/lightdm/lightdm-guest-session" pid=935
comm="apparmor_parser" 
[   17.790947] type=1400
audit(1445551644.704:21): apparmor="STATUS"
operation="profile_load" profile="unconfined"
name="chromium" pid=935 comm="apparmor_parser" 
[   17.790986] type=1400
audit(1445551644.704:22): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/NetworkManager/nm-dhcp-client.action"
pid=936 comm="apparmor_parser" 
[   17.790988] type=1400
audit(1445551644.704:23): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/connman/scripts/dhclient-script" pid=936
comm="apparmor_parser" 
[   47.304931] type=1400
audit(1445551674.156:68): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/lib/cups/backend/cups-pdf" pid=2335
comm="apparmor_parser" 
[   47.304938] type=1400
audit(1445551674.156:69): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/sbin/cupsd" pid=2335 comm="apparmor_parser"
[   47.305269] type=1400
audit(1445551674.160:70): apparmor="STATUS"
operation="profile_replace" profile="unconfined"
name="/usr/sbin/cupsd" pid=2335 comm="apparmor_parser"
```

More standard commands, entered with printer
powered on:

~$ ls -l /dev/lp* /dev/par* 
```

ls: cannot access /dev/lp*: No such file or directory   ls: cannot access /dev/par*: No such file or
directory
```

No printer auto-detection in kernel's virtual
file system: 
~$ ls -l
```
/proc/sys/dev/parport/parport*/autoprobe* 
ls: cannot access
/proc/sys/dev/parport/parport*/autoprobe*: No such file or directory
``` 

~$ sudo cat /proc/sys/dev/parport/parport*/autoprobe* 
```
cat: /proc/sys/dev/parport/parport*/autoprobe*:
No such file or directory 
```

The output of “lspci -v” also appears to
show no parallel port:
~$ lspci -v
```
00:00.0 Host bridge: Intel Corporation 4th Gen
Core Processor DRAM Controller (rev 06) 
    Subsystem: ASUSTeK Computer Inc. Device 8534 
    Flags: bus master, fast devsel, latency 0 
    Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Xeon
E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
(prog-if 00 [Normal decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
    I/O behind bridge: 0000e000-0000efff 
    Memory behind bridge: f6000000-f70fffff 
    Prefetchable memory behind bridge: 00000000e8000000-00000000f1ffffff 
    Capabilities: <access denied> 
    Kernel driver in use: pcieport

00:14.0 USB controller: Intel Corporation Device 8cb1 (prog-if 30 [XHCI]) 
    Subsystem: ASUSTeK Computer Inc. Device 8534 
    Flags: bus master, medium devsel, latency 0, IRQ 41 
    Memory at f7400000 (64-bit, non-prefetchable)[size=64K] 
    Capabilities: <access denied> 
    Kernel driver in use: xhci_hcd 


00:16.0 Communication controller: Intel Corporation Device 8cba 
    Subsystem: ASUSTeK Computer Inc. Device 8534 
    Flags: bus master, fast devsel, latency 0, IRQ 45 
    Memory at f7419000 (64-bit, non-prefetchable) [size=16] 
    Capabilities: <access denied> 
    Kernel driver in use: mei_me 

00:1a.0 USB controller: Intel Corporation Device 8cad (prog-if 20 [EHCI]) 
    Subsystem: ASUSTeK Computer Inc. Device 8534 
    Flags: bus master, medium devsel, latency 0, IRQ 20 
    Memory at f7417000 (32-bit, non-prefetchable) [size=1K] 
    Capabilities: <access denied> 
    Kernel driver in use: ehci-pci 

00:1b.0 Audio device: Intel Corporation Device 8ca0 
    Subsystem: ASUSTeK Computer Inc. Device 8616 
    Flags: bus master, fast devsel, latency 0, IRQ 46 
    Memory at f7410000 (64-bit, non-prefetchable) [size=16K] 
    Capabilities: <access denied> 
    Kernel driver in use: snd_hda_intel 

00:1c.0 PCI bridge: Intel Corporation Device 8c90 (rev d0) (prog-if 00 [Normal decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
    I/O behind bridge: 00002000-00002fff 
    Memory behind bridge: e0000000-e01fffff 
    Prefetchable memory behind bridge: 00000000e0200000-00000000e03fffff 
    Capabilities: <access denied> 
    Kernel driver in use: pcieport 

00:1c.2 PCI bridge: Intel Corporation Device 8c94 (rev d0) (prog-if 00 [Normal decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0 
    I/O behind bridge: 0000d000-0000dfff 
    Memory behind bridge: f7300000-f73fffff 
    Prefetchable memory behind bridge: 00000000f2200000-00000000f22fffff 
    Capabilities: <access denied> 
    Kernel driver in use: pcieport 

00:1c.6 PCI bridge: Intel Corporation Device 8c9c (rev d0) (prog-if 00 [Normal decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0 
    I/O behind bridge: 0000c000-0000cfff 
    Memory behind bridge: f7200000-f72fffff 
    Prefetchable memory behind bridge: 00000000f2100000-00000000f21fffff 
    Capabilities: <access denied> 
    Kernel driver in use: pcieport

00:1c.7 PCI bridge: Intel Corporation Device 8c9e (rev d0) (prog-if 00 [Normal decode]) 
    Flags: bus master, fast devsel, latency 0 
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0 
    I/O behind bridge: 0000b000-0000bfff 
    Memory behind bridge: f7100000-f71fffff 
    Capabilities: <access denied> 
    Kernel driver in use: pcieport 

00:1d.0 USB controller: Intel Corporation Device 8ca6 (prog-if 20 [EHCI]) 
    Subsystem: ASUSTeK Computer Inc. Device 8534 
    Flags: bus master, medium devsel, latency 0, IRQ 23 
    Memory at f7416000 (32-bit, non-prefetchable) [size=1K] 
    Capabilities: <access denied> 
    Kernel driver in use: ehci-pci 

00:1f.0 ISA bridge: Intel Corporation Device 8cc6 
    Subsystem: ASUSTeK Computer Inc. Device 8534 
    Flags: bus master, medium devsel, latency 0 
    Capabilities: <access denied> 

00:1f.2 SATA controller: Intel Corporation Device 8c82 (prog-if 01 [AHCI 1.0]) 
    Subsystem: ASUSTeK Computer Inc. Device 8534 
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42 
    I/O ports at f070 [size=8] 
    I/O ports at f060 [size=4] 
    I/O ports at f050 [size=8] 
    I/O ports at f040 [size=4] 
    I/O ports at f020 [size=32] 
    Memory at f7415000 (32-bit, non-prefetchable) [size=2K] 
    Capabilities: <access denied> 
    Kernel driver in use: ahci 

00:1f.3 SMBus: Intel Corporation Device 8ca2 
    Subsystem: ASUSTeK Computer Inc. Device 8534 
    Flags: medium devsel, IRQ 6 
    Memory at f7414000 (64-bit, non-prefetchable) [size=256] 
    I/O ports at f000 [size=32] 

01:00.0 VGA compatible controller: NVIDIA Corporation GK110 [GeForce GTX 780]
(rev a1) (prog-if 00 [VGA controller]) 
    Subsystem: ASUSTeK Computer Inc. Device 8499 
    Flags: fast devsel, IRQ 16 
    Memory at f6000000 (32-bit, non-prefetchable) [size=16M] 
    Memory at e8000000 (64-bit, prefetchable) [size=128M] 
    Memory at f0000000 (64-bit, prefetchable) [size=32M] 
    I/O ports at e000 [size=128] 
    Expansion ROM at f7000000 [disabled] [size=512K] 
    Capabilities: <access denied> 

01:00.1 Audio device: NVIDIA Corporation GK110 HDMI Audio (rev a1) 
    Subsystem: ASUSTeK Computer Inc. Device 8499 
    Flags: bus master, fast devsel, latency 0, IRQ 17 
    Memory at f7080000 (32-bit, non-prefetchable) [size=16K] 
    Capabilities: <access denied> 
    Kernel driver in use: snd_hda_intel

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit
Ethernet Controller (rev 11) 
    Subsystem: ASUSTeK Computer Inc. Device 859e 
    Flags: bus master, fast devsel, latency 0, IRQ 43 
    I/O ports at d000 [size=256] 
    Memory at f7300000 (64-bit, non-prefetchable) [size=4K] 
    Memory at f2200000 (64-bit, prefetchable) [size=16K] 
    Capabilities: <access denied> 
    Kernel driver in use: r8169 

04:00.0 Serial controller: Device 1c00:3050 (rev 10) (prog-if 05 [16850]) 
    Subsystem: Device 1c00:3050 
    Flags: fast devsel, IRQ 18 
    I/O ports at c000 [size=256] 
    Memory at f2100000 (32-bit, prefetchable) [size=32K] 
    I/O ports at c100 [size=4] 
    Expansion ROM at f7200000 [disabled] [size=32K]
    Capabilities: <access denied>

05:00.0 SATA controller: ASMedia Technology Inc.
ASM1062 Serial ATA Controller (rev 01) (prog-if 01 [AHCI 1.0]) 
    Subsystem: ASMedia Technology Inc. Device 1060 
    Flags: bus master, fast devsel, latency 0, IRQ 44 
    I/O ports at b050 [size=8] 
    I/O ports at b040 [size=4] 
    I/O ports at b030 [size=8] 
    I/O ports at b020 [size=4] 
    I/O ports at b000 [size=32] 
    Memory at f7110000 (32-bit, non-prefetchable) [size=512] 
    Expansion ROM at f7100000 [disabled] [size=64K]
    Capabilities: <access denied> 
    Kernel driver in use: ahci
```

I ran these commands for the parallel port CUPS
backend twice; once as user and once as root, and both simply return
to the prompt. 

[I]$ /usr/lib/cups/backend/parallel  
$ sudo /usr/lib/cups/backend/parallel[/I]

Thank you very much for you assistance.

---

### Post by Geoffrey_Arndt on 2015-10-24
It's been a while, but in the past I've used a parallel to serial port adapter. 

   I don't know if this type of solution is feasible for your specific situation but it's worth a mention just in case.    These are available via amazon, new egg etc.

---

### Post by Chance_Hudson on 2015-10-24
Yes, my hardware vendor tells me I might even be able to install a card right into the printer for USB access, but I am hoping to avoid that if a software solution is possible.

---

