---
title: "configure: error: Missing a vital header file for id3lib"
date: 2009-03-12
forum: Programming Talk
---

### Post by huangyingw on 2009-03-12
hello, I met this when I wanting to configure the id3lib-3.8.3 package.
I saw following sentence in configure.in file:
=================================================================AC_CHECK_HEADERS(               \
  string                        \
  iomanip.h                     \
  ,,AC_MSG_ERROR([Missing a vital header file for id3lib])
)
=================================================================
So, it means that I am missing the iomanip.h file. 
To resovlve this, what ever action should I do.
Any clue would be greatly appreciated.

---

### Post by dwhitney67 on 2009-03-12
Have you installed the "build-essential" package onto your system?
If not, try
```

sudo apt-get install build-essential

```

P.S.  I do not believe iomanip.h is used anymore; today it is referred to merely as iomanip.

---

### Post by huangyingw on 2009-03-15
Sorry for late reply.
Yes, I have installed the build-essential. While still get this error.
I would try to replace the iomanip.h with iomanip in the configure.in file.
I am not sure whether would this work. 
Will let you know the result of my try.

---

