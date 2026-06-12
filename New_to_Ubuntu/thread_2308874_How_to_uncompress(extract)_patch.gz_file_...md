---
title: "How to uncompress(extract) patch.gz file .."
date: 2016-01-06
forum: New to Ubuntu
---

### Post by latha2 on 2016-01-06
Dear all,
I struck at  decompress a patch.gz file 
which is
patch-4.1.15-rt17.patch.gz 
and also patching command for this just like we do for bz2 
i.e 
bzcat ../patch-x.x.x-rtx.bz2 | patch -p1 Anyone help me out ..
Thank you.

---

### Post by slickymaster on 2016-01-06
You can either ```
gunzip patch-4.1.15-rt17.patch.gz
```or```
gzip -d patch-4.1.15-rt17.patch.gz
```

---

