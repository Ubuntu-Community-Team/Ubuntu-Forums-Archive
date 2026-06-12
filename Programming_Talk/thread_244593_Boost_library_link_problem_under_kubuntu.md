---
title: "Boost library link problem under kubuntu"
date: 2006-08-26
forum: Programming Talk
---

### Post by utab on 2006-08-26
Dear all,

I have installed the boost libraries by aptitude but there is sth wrong 

when i use 

g++ -g -o Read Driver.cc Mesh_Gen.cc -I/usr/include/boost -L/usr/lib -lboost_filesystem-1_33_1

I get

/usr/bin/ld: cannot find -lboost_regex-gcc-1_33_1
collect2: ld returned 1 exit status
make: *** [Read] Error 1

this means that it can not find the library files, but they are there under /usr/lib. I could not figure this out. Can somebody help me?

Regards,

---

### Post by utab on 2006-08-26
ldconfig solved the problem and updated the /etc/ld.so.cache

---

### Post by AugustinMa on 2010-08-13
I had a very similar problem and found this post while searching. I managed to solved the problem after much more searching, so I post it here for other people.

I had to link to the proper library this way:
g++ boost_example.cpp -o run -lboost_filesystem-mt
[http://linux.overshoot.tv/ticket/127](http://linux.overshoot.tv/ticket/127)

The real problem is that the boost documentation is lacking and does not say which library to link to. See:
[http://linux.overshoot.tv/ticket/129](http://linux.overshoot.tv/ticket/129)

Anyway, to use boost/file_system, link to: -lboost_filesystem-mt .

---

