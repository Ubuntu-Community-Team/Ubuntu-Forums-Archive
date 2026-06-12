---
title: "Application Start Time"
date: 2010-10-16
forum: Programming Talk
---

### Post by rampageoberon on 2010-10-16
Hi,

I'm trying to extract start time of various applications and having no issues with the code on Ubuntu.

However for Debian for some reason I don't get the correct time. It keeps resetting itself i.e. i'm unable to determine when the application instance started.

The code is below. Please help with this. Thanks

```
date -d @$(stat -c %X /proc/$(pidof <pid>))
```

---

### Post by cariboo on 2010-10-16
You may get better help here.

---

