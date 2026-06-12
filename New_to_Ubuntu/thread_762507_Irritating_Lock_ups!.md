---
title: "Irritating Lock ups!"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by aimpau on 2008-04-22
I had my 3rd STRAIGHT xubuntu Gutsy lock just 15mins ago! What's happening??? I've installed all updates and I though ubuntu was stable.

I check the syslog and look what I found:

Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.017890] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_2'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.021066] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_6330'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.024160] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_964'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.025907] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.026573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.027192] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_device_lun0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.027884] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.028521] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.029138] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.029759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.030379] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7001'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.030986] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.031587] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_0_if0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.032212] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7001_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.032825] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_1'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.033479] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_1_if0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.034139] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7001_1'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.034759] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_2'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.035366] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_2_if0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.036476] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.037330] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.037955] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7002'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.038560] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_3'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.039160] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_3_if0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.039774] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_900'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.040434] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_180'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.041044] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1057_3052'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.041646] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_1100'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.042244] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_1101'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.042837] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_1102'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.043429] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1022_1103'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.044045] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_eisa_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.044654] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.045245] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.045835] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.046430] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_AUX_port'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.047067] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.047716] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_serial8250'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.048337] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c01'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.048970] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0a03'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.049573] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c02'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.050156] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0200'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.050734] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0b00'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.051314] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0800'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.051918] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0c04'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.052507] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0700'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.053088] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.053669] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.054298] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0400'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.054889] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0303'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.055466] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.056088] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_if0_logicaldev_input'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.056674] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_pcspkr_logicaldev_input'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.057246] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/net_00_15_58_45_7d_1a'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.084208] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_scsi_device_lun0_scsi_generic'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.085053] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0_scsi_generic'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.085671] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_5513_scsi_host_0_scsi_device_lun0_0_scsi_generic'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.086249] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012_oss_pcm_1'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.086821] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012_oss_pcm_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.087396] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012_alsa_control__1'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.088043] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012_oss_pcm_0_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.088692] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012_oss_mixer__1'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.089284] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012_alsa_capture_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.089856] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012_alsa_playback_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.090418] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1039_7012_alsa_capture_1'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.090984] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_sequencer'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.091545] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.092131] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_oss_sequencer_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.092697] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_alsa_timer'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.093258] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.093864] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.094446] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.095022] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_1'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.095594] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/computer'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.096188] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pnp_PNP0501_0_serial_platform_1'). 
Apr 22 17:22:28 paulo-desktop kernel: [   71.749570] ppdev: user-space parallel port driver
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.153248] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1057_3052_serial_platform_2'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.245256] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1057_3052_serial_platform_3'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.286154] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_0_usbraw'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.286772] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_1_usbraw'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.287348] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_2_usbraw'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.287937] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_62a_0_noserial_usbraw'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.288564] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_0_0_0000_00_03_3_usbraw'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.353409] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_floppy_0_storage'). 
Apr 22 17:22:28 paulo-desktop kernel: [   71.969863] audit(1208856148.001:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4598 profile="/usr/sbin/cupsd"
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.386457] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_QUANTUM_FIREBALLlct15_15_612020817051'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.392801] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_1e77df68_7cd0_4845_9905_d3246a7fe343'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.430781] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_part2_size_1024'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.436638] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_81109867_3647_42f4_985b_de29b4283397'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.448817] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_1ATA_ST380215A_9QZ0BF7D'). 
Apr 22 17:22:28 paulo-desktop kernel: [   72.052517] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Apr 22 17:22:28 paulo-desktop kernel: [   72.052522] apm: overridden by ACPI.
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.532476] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_745CD7435CD6FF34'). 
Apr 22 17:22:28 paulo-desktop dhcdbd: Started up.
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.745461] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_CPU0'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.748910] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/acpi_FAN'). 
Apr 22 17:22:28 paulo-desktop NetworkManager: <debug> [1208856148.749927] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CD/DVDW_SH_S182M'). 
Apr 22 17:22:28 paulo-desktop avahi-daemon[4561]: Server startup complete. Host name is paulo-desktop.local. Local service cookie is 3262335566.
Apr 22 17:22:30 paulo-desktop anacron[4751]: Anacron 2.3 started on 2008-04-22
Apr 22 17:22:30 paulo-desktop anacron[4751]: Normal exit (0 jobs run)
Apr 22 17:22:30 paulo-desktop /usr/sbin/cron[4778]: (CRON) INFO (pidfile fd = 3)
Apr 22 17:22:30 paulo-desktop /usr/sbin/cron[4779]: (CRON) STARTUP (fork ok)
Apr 22 17:22:30 paulo-desktop /usr/sbin/cron[4779]: (CRON) INFO (Running @reboot jobs)
Apr 22 17:22:37 paulo-desktop kernel: [   81.026560] eth0: no IPv6 routers present
Apr 22 17:22:55 paulo-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
[B]Apr 22 17:22:55 paulo-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..
[/B]

