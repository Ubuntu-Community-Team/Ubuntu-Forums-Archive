---
title: "[SOLVED] Cannot find library libboost 1.34.1"
date: 2008-08-03
forum: Packaging and Compiling Programs
---

### Post by happysmileman on 2008-08-03
I've downloaded and am trying to build pokerth from source (the one in the repos is a bit older and I'd prefer the newest one), but after a while building stops with the error:

```
/usr/bin/qmake-qt4 pokerth_server.pro -unix -o Makefile.pokerth_server
Project MESSAGE: Found boost_thread
Project MESSAGE: Found boost_thread-mt
Project MESSAGE: Found boost_filesystem
Project MESSAGE: Found boost_filesystem-mt
Project MESSAGE: Found boost_iostreams
Project MESSAGE: Found boost_iostreams-mt
Project ERROR: could not locate required library: libboost (version >= 1.34.1) --> http://www.boost.org/
make: *** [Makefile.pokerth_server] Error 2
```

I have installed libboost-dev and an "apt-cache policy libboost-dev" confirms that I have version 1.34.1 installed, so I really have no idea what's going wrong. I have all of the libboost-*-dev packages except libboost-python-dev, which wouldn't be needed for this since there's no python involved.

EDIT: Just made a mistake, I hadn't got libboost-program-options-dev installed, figured this out after reading the project file for qmake4 (the error message was very vague as you can see)

---

