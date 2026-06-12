---
title: "Gdebi in 11.10 not downloading additional files"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by rojaasensei on 2011-10-24
After upgrading to 11.10 (using Xubuntu), and installing Gdebi, I cannot install a deb package that requires the downloading of additional files.

The installer opens, but just hangs when it tries to download the files.  I tried the fixes in the post [http://ubuntuforums.org/showthread.php?t=1863211&highlight=gdebi](http://ubuntuforums.org/showthread.php?t=1863211&highlight=gdebi) but it has not corrected the issue.

Any suggestions

---

### Post by TeoBigusGeekus on 2011-10-24
Try from command line with
```
sudo dpkg -i /path/name.deb
```

---

