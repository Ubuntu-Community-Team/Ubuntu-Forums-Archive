---
title: "How to get string so as to link libraries with dpkg?"
date: 2011-06-03
forum: Programming Talk
---

### Post by hakermania on 2011-06-03
I stuck! i think it starts with dpkg but not sure....
I've seen it several times, it is a command like
```
dpkglibs opencv
```and outputs
```
-L/usr/local/lib -lml -lcvaux -lhighgui -lcv -lcxcore
```
but i cannot remember the command! Any help?

---

### Post by hakermania on 2011-06-03
found it!!!
```
pkg-config --libs opencv
```

---

