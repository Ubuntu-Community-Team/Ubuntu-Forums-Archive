---
title: "System crashes: maybe associated with &quot;APIC Error&quot;?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by stueau on 2008-06-17
I keep getting unprompted system restarts which are getting slightly annoying. It seems that it may be associated with watching embedded flash videos, though I'm definitely not sure.

I've checked the system log and an entry that appears to correlate to the crash is an "APIC error"..
```

Jun 16 23:18:59 scott-laptop kernel: [ 8579.318888] APIC error on CPU1: 40(40)
Jun 16 23:18:59 scott-laptop kernel: [ 8579.340447] APIC error on CPU0: 40(40)
Jun 16 23:24:20 scott-laptop kernel: [ 8899.550345] APIC error on CPU1: 40(40)
Jun 16 23:24:20 scott-laptop kernel: [ 8899.572665] APIC error on CPU0: 40(40)
Jun 16 23:41:40 scott-laptop kernel: [ 9939.329985] APIC error on CPU0: 40(40)
Jun 16 23:41:40 scott-laptop kernel: [ 9939.305594] APIC error on CPU1: 40(40)
Jun 16 23:44:52 scott-laptop kernel: [10130.955793] APIC error on CPU1: 40(40)
Jun 16 23:44:52 scott-laptop kernel: [10130.980700] APIC error on CPU0: 40(40)

```

As you may guess from the above I'm running a AMD 64-bit system, and also Hardy 8.04

Any suggestions would be really appreciated!

---

### Post by kpkeerthi on 2008-06-17
You may want to [turn off APIC]("http://ubuntuforums.org/showpost.php?p=4385355&postcount=4").

---

### Post by stueau on 2008-06-17
thanks... I've done that. I'll just have to see if I still get crashes..

---

