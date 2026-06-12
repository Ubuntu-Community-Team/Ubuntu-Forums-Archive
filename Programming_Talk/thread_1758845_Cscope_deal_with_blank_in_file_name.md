---
title: "Cscope deal with blank in file name"
date: 2011-05-15
forum: Programming Talk
---

### Post by huangyingw on 2011-05-15
Hello all,
    I have written such shell to wrap cscope for code reading:
     ```
#!/bin/bash
TARGET='/export/home1/username/cscope_db/cscope.files'
find `pwd`/ -type f -name "*.h" -o -name "*.py" -o -name "*.xml" -o -name "*.properties" -o -name "*.jsp" -o -name "*.c" -o -name "*.cc" -o -name "*.cpp" -o -name "*.hpp" -o -name "*.java" -o -name "*.js"> ${TARGET}
cscope -qR -i "${TARGET}"
```
    But the problem for me is that: if there is files whose name contains blank like this one ```
/home/huangyingw/cvs/design/UED/DE Sample Index/3.2/Samples/CPP/SharingData/Client/_notes/dwsync.xml

```, then cscope will treat it as two files, and report files not found error.
    This would cause trouble when reading codes.
    Could anyone do me a favor?

---

