---
title: "How can I include boost iostreams library"
date: 2007-07-06
forum: Programming Talk
---

### Post by yinglcs2 on 2007-07-06
Hi,

i am trying to compile a boost iostreams example, but I get the following error:

/src/boostTest.cpp:3:51: warning: boost/iostreams/filtering_streambuf.hpp: No such file or directory
/src/boostTest.cpp:4:36: warning: boost/iostreams/copy.hpp: No such file or directory
/src/boostTest.cpp:5:43: warning: boost/iostreams/filter/zlib.hpp: No such file or directory

and when I go to '/usr/include/boost/' it does not have iostreams sub-directory.

Can you please tell to install iostreams sub-library of boost?

Thank you.

---

### Post by yinglcs2 on 2007-07-06
I solve it by 'sudo apt-get install libboost-iostreams-dev'

---

