---
title: "skype webcam in 10.04 not working"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by alex j on 2012-01-01
In Ubuntu 10.04 we have not gotten a webcam to work for Skype, although they worked in Cheese. We think everything else in skype works.  Any help would be appreciated.  Thanks.

---

### Post by TeoBigusGeekus on 2012-01-01
Try launching skype from terminal with
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

---

### Post by alex j on 2012-01-04
Thanks but did not work.  :(

---

### Post by alex j on 2012-01-04
Sorry, it works in the "Options"  "Video devices" "test," screen.
I will wait for my girlfriend to test it some more.  Thanks.

---

