---
title: "Malformed grub file"
date: 2015-04-15
forum: New to Ubuntu
---

### Post by nonsisa on 2015-04-15
Okay I take You by the word.

How do I resolve the bug described in [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247)

None of the fixes work. Please find me a solution that actually does work.

I'm tight as a rubber band.

---

### Post by oldfred on 2015-04-15
Did you try the fix in #79?

Some find a total uninstall/reinstall of grub helps.

       chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

But often easier to use Boot-Repair's advanced mode to uninstall/reinstall grub. Do not just run the autofix. That just reinstalls grub to MBR from existing grub.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nonsisa on 2015-04-15
Yes I did try the fix in #79 but still it is corrupt.

I will try out Your new suggestions. Thanks

---

### Post by nonsisa on 2015-04-15
I just tried the:

sudo grub-install --recheck /dev/sdX
sudo update-grub

and that did not work.

---

### Post by nonsisa on 2015-04-15
I tried the boot repair option now.

Lets wait if it will be stable from now on.

One thing I noticed tough is that it added a win bootloader on my harddrives second partition.

---

### Post by ajgreeny on 2015-04-15
I have seen your comments at the bug in launchpad where you carried out the solution from bug report #79, then promptly reversed it by changing the grub default line in /etc/default/grub back to 0 again, instead of 1.

Leave it at 1 and and the malformed line error should disappear, as you had said it did immediately after doing the first edit to /etc/default/grub.

---

### Post by oldfred on 2015-04-15
Boot-Repair does copy bootmgr to the main install. Many users delete the 100MB Windows boot partition as it normally is hidden in Windows and they just do not know it is essential.
But then grub2's os-prober finds boot files in both partitions and gives you two entries.

If an issue we can explain how to turn off os-prober and copy just one boot stanza into 40_custom.

---

### Post by nonsisa on 2015-04-16
> **nonsisa said:**
> I tried the boot repair option now.

Lets wait if it will be stable from now on.

One thing I noticed tough is that it added a win bootloader on my harddrives second partition.

After a few times of rebooting I still get the error massage with the malformed file.

What else can I do?

---

