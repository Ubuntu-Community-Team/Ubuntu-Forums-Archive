---
title: "Ubuntu goes to some sort of kernel while locked"
date: 2021-10-06
forum: New to Ubuntu
---

### Post by flyingminds on 2021-10-06
Hello, I am really new to Ubuntu and Linux in general.
Recently (I don't know if it's connected to some sort of software updates) I experience some strange issues.
Sometimes I leave my laptop locked for a while (between 20 minutes and an hour) and when I come back it has already loaded some sort of kernel (I've read about panic kernels but I don't know if that's the case).
It's really annoying since I cannot go back to my work and I have to reboot manually because I cannot type any commands or perform any actions whatsoever. Because of that I cannot show you the exact output but last time I saw that the last line said:

interrupt took too long(2505 > 2500) lowering kernel.perf_even_max_sample_rate to 79750 (I've read it had something to do with CPU performance).

On the upper lines there was something about packages involved. I also saw "nvidia" in a few lines. With previous versions I've had issues with nvidia drivers but after a fresh install of 20.04.3 LTS I am using the recommended one and I've had no issues so far (or at least I thought so).
First visible lines said something about RAX, RDX, RBP.

I would really love to have some advise because it's really frustrating to have to reboot my system every time this happens.

P.S. I am not completely sure that it doesn't happen only after I unplug my charger (not immediately, like I said it takes from 20 minutes to 1 hour).

Please HELP! :(

I am using an Asus laptop with this configuration:

Intel® Core™ i7-7500U CPU @ 2.70GHz × 4
8 GB RAM
NVIDIA Corporation GM108M [GeForce 940MX] / NVIDIA GeForce 940MX/PCIe/SSE2

---

### Post by grahammechanical on 2021-10-06
> I leave my laptop locked

What does that mean? Do you log out? Do you shut the lid? Do you select suspend? The kernel is always loaded even when we choose log out or suspend. It is the kernel that does the log out or suspend. The only time the kernel is not loaded is when we power off the computer.

On my desktop machine when I power off the OS there is still power going to the motherboard. I wonder what happens to a laptop that is suspended and the charger is disconnected and the battery state gets too low for the kernel to operate?

I found this information. The web page is all about debugging kernel suspend and is very complicated. At least I think so.

> Suspend and resume use facilities within your BIOS called ACPI, or  Advanced Configuration and Power Interface. Linux provides an ACPI  subsystem that manages the suspend and resume process. Usually problems  occur when resuming, and normally the culprit is a device driver that  does not recover from a powered down state. If your computer  successfully performs a suspend, then it is quite likely any resume  problems are due to another device driver and not the ACPI subsystem. 

And then there is this.

[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)

Regards

---

### Post by Doug S on 2021-10-06
> **flyingminds said:**
> interrupt took too long(2505 > 2500) lowering kernel.perf_even_max_sample_rate to 79750 (I've read it had something to do with CPU performance).The interrupt took too long message by itself is not too much of a concern.

---

### Post by flyingminds on 2021-10-11
I meant I leave my laptop locked and with the lid closed. Last time that happened I took a picture before rebooting manually.
Here's what I could capture.
[ATTACH=CONFIG]289266[/ATTACH]

---

### Post by Doug S on 2021-10-11
That information should also be in the /var/log/kern.log file. Find the beginning of the log entries and copy and paste its entirety herein.

---

### Post by flyingminds on 2021-10-11
```
Oct 11 14:35:49 elena-UX410UQK kernel: [18882.768174] wlp2s0: deauthenticating from 8c:04:ff:bd:a1:02 by local choice (Reason: 3=DEAUTH_LEAVING)
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.624434] rfkill: input handler enabled
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633804] BUG: kernel NULL pointer dereference, address: 0000000000000000
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633858] #PF: supervisor write access in kernel mode
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633883] #PF: error_code(0x0002) - not-present page
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633906] PGD 0 P4D 0 
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633921] Oops: 0002 [#1] SMP PTI
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633939] CPU: 2 PID: 8188 Comm: nvidia-sleep.sh Tainted: P           OE     5.11.0-37-generic #41~20.04.2-Ubuntu
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633982] Hardware name: ASUSTeK COMPUTER INC. UX410UQK/UX410UQK, BIOS UX410UQK.306 08/08/2017
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634018] RIP: 0010:_raw_q_schedule+0x40/0x70 [nvidia_uvm]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634071] Code: 89 fb 4c 89 ef e8 40 4a a5 fc 48 89 c6 49 8b 04 24 49 39 c4 75 31 48 8b 43 08 4c 89 63 08 4c 89 ef 49 89 1c 24 49 89 44 24 08 <4c> 89 20 e8 28 48 a5 fc 48 8d 7b 18 e8 af 28 f6 fb b8 01 00 00 00
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634147] RSP: 0018:ffffa12401de3ce8 EFLAGS: 00010046
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634178] RAX: 0000000000000000 RBX: ffffa12401905d38 RCX: 0000000000000001
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634218] RDX: 0000000000000001 RSI: 0000000000000246 RDI: ffffa12401905d48
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634256] RBP: ffffa12401de3d00 R08: 0000000000000000 R09: 0000000000000001
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634288] R10: 0000000000000000 R11: 0000000000000000 R12: ffffa12401de3d10
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634320] R13: ffffa12401905d48 R14: ffff903844e3ad20 R15: 0000000000000000
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634355] FS:  00007ff10ed0b740(0000) GS:ffff9039a6d00000(0000) knlGS:0000000000000000
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634387] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634402] CR2: 0000000000000000 CR3: 00000001aaa16002 CR4: 00000000003706e0
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634418] Call Trace:
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634429]  _raw_q_flush+0x66/0x90 [nvidia_uvm]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634472]  ? _raw_q_flush+0x90/0x90 [nvidia_uvm]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634514]  nv_kthread_q_flush+0x1a/0x70 [nvidia_uvm]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634559]  uvm_suspend+0x78/0x150 [nvidia_uvm]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634604]  uvm_suspend_entry+0x66/0x80 [nvidia_uvm]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634650]  ? down+0x33/0x60
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634665]  nv_uvm_suspend+0x33/0x50 [nvidia]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635031]  nv_set_system_power_state+0x2d9/0x3c0 [nvidia]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635246]  nv_procfs_write_suspend+0xe7/0x140 [nvidia]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635503]  proc_reg_write+0x66/0x90
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635516]  vfs_write+0xca/0x280
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635527]  ksys_write+0x67/0xe0
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635538]  __x64_sys_write+0x1a/0x20
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635549]  do_syscall_64+0x38/0x90
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635560]  entry_SYSCALL_64_after_hwframe+0x44/0xa9
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635575] RIP: 0033:0x7ff10ee1f1e7
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635609] Code: 64 89 02 48 c7 c0 ff ff ff ff eb bb 0f 1f 80 00 00 00 00 f3 0f 1e fa 64 8b 04 25 18 00 00 00 85 c0 75 10 b8 01 00 00 00 0f 05 <48> 3d 00 f0 ff ff 77 51 c3 48 83 ec 28 48 89 54 24 18 48 89 74 24
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635666] RSP: 002b:00007ffc284d1b88 EFLAGS: 00000246 ORIG_RAX: 0000000000000001
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635696] RAX: ffffffffffffffda RBX: 0000000000000008 RCX: 00007ff10ee1f1e7
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635713] RDX: 0000000000000008 RSI: 0000562204dbcb20 RDI: 0000000000000001
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635730] RBP: 0000562204dbcb20 R08: 000000000000000a R09: 0000000000000007
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635746] R10: 00005622036a1017 R11: 0000000000000246 R12: 0000000000000008
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635762] R13: 00007ff10eefa6a0 R14: 00007ff10eefb4a0 R15: 00007ff10eefa8a0
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635780] Modules linked in: rfcomm vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) ccm cmac algif_hash algif_skcipher af_alg bnep nls_iso8859_1 nvidia_uvm(PO) nvidia_drm(PO) nvidia_modeset(PO) snd_hda_codec_hdmi snd_hda_codec_generic ledtrig_audio nvidia(PO) x86_pkg_temp_thermal intel_powerclamp coretemp snd_soc_skl snd_soc_hdac_hda snd_hda_ext_core snd_soc_sst_ipc snd_soc_sst_dsp snd_soc_acpi_intel_match snd_soc_acpi snd_hda_intel snd_intel_dspcfg soundwire_intel soundwire_generic_allocation soundwire_cadence snd_hda_codec snd_hda_core snd_hwdep soundwire_bus snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine uvcvideo videobuf2_vmalloc videobuf2_memops snd_pcm videobuf2_v4l2 videobuf2_common kvm_intel videodev mei_hdcp snd_seq_midi intel_rapl_msr snd_seq_midi_event mc kvm snd_rawmidi usbhid iwlmvm crct10dif_pclmul mac80211 ghash_clmulni_intel snd_seq libarc4 aesni_intel snd_seq_device crypto_simd iwlwifi snd_timer cryptd intel_xhci_usb_role_switch i915 joydev input_leds glue_helper rapl
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.635822]  snd intel_cstate serio_raw drm_kms_helper btusb processor_thermal_device btrtl cec cfg80211 btbcm wmi_bmof asus_nb_wmi efi_pstore soundcore btintel processor_thermal_rfim rc_core i2c_algo_bit processor_thermal_mbox bluetooth mxm_wmi mei_me processor_thermal_rapl fb_sys_fops mei hid_multitouch intel_rapl_common syscopyarea sysfillrect ecdh_generic ecc sysimgblt intel_soc_dts_iosf intel_pch_thermal int3403_thermal int340x_thermal_zone acpi_pad acpi_als kfifo_buf industrialio int3400_thermal mac_hid asus_wireless acpi_thermal_rel sch_fq_codel msr parport_pc ppdev lp parport drm ip_tables x_tables autofs4 hid_generic mfd_aaeon asus_wmi i2c_i801 ahci i2c_hid sparse_keymap i2c_smbus libahci xhci_pci xhci_pci_renesas hid intel_lpss_pci intel_lpss crc32_pclmul idma64 virt_dma wmi video
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.636255] CR2: 0000000000000000
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.636272] ---[ end trace 0de8e03baf061ff7 ]---
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755004] RIP: 0010:_raw_q_schedule+0x40/0x70 [nvidia_uvm]
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755069] Code: 89 fb 4c 89 ef e8 40 4a a5 fc 48 89 c6 49 8b 04 24 49 39 c4 75 31 48 8b 43 08 4c 89 63 08 4c 89 ef 49 89 1c 24 49 89 44 24 08 <4c> 89 20 e8 28 48 a5 fc 48 8d 7b 18 e8 af 28 f6 fb b8 01 00 00 00
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755138] RSP: 0018:ffffa12401de3ce8 EFLAGS: 00010046
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755164] RAX: 0000000000000000 RBX: ffffa12401905d38 RCX: 0000000000000001
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755192] RDX: 0000000000000001 RSI: 0000000000000246 RDI: ffffa12401905d48
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755219] RBP: ffffa12401de3d00 R08: 0000000000000000 R09: 0000000000000001
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755247] R10: 0000000000000000 R11: 0000000000000000 R12: ffffa12401de3d10
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755275] R13: ffffa12401905d48 R14: ffff903844e3ad20 R15: 0000000000000000
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755304] FS:  00007ff10ed0b740(0000) GS:ffff9039a6d00000(0000) knlGS:0000000000000000
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755336] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.755360] CR2: 0000000000000000 CR3: 00000001aaa16002 CR4: 00000000003706e0
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.776636] iwlwifi 0000:02:00.0: Applying debug destination EXTERNAL_DRAM
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.957359] iwlwifi 0000:02:00.0: Applying debug destination EXTERNAL_DRAM
Oct 11 14:35:50 elena-UX410UQK kernel: [18884.045449] iwlwifi 0000:02:00.0: FW already configured (0) - re-configuring
Oct 11 14:35:54 elena-UX410UQK kernel: [18887.863135] wlp2s0: authenticate with 8c:04:ff:bd:a1:02
Oct 11 14:35:54 elena-UX410UQK kernel: [18887.873947] wlp2s0: send auth to 8c:04:ff:bd:a1:02 (try 1/3)
Oct 11 14:35:54 elena-UX410UQK kernel: [18887.882249] wlp2s0: authenticated
Oct 11 14:35:54 elena-UX410UQK kernel: [18887.887918] wlp2s0: associate with 8c:04:ff:bd:a1:02 (try 1/3)
Oct 11 14:35:54 elena-UX410UQK kernel: [18887.894163] wlp2s0: RX AssocResp from 8c:04:ff:bd:a1:02 (capab=0x1411 status=0 aid=2)
Oct 11 14:35:54 elena-UX410UQK kernel: [18887.902281] wlp2s0: associated
Oct 11 14:35:54 elena-UX410UQK kernel: [18887.943764] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
Oct 11 14:35:54 elena-UX410UQK kernel: [18888.096858] wlp2s0: Limiting TX power to 20 (20 - 0) dBm as advertised by 8c:04:ff:bd:a1:02
Oct 11 14:36:20 elena-UX410UQK kernel: [18913.187934] wlp2s0: deauthenticating from 8c:04:ff:bd:a1:02 by local choice (Reason: 3=DEAUTH_LEAVING)
```

---

### Post by Doug S on 2021-10-11
> **flyingminds said:**
> Oct 11 14:35:49 elena-UX410UQK kernel: [18882.768174] wlp2s0: deauthenticating from 8c:04:ff:bd:a1:02 by local choice (Reason: 3=DEAUTH_LEAVING)
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.624434] rfkill: input handler enabled
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633804] BUG: kernel NULL pointer dereference, address: 0000000000000000
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633858] #PF: supervisor write access in kernel mode
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633883] #PF: error_code(0x0002) - not-present page
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633906] PGD 0 P4D 0 
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633921] Oops: 0002 [#1] SMP PTI
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633939] CPU: 2 PID: 8188 Comm: nvidia-sleep.sh [COLOR="#FF0000"]Tainted: P           OE[/COLOR]     5.11.0-37-generic #41~20.04.2-Ubuntu
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.633982] Hardware name: ASUSTeK COMPUTER INC. UX410UQK/UX410UQK, BIOS UX410UQK.306 08/08/2017
Oct 11 14:35:50 elena-UX410UQK kernel: [18883.634018] RIP: 0010:_raw_q_schedule+0x40/0x70 [[COLOR="#FF0000"]nvidia_uvm[/COLOR]]
The taint flags are Proprietary, Externally built, Unsigned module loaded.  Likely some nvidia kernel module.

