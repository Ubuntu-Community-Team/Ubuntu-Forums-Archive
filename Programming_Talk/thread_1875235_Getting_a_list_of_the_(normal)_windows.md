---
title: "Getting a list of the (normal) windows"
date: 2011-11-04
forum: Programming Talk
---

### Post by sakishrist on 2011-11-04
Hello everyone!

I would like to get a list of the currently open windows. The most important is the top one but it would be nice if I could get the captions (and processes) of all of them. Could you please point me in the right direction?

Thanks in advance!

---

### Post by 11jmb on 2011-11-04
```
wmctrl -l
```

---

### Post by crdlb on 2011-11-04
GNOME's libwnck could also be used for this, particularly if you have a long-running process and want to monitor changes.

---

### Post by sakishrist on 2011-11-04
Thanks, I'll give it a try.

---

