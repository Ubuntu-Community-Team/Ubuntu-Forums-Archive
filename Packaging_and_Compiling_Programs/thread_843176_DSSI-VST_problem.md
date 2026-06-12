---
title: "DSSI-VST problem"
date: 2008-06-28
forum: Packaging and Compiling Programs
---

### Post by dlawler on 2008-06-28
ok, so i downloaded the source for the dssi-vst package, and i directed myself to the folder and ran make.
this is what happens.


daniel@daniel-laptop:~$ cd ~/dssi-vst-0.7/
daniel@daniel-laptop:~/dssi-vst-0.7$ make
g++ -Ivestige -Wall -fPIC remotepluginclient.cpp -c
make: g++: Command not found
make: *** [remotepluginclient.o] Error 127



dammit.

---

### Post by WW on 2008-06-28
It looks like you don't have the C++ compiler installed.  You can get the basic  C/C++ build tools by installing the package **build-essential**:
```

sudo apt-get install build-essential

```

---

