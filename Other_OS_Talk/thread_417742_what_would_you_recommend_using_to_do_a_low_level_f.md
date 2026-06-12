---
title: "what would you recommend using to do a low level format of a DVD+RW??"
date: 2007-04-21
forum: Other OS Talk
---

### Post by billdotson on 2007-04-21
I seriously have ruined WAY too many DVD+RWs.. I bought a spindle of 25 and now 8 are ruined.

What can I use to do a low level format to try to save them before they turn into expensive coasters?

---

### Post by billdotson on 2007-04-21
help?

---

### Post by pseudonym on 2007-04-22
You don't need to do a low-level format on a DVD+RW, unless you want to securely wipe the data. Otherwise just overwrite whatever's on them, as if it was a blank disk. Your DVD burning app will spit out a warning, but just continue on anyway. This is how this particular media is supposed to be used.

Virgin DVD+RW disks need to be formatted for initial use, but this gets done automatically by your DVD burning app. There is nothing you need to do specially.

But if you want to nullify the media, e.g. for privacy reasons, you can do it in the terminal with - ```
growisofs -Z /dev/dvd=/dev/zero
``` As you can see, this writes zeroes to the disk, thereby wiping whatever was on it.

Note that DVD-RW disks need to be blanked, however. Again, your DVD burning app will have an option to do this, but you can also use the terminal - ```
dvd+rw-format -blank /dev/dvd
``` Only do this with -RWs, not +RWs. Doing so will likely render them unusable.

---

### Post by billdotson on 2007-04-22
thanks I will try that.  Hopefully it will make those 8 DVD+RW's I ruined usable again!!! Thanks again!  do you have a jabber, IRC 9static) or AIM nick?

now I edit:  I ran that command and it seemed to be going fine at the end but after 98% was written it said there was so space left on the device.  Here is the output:

