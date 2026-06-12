---
title: "error while loading shared  libraries: libopencv_core.so.2.4: cannot open shared obje"
date: 2013-01-29
forum: Packaging and Compiling Programs
---

### Post by oujeboland on 2013-01-29
```
 libraries: libopencv_core.so.2.4: cannot open shared object file: No such file or directory
```hi , i want to run my first opencv application but it gives me the error above!
i added the lib folder to local directory variable but the error still exists. 
thx

---

### Post by oujeboland on 2013-01-30
i added a file in : /etc/ld.config.so.d/
and named it : opencv.conf
and i also added the path of libopencv_core.so.2.4 file in that file (without "libopencv_core.so.2.4"). 
i ran :
sudo ldconfig -v
and problem resolved .

directions:
stackoverflow.com/questions/12335848/opencv-program-compile-error-libopencv-core-so-2-4-cannot-open-shared-object-f

---

