---
title: "Streamzap remote crash on unplug"
date: 2011-10-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by effenberg0x0 on 2011-10-12
This started happening after yesterday updates to oneiric. I'll report a bug.

```
[  695.140778] usb 5-1: USB disconnect, device number 2
[  695.141526] streamzap 5-1:1.0: urb terminated, status: -108
[  695.155873] BUG: unable to handle kernel NULL pointer dereference at 0000000000000050
[  695.155887] IP: [<ffffffffa01988cf>] show_protocols+0x11f/0x130 [rc_core]
[  695.155907] PGD 3fe1d6067 PUD 3fe3cc067 PMD 0 
[  695.155917] Oops: 0000 [#1] SMP 
[  695.155925] CPU 3 
[  695.155928] Modules linked in: bnep rfcomm bluetooth speedstep_lib parport_pc ppdev ip6t_LOG xt_hl ip6t_rt nf_conntrack_ipv6 nf_defrag_ipv6 ipt_REJECT ipt_LOG xt_limit xt_tcpudp xt_addrtype xt_state ip6table_filter ip6_tables nf_conntrack_netbios_ns nf_conntrack_broadcast binfmt_misc nf_nat_ftp nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_conntrack_ftp nf_conntrack snd_hda_codec_realtek iptable_filter nvidia(P) ip_tables x_tables snd_hda_intel snd_hda_codec snd_hwdep ir_lirc_codec lirc_dev ir_sony_decoder ir_jvc_decoder ir_rc6_decoder snd_pcm ir_rc5_sz_decoder ir_rc5_decoder snd_seq_midi rc_streamzap ir_nec_decoder snd_rawmidi snd_seq_midi_event streamzap rc_core snd_seq snd_timer snd_seq_device snd soundcore snd_page_alloc sp5100_tco i2c_piix4 wmi edac_core k10temp edac_mce_amd asus_atk0110 lp parport raid10 raid456 async_raid6_recov async_pq firewire_ohci usbhid firewire_core raid6_pq async_xor hid crc_itu_t sata_sil r8169 ahci xhci_hcd pata_jmicron libahci xor async_memcpy async_tx raid1 raid0 multipath linear
[  695.156075] 
[  695.156082] Pid: 29539, comm: cat Tainted: P            3.0.0-0300-generic #201107220917 System manufacturer System Product Name/M4A89GTD-PRO/USB3
[  695.156095] RIP: 0010:[<ffffffffa01988cf>]  [<ffffffffa01988cf>] show_protocols+0x11f/0x130 [rc_core]
[  695.156111] RSP: 0018:ffff8803fdfdde48  EFLAGS: 00010202
[  695.156117] RAX: 0000000000000000 RBX: ffff880425109800 RCX: 0000000000000001
[  695.156123] RDX: ffff8803fdfddfd8 RSI: ffffffffa019c160 RDI: ffff880425109ac0
[  695.156129] RBP: ffff8803fdfdde78 R08: 0000000000015d4f R09: ffffea000dfe1f68
[  695.156135] R10: 0000000000000000 R11: 0000000000000246 R12: fffffffffffffffb
[  695.156140] R13: ffff880425109810 R14: ffffffff8164cb00 R15: ffff8803ff76b000
[  695.156148] FS:  00007ffed02ee720(0000) GS:ffff88043fcc0000(0000) knlGS:0000000000000000
[  695.156154] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  695.156159] CR2: 0000000000000050 CR3: 00000003fe35a000 CR4: 00000000000006e0
[  695.156165] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  695.156171] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  695.156178] Process cat (pid: 29539, threadinfo ffff8803fdfdc000, task ffff8803fe0fc4d0)
[  695.156183] Stack:
[  695.156186]  ffff880425109ac0 ffffffffa019c160 fffffffffffffffb ffff880425109810
[  695.156196]  ffffffff8164cb00 0000000000008000 ffff8803fdfdde98 ffffffff813c8e1f
[  695.156206]  ffff88041f884720 ffff88041e8496e0 ffff8803fdfddec8 ffffffff811dae57
[  695.156216] Call Trace:
[  695.156230]  [<ffffffff813c8e1f>] dev_attr_show+0x2f/0x60
[  695.156241]  [<ffffffff811dae57>] fill_read_buffer+0x67/0xe0
[  695.156250]  [<ffffffff811daf65>] sysfs_read_file+0x95/0xa0
[  695.156260]  [<ffffffff8116b669>] vfs_read+0xc9/0x180
[  695.156269]  [<ffffffff8116bbd5>] sys_read+0x55/0x90
[  695.156278]  [<ffffffff815e8382>] system_call_fastpath+0x16/0x1b
[  695.156283] Code: 01 4c 29 f8 48 83 c4 08 5b 41 5c 41 5d 41 5e 41 5f c9 c3 49 8b 94 24 c8 b2 19 a0 48 c7 c6 19 b4 19 a0 eb a6 48 8b 83 e8 02 00 00 <4c> 8b 60 50 e8 38 12 00 00 49 89 c5 e9 2b ff ff ff 55 48 89 e5 
[  695.156361] RIP  [<ffffffffa01988cf>] show_protocols+0x11f/0x130 [rc_core]
[  695.156374]  RSP <ffff8803fdfdde48>
[  695.156377] CR2: 0000000000000050
[  695.156383] ---[ end trace e4ccb47ce256ac3e ]---

```

Regards,
Effenberg

---

