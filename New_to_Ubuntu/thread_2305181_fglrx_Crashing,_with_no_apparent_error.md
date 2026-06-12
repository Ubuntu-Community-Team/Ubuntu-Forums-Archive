---
title: "fglrx Crashing, with no apparent error"
date: 2015-12-03
forum: New to Ubuntu
---

### Post by Jason_Hunter on 2015-12-03
I'm seeing fglrx crashing in dmesg, but I have problems figuring out what search term to search for, as there's no clear error message. 

Can someone point me in some direction as to what I can try?

I don't experience the crash like a crash; it's just that after this "crash", everything gets slower, I think. 

My Ubuntu 15.10 is completely updated. 

This is what I got from dmesg: 

```
[    6.903602] <6>[fglrx] Firegl kernel thread PID: 1055
[    6.903685] <6>[fglrx] Firegl kernel thread PID: 1056
[    6.903765] <6>[fglrx] Firegl kernel thread PID: 1057
[    6.903945] <6>[fglrx] IRQ 30 Enabled
[    6.915250] ------------[ cut here ]------------
[    6.915258] WARNING: CPU: 2 PID: 1044 at /build/linux-yZBlQv/linux-4.2.0/arch/x86/kernel/fpu/core.c:47 kernel_fpu_enable+0x38/0x50()
[    6.915260] Modules linked in: bnep binfmt_misc btusb btrtl btbcm btintel kvm_amd kvm bluetooth fglrx(POE) serio_raw input_leds snd_hdsp joydev snd_seq_midi snd_h
da_codec_hdmi snd_seq_midi_event xfs snd_rawmidi snd_hda_intel snd_hda_codec libcrc32c snd_hda_core snd_hwdep amd64_edac_mod snd_seq snd_pcm edac_core edac_mce_amd k
10temp snd_seq_device snd_timer snd soundcore i2c_nforce2 shpchp mac_hid 8250_fintek cuse parport_pc ppdev sunrpc lp parport autofs4 hid_logitech ff_memless hid_gene
ric hid_logitech_hidpp hid_logitech_dj usbhid hid psmouse firewire_ohci forcedeth pata_acpi firewire_core sata_nv crc_itu_t pata_amd floppy
[    6.915300] CPU: 2 PID: 1044 Comm: Xorg Tainted: P           OE   4.2.0-19-generic #23-Ubuntu
[    6.915302] Hardware name: empty empty/S2927/S2927-E, BIOS 'V2.03     ' 10/28/2008
[    6.915304]  c1a649a7 5409d8b9 00000000 e58017b0 c175e501 00000000 e58017e0 c106a847
[    6.915308]  c195ee1c 00000002 00000414 c194ef40 0000002f c101bb98 c101bb98 00000000
[    6.915312]  e5801924 f5983b40 e58017f0 c106a952 00000009 00000000 e58017f8 c101bb98
[    6.915316] Call Trace:
[    6.915321]  [<c175e501>] dump_stack+0x41/0x52
[    6.915324]  [<c106a847>] warn_slowpath_common+0x87/0xc0
[    6.915327]  [<c101bb98>] ? kernel_fpu_enable+0x38/0x50
[    6.915330]  [<c101bb98>] ? kernel_fpu_enable+0x38/0x50
[    6.915332]  [<c106a952>] warn_slowpath_null+0x22/0x30
[    6.915335]  [<c101bb98>] kernel_fpu_enable+0x38/0x50
[    6.915338]  [<c101c002>] __kernel_fpu_end+0x52/0x180
[    6.915418]  [<fa40765d>] KCL_fpu_end+0xd/0x10 [fglrx]
[    6.915477]  [<fa428fcb>] MCIL_RestoreFloatPointState+0xb/0x20 [fglrx]
[    6.915587]  [<fa568666>] PECI_RestoreFloatingPointContext+0x66/0x90 [fglrx]
[    6.915694]  [<fa5e31b4>] PhwSIslands_CalculateLeakageForVandT+0x194/0x1d0 [fglrx]
[    6.915751]  [<fa426238>] ? MCIL_ModifyRegister+0xa8/0x3f0 [fglrx]
[    6.915808]  [<fa426238>] ? MCIL_ModifyRegister+0xa8/0x3f0 [fglrx]
[    6.915910]  [<fa5e2d77>] PhwSIslands_InitDTELeakageTable+0x87/0x130 [fglrx]
[    6.916013]  [<fa5e1e08>] TF_PhwSIslands_InitializeSmcCacTables+0x278/0x470 [fglrx]
[    6.916118]  [<fa560071>] PHM_DispatchTable+0x101/0x260 [fglrx]
[    6.916223]  [<fa585940>] ? PSM_TranslateUILabelToClass+0x80/0x80 [fglrx]
[    6.916328]  [<fa55902c>] PHM_EnableDynamicStateManagement+0x7c/0x110 [fglrx]
[    6.916433]  [<fa58bf14>] PEM_Task_EnableDynamicStateManagement+0x44/0xe0 [fglrx]
[    6.916538]  [<fa58cec0>] ? PEM_Task_GetBootStateID+0x30/0x50 [fglrx]
[    6.916643]  [<fa589ed3>] PEM_ExcuteEventChain+0x63/0xf0 [fglrx]
[    6.916749]  [<fa58b0ab>] ? PEM_GetDisableGFXClockGatingActionChain+0x3b/0x60 [fglrx]
[    6.916854]  [<fa587ebf>] PEM_HandleEvent+0x5f/0xf0 [fglrx]
[    6.916959]  [<fa58a479>] ? PEM_InitializeEventActionChains+0x519/0x570 [fglrx]
[    6.917063]  [<fa588b00>] ? PEM_RecordQueryTimeStamp+0x30/0x30 [fglrx]
[    6.917168]  [<fa588063>] PEM_Initialize+0x113/0x490 [fglrx]
[    6.917273]  [<fa5856f2>] ? PSM_GetState+0x22/0x30 [fglrx]
[    6.917377]  [<fa556180>] PP_Initialize_internal+0x2f0/0x370 [fglrx]
[    6.917381]  [<c11b0d45>] ? __kmalloc+0x185/0x240
[    6.917441]  [<fa445daf>] ? firegl_trace+0x1f/0x180 [fglrx]
[    6.917545]  [<fa555d65>] PP_Initialize+0x45/0x70 [fglrx]
[    6.917606]  [<fa4482d3>] firegl_pplib_init_powerplay+0x93/0x210 [fglrx]
[    6.917667]  [<fa448a92>] firegl_pplib_init+0xa2/0x1a0 [fglrx]
[    6.917726]  [<fa445daf>] ? firegl_trace+0x1f/0x180 [fglrx]
[    6.917786]  [<fa440c13>] hal_init_gpu+0x273/0x590 [fglrx]
[    6.917846]  [<fa445daf>] ? firegl_trace+0x1f/0x180 [fglrx]
[    6.917901]  [<fa413c44>] firegl_open+0x344/0x380 [fglrx]
[    6.917951]  [<fa40019f>] ip_firegl_open+0x1f/0x30 [fglrx]
[    6.918001]  [<fa4019ca>] firegl_stub_open+0x9a/0x100 [fglrx]
[    6.918005]  [<c11ccec4>] chrdev_open+0xa4/0x180
[    6.918008]  [<c11c6c7c>] do_dentry_open+0x1ec/0x300
[    6.918011]  [<c11cce20>] ? cdev_put+0x20/0x20
[    6.918013]  [<c11c7c3f>] vfs_open+0x4f/0x60
[    6.918016]  [<c11d62c3>] path_openat+0x423/0x1150
[    6.918019]  [<c11d80c8>] do_filp_open+0x68/0xe0
[    6.918022]  [<c11e4dd6>] ? __alloc_fd+0x36/0x100
[    6.918025]  [<c11c7fed>] do_sys_open+0x11d/0x280
[    6.918028]  [<c11c8172>] SyS_open+0x22/0x30
[    6.918031]  [<c176421f>] sysenter_do_call+0x12/0x12
[    6.918033] ---[ end trace 7e99758b80c23772 ]---
[    6.921393] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
[    6.921395] <6>[fglrx] Reserved FB block: Unshared offset:f7b4000, size:4000
[    6.921397] <6>[fglrx] Reserved FB block: Unshared offset:f7b8000, size:548000 
[    6.921399] <6>[fglrx] Reserved FB block: Unshared offset:7ffee000, size:12000

Later in the dmesg, I see this: 
[45831.818476] Xorg: page allocation failure: order:5, mode:0x40d0
[45831.818483] CPU: 1 PID: 1044 Comm: Xorg Tainted: P        W  OE   4.2.0-19-generic #23-Ubuntu
[45831.818485] Hardware name: empty empty/S2927/S2927-E, BIOS 'V2.03     ' 10/28/2008
[45831.818487]  c1a649a7 5409d8b9 00000000 e5801ccc c175e501 00000000 e5801cfc c1168693
[45831.818492]  c197517c f598386c 00000005 000040d0 00000001 e5801d84 000040d0 5409d8b9
[45831.818496]  00000005 e5801d8c e5801db4 c116aade 000040d0 00000005 00000000 e5801d83
[45831.818500] Call Trace:
[45831.818508]  [<c175e501>] dump_stack+0x41/0x52
[45831.818512]  [<c1168693>] warn_alloc_failed+0xd3/0x110
[45831.818516]  [<c116aade>] __alloc_pages_nodemask+0x73e/0x910
[45831.818519]  [<c116aead>] alloc_kmem_pages+0x3d/0xe0
[45831.818522]  [<c1183884>] kmalloc_order+0x14/0x30
[45831.818525]  [<c11838bb>] kmalloc_order_trace+0x1b/0x80
[45831.818529]  [<c11b0d80>] __kmalloc+0x1c0/0x240
[45831.818619]  [<fa445daf>] ? firegl_trace+0x1f/0x180 [fglrx]
[45831.818672]  [<fa403245>] KCL_MEM_SmallBufferAlloc+0x15/0x20 [fglrx]
[45831.818724]  [<fa40a9ab>] drm_alloc+0xcb/0x1d0 [fglrx]
[45831.818729]  [<c138230c>] ? _copy_from_user+0x3c/0x50
[45831.818784]  [<fa41dd8e>] firegl_adl_escape+0x8e/0x1b0 [fglrx]
[45831.818838]  [<fa41dd00>] ? _r6x_init_hw_ctx+0xc0/0xc0 [fglrx]
[45831.818892]  [<fa41425a>] firegl_ioctl+0x22a/0x2b0 [fglrx]
[45831.818896]  [<c1192eb2>] ? unmap_region+0xa2/0xf0
[45831.818946]  [<fa4001d0>] ? ip_firegl_release+0x20/0x20 [fglrx]
[45831.818997]  [<fa4001eb>] ip_firegl_unlocked_ioctl+0x1b/0x20 [fglrx]
[45831.819000]  [<c11db472>] do_vfs_ioctl+0x2e2/0x520
[45831.819003]  [<c1192f4a>] ? remove_vma+0x4a/0x50
[45831.819006]  [<c11954c0>] ? do_munmap+0x250/0x390
[45831.819009]  [<c11db718>] SyS_ioctl+0x68/0x80
[45831.819012]  [<c176421f>] sysenter_do_call+0x12/0x12
[45831.819014] Mem-Info:
[45831.819019] active_anon:1543365 inactive_anon:267043 isolated_anon:0
                active_file:363072 inactive_file:274274 isolated_file:0
                unevictable:20298 dirty:7 writeback:0 unstable:0
                slab_reclaimable:66213 slab_unreclaimable:12235
                mapped:244061 shmem:112865 pagetables:15993 bounce:0
                free:1515730 free_pcp:0 free_cma:0
[45831.819029] DMA free:2844kB min:68kB low:84kB high:100kB active_anon:0kB inactive_anon:0kB active_file:180kB inactive_file:8kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15992kB managed:15916kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:10708kB slab_unreclaimable:1016kB kernel_stack:200kB pagetables:0kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[45831.819030] lowmem_reserve[]: 0 696 16188 16188
[45831.819038] Normal free:8256kB min:3216kB low:4020kB high:4824kB active_anon:5616kB inactive_anon:6252kB active_file:169748kB inactive_file:106912kB unevictable:3008kB isolated(anon):0kB isolated(file):0kB present:897016kB managed:714264kB mlocked:3008kB dirty:0kB writeback:0kB mapped:7272kB shmem:3512kB slab_reclaimable:254144kB slab_unreclaimable:47924kB kernel_stack:9216kB pagetables:324kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:32 all_unreclaimable? no
[45831.819039] lowmem_reserve[]: 0 0 123935 123935
[45831.819046] HighMem free:6051820kB min:512kB low:18392kB high:36272kB active_anon:6167844kB inactive_anon:1061920kB active_file:1282360kB inactive_file:990176kB unevictable:78184kB isolated(anon):0kB isolated(file):0kB present:15863752kB managed:15863752kB mlocked:78184kB dirty:28kB writeback:0kB mapped:968972kB shmem:447948kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:63648kB unstable:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
[45831.819048] lowmem_reserve[]: 0 0 0 0
[45831.819050] DMA: 47*4kB (UEM) 70*8kB (UE) 29*16kB (UE) 21*32kB (UEM) 3*64kB (U) 2*128kB (UE) 2*256kB (M) 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2844kB
[45831.819060] Normal: 548*4kB (UEM) 303*8kB (UEM) 199*16kB (UEM) 16*32kB (UEM) 3*64kB (UE) 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 8504kB
[45831.819068] HighMem: 5053*4kB (UM) 21865*8kB (UM) 9208*16kB (UM) 2926*32kB (UM) 5831*64kB (UM) 5140*128kB (UM) 3940*256kB (UM) 2405*512kB (UM) 1296*1024kB (UM) 15*2048kB (UM) 241*4096kB (UM) = 6052156kB
[45831.819079] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
[45831.819080] 750177 total pagecache pages
[45831.819082] 3 pages in swap cache
[45831.819083] Swap cache stats: add 3, delete 0, find 3/3
[45831.819085] Free swap  = 4881392kB
[45831.819086] Total swap = 4881404kB
[45831.819087] 4194190 pages RAM
[45831.819088] 3965938 pages HighMem/MovableOnly
[45831.819089] 45707 pages reserved
[45831.819090] 0 pages cma reserved
[48632.617820] lenovo 0005:17EF:6048.0015: unknown main item tag 0x0
```