The bold entry is the one right before my xubuntu freeze up. Fortunately xfmedia still played on. But everything hangs and no amount of keyboard shortcut express can unfreeze it. The mouse and monitor still works though including the CPU fan.

What I did:
As I'm typing I opened my network properties and deleted in the hosts tab everything that has the tag ip6. I also disabled the autostart feature of networkmanager. I'm going to open Gimp, Firefox and Xfmedia and see what happens. I have 1.73Ghz AMD Sempron, 512RAM.

Please help.

---

### Post by aimpau on 2008-04-22
Another ultra lock up. This time the debug lines started appearing once again but without the last line. My last lines this time are:

Apr 22 23:12:53 paulo-desktop ntpdate[4720]: no servers can be used, exiting
Apr 22 23:12:54 paulo-desktop anacron[4751]: Anacron 2.3 started on 2008-04-22
Apr 22 23:12:54 paulo-desktop anacron[4751]: Normal exit (0 jobs run)
Apr 22 23:12:54 paulo-desktop /usr/sbin/cron[4778]: (CRON) INFO (pidfile fd = 3)
Apr 22 23:12:54 paulo-desktop /usr/sbin/cron[4779]: (CRON) STARTUP (fork ok)
Apr 22 23:12:54 paulo-desktop /usr/sbin/cron[4779]: (CRON) INFO (Running @reboot jobs)
Apr 22 23:12:55 paulo-desktop avahi-daemon[4512]: Registering new address record for fe80::215:58ff:fe45:7d1a on eth0.*.
Apr 22 23:13:04 paulo-desktop kernel: [   63.800734] eth0: no IPv6 routers present
Apr 22 23:17:01 paulo-desktop /USR/SBIN/CRON[4989]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

Anacron is something like you can desync your time and it's ok with ubuntu. I believe time is one of the key aspects of Linux as the sudo command is dependent on this. Before the lock up, I was doing the ff:

1. staring at my desktop
2. I opened firefox..so far so good..
3. I opened Travian (a browser game) and ubuntuforums.org at the same time on different tabs.
4. this is where FF started acting strange and in a few seconds, BAM! lock up galore.

However, I think this time, I may have been given the clue and it is with regards Anacron. You see, in the browser game travian, I actually changed my real timezone (UTC+8) to UTC-5 to accomodate our international players. So probably, that's what causes the lock up.

Just now:
AHA! It is Anacron. I can't explain it all but if any knowledgeable Linux evangelist is around, please read through my problem and enter this:

**man anacron**

and read through it all.

Things I will do:
1. Change my system time to floating.
2. Check out more of this "Anacron".

Will report back.

[e]
Wasn't able to change the time to floating. Can anyone help me out on this one?

Also, I've done some reading on this Anacron and what I did was to delete all of my timestamps (though I made a backup). We'll see what will happen.

---

### Post by aimpau on 2008-04-22
My first boot..and no lock ups! :) Problem Solved!

I'll be posting a simple tutorial on how to prevent "lock ups" just after boot up.

Woohoo! It really feels good when you managed to solve something. :)

---

### Post by aimpau on 2008-04-23
Ok, I stand corrected. Yup, there are no more lockups but my screen gets a "lasting" effect. This means that when I open a certain program and close it, the graphic won't go away and it just stays there. Though I can move my mouse and click almost everything including shutdown, it still bugs me why is this happening.

Regarding the "tutorial"

try removing the cron timestamps

```

sudo rm -r /var/spool/anacron/*

```

Can someone please help me? I've been mono-posting here without even someone lending me a hand...please?

Thanks!

---

### Post by prshah on 2008-04-23
> **aimpau said:**
> 
Can someone please help me? I've been mono-posting here without even someone lending me a hand...please?


Pity post; ie, it is of no real use to you, feel free to ignore the rest.

Just wanted to tell you that I have read your thread with interest, but since:

a) I dont know what trevian is
b) I dont know what anacron is
c) I have only a vague idea of cron
d) I have no lockups whatsoever

I can be of know help other than to tell you that I wish I could help.

---

### Post by aimpau on 2008-04-23
Thank you.

I'm using xubuntu by the way.

---

### Post by sowelie on 2008-04-23
What are you using for a video card and driver?

---

### Post by aimpau on 2008-04-23
Supposedly, its a SIS760 Mirage integrated chip. However, xubuntu decided to use SIS Real256 for it.

---

### Post by sowelie on 2008-04-23
So, I'm assuming you're not using desktop effects right?

