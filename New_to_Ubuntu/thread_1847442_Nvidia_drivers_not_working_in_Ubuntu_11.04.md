---
title: "Nvidia drivers not working in Ubuntu 11.04"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by MashedUp on 2011-09-20
My previous post on this seems to have dropped off the radar ;)

I know there are heaps of posts on this (I've read most of them, and tried the solutions from many) but since going from 10.04, where everything worked perfectly, to 11.04 (also tried 10.10 - same) I can't get the drivers for my nvidia video card to work.


- I install the current driver (through Jockey or the terminal) which seems to go ok, and gives me a tiny little xorg.conf file without a "Driver" line.

- I reboot, but everything looks the same as before, and Jockey says the drivers are installed but not being used. 

- I run nvidia-settings but because xorg.conf doesn't say I'm using the nvidia driver it tells me to run nvidia-xconfig and reboot.

- I run nvidia-xconfig (well I do in 10.10 at least - 11.04 doesn't appear to have it!!) and get a nice looking xorg.conf.

- I reboot, and just get the CLI. The only way to boot back into the GUI is to remove the "Driver nvidia" line from xorg.conf (or to delete xorg.conf completely).


I've tried many, many variations on the above, but that's the basic story: install the drivers but see no change, and only get CLI if xorg.conf has the driver line.

Does anyone know how to fix this? Anything....?

EDIT: I have attached a nvidia bug report below.  I don't know what I'm looking for in it and it's quite large, so doesn't mean anything to me.  
Some extra info that may help make sense of the report: OS is latest Mint version (just tried it in desperation, but get same results as Ubuntu - surprise, surprise) and I have two cards: a GT240 and a 9300GS (both use the same driver and were working perfectly in 10.04 with 3 screens), but currently only interested in getting 1 screen on the GT240 to work properly.

This bug report is just after re-installing the current drivers through Jockey.  xorg.conf wasn't created so boot goes through to GUI, but the nvidia drivers aren't being used. (If I create xorg.conf with "Driver nvidia" I'll only be able to boot to CLI)

---

### Post by wildmanne39 on 2011-09-20
Hi, the part about it saying it is not in use is a bug and if you activated it and you see a green dot in additional drivers then it is working.

Please post the results of these commands here:
```
lsmod
```
```
/usr/lib/nux/unity_support_test -p
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by wildmanne39 on 2011-09-20
Hi, I looked over your logs, just so you know they are not bug reports as mentioned, they are your logs from your system, two different things. That was a lot of information let's see if we can get it to just a little bit.

Please run these commands in a terminal.

```
dmesg | egrep 'nvi|vga'
```
```
sudo tail -n100 /var/log/syslog
```
```
tail -n100 /var/log/kern.log
```
Restart your computer then right these commands as soon as you get boot back up
Thank you

---

### Post by MashedUp on 2011-09-20
Ok, here we go:


dmesg | egrep 'nvi|vga'```

[    0.351294] vgaarb: device added: PCI:0000:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.351296] vgaarb: loaded
[    9.736721] nvidia: module license 'NVIDIA' taints kernel.
[   10.091502] nvidia 0000:02:00.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[   10.091541] nvidia: probe of 0000:02:00.0 failed with error -1
```



sudo tail -n100 /var/log/syslog```

Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950692]  [<ffffffff81087750>] ? kthread+0x0/0xa0
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950694]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950695] ---[ end trace de2ce91896c58617 ]---
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950697] hda-intel: ioremap error
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950703] HDA Intel 0000:02:00.1: PCI INT B disabled
Sep 21 10:24:31 infin-MCP61M-M3 acpid: starting up with proc fs
Sep 21 10:24:31 infin-MCP61M-M3 acpid: 32 rules loaded
Sep 21 10:24:31 infin-MCP61M-M3 acpid: waiting for events: event logging is off
Sep 21 10:24:31 infin-MCP61M-M3 cron[1077]: (CRON) INFO (pidfile fd = 3)
Sep 21 10:24:31 infin-MCP61M-M3 anacron[1103]: Anacron 2.3 started on 2011-09-21
Sep 21 10:24:31 infin-MCP61M-M3 cron[1108]: (CRON) STARTUP (fork ok)
Sep 21 10:24:31 infin-MCP61M-M3 cron[1108]: (CRON) INFO (Running @reboot jobs)
Sep 21 10:24:31 infin-MCP61M-M3 anacron[1103]: Normal exit (0 jobs run)
Sep 21 10:24:31 infin-MCP61M-M3 anacron[1211]: Anacron 2.3 started on 2011-09-21
Sep 21 10:24:31 infin-MCP61M-M3 anacron[1211]: Normal exit (0 jobs run)
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   12.472942] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   12.493644] EXT4-fs (sda5): re-mounted. Opts: commit=0
Sep 21 10:24:32 infin-MCP61M-M3 avahi-daemon[844]: Server startup complete. Host name is infin-MCP61M-M3.local. Local service cookie is 3175967854.
Sep 21 10:24:32 infin-MCP61M-M3 NetworkManager[851]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep 21 10:24:32 infin-MCP61M-M3 NetworkManager[851]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep 21 10:24:32 infin-MCP61M-M3 NetworkManager[851]: <info> Activation (eth0) successful, device activated.
Sep 21 10:24:32 infin-MCP61M-M3 NetworkManager[851]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep 21 10:24:32 infin-MCP61M-M3 avahi-daemon[844]: Service "infin-MCP61M-M3" (/services/udisks.service) successfully established.
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.793084] ppdev: user-space parallel port driver
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805032] vesafb: framebuffer at 0xcf000000, mapped to 0xffffc90012600000, using 1216k, total 1216k
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805035] vesafb: mode is 640x480x32, linelength=2560, pages=0
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805037] vesafb: scrolling: redraw
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805039] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805157] Console: switching to colour frame buffer device 80x30
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.808959] fb0: VESA VGA frame buffer device
Sep 21 10:24:34 infin-MCP61M-M3 gdm-binary[1358]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 21 10:24:34 infin-MCP61M-M3 gdm-binary[1358]: WARNING: Unable to find users: no seat-id found
Sep 21 10:24:34 infin-MCP61M-M3 gdm-simple-slave[1428]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 21 10:24:34 infin-MCP61M-M3 acpid: client connected from 1431[0:0]
Sep 21 10:24:34 infin-MCP61M-M3 acpid: 1 client rule loaded
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   15.460517] [drm] Initialized drm 1.1.0 20060810
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.500910] nouveau 0000:02:00.0: setting latency timer to 64
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503097] resource map sanity check conflict: 0x0 0x7fffff 0xa0000 0xbffff PCI Bus 0000:00
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503100] ------------[ cut here ]------------
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503106] WARNING: at /build/buildd/linux-2.6.38/arch/x86/mm/ioremap.c:98 __ioremap_caller+0x387/0x3d0()
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503108] Hardware name: MCP61M-M3
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503109] Info: mapping multiple BARs. Your kernel is fine.
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503110] Modules linked in: nouveau(+) ttm drm_kms_helper drm i2c_algo_bit video vesafb parport_pc ppdev dm_crypt binfmt_misc snd_hda_codec_via snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd psmouse joydev edac_core edac_mce_amd soundcore serio_raw snd_page_alloc k10temp i2c_nforce2 lp parport dm_raid45 xor btrfs zlib_deflate libcrc32c usbhid hid pata_amd forcedeth sata_nv
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503134] Pid: 1438, comm: work_for_cpu Tainted: P        W   2.6.38-8-generic #42-Ubuntu
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503136] Call Trace:
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503140]  [<ffffffff81065cef>] ? warn_slowpath_common+0x7f/0xc0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503143]  [<ffffffff81065de6>] ? warn_slowpath_fmt+0x46/0x50
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503146]  [<ffffffff81040de7>] ? __ioremap_caller+0x387/0x3d0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503160]  [<ffffffffa02b3507>] ? nouveau_load+0xa7/0x550 [nouveau]
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503165]  [<ffffffff815c2cbe>] ? _raw_spin_lock+0xe/0x20
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503168]  [<ffffffff81081282>] ? __alloc_workqueue_key+0x202/0x560
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503170]  [<ffffffff81040e87>] ? ioremap_nocache+0x17/0x20
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503179]  [<ffffffffa02b3507>] ? nouveau_load+0xa7/0x550 [nouveau]
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503190]  [<ffffffffa0251b0e>] ? drm_get_pci_dev+0x18e/0x300 [drm]
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503193]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503203]  [<ffffffffa0331cd9>] ? nouveau_pci_probe+0x15/0x17 [nouveau]
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503205]  [<ffffffff8130031f>] ? local_pci_probe+0x5f/0xd0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503208]  [<ffffffff8107ffb0>] ? do_work_for_cpu+0x0/0x30
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503210]  [<ffffffff8107ffc8>] ? do_work_for_cpu+0x18/0x30
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503212]  [<ffffffff810877e6>] ? kthread+0x96/0xa0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503215]  [<ffffffff8100ce24>] ? kernel_thread_helper+0x4/0x10
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503217]  [<ffffffff81087750>] ? kthread+0x0/0xa0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503219]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503221] ---[ end trace de2ce91896c58618 ]---
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503224] [drm] nouveau 0000:02:00.0: Unable to initialize the mmio mapping. Please report your setup to dri-devel@lists.sourceforge.net
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503548] nouveau: probe of 0000:02:00.0 failed with error -22
Sep 21 10:24:36 infin-MCP61M-M3 gdm-session-worker[1486]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 21 10:24:36 infin-MCP61M-M3 rtkit-daemon[1493]: Successfully called chroot.
Sep 21 10:24:36 infin-MCP61M-M3 rtkit-daemon[1493]: Successfully dropped privileges.
Sep 21 10:24:36 infin-MCP61M-M3 rtkit-daemon[1493]: Successfully limited resources.
Sep 21 10:24:36 infin-MCP61M-M3 rtkit-daemon[1493]: Running.
Sep 21 10:24:36 infin-MCP61M-M3 rtkit-daemon[1493]: Canary thread running.
Sep 21 10:24:36 infin-MCP61M-M3 rtkit-daemon[1493]: Watchdog thread running.
Sep 21 10:24:36 infin-MCP61M-M3 rtkit-daemon[1493]: Successfully made thread 1491 of process 1491 (n/a) owned by '106' high priority at nice level -11.
Sep 21 10:24:36 infin-MCP61M-M3 rtkit-daemon[1493]: Supervising 1 threads of 1 processes of 1 users.
Sep 21 10:24:36 infin-MCP61M-M3 anacron[1554]: Anacron 2.3 started on 2011-09-21
Sep 21 10:24:36 infin-MCP61M-M3 anacron[1554]: Normal exit (0 jobs run)
Sep 21 10:24:37 infin-MCP61M-M3 kernel: [   17.584649] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Sep 21 10:24:37 infin-MCP61M-M3 kernel: [   17.586942] EXT4-fs (sda5): re-mounted. Opts: commit=0
Sep 21 10:24:38 infin-MCP61M-M3 gdm-simple-greeter[1482]: Gtk-WARNING: /build/buildd/gtk+2.0-2.24.4/gtk/gtkwidget.c:5687: widget not within a GtkWindow
Sep 21 10:24:38 infin-MCP61M-M3 gdm-simple-greeter[1482]: WARNING: Unable to load CK history: no seat-id found
Sep 21 10:24:39 infin-MCP61M-M3 gdm-session-worker[1486]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep 21 10:24:41 infin-MCP61M-M3 gdm-session-worker[1486]: pam_sm_authenticate: Called
Sep 21 10:24:41 infin-MCP61M-M3 gdm-session-worker[1486]: pam_sm_authenticate: username = [infin]
Sep 21 10:24:41 infin-MCP61M-M3 ntpdate[1308]: adjust time server 91.189.94.4 offset 0.292550 sec
Sep 21 10:24:41 infin-MCP61M-M3 pulseaudio[1491]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-uJCTJlQzry: Connection refused
Sep 21 10:24:41 infin-MCP61M-M3 kernel: [   22.280029] eth0: no IPv6 routers present
Sep 21 10:24:42 infin-MCP61M-M3 rtkit-daemon[1493]: Successfully made thread 1677 of process 1677 (n/a) owned by '1000' high priority at nice level -11.
Sep 21 10:24:42 infin-MCP61M-M3 rtkit-daemon[1493]: Supervising 2 threads of 2 processes of 2 users.
Sep 21 10:24:42 infin-MCP61M-M3 nautilus: [N-A] Nautilus-Actions Tracker 3.0.5 initializing...
Sep 21 10:24:42 infin-MCP61M-M3 nautilus: [N-A] Nautilus-Actions Menu Extender 3.0.5 initializing...
Sep 21 10:24:48 infin-MCP61M-M3 rtkit-daemon[1493]: Successfully made thread 1861 of process 1677 (n/a) owned by '1000' RT at priority 5.
Sep 21 10:24:48 infin-MCP61M-M3 rtkit-daemon[1493]: Supervising 3 threads of 2 processes of 2 users.
Sep 21 10:24:48 infin-MCP61M-M3 rtkit-daemon[1493]: Successfully made thread 1862 of process 1677 (n/a) owned by '1000' RT at priority 5.
Sep 21 10:24:48 infin-MCP61M-M3 rtkit-daemon[1493]: Supervising 4 threads of 2 processes of 2 users.
Sep 21 10:24:48 infin-MCP61M-M3 rtkit-daemon[1493]: Successfully made thread 1869 of process 1869 (n/a) owned by '1000' high priority at nice level -11.
Sep 21 10:24:48 infin-MCP61M-M3 rtkit-daemon[1493]: Supervising 5 threads of 3 processes of 2 users.
Sep 21 10:24:48 infin-MCP61M-M3 pulseaudio[1869]: pid.c: Daemon already running.
Sep 21 10:25:38 infin-MCP61M-M3 sudo: pam_sm_authenticate: Called
Sep 21 10:25:38 infin-MCP61M-M3 sudo: pam_sm_authenticate: username = [infin]

