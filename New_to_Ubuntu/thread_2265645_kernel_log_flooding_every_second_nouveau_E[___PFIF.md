---
title: "kernel log flooding every second nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by glev on 2015-02-16
Hello
Viewing my log file I see a new entry every second:
```

Feb 16 23:19:43 my-OB kernel: [  425.624947] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:46 my-OB kernel: [  428.407216] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:46 my-OB kernel: [  428.407221] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:47 my-OB kernel: [  429.456761] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:47 my-OB kernel: [  429.456766] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:48 my-OB kernel: [  430.523600] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:48 my-OB kernel: [  430.523608] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:48 my-OB kernel: [  430.823604] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:48 my-OB kernel: [  430.823609] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:50 my-OB kernel: [  432.255650] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:50 my-OB kernel: [  432.255655] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:50 my-OB kernel: [  432.555504] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:50 my-OB kernel: [  432.555510] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:52 my-OB kernel: [  434.289185] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:52 my-OB kernel: [  434.289190] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:53 my-OB kernel: [  435.337768] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:53 my-OB kernel: [  435.337772] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:53 my-OB kernel: [  435.354401] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:53 my-OB kernel: [  435.354408] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:54 my-OB kernel: [  436.403978] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:54 my-OB kernel: [  436.403986] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:55 my-OB kernel: [  437.403614] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:55 my-OB kernel: [  437.403620] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:56 my-OB kernel: [  438.469846] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:56 my-OB kernel: [  438.469855] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:56 my-OB kernel: [  438.487064] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:56 my-OB kernel: [  438.487075] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:57 my-OB kernel: [  439.519447] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:57 my-OB kernel: [  439.519452] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:19:58 my-OB kernel: [  440.535678] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:19:58 my-OB kernel: [  440.535683] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:20:00 my-OB kernel: [  442.584879] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:20:00 my-OB kernel: [  442.584885] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:20:05 my-OB kernel: [  447.183079] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:20:05 my-OB kernel: [  447.183084] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:20:05 my-OB kernel: [  447.199737] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:20:05 my-OB kernel: [  447.199741] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:20:05 my-OB kernel: [  447.217199] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:20:05 my-OB kernel: [  447.217210] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:20:05 my-OB kernel: [  447.250431] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:20:05 my-OB kernel: [  447.250441] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:20:05 my-OB kernel: [  447.283745] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:20:05 my-OB kernel: [  447.283752] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:20:05 my-OB kernel: [  447.300031] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ
Feb 16 23:20:05 my-OB kernel: [  447.300037] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: ch 1 [DRM] subc 5 mthd 0x0500 data 0x00000000
Feb 16 23:20:06 my-OB kernel: [  448.232662] nouveau E[   PFIFO][0000:01:00.0] PBDMA0: LBREQ

```

any idea what this is?
thank you for you help.

---

### Post by glev on 2015-02-17
Seems to be a [nouveau]("http://nouveau.freedesktop.org/wiki/") graphic driver bug.
I've installed the Nvidia drivers and all is ok now.
further reading: [BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") 

thanks :)

---

