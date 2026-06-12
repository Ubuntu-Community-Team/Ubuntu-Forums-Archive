---
title: "lsusb command hangs, unable to shutdown"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by duruttye on 2008-11-18
Hey there!

I tried a few times to connect my sony ericsson w380i phone to my laptop using ubuntu 8.10, a few times worked, used it as a mass storage device, but now it doesn't. When I plug  it in, nothing happens and the lsusb command doesn't display anything, then I can't shut down the laptop.

dmesg:
[HTML]
[14387.256032] APIC error on CPU0: 00(40)
[14387.256056] APIC error on CPU1: 00(40)
[15745.805084] usb 2-1: new full speed USB device using ohci_hcd and address 2
[15745.981545] usb 2-1: configuration #2 chosen from 1 choice
[15746.369520] BUG: unable to handle kernel NULL pointer dereference at 00000003
[15746.369539] IP: [<f9ba35bc>] :cdc_wdm:wdm_probe+0x13c/0x3c0
[15746.369556] *pde = 00000000 
[15746.369566] Oops: 0000 [#1] SMP 
[15746.369576] Modules linked in: cdc_wdm(+) ipv6 nls_iso8859_1 nls_cp437 vfat fat af_packet rfkill_input binfmt_misc rfcomm sco bridge stp bnep l2cap bluetooth ppdev powernow_k8 cpufreq_conservative cpufreq_ondemand cpufreq_userspace cpufreq_powersave cpufreq_stats freq_table container sbs sbshc pci_slot iptable_filter ip_tables x_tables parport_pc lp parport joydev mmc_block snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm dcdbas snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event serio_raw snd_seq pcspkr psmouse ricoh_mmc sdhci_pci sdhci snd_timer arc4 mmc_core snd_seq_device ecb k8temp crypto_blkcipher snd soundcore snd_page_alloc i2c_piix4 i2c_core b43 rfkill mac80211 evdev cfg80211 led_class input_polldev usblp video output wl(P) ieee80211_crypt fglrx(P) wmi ac button battery ati_agp agpgart shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom ata_generic usbhid hid b44 pata_atiixp sd_mod crc_t10dif sg ohci_hcd ehci_hcd mii pata_acpi ssb usbcore ahci libata scsi_mod dock thermal processor fan fbcon tileblit font bitblit softcursor fuse
[15746.369777] 
[15746.369785] Pid: 18086, comm: modprobe Tainted: P          (2.6.27-8-generic #1)
[15746.369793] EIP: 0060:[<f9ba35bc>] EFLAGS: 00010246 CPU: 1
[15746.369805] EIP is at wdm_probe+0x13c/0x3c0 [cdc_wdm]
[15746.369812] EAX: 00000000 EBX: 00000800 ECX: f9ba7480 EDX: e568d600
[15746.369818] ESI: 00000000 EDI: f2ee83c0 EBP: d3d67dec ESP: d3d67db0
[15746.369825]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
[15746.369833] Process modprobe (pid: 18086, ti=d3d66000 task=f3707110 task.ti=d3d66000)
[15746.369839] Stack: c0200a8b c02001c8 d3d67dd0 c0200275 d3d67dcc e568d600 00000000 d3d67de4 
[15746.369856]        fffffff4 0800a724 f229a45c f9ba5234 e568d600 00000000 e568d61c d3d67e18 
[15746.369873]        f893a4e7 e568d694 d3d67e04 c0201117 f9ba5200 f229a400 f9ba52a0 e568d61c 
[15746.369890] Call Trace:
[15746.369898]  [<c0200a8b>] ? sysfs_addrm_finish+0x3b/0xf0
[15746.369917]  [<c02001c8>] ? sysfs_add_one+0x18/0x50
[15746.369928]  [<c0200275>] ? sysfs_addrm_start+0x75/0xa0
[15746.369949]  [<f893a4e7>] ? usb_probe_interface+0xa7/0x140 [usbcore]
[15746.370002]  [<c0201117>] ? sysfs_create_link+0x17/0x20
[15746.370033]  [<c02c3d7e>] ? really_probe+0xee/0x190
[15746.370052]  [<f89398a9>] ? usb_match_id+0x49/0x60 [usbcore]
[15746.370107]  [<c02c3e63>] ? driver_probe_device+0x43/0x60
[15746.370117]  [<c02c3ef9>] ? __driver_attach+0x79/0x80
[15746.370132]  [<c02c35c3>] ? bus_for_each_dev+0x53/0x80
[15746.370151]  [<c02c3b9e>] ? driver_attach+0x1e/0x20
[15746.370161]  [<c02c3e80>] ? __driver_attach+0x0/0x80
[15746.370171]  [<c02c2f67>] ? bus_add_driver+0x1b7/0x230
[15746.370196]  [<c02c40ce>] ? driver_register+0x6e/0x150
[15746.370221]  [<f893a7bc>] ? usb_register_driver+0x7c/0xf0 [usbcore]
[15746.370257]  [<c012a260>] ? resched_task+0x60/0x70
[15746.370278]  [<f886a000>] ? wdm_init+0x0/0x1e [cdc_wdm]
[15746.370289]  [<f886a01c>] ? wdm_init+0x1c/0x1e [cdc_wdm]
[15746.370300]  [<c0101120>] ? _stext+0x30/0x160
[15746.370309]  [<c012b4ee>] ? try_to_wake_up+0xde/0x290
[15746.370326]  [<c014c604>] ? __blocking_notifier_call_chain+0x14/0x70
[15746.370355]  [<c015c208>] ? sys_init_module+0x88/0x1b0
[15746.370370]  [<c0103f7b>] ? sysenter_do_call+0x12/0x2f
[15746.370382]  =======================
[15746.370386] Code: 00 00 00 c7 87 9c 00 00 00 50 3b ba f9 66 89 47 38 8d 87 94 00 00 00 89 87 94 00 00 00 89 87 98 00 00 00 8b 02 8b 40 0c 89 45 dc <0f> b6 40 03 83 e0 03 83 f8 03 74 38 c7 45 e4 ea ff ff ff 89 f8 
[15746.370471] EIP: [<f9ba35bc>] wdm_probe+0x13c/0x3c0 [cdc_wdm] SS:ESP 0068:d3d67db0
[15746.370536] ---[ end trace afafbb676abffc04 ]---
[15758.544963] usb 2-1: USB disconnect, address 2
[/HTML]

Any thoughts on that?

---

### Post by oldos2er on 2008-11-18
Which version of Ubuntu are you running, and have you updated it?

---

### Post by duruttye on 2008-11-19
The version is ubuntu 8.10, updated of course, dell inspiron 1501.

---

### Post by oldos2er on 2008-11-19
I had very similar problems when I first ran 8.10, but installing updates seems to have fixed the problems for me (which is why I asked if you had updated). Sorry I don't have any further suggestions for you.

---

### Post by duruttye on 2008-11-19
Well, thanx anyway.

I'm right here right now, with the phone plugged in, the lsusb command hanging, waiting for suggestions :)

---

