---
title: "DB2 Installation problem"
date: 2006-01-11
forum: Programming Talk
---

### Post by 0x001A4 on 2006-01-11
I got the DB2 tarball from IBM for my kernel. Now when I try and run the sh file, i get this error:

```

/home/mat/db2/pe/db2/linux26/install/../bin/db2langdir: error while loading shared
libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
/home/mat/db2/pe/db2/linux26/install/../bin/db2langdir: error while loading shared
libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
/home/mat/db2/pe/db2/linux26/install/../bin/disp_msg: error while loading shared
libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

My guess is I'm missing a C++ library of some sort. Could anyone clarify and maybe help me fix this? Thanks!

---

### Post by Tom Stave on 2006-01-12
DB2 needs an older version of libstdc++.   The following will get your libstdc++.so.5.

sudo apt-get install libstdc++5

---

