---
title: "Repository changed its value.. must be accepted explicitly before upgrades can be"
date: 2023-01-25
forum: New to Ubuntu
---

### Post by chagzuki on 2023-01-25
applied.
This is the first time I've encountered these messages when trying to update and upgrade PPAs. There's "Repository changed its default priority for apt_preferences(5) from 500 to 100." and a bunch of other stuff, origin value, suite value, label value etc..

So I'm reading that the solution is to add the flag --allow-releaseinfo-change, but I'm also reading that there is some inherent security risk in doing this. Since I'm getting these error messages for the first time and for more than one repository simultaneously is it right to assume that some kind of Ubuntu system update has forced repositories to change their structure somewhat? And is there really any security risk in using the --allow-releaseinfo-change flag?

---

### Post by ActionParsnip on 2023-01-26
Can you give the full output of:
```

sudo apt update; lsb_release -a; uname -a

```
Thanks

---