```


tail -n100 /var/log/kern.log```

Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.424348] Adding 3912700k swap on /dev/sda4.  Priority:-1 extents:1 across:3912700k 
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.463843] i2c i2c-0: nForce2 SMBus adapter at 0x4d00
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.463877] i2c i2c-1: nForce2 SMBus adapter at 0x4e00
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.464368] lp: driver loaded but no devices found
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.483744] MCE: In-kernel MCE decoding enabled.
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.496605] EDAC MC: Ver: 2.1.0 Apr 11 2011
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.616357] EDAC amd64_edac: v3.3.0
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.620521] EDAC amd64: DRAM ECC disabled.
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.620530] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.620531]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.620532]  (Note that use of the override may cause unknown side effects.)
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.693245] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.693252] HDA Intel 0000:00:05.0: PCI INT B -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.693254] hda_intel: Disable MSI for Nvidia chipset
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.693280] HDA Intel 0000:00:05.0: setting latency timer to 64
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.736721] nvidia: module license 'NVIDIA' taints kernel.
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [    9.736725] Disabling lock debugging due to kernel taint
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091486] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091502] nvidia 0000:02:00.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091506] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091507] NVRM: BAR0 is 0M @ 0x0 (PCI:0000:02:00.0)
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091509] NVRM: The system BIOS may have misconfigured your GPU.
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091541] nvidia: probe of 0000:02:00.0 failed with error -1
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091580] NVRM: The NVIDIA probe routine failed for 1 device(s).
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091582] NVRM: None of the NVIDIA graphics adapters were initialized!
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.430821] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.533334] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   11.298020] EXT3-fs: barriers not enabled
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   11.307081] kjournald starting.  Commit interval 5 seconds
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   11.307343] EXT3-fs (sda6): using internal journal
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   11.307348] EXT3-fs (sda6): mounted filesystem with ordered data mode
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.525768] forcedeth 0000:00:07.0: irq 43 for MSI/MSI-X
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950600] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 18
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950617] HDA Intel 0000:02:00.1: PCI INT B -> Link[LNKC] -> GSI 18 (level, low) -> IRQ 18
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950619] hda_intel: Disable MSI for Nvidia chipset
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950622] ------------[ cut here ]------------
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950627] WARNING: at /build/buildd/linux-2.6.38/drivers/pci/pci.c:118 pci_ioremap_bar+0x71/0x80()
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950629] Hardware name: MCP61M-M3
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950630] Modules linked in: snd_hda_codec_via snd_hda_intel(+) snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd psmouse joydev edac_core edac_mce_amd soundcore serio_raw snd_page_alloc k10temp i2c_nforce2 lp parport dm_raid45 xor btrfs zlib_deflate libcrc32c usbhid hid pata_amd forcedeth sata_nv
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950649] Pid: 1026, comm: work_for_cpu Tainted: P            2.6.38-8-generic #42-Ubuntu
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950651] Call Trace:
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950656]  [<ffffffff81065cef>] ? warn_slowpath_common+0x7f/0xc0
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950658]  [<ffffffff81065d4a>] ? warn_slowpath_null+0x1a/0x20
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950661]  [<ffffffff812fde61>] ? pci_ioremap_bar+0x71/0x80
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950666]  [<ffffffffa01b8b33>] ? azx_create+0x347/0x7f4 [snd_hda_intel]
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950672]  [<ffffffffa0192444>] ? snd_card_create+0x1b4/0x390 [snd]
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950676]  [<ffffffffa01b929c>] ? azx_probe+0xb3/0x274 [snd_hda_intel]
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950678]  [<ffffffff8130031f>] ? local_pci_probe+0x5f/0xd0
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950681]  [<ffffffff8107ffb0>] ? do_work_for_cpu+0x0/0x30
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950684]  [<ffffffff8107ffc8>] ? do_work_for_cpu+0x18/0x30
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950686]  [<ffffffff810877e6>] ? kthread+0x96/0xa0
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950689]  [<ffffffff8100ce24>] ? kernel_thread_helper+0x4/0x10
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950692]  [<ffffffff81087750>] ? kthread+0x0/0xa0
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950694]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950695] ---[ end trace de2ce91896c58617 ]---
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950697] hda-intel: ioremap error
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   11.950703] HDA Intel 0000:02:00.1: PCI INT B disabled
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   12.472942] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Sep 21 10:24:31 infin-MCP61M-M3 kernel: [   12.493644] EXT4-fs (sda5): re-mounted. Opts: commit=0
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.793084] ppdev: user-space parallel port driver
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805032] vesafb: framebuffer at 0xcf000000, mapped to 0xffffc90012600000, using 1216k, total 1216k
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805035] vesafb: mode is 640x480x32, linelength=2560, pages=0
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805037] vesafb: scrolling: redraw
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805039] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.805157] Console: switching to colour frame buffer device 80x30
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   14.808959] fb0: VESA VGA frame buffer device
Sep 21 10:24:34 infin-MCP61M-M3 kernel: [   15.460517] [drm] Initialized drm 1.1.0 20060810
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.500910] nouveau 0000:02:00.0: setting latency timer to 64
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503097] resource map sanity check conflict: 0x0 0x7fffff 0xa0000 0xbffff PCI Bus 0000:00
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503100] ------------[ cut here ]------------
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503106] WARNING: at /build/buildd/linux-2.6.38/arch/x86/mm/ioremap.c:98 __ioremap_caller+0x387/0x3d0()
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503108] Hardware name: MCP61M-M3
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503109] Info: mapping multiple BARs. Your kernel is fine.
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503110] Modules linked in: nouveau(+) ttm drm_kms_helper drm i2c_algo_bit video vesafb parport_pc ppdev dm_crypt binfmt_misc snd_hda_codec_via snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd psmouse joydev edac_core edac_mce_amd soundcore serio_raw snd_page_alloc k10temp i2c_nforce2 lp parport dm_raid45 xor btrfs zlib_deflate libcrc32c usbhid hid pata_amd forcedeth sata_nv
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503134] Pid: 1438, comm: work_for_cpu Tainted: P        W   2.6.38-8-generic #42-Ubuntu
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503136] Call Trace:
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503140]  [<ffffffff81065cef>] ? warn_slowpath_common+0x7f/0xc0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503143]  [<ffffffff81065de6>] ? warn_slowpath_fmt+0x46/0x50
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503146]  [<ffffffff81040de7>] ? __ioremap_caller+0x387/0x3d0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503160]  [<ffffffffa02b3507>] ? nouveau_load+0xa7/0x550 [nouveau]
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503165]  [<ffffffff815c2cbe>] ? _raw_spin_lock+0xe/0x20
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503168]  [<ffffffff81081282>] ? __alloc_workqueue_key+0x202/0x560
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503170]  [<ffffffff81040e87>] ? ioremap_nocache+0x17/0x20
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503179]  [<ffffffffa02b3507>] ? nouveau_load+0xa7/0x550 [nouveau]
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503190]  [<ffffffffa0251b0e>] ? drm_get_pci_dev+0x18e/0x300 [drm]
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503193]  [<ffffffff81038c79>] ? default_spin_lock_flags+0x9/0x10
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503203]  [<ffffffffa0331cd9>] ? nouveau_pci_probe+0x15/0x17 [nouveau]
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503205]  [<ffffffff8130031f>] ? local_pci_probe+0x5f/0xd0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503208]  [<ffffffff8107ffb0>] ? do_work_for_cpu+0x0/0x30
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503210]  [<ffffffff8107ffc8>] ? do_work_for_cpu+0x18/0x30
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503212]  [<ffffffff810877e6>] ? kthread+0x96/0xa0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503215]  [<ffffffff8100ce24>] ? kernel_thread_helper+0x4/0x10
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503217]  [<ffffffff81087750>] ? kthread+0x0/0xa0
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503219]  [<ffffffff8100ce20>] ? kernel_thread_helper+0x0/0x10
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503221] ---[ end trace de2ce91896c58618 ]---
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503224] [drm] nouveau 0000:02:00.0: Unable to initialize the mmio mapping. Please report your setup to dri-devel@lists.sourceforge.net
Sep 21 10:24:35 infin-MCP61M-M3 kernel: [   15.503548] nouveau: probe of 0000:02:00.0 failed with error -22
Sep 21 10:24:37 infin-MCP61M-M3 kernel: [   17.584649] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
Sep 21 10:24:37 infin-MCP61M-M3 kernel: [   17.586942] EXT4-fs (sda5): re-mounted. Opts: commit=0
Sep 21 10:24:41 infin-MCP61M-M3 kernel: [   22.280029] eth0: no IPv6 routers present
```

lsmod```

