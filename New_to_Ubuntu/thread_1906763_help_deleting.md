---
title: "help deleting"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by openation1 on 2012-01-09
hi I need to remove LIBAVCODEC52 AND LIBAVUTIL50 in order to install ubuntu extras. any advice will be greatly appreciated. thank you

---

### Post by Basher101 on 2012-01-09
> **openation1 said:**
> hi I need to remove LIBAVCODEC52 AND LIBAVUTIL50 in order to install ubuntu extras. any advice will be greatly appreciated. thank you

```
sudo apt-get purge LIBAVCODEC52
```
```
sudo apt-get purge LIBAVUTIL50
```

regards

---

### Post by papibe on 2012-01-09
```
sudo apt-get remove libavcodec52
```
As far as libavutil50, it should be the same (although I don't know if it exists or it is a typo).

Hope it helps.
Regards.

---

### Post by /z@ch on 2012-01-09
Wouldn't they be removed automatically when installing the extras?

---

