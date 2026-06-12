---
title: "Help me with sound please"
date: 2008-06-22
forum: Philippine Team
---

### Post by joey129 on 2008-06-22
I'm using a Compaq Presario V3000. Kakainstall ko lang ng ubuntu pero wala siyang sound. I've been trying to fix it myself following these instructions (SoundTroubleshooting[!link!]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems") pero nasustuck ako..)

Here's what I did:
> joey@TopSecret-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0 
then:
> joey@TopSecret-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d4200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at d4300000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, fast devsel, latency 0
	Memory at d4280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at d4340000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d2000000-d3ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Memory behind bridge: d4000000-d40fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at d4544000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d4100000-d41fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at 18d0 [size=8]
	I/O ports at 18c4 [size=4]
	I/O ports at 18c8 [size=8]
	I/O ports at 18c0 [size=4]
	I/O ports at 18b0 [size=16]
	Memory at d4544400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: medium devsel, IRQ 10
	I/O ports at 18e0 [size=32]

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Compaq 6710b
	Flags: bus master, fast devsel, latency 0, IRQ 219
	Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 66, IRQ 19
	Memory at d4100000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 3000 [size=64]
	Capabilities: <access denied>

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at d4101000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at d4101800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: medium devsel, IRQ 10
	Memory at d4101c00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
	Subsystem: Hewlett-Packard Company Unknown device 30b2
	Flags: medium devsel, IRQ 10
	Memory at d4102000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f
Tama, right? anyway, I searched for the driver and ended up in this[!link!]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel") page. I think eto [!link!]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel") yung soundcard ko. So next step (at dito ako nasustuck):
> joey@TopSecret-laptop:~$ sudo modprobe snd-hda-intel
[sudo] password for joey: (i type my password here tapos..)
joey@TopSecret-laptop:~$ (nothing! bumabalik lang dito!)

I dont know what to do...:(

---

### Post by loell on 2008-06-22
i'm not sure why you're compiling a matrix driver ;)

as your audio is **Intel High Def Audio**

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

but do try this

[http://thio4linux.wordpress.com/2007/10/06/intel-hda-intel-corporation-82801g/]("http://thio4linux.wordpress.com/2007/10/06/intel-hda-intel-corporation-82801g/")

---

### Post by joey129 on 2008-06-22
> **loell said:**
> i'm not sure why you're compiling a matrix driver ;)

as your audio is **Intel High Def Audio**

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

but do try this