Module                  Size  Used by
nouveau               682322  0 
ttm                    76664  1 nouveau
drm_kms_helper         42136  1 nouveau
drm                   227495  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13400  1 nouveau
video                  19438  1 nouveau
vesafb                 13761  1 
parport_pc             36959  0 
ppdev                  17113  0 
dm_crypt               22993  0 
binfmt_misc            17565  1 
snd_hda_codec_via      62470  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  13 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
joydev                 17606  0 
edac_core              53845  0 
edac_mce_amd           23464  0 
soundcore              12680  1 snd
serio_raw              13166  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
k10temp                13119  0 
i2c_nforce2            13058  0 
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
dm_raid45              77827  0 
xor                    12890  1 dm_raid45
btrfs                 550402  0 
zlib_deflate           27074  1 btrfs
libcrc32c              12644  1 btrfs
usbhid                 46956  0 
hid                    91020  1 usbhid
pata_amd               14130  0 
forcedeth              63555  0 
sata_nv                32054  5 
```
Hmm, nouveau is showing up a lot there...maybe because after this OS install I tried nvidia, failed, so tried nouveau, failed, so tried nvidia again (and am failing)?


/usr/lib/nux/unity_support_test -p
```
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: unable to create the OpenGL context
```
Ah..I think this may be something to do with me turning off some compiz settings (after the nvidia drivers failed to work of course, not before)

Is this too much of a mess to easily get the info needed from it?  Should I do a fresh install and post this stuff again?

---

### Post by wildmanne39 on 2011-09-20
Hi, no give me a little while I am researching the error messages.

Also if you turned of compiz, you can not use unity, until it is back on because unity is a plugin in compiz.
Thank you

---

### Post by wildmanne39 on 2011-09-20
Hi, I have been researching and if you are not using the 280.13 driver, I would suggest to go to nvidia and down load it then, deactivate the one in additional drivers.

Also you need to reset unity and compiz to its default setting, and that will also enable Open GL again that you need.

**You might want to reset unity and compiz before you try the new driver from nvidia.**

When you reset unity just let it run for about 3 minutes then restart your computer and do not worry about the error messages, then reset compiz.

Click on the link in my signature the says setting up the cube and effects in 11.04, then on that page go to the bottom of the page and there are directions for resetting unity and restoring compiz to its default settings.
Thank you

---

### Post by MashedUp on 2011-09-20
Ok, will try that ASAP (am not at home right now).

I don't really care about Unity (although I would like to try it to see if I like it).  I want the nvidia drivers to work so I can have 1080p resolution, and (eventually) connect all 3 monitors. At the moment I'm limited to 768p and 1 screen.

I do get the green light in Jockey, and you say this means the drivers are working.  Unfortunately everything still looks exactly like it does without the drivers, and I can't use nvidia-settings because it wants an xorg.cof file with "Drivers nvidia" but and xorg.conf like that means I can boot to the GUI...

How do I find out which driver version I have?  Will the download from nvidia be a binary file that automatically installs the driver?

---

### Post by MashedUp on 2011-09-22
Ok, I've tried the drivers directly from nvidia.

When i ran it, it said the script had failed and asked me if I wanted to continue anyway.

I said yes, and it built the kernel module.  When that finished I got an error (can't remember it exactly) saying that nvidia.ko couldn't be used, and installation had failed.

So I'm still driverless, with no end in sight...?

EDIT: this was on a fresh install of 10.10 (didn't have 11.04 handy)

---

### Post by technosysind on 2011-09-22
Can you paste the screenshot of your additional drivers tab

---

### Post by MashedUp on 2011-09-22
Here is the screenshot...

This is in a fresh install of 10.10 that I have only run the installer from nvidia's site on.

If I try to install through Jockey, when I reboot I will get a green light at the top next to nvidia's driver, but at the bottom it will say it's not active.  I will have either no xorg.conf at all, or one just a couple of lines long, with no "Driver" line.
The desktop will look the same as it does now, and nvidia-settings will fail to run because of xorg.conf.
If I generate a proper xorg.conf, when I reboot it will only boot to the CLI.

---

### Post by technosysind on 2011-09-22
Have you tired installing experimental drivers??

---

### Post by MashedUp on 2011-09-22
Yes, I've tried (not with this fresh install, but one of the 6 or so in the last few days), but didn't get any result different to the nvidia drivers.

---

### Post by technosysind on 2011-09-22
I think you should try Experimental drivers. Everything will work fine except 3D Windows feature in Compiz

---

### Post by wildmanne39 on 2011-09-22
Hi, have you tried the recommended driver in 10.10?

Also do you know if one of your cards is optimus? I do not thinks so but we need to make sure.
Here is a link.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
Thank you

---

### Post by realzippy on 2011-09-22
@wildmanne39

Hi!
What about that output,it stinks,don't you think?
```
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091502] nvidia 0000:02:00.0: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091506] NVRM: This PCI I/O region assigned to your NVIDIA device is invalid:
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091507] NVRM: BAR0 is 0M @ 0x0 (PCI:0000:02:00.0)
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091509] NVRM: The system BIOS may have misconfigured your GPU.
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091541] nvidia: probe of 0000:02:00.0 failed with error -1
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091580] NVRM: The NVIDIA probe routine failed for 1 device(s).
Sep 21 10:24:30 infin-MCP61M-M3 kernel: [   10.091582] NVRM: None of the NVIDIA graphics adapters were initialized!
```

Btw,don't think it is optimus,9300 GS is pretty old.

@MashedUp
Sorry,didn 't loose your other thread/same issue from radar (still subscribed),just had no idea.
Is it possible to disable the 9300 GS in the BIOS ?
Did you plugin any other pci card which could have caused that trouble?

@technosysind
please stop jumping in graphics threads with your "experimental driver" solution.You only confuse people.
At least this one is about nvidia...   ;-)

---

### Post by wildmanne39 on 2011-09-22
Hi realzippy, yes I do, and he has 2 cards, google did not show it as optimus but I just wanted to make sure, the other card is a new one.

He also just reinstalled so I do not not know if those messages still apply.

If you have any ideas, please jump in.
Thank you

---

### Post by realzippy on 2011-09-22
After re-reading [last post of other thread]("http://ubuntuforums.org/showpost.php?p=11268358&postcount=6") ,I noticed that the
9300 GS seems to be a "real" graphics-card;for some reason I thought it was kind of built-in mainboard graphics.
If this is correct (*MashedUp* ? ),why not unplug the card and start with 1 monitor on GT 240 ?

---

### Post by MashedUp on 2011-09-22
Thanks very much guys!

That's all it took - I removed the 9300, and immediately on next reboot I had 1080p (still no drivers installed).
I installed the drivers through Jockey, and they were up and running on reboot, Jockey says they're active, and nvidia-settings works.
I put the 9300 back in, ran nvidia-xconfig, and rebooted. Everything was still fine, but the 9300 is not detected (are cards only detected when the drivers are installed?).

So my problem is solved (how to I change the thread title?) but I have more questions now - how do I detect the 9300/get the 9300 to work? (it worked fine in 10.04, and nvidia says it uses the same driver as the GT240)
Should I make a new thread for those?

---

### Post by realzippy on 2011-09-23
To see if the card is detected,run

```
lspci | grep VGA
```
..there should be both.

If there are both cards seen,
check your xorg.conf..if it is still minimal,try again nvidia-xconfig. (backup old before).
For 2 cards you need 2 "device" sections afaik.

I suggest to start a new thread:
"NVIDIA: 2nd graphics card not detected" or similar titled.
Send me a pm to your new thread...

---

### Post by fractalman on 2011-09-23
You could try through synaptic,

system>administration>synaptic package manager

and search for nvidia-current,  then tick and click apply.

---

### Post by wildmanne39 on 2011-09-23
Hi, I am glad you have part of it working now, I am out of idea's on the rest.
Thank you

---

### Post by MashedUp on 2011-09-23
> **realzippy said:**
> To see if the card is detected,run

```
lspci | grep VGA
```
..there should be both.

If there are both cards seen,
check your xorg.conf..if it is still minimal,try again nvidia-xconfig. (backup old before).
For 2 cards you need 2 "device" sections afaik.

I suggest to start a new thread:
"NVIDIA: 2nd graphics card not detected" or similar titled.
Send me a pm to your new thread...

They both show up there, and this time (not last reboot though) they are both showing in nvidia-settings.

So I guess it's just a matter of playing with xorg.conf, which I am pretty ok with.

Cheers! :D

---