I'm a server person and no help with nvidia stuff, but luckily there are many around that do know about the endless nvidia issues that might be able to help.

---

### Post by deniercountess on 2022-03-08
Guess - as said - it is not an Ubuntu 20.04 problem. I only paste the content of my screen of death that may help to find a way toward the reason for this behaviour when computer suspends by energy saving settings. This problem never occured by manually suspending:

Hardware:  [GeForce GTX 960M] / Mesa Intel® HD Graphics 620
Driver: NVIDIA Server Driver metapackage from nvidia-driver-470-server (proprietary)

```
===BEGIN===

(14576.950392] <TASK>
[14576.950408) _raw_q_flush+0x66/0x90 [nvidia_uvm)
(14576.950475) ? _raw_q_flush+0x90/0x90 [nvidia_uvm]
[14576.950536] nv_kthread_q_flush+0x1a/0x70 [nvidia_uvm)
[14576.950601) uvm_suspend+0x80/0x160 [nvidia_uvm]
[14576.950666) uvm_suspend_entry+0x66/0x80 [nvidia_uvm)
[14576.950733] ? nv_set_system_power_state+0x176/0x3c0 [nvidia)
[14576.951290] ? down+0x33/0x60
(14576.951310) nv_uvm_suspend+0x33/0x50 [nvidia]
[14576.951866) nv_set_system_power_state+0x2d9/0x3c0 [nvidia)
[14576.952383] nv_procfs_write_suspend+oxe7/0x140 [nvidia)
[14576.952881) proc_reg_write+0x66/0x90
[14576.952908] vfs_write+Oxb9/0x250
[14576.952931) ksys_write+0x67/0xeo
[14576.952955] -_x64_sys_write+0x1a/0x20
[14576.952977) do_syscall_64+0x61/0xbo
(14576.953003] ? irgentry_exit_to_user_mode+0x9/0x20
(14576.953031] ? irgentry_exit+0x19/0x30
[14576.953053) ? exc_page_fault+0x8f/0x170
(14576.953074] ? asm_exc_page_fault+0x8/0x30
[14576.953102] entry_SYSCALL_64_after_hwframe+0X44/0xae
[14576.953131) RIP: 0033:0x7f4c0603f0a7
(14576.953154] Code: 64 89 02 48 c7 co ff ff ff ff eb bb Of 1f 80 00 00 00 00 f3 of le fa 64 8b 04 25 18 00 00 00 85 CO 75 10 b8 01 00 00 00 of 05 <48> 3d 00 fo ff ff 77 51 c3 48 83 ec 28 48
(14576.953242) RSP: 002b:00007ffe75cfaf68 EFLAGS: 00000246 ORIG_RAX: 0000000000000001
[14576.953282] RAX: ffffffffffffffda RBX: 0000000000000008 RCX: 00007f4c0603f0a7
[14576.953320] RDX: 0000000000000008 RSI: 000055c7fca28b20 RDI: 0000000000000001
(14576.953354) RBP: 000055c7fca28b20 R08: 000000000000000a RO9: 0000000000000007
(14576.953389] R10: 000055c7fc55a017 R11: 0000000000000246 R12: 0000000000000008
(14576.953427] R13: 00007f4cc611e6a0 R14: 000076 40c611a4a0 R15: 00007f4cc61198a0
(14576.953467] </TASK>
(14576.953482] Modules linked in: uas usb_storage xt_contrack xt_MASQUERADE nf_conntrack_net link nfnet link xfrm_user xfrm_algo xt_addrtype iptable_filter iptable_nat nf_nat nf_contrack nf.
ridge stp llc rfcomm ccm aufs vboxnetadp(0) vboxnetflt(0) vboxdrvo) cmac algif_hash algif_skcipher af_alg bnep over lay binfmt_misc zfs(PO) zunicode (PO) zzstd(0) zlua(o) zavl(PO) icp (PO) zco
_hda_codec_realtek snd_hda_codec_generic ledtrig_audio hid_logitech_hidpp nvidia_uvm(PO) nvidia_drm(PO) nvidia_modeset (PO) nis_is08859_1 hid_logitech_dj intel_tcc_cooling x86_pkg_temp_therma
rtsx_usb_sdmmc mei_hdcp snd_soc_skl snd_soc_hdac_hda btusb intel_rapl_msr btrti snd_hda_ext_core btbcm snd_soc_sst_ipc btintel snd_soc_sst_dsp coretemp bluetooth snd_soc_acpi_intel_match e
ideobuf2_memops snd_soc_acpi videobuf2_v412
[14576.953561] snd_soc_core videobuf2_common snd_compress videodev ac97_bus snd_pcm_dmaeng ine mc snd_hda_intel snd_intel_dspcfg snd_intel_sdw_acpi snd_hda_codec snd_hda_core snd_hwdep snd_r
5 kvm_intel kvm crct 10dif_pclmul snd_seq ghash_clmulni_intel iwlmum joydev rtsx_usb snd_seq_device mac80211 snd_timer libarc4 iwlwifi aesni_intel crypto_simd cryptd rapl intel_cstate input_1
ore hid_multitouch rc_core asus_nb_wmi serio_raw efi_pstore i2c_algo_bit ee1004 processor_thermal_device fb_sys_fops processor_thermal_rfim me i_me syscopyarea processor_thermal_mbox processo
_soc_dts_iosf sysimgblt intel_xhci_usb_role_switch mei intel_pch_thermal int3403_thermal int340x_thermal_zone acpi_als industrialio_triggered_buffer kfifo_buf mac_hid int3400_thermal industr
fq_codel msr parport_pc ppdev lp parport drm
[14576.954040] ip_tables x_tables autofs4 btrfs blake2b_generic xor zstd_compress raid6_pq libcrc32c hid_generic mfd_aaeon asus_wmi i2c_1801 sparse_keymap 12c_smbus intel_lpss_pci intel_lps
ci_renesas i2c_hid_acpi i2c_hid hid wmi video
[14576.954602] CR2: 0000000000000000
(14576.954621] -- [ end trace 837373e7bd4115ce ] --
[14577.073373) RIP: 0010: _raw_g_schedule+0X40/0x70 [nvidia_uvm)
(14577.073434) Code: 89 fb 4c 89 ef e8 eo 64 Ob ei 48 89 C6 49 86 04 24 49 39 C4 75 31 48 86 43 08 4C 89 63 08 4C 89 ef 49 89 10 24 49 89 44 24 08 <4c> 89 20 e8 28 62 Ob ei 48 8d 7b 18 e8 91
(14577.073498) RSP: 0018:ffffa02fc7197ca8 EFLAGS: 00010046
[14577.073520] RAX: 0000000000000000 RBX: ffffa02fc7af9d38 RCX: 0000000000000001
[14577.075380] RDX: 0000000000000001 RSI: 0000000000000246 RDI: ffffa02fc7af9d48
(14577.077247] RBP: ffffa02fc7197CCO R08: 0000000000000000 RO9: 0000000000000000
(14577.079244] R10: 0000000000000001 R11: 0000000000000000 R12: ffffa02fc7197cdo
(14577.081051) R13: ffffa02fc7af9d48 R14: ffff8f8bc8c44d28 R15: 0000000000000000
[14577.082942] FS: 00007f4cc5f2e740(0000) GS:ffff8f8f1ed00000(0000) KNIGS:0000000000000000
(14577.084789) CS: 0010 DS: 0000 ES: 0000 CRO: 0000000080050033
(14577.086665] CR2: 0000000000000000 CR3: 000000010ac7e004 CR4: 00000000003706e0
(14577.132414) iwlwifi 0000:02:00.0: Applying debug destination EXTERNAL_DRAM
(14577.302879] iwlwifi 0000:02:00.0: Applying debug destination EXTERNAL_DRAM
(14577.398554) iwlwifi 0000:02:00.0: FW already configured (0) re-configuring
(14580.976336) wlp2so: authenticate with 34:20:04:e9:12:00
[14580.988629) wlp2so: send auth to 34:2c:c4:e9:12:00 (try 1/3)
(14581.020219) wlp2so: authenticated
[14581.025238) wlp2so: associate with 34:20:c4:e9:12:00 (try 1/3)
(14581.062380) wlp2so: RX AssocResp from 34:20:c4:e9:12:00 (capab=0x511 status=0 aid=4)
[14581.070532) wlp2s0: associated
(14581.142493] IPV6: ADDRCONF (NETDEV_CHANGE): wip2so: link becomes ready
(14581.145991) wlp2so: Limiting TX power to 17 (17 - 0) dBm as advertised by 34:20:04:e9: 12:00
```
-
SES
hp

