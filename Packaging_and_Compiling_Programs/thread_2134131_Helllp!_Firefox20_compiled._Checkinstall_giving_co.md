---
title: "Helllp! Firefox20 compiled. Checkinstall giving core dump at hyphenation files"
date: 2013-04-10
forum: Packaging and Compiling Programs
---

### Post by xfcewithmutter on 2013-04-10
I'm trying doing  optimized ( -O3, and march=corexxx like flags ) build for firefox 20. 

i tried  dpkg-buildpackage system no one can support for this. 

im get firefox 20 source. and  doed "./configure" with needed options and used "time make -j8" they are doing without problem. after 

im used  "sudo checkinstall"

i recompiled always per machine. i tried it over virtual box. i tried it on my machine (8 gb memory 3rd gen corei )  . i tried it on different (2gb memory core2duo)...

im tryind it over xubuntu i386. all updates done.

checkinstall always giving Segmantation Fault ( core dumped ) error.  at different files.... always at hyphenation *.dic files. error 139.

---