[http://thio4linux.wordpress.com/2007/10/06/intel-hda-intel-corporation-82801g/]("http://thio4linux.wordpress.com/2007/10/06/intel-hda-intel-corporation-82801g/")

matrix driver?:confused: hehe... ok, i admit, i have no idea what inputting all of these commands actually does.
and thanks for the link. it looks promising. but (sorry for my noobie-ness) i got stuck again XD
I was able to do steps 1 and 2 successfully but when i try to extract the files to /usr/src/alsa  i get an error message (this wasnt done from the terminal. i doubleclicked the file, extract, then set the location. i dunno if that info is relevant.. but whatever). here's the error:
> tar: alsa-driver-1.0.16: Cannot mkdir: Permission denied
tar: alsa-driver-1.0.16/Makefile.conf.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/acore/memalloc.inc1: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/sound.inc: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/misc_driver.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/control.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/pcm.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/pcm_misc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/sound.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/mixer_oss.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/mulaw.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/linear.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/io.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/pcm_plugin.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/route.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/rate.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/copy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/oss/pcm_oss.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_midi_event.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_ioctl.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_readq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_rw.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_init.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_writeq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_misc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_event.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/oss/seq_oss_timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_info.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_midi_emul.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_system.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_lock.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/CHANGES: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_queue.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_fifo.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_virmidi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old/seq_instr_missing.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old/instr: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old/instr/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old/instr/ainstr_iw.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old/instr/ainstr_simple.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old/instr/ainstr_gf1.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old/instr/ainstr_fm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/old/seq_instr.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_prioq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_device.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_clientmgr.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_memory.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_dummy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/seq/seq_ports.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/seq32.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/ioctl32.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/timer32_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/timer32.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/ioctl32_old.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/seq32_new.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/hwdep32_new.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/hwdep32.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/timer32_new.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/rawmidi32_new.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/pcm32.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/pcm32_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/pcm32_new.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/ioctl32_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/ioctl32.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/rawmidi32_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/rawmidi32.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/seq32_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/hwdep32_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/ioctl32/ioctl32_new.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/hpetimer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/pcm_memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/pcm_timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/device.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/pcm_native.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/control_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/wrappers.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/isadma.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/sgbuf.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/memalloc.inc: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/memory_wrapper.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/pcm_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/info_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/pci_compat_22.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/info.inc: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/pcm_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/info.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/hwdep.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/misc.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/init.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/timer.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/rawmidi.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/sound_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/rtctimer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/timer_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/hwdep_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/rawmidi_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/memalloc.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acore/memory_debug.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/misc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/misc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/misc/ac97_bus.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/scripts: Cannot create symlink to `alsa-kernel/scripts': No such file or directory
tar: alsa-driver-1.0.16/i2c: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/i2c/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/l3: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/i2c/l3/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/l3/uda1341.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/tea6330t.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/uda1380.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/i2c.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/cs8427.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/other: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/i2c/other/tea575x-tuner.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/other/ak4xxx-adda.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/other/ak4117.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/other/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/other/pt2258.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/i2c/other/ak4114.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/snddevices.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/toplevel.config: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/TODO: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/acinclude.m4: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/configure.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/version.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/sound: Cannot create symlink to `alsa-kernel': No such file or directory
tar: alsa-driver-1.0.16/arm: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/arm/sa11xx-uda1341.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/arm/pxa2xx-ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/arm/s3c24xx-iis.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/arm/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/arm/pxa2xx-i2sound.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/arm/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/arm/s3c24xx-iis.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/arm/pxa2xx-i2sound.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/arm/pxa2xx-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/ad1816a: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/ad1816a/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/ad1816a/ad1816a.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/ad1816a/ad1816a_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cmi8330.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/cs4231.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/pc98.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/cs4231_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/cs4232.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/sound_pc9800.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/pc9801_118_magic.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/cs4236.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/cs423x/cs4236_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sgalaxy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/wavefront: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/wavefront/wavefront_fx.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/wavefront/wavefront_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/wavefront/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/wavefront/wavefront.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/wavefront/yss225.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/wavefront/wavefront_synth.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/dt019x.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/azt2320.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/ad1848: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/ad1848/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/ad1848/ad1848.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/ad1848/ad1848_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/opti9xx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/opti9xx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/opti9xx/opti92x-ad1848.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/opti9xx/opti92x-cs4231.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/opti9xx/opti93x.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/opti9xx/miro.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sc6000.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/msnd_pinnacle.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/msnd_pinnacle.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/msnd_pinnacle_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/msnd.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/msnd_classic.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/msnd_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/msnd.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/msnd_classic.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/msnd/sintable.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/es1688: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/es1688/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/es1688/es1688.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/es1688/es1688_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/emu8000_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/emu8000_patch.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb8_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb16.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb8.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb16_csp_codecs.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sbawe.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb16_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb16_csp.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/es968.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/README: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb8_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/sb_common.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/emu8000_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/emu8000_callback.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sb/emu8000.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/es18xx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/als100.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/interwave-stb.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gusextreme.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_reset.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_uart.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_lfo.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/old: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/old/gus_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/old/gus_sample.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/old/gus-synth.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/old/gus_simple.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/old/gus_utils.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_io.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_mem_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gusmax.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_dram.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_dma.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gusclassic.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_volume.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/interwave.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_irq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_mem.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/gus/gus_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/adlib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/sscape.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/isa/opl3sa2.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa/pxa2xx-ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa/poodle.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa/spitz.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa/tosa.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa/corgi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa/pxa2xx-i2s.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/pxa/pxa2xx-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/soc-dapm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/at91: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/soc/at91/at91-ssc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/at91/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/at91/eti_b1_wm8731.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/at91/at91-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/soc-core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/fsl: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/soc/fsl/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx/s3c2443-ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx/smdk2443_wm9710.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx/ln2440sbc_alc650.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx/neo1970_wm8753.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx/s3c24xx-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx/s3c2412-i2s.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/s3c24xx/s3c24xx-is2.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs/wm8731.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs/wm9712.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs/wm8750.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs/ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs/cs4270.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs/wm8753.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/codecs/tlv320aic3x.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/sh: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/soc/sh/sh7760-ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/sh/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/sh/hac.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/soc/sh/ssi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/synth/emux: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/emux_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/emux_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/emux_nrpn.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/soundfont.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/emux_seq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/emux.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/emux_effect.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/emux_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/emux/emux_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/util_mem.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/synth/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/ppc/daca.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/awacs.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/pmac.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/beep_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/beep.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/keywest_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/pmac_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/tumbler.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/pmac.inc1: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/keywest.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/powermac.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/ppc/burgundy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/hgcompile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/aoa/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/core: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/aoa/core/snd-aoa-core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/core/snd-aoa-gpio-pmf.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/core/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/core/snd-aoa-gpio-feature.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/core/snd-aoa-alsa.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/codecs: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/aoa/codecs/snd-aoa-codec-toonie.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/codecs/snd-aoa-codec-onyx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/codecs/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/codecs/snd-aoa-codec-tas.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/fabrics: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/aoa/fabrics/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/fabrics/snd-aoa-fabric-layout.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus/sysfs.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus/i2sbus: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus/i2sbus/i2sbus-core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus/i2sbus/i2sbus-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus/i2sbus/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus/i2sbus/i2sbus-control.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aoa/soundbus/core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/INSTALL: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/snddevices: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/parisc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/parisc/harmony.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/parisc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/cmipci.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/maestro3.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/trident: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/trident/trident_memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/trident/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/trident/trident_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/trident/old: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/trident/old/trident_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/trident/old/trident-seq.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/trident/old/trident-synth.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/trident/trident.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/oxygen.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/oxygen.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/cm9780.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/hifier.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/virtuoso.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/oxygen_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/oxygen_io.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/oxygen_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/oxygen/oxygen_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ca0106: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/ca0106/ca0106_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ca0106/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ca0106/ca0106_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ca0106/ca0106_main.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ca0106/ca_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/es1968.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/rme32.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/als300.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/intel8x0m.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ad1889.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/riptide: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/riptide/riptide.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/riptide/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/azt3328.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/intel8x0.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs5530.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/au8820.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/au88x0.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/test: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/test/au88x0_a3d.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/test/au88x0_a3d.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/au8810.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/pci-ids.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/au88x0/au8830.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/delta.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/juli.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/ews.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/revo.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/hoontech.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/prodigy_hifi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/se.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/ice1724.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/vt1720_mobo.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/prodigy192.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/aureon.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/ice1712.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/wtm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/ak4xxx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/amp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/phase.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ice1712/pontis.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/atiixp.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/es1938.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/atiixp_modem.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ymfpci: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/ymfpci/ymfpci_main.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ymfpci/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ymfpci/ymfpci.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ymfpci/ymfpci_image.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpi4000.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpimsgx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpidspcd.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpimod.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpimsginit.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpipcida.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpios_linux_kernel.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpidebug.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpidspcd.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpimsginit.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/asihpi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpi6205.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpi4000.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpicmn.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpicmn.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpi6000.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpios.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpimsgx.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpios_linux_kernel.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpipci.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpi.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpifunc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpidebug.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpi6205.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/asihpi/hpi6000.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/nm256: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/nm256/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/nm256/nm256_coef.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/nm256/nm256.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ali5451: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/ali5451/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ali5451/ali5451.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs46xx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/cs46xx/dsp_spos.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs46xx/dsp_spos_scb_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs46xx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs46xx/cs46xx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs46xx/cs46xx_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/via82xx_modem.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs4281.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/vx222: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/vx222/vx222_ops.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/vx222/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/vx222/vx222.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emu10k1_callback.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emu10k1x.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emu10k1_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emu10k1_patch.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/irq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/io.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emumixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emufx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emu10k1.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emuproc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/tina2.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emumpu401.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/p16v.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/p16v.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emupcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/emu10k1_main.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/voice.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/emu10k1/p17v.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ac97: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/ac97/ac97_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ac97/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ac97/ak4531_codec.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ac97/ac97_codec.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ac97/ac97_id.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ac97/ac97_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/rme9652: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/rme9652/hdspm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/rme9652/hdsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/rme9652/rme9652.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/rme9652/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/rme96.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/sonicvibes.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs5535audio: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/cs5535audio/cs5535audio.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs5535audio/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs5535audio/cs5535audio_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/cs5535audio/cs5535audio_pm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/via82xx.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/hda_generic.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/patch_sigmatel.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/patch_analog.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/vmaster.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/hda_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/patch_conexant.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/patch_via.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/patch_cmedia.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/patch_realtek.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/hda_intel.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/hda_codec.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/patch_atihdmi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/hda_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/hda/patch_si3054.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ens1371.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pci_iomap_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/als4000.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ens1370.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/fm801.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/sis7019.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/mixart: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/mixart/mixart_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/mixart/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/mixart/mixart_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/mixart/mixart.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/mixart/mixart_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/bt87x.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/korg1212: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/korg1212/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/korg1212/korg1212.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/korg1212/korg1212-firmware.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pcxhr: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/pcxhr/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pcxhr/pcxhr.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pcxhr/pcxhr_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pcxhr/pcxhr_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pcxhr/pcxhr_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pdplus: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/pdplus/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pdplus/pdplus-pga-a.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pdplus/pdplus.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/pdplus/pdplus-pga-d.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/ad1889.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/gina24.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/gina20.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/indigoio.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/indigo.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/layla20_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/darla20_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/echo3g.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/darla24.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/echoaudio.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/gina24_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/layla20.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/mia_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/indigoio_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/mona_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/echo3g_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/indigodj_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/layla24.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/echoaudio_gml.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/indigo_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/echoaudio.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/layla24_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/echoaudio_3g.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/indigodj.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/darla20.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/mia.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/gina20_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/darla24_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/echoaudio_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pci/echoaudio/mona.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/configure: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/test/osspcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/ossoptr.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/mmap_test.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/osspcm1.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/seq1.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/osspcm2.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/ossdelay.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/oss-comm.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/seq2.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/test/oss-free.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/hal2: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/hal2/hal2.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/hal2/hal2_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/toplevel.config.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/drivers/virmidi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/serialmidi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl4: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl4/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl4/opl4_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl4/opl4_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl4/opl4_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl4/opl4_seq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl4/opl4_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl4/yrw801.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/pcsp: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/drivers/pcsp/pcsp_input.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/pcsp/pcsp_input.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/pcsp/pcsp_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/pcsp/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/pcsp/pcsp.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/pcsp/pcsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/pcsp/pcsp_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/mts64.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/portman2x4.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/serial-u16550.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/aloop-kernel.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/vx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/drivers/vx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/vx/vx_cmd.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/vx/vx_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/vx/vx_uer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/vx/vx_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/vx/vx_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/vx/vx_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl3: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl3/opl3_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl3/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl3/opl3_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl3/opl3_seq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl3/opl3_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl3/opl3_drums.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/opl3/opl3_lib.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/mtpav.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/aloop.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/mpu401: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/drivers/mpu401/mpu401_uart.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/mpu401/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/mpu401/mpu401.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/drivers/dummy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/scripts: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/scripts/docproc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/scripts/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/scripts/kernel-doc: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/scripts/kdeps: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/scripts/ksync: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/scripts/ksync.conf: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/scripts/kmerge: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/spi: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/spi/at73c213.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/spi/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/spi/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/spi/at73c213.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/l3: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/l3/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/l3/uda1341.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/tea6330t.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/i2c.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/cs8427.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/other: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/other/ak4xxx-adda.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/other/ak4117.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/other/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/other/pt2258.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/other/tea575x-tuner.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/i2c/other/ak4114.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/oss: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/oss/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/aaci.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/devdma.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/pxa2xx-ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/sa11xx-uda1341.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/aaci.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/devdma.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/pxa2xx-pcm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/arm/pxa2xx-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/ad1816a: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/ad1816a/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/ad1816a/ad1816a.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/ad1816a/ad1816a_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/cmi8330.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/cs423x: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/cs423x/cs4231.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/cs423x/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/cs423x/cs4231_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/cs423x/cs4232.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/cs423x/cs4236.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/cs423x/cs4236_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sgalaxy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/wavefront: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/wavefront/wavefront_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/wavefront/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/wavefront/wavefront.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/wavefront/yss225.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/wavefront/wavefront_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/wavefront/wavefront_fx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/dt019x.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/azt2320.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/ad1848: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/ad1848/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/ad1848/ad1848.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/ad1848/ad1848_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/opti9xx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/opti9xx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/opti9xx/opti92x-ad1848.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/opti9xx/opti92x-cs4231.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/opti9xx/miro.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/opti9xx/opti93x.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/opti9xx/miro.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sc6000.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/es1688: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/es1688/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/es1688/es1688.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/es1688/es1688_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/emu8000_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/emu8000_patch.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb8_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb16.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb8.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb16_csp_codecs.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sbawe.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb16_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/es968.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb16_csp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb8_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/sb_common.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/emu8000_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/emu8000_callback.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/emu8000_local.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sb/emu8000.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/es18xx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/als100.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/interwave-stb.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gusextreme.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_reset.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_instr.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_tables.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_uart.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_io.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_mem_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gusmax.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_dram.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_dma.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gusclassic.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_volume.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/interwave.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_irq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_mem.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/gus/gus_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/adlib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/sscape.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/isa/opl3sa2.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/pxa2xx-ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/pxa2xx-ac97.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/poodle.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/e800_wm9712.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/spitz.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/pxa2xx-i2s.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/tosa.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/corgi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/pxa2xx-pcm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/pxa2xx-i2s.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/pxa/pxa2xx-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/soc-dapm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/at91: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/at91/at91-ssc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/at91/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/at91/at91-ssc.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/at91/eti_b1_wm8731.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/at91/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/at91/at91-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/at91/at91-pcm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/soc-core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/fsl: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/fsl/fsl_ssi.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/fsl/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/fsl/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/fsl/fsl_dma.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/fsl/mpc8610_hpcd.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/fsl/fsl_ssi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/fsl/fsl_dma.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/s3c24xx-i2s.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/s3c2443-ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/smdk2443_wm9710.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/s3c24xx-ac97.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/neo1973_wm8753.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/s3c2412-i2s.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/ln2440sbc_alc650.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/lm4857.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/s3c24xx-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/s3c24xx-pcm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/s3c2412-i2s.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/s3c24xx/s3c24xx-i2s.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/wm8731.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/ac97.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/wm9712.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/wm8750.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/wm9712.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/wm8753.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/cs4270.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/cs4270.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/wm8750.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/wm8753.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/tlv320aic3x.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/tlv320aic3x.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/codecs/wm8731.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/sh: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/sh/sh7760-ac97.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/sh/dma-sh7760.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/sh/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/sh/hac.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/sh/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/soc/sh/ssi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux_nrpn.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/soundfont.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux_seq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux_voice.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux_effect.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/emux/emux_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/util_mem.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/synth/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/pmac.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/daca.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/burgundy.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/pmac.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/snd_ps3_reg.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/snd_ps3.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/tumbler_volume.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/beep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/awacs.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/awacs.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/snd_ps3.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/tumbler.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/keywest.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/powermac.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ppc/burgundy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/aoa.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/aoa-gpio.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/core: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/core/snd-aoa-core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/core/snd-aoa-gpio-pmf.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/core/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/core/snd-aoa-alsa.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/core/snd-aoa-gpio-feature.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/core/snd-aoa-alsa.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/snd-aoa-codec-toonie.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/snd-aoa-codec-onyx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/snd-aoa-codec-tas-basstreble.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/snd-aoa-codec-tas.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/snd-aoa-codec-tas-gain-table.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/snd-aoa-codec-tas.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/codecs/snd-aoa-codec-onyx.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/fabrics: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/fabrics/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/fabrics/snd-aoa-fabric-layout.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/fabrics/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/sysfs.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/soundbus.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/i2sbus: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/i2sbus/i2sbus-core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/i2sbus/i2sbus-pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/i2sbus/i2sbus-interface.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/i2sbus/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/i2sbus/i2sbus-control.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/i2sbus/i2sbus.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/aoa/soundbus/core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/CREDITS: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/arch: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/arch/arm: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/arch/arm/mach-pxa: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/arch/arm/mach-pxa/mainstone.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/usb: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/usb/gadget: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/usb/gadget/gmidi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/media: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/media/video: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/media/video/saa7134: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/media/video/saa7134/saa7134.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/media/video/saa7134/saa7134-alsa.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/media/video/cx88: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/media/video/cx88/cx88-alsa.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/input: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/input/touchscreen: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/drivers/input/touchscreen/ucb1400_ts.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/asm-arm: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/asm-arm/arch-omap: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/asm-arm/arch-omap/omap-alsa.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/asm-arm/arch-omap/eac.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/asm-arm/arch-pxa: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/asm-arm/arch-pxa/audio.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/linux: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/linux/spi: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/linux/spi/at73c213.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/linux/i2c-id.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/include/linux/pci_ids.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/kernel/MAINTAINERS: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/parisc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/parisc/harmony.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/parisc/harmony.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/parisc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/parisc/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ens1370.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/trident: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/trident/trident_memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/trident/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/trident/trident_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/trident/trident.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/oxygen.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/oxygen_regs.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/oxygen.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/cm9780.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/virtuoso.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/hifier.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/oxygen_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/oxygen_io.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/ak4396.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/oxygen_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/oxygen/oxygen_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/atiixp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ca0106: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ca0106/ca0106_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ca0106/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ca0106/ca0106_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ca0106/ca0106_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ca0106/ca0106.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ca0106/ca_midi.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ca0106/ca_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/es1968.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/rme32.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/als300.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/intel8x0m.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ad1889.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/riptide: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/riptide/riptide.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/riptide/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/via82xx_modem.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/azt3328.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs5530.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/intel8x0.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_wt.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_xtalk.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au8820.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_a3ddata.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au8830.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_mpu401.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_xtalk.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au8810.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au8810.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_a3d.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_eq.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_eqdata.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_eq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_a3d.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au8820.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au88x0_game.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/au88x0/au8830.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/delta.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/hoontech.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/juli.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/ews.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/revo.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/hoontech.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/prodigy_hifi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/amp.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/se.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/se.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/ice1724.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/juli.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/revo.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/prodigy192.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/vt1720_mobo.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/aureon.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/prodigy192.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/phase.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/pontis.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/aureon.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/stac946x.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/ice1712.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/wtm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/prodigy_hifi.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/ews.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/ice1712.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/ak4xxx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/envy24ht.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/amp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/delta.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/wtm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/vt1720_mobo.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/phase.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ice1712/pontis.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/es1938.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ad1889.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/maestro3.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ymfpci: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ymfpci/ymfpci_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ymfpci/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ymfpci/ymfpci.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ymfpci/ymfpci_image.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/nm256: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/nm256/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/nm256/nm256_coef.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/nm256/nm256.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ali5451: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ali5451/ali5451.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ali5451/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/dsp_spos.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/dsp_spos.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/dsp_spos_scb_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/cs46xx_lib.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/imgs: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/imgs/cwcdma.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/imgs/cwcbinhack.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/imgs/cwcasync.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/imgs/cwcsnoop.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/imgs/cwc4630.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/imgs/cwcdma.asp: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/cs46xx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/cs46xx_image.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs46xx/cs46xx_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs4281.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/vx222: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/vx222/vx222.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/vx222/vx222_ops.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/vx222/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/vx222/vx222.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emu10k1_main.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emu10k1_callback.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emu10k1_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emu10k1_patch.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/irq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/io.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emumixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emufx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emu10k1.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emuproc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emu10k1x.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/tina2.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emumpu401.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emu10k1_synth_local.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/p16v.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/p16v.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/emupcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/voice.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/emu10k1/p17v.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/bt87x.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/via82xx.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/ac97_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/ac97_patch.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/ac97_codec.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/ac97_local.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/ac97_patch.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/ak4531_codec.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/ac97_id.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ac97/ac97_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/rme9652: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/rme9652/hdspm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/rme9652/hdsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/rme9652/rme9652.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/rme9652/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/rme96.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/sonicvibes.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs5535audio: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs5535audio/cs5535audio.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs5535audio/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs5535audio/cs5535audio.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs5535audio/cs5535audio_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cs5535audio/cs5535audio_pm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/fm801.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/azt3328.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/sis7019.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/hda_generic.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/patch_sigmatel.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/hda_local.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/patch_analog.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/vmaster.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/hda_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/patch_conexant.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/patch_via.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/patch_cmedia.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/hda_patch.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/patch_realtek.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/hda_intel.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/hda_codec.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/hda_codec.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/patch_atihdmi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/hda_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/hda/patch_si3054.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/ens1371.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/als4000.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/cmipci.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/sis7019.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/mixart.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/mixart_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/mixart_mixer.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/mixart_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/mixart.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/mixart_core.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/mixart_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/mixart/mixart_hwdep.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/atiixp_modem.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/korg1212: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/korg1212/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/korg1212/korg1212.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/korg1212/korg1212-firmware.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/pcxhr.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/pcxhr_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/pcxhr_mixer.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/pcxhr_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/pcxhr_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/pcxhr_core.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/pcxhr_hwdep.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/pcxhr/pcxhr.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/darla24.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/echo3g.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/indigoio.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/layla20_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/darla20_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/echoaudio.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/gina24_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/gina20.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/mia.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/mia_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/indigoio_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/mona_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/echo3g_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/echoaudio_dsp.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/indigodj_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/indigo.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/echoaudio_gml.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/indigo_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/mona.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/layla24_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/echoaudio_3g.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/gina24.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/echoaudio.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/layla24.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/gina20_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/indigodj.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/darla24_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/echoaudio_dsp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/darla20.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pci/echoaudio/layla20.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/pcm-indirect2.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/virmidi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/portman2x4.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/mts64.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4/opl4_local.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4/opl4_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4/opl4_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4/opl4_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4/opl4_seq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4/opl4_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl4/yrw801.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/pcm-indirect2.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/ml403-ac97cr.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/serial-u16550.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx/vx_cmd.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx/vx_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx/vx_cmd.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx/vx_uer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx/vx_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx/vx_hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/vx/vx_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3/opl3_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3/opl3_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3/opl3_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3/opl3_seq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3/opl3_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3/opl3_voice.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/opl3/opl3_drums.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/mtpav.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/mpu401: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/mpu401/mpu401.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/mpu401/mpu401_uart.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/mpu401/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/drivers/dummy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/last.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/ac97_bus.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usbmixer_maps.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usbquirks.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usbmixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usbmidi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usbaudio.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usbaudio.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-midi.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-input.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-device.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-control.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-audio.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-control.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-audio.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-device.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-input.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/caiaq/caiaq-midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usbus428ctldefs.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usx2y.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usbusx2y.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usbusx2yaudio.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usX2Yhwdep.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usx2yhwdeppcm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usX2Yhwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usx2yhwdeppcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/usb/usx2y/usbusx2y.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/control.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/info.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/pcm_misc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/rawmidi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/mulaw.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/mixer_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/linear.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/io.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/pcm_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/pcm_plugin.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/route.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/rate.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/pcm_plugin.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/oss/copy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_clientmgr.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_midi_event.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_info.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_ioctl.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_synth.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_readq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_rw.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_init.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_readq.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_writeq.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_synth.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_timer.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_midi.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_event.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_writeq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_event.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_device.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss_timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/oss/seq_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_info.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_midi_emul.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_timer.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_system.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_prioq.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_lock.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_queue.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_memory.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_fifo.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_queue.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_fifo.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_virmidi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_prioq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_device.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_ports.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_system.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_clientmgr.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_dummy.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_lock.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/seq/seq_ports.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/misc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/pcm_memory.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/pcm_timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/sound.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/memalloc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/device.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/control_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/isadma.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/sgbuf.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/pcm_native.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/pcm_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/init.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/info_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/pcm_lib.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/hwdep.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/timer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/sound_oss.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/rtctimer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/timer_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/hwdep_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/core/rawmidi_compat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/mips: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/mips/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/mips/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/mips/au1x00.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/vx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/vx/vxpocket.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/vx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/vx/vxpocket.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/vx/vxp_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/vx/vxp_ops.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/pdaudiocf: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/pdaudiocf/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sparc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sparc/dbri.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sparc/cs4231.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sparc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sparc/amd7930.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sparc/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sound_firmware.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/Joystick.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/hda_codec.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc/clocking.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc/overview.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc/codec.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc/dapm.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc/pops_clicks.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc/machine.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc/DAI.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/soc/platform.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/Bt87x.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/VIA82xx-mixer.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/hdspm.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/ControlNames.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/serial-u16550.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/seq_oss.html: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/emu10k1-jack.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/powersave.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/OSS-Emulation.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/CMIPCI.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/Procfile.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/Audigy-mixer.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/DocBook: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/DocBook/alsa-driver-api.tmpl: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/DocBook/writing-an-alsa-driver.tmpl: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/Audiophile-Usb.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/ALSA-Configuration.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/MIXART.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/Documentation/SB-Live-mixer.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sound_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sh: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sh/aica.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sh/aica.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sh/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/sh/Kconfig: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/soc.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/sb16_csp.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/asoundef.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/seq_kernel.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/initval.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/cs4231.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/ak4xxx-adda.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/emux_synth.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/seq_virmidi.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/hwdep.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/core.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/wavefront.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/opl4.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/hdsp.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/pcm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/util_mem.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/seq_oss.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/cs4231-regs.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/emux_legacy.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/seq_oss_legacy.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/Kbuild: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/minors.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/emu8000.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/ac97_codec.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/pt2258.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/sfnt_info.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/cs8403.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/seq_midi_event.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/uda1341.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/pcm-indirect.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/seq_midi_emul.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/trident.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/cs46xx_dsp_scb_types.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/soc-dapm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/ak4117.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/rawmidi.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/memalloc.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/asound_fm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/ad1848.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/i2c.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/emu10k1.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/timer.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/ak4531_codec.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/hdspm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/pcm_params.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/emu8000_reg.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/mpu401.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/cs46xx_dsp_spos.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/cs46xx.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/mixer_oss.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/ymfpci.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/snd_wavefront.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/hda_hwdep.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/tlv.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/seq_device.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/ak4114.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/cs8427.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/sb.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/pcm_oss.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/opl3.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/es1688.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/control.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/driver.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/emu10k1_synth.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/vx_core.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/ad1816a.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/sscape_ioctl.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/asequencer.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/gus.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/info.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/soundfont.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/tea575x-tuner.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/asound.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/cs46xx_dsp_task_types.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/alsa-kernel/include/tea6330t.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/usb/usbaudio.inc: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usbaudio.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usbcompat.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usbmidi.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/caiaq: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/usb/caiaq/caiaq-input.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/caiaq/caiaq-control.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/caiaq/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/caiaq/caiaq-device.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/caiaq/caiaq-audio.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/caiaq/caiaq-midi.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usbmidi.inc1: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usbmixer.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usbaudio.inc1: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usx2y: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/usb/usx2y/usx2yhwdeppcm.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usx2y/usbusx2y.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usx2y/usX2Yhwdep.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usx2y/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usx2y/usbusx2yaudio.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/usb/usbmidi.inc: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/version: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/support/isapnp: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/support/isapnp/isapnp_proc.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/isapnp/isapnp.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/isapnp/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/isapnp/isapnp.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/isapnp/isapnp_test.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/isapnp/isapnp_quirks.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/isapnp/isapnp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/pnp: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/support/pnp/pnp.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/pnp/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/pnp/pnp.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/support/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/doc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/doc/SOUNDCARDS: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/doc/README.1st: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/doc/INSTALL.asihpi-alsa: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/doc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/doc/README.riptide: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/doc/serialmidi.txt: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/doc/DocBook: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/doc/DocBook/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/doc/README.asihpi-alsa: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/mips: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/mips/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/mips/au1x00.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vxpocket.conf: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vxpocket.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vxpocket-2.6.16.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vxpocket.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vxp_mixer.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vxp_ops.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vx_entry.inc1: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vxpocket_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/vx/vx_entry.inc: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/pdaudiocf.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/pdaudiocf_core.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/pdaudiocf.conf: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/pdaudiocf_old.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/pdaudiocf.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/pdaudiocf_irq.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/pdaudiocf_pcm.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/pcmcia/pdaudiocf/pdaudiocf-2.6.16.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/cvscompile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/sparc: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/sparc/dbri.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/sparc/cs4231.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/sparc/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/sparc/amd7930.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/README: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/kconfig-vers: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/utils/alsa-driver.spec.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/module-options: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/kredirect.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/alsasound.posix.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/buildrpm: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/link-modules: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/insert: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/convert_isapnp_ids: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.top.2.4.0-test10: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.15-01.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.22-01.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.1: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.16.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/rtc-2.2.16.dif: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/soundcore.2.4.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.21-02.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.19-01.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.14-01.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.20.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/patch.mem.c.2.3.34: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/byteswap.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.17-03.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/pnp-suspend-2.6.15-rc1.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.9.dif: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.top.2.4.1: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.0-test10: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.23.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/patch.Makefile.2.4.2: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/soundcore.2.4.20.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/pcsp-kernel-2.6.18-01.diff: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/rtc-2.4.25.patch: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patches/rtc-suse-7.0-2.2.16.dif: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/buildrpm.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/alsasound: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/old: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/utils/old/export-symbols.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/old/export-symbols.perl: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/mod-deps: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/patch-alsa: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/mod-deps.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/alsasound.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/oss-move: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/remove: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/utils/alsasound.posix: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/modules: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/modules/.keepme: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/aclocal.m4: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/SUPPORTED_KERNELS: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/sh: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/sh/aica.c: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/sh/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/include/compat_cs.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/hal2.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/compat_64.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/i2c-id_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/isa_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/config1.h.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/platform_device_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/syscalls_26.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/kthread_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/pci_ids_compat.h.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/i2c-id_compat.h.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/asm: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/include/Makefile: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/adriver.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/firmware_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/autoconf-extra.h.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/autoconf-extra.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/old: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/include/old/ainstr_iw.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/old/gf1.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/old/ainstr_fm.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/old/ainstr_gf1.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/old/ainstr_simple.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/old/ultra_todo.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/old/seq_instr.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/version.h.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/config.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/media: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/include/version.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/modules: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/include/modules/.keepme: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/config.h.in: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/config1.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/pci_ids_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/uda1380.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/linux: Cannot mkdir: No such file or directory
tar: alsa-driver-1.0.16/include/latency_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/bitmap_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/compat_22.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/mutex_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/err_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/device_compat.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/include/ppc-prom-hack.h: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/COPYING: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/Rules.make1: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/install-sh: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/WARNING: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/Rules.make: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/FAQ: Cannot open: No such file or directory
tar: alsa-driver-1.0.16/CARDS-STATUS: Cannot open: No such file or directory
tar: Error exit delayed from previous errors
:(...whoa, right? thats what happened when i tried extracting the alsa-driver-1.0.16.tar.bz2 file to /usr/src/alsa

oh, and how do i do this:
> sudo mkdir -p /usr/src/alsa
sudo cp alsa-* /usr/src/alsa sudo tar xjf
alsa-driver-1.0.14rc1.tar.bz2sudo tar xjf
alsa-lib-1.0.14rc1.tar.bz2sudo tar xjf
alsa-utils-1.0.14rc1.tar.bz2
cd /usr/src/alsa

thanks a bunch for replying, btw :)

---

### Post by loell on 2008-06-22
you must be root / super user to let the tar file be extracted to that directory.

---

### Post by joey129 on 2008-06-23
ok...i feel totally stupid. i double clicked the sound thinggy. then chose to display everything from the preferences menu. tapos i unmutted PCM 2 and voila! sound yey!!! that was easy! thanks for your help anyway!

---

### Post by Script Warlock on 2008-06-23
hehehe ok at solve na problema mo pero halos mapuno yung isang page

---

