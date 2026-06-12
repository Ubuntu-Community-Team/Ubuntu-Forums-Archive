---
title: "HOWTO: Run Maple 8"
date: 2005-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by Tobi Vollebregt on 2005-06-17
To install maple 8 you follow the instructions on the CD. If this fails with a lot of errors, the filename case on the CD might be wrong. If this happens, copy the entire install folder to your HD and make sure the filenames' case matches to the ones in the attached file maple.gz.

If the installation succeeded and you try to run maple or xmaple, you'll get this error:
```
maple/root/maple8/bin.IBM_INTEL_LINUX/mserver: relocation error: /root/maple8/bin.IBM_INTEL_LINUX/libmaple.so: symbol errno, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```

To solve this, create a script to run maple, containing the following lines:
```
#!/bin/sh
export LD_ASSUME_KERNEL=2.4.1
/root/maple8/bin/xmaple
```
Replace /root/maple8/ with the directory you installed it in. Replace xmaple with maple to run the non-graphical version of maple.

Note: google helped me out on this one, the official maple FAQ mentionned this solution for Red Hat 9 users.

---

