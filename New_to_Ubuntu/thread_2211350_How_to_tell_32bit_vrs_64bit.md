---
title: "How to tell 32bit vrs 64bit"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by mcsheffrey on 2014-03-15
What's the command to determine if I'm running 32bit or 64 bit ubuntu,  Tks Roy

---

### Post by oldos2er on 2014-03-15
```
uname -a
``` look for x86_64 in the output. 32-bit will show as x86.

---

### Post by deadflowr on 2014-03-15
uname -a will usually show 32-bit as i386,i586,and i686.

Any file or iso that has those in it is 32-bit.

As well, any file that has amd64 is 64-bit.
As far as amd64 goes don't worry about that on intel machines.
It's simply a naming scheme.
Something to do with amd and the advent of 64-bit systems.

Hope that makes some sort of sense.

---

### Post by whitesmith on 2014-03-15
The soft and gui (lazy) way is to click the Tool Gear, then:  System Settings->Details. I would go with the method suggested by the previous two answers because they make you think in Linux. Please click Thread Tools (right above your post) to mark this thread closed if the answers meet your liking. Regards.

---

