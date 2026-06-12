---
title: "Ubuntu 14.04 crashes frequently with double monitor"
date: 2015-08-21
forum: New to Ubuntu
---

### Post by cpf624 on 2015-08-21
I am using Ubuntu 14.04 LTS 64-bit, it crashes frequently. And I have double monitor.
After crash, I can goto command line by press CTRL + ALT + F1 for a long time.System resources look normal.
After I kill all application programs, I can goto graphics interface by press CTRL + ALT + F7 for a long time.
I don't known why that's happend.

My common software includes Firefox, Chrome, Eclipse, VMWare Workstation, fcitx sogoupinyin

That is my system info:
```
Linux Jhat-ubuntu 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

That is my PCI info:
```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Q87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
02:00.0 PCI bridge: Texas Instruments XIO2001 PCI Express-to-PCI Bridge
```

That is crash syslog:
```
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.061060] usb 2-1.4: USB disconnect, device number 4Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959058] ------------[ cut here ]------------
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959089] WARNING: CPU: 2 PID: 1378 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959090] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959117] CPU: 2 PID: 1378 Comm: Xorg Tainted: G           OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959118] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959119]  0000000000000009 ffff88040736fc10 ffffffff81765ca1 0000000000000000
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959120]  ffff88040736fc48 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959121]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1800 ffff88040736fc58
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959123] Call Trace:
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959129]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959132]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959134]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959143]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959148]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959156]  [<ffffffffc02b9463>] intel_crtc_disable_planes+0x33/0x1c0 [i915]
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959158]  [<ffffffff8176c1fb>] ? __ww_mutex_lock+0x1b/0x97
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959166]  [<ffffffffc02ba355>] haswell_crtc_disable+0x55/0x2e0 [i915]
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959168]  [<ffffffff8176c732>] ? mutex_lock+0x12/0x2f
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959176]  [<ffffffffc02bad67>] intel_crtc_update_dpms+0x67/0xa0 [i915]
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959183]  [<ffffffffc02bf229>] intel_connector_dpms+0x59/0x70 [i915]
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959193]  [<ffffffffc01fe9cf>] drm_mode_obj_set_property_ioctl+0x39f/0x3b0 [drm]
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959200]  [<ffffffffc01fea10>] drm_mode_connector_property_set_ioctl+0x30/0x40 [drm]
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959205]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959208]  [<ffffffff81211d08>] ? fsnotify+0x228/0x2f0
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959210]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959212]  [<ffffffff811d6d71>] ? __sb_end_write+0x31/0x60
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959213]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959215]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 15:52:51 Jhat-ubuntu kernel: [366569.959216] ---[ end trace 5c832c0d34f10221 ]---
Aug 21 15:52:52 Jhat-ubuntu kernel: [366570.542873] usb 2-1.4: new low-speed USB device number 10 using ehci-pci
Aug 21 15:52:52 Jhat-ubuntu mtp-probe: checking bus 2, device 10: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Aug 21 15:52:52 Jhat-ubuntu mtp-probe: bus: 2, device: 10 was not an MTP device
Aug 21 15:52:52 Jhat-ubuntu kernel: [366570.638869] usb 2-1.4: New USB device found, idVendor=04ca, idProduct=0061
Aug 21 15:52:52 Jhat-ubuntu kernel: [366570.638871] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 21 15:52:52 Jhat-ubuntu kernel: [366570.638872] usb 2-1.4: Product: USB Optical Mouse
Aug 21 15:52:52 Jhat-ubuntu kernel: [366570.638874] usb 2-1.4: Manufacturer: PixArt
Aug 21 15:52:52 Jhat-ubuntu kernel: [366570.641144] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:04CA:0061.0004/input/input15
Aug 21 15:52:52 Jhat-ubuntu kernel: [366570.641237] hid-generic 0003:04CA:0061.0004: input,hidraw0: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.4/input0
Aug 21 15:52:55 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:52:55 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:53:18 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:53:18 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471800] ------------[ cut here ]------------
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471862] WARNING: CPU: 3 PID: 1378 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471865] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471939] CPU: 3 PID: 1378 Comm: Xorg Tainted: G        W  OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471942] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471944]  0000000000000009 ffff88040736fc00 ffffffff81765ca1 0000000000000000
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471949]  ffff88040736fc38 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471953]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1b68 ffff88040736fc48
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471957] Call Trace:
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471970]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471979]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.471984]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472015]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472024]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472053]  [<ffffffffc02c01f9>] intel_crtc_set_config+0x959/0xdb0 [i915]
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472080]  [<ffffffffc01f9401>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472102]  [<ffffffffc01fce49>] drm_mode_setcrtc+0xd9/0x590 [drm]
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472117]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472126]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472131]  [<ffffffff811d6d71>] ? __sb_end_write+0x31/0x60
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472137]  [<ffffffff811d4902>] ? vfs_write+0x172/0x1f0
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472142]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472148]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472151] ---[ end trace 5c832c0d34f10222 ]---
Aug 21 15:55:02 Jhat-ubuntu kernel: [366700.472157] [drm:intel_pipe_set_base] *ERROR* pipe is still busy with an old pageflip
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454091] ------------[ cut here ]------------
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454171] WARNING: CPU: 3 PID: 1378 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454175] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454273] CPU: 3 PID: 1378 Comm: Xorg Tainted: G        W  OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454278] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454281]  0000000000000009 ffff88040736fc00 ffffffff81765ca1 0000000000000000
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454288]  ffff88040736fc38 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454294]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1b68 ffff88040736fc48
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454300] Call Trace:
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454317]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454328]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454335]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454389]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454402]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454449]  [<ffffffffc02c01f9>] intel_crtc_set_config+0x959/0xdb0 [i915]
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454487]  [<ffffffffc01f9401>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454518]  [<ffffffffc01fce49>] drm_mode_setcrtc+0xd9/0x590 [drm]
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454538]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454550]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454556]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454565]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454569] ---[ end trace 5c832c0d34f10223 ]---
Aug 21 15:56:02 Jhat-ubuntu kernel: [366760.454577] [drm:intel_pipe_set_base] *ERROR* pipe is still busy with an old pageflip
Aug 21 15:56:14 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:56:14 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464361] ------------[ cut here ]------------
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464401] WARNING: CPU: 0 PID: 1378 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464402] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464440] CPU: 0 PID: 1378 Comm: Xorg Tainted: G        W  OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464442] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464443]  0000000000000009 ffff88040736fac0 ffffffff81765ca1 0000000000000000
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464445]  ffff88040736faf8 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464447]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1800 ffff88040736fb08
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464450] Call Trace:
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464457]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464462]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464464]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464479]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464485]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464498]  [<ffffffffc02b9463>] intel_crtc_disable_planes+0x33/0x1c0 [i915]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464501]  [<ffffffff8111f164>] ? __delayacct_blkio_end+0x34/0x60
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464513]  [<ffffffffc02ba355>] haswell_crtc_disable+0x55/0x2e0 [i915]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464525]  [<ffffffffc02bbbf7>] __intel_set_mode+0x287/0xa90 [i915]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464537]  [<ffffffffc02bf256>] intel_set_mode+0x16/0x30 [i915]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464549]  [<ffffffffc02c018d>] intel_crtc_set_config+0x8ed/0xdb0 [i915]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464562]  [<ffffffffc01f9401>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464573]  [<ffffffffc01fce49>] drm_mode_setcrtc+0xd9/0x590 [drm]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464581]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464585]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464587]  [<ffffffff811d6d71>] ? __sb_end_write+0x31/0x60
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464589]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464593]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 15:57:02 Jhat-ubuntu kernel: [366820.464594] ---[ end trace 5c832c0d34f10224 ]---
Aug 21 15:58:10 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:10 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:10 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:10 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:10 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:10 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:11 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:11 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:11 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:11 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:11 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:14 Jhat-ubuntu avahi-daemon[1171]: message repeated 2 times: [ Invalid response packet from host 10.237.90.49.]
Aug 21 15:58:14 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:20 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:20 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:21 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:21 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:21 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:21 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:21 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:21 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:21 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:21 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:22 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:22 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:22 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:22 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:22 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:22 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:24 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:24 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:33 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:33 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:38 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:38 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:38 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:39 Jhat-ubuntu avahi-daemon[1171]: message repeated 2 times: [ Invalid response packet from host 10.237.90.49.]
Aug 21 15:58:39 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:39 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:39 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:39 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:39 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:39 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:39 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:42 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:42 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:58:51 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:58:51 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:34 Jhat-ubuntu kernel: [366972.115501] usb 2-1.4: USB disconnect, device number 10
Aug 21 15:59:35 Jhat-ubuntu kernel: [366973.592991] usb 2-1.4: new low-speed USB device number 11 using ehci-pci
Aug 21 15:59:35 Jhat-ubuntu mtp-probe: checking bus 2, device 11: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Aug 21 15:59:35 Jhat-ubuntu kernel: [366973.689121] usb 2-1.4: New USB device found, idVendor=04ca, idProduct=0061
Aug 21 15:59:35 Jhat-ubuntu kernel: [366973.689124] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 21 15:59:35 Jhat-ubuntu kernel: [366973.689125] usb 2-1.4: Product: USB Optical Mouse
Aug 21 15:59:35 Jhat-ubuntu kernel: [366973.689126] usb 2-1.4: Manufacturer: PixArt
Aug 21 15:59:35 Jhat-ubuntu kernel: [366973.691277] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:04CA:0061.0005/input/input16
Aug 21 15:59:35 Jhat-ubuntu kernel: [366973.691370] hid-generic 0003:04CA:0061.0005: input,hidraw0: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.4/input0
Aug 21 15:59:35 Jhat-ubuntu mtp-probe: bus: 2, device: 11 was not an MTP device
Aug 21 15:59:36 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:36 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:36 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:36 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:37 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:37 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:37 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:37 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:37 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:38 Jhat-ubuntu avahi-daemon[1171]: message repeated 2 times: [ Invalid response packet from host 10.237.90.49.]
Aug 21 15:59:38 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:41 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:41 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:47 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:47 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:47 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:47 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:48 Jhat-ubuntu avahi-daemon[1171]: message repeated 2 times: [ Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.]
Aug 21 15:59:48 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:48 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:48 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:48 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:48 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:48 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:49 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:49 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:49 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:49 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 15:59:51 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 15:59:51 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:00:00 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:00:00 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340739] ------------[ cut here ]------------
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340813] WARNING: CPU: 2 PID: 1378 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340817] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340902] CPU: 2 PID: 1378 Comm: Xorg Tainted: G        W  OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340906] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340909]  0000000000000009 ffff88040736fac0 ffffffff81765ca1 0000000000000000
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340914]  ffff88040736faf8 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340919]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1800 ffff88040736fb08
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340924] Call Trace:
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340939]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340948]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340955]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.340993]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341004]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341038]  [<ffffffffc02b9463>] intel_crtc_disable_planes+0x33/0x1c0 [i915]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341070]  [<ffffffffc02ba355>] haswell_crtc_disable+0x55/0x2e0 [i915]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341101]  [<ffffffffc02bbbf7>] __intel_set_mode+0x287/0xa90 [i915]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341133]  [<ffffffffc02bf256>] intel_set_mode+0x16/0x30 [i915]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341163]  [<ffffffffc02c018d>] intel_crtc_set_config+0x8ed/0xdb0 [i915]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341196]  [<ffffffffc01f9401>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341223]  [<ffffffffc01fce49>] drm_mode_setcrtc+0xd9/0x590 [drm]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341243]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341253]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341259]  [<ffffffff811d6d71>] ? __sb_end_write+0x31/0x60
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341267]  [<ffffffff811d4902>] ? vfs_write+0x172/0x1f0
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341272]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341280]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 16:00:42 Jhat-ubuntu kernel: [367040.341283] ---[ end trace 5c832c0d34f10225 ]---
Aug 21 16:01:46 Jhat-ubuntu kernel: [367104.419803] usb 2-1.4: USB disconnect, device number 11
Aug 21 16:01:47 Jhat-ubuntu kernel: [367105.641242] usb 2-1.4: new low-speed USB device number 12 using ehci-pci
Aug 21 16:01:47 Jhat-ubuntu kernel: [367105.737454] usb 2-1.4: New USB device found, idVendor=04ca, idProduct=0061
Aug 21 16:01:47 Jhat-ubuntu kernel: [367105.737456] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 21 16:01:47 Jhat-ubuntu kernel: [367105.737457] usb 2-1.4: Product: USB Optical Mouse
Aug 21 16:01:47 Jhat-ubuntu kernel: [367105.737458] usb 2-1.4: Manufacturer: PixArt
Aug 21 16:01:47 Jhat-ubuntu kernel: [367105.739605] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:04CA:0061.0006/input/input17
Aug 21 16:01:47 Jhat-ubuntu kernel: [367105.739782] hid-generic 0003:04CA:0061.0006: input,hidraw0: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.4/input0
Aug 21 16:01:47 Jhat-ubuntu mtp-probe: checking bus 2, device 12: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Aug 21 16:01:47 Jhat-ubuntu mtp-probe: bus: 2, device: 12 was not an MTP device
Aug 21 16:02:07 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:07 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:07 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:07 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:08 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:08 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:19 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:20 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:20 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:23 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:23 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:29 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:29 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:29 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:29 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: message repeated 2 times: [ Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.]
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:30 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:31 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:31 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:32 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:33 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:33 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:35 Jhat-ubuntu colord: device removed: xrandr-Dell Inc.-DELL U2414H-4CWX754I8ULL
Aug 21 16:02:35 Jhat-ubuntu colord: device removed: xrandr-Dell Inc.-DELL U2414H-4CWX754LARCL
Aug 21 16:02:35 Jhat-ubuntu colord: Profile removed: icc-9e921503dc221f2290e5300c8de41a3b
Aug 21 16:02:35 Jhat-ubuntu colord: Profile removed: icc-4b193b9955fba94620604af2dc1859cf
Aug 21 16:02:36 Jhat-ubuntu gnome-session[2574]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Aug 21 16:02:42 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:02:42 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:02:43 Jhat-ubuntu acpid: client 1378[0:0] has disconnected
Aug 21 16:02:43 Jhat-ubuntu acpid: client connected from 26300[0:0]
Aug 21 16:02:43 Jhat-ubuntu acpid: 1 client rule loaded
Aug 21 16:02:48 Jhat-ubuntu kernel: [367166.711533] device eth0 left promiscuous mode
Aug 21 16:02:48 Jhat-ubuntu kernel: [367166.711618] bridge-eth0: disabled promiscuous mode
Aug 21 16:03:36 Jhat-ubuntu kernel: [367214.204462] usb 2-1.4: USB disconnect, device number 12
Aug 21 16:03:37 Jhat-ubuntu kernel: [367215.681399] usb 2-1.4: new low-speed USB device number 13 using ehci-pci
Aug 21 16:03:37 Jhat-ubuntu kernel: [367215.777994] usb 2-1.4: New USB device found, idVendor=04ca, idProduct=0061
Aug 21 16:03:37 Jhat-ubuntu kernel: [367215.777999] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 21 16:03:37 Jhat-ubuntu kernel: [367215.778002] usb 2-1.4: Product: USB Optical Mouse
Aug 21 16:03:37 Jhat-ubuntu kernel: [367215.778004] usb 2-1.4: Manufacturer: PixArt
Aug 21 16:03:37 Jhat-ubuntu kernel: [367215.780485] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:04CA:0061.0007/input/input18
Aug 21 16:03:37 Jhat-ubuntu kernel: [367215.780715] hid-generic 0003:04CA:0061.0007: input,hidraw0: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.4/input0
Aug 21 16:03:37 Jhat-ubuntu mtp-probe: checking bus 2, device 13: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Aug 21 16:03:37 Jhat-ubuntu mtp-probe: bus: 2, device: 13 was not an MTP device
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363253] ------------[ cut here ]------------
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363333] WARNING: CPU: 7 PID: 26300 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363337] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363433] CPU: 7 PID: 26300 Comm: Xorg Tainted: G        W  OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363437] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363440]  0000000000000009 ffff880404417c00 ffffffff81765ca1 0000000000000000
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363446]  ffff880404417c38 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363452]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1b68 ffff880404417c48
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363458] Call Trace:
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363474]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363485]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363492]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363534]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363546]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363587]  [<ffffffffc02c01f9>] intel_crtc_set_config+0x959/0xdb0 [i915]
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363623]  [<ffffffffc01f9401>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363654]  [<ffffffffc01fce49>] drm_mode_setcrtc+0xd9/0x590 [drm]
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363675]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363686]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363693]  [<ffffffff811d6d71>] ? __sb_end_write+0x31/0x60
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363702]  [<ffffffff811d4902>] ? vfs_write+0x172/0x1f0
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363708]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363716]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363720] ---[ end trace 5c832c0d34f10226 ]---
Aug 21 16:03:43 Jhat-ubuntu kernel: [367221.363729] [drm:intel_pipe_set_base] *ERROR* pipe is still busy with an old pageflip
Aug 21 16:04:38 Jhat-ubuntu kernel: [367275.878193] usb 2-1.4: USB disconnect, device number 13
Aug 21 16:04:39 Jhat-ubuntu kernel: [367277.355165] usb 2-1.4: new low-speed USB device number 14 using ehci-pci
Aug 21 16:04:39 Jhat-ubuntu kernel: [367277.451758] usb 2-1.4: New USB device found, idVendor=04ca, idProduct=0061
Aug 21 16:04:39 Jhat-ubuntu kernel: [367277.451766] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 21 16:04:39 Jhat-ubuntu kernel: [367277.451771] usb 2-1.4: Product: USB Optical Mouse
Aug 21 16:04:39 Jhat-ubuntu kernel: [367277.451774] usb 2-1.4: Manufacturer: PixArt
Aug 21 16:04:39 Jhat-ubuntu kernel: [367277.454548] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:04CA:0061.0008/input/input19
Aug 21 16:04:39 Jhat-ubuntu kernel: [367277.454915] hid-generic 0003:04CA:0061.0008: input,hidraw0: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.4/input0
Aug 21 16:04:39 Jhat-ubuntu mtp-probe: checking bus 2, device 14: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Aug 21 16:04:39 Jhat-ubuntu mtp-probe: bus: 2, device: 14 was not an MTP device
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345531] ------------[ cut here ]------------
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345612] WARNING: CPU: 7 PID: 26300 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345616] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345713] CPU: 7 PID: 26300 Comm: Xorg Tainted: G        W  OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345716] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345719]  0000000000000009 ffff880404417c00 ffffffff81765ca1 0000000000000000
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345725]  ffff880404417c38 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345731]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1b68 ffff880404417c48
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345737] Call Trace:
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345753]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345764]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345771]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345814]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345826]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345866]  [<ffffffffc02c01f9>] intel_crtc_set_config+0x959/0xdb0 [i915]
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345902]  [<ffffffffc01f9401>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345933]  [<ffffffffc01fce49>] drm_mode_setcrtc+0xd9/0x590 [drm]
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345954]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345967]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345973]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345984]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345988] ---[ end trace 5c832c0d34f10227 ]---
Aug 21 16:04:43 Jhat-ubuntu kernel: [367281.345996] [drm:intel_pipe_set_base] *ERROR* pipe is still busy with an old pageflip
Aug 21 16:05:39 Jhat-ubuntu kernel: [367337.551931] usb 2-1.4: USB disconnect, device number 14
Aug 21 16:05:41 Jhat-ubuntu kernel: [367339.028754] usb 2-1.4: new low-speed USB device number 15 using ehci-pci
Aug 21 16:05:41 Jhat-ubuntu kernel: [367339.125244] usb 2-1.4: New USB device found, idVendor=04ca, idProduct=0061
Aug 21 16:05:41 Jhat-ubuntu kernel: [367339.125252] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 21 16:05:41 Jhat-ubuntu kernel: [367339.125257] usb 2-1.4: Product: USB Optical Mouse
Aug 21 16:05:41 Jhat-ubuntu kernel: [367339.125260] usb 2-1.4: Manufacturer: PixArt
Aug 21 16:05:41 Jhat-ubuntu kernel: [367339.128376] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:04CA:0061.0009/input/input20
Aug 21 16:05:41 Jhat-ubuntu kernel: [367339.128930] hid-generic 0003:04CA:0061.0009: input,hidraw0: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.4/input0
Aug 21 16:05:41 Jhat-ubuntu mtp-probe: checking bus 2, device 15: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Aug 21 16:05:41 Jhat-ubuntu mtp-probe: bus: 2, device: 15 was not an MTP device
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.339833] ------------[ cut here ]------------
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.339911] WARNING: CPU: 0 PID: 26300 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.339915] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340013] CPU: 0 PID: 26300 Comm: Xorg Tainted: G        W  OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340017] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340020]  0000000000000009 ffff880404417ac0 ffffffff81765ca1 0000000000000000
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340026]  ffff880404417af8 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340032]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1800 ffff880404417b08
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340038] Call Trace:
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340055]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340066]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340073]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340115]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340128]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340167]  [<ffffffffc02b9463>] intel_crtc_disable_planes+0x33/0x1c0 [i915]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340202]  [<ffffffffc02ba355>] haswell_crtc_disable+0x55/0x2e0 [i915]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340237]  [<ffffffffc02bbbf7>] __intel_set_mode+0x287/0xa90 [i915]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340272]  [<ffffffffc02bf256>] intel_set_mode+0x16/0x30 [i915]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340305]  [<ffffffffc02c018d>] intel_crtc_set_config+0x8ed/0xdb0 [i915]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340341]  [<ffffffffc01f9401>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340372]  [<ffffffffc01fce49>] drm_mode_setcrtc+0xd9/0x590 [drm]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340393]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340405]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340411]  [<ffffffff811d6d71>] ? __sb_end_write+0x31/0x60
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340421]  [<ffffffff811d4902>] ? vfs_write+0x172/0x1f0
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340427]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340435]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 16:05:43 Jhat-ubuntu kernel: [367341.340439] ---[ end trace 5c832c0d34f10228 ]---
Aug 21 16:05:46 Jhat-ubuntu rtkit-daemon[2218]: Successfully made thread 26394 of process 26394 (n/a) owned by '112' high priority at nice level -11.
Aug 21 16:05:46 Jhat-ubuntu rtkit-daemon[2218]: Supervising 1 threads of 1 processes of 1 users.
Aug 21 16:05:47 Jhat-ubuntu rtkit-daemon[2218]: Successfully made thread 26442 of process 26394 (n/a) owned by '112' RT at priority 5.
Aug 21 16:05:47 Jhat-ubuntu rtkit-daemon[2218]: Supervising 2 threads of 1 processes of 1 users.
Aug 21 16:05:47 Jhat-ubuntu rtkit-daemon[2218]: Successfully made thread 26443 of process 26394 (n/a) owned by '112' RT at priority 5.
Aug 21 16:05:47 Jhat-ubuntu rtkit-daemon[2218]: Supervising 3 threads of 1 processes of 1 users.
Aug 21 16:05:47 Jhat-ubuntu rtkit-daemon[2218]: Successfully made thread 26444 of process 26394 (n/a) owned by '112' RT at priority 5.
Aug 21 16:05:47 Jhat-ubuntu rtkit-daemon[2218]: Supervising 4 threads of 1 processes of 1 users.
Aug 21 16:05:47 Jhat-ubuntu rtkit-daemon[2218]: Successfully made thread 26446 of process 26446 (n/a) owned by '112' high priority at nice level -11.
Aug 21 16:05:47 Jhat-ubuntu rtkit-daemon[2218]: Supervising 5 threads of 2 processes of 1 users.
Aug 21 16:05:47 Jhat-ubuntu pulseaudio[26446]: [pulseaudio] pid.c: Daemon already running.
Aug 21 16:05:49 Jhat-ubuntu dbus[840]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Aug 21 16:05:49 Jhat-ubuntu dbus[840]: [system] Successfully activated service 'org.freedesktop.systemd1'
Aug 21 16:06:01 Jhat-ubuntu kernel: [367358.885298] init: tty1 main process ended, respawning
Aug 21 16:06:08 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:06:08 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:06:08 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:06:08 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:06:08 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:06:08 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:06:10 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:06:10 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:06:31 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host fe80::ecb8:d3c6:7bd9:f8a5.
Aug 21 16:06:31 Jhat-ubuntu avahi-daemon[1171]: Invalid response packet from host 10.237.90.49.
Aug 21 16:06:49 Jhat-ubuntu kernel: [367406.902718] usb 2-1.4: USB disconnect, device number 15
Aug 21 16:06:50 Jhat-ubuntu kernel: [367408.379576] usb 2-1.4: new low-speed USB device number 16 using ehci-pci
Aug 21 16:06:50 Jhat-ubuntu kernel: [367408.476211] usb 2-1.4: New USB device found, idVendor=04ca, idProduct=0061
Aug 21 16:06:50 Jhat-ubuntu kernel: [367408.476219] usb 2-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Aug 21 16:06:50 Jhat-ubuntu kernel: [367408.476224] usb 2-1.4: Product: USB Optical Mouse
Aug 21 16:06:50 Jhat-ubuntu kernel: [367408.476227] usb 2-1.4: Manufacturer: PixArt
Aug 21 16:06:50 Jhat-ubuntu kernel: [367408.479157] input: PixArt USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4/2-1.4:1.0/0003:04CA:0061.000A/input/input21
Aug 21 16:06:50 Jhat-ubuntu kernel: [367408.479605] hid-generic 0003:04CA:0061.000A: input,hidraw0: USB HID v1.11 Mouse [PixArt USB Optical Mouse] on usb-0000:00:1d.0-1.4/input0
Aug 21 16:06:50 Jhat-ubuntu mtp-probe: checking bus 2, device 16: "/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.4"
Aug 21 16:06:50 Jhat-ubuntu mtp-probe: bus: 2, device: 16 was not an MTP device
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155243] ------------[ cut here ]------------
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155307] WARNING: CPU: 5 PID: 26300 at /build/linux-lts-utopic-AIjdaQ/linux-lts-utopic-3.16.0/drivers/gpu/drm/i915/intel_display.c:3324 intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]()
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155310] Modules linked in: uas usb_storage btrfs xor raid6_pq ufs qnx4 hfsplus hfs minix ntfs msdos jfs xfs libcrc32c vmnet(OE) bnep rfcomm bluetooth vmw_vsock_vmci_transport 6lowpan_iphc vsock vmw_vmci vmmon(OE) dm_crypt snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi snd_hda_intel snd_hda_controller snd_hda_codec snd_hwdep snd_pcm intel_rapl mei_me x86_pkg_temp_thermal intel_powerclamp snd_seq_midi snd_seq_midi_event coretemp snd_rawmidi kvm_intel snd_seq kvm snd_seq_device snd_timer snd crct10dif_pclmul crc32_pclmul ghash_clmulni_intel soundcore aesni_intel mei dcdbas aes_x86_64 lrw lpc_ich gf128mul shpchp serio_raw mac_hid glue_helper ablk_helper cryptd parport_pc ppdev lp parport hid_generic usbhid hid i915 i2c_algo_bit drm_kms_helper drm e1000e psmouse ahci ptp libahci pps_core video
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155382] CPU: 5 PID: 26300 Comm: Xorg Tainted: G        W  OE 3.16.0-45-generic #60~14.04.1-Ubuntu
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155385] Hardware name: Dell Inc. OptiPlex 9020/03CPWF, BIOS A11 04/01/2015
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155387]  0000000000000009 ffff880404417ac0 ffffffff81765ca1 0000000000000000
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155392]  ffff880404417af8 ffffffff8106de3d 0000000000000000 ffff8804083d0000
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155396]  ffff880402dc8238 ffff8800da3b1800 ffff8800da3b1800 ffff880404417b08
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155400] Call Trace:
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155412]  [<ffffffff81765ca1>] dump_stack+0x45/0x56
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155420]  [<ffffffff8106de3d>] warn_slowpath_common+0x7d/0xa0
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155425]  [<ffffffff8106df1a>] warn_slowpath_null+0x1a/0x20
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155456]  [<ffffffffc02b69a1>] intel_crtc_wait_for_pending_flips+0x171/0x180 [i915]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155465]  [<ffffffff810b50b0>] ? prepare_to_wait_event+0x100/0x100
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155492]  [<ffffffffc02b9463>] intel_crtc_disable_planes+0x33/0x1c0 [i915]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155517]  [<ffffffffc02ba355>] haswell_crtc_disable+0x55/0x2e0 [i915]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155543]  [<ffffffffc02bbbf7>] __intel_set_mode+0x287/0xa90 [i915]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155568]  [<ffffffffc02bf256>] intel_set_mode+0x16/0x30 [i915]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155592]  [<ffffffffc02c018d>] intel_crtc_set_config+0x8ed/0xdb0 [i915]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155619]  [<ffffffffc01f9401>] drm_mode_set_config_internal+0x61/0xe0 [drm]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155643]  [<ffffffffc01fce49>] drm_mode_setcrtc+0xd9/0x590 [drm]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155658]  [<ffffffffc01ed9ec>] drm_ioctl+0x1ec/0x660 [drm]
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155667]  [<ffffffff811e7670>] do_vfs_ioctl+0x2e0/0x4c0
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155672]  [<ffffffff811d6d71>] ? __sb_end_write+0x31/0x60
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155678]  [<ffffffff811d4902>] ? vfs_write+0x172/0x1f0
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155683]  [<ffffffff811e78d1>] SyS_ioctl+0x81/0xa0
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155689]  [<ffffffff8176e34d>] system_call_fastpath+0x1a/0x1f
Aug 21 16:07:02 Jhat-ubuntu kernel: [367420.155692] ---[ end trace 5c832c0d34f10229 ]---
Aug 21 16:07:25 Jhat-ubuntu NetworkManager[1216]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.183': no such name
Aug 21 16:07:25 Jhat-ubuntu NetworkManager[1216]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.183': no such name
Aug 21 16:07:28 Jhat-ubuntu dbus[840]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Aug 21 16:07:28 Jhat-ubuntu dbus[840]: [system] Successfully activated service 'org.freedesktop.systemd1'
Aug 21 16:07:29 Jhat-ubuntu rtkit-daemon[2218]: Successfully made thread 26822 of process 26822 (n/a) owned by '1000' high priority at nice level -11.
```

---

