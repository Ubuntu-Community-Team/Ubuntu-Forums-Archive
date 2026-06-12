---
title: "Tecplot360 installation"
date: 2016-08-20
forum: New to Ubuntu
---

### Post by lakku2 on 2016-08-20
when i am running tecplot i am getting this error
/usr/local/tecplot/bin/tecplot.shared: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

### Post by mook765 on 2016-08-20
Try this:
```
sudo apt-get install libstdc++5
```
and see if the problem is solved...
On the other side:
Tecplot is a commercial software and they do have a support-team at
[http://www.tecplot.com/](http://www.tecplot.com/)
Kind regards...

---

