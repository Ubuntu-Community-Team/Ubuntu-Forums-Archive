---
title: "How easy install Qt5 on Ubuntu 13.04"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by mikhail4 on 2013-09-24
How easy install Qt5 on Ubuntu 13.04? apt-get install ... ?

---

### Post by slickymaster on 2013-09-24
I'd recommend following the steps on [http://developer.ubuntu.com/get-started/](http://developer.ubuntu.com/get-started/)

---

### Post by oldos2er on 2013-09-24
Moved to Absolute Beginners.

---

### Post by Jonathan Precise on 2013-09-24
Try:

```
sudo apt-get install qt5-default qttools5-dev-tools
```

If QT is not installed yet, then ```
sudo apt-get remove qt5-default qttools5-dev-tools && sudo apt-get autoremove && sudo apt-get clean && sudo apt-get autoclean
``` and return errors (if any).

---

