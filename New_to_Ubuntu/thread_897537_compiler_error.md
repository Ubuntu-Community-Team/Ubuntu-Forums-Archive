---
title: "compiler error"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by taith on 2008-08-22
```
 ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```


anyone know what program i'm missing here?

---

### Post by glennric on 2008-08-22
Have you installed the package "build-essential"?  If not install that and try again.  Most likely you don't have a C compiler installed.

---

### Post by linuxguymarshall on 2008-08-22
Just run this 
```
sudo apt-get install build-essential g++
```

---

### Post by Cypher on 2008-08-22
What program are you trying to compile and also take a look at the config.log file which will contain more information about what failed.

---

