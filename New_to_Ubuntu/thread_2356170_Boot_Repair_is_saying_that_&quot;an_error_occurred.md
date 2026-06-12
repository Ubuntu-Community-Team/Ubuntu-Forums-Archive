---
title: "Boot Repair is saying that &quot;an error occurred during the repair&quot;"
date: 2017-03-20
forum: New to Ubuntu
---

### Post by robinlp on 2017-03-20
[I never posted here before. Please tell me, and excuse me in advance, if I am missing some usage rules.]

Hi all,

This morning, all of a sudden, my laptop stopped booting (Acer Aspire V Nitro, Ubuntu 16.04).

I tried the "recommended repair" tool from Boot Repair on a Live USB, without success: a system-error window pops up during the process, then Boot Repair finally concludes that "an error occurred during the repair."

Here is the boot info: [http://paste2.org/HbBe2eXN](http://paste2.org/HbBe2eXN)

The main claim I understand from this summary is the following:* Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector** 97486056 of the same hard drive for core.img, but core.img can not be **found at this location.*

I currently have two possible interpretations for this message:
1) Grub2 suddenly does not look any more at the right sector.
2) It does, but OS is not there any more.

Well, this is just a very rough guess from a beginner. Does someone know how I could clarify the situation and then, hopefully, solve it?

Thanks in advance!

---

### Post by alexandari on 2017-03-21
Boot a rescue disk or a live cd and run ```
sudo badblocks -n /dev/sdx
```. This scans for bad blocks/sectors on your hard drive. To me it seems like your hard disk is failing, but please provide the output to this command first

---

### Post by robinlp on 2017-03-21
Thanks for your reply.

The result is a list of 737 blocks (see below), that I assume are corrupted.

I will run the command again with the verbose option (-v) to see if more details are then available.

If these blocks are now corrupted, what is then my best option?

1) Repair the bad blocks on this SSD, hoping that I can have my OS back this way. I don't know if its even possible?

2) Reinstall the OS on the same SSD, hoping that it won't happen again in a near future. Should I do the installation in such a way that it avoids the bad blocks, or will it be automatic?

3) Change my SSD because it might worsen in the future. (Note: it is only two years old.)