### Post by nonsisa on 2015-04-16
Here the boot repair log, if it helps:

 [URL="http://paste.ubuntu.com/10828807/plain/"]Download as text```
[/URL]  [TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
493
494
495
496
497
498
499
500
501
502
503
504
505
506
507
508
509
510
511
512
513
514
515
516
517
518
519
520
521
522
523
524
525
526
527
528
529
530
531
532
533
534
535
536
537
538
539
540
541
542
543
544
545
546
547
548
549
550
551
552
553
554
555
556
557
558
559
560
561
562
563
564
565
566
567
568
569
570
571
572
573
574
575
576
577
578
579
580
581
582
583
584
585
586
587
588
589
590
591
592
593
594
595
596
597
598
599
600
601
602
603
604
605
606
607
608
609
610
611
612
613
614
615
616
617
618
619
620
621
622
623
624
625
626
627
628
629
630
631
632
633
634
635
636
637
638
639
640
641
642
643
644
645
646
647
648
649
650
651
652
653
654
655
656
657
658
659
660
661
662
663
664
665
666
667
668
669
670
671
672
673
674
675
676
677
678
679
680
681
682
683
684
685
686
687
688
689
690
691
692
693
694
695
696
697
698
699
700
701
702
703
704
705
706
707
708
709
710
711
712
713
714
715
716
717
718
719
720
721
722
723
724
725
726
727
728
729
730
731
732
733
734
735
736
737
738
739
740
741
742
743
744
745
746
747
748
749
750
751
752
753
754
755
756
757
758
759
760
761
762
763
764
765
766
767
768
769
770
771
772
773
774
775
776
777
778
779
780
781
782
783
784
785
786
787
788
789
790
791
792
793
794
795
796
797
798
799
800
801
802
803
804
805
806
807
808
809
810
811
812
813
814
815
816
817
818
819
820
821
822
823
824
825
826
827
828
829
830
831
832
833
834
835
[/TD]
[TD="class: code"] Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.2 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   567,173,119   566,966,272   7 NTFS / exFAT / HPFS
/dev/sda3         567,173,120   976,771,071   409,597,952   7 NTFS / exFAT / HPFS


GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 62.2 GB, 62176362496 bytes
255 heads, 63 sectors/track, 7559 cylinders, total 121438208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    62,841,859    62,841,797  83 Linux
/dev/sdb2          62,842,878    64,794,623     1,951,746   5 Extended
/dev/sdb5          62,842,880    64,794,623     1,951,744  82 Linux swap / Solaris
/dev/sdb3          64,794,624   121,436,159    56,641,536  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        EAE611E8E611B5B3                       ntfs       System-reserviert
/dev/sda2        04C42786C42778D6                       ntfs       Main
/dev/sda3        A6B63857B63829E7                       ntfs       X-tra
/dev/sdb1        550ccb88-0c6a-4089-8743-566816deef9c   ext4       
/dev/sdb3        07e9841d-f19a-4c96-ad08-ed5552f5f38d   ext4       
/dev/sdb5        df27a7ba-ca13-403f-8aca-e74707570fd4   swap       

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Apr 15 22:34 ata-ST500LT012-9WS142_W0V8YB82 -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 15 22:35 ata-ST500LT012-9WS142_W0V8YB82-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 15 22:35 ata-ST500LT012-9WS142_W0V8YB82-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 15 22:35 ata-ST500LT012-9WS142_W0V8YB82-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Apr 15 22:34 usb-SanDisk_Ultra_Fit_4C530123301125117574-0:0 -> ../../sdb
lrwxrwxrwx 1 root root 10 Apr 15 22:19 usb-SanDisk_Ultra_Fit_4C530123301125117574-0:0-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Apr 15 22:19 usb-SanDisk_Ultra_Fit_4C530123301125117574-0:0-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Apr 15 22:19 usb-SanDisk_Ultra_Fit_4C530123301125117574-0:0-part3 -> ../../sdb3
lrwxrwxrwx 1 root root 10 Apr 15 22:19 usb-SanDisk_Ultra_Fit_4C530123301125117574-0:0-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 Apr 15 22:34 wwn-0x5000c500609db19c -> ../../sda
lrwxrwxrwx 1 root root 10 Apr 15 22:35 wwn-0x5000c500609db19c-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Apr 15 22:35 wwn-0x5000c500609db19c-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Apr 15 22:35 wwn-0x5000c500609db19c-part3 -> ../../sda3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb3        /home                    ext4       (rw)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd1,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  550ccb88-0c6a-4089-8743-566816deef9c
else
  search --no-floppy --fs-uuid --set=root 550ccb88-0c6a-4089-8743-566816deef9c
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=de_AT
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-550ccb88-0c6a-4089-8743-566816deef9c' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  550ccb88-0c6a-4089-8743-566816deef9c
    else
      search --no-floppy --fs-uuid --set=root 550ccb88-0c6a-4089-8743-566816deef9c
    fi
    linux    /boot/vmlinuz-3.13.0-49-generic root=UUID=550ccb88-0c6a-4089-8743-566816deef9c ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-49-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-550ccb88-0c6a-4089-8743-566816deef9c' {
    menuentry 'Ubuntu, with Linux 3.13.0-49-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-49-generic-advanced-550ccb88-0c6a-4089-8743-566816deef9c' {
        recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  550ccb88-0c6a-4089-8743-566816deef9c
        else
          search --no-floppy --fs-uuid --set=root 550ccb88-0c6a-4089-8743-566816deef9c
        fi
        echo    'Loading Linux 3.13.0-49-generic ...'
        linux    /boot/vmlinuz-3.13.0-49-generic root=UUID=550ccb88-0c6a-4089-8743-566816deef9c ro  quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-49-generic
    }
    menuentry 'Ubuntu, with Linux 3.13.0-49-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-49-generic-recovery-550ccb88-0c6a-4089-8743-566816deef9c' {
        recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd1,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  550ccb88-0c6a-4089-8743-566816deef9c
        else
          search --no-floppy --fs-uuid --set=root 550ccb88-0c6a-4089-8743-566816deef9c
        fi
        echo    'Loading Linux 3.13.0-49-generic ...'
        linux    /boot/vmlinuz-3.13.0-49-generic root=UUID=550ccb88-0c6a-4089-8743-566816deef9c ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.13.0-49-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  550ccb88-0c6a-4089-8743-566816deef9c
    else
      search --no-floppy --fs-uuid --set=root 550ccb88-0c6a-4089-8743-566816deef9c
    fi
    knetbsd    /boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd1,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  550ccb88-0c6a-4089-8743-566816deef9c
    else
      search --no-floppy --fs-uuid --set=root 550ccb88-0c6a-4089-8743-566816deef9c
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-EAE611E8E611B5B3' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  EAE611E8E611B5B3
    else
      search --no-floppy --fs-uuid --set=root EAE611E8E611B5B3
    fi
    parttool ${root} hidden-
    chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-04C42786C42778D6' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  04C42786C42778D6
    else
      search --no-floppy --fs-uuid --set=root 04C42786C42778D6
    fi
    parttool ${root} hidden-
    chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=550ccb88-0c6a-4089-8743-566816deef9c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb3 during installation
UUID=07e9841d-f19a-4c96-ad08-ed5552f5f38d /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=df27a7ba-ca13-403f-8aca-e74707570fd4 none            swap    sw              0       0
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe

ADDITIONAL INFORMATION :
=================== log of boot-repair 2015-04-15__22h34 ===================
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
boot-repair is executed in installed-session (Ubuntu 14.04.2 LTS, trusty, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.13.0-49-generic root=UUID=550ccb88-0c6a-4089-8743-566816deef9c ro quiet splash vt.handoff=7

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sdb1:Das aktuell benutzte Betriebssystem - Ubuntu 14.04.2 LTS CurrentSession:linux
/dev/sda1:Windows 7 (loader):Windows:chain

=================== blkid:
/dev/sda1: LABEL="System-reserviert" UUID="EAE611E8E611B5B3" TYPE="ntfs"
/dev/sda2: LABEL="Main" UUID="04C42786C42778D6" TYPE="ntfs"
/dev/sda3: LABEL="X-tra" UUID="A6B63857B63829E7" TYPE="ntfs"
/dev/sdb1: UUID="550ccb88-0c6a-4089-8743-566816deef9c" TYPE="ext4"
/dev/sdb3: UUID="07e9841d-f19a-4c96-ad08-ed5552f5f38d" TYPE="ext4"
/dev/sdb5: UUID="df27a7ba-ca13-403f-8aca-e74707570fd4" TYPE="swap"


2 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== /etc/grub.d/ :
drwxr-xr-x  2 root root      4096 Jul 23  2014 grub.d
insgesamt 76
-rwxr-xr-x 1 root root  9424 Mai 15  2014 00_header
-rwxr-xr-x 1 root root  6058 Mai  8  2014 05_debian_theme
-rwxr-xr-x 1 root root 11608 Mai 15  2014 10_linux
-rwxr-xr-x 1 root root 10412 Mai 15  2014 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mär 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 Mai 15  2014 30_os-prober
-rwxr-xr-x 1 root root  1416 Mai 15  2014 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Mai 15  2014 40_custom
-rwxr-xr-x 1 root root   216 Mai 15  2014 41_custom
-rw-r--r-- 1 root root   483 Mai 15  2014 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
#GRUB_SAVEDEFAULT=true





=================== sdb1saved_entry=gnulinux-simple-550ccb88-0c6a-4089-8743-566816deef9c/grub/grubenv :
saved_entry=gnulinux-simple-550ccb88-0c6a-4089-8743-566816deef9c




=================== UEFI/Legacy mode:
This installed-session is not EFI-compatible.
EFI in dmesg.
[    0.000000] ACPI: UEFI 9affd000 000236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sdb1    : sdb,    not-sepboot,    grubenv-ng    grub2,    grub-pc ,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda3    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda3.
sdb3    : sdb,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /home.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     usb-disk,    has-os,    63 sectors * 512 bytes
sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Model: ATA ST500LT012-9WS14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: SanDisk Ultra Fit (scsi)
Disk /dev/sdb: 62.2GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      32.3kB  32.2GB  32.2GB  primary   ext4            boot
2      32.2GB  33.2GB  999MB   extended
5      32.2GB  33.2GB  999MB   logical   linux-swap(v1)
3      33.2GB  62.2GB  29.0GB  primary   ext4

=================== parted -lm:

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
BYT;
/dev/sda:500GB:scsi:512:4096:gpt:ATA ST500LT012-9WS14;

BYT;
/dev/sdb:62.2GB:scsi:512:512:msdos:SanDisk Ultra Fit;
1:32.3kB:32.2GB:32.2GB:ext4::boot;
2:32.2GB:33.2GB:999MB:::;
5:32.2GB:33.2GB:999MB:linux-swap(v1)::;
3:33.2GB:62.2GB:29.0GB:ext4::;

=================== lsblk:
KNAME TYPE FSTYPE   SIZE LABEL     MODEL    UUID
sda   disk        465,8G           ST500LT0
sda1  part ntfs     100M System-reserviert
EAE611E8E611B5B3
sda2  part ntfs   270,4G Main               04C42786C42778D6
sda3  part ntfs   195,3G X-tra              A6B63857B63829E7
sdb   disk         57,9G           Ultra Fi
sdb1  part ext4      30G                    550ccb88-0c6a-4089-8743-566816deef9c
sdb2  part            1K
sdb3  part ext4      27G                    07e9841d-f19a-4c96-ad08-ed5552f5f38d
sdb5  part swap     953M                    df27a7ba-ca13-403f-8aca-e74707570fd4

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /mnt/boot-sav/sda2
sda3     1  0  0         /mnt/boot-sav/sda3
sdb      1  0  1 running
sdb1     1  0  1         /
sdb2     1  0  1
sdb3     1  0  1         /home
sdb5     1  0  1         [SWAP]


=================== mount:
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=blacktop)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /mnt/boot-sav/sda3 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 sdb5 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdb3 sdb5 sg0 sg1 shm snapshot snd stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhci vhost-net video0 zero
ls /dev/mapper:  control
ls: Zugriff auf  nicht möglich: Datei oder Verzeichnis nicht gefunden

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  b3 b5 11 e6 e8 11 e6 ea  |................|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 37 cb 21 00 00 00 00  |.........7.!....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  d6 78 27 c4 86 27 c4 04  |.........x'..'..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 46 65  |t.............Fe|
00000190  68 6c 65 72 20 62 65 69  6d 20 4c 65 73 65 6e 20  |hler beim Lesen |
000001a0  64 65 73 20 44 61 74 65  6e 74 72 84 67 65 72 73  |des Datentr.gers|
000001b0  00 0d 0a 42 4f 4f 54 4d  47 52 20 66 65 68 6c 74  |...BOOTMGR fehlt|
000001c0  00 0d 0a 42 4f 4f 54 4d  47 52 20 6b 6f 6d 70 72  |...BOOTMGR kompr|
000001d0  69 6d 69 65 72 74 00 0d  0a 4e 65 75 73 74 61 72  |imiert...Neustar|
000001e0  74 20 6d 69 74 20 53 74  72 67 2b 41 6c 74 2b 45  |t mit Strg+Alt+E|
000001f0  6e 74 66 0d 0a 00 0a 00  8c b1 c1 d7 00 00 55 aa  |ntf...........U.|
00000200

=================== hexdump -n512 -C /dev/sda3
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 60 ce 21  |........?....`.!|
00000020  00 00 00 00 80 00 80 00  ff f7 69 18 00 00 00 00  |..........i.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  e7 29 38 b6 57 38 b6 a6  |.........)8.W8..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 46 65  |t.............Fe|
00000190  68 6c 65 72 20 62 65 69  6d 20 4c 65 73 65 6e 20  |hler beim Lesen |
000001a0  64 65 73 20 44 61 74 65  6e 74 72 84 67 65 72 73  |des Datentr.gers|
000001b0  00 0d 0a 42 4f 4f 54 4d  47 52 20 66 65 68 6c 74  |...BOOTMGR fehlt|
000001c0  00 0d 0a 42 4f 4f 54 4d  47 52 20 6b 6f 6d 70 72  |...BOOTMGR kompr|
000001d0  69 6d 69 65 72 74 00 0d  0a 4e 65 75 73 74 61 72  |imiert...Neustar|
000001e0  74 20 6d 69 74 20 53 74  72 67 2b 41 6c 74 2b 45  |t mit Strg+Alt+E|
000001f0  6e 74 66 0d 0a 00 0a 00  8c b1 c1 d7 00 00 55 aa  |ntf...........U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      ext4       30G  4.0G   24G  15% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     797M  1.4M  796M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     3.9G   80K  3.9G   1% /run/shm
none           tmpfs     100M   32K  100M   1% /run/user
/dev/sdb3      ext4       27G  3.6G   22G  15% /home
/dev/sda1      fuseblk   100M   57M   44M  57% /mnt/boot-sav/sda1
/dev/sda2      fuseblk   271G  120G  151G  45% /mnt/boot-sav/sda2
/dev/sda3      fuseblk   196G  6.8G  189G   4% /mnt/boot-sav/sda3

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x57cb5d9d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   567173119   283483136    7  HPFS/NTFS/exFAT
/dev/sda3       567173120   976771071   204798976    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 62.2 GB, 62176362496 bytes
255 heads, 63 sectors/track, 7559 cylinders, total 121438208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ebb7a

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    62841859    31420898+  83  Linux
/dev/sdb2        62842878    64794623      975873    5  Extended
/dev/sdb3        64794624   121436159    28320768   83  Linux
/dev/sdb5        62842880    64794623      975872   82  Linux swap / Solaris