---

### Post by T.J. on 2015-12-03
Since Catalyst (aka fglrx) is a closed source driver, there is very little that can be done to help, but I can make a few simple suggestions. Depending on the age of your hardware, you may want to look at the AMDGPU driver, but it is reported to have a few issues and only works with newer AMD cards from the last few years.   Don't expect any future help from AMD with the existing Catalyst drivers, they have pretty much stated that 15.9 is the last version they will do anything with.  Everyone who does not like a hassle is using the open Radeon driver.

As for the suggestions, I would remove fglrx completely and then reinstall it.  I personally have had trouble with the "updated" versions, so I would suggest using the version that originally came with your version of Ubuntu.  If you have some programming experience or a friend who does, you could have them backport the final version of Catalyst for you.  I would, but I do not use Ubuntu presently, and have no plans to try again until 16.04 LTS.

From a glance at your errors, assuming you are not having a hardware failure, I would guess that the driver interface was compiled by someone using a version of GCC that hadn't been thoroughly tested.  If you are running 15.04 or 15.10, you should expect driver issues.

---

### Post by sandyd on 2015-12-03
Fgrlx was a bit buggy at release-time, was not supported with the release kernel.
See [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888)

The bug indicates it is fixed now, though a few issues seem to be continuing with the fix.

Do you have the proposed repositories enabled, and what version of the driver are you running? 
You can check if you have the proposed repositories enabled "Software Sources", which is accessible via the Software Center. The driver version can be checked from "Additional Drivers".

