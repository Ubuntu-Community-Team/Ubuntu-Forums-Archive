---
title: "USB Memory Card Reader issues"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by Sarteck on 2008-09-19
I have a problem.  There is a 13-in-1 memory card reader that came installed on my computer.  It seemed to be working normally until recently.

Now, I can put a card into the reader and the computer will recognize it and auto-mount it just fine.  But only once.  And I cannot plug it in again and have the computer recognize it until I reboot the computer.

When plugging it in, this is the last few lines of dmesg:```
[33128.411951] sd 4:0:0:2: [sdd] 63424 512-byte hardware sectors (32 MB)
[33128.420070] sd 4:0:0:2: [sdd] Write Protect is off
[33128.420072] sd 4:0:0:2: [sdd] Mode Sense: 87 00 00 00
[33128.420074] sd 4:0:0:2: [sdd] Assuming drive cache: write through
[33128.429131] sd 4:0:0:2: [sdd] 63424 512-byte hardware sectors (32 MB)
[33128.437215] sd 4:0:0:2: [sdd] Write Protect is off
[33128.437217] sd 4:0:0:2: [sdd] Mode Sense: 87 00 00 00
[33128.437218] sd 4:0:0:2: [sdd] Assuming drive cache: write through
[33128.437222]  sdd:end_request: I/O error, dev sdd, sector 0
[33128.446318] Buffer I/O error on device sdd, logical block 0
[33128.456134] end_request: I/O error, dev sdd, sector 0
[33128.456137] Buffer I/O error on device sdd, logical block 0
[33128.465685] end_request: I/O error, dev sdd, sector 0
[33128.465687] Buffer I/O error on device sdd, logical block 0
[33128.476444] end_request: I/O error, dev sdd, sector 0
[33128.476446] Buffer I/O error on device sdd, logical block 0
[33128.487245] end_request: I/O error, dev sdd, sector 0
[33128.487247] Buffer I/O error on device sdd, logical block 0
[33128.487253] ldm_validate_partition_table(): Disk read failed.
[33128.497070] end_request: I/O error, dev sdd, sector 0
[33128.497074] Buffer I/O error on device sdd, logical block 0
[33128.506619] end_request: I/O error, dev sdd, sector 0
[33128.506621] Buffer I/O error on device sdd, logical block 0
[33128.516304] end_request: I/O error, dev sdd, sector 0
[33128.516306] Buffer I/O error on device sdd, logical block 0
[33128.526125] end_request: I/O error, dev sdd, sector 0
[33128.526128] Buffer I/O error on device sdd, logical block 0
[33128.526133] Dev sdd: unable to read RDB block 0
[33128.535766] end_request: I/O error, dev sdd, sector 0
[33128.535768] Buffer I/O error on device sdd, logical block 0
[33128.546522] end_request: I/O error, dev sdd, sector 0
[33128.556255] end_request: I/O error, dev sdd, sector 24
[33128.565940] end_request: I/O error, dev sdd, sector 24
[33128.575582] end_request: I/O error, dev sdd, sector 0
[33128.585402] end_request: I/O error, dev sdd, sector 0
[33128.585409]  unable to read partition table
[33128.602498] end_request: I/O error, dev sdd, sector 0
[33128.612139] end_request: I/O error, dev sdd, sector 0
```

Anyone have an idea what I need to do to fix this problem?

---

### Post by PocketDog on 2008-09-19
Are you un-mounting the card before you take it out?

---

### Post by Sarteck on 2008-09-19
Nope, I never have had to.  O.o  Before, it allowed me to take it out or shove it in as much as I wanted.  Kind of like my ex.  Never had to worry about unmounting. XD

---

### Post by PocketDog on 2008-09-19
You should, much like 'safely remove device' in Windows. Not doing so can cause problems (which you're having) or corrupted/lost data

---

### Post by Sarteck on 2008-09-19
Didn't think that would be the problem, but I rebooted and tried anyhow.  Still no dice--when trying to put it back in, still nothing.

---

