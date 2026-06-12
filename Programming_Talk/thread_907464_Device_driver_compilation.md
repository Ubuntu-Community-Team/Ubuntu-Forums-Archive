---
title: "Device driver compilation"
date: 2008-09-01
forum: Programming Talk
---

### Post by rajez79 on 2008-09-01
Am getting the follwing error while compiling a device driver program

rajesh@rajesh-desktop:~/Desktop$ gcc dd.c
dd.c:1:24: error: linux/init.h: No such file or directory
dd.c:2:26: error: linux/module.h: No such file or directory

Please help me in solving this....

---

### Post by Skorzen on 2008-09-01
What's to be solved?
It seems like those headers are not available in your system.
You can possibly fix them, installing kernel source package.

---

### Post by Bachstelze on 2008-09-01
```
sudo apt-get install linux-headers-`uname -r`
```

---

