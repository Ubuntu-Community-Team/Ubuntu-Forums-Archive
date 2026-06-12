---
title: "How to upgrade a single package?"
date: 2015-04-18
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-04-18
Hello guys 
I want to know what's the command line to upgrade a single package.
Thank you

---

### Post by slickymaster on 2015-04-18
You just need to:```
sudo apt-get install --only-upgrade <packagename>
```This will upgrade only that single package, and only if it is installed.

---

