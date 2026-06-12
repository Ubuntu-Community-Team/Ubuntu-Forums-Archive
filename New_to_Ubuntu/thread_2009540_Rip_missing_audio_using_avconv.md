---
title: "Rip missing audio using avconv"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by r3bol on 2012-06-24
I'm trying to convert some digibox content from .ts to avi. The video is ok, but the problem is whatever I try, I can't get any audio on the rip. 

```
avconv -i example.ts -c:v mpeg4 -b 2000k -acodec copy output.avi 
```

Does anyone have any tips on getting audio from .ts?

Thanks.

---