---

### Post by aimpau on 2008-04-23
Nope. I'm after efficiency.

The error occurs during a fresh boot up. However, once restarted the error is gone.

Hmmmm...As I'm typing to you, this is a fresh boot up and the first thing I did was to open a terminal and type

```

sudo -K

```

and so far, no problem. Still observing and experimenting.

Just a side question, in Application>>Setting>>Login Window, what's the GTKRC file for?

[edit]
Also, before shutting down yesterday, I open Application>>Setting>>Autostarted Applications and unchecked:

Restricted Drivers (which detect if I need them)

---

### Post by sowelie on 2008-04-24
I'm not sure what the gtkrc is exactly, but I know it has something to do with themes.  Are you still experiencing the lock ups?  Have you upgraded to hardy?

---

### Post by aimpau on 2008-04-25
Im still on Gutsy, but I think I might have solve the problem!:)

The only thing I did was to uncheck Restricted Drivers in Applications>>Settings>>Autostarted applications. Since I've already saved my video chip's profile, it is no longer necessary for xubuntu to always check for restricted drivers (in my case, the only thing that's restricted was the video chip).

No more lock ups! :)

Thanks for bearing with me! :)

Oh, just to add, the lock up began AFTER I installed all the gutsy security and other updates.

---

### Post by muteXe on 2008-04-25
> **prshah said:**
> 
Just wanted to tell you that I have read your thread with interest, but since:

a) I dont know what trevian is
b) I dont know what anacron is
c) I have only a vague idea of cron
d) I have no lockups whatsoever

I can be of know help other than to tell you that I wish I could help.

I'm sorry, but that was the point of that post?

If you use cron to schedule something to happen, and your machine is off when that time arrives, then it will not happen.  Using anacron instead of cron means that it will next execute when the machine is switched on, even though it's later than the time you told it to happen at.

---

### Post by aimpau on 2008-04-25
Ok. I SIT corrected. The lock ups still persist.

And I think this is the culprit:
Syslog:

Apr 26 11:17:01 paulo-desktop /USR/SBIN/CRON[4934]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

This is the last line before the restart mark.

How can I disable cron? Also, I've noticed in the services dialog, anacron and atd are supposedly scheduling programs that executes programs scheduled. Should I deacitvate both or just anacron? What are the side effects of disabling anacron? cron? How essential are they?

I'm so challenge at this problem, I'll make it one of my year's goals.

Thanks everyone!

---

### Post by wthoang on 2008-04-26
yeh...as uve seen on my post..im having the same problem...can i just ask wat comp ure using...this is only happening on my IBM...all my macs have no problem with this.

---

### Post by aimpau on 2008-04-26
AMD Sempron.

Here's what I did so far:

Uninstall cron.
Deactivated anacron startup.

Here's my last line in the syslog before lock up:

Apr 27 02:03:25 paulo-desktop kernel: [   62.376304] eth0: no IPv6 routers present

Can anyone help us? I'm a fresh noob coming from XP and would really like some guidance.

Thanks!

---

### Post by GoCool on 2008-04-26
> Apr 27 02:03:25 paulo-desktop kernel: [ 62.376304] eth0: no IPv6 routers present
This shouldnt be a cause of concern, its the new ip standard, check if its showing any errors with IPv4 which is universal.

> Apr 26 11:17:01 paulo-desktop /USR/SBIN/CRON[4934]: (root) CMD ( cd / && run-parts --report /etc/cron.hourly)
Even this shouldnt be a cause of concern, this just let's you know about the cron as such.

And may I know how your cronjob looks like? I just want the contents in it.

---

### Post by aimpau on 2008-04-27
I've already uninstalled my cron so there isn't any cronjob but I've managed to look at it before and it just shows nothing (other than the usual markings).

Also, the lock ups usually occur during a fresh boot and when I'm on FF. I remove the ubuntu extension in FF but still, it persist.

---

### Post by aimpau on 2008-04-27
found this link:

[http://ubuntuforums.org/showthread.php?t=745093](http://ubuntuforums.org/showthread.php?t=745093)

---

### Post by incandenza on 2008-04-27
Just a suggestion, but I think the cron stuff may be a red herring here.  If I look at my syslog at any random time, the last lines will almost always have something to do with cron.  I don't think it has anything to do with your lockups.

---

### Post by aimpau on 2008-04-28
I unistalled it anyway and doesn't effect anything. I tried the link above and yep, I don't experience any lock up so far. This is my 2nd fresh boot.


[e]
Got two consecutive lock ups.

1. I was logging in here, then BOOM.

2. After restart, I was resizing Pidgin chat window, then BOOM


What's wrong with xubuntu???

---

