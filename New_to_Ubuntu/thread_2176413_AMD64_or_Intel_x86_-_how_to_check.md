---
title: "AMD64 or Intel x86 - how to check?"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by lakeshore2985 on 2013-09-24
Might sound silly but I am not sure which .iso version I've downloaded and installed on my AMD64-based system.

Question is, how do I check which version of Lubuntu is installed on my computer? And would the Intel x86 version even install on an AMD computer? If so, what would be the differences? I'm guessing it would have something to do with code optimization for each platform?

Thanks.

---

### Post by howefield on 2013-09-24
Open a terminal and type..

```
uname -a
```

If you have x86_64 in the output, you have a 64 bit installation.

Or System Settings > Details > Overview.

---

### Post by Impavidus on 2013-09-24
The names Intel and AMD are used for historical reasons. AMD64 just means 64 bit, Intel x86 means 32 bit. The both are compatible with both Intel and AMD processors. The only thing is that the AMD64 version doesn't install on any (neither Intel nor AMD) 32 bit system, and that the AMD64 version gives better performance on any (both AMD and Intel) 64 bit system.

---

### Post by lakeshore2985 on 2013-09-24
Ah, thanks for the clarification.

EDIT: was going to ask just that! :)

---

