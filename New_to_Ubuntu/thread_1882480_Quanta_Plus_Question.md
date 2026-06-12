---
title: "Quanta Plus Question"
date: 2011-11-17
forum: New to Ubuntu
---

### Post by nickcollie on 2011-11-17
Does anyone know how to set the default file permissions of an upload in Quanta plus?  

At the moment all files are uploaded as 664 and I would like it to be 644.

Thanks

Nick

---

### Post by maticer on 2011-11-17
U need to set appropriate umask. Look at man page (type in console): ```
man umask
```
or [http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html](http://www.cyberciti.biz/tips/understanding-linux-unix-umask-value-usage.html)

---

