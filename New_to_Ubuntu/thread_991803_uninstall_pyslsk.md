---
title: "uninstall pyslsk"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Dosunmu on 2008-11-24
Hello,

how can i uninstall pyslsk? I installed it with python "setup.py install".

thx

---

### Post by Xiong Chiamiov on 2008-11-27
There might be an uninstall option for setup.py, meaning that you could run 
```

python setup.py uninstall

```
If not, then you just need to delete the files that it extracted, as that's all an install does (extract files to places).  You should be able to find out what went where by looking at setup.py in an editor.

---