---

### Post by MAFoElffen on 2022-03-08
Please go back to all your posts with output and Edit Post > Go Advanced... Hightlight the output (select with mouse), then select the "#" Icon to wrap with Code Tags... Then save... when you post output or commands, please post them wrapped in codes tags. I can see that a Moderator hasn't seen those yet. You might want to do that before they do.

A few things I see. One, you didn't say which model laptop it was, but you did say 7th Gen iCore. Has the BIOS firmware been updated yet? A lot of suspend and hibernation problems can be resolved just by doing that, if there was a BIOS Firmware update for it.

Next, you said that you are on 20.04.3... Current is 20.04.4, and going through your output and seeing the Linux Kernel version, you are in the HWE kernel series, but... You haven't applied any updates for anything in a while. I can see that the kernel version is quite a few version back. There were NVidia module hook updates in those newer kernels. Is there is reason for that? That in itself might change your circumstances greatly.

Just saying what I see. That might also help with how your NVidia relates to your system... Graphics Drivers assume that the system is up to date... And if your didn't update recently, you missed out on the recent linux-firmware updates, and possibly a new NVidia update that might have resolved your issues.

Just saying, you might want to update both those areas and see if those take care of things.

EDIT:
You also did not mention if your NVidia Driver was installed from the Repo's or was straight from NVidia...

---