```
52
53
54
55
540
541
542
543
580
581
582
583
620
621
622
623
2716
2717
2718
2719
2744
2745
2746
2747
5236
5237
5238
5239
5316
5317
5318
5319
5440
5441
5442
5443
47472
47473
47474
47475
47500
47501
47502
47503
47664
47665
47666
47667
47920
47921
47922
47923
48176
48177
48178
48179
48368
48369
48370
48371
48492
48493
48494
48495
48748
48749
48750
48751
49004
49005
49006
49007
49744
49745
49746
49747
54272
54273
54274
54275
54520
54521
54522
54523
54776
54777
54778
54779
55032
55033
55034
55035
55224
55225
55226
55227
55532
55533
55534
55535
55604
55605
55606
55607
55860
55861
55862
55863
56116
56117
56118
56119
56556
56557
56558
56559
56812
56813
56814
56815
57068
57069
57070
57071
57324
57325
57326
57327
57432
57433
57434
57435
76152
76153
76154
76155
76408
76409
76410
76411
76664
76665
76666
76667
76792
76793
76794
76795
77144
77145
77146
77147
77300
77301
77302
77303
77556
77557
77558
77559
77812
77813
77814
77815
78068
78069
78070
78071
78412
78413
78414
78415
78668
78669
78670
78671
78924
78925
78926
78927
79180
79181
79182
79183
79404
79405
79406
79407
83212
83213
83214
83215
83436
83437
83438
83439
83692
83693
83694
83695
83948
83949
83950
83951
84204
84205
84206
84207
84452
84453
84454
84455
84708
84709
84710
84711
84964
84965
84966
84967
85220
85221
85222
85223
85572
85573
85574
85575
85828
85829
85830
85831
86084
86085
86086
86087
86340
86341
86342
86343
86596
86597
86598
86599
86860
86861
86862
86863
87132
87133
87134
87135
87388
87389
87390
87391
87644
87645
87646
87647
87900
87901
87902
87903
88136
88137
88138
88139
88216
88217
88218
88219
88472
88473
88474
88475
88728
88729
88730
88731
89068
89069
89070
89071
89328
89329
89330
89331
89584
89585
89586
89587
89840
89841
89842
89843
90096
90097
90098
90099
90352
90353
90354
90355
90464
90465
90466
90467
90720
90721
90722
90723
90976
90977
90978
90979
91232
91233
91234
91235
91584
91585
91586
91587
91932
91933
91934
91935
92188
92189
92190
92191
92444
92445
92446
92447
92700
92701
92702
92703
92852
92853
92854
92855
93108
93109
93110
93111
93364
93365
93366
93367
93620
93621
93622
93623
93852
93853
93854
93855
323356
323357
323358
323359
323612
323613
323614
323615
323868
323869
323870
323871
324124
324125
324126
324127
324380
324381
324382
324383
324740
324741
324742
324743
324892
324893
324894
324895
325148
325149
325150
325151
325404
325405
325406
325407
325660
325661
325662
325663
325916
325917
325918
325919
326172
326173
326174
326175
326428
326429
326430
326431
326788
326789
326790
326791
326940
326941
326942
326943
327196
327197
327198
327199
327452
327453
327454
327455
327708
327709
327710
327711
327964
327965
327966
327967
328220
328221
328222
328223
328476
328477
328478
328479
328836
328837
328838
328839
328988
328989
328990
328991
329244
329245
329246
329247
329500
329501
329502
329503
329756
329757
329758
329759
330012
330013
330014
330015
330268
330269
330270
330271
330524
330525
330526
330527
330884
330885
330886
330887
331036
331037
331038
331039
331292
331293
331294
331295
331548
331549
331550
331551
331804
331805
331806
331807
332060
332061
332062
332063
332316
332317
332318
332319
332572
332573
332574
332575
332932
332933
332934
332935
333084
333085
333086
333087
333340
333341
333342
333343
333596
333597
333598
333599
333852
333853
333854
333855
334108
334109
334110
334111
334364
334365
334366
334367
334620
334621
334622
334623
334980
334981
334982
334983
335132
335133
335134
335135
335388
335389
335390
335391
335644
335645
335646
335647
335900
335901
335902
335903
336156
336157
336158
336159
336412
336413
336414
336415
336668
336669
336670
336671
337028
337029
337030
337031
337180
337181
337182
337183
337436
337437
337438
337439
337692
337693
337694
337695
337948
337949
337950
337951
338204
338205
338206
338207
338460
338461
338462
338463
338716
338717
338718
338719
339076
339077
339078
339079
339228
339229
339230
339231
339484
339485
339486
339487
339740
339741
339742
339743
339996
339997
339998
339999
340252
340253
340254
340255
340508
340509
340510
340511
340764
340765
340766
340767
341124
341125
341126
341127
341276
341277
341278
341279
341532
341533
341534
341535
341788
341789
341790
341791
342044
342045
342046
342047
342300
342301
342302
342303
342556
342557
342558
342559
342812
342813
342814
342815
343172
343173
343174
343175
343324
343325
343326
343327
343580
343581
343582
343583
343836
343837
343838
343839
344092
344093
344094
344095
344348
344349
344350
344351
344604
344605
344606
344607
344860
344861
344862
344863
345212
345213
345214
345215
443492
443493
443494
443495
445569
445570
445571
447416
447417
447418
447419
586828
586829
586830
586831
707905
707906
707907
716289
716290
716291
743712
743713
743714
743715
743992
743993
743994
743995
744384
744385
744386
744387
```

---

### Post by oldfred on 2017-03-21
Not sure about the bad blocks issue.

But you have grub installed to both MBR for BIOS boot and ESP - efi system partition for UEFI boot.

Your fstab shows the mount of the efi partition, so you really are UEFI boot. And then should not have grub in gpt drive's protective MBR.
So always boot in UEFI mode and always boot installer in UEFI mode to make repairs, attempting to repair in BIOS mode just confuses it.

Grub in MBR is not used, nor is MBR otherwise used, so leaving it probably best as trying to erase can be dangerous. But if you ever try to boot in BIOS mode it will just give errors.

---

### Post by robinlp on 2017-03-21
Badblocks with verbose gives:

```
Checking for bad blocks in non-destructive read-write mode
From block 0 to 58615703
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
```

So, that's good news. :)


> **oldfred said:**
> Not sure about the bad blocks issue.

But you have grub installed to both MBR for BIOS boot and ESP - efi system partition for UEFI boot.

Your fstab shows the mount of the efi partition, so you really are UEFI boot. And then should not have grub in gpt drive's protective MBR.
So always boot in UEFI mode and always boot installer in UEFI mode to make repairs, attempting to repair in BIOS mode just confuses it.

Grub in MBR is not used, nor is MBR otherwise used, so leaving it probably best as trying to erase can be dangerous. But if you ever try to boot in BIOS mode it will just give errors.

My BIOS config states that it currently uses "UEFI mode" (and not "Legacy", that is the only other option available).

Yet, I am not sure that the live USB I am currently booting on also uses UEFI mode. This is now what I will check.

Thanks again for your help.

---

### Post by robinlp on 2017-03-21
The command```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Not UEFI"
```answers "UEFI" when I am running it on the live session. Is it sufficient to be sure that the live USB I use is running with UEFI mode?

If so, everything is using this mode: the boot option in BIOS, the OS I am trying to boot, and my bootable USB.

What could be my next step?

---

### Post by oldfred on 2017-03-21
Either just the auto fix that updates grub settings,  or the total reinstall of grub that makes sure everything is in sync.

---

