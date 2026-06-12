---
title: "Fully Freezes out all the time need help"
date: 2014-04-16
forum: New to Ubuntu
---

### Post by Daimyo on 2014-04-16
```
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713445] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713450] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713454] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713456] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713459] CPU: 0 PID: 14675 Comm: webrtc_audio_mo Tainted: PF          O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713460] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713462]  ffff88025fea2cf0 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713465]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713467]  ffff8801b3b52580 ffff88042609a7b0 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713470] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713474]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713477]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713480]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713482]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713484]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713486]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713489]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713492]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713494]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713497]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713499]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713501]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.713504]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733603] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88020e9cf578 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733607] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733611] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733613] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733615] CPU: 0 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733617] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733618]  ffff8801b3868f18 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733621]  ffff88038f877cb8 ffffffff81163e58 ffff88020e9cf578 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733623]  ffff8801b3b52580 ffff88020e9cf578 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733626] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733630]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733633]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733635]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733638]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733640]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733642]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733644]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733647]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733650]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733652]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733654]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733656]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733658]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.733661]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743812] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88020e9cf578 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743817] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743822] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743823] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743826] CPU: 0 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743828] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743829]  ffff8801deb0c958 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743832]  ffff88038f877cb8 ffffffff81163e58 ffff88020e9cf578 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743835]  ffff8801b3b52580 ffff88020e9cf578 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743837] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743842]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743845]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743847]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743850]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743852]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743854]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743857]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743859]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743861]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743865]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743867]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743869]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743872]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743873]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.743876]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753842] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753847] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753852] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753854] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753857] CPU: 0 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753858] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753860]  ffff8801b3979508 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753863]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753865]  ffff8801b3b52580 ffff88042609a7b0 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753868] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753873]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753876]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753878]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753880]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753883]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753885]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753887]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753890]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753893]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753895]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753898]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753900]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753902]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.753905]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798072] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798079] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798085] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798088] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798091] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798093] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798095]  ffff8801b38687e8 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798100]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798102]  ffff8801b3b52580 ffff88042609a7b0 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798105] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798111]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798114]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798117]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798119]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798122]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798124]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798126]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798131]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798133]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798135]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798138]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798139]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.798143]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804123] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804128] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804133] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804135] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804138] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804139] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804141]  ffff8801deb0ca10 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804144]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804147]  ffff8801b3b52580 ffff88042609a7b0 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804149] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804154]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804157]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804160]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804162]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804164]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804167]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804169]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804172]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804175]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804177]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804179]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804181]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.804184]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814002] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814005] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814009] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814011] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814013] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814015] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814016]  ffff8801deb81508 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814020]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814022]  ffff8801b3b52580 ffff88042609a7b0 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814028] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814031]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814034]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814036]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814038]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814041]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814043]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814045]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814048]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814050]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814052]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814055]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814056]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.814059]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824098] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824101] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824105] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824107] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824109] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824111] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824112]  ffff8801deb81508 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824119]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824121]  ffff8801b3b52580 ffff88042609a7b0 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824123] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824127]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824129]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824132]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824134]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824136]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824138]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824141]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824144]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824146]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824148]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824150]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824152]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.824155]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834019] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834023] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834026] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834028] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834031] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834032] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834034]  ffff8801deb81508 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834037]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 00000000000002b8
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834039]  ffff8801b3b52580 ffff88042609a7b0 00007eff882b0000 00007eff88400000
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834041] Call Trace:
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834045]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834048]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834050]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834052]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834055]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834057]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834059]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834062]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834064]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834066]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834069]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834070]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:36:03 miles-desktop kernel: [ 5064.834073]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320411] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320416] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320420] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320422] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320425] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320426] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320427]  ffff8801b3a47000 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320431]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320433]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320435] Call Trace:
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320440]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320443]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320447]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320451]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320454]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320458]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320460]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320464]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320468]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320471]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320473]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320476]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320478]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.320482]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330280] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330284] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330288] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330290] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330292] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330293] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330294]  ffff8801deb81228 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330297]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330299]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330302] Call Trace:
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330305]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330308]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330310]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330312]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330314]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330317]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330319]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330321]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330324]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330326]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330328]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330330]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330332]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.330335]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340394] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340399] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340403] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340405] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340408] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340410] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340411]  ffff8801deb81228 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340415]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340417]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340419] Call Trace:
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340424]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340427]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340429]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340431]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340434]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340436]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340439]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340442]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340444]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340446]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340449]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340451]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.340453]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350357] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88032cd25578 pmd:1b3b52067
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350361] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350364] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350367] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350369] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350371] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350372]  ffff8801deb81228 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350376]  ffff88038f877cb8 ffffffff81163e58 ffff88032cd25578 0000000000000cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350378]  ffff8801b3b52580 ffff88032cd25578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350386] Call Trace:
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350391]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350394]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350396]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350398]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350401]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350403]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350405]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350408]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350411]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350421]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350424]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350426]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350428]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.350431]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360439] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360442] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360445] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360447] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360449] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360450] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360451]  ffff8801b3979958 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360454]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360456]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360459] Call Trace:
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360462]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360465]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360467]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360469]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360472]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360474]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360476]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360479]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360481]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360483]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360486]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360487]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:06 miles-desktop kernel: [ 5188.360490]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533490] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88032cd25578 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533496] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533503] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533505] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533508] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533510] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533512]  ffff8801b3868228 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533515]  ffff88038f877cb8 ffffffff81163e58 ffff88032cd25578 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533518]  ffff8801b3b52580 ffff88032cd25578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533520] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533527]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533531]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533534]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533537]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533539]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533542]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533545]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533547]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533549]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533554]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533557]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533560]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533563]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533566]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5189.533570]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025575] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025580] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025586] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025588] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025591] CPU: 3 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025592] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025594]  ffff8801b3979508 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025597]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025599]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025602] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025607]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025609]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025616]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025618]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025621]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025623]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025625]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025628]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025631]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025634]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025636]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025638]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025640]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.025643]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065563] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065567] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065571] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065573] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065576] CPU: 3 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065577] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065579]  ffff8801b3979f18 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065582]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065584]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065587] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065591]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065594]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065596]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065598]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065601]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065603]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065605]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065608]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065610]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065612]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065615]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065617]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.065619]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075889] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075893] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075897] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075899] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075901] CPU: 3 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075903] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075904]  ffff8801b39795c0 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075908]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075910]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075913] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075916]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075919]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075921]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075923]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075926]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075928]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075930]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075933]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075935]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075937]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075940]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075941]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.075944]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085874] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085878] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085881] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085883] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085886] CPU: 3 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085887] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085889]  ffff8801b39795c0 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085892]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085895]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085897] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085901]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085903]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085905]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085907]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085910]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085912]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085914]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085917]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085919]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085922]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085924]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085926]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.085928]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095938] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095941] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095945] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095947] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095949] CPU: 3 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095951] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095952]  ffff8801b3979f18 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095956]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095958]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095960] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095964]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095966]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095968]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095970]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095973]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095975]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095977]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095980]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095982]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095985]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095987]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095989]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.095991]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105774] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105778] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105782] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105784] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105787] CPU: 3 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105788] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105790]  ffff8801b3979958 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105793]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105795]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105798] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105802]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105804]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105806]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105808]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105811]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105813]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105816]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105819]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105821]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105823]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105826]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105827]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.105830]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5190.135990] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88032cd25578 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5190.135994] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.135998] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136000] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136003] CPU: 3 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136004] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136005]  ffff8801b3868170 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136008]  ffff88038f877cb8 ffffffff81163e58 ffff88032cd25578 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136010]  ffff8801b3b52580 ffff88032cd25578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136013] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136017]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136020]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136023]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136025]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136027]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136030]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136032]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136034]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136037]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136040]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136042]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136044]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136046]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.136049]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145897] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88042609a7b0 pmd:1b3b52067
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145902] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145907] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145910] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145912] CPU: 3 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145914] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145915]  ffff8801b3868f18 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145919]  ffff88038f877cb8 ffffffff81163e58 ffff88042609a7b0 0000000000000cb8
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145921]  ffff8801b3b52580 ffff88042609a7b0 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145923] Call Trace:
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145929]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145931]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145934]  [<ffffffff811651c9>] vm_normal_page+0x69/0x80
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145936]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145939]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145941]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145943]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145947]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145949]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145951]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145954]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145955]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:08 miles-desktop kernel: [ 5190.145958]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716670] BUG: Bad page map in process Xorg  pte:ffff8802e7882048 pmd:1b3b52067
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716676] addr:00007f62a32b0000 vm_flags:040400fb anon_vma:          (null) mapping:ffff880423f093d0 index:144e8
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716818] vma->vm_ops->fault: ip_vm_gart_fault+0x0/0x100 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716853] vma->vm_file->f_op->mmap: ip_firegl_mmap+0x0/0x70 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716856] CPU: 1 PID: 1419 Comm: Xorg Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716858] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716860]  ffff8801b39792e0 ffff8804256877f0 ffffffff816e87f1 00007f62a32b0000
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716863]  ffff880425687838 ffffffff81163e58 ffff8802e7882048 00000000000144e8
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716865]  ffff8801b3b52580 ffff8802e7882048 00007f62a32b0000 00007f62a3400000
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716868] Call Trace:
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716880]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716884]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716887]  [<ffffffff811658d6>] unmap_page_range+0x6f6/0x7f0
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716889]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716892]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716894]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716897]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716900]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716938]  [<ffffffffa00f241e>] KCL_MEM_ReleaseLinearAddrInterval+0xe/0x10 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.716979]  [<ffffffffa011a967>] __destroy_mapping+0x187/0x230 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717051]  [<ffffffffa01c7090>] ? _ZN11NODElist_TS7addNodeEP7CMMNode14_LARGE_INTEGER12_QS_CP_RING_+0xc0/0x110 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717092]  [<ffffffffa01165c8>] ? gal_unmap_virtual_space+0x58/0xb0 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717132]  [<ffffffffa0121133>] ? __mc_heap_unmap_virtual_space+0xa3/0x150 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717173]  [<ffffffffa011bcbe>] ? mc_heap_unmap_virtual_space+0x5e/0xe0 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717213]  [<ffffffffa010faf1>] ? MCIL_FreeVirtualAddressInDescriptor+0xb1/0x160 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717281]  [<ffffffffa01dbf89>] ? _ZN2OS18freeVirtualAddressEP4AsicPvmm9_CMM_HEAPb+0x99/0xc0 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717347]  [<ffffffffa01cd8e7>] ? _ZN8CMapping13FreeOSMappingEv+0x97/0xa0 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717412]  [<ffffffffa01cd13d>] ? _ZN17SegmentMapManager5UnmapEbP4AsicP9CMMClient+0x5d/0xd0 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717477]  [<ffffffffa01cb58a>] ? _Z16CMMUnlockSurfacemP23_CMM_UNLOCK_SURF_INPUT_+0x12a/0x160 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717539]  [<ffffffffa01bc0e8>] ? _Z8uCWDDEQCmjjPvjS_+0x928/0x1240 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717543]  [<ffffffff8104def9>] ? default_spin_lock_flags+0x9/0x10
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717596]  [<ffffffffa018792a>] ? CMMQS_uCWDDEQC+0xa/0x10 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717638]  [<ffffffffa013059f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717680]  [<ffffffffa012ee3e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717684]  [<ffffffff8106b6f7>] ? capable+0x17/0x20
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717725]  [<ffffffffa012edb0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717764]  [<ffffffffa010108d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717799]  [<ffffffffa00ef1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717801]  [<ffffffff811b9f75>] ? do_vfs_ioctl+0x2e5/0x4d0
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717804]  [<ffffffff811a7e27>] ? vfs_read+0xf7/0x170
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717806]  [<ffffffff811ba1e1>] ? SyS_ioctl+0x81/0xa0
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717808]  [<ffffffff811a88f9>] ? SyS_read+0x49/0xa0
Apr 15 22:38:16 miles-desktop kernel: [ 5197.717812]  [<ffffffff816f869d>] ? system_call_fastpath+0x1a/0x1f
Apr 15 22:38:35 miles-desktop kernel: [ 5216.615955] BUG: Bad page map in process Xorg  pte:ffff8802e7882048 pmd:1b3b52067
Apr 15 22:38:35 miles-desktop kernel: [ 5216.615962] addr:00007f62a30b0000 vm_flags:040400fb anon_vma:          (null) mapping:ffff880423f093d0 index:14348
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616107] vma->vm_ops->fault: ip_vm_gart_fault+0x0/0x100 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616142] vma->vm_file->f_op->mmap: ip_firegl_mmap+0x0/0x70 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616145] CPU: 0 PID: 1419 Comm: Xorg Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616147] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616149]  ffff8801b3b68508 ffff8804256877f0 ffffffff816e87f1 00007f62a30b0000
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616152]  ffff880425687838 ffffffff81163e58 ffff8802e7882048 0000000000014348
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616154]  ffff8801b3b52580 ffff8802e7882048 00007f62a30b0000 00007f62a3200000
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616157] Call Trace:
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616165]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616170]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616172]  [<ffffffff811658d6>] unmap_page_range+0x6f6/0x7f0
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616175]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616177]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616179]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616182]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616185]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616223]  [<ffffffffa00f241e>] KCL_MEM_ReleaseLinearAddrInterval+0xe/0x10 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616264]  [<ffffffffa011a967>] __destroy_mapping+0x187/0x230 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616333]  [<ffffffffa01c7090>] ? _ZN11NODElist_TS7addNodeEP7CMMNode14_LARGE_INTEGER12_QS_CP_RING_+0xc0/0x110 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616374]  [<ffffffffa01165c8>] ? gal_unmap_virtual_space+0x58/0xb0 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616415]  [<ffffffffa0121133>] ? __mc_heap_unmap_virtual_space+0xa3/0x150 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616459]  [<ffffffffa011bcbe>] ? mc_heap_unmap_virtual_space+0x5e/0xe0 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616499]  [<ffffffffa010faf1>] ? MCIL_FreeVirtualAddressInDescriptor+0xb1/0x160 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616567]  [<ffffffffa01dbf89>] ? _ZN2OS18freeVirtualAddressEP4AsicPvmm9_CMM_HEAPb+0x99/0xc0 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616645]  [<ffffffffa01cd8e7>] ? _ZN8CMapping13FreeOSMappingEv+0x97/0xa0 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616721]  [<ffffffffa01cd13d>] ? _ZN17SegmentMapManager5UnmapEbP4AsicP9CMMClient+0x5d/0xd0 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616792]  [<ffffffffa01cb58a>] ? _Z16CMMUnlockSurfacemP23_CMM_UNLOCK_SURF_INPUT_+0x12a/0x160 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616861]  [<ffffffffa01bc0e8>] ? _Z8uCWDDEQCmjjPvjS_+0x928/0x1240 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616867]  [<ffffffff8104def9>] ? default_spin_lock_flags+0x9/0x10
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616920]  [<ffffffffa018792a>] ? CMMQS_uCWDDEQC+0xa/0x10 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.616962]  [<ffffffffa013059f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617004]  [<ffffffffa012ee3e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617014]  [<ffffffff8106b6f7>] ? capable+0x17/0x20
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617055]  [<ffffffffa012edb0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617096]  [<ffffffffa010108d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617132]  [<ffffffffa00ef1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617134]  [<ffffffff811b9f75>] ? do_vfs_ioctl+0x2e5/0x4d0
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617137]  [<ffffffff811a7e27>] ? vfs_read+0xf7/0x170
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617139]  [<ffffffff811ba1e1>] ? SyS_ioctl+0x81/0xa0
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617141]  [<ffffffff811a88f9>] ? SyS_read+0x49/0xa0
Apr 15 22:38:35 miles-desktop kernel: [ 5216.617145]  [<ffffffff816f869d>] ? system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574005] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88038f578578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574010] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574014] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574016] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574018] CPU: 0 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574020] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574021]  ffff8801b3a47000 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574025]  ffff88038f877cb8 ffffffff81163e58 ffff88038f578578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574027]  ffff8801b3b52580 ffff88038f578578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574029] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574034]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574037]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574039]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574042]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574044]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574047]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574049]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574051]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574054]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574056]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574059]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574060]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5217.574063]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584050] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88038f578578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584053] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584057] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584059] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584060] CPU: 0 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584062] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584063]  ffff8801b3868730 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584066]  ffff88038f877cb8 ffffffff81163e58 ffff88038f578578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584068]  ffff8801b3b52580 ffff88038f578578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584070] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584074]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584076]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584079]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584081]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584083]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584086]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584088]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584090]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584093]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584095]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584097]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584099]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5217.584102]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594023] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88038f578578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594026] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594030] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594032] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594034] CPU: 0 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594035] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594036]  ffff8801b3a47ac8 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594039]  ffff88038f877cb8 ffffffff81163e58 ffff88038f578578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594041]  ffff8801b3b52580 ffff88038f578578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594044] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594048]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594050]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594053]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594055]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594057]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594060]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594062]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594064]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594067]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594069]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594071]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594073]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5217.594076]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608498] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fefd578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608505] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608513] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608515] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608518] CPU: 2 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608520] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608522]  ffff8801b3a47000 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608528]  ffff88038f877cb8 ffffffff81163e58 ffff88025fefd578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608531]  ffff8801b3b52580 ffff88025fefd578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608534] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608540]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608544]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608547]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608552]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608554]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608558]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608560]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608563]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608567]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608570]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608574]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608578]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608580]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5217.608583]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025835] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025839] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025844] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025846] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025849] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025850] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025852]  ffff8801b3a47000 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025855]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025857]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025859] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025864]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025867]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025869]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025872]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025874]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025877]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025879]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025881]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025883]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025886]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025888]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025890]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.025893]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035903] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035906] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035909] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035911] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035913] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035914] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035915]  ffff8801b3b68508 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035918]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035920]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035922] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035926]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035928]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035930]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035933]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035935]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035937]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035939]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035942]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035944]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035946]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035949]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035951]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.035953]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046030] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046033] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046036] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046038] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046040] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046042] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046043]  ffff8801b3b68450 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046046]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046048]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046050] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046054]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046056]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046059]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046061]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046063]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046066]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046068]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046070]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046073]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046075]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046077]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046079]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.046081]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056012] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056015] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056018] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056021] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056023] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056025] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056026]  ffff8801b3979450 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056030]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056032]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056035] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056038]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056040]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056043]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056045]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056047]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056050]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056052]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056054]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056056]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056059]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056061]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056063]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.056065]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066135] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066147] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066151] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066158] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066161] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066162] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066164]  ffff8801b3979da8 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066167]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066170]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066173] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066177]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066187]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066190]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066192]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066194]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066197]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066199]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066202]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066210]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066212]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066214]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066216]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.066219]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076137] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076140] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076143] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076145] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076147] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076148] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076149]  ffff8801b3a47000 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076152]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076154]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076157] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076160]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076162]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076165]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076167]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076169]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076172]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076174]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076176]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076178]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076181]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076183]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076185]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.076187]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175482] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175486] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175491] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175493] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175495] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175497] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175499]  ffff8801b3979678 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175502]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175504]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175506] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175511]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175514]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175516]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175519]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175521]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175523]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175525]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175527]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175530]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175532]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175535]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175537]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175539]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.175542]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185529] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185532] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185535] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185537] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185539] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185540] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185542]  ffff8801b3b68e60 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185544]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185547]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185549] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185552]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185555]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185557]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185559]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185561]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185564]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185566]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185568]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185571]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185573]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185576]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185577]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.185580]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195749] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88025fdf3578 pmd:1b3b52067
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195755] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195761] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195764] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195767] CPU: 4 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195769] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195771]  ffff8801b3a47ac8 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195776]  ffff88038f877cb8 ffffffff81163e58 ffff88025fdf3578 00000000000002b8
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195780]  ffff8801b3b52580 ffff88025fdf3578 00007eff882b0000 00007eff88400000
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195783] Call Trace:
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195790]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195794]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195797]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195801]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195804]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195807]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195810]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195813]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195816]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195820]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195823]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195825]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:36 miles-desktop kernel: [ 5218.195829]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576200] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88021aba7578 pmd:1b3b52067
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576204] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576209] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576211] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576213] CPU: 2 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576215] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576216]  ffff8801b39795c0 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576219]  ffff88038f877cb8 ffffffff81163e58 ffff88021aba7578 00000000000002b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576221]  ffff8801b3b52580 ffff88021aba7578 00007eff882b0000 00007eff88400000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576224] Call Trace:
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576228]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576231]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576234]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576236]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576238]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576241]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576243]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576245]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576248]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576250]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576253]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576255]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.576258]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586155] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88021aba7578 pmd:1b3b52067
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586159] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586162] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586164] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586166] CPU: 2 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586167] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586168]  ffff8801b3979958 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586171]  ffff88038f877cb8 ffffffff81163e58 ffff88021aba7578 00000000000002b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586173]  ffff8801b3b52580 ffff88021aba7578 00007eff882b0000 00007eff88400000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586175] Call Trace:
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586179]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586182]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586184]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586188]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586190]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586193]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586195]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586197]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586200]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586202]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586204]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586206]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.586209]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598795] BUG: Bad page map in process webrtc_audio_mo  pte:ffff8802e7882048 pmd:1b3b52067
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598801] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598808] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598811] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598817] CPU: 2 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598819] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598821]  ffff8801b3979398 ffff88038f877c88 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598826]  ffff88038f877cd0 ffffffff81163e58 ffff8802e7882048 00000000000002b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598828]  ffff8801b3b52580 ffff8802e7882048 00007eff882b0000 00007eff88400000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598831] Call Trace:
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598839]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598843]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598846]  [<ffffffff811658d6>] unmap_page_range+0x6f6/0x7f0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598849]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598852]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598855]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598858]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598861]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598864]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598866]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598868]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.598876]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616288] BUG: Bad page map in process webrtc_audio_mo  pte:ffff8801de82a578 pmd:1b3b52067
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616292] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616297] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616299] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616302] CPU: 2 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616303] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616305]  ffff8801b3b680b8 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616308]  ffff88038f877cb8 ffffffff81163e58 ffff8801de82a578 00000000000002b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616310]  ffff8801b3b52580 ffff8801de82a578 00007eff882b0000 00007eff88400000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616313] Call Trace:
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616318]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616321]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616323]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616326]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616328]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616331]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616333]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616335]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616337]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616340]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616342]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616345]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616346]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.616349]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805247] BUG: Bad page map in process webrtc_audio_mo  pte:ffff880350e78578 pmd:1b3b52067
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805252] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805256] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805258] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805260] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805262] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805263]  ffff8801b3979170 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805266]  ffff88038f877cb8 ffffffff81163e58 ffff880350e78578 00000000000002b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805269]  ffff8801b3b52580 ffff880350e78578 00007eff882b0000 00007eff88400000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805271] Call Trace:
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805276]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805279]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805281]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805284]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805286]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805289]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805291]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805293]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805296]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805298]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805300]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805302]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.805305]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815250] BUG: Bad page map in process webrtc_audio_mo  pte:ffff880350e78578 pmd:1b3b52067
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815253] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815256] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815258] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815260] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815261] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815262]  ffff8801b3979678 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815265]  ffff88038f877cb8 ffffffff81163e58 ffff880350e78578 00000000000002b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815267]  ffff8801b3b52580 ffff880350e78578 00007eff882b0000 00007eff88400000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815269] Call Trace:
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815273]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815275]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815278]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815280]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815282]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815285]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815287]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815289]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815291]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815294]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815296]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815298]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.815300]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825254] BUG: Bad page map in process webrtc_audio_mo  pte:ffff880350e78578 pmd:1b3b52067
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825257] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825260] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825262] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825264] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825265] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825266]  ffff8801b39792e0 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825269]  ffff88038f877cb8 ffffffff81163e58 ffff880350e78578 00000000000002b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825271]  ffff8801b3b52580 ffff880350e78578 00007eff882b0000 00007eff88400000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825274] Call Trace:
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825277]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825279]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825282]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825284]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825286]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825289]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825291]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825293]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825296]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825298]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825300]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825302]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.825305]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835425] BUG: Bad page map in process webrtc_audio_mo  pte:ffff880350e78578 pmd:1b3b52067
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835428] addr:00007eff882b0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:2b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835431] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835433] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835435] CPU: 5 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835436] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835438]  ffff8801b3979da8 ffff88038f877c70 ffffffff816e87f1 00007eff882b0000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835440]  ffff88038f877cb8 ffffffff81163e58 ffff880350e78578 00000000000002b8
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835443]  ffff8801b3b52580 ffff880350e78578 00007eff882b0000 00007eff88400000
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835445] Call Trace:
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835448]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835451]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835453]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835455]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835458]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835460]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835462]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835465]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835467]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835470]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835472]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835474]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:37 miles-desktop kernel: [ 5218.835476]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842729] BUG: Bad page map in process webrtc_audio_mo  pte:ffff8802e7882048 pmd:1b3b52067
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842733] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842738] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842741] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842743] CPU: 1 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842744] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842746]  ffff8801b3868508 ffff88038f877c88 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842749]  ffff88038f877cd0 ffffffff81163e58 ffff8802e7882048 0000000000000cb8
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842751]  ffff8801b3b52580 ffff8802e7882048 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842754] Call Trace:
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842758]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842761]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842764]  [<ffffffff811658d6>] unmap_page_range+0x6f6/0x7f0
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842766]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842768]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842771]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842774]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842776]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842778]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842781]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842783]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:42 miles-desktop kernel: [ 5223.842786]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843095] BUG: Bad page map in process webrtc_audio_mo  pte:ffff8801b38bd578 pmd:1b3b52067
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843097] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843099] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843100] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843102] CPU: 1 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843103] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843104]  ffff8801b3868f18 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843107]  ffff88038f877cb8 ffffffff81163e58 ffff8801b38bd578 0000000000000cb8
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843109]  ffff8801b3b52580 ffff8801b38bd578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843111] Call Trace:
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843114]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843116]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843118]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843121]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843123]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843125]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843127]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843130]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843132]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843135]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843137]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843139]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:42 miles-desktop kernel: [ 5223.843141]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784811] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88020e831578 pmd:1b3b52067
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784816] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784820] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784822] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784825] CPU: 1 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784826] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784828]  ffff8801b3a47508 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784831]  ffff88038f877cb8 ffffffff81163e58 ffff88020e831578 0000000000000cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784833]  ffff8801b3b52580 ffff88020e831578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784835] Call Trace:
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784840]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784843]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784845]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784848]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784850]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784852]  [<ffffffff8114c910>] ? release_pages+0x1e0/0x220
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784855]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784857]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784859]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784862]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784864]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784866]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784868]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.784871]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794969] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88020e831578 pmd:1b3b52067
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794973] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794976] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794978] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794980] CPU: 1 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794982] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794983]  ffff8801b3a47ac8 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794986]  ffff88038f877cb8 ffffffff81163e58 ffff88020e831578 0000000000000cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794988]  ffff8801b3b52580 ffff88020e831578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794991] Call Trace:
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794994]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:43 miles-desktop kernel: [ 5224.794997]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795000]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795002]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795004]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795007]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795009]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795011]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795014]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795016]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795018]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795020]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.795023]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804970] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88020e831578 pmd:1b3b52067
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804973] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804977] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804979] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804981] CPU: 1 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804982] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804983]  ffff8801b3b688a0 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804986]  ffff88038f877cb8 ffffffff81163e58 ffff88020e831578 0000000000000cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804989]  ffff8801b3b52580 ffff88020e831578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804991] Call Trace:
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804995]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:43 miles-desktop kernel: [ 5224.804998]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805000]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805002]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805004]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805007]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805009]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805011]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805014]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805016]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805018]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805020]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.805023]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815076] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88020e831578 pmd:1b3b52067
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815079] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815082] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815084] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815086] CPU: 1 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815087] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815088]  ffff8801b3a47ac8 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815091]  ffff88038f877cb8 ffffffff81163e58 ffff88020e831578 0000000000000cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815093]  ffff8801b3b52580 ffff88020e831578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815095] Call Trace:
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815099]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815101]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815104]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815106]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815108]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815110]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815113]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815115]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815117]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815120]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815122]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815124]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.815126]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935587] BUG: Bad page map in process webrtc_audio_mo  pte:ffff88020e831578 pmd:1b3b52067
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935593] addr:00007eff88cb0000 vm_flags:000000d1 anon_vma:          (null) mapping:ffff8803f03b65f8 index:cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935599] vma->vm_ops->fault: shmem_fault+0x0/0xa0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935601] vma->vm_file->f_op->mmap: shmem_mmap+0x0/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935605] CPU: 1 PID: 14675 Comm: webrtc_audio_mo Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935607] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935609]  ffff8801b397bf18 ffff88038f877c70 ffffffff816e87f1 00007eff88cb0000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935613]  ffff88038f877cb8 ffffffff81163e58 ffff88020e831578 0000000000000cb8
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935616]  ffff8801b3b52580 ffff88020e831578 00007eff88cb0000 00007eff88e00000
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935620] Call Trace:
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935627]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935631]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935633]  [<ffffffff811651d9>] vm_normal_page+0x79/0x80
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935637]  [<ffffffff816efa0e>] ? _raw_spin_lock+0xe/0x20
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935640]  [<ffffffff8116558b>] unmap_page_range+0x3ab/0x7f0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935643]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935646]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935649]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935654]  [<ffffffff810c4a10>] ? do_futex+0x160/0x620
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935656]  [<ffffffff8116c751>] ? vma_rb_erase+0x121/0x220
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935659]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935662]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935665]  [<ffffffff8116f682>] SyS_munmap+0x22/0x30
Apr 15 22:38:43 miles-desktop kernel: [ 5224.935669]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:38:43 miles-desktop kernel: [ 5225.139950] BUG: Bad page map in process Xorg  pte:ffff8802e7882048 pmd:1b3b52067
Apr 15 22:38:43 miles-desktop kernel: [ 5225.139957] addr:00007f62a2eb0000 vm_flags:040400fb anon_vma:          (null) mapping:ffff880423f093d0 index:14170
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140109] vma->vm_ops->fault: ip_vm_gart_fault+0x0/0x100 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140144] vma->vm_file->f_op->mmap: ip_firegl_mmap+0x0/0x70 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140147] CPU: 1 PID: 1419 Comm: Xorg Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140149] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140151]  ffff8801b3979e60 ffff8804256877f0 ffffffff816e87f1 00007f62a2eb0000
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140155]  ffff880425687838 ffffffff81163e58 ffff8802e7882048 0000000000014170
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140157]  ffff8801b3b52580 ffff8802e7882048 00007f62a2eb0000 00007f62a3000000
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140160] Call Trace:
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140168]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140172]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140175]  [<ffffffff811658d6>] unmap_page_range+0x6f6/0x7f0
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140177]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140180]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140182]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140185]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140188]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140225]  [<ffffffffa00f241e>] KCL_MEM_ReleaseLinearAddrInterval+0xe/0x10 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140267]  [<ffffffffa011a967>] __destroy_mapping+0x187/0x230 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140337]  [<ffffffffa01c7090>] ? _ZN11NODElist_TS7addNodeEP7CMMNode14_LARGE_INTEGER12_QS_CP_RING_+0xc0/0x110 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140378]  [<ffffffffa01165c8>] ? gal_unmap_virtual_space+0x58/0xb0 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140419]  [<ffffffffa0121133>] ? __mc_heap_unmap_virtual_space+0xa3/0x150 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140460]  [<ffffffffa011bcbe>] ? mc_heap_unmap_virtual_space+0x5e/0xe0 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140500]  [<ffffffffa010faf1>] ? MCIL_FreeVirtualAddressInDescriptor+0xb1/0x160 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140569]  [<ffffffffa01dbf89>] ? _ZN2OS18freeVirtualAddressEP4AsicPvmm9_CMM_HEAPb+0x99/0xc0 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140636]  [<ffffffffa01cd8e7>] ? _ZN8CMapping13FreeOSMappingEv+0x97/0xa0 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140701]  [<ffffffffa01cd13d>] ? _ZN17SegmentMapManager5UnmapEbP4AsicP9CMMClient+0x5d/0xd0 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140766]  [<ffffffffa01cb58a>] ? _Z16CMMUnlockSurfacemP23_CMM_UNLOCK_SURF_INPUT_+0x12a/0x160 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140828]  [<ffffffffa01bc0e8>] ? _Z8uCWDDEQCmjjPvjS_+0x928/0x1240 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140832]  [<ffffffff8104def9>] ? default_spin_lock_flags+0x9/0x10
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140890]  [<ffffffffa018792a>] ? CMMQS_uCWDDEQC+0xa/0x10 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140932]  [<ffffffffa013059f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140975]  [<ffffffffa012ee3e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.140978]  [<ffffffff8106b6f7>] ? capable+0x17/0x20
Apr 15 22:38:43 miles-desktop kernel: [ 5225.141020]  [<ffffffffa012edb0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.141058]  [<ffffffffa010108d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.141094]  [<ffffffffa00ef1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
Apr 15 22:38:43 miles-desktop kernel: [ 5225.141096]  [<ffffffff811b9f75>] ? do_vfs_ioctl+0x2e5/0x4d0
Apr 15 22:38:43 miles-desktop kernel: [ 5225.141099]  [<ffffffff811a7e27>] ? vfs_read+0xf7/0x170
Apr 15 22:38:43 miles-desktop kernel: [ 5225.141101]  [<ffffffff811ba1e1>] ? SyS_ioctl+0x81/0xa0
Apr 15 22:38:43 miles-desktop kernel: [ 5225.141103]  [<ffffffff811a88f9>] ? SyS_read+0x49/0xa0
Apr 15 22:38:43 miles-desktop kernel: [ 5225.141107]  [<ffffffff816f869d>] ? system_call_fastpath+0x1a/0x1f
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902127] BUG: Bad page map in process Xorg  pte:ffff8802e7882048 pmd:1b3b52067
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902133] addr:00007f62a2eb0000 vm_flags:040400fb anon_vma:          (null) mapping:ffff880423f093d0 index:14178
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902287] vma->vm_ops->fault: ip_vm_gart_fault+0x0/0x100 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902322] vma->vm_file->f_op->mmap: ip_firegl_mmap+0x0/0x70 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902325] CPU: 1 PID: 1419 Comm: Xorg Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902327] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902328]  ffff8801b39792e0 ffff8804256877f0 ffffffff816e87f1 00007f62a2eb0000
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902332]  ffff880425687838 ffffffff81163e58 ffff8802e7882048 0000000000014178
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902334]  ffff8801b3b52580 ffff8802e7882048 00007f62a2eb0000 00007f62a3000000
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902337] Call Trace:
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902344]  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902349]  [<ffffffff81163e58>] print_bad_pte+0x1a8/0x240
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902351]  [<ffffffff811658d6>] unmap_page_range+0x6f6/0x7f0
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902354]  [<ffffffff81165a51>] unmap_single_vma+0x81/0xf0
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902356]  [<ffffffff81166ad9>] unmap_vmas+0x49/0x90
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902359]  [<ffffffff8116c1dd>] unmap_region+0x9d/0x110
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902362]  [<ffffffff8116e586>] do_munmap+0x226/0x3b0
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902364]  [<ffffffff8116e751>] vm_munmap+0x41/0x60
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902402]  [<ffffffffa00f241e>] KCL_MEM_ReleaseLinearAddrInterval+0xe/0x10 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902444]  [<ffffffffa011a967>] __destroy_mapping+0x187/0x230 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902513]  [<ffffffffa01c7090>] ? _ZN11NODElist_TS7addNodeEP7CMMNode14_LARGE_INTEGER12_QS_CP_RING_+0xc0/0x110 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902554]  [<ffffffffa01165c8>] ? gal_unmap_virtual_space+0x58/0xb0 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902594]  [<ffffffffa0121133>] ? __mc_heap_unmap_virtual_space+0xa3/0x150 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902634]  [<ffffffffa011bcbe>] ? mc_heap_unmap_virtual_space+0x5e/0xe0 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902673]  [<ffffffffa010faf1>] ? MCIL_FreeVirtualAddressInDescriptor+0xb1/0x160 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902740]  [<ffffffffa01dbf89>] ? _ZN2OS18freeVirtualAddressEP4AsicPvmm9_CMM_HEAPb+0x99/0xc0 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902805]  [<ffffffffa01cd8e7>] ? _ZN8CMapping13FreeOSMappingEv+0x97/0xa0 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902869]  [<ffffffffa01cd13d>] ? _ZN17SegmentMapManager5UnmapEbP4AsicP9CMMClient+0x5d/0xd0 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902933]  [<ffffffffa01cb58a>] ? _Z16CMMUnlockSurfacemP23_CMM_UNLOCK_SURF_INPUT_+0x12a/0x160 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902995]  [<ffffffffa01bc0e8>] ? _Z8uCWDDEQCmjjPvjS_+0x928/0x1240 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.902998]  [<ffffffff8104def9>] ? default_spin_lock_flags+0x9/0x10
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903050]  [<ffffffffa018792a>] ? CMMQS_uCWDDEQC+0xa/0x10 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903091]  [<ffffffffa013059f>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903133]  [<ffffffffa012ee3e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903136]  [<ffffffff8106b6f7>] ? capable+0x17/0x20
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903177]  [<ffffffffa012edb0>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903214]  [<ffffffffa010108d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903250]  [<ffffffffa00ef1de>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903252]  [<ffffffff811b9f75>] ? do_vfs_ioctl+0x2e5/0x4d0
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903255]  [<ffffffff811a7e27>] ? vfs_read+0xf7/0x170
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903256]  [<ffffffff811ba1e1>] ? SyS_ioctl+0x81/0xa0
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903258]  [<ffffffff811a88f9>] ? SyS_read+0x49/0xa0
Apr 15 22:38:44 miles-desktop kernel: [ 5225.903262]  [<ffffffff816f869d>] ? system_call_fastpath+0x1a/0x1f
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445767] BUG: unable to handle kernel NULL pointer dereference at           (null)
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445771] IP: [<          (null)>]           (null)
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445774] PGD 34814a067 PUD 0 
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445776] Oops: 0010 [#1] SMP 
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445778] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) dm_crypt parport_pc ppdev eeepc_wmi asus_wmi sparse_keymap video kvm_amd kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_usb_audio snd_usbmidi_lib joydev rfcomm bnep aesni_intel aes_x86_64 lrw bluetooth gf128mul glue_helper snd_hda_codec_hdmi ablk_helper cryptd snd_hda_codec_realtek microcode snd_hda_intel snd_hda_codec snd_hwdep psmouse serio_raw snd_pcm edac_core k10temp edac_mce_amd fam15h_power snd_page_alloc sp5100_tco snd_seq_midi i2c_piix4 snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device fglrx(POF) snd_timer snd it87 hwmon_vid amd_iommu_v2 soundcore lp parport mac_hid binfmt_misc hid_generic usbhid hid mxm_wmi firewire_ohci firewire_core crc_itu_t ahci libahci r8169 mii wmi
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445811] CPU: 4 PID: 14709 Comm: skype Tainted: PF   B      O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445813] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445814] task: ffff8802b5c91770 ti: ffff8802e7904000 task.ti: ffff8802e7904000
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445816] RIP: 0010:[<0000000000000000>]  [<          (null)>]           (null)
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445817] RSP: 0018:ffff8802e79059c0  EFLAGS: 00210002
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445819] RAX: ffff8801b3b52560 RBX: 0000000000000000 RCX: 0000000000000304
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445820] RDX: 0000000000000001 RSI: 0000000000000001 RDI: ffff8801b3b52560
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445821] RBP: ffff8802e7905a00 R08: 0000000000000304 R09: 0000000000000000
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445822] R10: ffff88042e010430 R11: 0000000000200293 R12: ffff8802e7882048
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445823] R13: ffffffffffffffe8 R14: 0000000000000001 R15: 0000000000000001
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445824] FS:  00007fc074997700(0000) GS:ffff88043ed00000(0063) knlGS:00000000f59dda40
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445826] CS:  0010 DS: 002b ES: 002b CR0: 000000008005003b
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445827] CR2: 0000000000000000 CR3: 0000000423416000 CR4: 00000000000407e0
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445828] Stack:
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445829]  ffffffff8108d3c8 00000001810915b0 0000000000000304 ffff8802e7882040
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445832]  0000000000000001 0000000000000001 0000000000000304 0000000000200282
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445834]  ffff8802e7905a38 ffffffff8108ee34 ffff880315e7e800 ffff880315e7e8f4
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445837] Call Trace:
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445841]  [<ffffffff8108d3c8>] ? __wake_up_common+0x58/0x90
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445845]  [<ffffffff8108ee34>] __wake_up_sync_key+0x44/0x60
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445848]  [<ffffffff81683c3b>] unix_write_space+0x4b/0x80
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445850]  [<ffffffff815df8bb>] sock_wfree+0x5b/0x70
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445852]  [<ffffffff816846c1>] unix_destruct_scm+0x71/0x80
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445854]  [<ffffffff815e39f6>] skb_release_head_state+0x66/0xe0
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445856]  [<ffffffff815e3c82>] skb_release_all+0x12/0x30
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445858]  [<ffffffff815e3edc>] consume_skb+0x2c/0x80
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445860]  [<ffffffff81684e7f>] unix_stream_recvmsg+0x52f/0x860
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445863]  [<ffffffff815dbb98>] sock_recvmsg+0xa8/0xe0
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445867]  [<ffffffff811b2652>] ? __inode_permission+0x52/0xc0
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445869]  [<ffffffff811b26d8>] ? inode_permission+0x18/0x50
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445871]  [<ffffffff811b42cc>] ? link_path_walk+0x7c/0x8b0
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445874]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445876]  [<ffffffff815dbeb0>] ___sys_recvmsg+0x120/0x2b0
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445878]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445880]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445882]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445884]  [<ffffffff8109a3a5>] ? set_next_entity+0x95/0xb0
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445887]  [<ffffffff810118bf>] ? __switch_to+0x41f/0x4b0
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445890]  [<ffffffff815dc992>] __sys_recvmsg+0x42/0x80
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445893]  [<ffffffff81610321>] compat_sys_socketcall+0x71/0x260
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445895]  [<ffffffff816fa5ac>] cstar_dispatch+0x7/0x21
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445896] Code:  Bad RIP value.
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445900] RIP  [<          (null)>]           (null)
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445901]  RSP <ffff8802e79059c0>
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445903] CR2: 0000000000000000
Apr 15 22:38:47 miles-desktop kernel: [ 5228.445905] ---[ end trace 15336a262fd42304 ]---
Apr 15 22:39:01 miles-desktop CRON[25281]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr/lib/php5/maxlifetime))
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892387] ------------[ cut here ]------------
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892395] WARNING: CPU: 0 PID: 1419 at /build/buildd/linux-3.11.0/kernel/watchdog.c:245 watchdog_overflow_callback+0x9c/0xd0()
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892396] Watchdog detected hard LOCKUP on cpu 0
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892398] Modules linked in: pci_stub vboxpci(OF) vboxnetadp(OF) vboxnetflt(OF) vboxdrv(OF) dm_crypt parport_pc ppdev eeepc_wmi asus_wmi sparse_keymap video kvm_amd kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel snd_usb_audio snd_usbmidi_lib joydev rfcomm bnep aesni_intel aes_x86_64 lrw bluetooth gf128mul glue_helper snd_hda_codec_hdmi ablk_helper cryptd snd_hda_codec_realtek microcode snd_hda_intel snd_hda_codec snd_hwdep psmouse serio_raw snd_pcm edac_core k10temp edac_mce_amd fam15h_power snd_page_alloc sp5100_tco snd_seq_midi i2c_piix4 snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device fglrx(POF) snd_timer snd it87 hwmon_vid amd_iommu_v2 soundcore lp parport mac_hid binfmt_misc hid_generic usbhid hid mxm_wmi firewire_ohci firewire_core crc_itu_t ahci libahci r8169 mii wmi
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892436] CPU: 0 PID: 1419 Comm: Xorg Tainted: PF   B D    O 3.11.0-19-generic #33-Ubuntu
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892438] Hardware name: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892439]  0000000000000009 ffff88043ec06c40 ffffffff816e87f1 ffff88043ec06c88
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892442]  ffff88043ec06c78 ffffffff81061e2d ffff88042e012800 0000000000000000
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892444]  ffff88043ec06d90 0000000000000000 ffff88043ec06ef8 ffff88043ec06cd8
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892447] Call Trace:
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892448]  <NMI>  [<ffffffff816e87f1>] dump_stack+0x45/0x56
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892456]  [<ffffffff81061e2d>] warn_slowpath_common+0x7d/0xa0
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892458]  [<ffffffff81061e9c>] warn_slowpath_fmt+0x4c/0x50
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892461]  [<ffffffff8101a3b5>] ? native_sched_clock+0x15/0x80
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892463]  [<ffffffff8101a429>] ? sched_clock+0x9/0x10
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892465]  [<ffffffff810f5950>] ? watchdog_enable_all_cpus.part.2+0x40/0x40
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892467]  [<ffffffff810f59ec>] watchdog_overflow_callback+0x9c/0xd0
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892470]  [<ffffffff811363ce>] __perf_event_overflow+0x8e/0x220
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892472]  [<ffffffff81135199>] ? perf_event_update_userpage+0x19/0x100
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892474]  [<ffffffff81136f14>] perf_event_overflow+0x14/0x20
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892476]  [<ffffffff81028039>] x86_pmu_handle_irq+0x139/0x180
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892480]  [<ffffffff816f19eb>] perf_event_nmi_handler+0x2b/0x50
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892481]  [<ffffffff816f10c8>] nmi_handle.isra.3+0x88/0x180
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892483]  [<ffffffff816f1339>] do_nmi+0x179/0x330
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892485]  [<ffffffff816f0641>] end_repeat_nmi+0x1e/0x2e
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892488]  [<ffffffff8104de62>] ? __ticket_spin_lock+0x22/0x30
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892490]  [<ffffffff8104de62>] ? __ticket_spin_lock+0x22/0x30
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892493]  [<ffffffff8104de62>] ? __ticket_spin_lock+0x22/0x30
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892494]  <<EOE>>  [<ffffffff8104def9>] default_spin_lock_flags+0x9/0x10
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892498]  [<ffffffff816efa43>] _raw_spin_lock_irqsave+0x23/0x30
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892501]  [<ffffffff810852ea>] add_wait_queue+0x1a/0x50
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892503]  [<ffffffff811ba95f>] __pollwait+0x7f/0xf0
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892506]  [<ffffffff816846f9>] unix_poll+0x29/0xb0
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892509]  [<ffffffff815db1a0>] sock_poll+0xf0/0x100
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892511]  [<ffffffff811bb1e5>] do_select+0x395/0x7a0
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892513]  [<ffffffff811ba8e0>] ? poll_initwait+0x50/0x50
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892516]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892518]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892520]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892522]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892523]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892525]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892527]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892529]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892531]  [<ffffffff811baba0>] ? poll_select_copy_remaining+0x130/0x130
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892533]  [<ffffffff811bb7bc>] core_sys_select+0x1cc/0x2e0
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892536]  [<ffffffff8104def9>] ? default_spin_lock_flags+0x9/0x10
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892540]  [<ffffffff8108a052>] ? up+0x32/0x50
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892615]  [<ffffffffa00f1f5e>] ? KCL_SEMAPHORE_Up+0xe/0x10 [fglrx]
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892658]  [<ffffffffa0131bf4>] ? firegl_asyncio_read+0x94/0x220 [fglrx]
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892661]  [<ffffffff81019ea9>] ? read_tsc+0x9/0x20
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892663]  [<ffffffff810b7e08>] ? ktime_get_ts+0x48/0xe0
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892666]  [<ffffffff811bb97b>] SyS_select+0xab/0x100
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892669]  [<ffffffff816f869d>] system_call_fastpath+0x1a/0x1f
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892670] ---[ end trace 15336a262fd42305 ]---
Apr 15 22:39:39 miles-desktop kernel: [ 5257.892672] perf samples too long (3138 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Apr 15 22:39:39 miles-desktop kernel: [ 5280.653143] SysRq : This sysrq operation is disabled.
Apr 15 22:39:39 miles-desktop kernel: [ 5281.040492] SysRq : This sysrq operation is disabled.
Apr 15 22:39:40 miles-desktop kernel: [ 5281.285082] SysRq : This sysrq operation is disabled.
Apr 15 22:39:41 miles-desktop kernel: [ 5282.341323] SysRq : Emergency Sync
Apr 15 22:39:41 miles-desktop kernel: [ 5282.792565] SysRq : Emergency Remount R/O
Apr 16 04:41:28 miles-desktop kernel: imklog 5.8.11, log source = /proc/kmsg started.
Apr 16 04:41:28 miles-desktop rsyslogd: [origin software="rsyslogd" swVersion="5.8.11" x-pid="4382" x-info="http://www.rsyslog.com"] start
Apr 16 04:41:28 miles-desktop rsyslogd: rsyslogd's groupid changed to 103
Apr 16 04:41:28 miles-desktop rsyslogd: rsyslogd's userid changed to 101
Apr 16 04:41:28 miles-desktop rsyslogd-2039: Could not open output pipe '/dev/xconsole' [try [http://www.rsyslog.com/e/2039](http://www.rsyslog.com/e/2039) ]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Initializing cgroup subsys cpuset
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Initializing cgroup subsys cpu
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Initializing cgroup subsys cpuacct
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Linux version 3.11.0-19-generic (buildd@comet) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 (Ubuntu 3.11.0-19.33-generic 3.11.10.5)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-19-generic root=UUID=c5843ff0-1e81-4ec2-8655-107a19dcec52 ro recovery nomodeset
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] KERNEL supported cpus:
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   Intel GenuineIntel
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   AMD AuthenticAMD
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   Centaur CentaurHauls
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bd838fff] usable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bd839000-0x00000000bd888fff] ACPI NVS
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bd889000-0x00000000bd892fff] ACPI data
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bd893000-0x00000000bdaddfff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bdade000-0x00000000bdaeefff] ACPI NVS
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bdaef000-0x00000000bdb01fff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bdb02000-0x00000000bdb03fff] ACPI NVS
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bdb04000-0x00000000bdb0cfff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bdb0d000-0x00000000bdb12fff] ACPI NVS
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bdb13000-0x00000000bdb74fff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bdb75000-0x00000000bdd77fff] ACPI NVS
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000bdd78000-0x00000000bdefffff] usable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec20000-0x00000000fec20fff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed00fff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed61000-0x00000000fed70fff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed8ffff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x00000000fef00000-0x00000000ffffffff] reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BIOS-e820: [mem 0x0000000100001000-0x000000043effffff] usable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] NX (Execute Disable) protection: active
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] SMBIOS 2.7 present.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] DMI: To be filled by O.E.M. To be filled by O.E.M./M5A99X EVO, BIOS 0705 08/23/2011
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] No AGP bridge found
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] e820: last_pfn = 0x43f000 max_arch_pfn = 0x400000000
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] MTRR default type: uncachable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] MTRR fixed ranges enabled:
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   00000-9FFFF write-back
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   A0000-BFFFF write-through
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   C0000-D2FFF write-protect
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   D3000-EBFFF uncachable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   EC000-FFFFF write-protect
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] MTRR variable ranges enabled:
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   2 base 0000BDF00000 mask FFFFFFF00000 uncachable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   3 base 0000BE000000 mask FFFFFE000000 uncachable
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   4 disabled
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   5 disabled
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   6 disabled
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   7 disabled
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] TOM2: 000000043f000000 aka 17392M
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] original variable MTRRs
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] reg 2, base: 3039MB, range: 1MB, type UC
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] reg 3, base: 3040MB, range: 32MB, type UC
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] total RAM covered: 3039M
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Found optimal setting for mtrr clean up
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  gran_size: 64K     chunk_size: 64M     num_reg: 4      lose cover RAM: 0G
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] New variable MTRRs
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] reg 0, base: 0GB, range: 2GB, type WB
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] reg 1, base: 2GB, range: 1GB, type WB
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] reg 2, base: 3039MB, range: 1MB, type UC
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] reg 3, base: 3040MB, range: 32MB, type UC
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] e820: update [mem 0xbdf00000-0xffffffff] usable ==> reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] e820: last_pfn = 0xbdf00 max_arch_pfn = 0x400000000
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Scanning 1 areas for low memory corruption
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Using GB pages for direct mapping
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x00000000-0x000fffff] page 4k
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] init_memory_mapping: [mem 0x43ee00000-0x43effffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x43ee00000-0x43effffff] page 2M
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] init_memory_mapping: [mem 0x43c000000-0x43edfffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x43c000000-0x43edfffff] page 2M
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] init_memory_mapping: [mem 0x400000000-0x43bffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x400000000-0x43bffffff] page 2M
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] init_memory_mapping: [mem 0x00100000-0xbd838fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x00100000-0x001fffff] page 4k
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x00200000-0x3fffffff] page 2M
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x40000000-0x7fffffff] page 1G
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x80000000-0xbd7fffff] page 2M
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0xbd800000-0xbd838fff] page 4k
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] init_memory_mapping: [mem 0xbdd78000-0xbdefffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0xbdd78000-0xbdefffff] page 4k
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] BRK [0x01fd7000, 0x01fd7fff] PGTABLE
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] init_memory_mapping: [mem 0x100001000-0x3ffffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x100001000-0x1001fffff] page 4k
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x100200000-0x13fffffff] page 2M
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [mem 0x140000000-0x3ffffffff] page 1G
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] RAMDISK: [mem 0x34f72000-0x367b0fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: RSDP 00000000000f0450 00024 (v02 ALASKA)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: XSDT 00000000bd889068 0004C (v01 ALASKA    A M I 01072009 AMI  00010013)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: FACP 00000000bd891d00 000F4 (v04 ALASKA    A M I 01072009 AMI  00010013)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20130517/tbfadt-603)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: DSDT 00000000bd889140 08BBD (v02 ALASKA    A M I 00000000 INTL 20051117)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: FACS 00000000bdb0df80 00040
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: APIC 00000000bd891df8 0009E (v03 ALASKA    A M I 01072009 AMI  00010013)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: MCFG 00000000bd891e98 0003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: HPET 00000000bd891ed8 00038 (v01 ALASKA    A M I 01072009 AMI  00000004)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: SSDT 00000000bd891f10 0024C (v01 AMD    POWERNOW 00000001 AMD  00000001)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] No NUMA configuration found
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000043effffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Initmem setup node 0 [mem 0x00000000-0x43effffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   NODE_DATA [mem 0x43eff7000-0x43effbfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]  [ffffea0000000000-ffffea0010ffffff] PMD -> [ffff88042e600000-ffff88043e5fffff] on node 0
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Zone ranges:
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   Normal   [mem 0x100000000-0x43effffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Movable zone start for each node
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Early memory node ranges
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   node   0: [mem 0x00001000-0x0009cfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   node   0: [mem 0x00100000-0xbd838fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   node   0: [mem 0xbdd78000-0xbdefffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   node   0: [mem 0x100001000-0x43effffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] On node 0 totalpages: 4180316
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   DMA zone: 21 pages reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   DMA zone: 3996 pages, LIFO batch:0
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   DMA32 zone: 12072 pages used for memmap
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   DMA32 zone: 772545 pages, LIFO batch:31
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   Normal zone: 53184 pages used for memmap
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]   Normal zone: 3403775 pages, LIFO batch:31
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] disabled)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x08] disabled)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x10] enabled)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x11] enabled)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x12] enabled)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x13] enabled)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] enabled)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] enabled)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x07] address[0xfec00000] gsi_base[0])
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] IOAPIC[0]: apic_id 7, version 33, address 0xfec00000, GSI 0-23
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec20000] gsi_base[24])
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] IOAPIC[1]: apic_id 8, version 33, address 0xfec20000, GSI 24-55
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: IRQ0 used by override.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: IRQ2 used by override.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: IRQ9 used by override.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] ACPI: HPET id: 0xffffffff base: 0xfed00000
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] smpboot: Allowing 8 CPUs, 2 hotplug CPUs
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] nr_irqs_gsi: 72
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009d000-0x0009dfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbd839000-0xbd888fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbd889000-0xbd892fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbd893000-0xbdaddfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbdade000-0xbdaeefff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbdaef000-0xbdb01fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbdb02000-0xbdb03fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbdb04000-0xbdb0cfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbdb0d000-0xbdb12fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbdb13000-0xbdb74fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbdb75000-0xbdd77fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xbdf00000-0xfebfffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfec1ffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec20000-0xfec20fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec21000-0xfecfffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed60fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed61000-0xfed70fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed71000-0xfed7ffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeefffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfef00000-0xffffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] e820: [mem 0xbdf00000-0xfebfffff] available for PCI devices
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88043ec00000 s86720 r8192 d23872 u262144
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] pcpu-alloc: s86720 r8192 d23872 u262144 alloc=1*2097152
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 4114975
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Policy zone: Normal
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-19-generic root=UUID=c5843ff0-1e81-4ec2-8655-107a19dcec52 ro recovery nomodeset
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] xsave: enabled xstate_bv 0x7, cntxt size 0x340
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Checking aperture...
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] No AGP bridge found
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Node 0: aperture @ b4000000 size 32 MB
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Aperture pointing to e820 RAM. Ignoring.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Your BIOS doesn't leave a aperture memory hole
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Please enable the IOMMU option in the BIOS setup
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] This costs you 64 MB of RAM
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Mapping aperture over 65536 KB of RAM @ b4000000
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] PM: Registered nosave memory: [mem 0xb4000000-0xb7ffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Memory: 16285176K/16721264K available (7154K kernel code, 1083K rwdata, 3312K rodata, 1368K init, 1420K bss, 436088K reserved)
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Hierarchical RCU implementation.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]     Offload RCU callbacks from all CPUs
Apr 16 04:41:28 miles-desktop kernel: [    0.000000]     Offload RCU callbacks from CPUs: 0-255.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] NR_IRQS:16640 nr_irqs:1288 16
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] spurious 8259A interrupt: IRQ7.
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] Console: colour VGA+ 80x25
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] console [tty0] enabled
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] allocated 67108864 bytes of page_cgroup
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] hpet clockevent registered
Apr 16 04:41:28 miles-desktop kernel: [    0.000000] tsc: Fast TSC calibration using PIT
Apr 16 04:41:28 miles-desktop kernel: [    0.004000] tsc: Detected 4139.077 MHz processor
Apr 16 04:41:28 miles-desktop kernel: [    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 8278.15 BogoMIPS (lpj=16556308)
Apr 16 04:41:28 miles-desktop kernel: [    0.000080] pid_max: default: 32768 minimum: 301
Apr 16 04:41:28 miles-desktop kernel: [    0.000139] Security Framework initialized
Apr 16 04:41:28 miles-desktop kernel: [    0.000192] AppArmor: AppArmor initialized
Apr 16 04:41:28 miles-desktop kernel: [    0.000230] Yama: becoming mindful.
Apr 16 04:41:28 miles-desktop kernel: [    0.001149] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.004785] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.006456] Mount-cache hash table entries: 256
Apr 16 04:41:28 miles-desktop kernel: [    0.006646] Initializing cgroup subsys memory
Apr 16 04:41:28 miles-desktop kernel: [    0.006691] Initializing cgroup subsys devices
Apr 16 04:41:28 miles-desktop kernel: [    0.006730] Initializing cgroup subsys freezer
Apr 16 04:41:28 miles-desktop kernel: [    0.006768] Initializing cgroup subsys blkio
Apr 16 04:41:28 miles-desktop kernel: [    0.006805] Initializing cgroup subsys perf_event
Apr 16 04:41:28 miles-desktop kernel: [    0.006844] Initializing cgroup subsys hugetlb
Apr 16 04:41:28 miles-desktop kernel: [    0.006895] tseg: 00bdf00000
Apr 16 04:41:28 miles-desktop kernel: [    0.006897] CPU: Physical Processor ID: 0
Apr 16 04:41:28 miles-desktop kernel: [    0.006934] CPU: Processor Core ID: 0
Apr 16 04:41:28 miles-desktop kernel: [    0.006973] mce: CPU supports 7 MCE banks
Apr 16 04:41:28 miles-desktop kernel: [    0.007014] LVT offset 1 assigned for vector 0xf9
Apr 16 04:41:28 miles-desktop kernel: [    0.007056] Last level iTLB entries: 4KB 512, 2MB 1024, 4MB 512
Apr 16 04:41:28 miles-desktop kernel: [    0.007056] Last level dTLB entries: 4KB 1024, 2MB 1024, 4MB 512
Apr 16 04:41:28 miles-desktop kernel: [    0.007056] tlb_flushall_shift: 5
Apr 16 04:41:28 miles-desktop kernel: [    0.007173] Freeing SMP alternatives memory: 28K (ffffffff81e66000 - ffffffff81e6d000)
Apr 16 04:41:28 miles-desktop kernel: [    0.008533] ACPI: Core revision 20130517
Apr 16 04:41:28 miles-desktop kernel: [    0.010809] ACPI: All ACPI Tables successfully acquired
Apr 16 04:41:28 miles-desktop kernel: [    0.107207] ftrace: allocating 27857 entries in 109 pages
Apr 16 04:41:28 miles-desktop kernel: [    0.116545] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Apr 16 04:41:28 miles-desktop kernel: [    0.156204] smpboot: CPU0: AMD FX(tm)-6100 Six-Core Processor (fam: 15, model: 01, stepping: 02)
Apr 16 04:41:28 miles-desktop kernel: [    0.262946] Performance Events: Fam15h core perfctr, AMD PMU driver.
Apr 16 04:41:28 miles-desktop kernel: [    0.263086] ... version:                0
Apr 16 04:41:28 miles-desktop kernel: [    0.263124] ... bit width:              48
Apr 16 04:41:28 miles-desktop kernel: [    0.263161] ... generic registers:      6
Apr 16 04:41:28 miles-desktop kernel: [    0.263199] ... value mask:             0000ffffffffffff
Apr 16 04:41:28 miles-desktop kernel: [    0.263237] ... max period:             00007fffffffffff
Apr 16 04:41:28 miles-desktop kernel: [    0.263275] ... fixed-purpose events:   0
Apr 16 04:41:28 miles-desktop kernel: [    0.263312] ... event mask:             000000000000003f
Apr 16 04:41:28 miles-desktop kernel: [    0.264679] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
Apr 16 04:41:28 miles-desktop kernel: [    0.264781] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5
Apr 16 04:41:28 miles-desktop kernel: [    0.330707] Brought up 6 CPUs
Apr 16 04:41:28 miles-desktop kernel: [    0.330782] smpboot: Total of 6 processors activated (49668.92 BogoMIPS)
Apr 16 04:41:28 miles-desktop kernel: [    0.339666] devtmpfs: initialized
Apr 16 04:41:28 miles-desktop kernel: [    0.341433] EVM: security.selinux
Apr 16 04:41:28 miles-desktop kernel: [    0.341471] EVM: security.SMACK64
Apr 16 04:41:28 miles-desktop kernel: [    0.341508] EVM: security.capability
Apr 16 04:41:28 miles-desktop kernel: [    0.341602] PM: Registering ACPI NVS region [mem 0xbd839000-0xbd888fff] (327680 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.341651] PM: Registering ACPI NVS region [mem 0xbdade000-0xbdaeefff] (69632 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.341695] PM: Registering ACPI NVS region [mem 0xbdb02000-0xbdb03fff] (8192 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.341737] PM: Registering ACPI NVS region [mem 0xbdb0d000-0xbdb12fff] (24576 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.341780] PM: Registering ACPI NVS region [mem 0xbdb75000-0xbdd77fff] (2109440 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.342592] regulator-dummy: no parameters
Apr 16 04:41:28 miles-desktop kernel: [    0.342651] RTC time:  4:40:33, date: 04/16/14
Apr 16 04:41:28 miles-desktop kernel: [    0.342723] NET: Registered protocol family 16
Apr 16 04:41:28 miles-desktop kernel: [    0.342905] ACPI: bus type PCI registered
Apr 16 04:41:28 miles-desktop kernel: [    0.342943] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Apr 16 04:41:28 miles-desktop kernel: [    0.343027] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr 16 04:41:28 miles-desktop kernel: [    0.343072] PCI: not using MMCONFIG
Apr 16 04:41:28 miles-desktop kernel: [    0.343109] PCI: Using configuration type 1 for base access
Apr 16 04:41:28 miles-desktop kernel: [    0.343147] PCI: Using configuration type 1 for extended access
Apr 16 04:41:28 miles-desktop kernel: [    0.344183] bio: create slab <bio-0> at 0
Apr 16 04:41:28 miles-desktop kernel: [    0.344377] ACPI: Added _OSI(Module Device)
Apr 16 04:41:28 miles-desktop kernel: [    0.344416] ACPI: Added _OSI(Processor Device)
Apr 16 04:41:28 miles-desktop kernel: [    0.344453] ACPI: Added _OSI(3.0 _SCP Extensions)
Apr 16 04:41:28 miles-desktop kernel: [    0.344491] ACPI: Added _OSI(Processor Aggregator Device)
Apr 16 04:41:28 miles-desktop kernel: [    0.345611] ACPI: EC: Look up EC in DSDT
Apr 16 04:41:28 miles-desktop kernel: [    0.346715] ACPI: Executed 2 blocks of module-level executable AML code
Apr 16 04:41:28 miles-desktop kernel: [    0.351271] ACPI: Interpreter enabled
Apr 16 04:41:28 miles-desktop kernel: [    0.351316] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
Apr 16 04:41:28 miles-desktop kernel: [    0.351436] ACPI: (supports S0 S1 S3 S4 S5)
Apr 16 04:41:28 miles-desktop kernel: [    0.351474] ACPI: Using IOAPIC for interrupt routing
Apr 16 04:41:28 miles-desktop kernel: [    0.351637] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
Apr 16 04:41:28 miles-desktop kernel: [    0.351714] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
Apr 16 04:41:28 miles-desktop kernel: [    0.365046] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Apr 16 04:41:28 miles-desktop kernel: [    0.365195] ACPI: No dock devices found.
Apr 16 04:41:28 miles-desktop kernel: [    0.374479] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
Apr 16 04:41:28 miles-desktop kernel: [    0.374521] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
Apr 16 04:41:28 miles-desktop kernel: [    0.374565] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
Apr 16 04:41:28 miles-desktop kernel: [    0.374955] PCI host bridge to bus 0000:00
Apr 16 04:41:28 miles-desktop kernel: [    0.374995] pci_bus 0000:00: root bus resource [bus 00-ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.375033] pci_bus 0000:00: root bus resource [io  0x0000-0x03af]
Apr 16 04:41:28 miles-desktop kernel: [    0.375072] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7]
Apr 16 04:41:28 miles-desktop kernel: [    0.375110] pci_bus 0000:00: root bus resource [io  0x03b0-0x03df]
Apr 16 04:41:28 miles-desktop kernel: [    0.375149] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.375187] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.375226] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000dffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.375265] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xffffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.375313] pci 0000:00:00.0: [1002:5a14] type 00 class 0x060000
Apr 16 04:41:28 miles-desktop kernel: [    0.375433] pci 0000:00:02.0: [1002:5a16] type 01 class 0x060400
Apr 16 04:41:28 miles-desktop kernel: [    0.375466] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.375518] pci 0000:00:02.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.375581] pci 0000:00:04.0: [1002:5a18] type 01 class 0x060400
Apr 16 04:41:28 miles-desktop kernel: [    0.375614] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.375665] pci 0000:00:04.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.375726] pci 0000:00:05.0: [1002:5a19] type 01 class 0x060400
Apr 16 04:41:28 miles-desktop kernel: [    0.375758] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.375810] pci 0000:00:05.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.375871] pci 0000:00:06.0: [1002:5a1a] type 01 class 0x060400
Apr 16 04:41:28 miles-desktop kernel: [    0.375902] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.375953] pci 0000:00:06.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.376017] pci 0000:00:07.0: [1002:5a1b] type 01 class 0x060400
Apr 16 04:41:28 miles-desktop kernel: [    0.376049] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.376100] pci 0000:00:07.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.376162] pci 0000:00:0a.0: [1002:5a1d] type 01 class 0x060400
Apr 16 04:41:28 miles-desktop kernel: [    0.376193] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.376244] pci 0000:00:0a.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.376314] pci 0000:00:11.0: [1002:4391] type 00 class 0x010601
Apr 16 04:41:28 miles-desktop kernel: [    0.376329] pci 0000:00:11.0: reg 0x10: [io  0xf040-0xf047]
Apr 16 04:41:28 miles-desktop kernel: [    0.376336] pci 0000:00:11.0: reg 0x14: [io  0xf030-0xf033]
Apr 16 04:41:28 miles-desktop kernel: [    0.376344] pci 0000:00:11.0: reg 0x18: [io  0xf020-0xf027]
Apr 16 04:41:28 miles-desktop kernel: [    0.376351] pci 0000:00:11.0: reg 0x1c: [io  0xf010-0xf013]
Apr 16 04:41:28 miles-desktop kernel: [    0.376358] pci 0000:00:11.0: reg 0x20: [io  0xf000-0xf00f]
Apr 16 04:41:28 miles-desktop kernel: [    0.376366] pci 0000:00:11.0: reg 0x24: [mem 0xfeb0b000-0xfeb0b3ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.376469] pci 0000:00:12.0: [1002:4397] type 00 class 0x0c0310
Apr 16 04:41:28 miles-desktop kernel: [    0.376479] pci 0000:00:12.0: reg 0x10: [mem 0xfeb0a000-0xfeb0afff]
Apr 16 04:41:28 miles-desktop kernel: [    0.376568] pci 0000:00:12.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.376634] pci 0000:00:12.2: [1002:4396] type 00 class 0x0c0320
Apr 16 04:41:28 miles-desktop kernel: [    0.376649] pci 0000:00:12.2: reg 0x10: [mem 0xfeb09000-0xfeb090ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.376712] pci 0000:00:12.2: supports D1 D2
Apr 16 04:41:28 miles-desktop kernel: [    0.376714] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
Apr 16 04:41:28 miles-desktop kernel: [    0.376766] pci 0000:00:12.2: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.376831] pci 0000:00:13.0: [1002:4397] type 00 class 0x0c0310
Apr 16 04:41:28 miles-desktop kernel: [    0.376841] pci 0000:00:13.0: reg 0x10: [mem 0xfeb08000-0xfeb08fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.376929] pci 0000:00:13.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.376994] pci 0000:00:13.2: [1002:4396] type 00 class 0x0c0320
Apr 16 04:41:28 miles-desktop kernel: [    0.377008] pci 0000:00:13.2: reg 0x10: [mem 0xfeb07000-0xfeb070ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.377072] pci 0000:00:13.2: supports D1 D2
Apr 16 04:41:28 miles-desktop kernel: [    0.377073] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
Apr 16 04:41:28 miles-desktop kernel: [    0.377125] pci 0000:00:13.2: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.377189] pci 0000:00:14.0: [1002:4385] type 00 class 0x0c0500
Apr 16 04:41:28 miles-desktop kernel: [    0.377305] pci 0000:00:14.2: [1002:4383] type 00 class 0x040300
Apr 16 04:41:28 miles-desktop kernel: [    0.377321] pci 0000:00:14.2: reg 0x10: [mem 0xfeb00000-0xfeb03fff 64bit]
Apr 16 04:41:28 miles-desktop kernel: [    0.377372] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.377422] pci 0000:00:14.2: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.377481] pci 0000:00:14.3: [1002:439d] type 00 class 0x060100
Apr 16 04:41:28 miles-desktop kernel: [    0.377595] pci 0000:00:14.4: [1002:4384] type 01 class 0x060401
Apr 16 04:41:28 miles-desktop kernel: [    0.377666] pci 0000:00:14.4: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.377727] pci 0000:00:14.5: [1002:4399] type 00 class 0x0c0310
Apr 16 04:41:28 miles-desktop kernel: [    0.377738] pci 0000:00:14.5: reg 0x10: [mem 0xfeb06000-0xfeb06fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.377826] pci 0000:00:14.5: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.377890] pci 0000:00:16.0: [1002:4397] type 00 class 0x0c0310
Apr 16 04:41:28 miles-desktop kernel: [    0.377900] pci 0000:00:16.0: reg 0x10: [mem 0xfeb05000-0xfeb05fff]
Apr 16 04:41:28 miles-desktop kernel: [    0.377988] pci 0000:00:16.0: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.378053] pci 0000:00:16.2: [1002:4396] type 00 class 0x0c0320
Apr 16 04:41:28 miles-desktop kernel: [    0.378068] pci 0000:00:16.2: reg 0x10: [mem 0xfeb04000-0xfeb040ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.378133] pci 0000:00:16.2: supports D1 D2
Apr 16 04:41:28 miles-desktop kernel: [    0.378134] pci 0000:00:16.2: PME# supported from D0 D1 D2 D3hot
Apr 16 04:41:28 miles-desktop kernel: [    0.378186] pci 0000:00:16.2: System wakeup disabled by ACPI
Apr 16 04:41:28 miles-desktop kernel: [    0.378251] pci 0000:00:18.0: [1022:1600] type 00 class 0x060000
Apr 16 04:41:28 miles-desktop kernel: [    0.378323] pci 0000:00:18.1: [1022:1601] type 00 class 0x060000
Apr 16 04:41:28 miles-desktop kernel: [    0.378392] pci 0000:00:18.2: [1022:1602] type 00 class 0x060000
Apr 16 04:41:28 miles-desktop kernel: [    0.378461] pci 0000:00:18.3: [1022:1603] type 00 class 0x060000
Apr 16 04:41:28 miles-desktop kernel: [    0.378532] pci 0000:00:18.4: [1022:1604] type 00 class 0x060000
Apr 16 04:41:28 miles-desktop kernel: [    0.378599] pci 0000:00:18.5: [1022:1605] type 00 class 0x060000
Apr 16 04:41:28 miles-desktop kernel: [    0.378710] pci 0000:01:00.0: [1002:6818] type 00 class 0x030000
Apr 16 04:41:28 miles-desktop kernel: [    0.378721] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.378729] pci 0000:01:00.0: reg 0x18: [mem 0xfea00000-0xfea3ffff 64bit]
Apr 16 04:41:28 miles-desktop kernel: [    0.378735] pci 0000:01:00.0: reg 0x20: [io  0xe000-0xe0ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.378748] pci 0000:01:00.0: reg 0x30: [mem 0xfea40000-0xfea5ffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.378780] pci 0000:01:00.0: supports D1 D2
Apr 16 04:41:28 miles-desktop kernel: [    0.378781] pci 0000:01:00.0: PME# supported from D1 D2 D3hot
Apr 16 04:41:28 miles-desktop kernel: [    0.378825] pci 0000:01:00.1: [1002:aab0] type 00 class 0x040300
Apr 16 04:41:28 miles-desktop kernel: [    0.378836] pci 0000:01:00.1: reg 0x10: [mem 0xfea60000-0xfea63fff 64bit]
Apr 16 04:41:28 miles-desktop kernel: [    0.378889] pci 0000:01:00.1: supports D1 D2
Apr 16 04:41:28 miles-desktop kernel: [    0.386756] pci 0000:00:02.0: PCI bridge to [bus 01]
Apr 16 04:41:28 miles-desktop kernel: [    0.386804] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
Apr 16 04:41:28 miles-desktop kernel: [    0.386809] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.386815] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.386898] pci 0000:02:00.0: [10ec:8168] type 00 class 0x020000
Apr 16 04:41:28 miles-desktop kernel: [    0.386915] pci 0000:02:00.0: reg 0x10: [io  0xd000-0xd0ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.386941] pci 0000:02:00.0: reg 0x18: [mem 0xd0004000-0xd0004fff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.386957] pci 0000:02:00.0: reg 0x20: [mem 0xd0000000-0xd0003fff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.387024] pci 0000:02:00.0: supports D1 D2
Apr 16 04:41:28 miles-desktop kernel: [    0.387028] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.394741] pci 0000:00:04.0: PCI bridge to [bus 02]
Apr 16 04:41:28 miles-desktop kernel: [    0.394789] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.394797] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.394883] pci 0000:03:00.0: [1b21:1042] type 00 class 0x0c0330
Apr 16 04:41:28 miles-desktop kernel: [    0.394906] pci 0000:03:00.0: reg 0x10: [mem 0xfe900000-0xfe907fff 64bit]
Apr 16 04:41:28 miles-desktop kernel: [    0.395011] pci 0000:03:00.0: PME# supported from D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.402726] pci 0000:00:05.0: PCI bridge to [bus 03]
Apr 16 04:41:28 miles-desktop kernel: [    0.402776] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.402890] pci 0000:04:00.0: [197b:2362] type 00 class 0x010185
Apr 16 04:41:28 miles-desktop kernel: [    0.402919] pci 0000:04:00.0: reg 0x10: [io  0xc040-0xc047]
Apr 16 04:41:28 miles-desktop kernel: [    0.402933] pci 0000:04:00.0: reg 0x14: [io  0xc030-0xc033]
Apr 16 04:41:28 miles-desktop kernel: [    0.402947] pci 0000:04:00.0: reg 0x18: [io  0xc020-0xc027]
Apr 16 04:41:28 miles-desktop kernel: [    0.402961] pci 0000:04:00.0: reg 0x1c: [io  0xc010-0xc013]
Apr 16 04:41:28 miles-desktop kernel: [    0.402974] pci 0000:04:00.0: reg 0x20: [io  0xc000-0xc00f]
Apr 16 04:41:28 miles-desktop kernel: [    0.402988] pci 0000:04:00.0: reg 0x24: [mem 0xfe810000-0xfe8101ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.403002] pci 0000:04:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.403052] pci 0000:04:00.0: PME# supported from D3hot
Apr 16 04:41:28 miles-desktop kernel: [    0.410714] pci 0000:00:06.0: PCI bridge to [bus 04]
Apr 16 04:41:28 miles-desktop kernel: [    0.410762] pci 0000:00:06.0:   bridge window [io  0xc000-0xcfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.410767] pci 0000:00:06.0:   bridge window [mem 0xfe800000-0xfe8fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.410852] pci 0000:05:00.0: [1b21:1042] type 00 class 0x0c0330
Apr 16 04:41:28 miles-desktop kernel: [    0.410875] pci 0000:05:00.0: reg 0x10: [mem 0xfe700000-0xfe707fff 64bit]
Apr 16 04:41:28 miles-desktop kernel: [    0.410982] pci 0000:05:00.0: PME# supported from D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.418699] pci 0000:00:07.0: PCI bridge to [bus 05]
Apr 16 04:41:28 miles-desktop kernel: [    0.418748] pci 0000:00:07.0:   bridge window [mem 0xfe700000-0xfe7fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.418853] pci 0000:06:00.0: [197b:2362] type 00 class 0x010185
Apr 16 04:41:28 miles-desktop kernel: [    0.418882] pci 0000:06:00.0: reg 0x10: [io  0xb040-0xb047]
Apr 16 04:41:28 miles-desktop kernel: [    0.418896] pci 0000:06:00.0: reg 0x14: [io  0xb030-0xb033]
Apr 16 04:41:28 miles-desktop kernel: [    0.418910] pci 0000:06:00.0: reg 0x18: [io  0xb020-0xb027]
Apr 16 04:41:28 miles-desktop kernel: [    0.418924] pci 0000:06:00.0: reg 0x1c: [io  0xb010-0xb013]
Apr 16 04:41:28 miles-desktop kernel: [    0.418938] pci 0000:06:00.0: reg 0x20: [io  0xb000-0xb00f]
Apr 16 04:41:28 miles-desktop kernel: [    0.418952] pci 0000:06:00.0: reg 0x24: [mem 0xfe610000-0xfe6101ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.418967] pci 0000:06:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.419016] pci 0000:06:00.0: PME# supported from D3hot
Apr 16 04:41:28 miles-desktop kernel: [    0.426686] pci 0000:00:0a.0: PCI bridge to [bus 06]
Apr 16 04:41:28 miles-desktop kernel: [    0.426734] pci 0000:00:0a.0:   bridge window [io  0xb000-0xbfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.426739] pci 0000:00:0a.0:   bridge window [mem 0xfe600000-0xfe6fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.426810] pci 0000:07:06.0: [1106:3044] type 00 class 0x0c0010
Apr 16 04:41:28 miles-desktop kernel: [    0.426835] pci 0000:07:06.0: reg 0x10: [mem 0xfe500000-0xfe5007ff]
Apr 16 04:41:28 miles-desktop kernel: [    0.426849] pci 0000:07:06.0: reg 0x14: [io  0xa000-0xa07f]
Apr 16 04:41:28 miles-desktop kernel: [    0.426942] pci 0000:07:06.0: supports D2
Apr 16 04:41:28 miles-desktop kernel: [    0.426945] pci 0000:07:06.0: PME# supported from D2 D3hot D3cold
Apr 16 04:41:28 miles-desktop kernel: [    0.427041] pci 0000:00:14.4: PCI bridge to [bus 07] (subtractive decode)
Apr 16 04:41:28 miles-desktop kernel: [    0.427087] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
Apr 16 04:41:28 miles-desktop kernel: [    0.427092] pci 0000:00:14.4:   bridge window [mem 0xfe500000-0xfe5fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.427098] pci 0000:00:14.4:   bridge window [io  0x0000-0x03af] (subtractive decode)
Apr 16 04:41:28 miles-desktop kernel: [    0.427102] pci 0000:00:14.4:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
Apr 16 04:41:28 miles-desktop kernel: [    0.427105] pci 0000:00:14.4:   bridge window [io  0x03b0-0x03df] (subtractive decode)
Apr 16 04:41:28 miles-desktop kernel: [    0.427108] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
Apr 16 04:41:28 miles-desktop kernel: [    0.427112] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
Apr 16 04:41:28 miles-desktop kernel: [    0.427115] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000dffff] (subtractive decode)
Apr 16 04:41:28 miles-desktop kernel: [    0.427118] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
Apr 16 04:41:28 miles-desktop kernel: [    0.428102] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 10 11 14 15) *0
Apr 16 04:41:28 miles-desktop kernel: [    0.428604] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 11 14 15) *0
Apr 16 04:41:28 miles-desktop kernel: [    0.429107] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 10 11 14 15) *0
Apr 16 04:41:28 miles-desktop kernel: [    0.429608] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 10 11 14 15) *0
Apr 16 04:41:28 miles-desktop kernel: [    0.430092] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 14 15) *0
Apr 16 04:41:28 miles-desktop kernel: [    0.430544] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 14 15) *0
Apr 16 04:41:28 miles-desktop kernel: [    0.431006] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 11 14 15) *0
Apr 16 04:41:28 miles-desktop kernel: [    0.431462] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 14 15) *0
Apr 16 04:41:28 miles-desktop kernel: [    0.432106] ACPI: \_SB_.PCI0: notify handler is installed
Apr 16 04:41:28 miles-desktop kernel: [    0.432213] Found 1 acpi root devices
Apr 16 04:41:28 miles-desktop kernel: [    0.432246] ACPI: EC: GPE = 0xa, I/O: command/status = 0x66, data = 0x62
Apr 16 04:41:28 miles-desktop kernel: [    0.432457] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
Apr 16 04:41:28 miles-desktop kernel: [    0.432508] vgaarb: loaded
Apr 16 04:41:28 miles-desktop kernel: [    0.432548] vgaarb: bridge control possible 0000:01:00.0
Apr 16 04:41:28 miles-desktop kernel: [    0.432900] SCSI subsystem initialized
Apr 16 04:41:28 miles-desktop kernel: [    0.432943] ACPI: bus type ATA registered
Apr 16 04:41:28 miles-desktop kernel: [    0.433072] libata version 3.00 loaded.
Apr 16 04:41:28 miles-desktop kernel: [    0.433100] ACPI: bus type USB registered
Apr 16 04:41:28 miles-desktop kernel: [    0.433165] usbcore: registered new interface driver usbfs
Apr 16 04:41:28 miles-desktop kernel: [    0.433222] usbcore: registered new interface driver hub
Apr 16 04:41:28 miles-desktop kernel: [    0.433304] usbcore: registered new device driver usb
Apr 16 04:41:28 miles-desktop kernel: [    0.433547] PCI: Using ACPI for IRQ routing
Apr 16 04:41:28 miles-desktop kernel: [    0.440816] PCI: pci_cache_line_size set to 64 bytes
Apr 16 04:41:28 miles-desktop kernel: [    0.440876] e820: reserve RAM buffer [mem 0x0009d800-0x0009ffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.440878] e820: reserve RAM buffer [mem 0xbd839000-0xbfffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.440879] e820: reserve RAM buffer [mem 0xbdf00000-0xbfffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.440880] e820: reserve RAM buffer [mem 0x43f000000-0x43fffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.440943] NetLabel: Initializing
Apr 16 04:41:28 miles-desktop kernel: [    0.440981] NetLabel:  domain hash size = 128
Apr 16 04:41:28 miles-desktop kernel: [    0.441018] NetLabel:  protocols = UNLABELED CIPSOv4
Apr 16 04:41:28 miles-desktop kernel: [    0.441065] NetLabel:  unlabeled traffic allowed by default
Apr 16 04:41:28 miles-desktop kernel: [    0.441151] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Apr 16 04:41:28 miles-desktop kernel: [    0.441321] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
Apr 16 04:41:28 miles-desktop kernel: [    0.443401] Switched to clocksource hpet
Apr 16 04:41:28 miles-desktop kernel: [    0.448251] AppArmor: AppArmor Filesystem Enabled
Apr 16 04:41:28 miles-desktop kernel: [    0.448305] pnp: PnP ACPI init
Apr 16 04:41:28 miles-desktop kernel: [    0.448349] ACPI: bus type PNP registered
Apr 16 04:41:28 miles-desktop kernel: [    0.448458] system 00:00: [mem 0xe0000000-0xefffffff] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.448498] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.449074] system 00:01: [io  0x040b] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449113] system 00:01: [io  0x04d6] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449152] system 00:01: [io  0x0c00-0x0c01] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449190] system 00:01: [io  0x0c14] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449228] system 00:01: [io  0x0c50-0x0c51] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449267] system 00:01: [io  0x0c52] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449305] system 00:01: [io  0x0c6c] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449344] system 00:01: [io  0x0c6f] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449382] system 00:01: [io  0x0cd0-0x0cd1] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449420] system 00:01: [io  0x0cd2-0x0cd3] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449459] system 00:01: [io  0x0cd4-0x0cd5] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449497] system 00:01: [io  0x0cd6-0x0cd7] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449536] system 00:01: [io  0x0cd8-0x0cdf] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449575] system 00:01: [io  0x0800-0x089f] could not be reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449614] system 00:01: [io  0x0b20-0x0b3f] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449652] system 00:01: [io  0x0900-0x090f] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449690] system 00:01: [io  0x0910-0x091f] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449729] system 00:01: [io  0xfe00-0xfefe] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449769] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449808] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449847] system 00:01: [mem 0xfed80000-0xfed8ffff] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449886] system 00:01: [mem 0xfed61000-0xfed70fff] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449927] system 00:01: [mem 0xfec10000-0xfec10fff] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.449967] system 00:01: [mem 0xfed00000-0xfed00fff] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.450005] system 00:01: [mem 0xffc00000-0xffffffff] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.450045] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450169] system 00:02: [io  0x0290-0x02af] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.450208] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450219] pnp 00:03: [dma 4]
Apr 16 04:41:28 miles-desktop kernel: [    0.450234] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450258] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450277] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450325] system 00:06: [io  0x04d0-0x04d1] has been reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.450364] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450385] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450415] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450577] pnp 00:09: [dma 0 disabled]
Apr 16 04:41:28 miles-desktop kernel: [    0.450615] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450723] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.450817] system 00:0b: [mem 0xfec20000-0xfec200ff] could not be reserved
Apr 16 04:41:28 miles-desktop kernel: [    0.450857] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.451027] pnp 00:0c: Plug and Play ACPI device, IDs PNP0103 (active)
Apr 16 04:41:28 miles-desktop kernel: [    0.451031] pnp: PnP ACPI: found 13 devices
Apr 16 04:41:28 miles-desktop kernel: [    0.451069] ACPI: bus type PNP unregistered
Apr 16 04:41:28 miles-desktop kernel: [    0.457297] pci 0000:00:06.0: BAR 15: assigned [mem 0xd0100000-0xd01fffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.457341] pci 0000:00:0a.0: BAR 15: assigned [mem 0xd0200000-0xd02fffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.457385] pci 0000:00:02.0: PCI bridge to [bus 01]
Apr 16 04:41:28 miles-desktop kernel: [    0.457424] pci 0000:00:02.0:   bridge window [io  0xe000-0xefff]
Apr 16 04:41:28 miles-desktop kernel: [    0.457464] pci 0000:00:02.0:   bridge window [mem 0xfea00000-0xfeafffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.457503] pci 0000:00:02.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.457547] pci 0000:00:04.0: PCI bridge to [bus 02]
Apr 16 04:41:28 miles-desktop kernel: [    0.457586] pci 0000:00:04.0:   bridge window [io  0xd000-0xdfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.457626] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd00fffff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.457670] pci 0000:00:05.0: PCI bridge to [bus 03]
Apr 16 04:41:28 miles-desktop kernel: [    0.457709] pci 0000:00:05.0:   bridge window [mem 0xfe900000-0xfe9fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.457750] pci 0000:04:00.0: BAR 6: assigned [mem 0xd0100000-0xd010ffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.457793] pci 0000:00:06.0: PCI bridge to [bus 04]
Apr 16 04:41:28 miles-desktop kernel: [    0.457831] pci 0000:00:06.0:   bridge window [io  0xc000-0xcfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.457870] pci 0000:00:06.0:   bridge window [mem 0xfe800000-0xfe8fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.457909] pci 0000:00:06.0:   bridge window [mem 0xd0100000-0xd01fffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.457953] pci 0000:00:07.0: PCI bridge to [bus 05]
Apr 16 04:41:28 miles-desktop kernel: [    0.457992] pci 0000:00:07.0:   bridge window [mem 0xfe700000-0xfe7fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.458032] pci 0000:06:00.0: BAR 6: assigned [mem 0xd0200000-0xd020ffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.458075] pci 0000:00:0a.0: PCI bridge to [bus 06]
Apr 16 04:41:28 miles-desktop kernel: [    0.459999] pci 0000:00:0a.0:   bridge window [io  0xb000-0xbfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460038] pci 0000:00:0a.0:   bridge window [mem 0xfe600000-0xfe6fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460077] pci 0000:00:0a.0:   bridge window [mem 0xd0200000-0xd02fffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.460121] pci 0000:00:14.4: PCI bridge to [bus 07]
Apr 16 04:41:28 miles-desktop kernel: [    0.460159] pci 0000:00:14.4:   bridge window [io  0xa000-0xafff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460199] pci 0000:00:14.4:   bridge window [mem 0xfe500000-0xfe5fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460568] pci_bus 0000:00: resource 4 [io  0x0000-0x03af]
Apr 16 04:41:28 miles-desktop kernel: [    0.460570] pci_bus 0000:00: resource 5 [io  0x03e0-0x0cf7]
Apr 16 04:41:28 miles-desktop kernel: [    0.460571] pci_bus 0000:00: resource 6 [io  0x03b0-0x03df]
Apr 16 04:41:28 miles-desktop kernel: [    0.460572] pci_bus 0000:00: resource 7 [io  0x0d00-0xffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460574] pci_bus 0000:00: resource 8 [mem 0x000a0000-0x000bffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460575] pci_bus 0000:00: resource 9 [mem 0x000c0000-0x000dffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460577] pci_bus 0000:00: resource 10 [mem 0xc0000000-0xffffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460578] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460579] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460581] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.460582] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460584] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd00fffff 64bit pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.460585] pci_bus 0000:03: resource 1 [mem 0xfe900000-0xfe9fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460587] pci_bus 0000:04: resource 0 [io  0xc000-0xcfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460588] pci_bus 0000:04: resource 1 [mem 0xfe800000-0xfe8fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460590] pci_bus 0000:04: resource 2 [mem 0xd0100000-0xd01fffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.460591] pci_bus 0000:05: resource 1 [mem 0xfe700000-0xfe7fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460593] pci_bus 0000:06: resource 0 [io  0xb000-0xbfff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460594] pci_bus 0000:06: resource 1 [mem 0xfe600000-0xfe6fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460595] pci_bus 0000:06: resource 2 [mem 0xd0200000-0xd02fffff pref]
Apr 16 04:41:28 miles-desktop kernel: [    0.460597] pci_bus 0000:07: resource 0 [io  0xa000-0xafff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460598] pci_bus 0000:07: resource 1 [mem 0xfe500000-0xfe5fffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460599] pci_bus 0000:07: resource 4 [io  0x0000-0x03af]
Apr 16 04:41:28 miles-desktop kernel: [    0.460601] pci_bus 0000:07: resource 5 [io  0x03e0-0x0cf7]
Apr 16 04:41:28 miles-desktop kernel: [    0.460602] pci_bus 0000:07: resource 6 [io  0x03b0-0x03df]
Apr 16 04:41:28 miles-desktop kernel: [    0.460603] pci_bus 0000:07: resource 7 [io  0x0d00-0xffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460604] pci_bus 0000:07: resource 8 [mem 0x000a0000-0x000bffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460606] pci_bus 0000:07: resource 9 [mem 0x000c0000-0x000dffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460607] pci_bus 0000:07: resource 10 [mem 0xc0000000-0xffffffff]
Apr 16 04:41:28 miles-desktop kernel: [    0.460628] NET: Registered protocol family 2
Apr 16 04:41:28 miles-desktop kernel: [    0.460895] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.461374] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.461598] TCP: Hash tables configured (established 131072 bind 65536)
Apr 16 04:41:28 miles-desktop kernel: [    0.461663] TCP: reno registered
Apr 16 04:41:28 miles-desktop kernel: [    0.461716] UDP hash table entries: 8192 (order: 6, 262144 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.461819] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    0.461959] NET: Registered protocol family 1
Apr 16 04:41:28 miles-desktop kernel: [    1.518067] pci 0000:01:00.0: Boot video device
Apr 16 04:41:28 miles-desktop kernel: [    1.518308] PCI: CLS 64 bytes, default 64
Apr 16 04:41:28 miles-desktop kernel: [    1.518382] Trying to unpack rootfs image as initramfs...
Apr 16 04:41:28 miles-desktop kernel: [    1.848338] Freeing initrd memory: 24828K (ffff880034f72000 - ffff8800367b1000)
Apr 16 04:41:28 miles-desktop kernel: [    1.848645] PCI-DMA: Disabling AGP.
Apr 16 04:41:28 miles-desktop kernel: [    1.848748] PCI-DMA: aperture base @ b4000000 size 65536 KB
Apr 16 04:41:28 miles-desktop kernel: [    1.848786] PCI-DMA: using GART IOMMU.
Apr 16 04:41:28 miles-desktop kernel: [    1.848825] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
Apr 16 04:41:28 miles-desktop kernel: [    1.852926] perf: AMD NB counters detected
Apr 16 04:41:28 miles-desktop kernel: [    1.852989] LVT offset 0 assigned for vector 0x400
Apr 16 04:41:28 miles-desktop kernel: [    1.853055] perf: AMD IBS detected (0x000000ff)
Apr 16 04:41:28 miles-desktop kernel: [    1.853118] Scanning for low memory corruption every 60 seconds
Apr 16 04:41:28 miles-desktop kernel: [    1.853406] Initialise module verification
Apr 16 04:41:28 miles-desktop kernel: [    1.853476] audit: initializing netlink socket (disabled)
Apr 16 04:41:28 miles-desktop kernel: [    1.853521] type=2000 audit(1397623234.652:1): initialized
Apr 16 04:41:28 miles-desktop kernel: [    1.872758] bounce pool size: 64 pages
Apr 16 04:41:28 miles-desktop kernel: [    1.872807] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Apr 16 04:41:28 miles-desktop kernel: [    1.874378] zbud: loaded
Apr 16 04:41:28 miles-desktop kernel: [    1.874522] VFS: Disk quotas dquot_6.5.2
Apr 16 04:41:28 miles-desktop kernel: [    1.874595] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Apr 16 04:41:28 miles-desktop kernel: [    1.875064] fuse init (API version 7.22)
Apr 16 04:41:28 miles-desktop kernel: [    1.875163] msgmni has been set to 31984
Apr 16 04:41:28 miles-desktop kernel: [    1.875701] Key type asymmetric registered
Apr 16 04:41:28 miles-desktop kernel: [    1.875741] Asymmetric key parser 'x509' registered
Apr 16 04:41:28 miles-desktop kernel: [    1.875801] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
Apr 16 04:41:28 miles-desktop kernel: [    1.875888] io scheduler noop registered
Apr 16 04:41:28 miles-desktop kernel: [    1.875928] io scheduler deadline registered (default)
Apr 16 04:41:28 miles-desktop kernel: [    1.875984] io scheduler cfq registered
Apr 16 04:41:28 miles-desktop kernel: [    1.876208] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Apr 16 04:41:28 miles-desktop kernel: [    1.876256] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Apr 16 04:41:28 miles-desktop kernel: [    1.876386] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
Apr 16 04:41:28 miles-desktop kernel: [    1.876432] ACPI: Power Button [PWRB]
Apr 16 04:41:28 miles-desktop kernel: [    1.876495] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
Apr 16 04:41:28 miles-desktop kernel: [    1.876538] ACPI: Power Button [PWRF]
Apr 16 04:41:28 miles-desktop kernel: [    1.876613] ACPI: acpi_idle registered with cpuidle
Apr 16 04:41:28 miles-desktop kernel: [    1.876963] GHES: HEST is not enabled!
Apr 16 04:41:28 miles-desktop kernel: [    1.877095] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Apr 16 04:41:28 miles-desktop kernel: [    1.897473] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Apr 16 04:41:28 miles-desktop kernel: [    1.898644] Linux agpgart interface v0.103
Apr 16 04:41:28 miles-desktop kernel: [    1.899750] brd: module loaded
Apr 16 04:41:28 miles-desktop kernel: [    1.900335] loop: module loaded
Apr 16 04:41:28 miles-desktop kernel: [    1.900642] libphy: Fixed MDIO Bus: probed
Apr 16 04:41:28 miles-desktop kernel: [    1.900744] tun: Universal TUN/TAP device driver, 1.6
Apr 16 04:41:28 miles-desktop kernel: [    1.900784] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Apr 16 04:41:28 miles-desktop kernel: [    1.900868] PPP generic driver version 2.4.2
Apr 16 04:41:28 miles-desktop kernel: [    1.900937] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Apr 16 04:41:28 miles-desktop kernel: [    1.900984] ehci-pci: EHCI PCI platform driver
Apr 16 04:41:28 miles-desktop kernel: [    1.901115] ehci-pci 0000:00:12.2: EHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    1.901156] ehci-pci 0000:00:12.2: new USB bus registered, assigned bus number 1
Apr 16 04:41:28 miles-desktop kernel: [    1.901207] QUIRK: Enable AMD PLL fix
Apr 16 04:41:28 miles-desktop kernel: [    1.901208] ehci-pci 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 04:41:28 miles-desktop kernel: [    1.901260] ehci-pci 0000:00:12.2: debug port 1
Apr 16 04:41:28 miles-desktop kernel: [    1.901327] ehci-pci 0000:00:12.2: irq 17, io mem 0xfeb09000
Apr 16 04:41:28 miles-desktop kernel: [    1.912987] ehci-pci 0000:00:12.2: USB 2.0 started, EHCI 1.00
Apr 16 04:41:28 miles-desktop kernel: [    1.913064] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
Apr 16 04:41:28 miles-desktop kernel: [    1.913108] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    1.913156] usb usb1: Product: EHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    1.913198] usb usb1: Manufacturer: Linux 3.11.0-19-generic ehci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    1.913241] usb usb1: SerialNumber: 0000:00:12.2
Apr 16 04:41:28 miles-desktop kernel: [    1.913448] hub 1-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    1.913494] hub 1-0:1.0: 5 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    1.913866] ehci-pci 0000:00:13.2: EHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    1.913914] ehci-pci 0000:00:13.2: new USB bus registered, assigned bus number 2
Apr 16 04:41:28 miles-desktop kernel: [    1.913964] ehci-pci 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 04:41:28 miles-desktop kernel: [    1.914024] ehci-pci 0000:00:13.2: debug port 1
Apr 16 04:41:28 miles-desktop kernel: [    1.914107] ehci-pci 0000:00:13.2: irq 21, io mem 0xfeb07000
Apr 16 04:41:28 miles-desktop kernel: [    1.924975] ehci-pci 0000:00:13.2: USB 2.0 started, EHCI 1.00
Apr 16 04:41:28 miles-desktop kernel: [    1.925040] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
Apr 16 04:41:28 miles-desktop kernel: [    1.925084] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    1.925132] usb usb2: Product: EHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    1.925175] usb usb2: Manufacturer: Linux 3.11.0-19-generic ehci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    1.925218] usb usb2: SerialNumber: 0000:00:13.2
Apr 16 04:41:28 miles-desktop kernel: [    1.925423] hub 2-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    1.925468] hub 2-0:1.0: 5 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    1.925824] ehci-pci 0000:00:16.2: EHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    1.925872] ehci-pci 0000:00:16.2: new USB bus registered, assigned bus number 3
Apr 16 04:41:28 miles-desktop kernel: [    1.925922] ehci-pci 0000:00:16.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
Apr 16 04:41:28 miles-desktop kernel: [    1.925981] ehci-pci 0000:00:16.2: debug port 1
Apr 16 04:41:28 miles-desktop kernel: [    1.926060] ehci-pci 0000:00:16.2: irq 23, io mem 0xfeb04000
Apr 16 04:41:28 miles-desktop kernel: [    1.936953] ehci-pci 0000:00:16.2: USB 2.0 started, EHCI 1.00
Apr 16 04:41:28 miles-desktop kernel: [    1.937018] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
Apr 16 04:41:28 miles-desktop kernel: [    1.937062] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    1.937110] usb usb3: Product: EHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    1.937153] usb usb3: Manufacturer: Linux 3.11.0-19-generic ehci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    1.937196] usb usb3: SerialNumber: 0000:00:16.2
Apr 16 04:41:28 miles-desktop kernel: [    1.937394] hub 3-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    1.937439] hub 3-0:1.0: 4 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    1.937637] ehci-platform: EHCI generic platform driver
Apr 16 04:41:28 miles-desktop kernel: [    1.937689] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Apr 16 04:41:28 miles-desktop kernel: [    1.937731] ohci-pci: OHCI PCI platform driver
Apr 16 04:41:28 miles-desktop kernel: [    1.937927] ohci-pci 0000:00:12.0: OHCI PCI host controller
Apr 16 04:41:28 miles-desktop kernel: [    1.937975] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 4
Apr 16 04:41:28 miles-desktop kernel: [    1.938049] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb0a000
Apr 16 04:41:28 miles-desktop kernel: [    1.996854] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
Apr 16 04:41:28 miles-desktop kernel: [    1.996900] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    1.996949] usb usb4: Product: OHCI PCI host controller
Apr 16 04:41:28 miles-desktop kernel: [    1.996992] usb usb4: Manufacturer: Linux 3.11.0-19-generic ohci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    1.997035] usb usb4: SerialNumber: 0000:00:12.0
Apr 16 04:41:28 miles-desktop kernel: [    1.997236] hub 4-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    1.997284] hub 4-0:1.0: 5 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    1.997618] ohci-pci 0000:00:13.0: OHCI PCI host controller
Apr 16 04:41:28 miles-desktop kernel: [    1.997668] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 5
Apr 16 04:41:28 miles-desktop kernel: [    1.997746] ohci-pci 0000:00:13.0: irq 20, io mem 0xfeb08000
Apr 16 04:41:28 miles-desktop kernel: [    2.056752] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
Apr 16 04:41:28 miles-desktop kernel: [    2.056799] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    2.056847] usb usb5: Product: OHCI PCI host controller
Apr 16 04:41:28 miles-desktop kernel: [    2.056890] usb usb5: Manufacturer: Linux 3.11.0-19-generic ohci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    2.056933] usb usb5: SerialNumber: 0000:00:13.0
Apr 16 04:41:28 miles-desktop kernel: [    2.057136] hub 5-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    2.057184] hub 5-0:1.0: 5 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    2.057528] ohci-pci 0000:00:14.5: OHCI PCI host controller
Apr 16 04:41:28 miles-desktop kernel: [    2.057576] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 6
Apr 16 04:41:28 miles-desktop kernel: [    2.057640] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb06000
Apr 16 04:41:28 miles-desktop kernel: [    2.116667] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
Apr 16 04:41:28 miles-desktop kernel: [    2.116716] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    2.116765] usb usb6: Product: OHCI PCI host controller
Apr 16 04:41:28 miles-desktop kernel: [    2.116809] usb usb6: Manufacturer: Linux 3.11.0-19-generic ohci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    2.116852] usb usb6: SerialNumber: 0000:00:14.5
Apr 16 04:41:28 miles-desktop kernel: [    2.117069] hub 6-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    2.117119] hub 6-0:1.0: 2 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    2.117411] ohci-pci 0000:00:16.0: OHCI PCI host controller
Apr 16 04:41:28 miles-desktop kernel: [    2.117460] ohci-pci 0000:00:16.0: new USB bus registered, assigned bus number 7
Apr 16 04:41:28 miles-desktop kernel: [    2.117537] ohci-pci 0000:00:16.0: irq 22, io mem 0xfeb05000
Apr 16 04:41:28 miles-desktop kernel: [    2.176565] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
Apr 16 04:41:28 miles-desktop kernel: [    2.176611] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    2.176659] usb usb7: Product: OHCI PCI host controller
Apr 16 04:41:28 miles-desktop kernel: [    2.176703] usb usb7: Manufacturer: Linux 3.11.0-19-generic ohci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    2.176746] usb usb7: SerialNumber: 0000:00:16.0
Apr 16 04:41:28 miles-desktop kernel: [    2.176952] hub 7-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    2.177000] hub 7-0:1.0: 4 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    2.177186] ohci-platform: OHCI generic platform driver
Apr 16 04:41:28 miles-desktop kernel: [    2.177238] uhci_hcd: USB Universal Host Controller Interface driver
Apr 16 04:41:28 miles-desktop kernel: [    2.177392] xhci_hcd 0000:03:00.0: xHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    2.177440] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
Apr 16 04:41:28 miles-desktop kernel: [    2.187128] xhci_hcd 0000:03:00.0: irq 72 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.187142] xhci_hcd 0000:03:00.0: irq 73 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.187154] xhci_hcd 0000:03:00.0: irq 74 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.187165] xhci_hcd 0000:03:00.0: irq 75 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.187177] xhci_hcd 0000:03:00.0: irq 76 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.187188] xhci_hcd 0000:03:00.0: irq 77 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.187200] xhci_hcd 0000:03:00.0: irq 78 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.187344] usb usb8: New USB device found, idVendor=1d6b, idProduct=0002
Apr 16 04:41:28 miles-desktop kernel: [    2.187388] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    2.187435] usb usb8: Product: xHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    2.187478] usb usb8: Manufacturer: Linux 3.11.0-19-generic xhci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    2.187521] usb usb8: SerialNumber: 0000:03:00.0
Apr 16 04:41:28 miles-desktop kernel: [    2.187671] xHCI xhci_add_endpoint called for root hub
Apr 16 04:41:28 miles-desktop kernel: [    2.187674] xHCI xhci_check_bandwidth called for root hub
Apr 16 04:41:28 miles-desktop kernel: [    2.187708] hub 8-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    2.187755] hub 8-0:1.0: 2 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    2.187905] xhci_hcd 0000:03:00.0: xHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    2.187951] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 9
Apr 16 04:41:28 miles-desktop kernel: [    2.188032] usb usb9: New USB device found, idVendor=1d6b, idProduct=0003
Apr 16 04:41:28 miles-desktop kernel: [    2.189972] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    2.190020] usb usb9: Product: xHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    2.190062] usb usb9: Manufacturer: Linux 3.11.0-19-generic xhci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    2.190104] usb usb9: SerialNumber: 0000:03:00.0
Apr 16 04:41:28 miles-desktop kernel: [    2.190250] xHCI xhci_add_endpoint called for root hub
Apr 16 04:41:28 miles-desktop kernel: [    2.190252] xHCI xhci_check_bandwidth called for root hub
Apr 16 04:41:28 miles-desktop kernel: [    2.190284] hub 9-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    2.190331] hub 9-0:1.0: 2 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    2.196634] xhci_hcd 0000:05:00.0: xHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    2.196684] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 10
Apr 16 04:41:28 miles-desktop kernel: [    2.206363] xhci_hcd 0000:05:00.0: irq 79 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.206376] xhci_hcd 0000:05:00.0: irq 80 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.206387] xhci_hcd 0000:05:00.0: irq 81 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.206399] xhci_hcd 0000:05:00.0: irq 82 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.206413] xhci_hcd 0000:05:00.0: irq 83 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.206425] xhci_hcd 0000:05:00.0: irq 84 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.206436] xhci_hcd 0000:05:00.0: irq 85 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.206584] usb usb10: New USB device found, idVendor=1d6b, idProduct=0002
Apr 16 04:41:28 miles-desktop kernel: [    2.206629] usb usb10: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    2.206676] usb usb10: Product: xHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    2.206719] usb usb10: Manufacturer: Linux 3.11.0-19-generic xhci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    2.206762] usb usb10: SerialNumber: 0000:05:00.0
Apr 16 04:41:28 miles-desktop kernel: [    2.206925] xHCI xhci_add_endpoint called for root hub
Apr 16 04:41:28 miles-desktop kernel: [    2.206927] xHCI xhci_check_bandwidth called for root hub
Apr 16 04:41:28 miles-desktop kernel: [    2.206963] hub 10-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    2.207011] hub 10-0:1.0: 2 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    2.207153] xhci_hcd 0000:05:00.0: xHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    2.207199] xhci_hcd 0000:05:00.0: new USB bus registered, assigned bus number 11
Apr 16 04:41:28 miles-desktop kernel: [    2.207279] usb usb11: New USB device found, idVendor=1d6b, idProduct=0003
Apr 16 04:41:28 miles-desktop kernel: [    2.207323] usb usb11: New USB device strings: Mfr=3, Product=2, SerialNumber=1
Apr 16 04:41:28 miles-desktop kernel: [    2.207372] usb usb11: Product: xHCI Host Controller
Apr 16 04:41:28 miles-desktop kernel: [    2.207414] usb usb11: Manufacturer: Linux 3.11.0-19-generic xhci_hcd
Apr 16 04:41:28 miles-desktop kernel: [    2.207457] usb usb11: SerialNumber: 0000:05:00.0
Apr 16 04:41:28 miles-desktop kernel: [    2.207604] xHCI xhci_add_endpoint called for root hub
Apr 16 04:41:28 miles-desktop kernel: [    2.207606] xHCI xhci_check_bandwidth called for root hub
Apr 16 04:41:28 miles-desktop kernel: [    2.207638] hub 11-0:1.0: USB hub found
Apr 16 04:41:28 miles-desktop kernel: [    2.207685] hub 11-0:1.0: 2 ports detected
Apr 16 04:41:28 miles-desktop kernel: [    2.212602] i8042: PNP: No PS/2 controller found. Probing ports directly.
Apr 16 04:41:28 miles-desktop kernel: [    2.213030] serio: i8042 KBD port at 0x60,0x64 irq 1
Apr 16 04:41:28 miles-desktop kernel: [    2.213082] serio: i8042 AUX port at 0x60,0x64 irq 12
Apr 16 04:41:28 miles-desktop kernel: [    2.213284] mousedev: PS/2 mouse device common for all mice
Apr 16 04:41:28 miles-desktop kernel: [    2.213552] rtc_cmos 00:04: RTC can wake from S4
Apr 16 04:41:28 miles-desktop kernel: [    2.213732] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
Apr 16 04:41:28 miles-desktop kernel: [    2.213800] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Apr 16 04:41:28 miles-desktop kernel: [    2.213950] device-mapper: uevent: version 1.0.3
Apr 16 04:41:28 miles-desktop kernel: [    2.214114] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
Apr 16 04:41:28 miles-desktop kernel: [    2.214301] cpuidle: using governor ladder
Apr 16 04:41:28 miles-desktop kernel: [    2.214541] cpuidle: using governor menu
Apr 16 04:41:28 miles-desktop kernel: [    2.214601] ledtrig-cpu: registered to indicate activity on CPUs
Apr 16 04:41:28 miles-desktop kernel: [    2.214776] TCP: cubic registered
Apr 16 04:41:28 miles-desktop kernel: [    2.214983] NET: Registered protocol family 10
Apr 16 04:41:28 miles-desktop kernel: [    2.215340] NET: Registered protocol family 17
Apr 16 04:41:28 miles-desktop kernel: [    2.215393] Key type dns_resolver registered
Apr 16 04:41:28 miles-desktop kernel: [    2.215981] PM: Hibernation image not present or could not be loaded.
Apr 16 04:41:28 miles-desktop kernel: [    2.215987] Loading module verification certificates
Apr 16 04:41:28 miles-desktop kernel: [    2.217778] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 5553b4b7b74ebe0a90f93fbc0d8e2b9c98211b47'
Apr 16 04:41:28 miles-desktop kernel: [    2.217838] registered taskstats version 1
Apr 16 04:41:28 miles-desktop kernel: [    2.222482] Key type trusted registered
Apr 16 04:41:28 miles-desktop kernel: [    2.226065] Key type encrypted registered
Apr 16 04:41:28 miles-desktop kernel: [    2.229676] AppArmor: AppArmor sha1 policy hashing enabled
Apr 16 04:41:28 miles-desktop kernel: [    2.230357]   Magic number: 10:742:666
Apr 16 04:41:28 miles-desktop kernel: [    2.230496] rtc_cmos 00:04: setting system clock to 2014-04-16 04:40:35 UTC (1397623235)
Apr 16 04:41:28 miles-desktop kernel: [    2.230659] powernow-k8: This CPU is not supported anymore, using acpi-cpufreq instead.
Apr 16 04:41:28 miles-desktop kernel: [    2.232498] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Apr 16 04:41:28 miles-desktop kernel: [    2.232545] EDD information not available.
Apr 16 04:41:28 miles-desktop kernel: [    2.234632] Freeing unused kernel memory: 1368K (ffffffff81d10000 - ffffffff81e66000)
Apr 16 04:41:28 miles-desktop kernel: [    2.234681] Write protecting the kernel read-only data: 12288k
Apr 16 04:41:28 miles-desktop kernel: [    2.240040] Freeing unused kernel memory: 1028K (ffff8800016ff000 - ffff880001800000)
Apr 16 04:41:28 miles-desktop kernel: [    2.242378] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
Apr 16 04:41:28 miles-desktop kernel: [    2.266969] wmi: Mapper loaded
Apr 16 04:41:28 miles-desktop kernel: [    2.274660] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Apr 16 04:41:28 miles-desktop kernel: [    2.274706] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
Apr 16 04:41:28 miles-desktop kernel: [    2.274952] r8169 0000:02:00.0: irq 86 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [    2.275076] r8169 0000:02:00.0 eth0: RTL8168evl/8111evl at 0xffffc90001818000, 14:da:e9:0f:72:81, XID 0c900800 IRQ 86
Apr 16 04:41:28 miles-desktop kernel: [    2.275120] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
Apr 16 04:41:28 miles-desktop kernel: [    2.276938] ahci 0000:00:11.0: version 3.0
Apr 16 04:41:28 miles-desktop kernel: [    2.277116] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
Apr 16 04:41:28 miles-desktop kernel: [    2.277163] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
Apr 16 04:41:28 miles-desktop kernel: [    2.277916] scsi0 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.278067] scsi1 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.278186] scsi2 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.278323] scsi3 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.278450] scsi4 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.278565] scsi5 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.278670] ata1: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b100 irq 19
Apr 16 04:41:28 miles-desktop kernel: [    2.278715] ata2: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b180 irq 19
Apr 16 04:41:28 miles-desktop kernel: [    2.278759] ata3: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b200 irq 19
Apr 16 04:41:28 miles-desktop kernel: [    2.278804] ata4: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b280 irq 19
Apr 16 04:41:28 miles-desktop kernel: [    2.278851] ata5: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b300 irq 19
Apr 16 04:41:28 miles-desktop kernel: [    2.278899] ata6: SATA max UDMA/133 abar m1024@0xfeb0b000 port 0xfeb0b380 irq 19
Apr 16 04:41:28 miles-desktop kernel: [    2.279079] ahci 0000:04:00.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Apr 16 04:41:28 miles-desktop kernel: [    2.279141] ahci 0000:04:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Apr 16 04:41:28 miles-desktop kernel: [    2.279488] scsi6 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.279604] scsi7 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.279694] ata7: SATA max UDMA/133 abar m512@0xfe810000 port 0xfe810100 irq 51
Apr 16 04:41:28 miles-desktop kernel: [    2.279740] ata8: SATA max UDMA/133 abar m512@0xfe810000 port 0xfe810180 irq 51
Apr 16 04:41:28 miles-desktop kernel: [    2.279886] ahci 0000:06:00.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
Apr 16 04:41:28 miles-desktop kernel: [    2.279940] ahci 0000:06:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
Apr 16 04:41:28 miles-desktop kernel: [    2.280258] scsi8 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.280385] scsi9 : ahci
Apr 16 04:41:28 miles-desktop kernel: [    2.280481] ata9: SATA max UDMA/133 abar m512@0xfe610000 port 0xfe610100 irq 47
Apr 16 04:41:28 miles-desktop kernel: [    2.280526] ata10: SATA max UDMA/133 abar m512@0xfe610000 port 0xfe610180 irq 47
Apr 16 04:41:28 miles-desktop kernel: [    2.352338] firewire_ohci 0000:07:06.0: added OHCI v1.10 device as card 0, 4 IR + 8 IT contexts, quirks 0x11
Apr 16 04:41:28 miles-desktop kernel: [    2.595968] ata4: SATA link down (SStatus 0 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.595991] ata7: SATA link down (SStatus 0 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.599907] ata9: SATA link down (SStatus 0 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.599991] ata10: SATA link down (SStatus 0 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.767636] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.767650] ata8: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.767752] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.767808] ata3: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.767864] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.767921] ata6: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Apr 16 04:41:28 miles-desktop kernel: [    2.769113] ata6.00: ATA-8: ST31000524AS, JC45, max UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.769154] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32)
Apr 16 04:41:28 miles-desktop kernel: [    2.769524] ata5.00: ATAPI: Optiarc DVD RW AD-7260S, 1.03, max UDMA/100
Apr 16 04:41:28 miles-desktop kernel: [    2.770703] ata6.00: configured for UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.771580] ata5.00: configured for UDMA/100
Apr 16 04:41:28 miles-desktop kernel: [    2.779507] ata2.00: ATA-8: OCZ-AGILITY3, 2.15, max UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.779553] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Apr 16 04:41:28 miles-desktop kernel: [    2.779600] ata1.00: ATA-8: OCZ-AGILITY3, 2.15, max UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.779643] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Apr 16 04:41:28 miles-desktop kernel: [    2.779913] ata3.00: ATA-8: OCZ-AGILITY3, 2.15, max UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.779952] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
Apr 16 04:41:28 miles-desktop kernel: [    2.789313] ata2.00: configured for UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.789516] ata1.00: configured for UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.789796] scsi 0:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.15 PQ: 0 ANSI: 5
Apr 16 04:41:28 miles-desktop kernel: [    2.789981] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Apr 16 04:41:28 miles-desktop kernel: [    2.790003] sd 0:0:0:0: Attached scsi generic sg0 type 0
Apr 16 04:41:28 miles-desktop kernel: [    2.790165] scsi 1:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.15 PQ: 0 ANSI: 5
Apr 16 04:41:28 miles-desktop kernel: [    2.790241] sd 0:0:0:0: [sda] Write Protect is off
Apr 16 04:41:28 miles-desktop kernel: [    2.790287] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 16 04:41:28 miles-desktop kernel: [    2.790313] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 16 04:41:28 miles-desktop kernel: [    2.790367] sd 1:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Apr 16 04:41:28 miles-desktop kernel: [    2.790479] sd 1:0:0:0: Attached scsi generic sg1 type 0
Apr 16 04:41:28 miles-desktop kernel: [    2.790527] sd 1:0:0:0: [sdb] Write Protect is off
Apr 16 04:41:28 miles-desktop kernel: [    2.790571] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Apr 16 04:41:28 miles-desktop kernel: [    2.790595] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 16 04:41:28 miles-desktop kernel: [    2.790764]  sda: sda1 sda2
Apr 16 04:41:28 miles-desktop kernel: [    2.791185]  sdb: sdb1 sdb2 < sdb5 >
Apr 16 04:41:28 miles-desktop kernel: [    2.791203] sd 0:0:0:0: [sda] Attached SCSI disk
Apr 16 04:41:28 miles-desktop kernel: [    2.791766] sd 1:0:0:0: [sdb] Attached SCSI disk
Apr 16 04:41:28 miles-desktop kernel: [    2.809096] ata3.00: configured for UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.809230] scsi 2:0:0:0: Direct-Access     ATA      OCZ-AGILITY3     2.15 PQ: 0 ANSI: 5
Apr 16 04:41:28 miles-desktop kernel: [    2.809406] sd 2:0:0:0: [sdc] 234441648 512-byte logical blocks: (120 GB/111 GiB)
Apr 16 04:41:28 miles-desktop kernel: [    2.809426] sd 2:0:0:0: Attached scsi generic sg2 type 0
Apr 16 04:41:28 miles-desktop kernel: [    2.809615] sd 2:0:0:0: [sdc] Write Protect is off
Apr 16 04:41:28 miles-desktop kernel: [    2.809662] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Apr 16 04:41:28 miles-desktop kernel: [    2.809689] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 16 04:41:28 miles-desktop kernel: [    2.810254]  sdc: sdc1 sdc2
Apr 16 04:41:28 miles-desktop kernel: [    2.810690] scsi 4:0:0:0: CD-ROM            Optiarc  DVD RW AD-7260S  1.03 PQ: 0 ANSI: 5
Apr 16 04:41:28 miles-desktop kernel: [    2.810730] sd 2:0:0:0: [sdc] Attached SCSI disk
Apr 16 04:41:28 miles-desktop kernel: [    2.812912] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Apr 16 04:41:28 miles-desktop kernel: [    2.812965] cdrom: Uniform CD-ROM driver Revision: 3.20
Apr 16 04:41:28 miles-desktop kernel: [    2.813110] sr 4:0:0:0: Attached scsi CD-ROM sr0
Apr 16 04:41:28 miles-desktop kernel: [    2.813218] sr 4:0:0:0: Attached scsi generic sg3 type 5
Apr 16 04:41:28 miles-desktop kernel: [    2.815352] scsi 5:0:0:0: Direct-Access     ATA      ST31000524AS     JC45 PQ: 0 ANSI: 5
Apr 16 04:41:28 miles-desktop kernel: [    2.815552] sd 5:0:0:0: Attached scsi generic sg4 type 0
Apr 16 04:41:28 miles-desktop kernel: [    2.815562] sd 5:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Apr 16 04:41:28 miles-desktop kernel: [    2.815573] ata8.00: ATA-7: ST3400820AS, 3.AAD, max UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.815575] ata8.00: 781422768 sectors, multi 0: LBA48 NCQ (depth 31/32)
Apr 16 04:41:28 miles-desktop kernel: [    2.815660] sd 5:0:0:0: [sdd] Write Protect is off
Apr 16 04:41:28 miles-desktop kernel: [    2.815662] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
Apr 16 04:41:28 miles-desktop kernel: [    2.815702] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 16 04:41:28 miles-desktop kernel: [    2.826343]  sdd: sdd1 sdd2
Apr 16 04:41:28 miles-desktop kernel: [    2.826701] sd 5:0:0:0: [sdd] Attached SCSI disk
Apr 16 04:41:28 miles-desktop kernel: [    2.847485] tsc: Refined TSC clocksource calibration: 4138.835 MHz
Apr 16 04:41:28 miles-desktop kernel: [    2.851598] firewire_core 0000:07:06.0: created device fw0: GUID 001fc6000014eaae, S400
Apr 16 04:41:28 miles-desktop kernel: [    2.873855] ata8.00: configured for UDMA/133
Apr 16 04:41:28 miles-desktop kernel: [    2.874115] scsi 7:0:0:0: Direct-Access     ATA      ST3400820AS      3.AA PQ: 0 ANSI: 5
Apr 16 04:41:28 miles-desktop kernel: [    2.874289] sd 7:0:0:0: [sde] 781422768 512-byte logical blocks: (400 GB/372 GiB)
Apr 16 04:41:28 miles-desktop kernel: [    2.874294] sd 7:0:0:0: Attached scsi generic sg5 type 0
Apr 16 04:41:28 miles-desktop kernel: [    2.874491] sd 7:0:0:0: [sde] Write Protect is off
Apr 16 04:41:28 miles-desktop kernel: [    2.874532] sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
Apr 16 04:41:28 miles-desktop kernel: [    2.874567] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr 16 04:41:28 miles-desktop kernel: [    2.921709]  sde: sde1
Apr 16 04:41:28 miles-desktop kernel: [    2.922020] sd 7:0:0:0: [sde] Attached SCSI disk
Apr 16 04:41:28 miles-desktop kernel: [    3.154967] usb 5-5: new full-speed USB device number 2 using ohci-pci
Apr 16 04:41:28 miles-desktop kernel: [    3.319740] usb 5-5: config 1 has an invalid descriptor of length 1, skipping remainder of the config
Apr 16 04:41:28 miles-desktop kernel: [    3.319794] usb 5-5: config 1 has 4 interfaces, different from the descriptor's value: 7
Apr 16 04:41:28 miles-desktop kernel: [    3.325732] usb 5-5: New USB device found, idVendor=046d, idProduct=0a15
Apr 16 04:41:28 miles-desktop kernel: [    3.325781] usb 5-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 16 04:41:28 miles-desktop kernel: [    3.325827] usb 5-5: Product: Logitech G35 Headset
Apr 16 04:41:28 miles-desktop kernel: [    3.325865] usb 5-5: Manufacturer: Logitech
Apr 16 04:41:28 miles-desktop kernel: [    3.332509] hidraw: raw HID events driver (C) Jiri Kosina
Apr 16 04:41:28 miles-desktop kernel: [    3.337804] usbcore: registered new interface driver usbhid
Apr 16 04:41:28 miles-desktop kernel: [    3.337849] usbhid: USB HID core driver
Apr 16 04:41:28 miles-desktop kernel: [    3.340797] input: Logitech Logitech G35 Headset as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.3/input/input2
Apr 16 04:41:28 miles-desktop kernel: [    3.340936] hid-generic 0003:046D:0A15.0001: input,hidraw0: USB HID v1.00 Device [Logitech Logitech G35 Headset] on usb-0000:00:13.0-5/input3
Apr 16 04:41:28 miles-desktop kernel: [    3.718017] usb 4-1: new full-speed USB device number 2 using ohci-pci
Apr 16 04:41:28 miles-desktop kernel: [    3.845926] Switched to clocksource tsc
Apr 16 04:41:28 miles-desktop kernel: [    3.892779] usb 4-1: New USB device found, idVendor=045e, idProduct=0745
Apr 16 04:41:28 miles-desktop kernel: [    3.892828] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 16 04:41:28 miles-desktop kernel: [    3.892875] usb 4-1: Product: Microsoft® Nano Transceiver v2.0
Apr 16 04:41:28 miles-desktop kernel: [    3.892913] usb 4-1: Manufacturer: Microsoft
Apr 16 04:41:28 miles-desktop kernel: [    3.899970] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.0/input/input3
Apr 16 04:41:28 miles-desktop kernel: [    3.900146] hid-generic 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:12.0-1/input0
Apr 16 04:41:28 miles-desktop kernel: [    3.908168] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.1/input/input4
Apr 16 04:41:28 miles-desktop kernel: [    3.908312] hid-generic 0003:045E:0745.0003: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:12.0-1/input1
Apr 16 04:41:28 miles-desktop kernel: [    3.933876] input: Microsoft Microsoft® Nano Transceiver v2.0 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.2/input/input5
Apr 16 04:41:28 miles-desktop kernel: [    3.934122] hid-generic 0003:045E:0745.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Microsoft Microsoft® Nano Transceiver v2.0] on usb-0000:00:12.0-1/input2
Apr 16 04:41:28 miles-desktop kernel: [    4.197200] usb 4-2: new full-speed USB device number 3 using ohci-pci
Apr 16 04:41:28 miles-desktop kernel: [    4.257069] EXT4-fs (sdc2): orphan cleanup on readonly fs
Apr 16 04:41:28 miles-desktop kernel: [    4.271813] EXT4-fs (sdc2): 35 orphan inodes deleted
Apr 16 04:41:28 miles-desktop kernel: [    4.271820] EXT4-fs (sdc2): recovery complete
Apr 16 04:41:28 miles-desktop kernel: [    4.274828] EXT4-fs (sdc2): mounted filesystem with ordered data mode. Opts: (null)
Apr 16 04:41:28 miles-desktop kernel: [    4.377969] usb 4-2: New USB device found, idVendor=1532, idProduct=0118
Apr 16 04:41:28 miles-desktop kernel: [    4.377983] usb 4-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Apr 16 04:41:28 miles-desktop kernel: [    4.377993] usb 4-2: Product: Razer DeathStalker
Apr 16 04:41:28 miles-desktop kernel: [    4.378001] usb 4-2: Manufacturer: Razer
Apr 16 04:41:28 miles-desktop kernel: [    4.384063] input: Razer Razer DeathStalker as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.0/input/input6
Apr 16 04:41:28 miles-desktop kernel: [    4.384198] hid-generic 0003:1532:0118.0005: input,hidraw4: USB HID v1.11 Keyboard [Razer Razer DeathStalker] on usb-0000:00:12.0-2/input0
Apr 16 04:41:28 miles-desktop kernel: [    4.393958] input: Razer Razer DeathStalker as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.1/input/input7
Apr 16 04:41:28 miles-desktop kernel: [    4.394127] hid-generic 0003:1532:0118.0006: input,hidraw5: USB HID v1.11 Keyboard [Razer Razer DeathStalker] on usb-0000:00:12.0-2/input1
Apr 16 04:41:28 miles-desktop kernel: [    4.400897] input: Razer Razer DeathStalker as /devices/pci0000:00/0000:00:12.0/usb4/4-2/4-2:1.2/input/input8
Apr 16 04:41:28 miles-desktop kernel: [    4.401041] hid-generic 0003:1532:0118.0007: input,hidraw6: USB HID v1.11 Mouse [Razer Razer DeathStalker] on usb-0000:00:12.0-2/input2
Apr 16 04:41:28 miles-desktop kernel: [    5.584673] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
Apr 16 04:41:28 miles-desktop kernel: [    5.584718] AMD IOMMUv2 functionality not available on this system
Apr 16 04:41:28 miles-desktop kernel: [    5.631679] MCE: In-kernel MCE decoding enabled.
Apr 16 04:41:28 miles-desktop kernel: [    5.632847] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
Apr 16 04:41:28 miles-desktop kernel: [    5.636242] EDAC MC: Ver: 3.0.0
Apr 16 04:41:28 miles-desktop kernel: [    5.637654] sp5100_tco: SP5100/SB800 TCO WatchDog Timer Driver v0.05
Apr 16 04:41:28 miles-desktop kernel: [    5.637757] sp5100_tco: PCI Revision ID: 0x42
Apr 16 04:41:28 miles-desktop kernel: [    5.637839] sp5100_tco: Using 0xfed80b00 for watchdog MMIO address
Apr 16 04:41:28 miles-desktop kernel: [    5.637890] sp5100_tco: Last reboot was not triggered by watchdog.
Apr 16 04:41:28 miles-desktop kernel: [    5.637974] sp5100_tco: initialized (0xffffc90011bc6b00). heartbeat=60 sec (nowayout=0)
Apr 16 04:41:28 miles-desktop kernel: [    5.640808] AMD64 EDAC driver v3.4.0
Apr 16 04:41:28 miles-desktop kernel: [    5.640874] EDAC amd64: DRAM ECC disabled.
Apr 16 04:41:28 miles-desktop kernel: [    5.640920] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Apr 16 04:41:28 miles-desktop kernel: [    5.640920]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Apr 16 04:41:28 miles-desktop kernel: [    5.640920]  (Note that use of the override may cause unknown side effects.)
Apr 16 04:41:28 miles-desktop kernel: [    5.649310] microcode: CPU0: patch_level=0x06000605
Apr 16 04:41:28 miles-desktop kernel: [    5.654050] hda-intel 0000:00:14.2: Using LPIB position fix
Apr 16 04:41:28 miles-desktop kernel: [    5.656983] hda-intel 0000:00:14.2: Enable sync_write for stable communication
Apr 16 04:41:28 miles-desktop kernel: [    5.660235] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Apr 16 04:41:28 miles-desktop kernel: [    5.660282] Disabling lock debugging due to kernel taint
Apr 16 04:41:28 miles-desktop kernel: [    5.665084] fglrx: module verification failed: signature and/or required key missing - tainting kernel
Apr 16 04:41:28 miles-desktop kernel: [    5.665596] microcode: CPU0: new patch_level=0x0600063d
Apr 16 04:41:28 miles-desktop kernel: [    5.659660] microcode: CPU1: patch_level=0x06000605
Apr 16 04:41:28 miles-desktop kernel: [    5.665702] microcode: CPU2: patch_level=0x06000605
Apr 16 04:41:28 miles-desktop kernel: [    5.674557] microcode: CPU2: new patch_level=0x0600063d
Apr 16 04:41:28 miles-desktop kernel: [    5.659932] microcode: CPU3: patch_level=0x06000605
Apr 16 04:41:28 miles-desktop kernel: [    5.675170] microcode: CPU4: patch_level=0x06000605
Apr 16 04:41:28 miles-desktop kernel: [    5.684019] microcode: CPU4: new patch_level=0x0600063d
Apr 16 04:41:28 miles-desktop kernel: [    5.656942] microcode: CPU5: patch_level=0x06000605
Apr 16 04:41:28 miles-desktop kernel: [    5.659932] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Apr 16 04:41:28 miles-desktop kernel: [    5.686551] <6>[fglrx] Maximum main memory to use for locked dma buffers: 15621 MBytes.
Apr 16 04:41:28 miles-desktop kernel: [    5.686934] <6>[fglrx]   vendor: 1002 device: 6818 count: 1
Apr 16 04:41:28 miles-desktop kernel: [    5.687978] <6>[fglrx] ioport: bar 4, base 0xe000, size: 0x100
Apr 16 04:41:28 miles-desktop kernel: [    5.688340] <6>[fglrx] Kernel PAT support is enabled
Apr 16 04:41:28 miles-desktop kernel: [    5.688416] <6>[fglrx] module loaded - fglrx 13.35.5 [Mar 12 2014] with 1 minors
Apr 16 04:41:28 miles-desktop kernel: [    5.724438] kvm: Nested Virtualization enabled
Apr 16 04:41:28 miles-desktop kernel: [    5.724483] kvm: Nested Paging enabled
Apr 16 04:41:28 miles-desktop kernel: [    5.771654] asus_wmi: ASUS WMI generic driver loaded
Apr 16 04:41:28 miles-desktop kernel: [    5.773832] asus_wmi: Initialization: 0x0
Apr 16 04:41:28 miles-desktop kernel: [    5.774025] asus_wmi: BIOS WMI version: 0.9
Apr 16 04:41:28 miles-desktop kernel: [    5.774129] asus_wmi: SFUN value: 0x0
Apr 16 04:41:28 miles-desktop kernel: [    5.774802] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input9
Apr 16 04:41:28 miles-desktop kernel: [    5.776562] asus_wmi: Disabling ACPI video driver
Apr 16 04:41:28 miles-desktop kernel: [    5.857951] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 04:41:28 miles-desktop kernel: [    5.992459] usbcore: registered new interface driver snd-usb-audio
Apr 16 04:41:28 miles-desktop kernel: [   26.460933] SKU: Nid=0x1d sku_cfg=0x4005e601
Apr 16 04:41:28 miles-desktop kernel: [   26.460935] SKU: port_connectivity=0x1
Apr 16 04:41:28 miles-desktop kernel: [   26.460936] SKU: enable_pcbeep=0x0
Apr 16 04:41:28 miles-desktop kernel: [   26.460937] SKU: check_sum=0x00000005
Apr 16 04:41:28 miles-desktop kernel: [   26.460938] SKU: customization=0x000000e6
Apr 16 04:41:28 miles-desktop kernel: [   26.460939] SKU: external_amp=0x0
Apr 16 04:41:28 miles-desktop kernel: [   26.460940] SKU: platform_type=0x0
Apr 16 04:41:28 miles-desktop kernel: [   26.460940] SKU: swap=0x0
Apr 16 04:41:28 miles-desktop kernel: [   26.460941] SKU: override=0x1
Apr 16 04:41:28 miles-desktop kernel: [   26.461367] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
Apr 16 04:41:28 miles-desktop kernel: [   26.461369]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Apr 16 04:41:28 miles-desktop kernel: [   26.461370]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Apr 16 04:41:28 miles-desktop kernel: [   26.461370]    mono: mono_out=0x0
Apr 16 04:41:28 miles-desktop kernel: [   26.461371]    dig-out=0x11/0x1e
Apr 16 04:41:28 miles-desktop kernel: [   26.461372]    inputs:
Apr 16 04:41:28 miles-desktop kernel: [   26.461373]      Front Mic=0x19
Apr 16 04:41:28 miles-desktop kernel: [   26.461374]      Rear Mic=0x18
Apr 16 04:41:28 miles-desktop kernel: [   26.461375]      Line=0x1a
Apr 16 04:41:28 miles-desktop kernel: [   26.461376] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
Apr 16 04:41:28 miles-desktop kernel: [   26.461377] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0892
Apr 16 04:41:28 miles-desktop kernel: [   26.474369] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
Apr 16 04:41:28 miles-desktop kernel: [   26.474433] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
Apr 16 04:41:28 miles-desktop kernel: [   26.474485] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
Apr 16 04:41:28 miles-desktop kernel: [   26.474535] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
Apr 16 04:41:28 miles-desktop kernel: [   26.474586] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input14
Apr 16 04:41:28 miles-desktop kernel: [   26.474634] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input15
Apr 16 04:41:28 miles-desktop kernel: [   26.474684] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input16
Apr 16 04:41:28 miles-desktop kernel: [   26.474734] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input17
Apr 16 04:41:28 miles-desktop kernel: [   26.475008] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
Apr 16 04:41:28 miles-desktop kernel: [   26.475009] hda-intel 0000:01:00.1: Using LPIB position fix
Apr 16 04:41:28 miles-desktop kernel: [   26.475010] hda-intel 0000:01:00.1: Force to non-snoop mode
Apr 16 04:41:28 miles-desktop kernel: [   26.475040] snd_hda_intel 0000:01:00.1: irq 87 for MSI/MSI-X
Apr 16 04:41:28 miles-desktop kernel: [   26.477457] hda-intel 0000:01:00.1: Enable sync_write for stable communication
Apr 16 04:41:28 miles-desktop kernel: [   26.481981] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input18
Apr 16 04:41:28 miles-desktop kernel: [   26.482042] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input19
Apr 16 04:41:28 miles-desktop kernel: [   26.482098] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input20
Apr 16 04:41:28 miles-desktop kernel: [   26.482148] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input21
Apr 16 04:41:28 miles-desktop kernel: [   26.482202] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input22
Apr 16 04:41:28 miles-desktop kernel: [   26.482251] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card2/input23
Apr 16 04:41:28 miles-desktop kernel: [   30.031288] Adding 16718844k swap on /dev/sdb5.  Priority:-1 extents:1 across:16718844k SSFS
Apr 16 04:41:28 miles-desktop kernel: [   30.033614] Adding 1998844k swap on /dev/sdc1.  Priority:-2 extents:1 across:1998844k SSFS
Apr 16 04:41:28 miles-desktop kernel: [   30.064603] EXT4-fs (sdc2): re-mounted. Opts: errors=remount-ro
Apr 16 04:41:28 miles-desktop kernel: [   38.340042] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Apr 16 04:41:28 miles-desktop kernel: [   38.346642] JFS: nTxBlock = 8192, nTxLock = 65536
Apr 16 04:41:28 miles-desktop kernel: [   38.356061] NTFS driver 2.1.30 [Flags: R/O MODULE].
Apr 16 04:41:28 miles-desktop kernel: [   38.370313] QNX4 filesystem 0.2.3 registered.
Apr 16 04:41:28 miles-desktop kernel: [   38.376933] xor: automatically using best checksumming function:
Apr 16 04:41:28 miles-desktop kernel: [   38.416028]    avx       : 12180.000 MB/sec
Apr 16 04:41:28 miles-desktop kernel: [   38.483872] raid6: sse2x1    5130 MB/s
Apr 16 04:41:28 miles-desktop kernel: [   38.551753] raid6: sse2x2    9737 MB/s
Apr 16 04:41:28 miles-desktop kernel: [   38.619639] raid6: sse2x4   13020 MB/s
Apr 16 04:41:28 miles-desktop kernel: [   38.619640] raid6: using algorithm sse2x4 (13020 MB/s)
Apr 16 04:41:28 miles-desktop kernel: [   38.619641] raid6: using ssse3x2 recovery algorithm
Apr 16 04:41:28 miles-desktop kernel: [   38.636501] bio: create slab <bio-1> at 1
Apr 16 04:41:28 miles-desktop kernel: [   38.637090] Btrfs loaded
Apr 16 04:41:28 miles-desktop kernel: [   55.024471] lp: driver loaded but no devices found
Apr 16 04:41:28 miles-desktop kernel: [   55.033484] it87: Found IT8721F chip at 0x290, revision 1
Apr 16 04:41:28 miles-desktop kernel: [   55.080470] AMD64 EDAC driver v3.4.0
Apr 16 04:41:28 miles-desktop kernel: [   55.080566] EDAC amd64: DRAM ECC disabled.
Apr 16 04:41:28 miles-desktop kernel: [   55.080574] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
Apr 16 04:41:28 miles-desktop kernel: [   55.080574]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
Apr 16 04:41:28 miles-desktop kernel: [   55.080574]  (Note that use of the override may cause unknown side effects.)
Apr 16 04:41:28 miles-desktop kernel: [   55.410010] Bluetooth: Core ver 2.16
Apr 16 04:41:28 miles-desktop kernel: [   55.410032] NET: Registered protocol family 31
Apr 16 04:41:28 miles-desktop kernel: [   55.410033] Bluetooth: HCI device and connection manager initialized
Apr 16 04:41:28 miles-desktop kernel: [   55.410041] Bluetooth: HCI socket layer initialized
Apr 16 04:41:28 miles-desktop kernel: [   55.410044] Bluetooth: L2CAP socket layer initialized
Apr 16 04:41:28 miles-desktop kernel: [   55.410050] Bluetooth: SCO socket layer initialized
Apr 16 04:41:28 miles-desktop kernel: [   55.412544] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Apr 16 04:41:28 miles-desktop kernel: [   55.412547] Bluetooth: BNEP filters: protocol multicast
Apr 16 04:41:28 miles-desktop kernel: [   55.412552] Bluetooth: BNEP socket layer initialized
Apr 16 04:41:28 miles-desktop kernel: [   55.413981] Bluetooth: RFCOMM TTY layer initialized
Apr 16 04:41:28 miles-desktop kernel: [   55.413990] Bluetooth: RFCOMM socket layer initialized
Apr 16 04:41:28 miles-desktop kernel: [   55.413991] Bluetooth: RFCOMM ver 1.11
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> NetworkManager (version 0.9.8.8) is starting...
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> WEXT support is enabled
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> DNS: loaded plugin dnsmasq
Apr 16 04:41:28 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.PolicyKit1' (using servicehelper)
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Found user 'avahi' (UID 110) and group 'avahi' (GID 116).
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Successfully dropped root privileges.
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: avahi-daemon 0.6.31 starting up.
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Successfully called chroot().
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Successfully dropped remaining capabilities.
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Loading service file /services/udisks.service.
Apr 16 04:41:28 miles-desktop kernel: [   55.483117] type=1400 audit(1397644888.836:2): apparmor="STATUS" operation="profile_load" parent=4430 profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=4440 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.483124] type=1400 audit(1397644888.836:3): apparmor="STATUS" operation="profile_load" parent=4430 profile="unconfined" name="chromium_browser" pid=4440 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.483486] type=1400 audit(1397644888.840:4): apparmor="STATUS" operation="profile_load" parent=4430 profile="unconfined" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=4439 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.483492] type=1400 audit(1397644888.840:5): apparmor="STATUS" operation="profile_load" parent=4430 profile="unconfined" name="chromium_browser" pid=4439 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.483783] type=1400 audit(1397644888.840:6): apparmor="STATUS" operation="profile_replace" parent=4430 profile="unconfined" name="chromium_browser" pid=4440 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.484006] type=1400 audit(1397644888.840:7): apparmor="STATUS" operation="profile_load" parent=4430 profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=4442 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.484013] type=1400 audit(1397644888.840:8): apparmor="STATUS" operation="profile_load" parent=4430 profile="unconfined" name="chromium_browser" pid=4442 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.484021] type=1400 audit(1397644888.840:9): apparmor="STATUS" operation="profile_replace" parent=4430 profile="unconfined" name="chromium_browser" pid=4439 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.484521] type=1400 audit(1397644888.840:10): apparmor="STATUS" operation="profile_replace" parent=4430 profile="unconfined" name="chromium_browser" pid=4442 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop kernel: [   55.487077] type=1400 audit(1397644888.840:11): apparmor="STATUS" operation="profile_load" parent=4430 profile="unconfined" name="/usr/sbin/mysqld-akonadi" pid=4450 comm="apparmor_parser"
Apr 16 04:41:28 miles-desktop polkitd[4425]: started daemon version 0.105 using authority implementation `local' version `0.105'
Apr 16 04:41:28 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Network interface enumeration completed.
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Registering HINFO record with values 'X86_64'/'LINUX'.
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Server startup complete. Host name is miles-desktop.local. Local service cookie is 1478068680.
Apr 16 04:41:28 miles-desktop avahi-daemon[4426]: Service "miles-desktop" (/services/udisks.service) successfully established.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: init!
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: update_system_hostname
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPluginIfupdown: management mode: unmanaged
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0)
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: end _init.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ofono: init!
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ofono: end _init.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> Loaded plugin (null): (null)
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    Ifupdown: get unmanaged devices count: 0
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: (11339008) ... get_connections.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ifupdown: (11339008) ... get_connections (managed=false): return empty list.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    keyfile: parsing Profile 1 ... 
Apr 16 04:41:28 miles-desktop kernel: [   55.502592] ppdev: user-space parallel port driver
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    keyfile:     read connection 'Profile 1'
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    keyfile: parsing XT1049 Network ... 
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    keyfile:     read connection 'XT1049 Network'
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ofono: (-738183824) ... get_connections.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    SCPlugin-Ofono: (-738183824) connections count: 0
Apr 16 04:41:28 miles-desktop NetworkManager[4406]:    Ifupdown: get unmanaged devices count: 0
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> WiFi hardware radio set enabled
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> Networking is enabled by state file
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> (eth0): carrier is OFF
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 16 04:41:28 miles-desktop NetworkManager[4406]: <info> (eth0): bringing up device.
Apr 16 04:41:28 miles-desktop ntpdate[4536]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Apr 16 04:41:28 miles-desktop ntpdate[4536]: no servers can be used, exiting
Apr 16 04:41:29 miles-desktop NetworkManager[4406]: <info> (eth0): preparing device.
Apr 16 04:41:29 miles-desktop NetworkManager[4406]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 16 04:41:29 miles-desktop NetworkManager[4406]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 16 04:41:29 miles-desktop NetworkManager[4406]: <warn> /sys/devices/virtual/net/lo: couldn't determine device driver; ignoring...
Apr 16 04:41:29 miles-desktop kernel: [   55.649240] r8169 0000:02:00.0 eth0: link down
Apr 16 04:41:29 miles-desktop kernel: [   55.649256] r8169 0000:02:00.0 eth0: link down
Apr 16 04:41:29 miles-desktop kernel: [   55.649288] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 04:41:29 miles-desktop kernel: [   55.649510] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Apr 16 04:41:29 miles-desktop NetworkManager[4406]: <info> ModemManager available in the bus
Apr 16 04:41:29 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.ColorManager' (using servicehelper)
Apr 16 04:41:29 miles-desktop colord: Using config file /etc/colord.conf
Apr 16 04:41:29 miles-desktop colord: Using mapping database file /var/lib/colord/mapping.db
Apr 16 04:41:29 miles-desktop colord: Using device database file /var/lib/colord/storage.db
Apr 16 04:41:29 miles-desktop colord: loaded plugin libcd_plugin_scanner.so
Apr 16 04:41:29 miles-desktop colord: plugin /usr/lib/x86_64-linux-gnu/colord-plugins/libcd_plugin_sane.so not loaded: plugin refused to load
Apr 16 04:41:29 miles-desktop colord: loaded plugin libcd_plugin_camera.so
Apr 16 04:41:29 miles-desktop colord: Daemon ready for requests
Apr 16 04:41:29 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.ColorManager'
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-07000710072007300740075007600770
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-7834e9a71bb75c472c56859940927dec
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-7cfad1a392b1ed7aaf7bd4cb60faaae4
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-79e56e42bf930a269bb6a0421eb80753
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-d0f2748c6e21eee954827c71e1e81c12
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-10080b14e236a5c33088e1d3404db83c
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-e729b445abc89051fe8ba7c6d8e9b127
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-781f6f71344167d3526631689139f109
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-dd1b891b264e83308a8b1f354cfbca12
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-eb2b99e986618d6a421e32a26568b9c2
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-b0701c2ccf059287d0b067464df8bda9
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-654b99c87e67edb1c1cfb0dcb7fa9d04
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-cfc9dd8a5ec9e96ebed35eb0271e58b4
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-c227f46f246694ba9971f270cb61a0c1
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-6ad6d63767ce0393245528ada92f1cb2
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-59641d682694acfe8c6f96fdf85bd63e
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-6a245ab2d8892e2e56232af93cd48b81
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-0383c34650771ce95ef93fe916867725
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-72f5b1cba915b68ea75cc843e270df5a
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-353a6bcabda00f04b6988f89126ce6f5
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-7b291073bdbbe0f2b32b7e3bccdce938
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-c3e6382fa9b2d31b01b736f6f97aac3a
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-523e494bc2f53c53d51d0758b07f4879
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-effe5db8db21fd1654c950f0a4e4b19a
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-a10be98be58460669fcdc6946939b7cf
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-3a2f991768eb90d7d1df3bbd321b533a
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-ba1807d66422db406033860b60d0ef1f
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-b8370820581b7df664fb7a52d576251f
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-7122a6ec78bc3d592e0cfcc73782c280
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-3a34aa6c3d1fb1ef63ff41e04ee00979
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-91a0293409a6b60f212e258c5b54336a
Apr 16 04:41:29 miles-desktop colord: Profile added: icc-87c7aaf8cdf533e9ce22a8d78a713517
Apr 16 04:41:29 miles-desktop colord: Profile added: EPSON_Artisan_830-Gray..
Apr 16 04:41:29 miles-desktop colord: Profile added: EPSON_Artisan_830-RGB..
Apr 16 04:41:29 miles-desktop anacron[4899]: Anacron 2.3 started on 2014-04-16
Apr 16 04:41:29 miles-desktop colord: Device added: cups-EPSON_Artisan_830
Apr 16 04:41:29 miles-desktop acpid: starting up with proc fs
Apr 16 04:41:29 miles-desktop cron[4631]: (CRON) INFO (pidfile fd = 3)
Apr 16 04:41:29 miles-desktop anacron[4899]: Normal exit (0 jobs run)
Apr 16 04:41:29 miles-desktop acpid: 9 rules loaded
Apr 16 04:41:29 miles-desktop acpid: waiting for events: event logging is off
Apr 16 04:41:29 miles-desktop cron[4947]: (CRON) STARTUP (fork ok)
Apr 16 04:41:29 miles-desktop cron[4947]: (CRON) INFO (Running @reboot jobs)
Apr 16 04:41:29 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.Accounts' (using servicehelper)
Apr 16 04:41:29 miles-desktop accounts-daemon[5223]: started daemon version 0.6.34
Apr 16 04:41:29 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.Accounts'
Apr 16 04:41:29 miles-desktop mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Apr 16 04:41:29 miles-desktop acpid: client connected from 5218[0:0]
Apr 16 04:41:29 miles-desktop acpid: 1 client rule loaded
Apr 16 04:41:30 miles-desktop mysqld: 140416  4:41:30 InnoDB: The InnoDB memory heap is disabled
Apr 16 04:41:30 miles-desktop mysqld: 140416  4:41:30 InnoDB: Mutexes and rw_locks use GCC atomic builtins
Apr 16 04:41:30 miles-desktop mysqld: 140416  4:41:30 InnoDB: Compressed tables use zlib 1.2.8
Apr 16 04:41:30 miles-desktop mysqld: 140416  4:41:30 InnoDB: Using Linux native AIO
Apr 16 04:41:30 miles-desktop mysqld: 140416  4:41:30 InnoDB: Initializing buffer pool, size = 256.0M
Apr 16 04:41:30 miles-desktop mysqld: 140416  4:41:30 InnoDB: Completed initialization of buffer pool
Apr 16 04:41:30 miles-desktop mysqld: 140416  4:41:30 InnoDB: highest supported file format is Barracuda.
Apr 16 04:41:30 miles-desktop kernel: [   56.739086] fglrx_pci 0000:01:00.0: irq 88 for MSI/MSI-X
Apr 16 04:41:30 miles-desktop kernel: [   56.739771] <6>[fglrx] Firegl kernel thread PID: 5425
Apr 16 04:41:30 miles-desktop kernel: [   56.739842] <6>[fglrx] Firegl kernel thread PID: 5426
Apr 16 04:41:30 miles-desktop kernel: [   56.739912] <6>[fglrx] Firegl kernel thread PID: 5427
Apr 16 04:41:30 miles-desktop kernel: [   56.740008] <6>[fglrx] IRQ 88 Enabled
Apr 16 04:41:30 miles-desktop kernel: [   56.750454] <6>[fglrx] Reserved FB block: Shared offset:0, size:1000000 
Apr 16 04:41:30 miles-desktop kernel: [   56.750456] <6>[fglrx] Reserved FB block: Unshared offset:f878000, size:4000 
Apr 16 04:41:30 miles-desktop kernel: [   56.750457] <6>[fglrx] Reserved FB block: Unshared offset:f87c000, size:484000 
Apr 16 04:41:30 miles-desktop kernel: [   56.750459] <6>[fglrx] Reserved FB block: Unshared offset:7ffef000, size:11000 
Apr 16 04:41:30 miles-desktop mysqld: 140416  4:41:30  InnoDB: Waiting for the background threads to start
Apr 16 04:41:30 miles-desktop gdm-simple-slave[5078]: Failed to give slave programs access to the display. Trying to proceed.
Apr 16 04:41:30 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Apr 16 04:41:30 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Apr 16 04:41:31 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Apr 16 04:41:31 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.UPower'
Apr 16 04:41:31 miles-desktop mysqld: 140416  4:41:31 Percona XtraDB ([http://www.percona.com](http://www.percona.com)) 5.5.36-MariaDB-33.0 started; log sequence number 6222998589
Apr 16 04:41:31 miles-desktop mysqld: 140416  4:41:31 [Note] Plugin 'FEEDBACK' is disabled.
Apr 16 04:41:31 miles-desktop mysqld: 140416  4:41:31 [Note] Recovering after a crash using /var/log/mysql/mariadb-bin
Apr 16 04:41:31 miles-desktop mysqld: 140416  4:41:31 [Note] Starting crash recovery...
Apr 16 04:41:31 miles-desktop mysqld: 140416  4:41:31 [Note] Crash recovery finished.
Apr 16 04:41:31 miles-desktop mysqld: 140416  4:41:31 [Note] Server socket created on IP: '127.0.0.1'.
Apr 16 04:41:31 miles-desktop mysqld: 140416  4:41:31 [Note] Event Scheduler: Loaded 0 events
Apr 16 04:41:31 miles-desktop mysqld: 140416  4:41:31 [Note] /usr/sbin/mysqld: ready for connections.
Apr 16 04:41:31 miles-desktop mysqld: Version: '5.5.36-MariaDB-1~saucy-log'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  mariadb.org binary distribution
Apr 16 04:41:31 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.RealtimeKit1' (using servicehelper)
Apr 16 04:41:31 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully called chroot.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully dropped privileges.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully limited resources.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Running.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Canary thread running.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Watchdog thread running.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully made thread 5732 of process 5732 (n/a) owned by '117' high priority at nice level -11.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Supervising 1 threads of 1 processes of 1 users.
Apr 16 04:41:31 miles-desktop anacron[5750]: Anacron 2.3 started on 2014-04-16
Apr 16 04:41:31 miles-desktop anacron[5750]: Normal exit (0 jobs run)
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully made thread 5755 of process 5732 (n/a) owned by '117' RT at priority 5.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Supervising 2 threads of 1 processes of 1 users.
Apr 16 04:41:31 miles-desktop ModemManager[4343]: <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0': not supported by any plugin
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully made thread 5899 of process 5732 (n/a) owned by '117' RT at priority 5.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Supervising 3 threads of 1 processes of 1 users.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully made thread 5903 of process 5732 (n/a) owned by '117' RT at priority 5.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Supervising 4 threads of 1 processes of 1 users.
Apr 16 04:41:31 miles-desktop /etc/mysql/debian-start[5908]: Upgrading MySQL tables if necessary.
Apr 16 04:41:31 miles-desktop mcelog: failed to prefill DIMM database from DMI data
Apr 16 04:41:31 miles-desktop /etc/mysql/debian-start[5912]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Apr 16 04:41:31 miles-desktop /etc/mysql/debian-start[5912]: Looking for 'mysql' as: /usr/bin/mysql
Apr 16 04:41:31 miles-desktop /etc/mysql/debian-start[5912]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Apr 16 04:41:31 miles-desktop /etc/mysql/debian-start[5912]: This installation of MySQL is already upgraded to 5.5.36-MariaDB, use --force if you still need to run mysql_upgrade
Apr 16 04:41:31 miles-desktop /etc/mysql/debian-start[5935]: Checking for insecure root accounts.
Apr 16 04:41:31 miles-desktop /etc/mysql/debian-start[5940]: Triggering myisam-recover for all MyISAM tables
Apr 16 04:41:31 miles-desktop postfix/master[6061]: daemon started -- version 2.10.2, configuration /etc/postfix
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully made thread 6082 of process 5732 (n/a) owned by '117' RT at priority 5.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Supervising 5 threads of 1 processes of 1 users.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully made thread 6083 of process 5732 (n/a) owned by '117' RT at priority 5.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Supervising 6 threads of 1 processes of 1 users.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Successfully made thread 6087 of process 6087 (n/a) owned by '117' high priority at nice level -11.
Apr 16 04:41:31 miles-desktop rtkit-daemon[5734]: Supervising 7 threads of 2 processes of 1 users.
Apr 16 04:41:31 miles-desktop pulseaudio[6087]: [pulseaudio] pid.c: Daemon already running.
Apr 16 04:41:31 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.locale1' (using servicehelper)
Apr 16 04:41:31 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.locale1'
Apr 16 04:41:31 miles-desktop colord: Profile added: icc-83c166a38e9fe980ca454de8b7f7568a
Apr 16 04:41:31 miles-desktop colord: Profile added: icc-b2a31c9e390105ba1fe6db2bd5e608db
Apr 16 04:41:31 miles-desktop colord: Profile added: icc-a20f6866b86622f01bdcfbc9d09ef397
Apr 16 04:41:31 miles-desktop kernel: [   58.580859] vboxdrv: Found 6 processor cores.
Apr 16 04:41:31 miles-desktop kernel: [   58.581495] vboxdrv: fAsync=0 offMin=0x645 offMax=0x8e3e
Apr 16 04:41:31 miles-desktop kernel: [   58.581569] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
Apr 16 04:41:31 miles-desktop kernel: [   58.581570] vboxdrv: Successfully loaded version 4.3.8 (interface 0x001a0007).
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> (eth0): carrier now ON (device state 20)
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> (eth0): device state change: unavailable -> disconnected (reason 'carrier-changed') [20 30 40]
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Auto-activating connection 'Profile 1'.
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) starting connection 'Profile 1'
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> (eth0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> NetworkManager state is now CONNECTING
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> (eth0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> (eth0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 16 04:41:31 miles-desktop kernel: [   58.599449] r8169 0000:02:00.0 eth0: link up
Apr 16 04:41:31 miles-desktop kernel: [   58.599456] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> dhclient started with pid 6156
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Beginning IP6 addrconf.
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Apr 16 04:41:31 miles-desktop dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 16 04:41:31 miles-desktop dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 16 04:41:31 miles-desktop dhclient: All rights reserved.
Apr 16 04:41:31 miles-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 16 04:41:31 miles-desktop dhclient: 
Apr 16 04:41:31 miles-desktop NetworkManager[4406]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Apr 16 04:41:31 miles-desktop dhclient: Listening on LPF/eth0/14:da:e9:0f:72:81
Apr 16 04:41:31 miles-desktop dhclient: Sending on   LPF/eth0/14:da:e9:0f:72:81
Apr 16 04:41:31 miles-desktop dhclient: Sending on   Socket/fallback
Apr 16 04:41:31 miles-desktop dhclient: DHCPREQUEST of 10.0.0.8 on eth0 to 255.255.255.255 port 67 (xid=0x69566259)
Apr 16 04:41:32 miles-desktop dhclient: DHCPACK of 10.0.0.8 from 10.0.0.1
Apr 16 04:41:32 miles-desktop dhclient: bound to 10.0.0.8 -- renewal in 274345 seconds.
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info>   address 10.0.0.8
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info>   prefix 24 (255.255.255.0)
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info>   gateway 10.0.0.1
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info>   nameserver '75.75.76.76'
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info>   nameserver '75.75.75.75'
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info>   domain name 'hsd1.ut.comcast.net.'
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 16 04:41:32 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Apr 16 04:41:32 miles-desktop avahi-daemon[4426]: Joining mDNS multicast group on interface eth0.IPv4 with address 10.0.0.8.
Apr 16 04:41:32 miles-desktop avahi-daemon[4426]: New relevant interface eth0.IPv4 for mDNS.
Apr 16 04:41:32 miles-desktop avahi-daemon[4426]: Registering new address record for 10.0.0.8 on eth0.IPv4.
Apr 16 04:41:32 miles-desktop kernel: [   58.789075] vboxpci: IOMMU not found (not registered)
Apr 16 04:41:32 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Apr 16 04:41:32 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.systemd1'
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> (eth0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> (eth0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> NetworkManager state is now CONNECTED_GLOBAL
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> Policy set 'Profile 1' (eth0) as default for IPv4 routing and DNS.
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> DNS: starting dnsmasq...
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <error> [1397644893.23590] [nm-dns-dnsmasq.c:400] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <warn> DNS: plugin dnsmasq update failed
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> Writing DNS information to /sbin/resolvconf
Apr 16 04:41:33 miles-desktop dnsmasq[6726]: started, version 2.66 cache disabled
Apr 16 04:41:33 miles-desktop dnsmasq[6726]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Apr 16 04:41:33 miles-desktop dnsmasq[6726]: DBus support enabled: connected to system bus
Apr 16 04:41:33 miles-desktop dnsmasq[6726]: warning: no upstream servers configured
Apr 16 04:41:33 miles-desktop goa[6725]: goa-daemon version 3.10.2 starting [main.c:117, main()]
Apr 16 04:41:33 miles-desktop postfix/master[6061]: reload -- version 2.10.2, configuration /etc/postfix
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> Activation (eth0) successful, device activated.
Apr 16 04:41:33 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <warn> dnsmasq appeared on DBus: :1.42
Apr 16 04:41:33 miles-desktop NetworkManager[4406]: <info> Writing DNS information to /sbin/resolvconf
Apr 16 04:41:33 miles-desktop dnsmasq[6726]: setting upstream servers from DBus
Apr 16 04:41:33 miles-desktop dnsmasq[6726]: using nameserver 75.75.75.75#53
Apr 16 04:41:33 miles-desktop dnsmasq[6726]: using nameserver 75.75.76.76#53
Apr 16 04:41:33 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 16 04:41:33 miles-desktop postfix/master[6061]: reload -- version 2.10.2, configuration /etc/postfix
Apr 16 04:41:33 miles-desktop colord: Automatic metadata add icc-b2a31c9e390105ba1fe6db2bd5e608db to xrandr-Ancor Communications Inc-VS248-D9LMQS090801
Apr 16 04:41:33 miles-desktop colord: Device added: xrandr-Ancor Communications Inc-VS248-D9LMQS090801
Apr 16 04:41:33 miles-desktop colord: Automatic metadata add icc-83c166a38e9fe980ca454de8b7f7568a to xrandr-Ancor Communications Inc-VE248-BALMQS091299
Apr 16 04:41:33 miles-desktop colord: Device added: xrandr-Ancor Communications Inc-VE248-BALMQS091299
Apr 16 04:41:33 miles-desktop colord: Automatic metadata add icc-a20f6866b86622f01bdcfbc9d09ef397 to xrandr-Ancor Communications Inc-VE248-BALMQS091303
Apr 16 04:41:33 miles-desktop colord: Device added: xrandr-Ancor Communications Inc-VE248-BALMQS091303
Apr 16 04:41:33 miles-desktop avahi-daemon[4426]: Joining mDNS multicast group on interface eth0.IPv6 with address 2601:b:5a80:7be:72:a5af:e6a1:6078.
Apr 16 04:41:33 miles-desktop avahi-daemon[4426]: New relevant interface eth0.IPv6 for mDNS.
Apr 16 04:41:33 miles-desktop avahi-daemon[4426]: Registering new address record for 2601:b:5a80:7be:72:a5af:e6a1:6078 on eth0.*.
Apr 16 04:41:33 miles-desktop avahi-daemon[4426]: Registering new address record for 2601:b:5a80:7be:16da:e9ff:fe0f:7281 on eth0.*.
Apr 16 04:41:36 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) starting DHCPv6 as requested by IPv6 router...
Apr 16 04:41:36 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Beginning DHCPv6 transaction (timeout in 45 seconds)
Apr 16 04:41:36 miles-desktop NetworkManager[4406]: <info> dhclient started with pid 7065
Apr 16 04:41:36 miles-desktop dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 16 04:41:36 miles-desktop dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 16 04:41:36 miles-desktop dhclient: All rights reserved.
Apr 16 04:41:36 miles-desktop dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Apr 16 04:41:36 miles-desktop dhclient: 
Apr 16 04:41:36 miles-desktop dhclient: Bound to *:546
Apr 16 04:41:36 miles-desktop dhclient: Listening on Socket/eth0
Apr 16 04:41:36 miles-desktop dhclient: Sending on   Socket/eth0
Apr 16 04:41:37 miles-desktop dhclient: XMT: Info-Request on eth0, interval 1000ms.
Apr 16 04:41:37 miles-desktop dhclient: RCV: Reply message on eth0 from fe80::21d:d3ff:fe30:d691.
Apr 16 04:41:37 miles-desktop NetworkManager[4406]: <info> (eth0): DHCPv6 client pid 7065 exited with status 0
Apr 16 04:41:37 miles-desktop NetworkManager[4406]: <info> (eth0): DHCPv6 state changed end -> renew6
Apr 16 04:41:37 miles-desktop NetworkManager[4406]: <info>   nameserver '2001:558:feed::2'
Apr 16 04:41:37 miles-desktop NetworkManager[4406]: <info>   nameserver '2001:558:feed::1'
Apr 16 04:41:37 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 5 of 5 (IPv6 Commit) scheduled...
Apr 16 04:41:37 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 5 of 5 (IPv6 Commit) started...
Apr 16 04:41:38 miles-desktop NetworkManager[4406]: <info> Policy set 'Profile 1' (eth0) as default for IPv6 routing and DNS.
Apr 16 04:41:38 miles-desktop NetworkManager[4406]: <info> Writing DNS information to /sbin/resolvconf
Apr 16 04:41:38 miles-desktop dnsmasq[6726]: setting upstream servers from DBus
Apr 16 04:41:38 miles-desktop dnsmasq[6726]: using nameserver 75.75.75.75#53
Apr 16 04:41:38 miles-desktop dnsmasq[6726]: using nameserver 2001:558:feed::1#53
Apr 16 04:41:38 miles-desktop dnsmasq[6726]: using nameserver 75.75.76.76#53
Apr 16 04:41:38 miles-desktop NetworkManager[4406]: <info> Activation (eth0) Stage 5 of 5 (IPv6 Commit) complete.
Apr 15 22:41:38 miles-desktop ntpdate[6856]: step time server 91.189.94.4 offset -21601.222922 sec
Apr 15 22:41:39 miles-desktop colord: Automatic remove of icc-83c166a38e9fe980ca454de8b7f7568a from xrandr-Ancor Communications Inc-VE248-BALMQS091299
Apr 15 22:41:39 miles-desktop colord: Profile removed: icc-83c166a38e9fe980ca454de8b7f7568a
Apr 15 22:41:39 miles-desktop colord: Automatic remove of icc-b2a31c9e390105ba1fe6db2bd5e608db from xrandr-Ancor Communications Inc-VS248-D9LMQS090801
Apr 15 22:41:39 miles-desktop colord: Profile removed: icc-b2a31c9e390105ba1fe6db2bd5e608db
Apr 15 22:41:39 miles-desktop colord: Automatic remove of icc-a20f6866b86622f01bdcfbc9d09ef397 from xrandr-Ancor Communications Inc-VE248-BALMQS091303
Apr 15 22:41:39 miles-desktop colord: Profile removed: icc-a20f6866b86622f01bdcfbc9d09ef397
Apr 15 22:41:39 miles-desktop colord: device removed: xrandr-Ancor Communications Inc-VS248-D9LMQS090801
Apr 15 22:41:39 miles-desktop colord: device removed: xrandr-Ancor Communications Inc-VE248-BALMQS091299
Apr 15 22:41:39 miles-desktop colord: device removed: xrandr-Ancor Communications Inc-VE248-BALMQS091303
Apr 15 22:41:39 miles-desktop gdm-simple-slave[5078]: Failed to remove slave program access to the display. Trying to proceed.
Apr 15 22:41:39 miles-desktop x-session-manager[7117]: WARNING: Could not parse desktop file caribou-autostart.desktop or it references a not found TryExec binary
Apr 15 22:41:39 miles-desktop x-session-manager[7117]: WARNING: Could not parse desktop file gnome-sound-applet.desktop or it references a not found TryExec binary
Apr 15 22:41:39 miles-desktop rtkit-daemon[5734]: Successfully made thread 7227 of process 7227 (n/a) owned by '1000' high priority at nice level -11.
Apr 15 22:41:39 miles-desktop rtkit-daemon[5734]: Supervising 7 threads of 2 processes of 2 users.
Apr 15 22:41:39 miles-desktop rtkit-daemon[5734]: Successfully made thread 7231 of process 7227 (n/a) owned by '1000' RT at priority 5.
Apr 15 22:41:39 miles-desktop rtkit-daemon[5734]: Supervising 8 threads of 2 processes of 2 users.
Apr 15 22:41:39 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.timedate1' (using servicehelper)
Apr 15 22:41:39 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.timedate1'
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Successfully made thread 7249 of process 7227 (n/a) owned by '1000' RT at priority 5.
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Supervising 9 threads of 2 processes of 2 users.
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Successfully made thread 7250 of process 7227 (n/a) owned by '1000' RT at priority 5.
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Supervising 10 threads of 2 processes of 2 users.
Apr 15 22:41:40 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.GeoClue2' (using servicehelper)
Apr 15 22:41:40 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.GeoClue2'
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Successfully made thread 7259 of process 7227 (n/a) owned by '1000' RT at priority 5.
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Supervising 11 threads of 2 processes of 2 users.
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Successfully made thread 7260 of process 7227 (n/a) owned by '1000' RT at priority 5.
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Supervising 12 threads of 2 processes of 2 users.
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Successfully made thread 7262 of process 7262 (n/a) owned by '1000' high priority at nice level -11.
Apr 15 22:41:40 miles-desktop rtkit-daemon[5734]: Supervising 13 threads of 3 processes of 2 users.
Apr 15 22:41:40 miles-desktop pulseaudio[7262]: [pulseaudio] pid.c: Daemon already running.
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-3e61204c35ece819bcb94cd8a13430a1
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-618286af9358858c6fe015d6f930e279
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-9505401116ba4f8c52d2ac9c91327f2d
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-018a3c2e98a74a94017540950fceeebc
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-2d00a97f48c03abdf0cc0f5c83b73c98
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-a0f705c343969157cbb5bc9806c01b6a
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-75952c52cc38a7cdf232f5041d5d9b8a
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-cf939994832f8219422ddace8fdbe281
Apr 15 22:41:40 miles-desktop colord: Profile added: icc-9cb609e31e32105eddca1b3ce6ea9d1c
Apr 15 22:41:41 miles-desktop goa[7360]: goa-daemon version 3.10.2 starting [main.c:117, main()]
Apr 15 22:41:41 miles-desktop signond[7362]: ../../../../src/signond/signondaemon.cpp 388 init Failed to SUID root. Secure storage will not be available. 
Apr 15 22:41:41 miles-desktop signond[7362]: ../../../../src/signond/credentialsaccessmanager.cpp 211 init Couldn't load AccessControlManager: "apparmor-ac" 
Apr 15 22:41:41 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.UDisks2' (using servicehelper)
Apr 15 22:41:41 miles-desktop udisksd[7400]: udisks daemon version 2.1.2 starting
Apr 15 22:41:41 miles-desktop udisksd[7400]: Applying configuration from /etc/udisks2/ST31000524AS-6VPDSRAY.conf to /dev/sdd
Apr 15 22:41:41 miles-desktop udisksd[7400]: Set standby timer to 600 seconds (value 120) on /dev/sdd [ST31000524AS-6VPDSRAY]
Apr 15 22:41:41 miles-desktop udisksd[7400]: Applying configuration from /etc/udisks2/ST3400820AS-9QG2THTT.conf to /dev/sde
Apr 15 22:41:41 miles-desktop udisksd[7400]: Set standby timer to 600 seconds (value 120) on /dev/sde [ST3400820AS-9QG2THTT]
Apr 15 22:41:41 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.UDisks2'
Apr 15 22:41:41 miles-desktop udisksd[7400]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Apr 15 22:41:41 miles-desktop udisksd[7400]: Cleaning up mount point /media/miles/linux_drive (device 8:65 is not mounted)
Apr 15 22:41:42 miles-desktop colord: Automatic metadata add icc-3e61204c35ece819bcb94cd8a13430a1 to xrandr-Ancor Communications Inc-VS248-D9LMQS090801
Apr 15 22:41:42 miles-desktop colord: Automatic metadata add icc-018a3c2e98a74a94017540950fceeebc to xrandr-Ancor Communications Inc-VS248-D9LMQS090801
Apr 15 22:41:42 miles-desktop colord: Automatic metadata add icc-cf939994832f8219422ddace8fdbe281 to xrandr-Ancor Communications Inc-VS248-D9LMQS090801
Apr 15 22:41:42 miles-desktop colord: Device added: xrandr-Ancor Communications Inc-VS248-D9LMQS090801
Apr 15 22:41:42 miles-desktop colord: Automatic metadata add icc-618286af9358858c6fe015d6f930e279 to xrandr-Ancor Communications Inc-VE248-BALMQS091299
Apr 15 22:41:42 miles-desktop colord: Automatic metadata add icc-2d00a97f48c03abdf0cc0f5c83b73c98 to xrandr-Ancor Communications Inc-VE248-BALMQS091299
Apr 15 22:41:42 miles-desktop colord: Automatic metadata add icc-75952c52cc38a7cdf232f5041d5d9b8a to xrandr-Ancor Communications Inc-VE248-BALMQS091299
Apr 15 22:41:42 miles-desktop colord: Device added: xrandr-Ancor Communications Inc-VE248-BALMQS091299
Apr 15 22:41:42 miles-desktop colord: Automatic metadata add icc-9505401116ba4f8c52d2ac9c91327f2d to xrandr-Ancor Communications Inc-VE248-BALMQS091303
Apr 15 22:41:42 miles-desktop colord: Device added: xrandr-Ancor Communications Inc-VE248-BALMQS091303
Apr 15 22:41:48 miles-desktop dbus[4298]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Apr 15 22:41:48 miles-desktop dbus[4298]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr 15 22:41:51 miles-desktop kernel: [   79.611426] EXT4-fs (sde1): recovery complete
Apr 15 22:41:51 miles-desktop kernel: [   79.626105] EXT4-fs (sde1): mounted filesystem with ordered data mode. Opts: (null)
Apr 15 22:41:51 miles-desktop udisksd[7400]: Mounted /dev/sde1 at /media/miles/linux_drive on behalf of uid 1000
Apr 15 22:45:01 miles-desktop CRON[8582]: (root) CMD (test -x /usr/sbin/mcelog -a ! -e /etc/mcelog-disabled && /usr/sbin/mcelog --ignorenodev --filter >> /var/log/mcelog)
```

---

### Post by QIII on 2014-04-16
When pasting lengthy code, please use code tags.

If you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by 3rdalbum on 2014-04-16
If you have overclocked your CPU, reduce the clock speed to normal and see if that helps. (If you have no idea what I have just said, then you have not overclocked).

Full kernel crashes like that are usually caused by bad RAM, a failing power supply, or a bad driver - namely, proprietary graphics drivers. If you are using the AMD or Nvidia proprietary driver instead of the default one, try disabling the proprietary driver and see if that helps.

If no change, then try testing your RAM. I recommend the old-fashioned approach where you remove a RAM stick and see if that solves the problem, and if it doesn't then try putting it back in and removing the other, etc. If this is not an option, running Memtest86 overnight might report problems. Or try the memory benchmark on Phoronix Test Suite, if that crashes your system it probably indicates bad RAM.

To troubleshoot a dying power supply... Well, you can only really swap it out for another one and see if that solves it.

I hope this helps.

---