```

ubuntu@ubuntu:~$ growisofs -Z /dev/hdb=/dev/zero
WARNING: /dev/hdb already carries isofs!
About to execute 'builtin_dd if=/dev/zero of=/dev/hdb obs=32k seek=0'
/dev/hdb: restarting DVD+RW format...
/dev/hdb: "Current Write Speed" is 4.0x1385KBps.
         0/4700372992 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
   8388608/4700372992 ( 0.2%) @1.8x, remaining 83:53 RBU 100.0%
  27459584/4700372992 ( 0.6%) @4.0x, remaining 34:02 RBU 100.0%
  46563328/4700372992 ( 1.0%) @4.0x, remaining 24:59 RBU 100.0%
  65634304/4700372992 ( 1.4%) @4.0x, remaining 22:21 RBU 100.0%
  84705280/4700372992 ( 1.8%) @4.0x, remaining 19:58 RBU 100.0%
 103776256/4700372992 ( 2.2%) @4.0x, remaining 18:27 RBU 100.0%
 122847232/4700372992 ( 2.6%) @4.0x, remaining 18:00 RBU 100.0%
 141918208/4700372992 ( 3.0%) @4.0x, remaining 17:07 RBU 100.0%
 160989184/4700372992 ( 3.4%) @4.0x, remaining 16:26 RBU 100.0%
 180060160/4700372992 ( 3.8%) @4.0x, remaining 16:19 RBU 100.0%
 199131136/4700372992 ( 4.2%) @4.0x, remaining 15:49 RBU 100.0%
 218202112/4700372992 ( 4.6%) @4.0x, remaining 15:24 RBU 100.0%
 237273088/4700372992 ( 5.0%) @4.0x, remaining 15:21 RBU 100.0%
 256376832/4700372992 ( 5.5%) @4.0x, remaining 15:01 RBU 100.0%
 275447808/4700372992 ( 5.9%) @4.0x, remaining 14:43 RBU 100.0%
 294518784/4700372992 ( 6.3%) @4.0x, remaining 14:42 RBU 100.0%
 313589760/4700372992 ( 6.7%) @4.0x, remaining 14:27 RBU 100.0%
 332660736/4700372992 ( 7.1%) @4.0x, remaining 14:13 RBU 100.0%
 351731712/4700372992 ( 7.5%) @4.0x, remaining 14:13 RBU 100.0%
 370802688/4700372992 ( 7.9%) @4.0x, remaining 14:00 RBU 100.0%
 389873664/4700372992 ( 8.3%) @4.0x, remaining 13:49 RBU 100.0%
 408977408/4700372992 ( 8.7%) @4.0x, remaining 13:48 RBU 100.0%
 428048384/4700372992 ( 9.1%) @4.0x, remaining 13:38 RBU 100.0%
 447119360/4700372992 ( 9.5%) @4.0x, remaining 13:28 RBU 100.0%
 466190336/4700372992 ( 9.9%) @4.0x, remaining 13:28 RBU 100.0%
 485261312/4700372992 (10.3%) @4.0x, remaining 13:19 RBU 100.0%
 504332288/4700372992 (10.7%) @4.0x, remaining 13:10 RBU 100.0%
 523403264/4700372992 (11.1%) @4.0x, remaining 13:10 RBU 100.0%
 542474240/4700372992 (11.5%) @4.0x, remaining 13:01 RBU 100.0%
 561545216/4700372992 (11.9%) @4.0x, remaining 12:53 RBU 100.0%
 580648960/4700372992 (12.4%) @4.0x, remaining 12:53 RBU 100.0%
 599719936/4700372992 (12.8%) @4.0x, remaining 12:45 RBU 100.0%
 618758144/4700372992 (13.2%) @4.0x, remaining 12:38 RBU 100.0%
 637861888/4700372992 (13.6%) @4.0x, remaining 12:37 RBU 100.0%
 656932864/4700372992 (14.0%) @4.0x, remaining 12:30 RBU 100.0%
 676003840/4700372992 (14.4%) @4.0x, remaining 12:24 RBU 100.0%
 695074816/4700372992 (14.8%) @4.0x, remaining 12:23 RBU 100.0%
 714145792/4700372992 (15.2%) @4.0x, remaining 12:16 RBU 100.0%
 733249536/4700372992 (15.6%) @4.0x, remaining 12:10 RBU 100.0%
 752320512/4700372992 (16.0%) @4.0x, remaining 12:09 RBU 100.0%
 771391488/4700372992 (16.4%) @4.0x, remaining 12:03 RBU 100.0%
 790462464/4700372992 (16.8%) @4.0x, remaining 11:57 RBU 100.0%
 809533440/4700372992 (17.2%) @4.0x, remaining 11:56 RBU 100.0%
 828637184/4700372992 (17.6%) @4.0x, remaining 11:50 RBU 100.0%
 847708160/4700372992 (18.0%) @4.0x, remaining 11:44 RBU 100.0%
 866779136/4700372992 (18.4%) @4.0x, remaining 11:43 RBU 100.0%
 885850112/4700372992 (18.8%) @4.0x, remaining 11:37 RBU 100.0%
 904921088/4700372992 (19.3%) @4.0x, remaining 11:32 RBU 100.0%
 923992064/4700372992 (19.7%) @4.0x, remaining 11:30 RBU 100.0%
 943063040/4700372992 (20.1%) @4.0x, remaining 11:25 RBU 100.0%
 962134016/4700372992 (20.5%) @4.0x, remaining 11:19 RBU 100.0%
 981237760/4700372992 (20.9%) @4.0x, remaining 11:18 RBU 100.0%
1000308736/4700372992 (21.3%) @4.0x, remaining 11:13 RBU 100.0%
1019412480/4700372992 (21.7%) @4.0x, remaining 11:08 RBU 100.0%
1038483456/4700372992 (22.1%) @4.0x, remaining 11:06 RBU 100.0%
1057554432/4700372992 (22.5%) @4.0x, remaining 11:01 RBU 100.0%
1076625408/4700372992 (22.9%) @4.0x, remaining 10:56 RBU 100.0%
1095696384/4700372992 (23.3%) @4.0x, remaining 10:54 RBU 100.0%
1114767360/4700372992 (23.7%) @4.0x, remaining 10:49 RBU 100.0%
1133838336/4700372992 (24.1%) @4.0x, remaining 10:44 RBU 100.0%
1152909312/4700372992 (24.5%) @4.0x, remaining 10:43 RBU 100.0%
1171980288/4700372992 (24.9%) @4.0x, remaining 10:38 RBU 100.0%
1191051264/4700372992 (25.3%) @4.0x, remaining 10:33 RBU 100.0%
1210122240/4700372992 (25.7%) @4.0x, remaining 10:31 RBU 100.0%
1229225984/4700372992 (26.2%) @4.0x, remaining 10:26 RBU 100.0%
1248296960/4700372992 (26.6%) @4.0x, remaining 10:24 RBU 100.0%
1267367936/4700372992 (27.0%) @4.0x, remaining 10:20 RBU 100.0%
1286438912/4700372992 (27.4%) @4.0x, remaining 10:15 RBU 100.0%
1305509888/4700372992 (27.8%) @4.0x, remaining 10:13 RBU 100.0%
1324580864/4700372992 (28.2%) @4.0x, remaining 10:09 RBU 100.0%
1343651840/4700372992 (28.6%) @4.0x, remaining 10:04 RBU 100.0%
1362722816/4700372992 (29.0%) @4.0x, remaining 10:02 RBU 100.0%
1381793792/4700372992 (29.4%) @4.0x, remaining 9:58 RBU 100.0%
1400864768/4700372992 (29.8%) @4.0x, remaining 9:53 RBU 100.0%
1419968512/4700372992 (30.2%) @4.0x, remaining 9:51 RBU 100.0%
1439039488/4700372992 (30.6%) @4.0x, remaining 9:46 RBU 100.0%
1458110464/4700372992 (31.0%) @4.0x, remaining 9:42 RBU 100.0%
1477181440/4700372992 (31.4%) @4.0x, remaining 9:40 RBU 100.0%
1496252416/4700372992 (31.8%) @4.0x, remaining 9:36 RBU 100.0%
1515356160/4700372992 (32.2%) @4.0x, remaining 9:31 RBU 100.0%
1534427136/4700372992 (32.6%) @4.0x, remaining 9:29 RBU 100.0%
1553498112/4700372992 (33.1%) @4.0x, remaining 9:25 RBU 100.0%
1572569088/4700372992 (33.5%) @4.0x, remaining 9:20 RBU 100.0%
1591640064/4700372992 (33.9%) @4.0x, remaining 9:18 RBU 100.0%
1610711040/4700372992 (34.3%) @4.2x, remaining 9:14 RBU 100.0%
1629814784/4700372992 (34.7%) @4.0x, remaining 9:10 RBU 100.0%
1648885760/4700372992 (35.1%) @4.0x, remaining 9:05 RBU 100.0%
1667923968/4700372992 (35.5%) @4.0x, remaining 9:03 RBU 100.0%
1687027712/4700372992 (35.9%) @4.0x, remaining 8:59 RBU 100.0%
1706098688/4700372992 (36.3%) @4.0x, remaining 8:55 RBU 100.0%
1725169664/4700372992 (36.7%) @4.0x, remaining 8:52 RBU 100.0%
1744240640/4700372992 (37.1%) @4.0x, remaining 8:48 RBU 100.0%
1763311616/4700372992 (37.5%) @4.0x, remaining 8:44 RBU 100.0%
1782382592/4700372992 (37.9%) @4.0x, remaining 8:42 RBU 100.0%
1801486336/4700372992 (38.3%) @4.0x, remaining 8:38 RBU 100.0%
1820557312/4700372992 (38.7%) @4.0x, remaining 8:34 RBU 100.0%
1839628288/4700372992 (39.1%) @4.0x, remaining 8:31 RBU 100.0%
1858699264/4700372992 (39.5%) @4.0x, remaining 8:27 RBU 100.0%
1877770240/4700372992 (39.9%) @4.0x, remaining 8:23 RBU 100.0%
1896841216/4700372992 (40.4%) @4.0x, remaining 8:21 RBU 100.0%
1915912192/4700372992 (40.8%) @4.0x, remaining 8:17 RBU 100.0%
1934983168/4700372992 (41.2%) @4.0x, remaining 8:13 RBU 100.0%
1954054144/4700372992 (41.6%) @4.0x, remaining 8:10 RBU 100.0%
1973125120/4700372992 (42.0%) @4.0x, remaining 8:06 RBU 100.0%
1992196096/4700372992 (42.4%) @4.0x, remaining 8:02 RBU 100.0%
2011299840/4700372992 (42.8%) @4.0x, remaining 7:59 RBU 100.0%
2030370816/4700372992 (43.2%) @4.0x, remaining 7:56 RBU 100.0%
2049441792/4700372992 (43.6%) @4.0x, remaining 7:52 RBU 100.0%
2068545536/4700372992 (44.0%) @4.0x, remaining 7:49 RBU 100.0%
2087616512/4700372992 (44.4%) @4.0x, remaining 7:45 RBU 100.0%
2106687488/4700372992 (44.8%) @4.0x, remaining 7:41 RBU 100.0%
2125758464/4700372992 (45.2%) @4.0x, remaining 7:39 RBU 100.0%
2144829440/4700372992 (45.6%) @4.0x, remaining 7:35 RBU 100.0%
2163900416/4700372992 (46.0%) @4.0x, remaining 7:32 RBU 100.0%
2182971392/4700372992 (46.4%) @4.0x, remaining 7:28 RBU 100.0%
2202042368/4700372992 (46.8%) @4.0x, remaining 7:24 RBU 100.0%
2221146112/4700372992 (47.3%) @4.0x, remaining 7:22 RBU 100.0%
2240184320/4700372992 (47.7%) @4.0x, remaining 7:18 RBU 100.0%
2259255296/4700372992 (48.1%) @4.0x, remaining 7:14 RBU 100.0%
2278359040/4700372992 (48.5%) @4.0x, remaining 7:11 RBU 100.0%
2297462784/4700372992 (48.9%) @4.0x, remaining 7:07 RBU 100.0%
2316566528/4700372992 (49.3%) @4.0x, remaining 7:03 RBU 100.0%
2335637504/4700372992 (49.7%) @4.0x, remaining 7:01 RBU 100.0%
2354708480/4700372992 (50.1%) @4.0x, remaining 6:57 RBU 100.0%
2373779456/4700372992 (50.5%) @4.0x, remaining 6:53 RBU 100.0%
2392850432/4700372992 (50.9%) @4.0x, remaining 6:50 RBU 100.0%
2411921408/4700372992 (51.3%) @4.0x, remaining 6:47 RBU 100.0%
2430992384/4700372992 (51.7%) @4.0x, remaining 6:43 RBU 100.0%
2450063360/4700372992 (52.1%) @4.0x, remaining 6:40 RBU 100.0%
2469167104/4700372992 (52.5%) @4.0x, remaining 6:36 RBU 100.0%
2488270848/4700372992 (52.9%) @4.0x, remaining 6:32 RBU 100.0%
2507309056/4700372992 (53.3%) @3.8x, remaining 6:30 RBU 100.0%
2526412800/4700372992 (53.7%) @4.0x, remaining 6:26 RBU 100.0%
2545483776/4700372992 (54.2%) @4.0x, remaining 6:22 RBU 100.0%
2564554752/4700372992 (54.6%) @4.0x, remaining 6:19 RBU 100.0%
2583625728/4700372992 (55.0%) @4.0x, remaining 6:16 RBU 100.0%
2602696704/4700372992 (55.4%) @4.0x, remaining 6:12 RBU 100.0%
2621800448/4700372992 (55.8%) @4.0x, remaining 6:09 RBU 100.0%
2640838656/4700372992 (56.2%) @4.0x, remaining 6:05 RBU 100.0%
2659909632/4700372992 (56.6%) @4.0x, remaining 6:02 RBU 100.0%
2678980608/4700372992 (57.0%) @4.0x, remaining 5:59 RBU 100.0%
2698084352/4700372992 (57.4%) @4.0x, remaining 5:55 RBU 100.0%
2717155328/4700372992 (57.8%) @4.0x, remaining 5:51 RBU 100.0%
2736226304/4700372992 (58.2%) @4.0x, remaining 5:48 RBU 100.0%
2755297280/4700372992 (58.6%) @4.0x, remaining 5:45 RBU 100.0%
2774368256/4700372992 (59.0%) @4.0x, remaining 5:41 RBU 100.0%
2793439232/4700372992 (59.4%) @4.0x, remaining 5:38 RBU 100.0%
2812510208/4700372992 (59.8%) @4.0x, remaining 5:34 RBU 100.0%
2831581184/4700372992 (60.2%) @4.0x, remaining 5:31 RBU 100.0%
2850684928/4700372992 (60.6%) @4.0x, remaining 5:28 RBU 100.0%
2869755904/4700372992 (61.1%) @4.0x, remaining 5:24 RBU 100.0%
2888826880/4700372992 (61.5%) @4.0x, remaining 5:21 RBU 100.0%
2907897856/4700372992 (61.9%) @4.0x, remaining 5:18 RBU 100.0%
2926968832/4700372992 (62.3%) @4.0x, remaining 5:14 RBU 100.0%
2946039808/4700372992 (62.7%) @4.0x, remaining 5:11 RBU 100.0%
2965110784/4700372992 (63.1%) @4.0x, remaining 5:07 RBU 100.0%
2984181760/4700372992 (63.5%) @4.0x, remaining 5:04 RBU 100.0%
3003252736/4700372992 (63.9%) @4.0x, remaining 5:01 RBU 100.0%
3022356480/4700372992 (64.3%) @4.0x, remaining 4:57 RBU 100.0%
3041427456/4700372992 (64.7%) @4.0x, remaining 4:53 RBU 100.0%
3060498432/4700372992 (65.1%) @4.0x, remaining 4:50 RBU 100.0%
3079569408/4700372992 (65.5%) @4.0x, remaining 4:47 RBU 100.0%
3098640384/4700372992 (65.9%) @4.0x, remaining 4:43 RBU 100.0%
3117711360/4700372992 (66.3%) @4.0x, remaining 4:40 RBU 100.0%
3136782336/4700372992 (66.7%) @4.0x, remaining 4:37 RBU 100.0%
3155853312/4700372992 (67.1%) @4.0x, remaining 4:33 RBU 100.0%
3174957056/4700372992 (67.5%) @4.0x, remaining 4:30 RBU 100.0%
3194028032/4700372992 (68.0%) @4.0x, remaining 4:26 RBU 100.0%
3213099008/4700372992 (68.4%) @4.0x, remaining 4:23 RBU 100.0%
3232169984/4700372992 (68.8%) @4.0x, remaining 4:20 RBU 100.0%
3251240960/4700372992 (69.2%) @4.0x, remaining 4:16 RBU 100.0%
3270311936/4700372992 (69.6%) @4.0x, remaining 4:13 RBU 100.0%
3289382912/4700372992 (70.0%) @4.0x, remaining 4:10 RBU 100.0%
3308453888/4700372992 (70.4%) @4.0x, remaining 4:06 RBU 100.0%
3327524864/4700372992 (70.8%) @4.0x, remaining 4:03 RBU 100.0%
3346595840/4700372992 (71.2%) @4.0x, remaining 3:59 RBU 100.0%
3365666816/4700372992 (71.6%) @4.0x, remaining 3:56 RBU 100.0%
3384770560/4700372992 (72.0%) @4.0x, remaining 3:52 RBU 100.0%
3403841536/4700372992 (72.4%) @4.0x, remaining 3:49 RBU 100.0%
3422912512/4700372992 (72.8%) @4.0x, remaining 3:46 RBU 100.0%
3441983488/4700372992 (73.2%) @4.0x, remaining 3:42 RBU 100.0%
3461054464/4700372992 (73.6%) @4.0x, remaining 3:39 RBU 100.0%
3480125440/4700372992 (74.0%) @4.0x, remaining 3:35 RBU 100.0%
3499196416/4700372992 (74.4%) @4.0x, remaining 3:32 RBU 100.0%
3518267392/4700372992 (74.9%) @4.0x, remaining 3:29 RBU 100.0%
3537338368/4700372992 (75.3%) @4.0x, remaining 3:25 RBU 100.0%
3556442112/4700372992 (75.7%) @4.0x, remaining 3:22 RBU 100.0%
3575513088/4700372992 (76.1%) @4.0x, remaining 3:19 RBU 100.0%
3594584064/4700372992 (76.5%) @4.0x, remaining 3:15 RBU 100.0%
3613655040/4700372992 (76.9%) @4.0x, remaining 3:12 RBU 100.0%
3632726016/4700372992 (77.3%) @4.0x, remaining 3:08 RBU 100.0%
3651796992/4700372992 (77.7%) @4.0x, remaining 3:05 RBU 100.0%
3670867968/4700372992 (78.1%) @4.0x, remaining 3:02 RBU 100.0%
3689938944/4700372992 (78.5%) @4.0x, remaining 2:58 RBU 100.0%
3709009920/4700372992 (78.9%) @4.0x, remaining 2:55 RBU 100.0%
3728080896/4700372992 (79.3%) @4.0x, remaining 2:51 RBU 100.0%
3747151872/4700372992 (79.7%) @4.0x, remaining 2:48 RBU 100.0%
3766222848/4700372992 (80.1%) @4.0x, remaining 2:45 RBU 100.0%
3785293824/4700372992 (80.5%) @4.0x, remaining 2:41 RBU 100.0%
3804364800/4700372992 (80.9%) @4.0x, remaining 2:38 RBU 100.0%
3823468544/4700372992 (81.3%) @4.0x, remaining 2:35 RBU 100.0%
3842539520/4700372992 (81.7%) @4.0x, remaining 2:31 RBU 100.0%
3861610496/4700372992 (82.2%) @4.0x, remaining 2:28 RBU 100.0%
3880681472/4700372992 (82.6%) @4.0x, remaining 2:24 RBU 100.0%
3899752448/4700372992 (83.0%) @4.0x, remaining 2:21 RBU 100.0%
3918823424/4700372992 (83.4%) @4.0x, remaining 2:18 RBU 100.0%
3937894400/4700372992 (83.8%) @4.0x, remaining 2:14 RBU 100.0%
3956998144/4700372992 (84.2%) @4.0x, remaining 2:11 RBU 100.0%
3976069120/4700372992 (84.6%) @4.0x, remaining 2:08 RBU 100.0%
3995140096/4700372992 (85.0%) @4.0x, remaining 2:04 RBU 100.0%
4014211072/4700372992 (85.4%) @4.0x, remaining 2:01 RBU 100.0%
4033282048/4700372992 (85.8%) @4.0x, remaining 1:57 RBU 100.0%
4052353024/4700372992 (86.2%) @4.0x, remaining 1:54 RBU 100.0%
4071424000/4700372992 (86.6%) @4.0x, remaining 1:51 RBU 100.0%
4090494976/4700372992 (87.0%) @4.0x, remaining 1:47 RBU 100.0%
4109598720/4700372992 (87.4%) @4.0x, remaining 1:44 RBU 100.0%
4128669696/4700372992 (87.8%) @4.0x, remaining 1:40 RBU 100.0%
4147707904/4700372992 (88.2%) @4.0x, remaining 1:37 RBU 100.0%
4166811648/4700372992 (88.6%) @4.0x, remaining 1:34 RBU 100.0%
4185882624/4700372992 (89.1%) @4.0x, remaining 1:30 RBU 100.0%
4204953600/4700372992 (89.5%) @4.0x, remaining 1:27 RBU 100.0%
4224024576/4700372992 (89.9%) @4.0x, remaining 1:24 RBU 100.0%
4243095552/4700372992 (90.3%) @4.0x, remaining 1:20 RBU 100.0%
4262166528/4700372992 (90.7%) @4.0x, remaining 1:17 RBU 100.0%
4281270272/4700372992 (91.1%) @4.0x, remaining 1:14 RBU 100.0%
4300341248/4700372992 (91.5%) @4.0x, remaining 1:10 RBU 100.0%
4319412224/4700372992 (91.9%) @4.0x, remaining 1:07 RBU 100.0%
4338483200/4700372992 (92.3%) @4.0x, remaining 1:03 RBU 100.0%
4357554176/4700372992 (92.7%) @4.0x, remaining 1:00 RBU 100.0%
4376625152/4700372992 (93.1%) @4.0x, remaining 0:57 RBU 100.0%
4395696128/4700372992 (93.5%) @4.0x, remaining 0:53 RBU 100.0%
4414767104/4700372992 (93.9%) @4.0x, remaining 0:50 RBU 100.0%
4433838080/4700372992 (94.3%) @4.0x, remaining 0:47 RBU 100.0%
4452909056/4700372992 (94.7%) @4.0x, remaining 0:43 RBU 100.0%
4472012800/4700372992 (95.1%) @4.0x, remaining 0:40 RBU 100.0%
4491083776/4700372992 (95.5%) @4.0x, remaining 0:36 RBU 100.0%
4510154752/4700372992 (96.0%) @4.0x, remaining 0:33 RBU 100.0%
4529225728/4700372992 (96.4%) @4.0x, remaining 0:30 RBU 100.0%
4548296704/4700372992 (96.8%) @4.0x, remaining 0:26 RBU 100.0%
4568219648/4700372992 (97.2%) @4.2x, remaining 0:23 RBU 100.0%
4592992256/4700372992 (97.7%) @5.2x, remaining 0:18 RBU 100.0%
4617764864/4700372992 (98.2%) @5.2x, remaining 0:14 RBU 100.0%
4642504704/4700372992 (98.8%) @5.2x, remaining 0:10 RBU 100.0%
4667277312/4700372992 (99.3%) @5.2x, remaining 0:05 RBU 100.0%
4692049920/4700372992 (99.8%) @5.2x, remaining 0:01 RBU 100.0%
:-[ WRITE@LBA=230540h failed with SK=5h/ASC=21h/ACQ=00h]: No space left on device
:-( write failed: No space left on device
/dev/hdb: flushing cache
/dev/hdb: stopping de-icing
/dev/hdb: writing lead-out
ubuntu@ubuntu:~$ 

```

