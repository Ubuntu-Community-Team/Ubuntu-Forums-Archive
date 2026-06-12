---
title: "Compiling Testdisk 7.1 from source code on ubuntu 16.04 64bit Failed"
date: 2016-11-08
forum: Packaging and Compiling Programs
---

### Post by ps3love on 2016-11-08
Hello, i need a procedure to compiling testdisk-7.1-WIP.tar.bz2 on ubuntu 16.04 64 bit, my procedure is fail.


```
sudo apt install build-essential e2fslibs-dev libncurses5-dev libncursesw5-dev ntfs-3g-dev libjpeg-dev uuid-dev zlib1g-dev qtbase5-dev qttools5-dev-tools pkg-config dh-autoreconf
sudo apt install autoconf automake git-core
cd testdisk7.1-WIP
sudo ./configure
sudo make
here fail:  moc: could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/moc': No such file or directory
```

---

### Post by mc4man on 2016-11-08
Maybe just download & use the pre-compiled binary instead.
Otherwise  - you could try,
install qt5-default package (may not be needed...

Then in the terminal you are using to configure & make run this first -  (definitely needed
```
export QT_SELECT=qt5
```

---

### Post by ps3love on 2016-11-09
suspend_no.c: In function &#8216;resume_memory&#8217;:
suspend_no.c:17:32: warning: unused parameter &#8216;cinfo&#8217; [-Wunused-parameter]
 int resume_memory(j_common_ptr cinfo)
                                ^
  CCLD     photorec
  CC       fidentify.o
  CCLD     fidentify
  CXX      qphotorec-qmainrec.o
  CXX      qphotorec-qphotorec.o
  CXX      qphotorec-qphbs.o
  CXX      qphotorec-qpsearch.o
  GEN      moc_qphotorec.cpp
moc: could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/moc': No such file or directory
Makefile:2149: set di istruzioni per l'obiettivo "moc_qphotorec.cpp" non riuscito
make[2]: *** [moc_qphotorec.cpp] Errore 1
make[2]: uscita dalla directory "/home/rtk/Scaricati/testdisk-7.1-WIP/src"
Makefile:434: set di istruzioni per l'obiettivo "all-recursive" non riuscito
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory "/home/rtk/Scaricati/testdisk-7.1-WIP"
Makefile:373: set di istruzioni per l'obiettivo "all" non riuscito
make: *** [all] Errore 2

---

### Post by howefield on 2016-11-09
Moved to the "*Packaging and Compiling Programs*" forum.

---

### Post by mc4man on 2016-11-09
Then you should just use the prebuilt unless you can figure what you're doing differently.
Doing the 2 things I mentioned works fine here, the binaries are produced,  point of your fail - 
 ```
CCLD     photorec
  CC       fidentify.o
  CCLD     fidentify
  CXX      qphotorec-qmainrec.o
  CXX      qphotorec-qphotorec.o
  CXX      qphotorec-qphbs.o
  CXX      qphotorec-qpsearch.o
  GEN      moc_qphotorec.cpp
  CXX      qphotorec-moc_qphotorec.o
  GEN      rcc_qphotorec.cpp
  CXX      qphotorec-rcc_qphotorec.o
ln -s qphotorec_locale.qrc . || exit 0
ln: failed to create symbolic link './qphotorec_locale.qrc': File exists
  GEN      rcc_qphotorec_locale.cpp
  CXX      qphotorec-rcc_qphotorec_locale.o
  CXXLD    qphotorec

```
Or consider disabling qt in build & just build/use the text interface...

---