---

### Post by QIII on 2015-12-03
The Catalyst driver may disappear, but something will take its place.  AMD is a member of the Linux Foundation and has had a romance with Canonical for many years.

I seriously doubt they are shaking the dust from their sandals.

@Jason_Hunter:

What is the model of your GPU?  Is this a desktop?  Is this a laptop?  If the latter, is it one with hybrid Intel/AMD graphics?  If it is a hybrid, is it MUXed or MUXless?

---

### Post by T.J. on 2015-12-05
> **QIII said:**
> The Catalyst driver may disappear, but something will take its place.  AMD is a member of the Linux Foundation and has had a romance with Canonical for many years.

I seriously doubt they are shaking the dust from their sandals.

Probably not. AMD has provided advice for the open Radeon driver for some time, including firmware, and the new AMDGPU driver is in part, based on that work. The only support you will see from AMD other than the AMDGPU driver is the open Radeon driver. AMD has pulled the plug on Catalyst and any hardware from approximately the 6000-7000 series, and anything older, depending on the chipset used. IMHO, it is just as well. AMD's proprietary drivers are substandard at best.  They have had outstanding bugs for years at a time.

---

### Post by Jason_Hunter on 2015-12-05
Right, I've disabled fglrx and all is fine and dandy. Thanks.

---

### Post by T.J. on 2015-12-07
Great! Please mark the thread solved if you feel the matter is closed.  If not, please let me know.

---

