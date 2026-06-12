---
title: "Accidently removing files with sudo apt-get remove"
date: 2012-04-26
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-04-26
HI there

I accidentally deleted some important files using sudo apt-get remove. Is there a log file that records the removal, so I can re-download the files I so carelessly removed?

Glenn.

---

### Post by sandyd on 2012-04-26
> **Senior_Buckethead said:**
> HI there

I accidentally deleted some important files using sudo apt-get remove. Is there a log file that records the removal, so I can re-download the files I so carelessly removed?

Glenn.
```

gedit /var/log/dpkg.log
```

---

