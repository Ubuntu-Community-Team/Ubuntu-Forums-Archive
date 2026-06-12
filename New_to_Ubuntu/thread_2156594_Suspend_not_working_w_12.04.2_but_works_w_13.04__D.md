---
title: "Suspend not working w/ 12.04.2 but works w/ 13.04 _Dual Boot_amd64 Laptop"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by Rekhillbill on 2013-06-22
Flashing white screen, after lifting lid running 12.04.2 but password screen appears, after lifting lid running 13.04.

Please explain why suspend works with one OS and not the other?

Any suggestion for getting suspend to work with 12.04.2?

Thanks

---

### Post by José Serra on 2013-06-22
Ubuntu 12.04.2 has an older kernel version, may be you could consider to use a newer kernel version.
[http://askubuntu.com/questions/258798/installing-kernel-3-8-on-12-10-12-04](http://askubuntu.com/questions/258798/installing-kernel-3-8-on-12-10-12-04)

Regards.

---

### Post by Rekhillbill on 2013-06-30
Jose, Thanks for the suggestion.  But, Iam not ready to change Kernels, since 12.04.2 works OK in every respect but the "suspend" / "resume" feature.

I have found the suspend is "time" dependent, i.e., if I suspend [without requiring a password to resume] then I can "resume" OK within a few minutes.

But, leaving the Toshiba in the suspended state for awhile  [undetermined time, since I have not tried to find out how long] results in the resume not working.

The display alternates, flashes, between black and white.  At this point, the only option is the on/off button to shutdown.

But, since every other 12.04.2 feature works OK, I am going to simply not worry about the issue.  I'll just wait for a kernal update.

Best,
Bill


A quick update:

I updated 12.04 the other day via the normal Update Manager, at the UM's request, and found the following kernal present:

bill@bill-Satellite-L500D:~$ uname -a
Linux bill-Satellite-L500D 3.5.0-34-generic #55~precise1-Ubuntu SMP Fri Jun 7 16:25:50 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
bill@bill-Satellite-L500D:~$

My suspend feature is now working correctly with or without requiring a password.  Also, it works by closing the lid or with clicking "suspend" in the OS.

Of course I am very happy about this, but don't have a clue as to why it's working now?

Best,
Bill

---

