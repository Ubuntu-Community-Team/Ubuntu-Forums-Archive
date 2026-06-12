---
title: "Strange error"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by skinnerc on 2008-11-28
Nov 28 17:30:50 william-laptop kernel: [ 2553.424177] ide: failed opcode was: unknown
Nov 28 17:30:50 william-laptop kernel: [ 2553.424182] end_request: I/O error, dev hda, sector 4826879
Nov 28 17:30:55 william-laptop kernel: [ 2558.546767] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Nov 28 17:30:55 william-laptop kernel: [ 2558.546777] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=4826915, sector=4826887

Not sure what this means.  But I haven't been able to get Open Office to start and this is the only error I have found.

---

### Post by LowSky on 2008-11-28
open a terminal and try starting Open Office that way

here the command

```
ooffice -writer
```

---

### Post by skinnerc on 2008-11-28
> **LowSky said:**
> open a terminal and try starting Open Office that way

here the command

```
ooffice -writer
```

When I did this, nothing happened.  The terminal stopped responding. The computer lagged to almost a stop.  The only thing I could do was turn the computer off.  I did let it run for about 10 minutes before I turned it off.

---

