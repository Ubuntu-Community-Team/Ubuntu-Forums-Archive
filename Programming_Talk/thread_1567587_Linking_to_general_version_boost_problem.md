---
title: "Linking to general version boost problem"
date: 2010-09-04
forum: Programming Talk
---

### Post by redeyerulk on 2010-09-04
Hi,
I'm trying to link to boost libraries (boost_thread and boost_filesystem)  I add -lboost_thread
-lboost_filesystem
flags and everything seems to work until I tried to deploy my application on machine with a newer version of boost then on my machine. It turned out that my application is linked against libboost_thread.so.1.40.0  and libboost_filesystem.so.1.40.0 instead of simply libboost_filesystem.so and libboost_thread.so. How can i link against general version of the library?

---

### Post by SledgeHammer_999 on 2010-09-04
I don't think there is way. In my system, libboost_filesystem.so and libboost_thread.so don't exist. And if they did, I think they would be symbolic links, linking back to libboost_filesystem.so.1.40.0.

Alternatively, you could link statically.

---