User choice: Ist sdb (62.2GB) ein austauschbarer Datenträger? yes



=================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub2 of sdb1 into the MBR of sdb.
It will also fix access to other systems (other MBRs) for the situations when the removable media is disconnected.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot


Quantity of real Windows: 1
WinSE in sda2
Copied Win boot files from sda1 to sda2
sdb is removable, so we reinstall GRUB of the removable media only in its disk MBR

*******lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
Subsystem: Acer Incorporated [ALI] Device [1025:0798]
Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
*******

grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1,grub-install (GRUB) 2.

Reinstall the GRUB of sdb1 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Unhide GRUB boot menu in sdb1/boot/grub/grub.cfg

Bootsektor wurde erfolgreich repariert.

Sie können Ihren Rechner nun neu starten.
Bitte vergessen Sie nicht, das BIOS so zu konfigurieren, dass vom Wechseldatenträger gebootet wird!
[/TD]
[/TR]
[/TABLE]
 
```
 [Download as text]("http://paste.ubuntu.com/10828807/plain/")

---

### Post by nonsisa on 2015-04-16
> **ajgreeny said:**
> I have seen your comments at the bug in launchpad where you carried out the solution from bug report #79, then promptly reversed it by changing the grub default line in /etc/default/grub back to 0 again, instead of 1.

Leave it at 1 and and the malformed line error should disappear, as you had said it did immediately after doing the first edit to /etc/default/grub.

No, that does not work. I still get the same error, even when I set the default line on 1.

---

### Post by oldfred on 2015-04-16
Please use code tags or # in advanced editor. Better to just have posted the link that Boot-Repair gives.

Was sda originally Windows 8  in UEFI boot mode? 
When you reinstall Windows in BIOS boot mode it converts to MBR partitioning but does it incorrectly. And leaves the backup gpt partition table on drive. Linux tools see both MBR & gpt so can only erase drive to be one or the other. But you can use fixparts to remove backup gpt data.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
    
If you have a new UEFI system, better to have installed Windows 7 in UEFI mode. But you have to copy to flash drive and move some files around to make it boot in UEFI mode. Default is BIOS with MBR partitioning.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

    
And I knew I was eventually getting a UEFI system, so started converting my Ubuntu only drives and data only drives to gpt a long time ago. And on newer drives that I might move to new system, I included an efi partition for UEFI boot and the bios_grub partition so I could boot in BIOS mode.
Windows only boots from gpt drives with UEFI.
Windows only boots from MBR(msdos) drives with BIOS.
But Ubuntu can boot from gpt with either BIOS or UEFI.
But always have all systems booting in same boot mode, either all UEFI or all BIOS.

---

