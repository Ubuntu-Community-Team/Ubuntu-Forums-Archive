---
title: "make error"
date: 2019-03-04
forum: New to Ubuntu
---

### Post by asghari.be on 2019-03-04
```
bubi@bubi:~/Bio/last-973$ make
make[1]: Entering directory '/home/bubi/Bio/last-973/src'
g++ -DLAST_INT_TYPE=unsigned  -O3 -std=c++11 -pthread -DHAS_CXX_THREADS -I. -c -o CyclicSubsetSeed.o CyclicSubsetSeed.cc
In file included from zio.hh:6:0,
                 from CyclicSubsetSeed.cc:5:
mcf_zstream.hh:10:10: fatal error: zlib.h: No such file or directory
 #include <zlib.h>
          ^~~~~~~~
compilation terminated.
makefile:96: recipe for target 'CyclicSubsetSeed.o' failed
make[1]: *** [CyclicSubsetSeed.o] Error 1
make[1]: Leaving directory '/home/bubi/Bio/last-973/src'
makefile:3: recipe for target 'all' failed
make: *** [all] Error 2
```

...............................................................................

i have a problem please help

---

### Post by Impavidus on 2019-03-04
You haven't installed all required header files. Try```
sudo apt install zlib1g-dev
```

---

