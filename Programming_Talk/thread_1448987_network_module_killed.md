---
title: "network module killed"
date: 2010-04-07
forum: Programming Talk
---

### Post by scanty on 2010-04-07
hi all, 
while running a network module snull.ko(with snull.c on kernel 2.6.33 ubuntu 9.10)
the module gets killed.

/var/log/messages has following message:

Apr  7 19:36:15 MyLinuz kernel: [  312.676032] *pde = 00883067 *pte = 00000000 
Apr  7 19:36:15 MyLinuz kernel: [  312.676032] Modules linked in: snull(+) binfmt_misc snd_ens1371 gameport snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event iptable_filter snd_seq ip_tables snd_timer snd_seq_device x_tables ppdev snd soundcore snd_page_alloc parport_pc psmouse lp parport shpchp i2c_piix4 serio_raw mptspi mptscsih mptbase intel_agp pcnet32 mii floppy scsi_transport_spi agpgart
Apr  7 19:36:15 MyLinuz kernel: [  312.676032] 
Apr  7 19:36:15 MyLinuz kernel: [  312.676032] Pid: 1718, comm: insmod Not tainted 2.6.33-020633-generic #020633 440BX Desktop Reference Platform/VMware Virtual Platform
Apr  7 19:36:15 MyLinuz kernel: [  312.676032] EIP: 0060:[<ffffffff>] EFLAGS: 00010286 CPU: 0
Apr  7 19:36:15 MyLinuz kernel: [  312.676032] EIP is at 0xffffffff
Apr  7 19:36:15 MyLinuz kernel: [  312.676032] EAX: e17db800 EBX: e17db800 ECX: 00000000 EDX: ffffffff
Apr  7 19:36:15 MyLinuz kernel: [  312.676032] ESI: e17db800 EDI: c090b4c0 EBP: d99e7f34 ESP: d99e7f18
Apr  7 19:36:15 MyLinuz kernel: [  312.676032]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Apr  7 19:36:15 MyLinuz kernel: [  312.676032]  c04bde53 d99e7f2c c05978e4 a3abc1c8 00000000 e17db800 b77adff4 d99e7f44
Apr  7 19:36:15 MyLinuz kernel: [  312.676032] <0> c04be02a e38d5420 00004000 d99e7f5c e38d54ab 00000001 c07a2f30 d99e7f78
Apr  7 19:36:16 MyLinuz kernel: [  312.676032] <0> e38d5420 d99e7f88 c0101127 e38d5bc0 00000001 e38d5bc0 00004000 b77adff4
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<c04bde53>] ? register_netdevice+0x73/0x210
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<c05978e4>] ? mutex_lock+0x14/0x40
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<c04be02a>] ? register_netdev+0x3a/0x50
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<e38d5420>] ? snull_init_module+0x0/0xf0 [snull]
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<e38d54ab>] ? snull_init_module+0x8b/0xf0 [snull]
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<e38d5420>] ? snull_init_module+0x0/0xf0 [snull]
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<c0101127>] ? do_one_initcall+0x27/0x190
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<c0181924>] ? sys_init_module+0x94/0x1f0
Apr  7 19:36:16 MyLinuz kernel: [  312.676032]  [<c0102d23>] ? sysenter_do_call+0x12/0x28
Apr  7 19:36:16 MyLinuz kernel: [  312.676032] ---[ end trace 523fa70b26605921 ]---


please help out how to deal with this error.

---

