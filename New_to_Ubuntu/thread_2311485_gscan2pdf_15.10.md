---
title: "gscan2pdf 15.10"
date: 2016-01-27
forum: New to Ubuntu
---

### Post by mahjsa on 2016-01-27
As I have read in various fora, gscan2pdf -or better sane and it's libs - can give some problems with scanning over Wifi. I ran into this problem with the update to 15.04 which I solved by first uninstalling all sane software and then reinstall some older version (I believe 1.024).
A short while ago I ran into the same problem after an update in 15.10 (to 4.0.25 kernel). My Pixma 560 scanner stopped working.
After an extensive search on the internet I found a possible solution stating that installing a newer (experimental) version of libsane and dependent libraries could help.
So again I removed all sane libraries (with the exclusion of the scanner specific software) and replaced them with the experimental 1.0.26 versions. That solved my problem, but still I think it is strange that a kernel update broke the sane libraries or something.
At least I have now again a working scanner over Wifi.

---