---

### Post by pseudonym on 2007-04-23
Although it sounds like there was a problem, your disk should be OK. Have a look at [this]("http://lists.debian.org/cdwrite/2003/12/msg00067.html") for an explanation, from the author of growisofs himself (just ignore the part about firmware).

Also, in your PM to me you wrote - ```
I think when I originally formatted them the filesystem did not get created correctly
``` Unless I'm misinterpreting you here, I should point out that 'formatting' a DVD+RW doesn't mean creating a filesystem on it (like you do with a floppy disk or USB stick). It's just the name given to the brief initialisation process which *enables* a filesystem to be created on the disk. That filesystem gets created in the course of burning your data/video/image/whatever. You do not need to create one beforehand.

HTH

---

### Post by mips on 2007-04-23
Send the ones you ruined to me :)

---

### Post by billdotson on 2007-04-23
so does doing this low level format fix my media?  I was under the impression RW media was much harder to screw up.. guess I am wrong

---

### Post by pseudonym on 2007-04-23
> **billdotson said:**
> so does doing this low level format fix my media?  I was under the impression RW media was much harder to screw up.. guess I am wrong
That depends on what you did with them previously. If it was just a failed burn due to say, a bug in your burning app, your disks should probably be OK. As I mentioned in my first post, with +RW media you just overwrite them. Low-level formatting, or 'zero filling', the disk won't 'repair' it in this situation. But it doesn't hurt either if you're concerned about it.

On the other hand, if the disk has sustained physical damage due to a faulty burner, or you were blanking an +RW in a way you're not supposed to (see above), then it's almost certainly a coaster.

---

