---
title: "Where is the standard library in c++?"
date: 2009-03-11
forum: Programming Talk
---

### Post by Melindrea on 2009-03-11
It's very possibly that this has come up and that I'm just not sure how to search for it.

I have need to look up the standard implementation of something (quicksort, to be exact), but I have no idea where to look for it. I've found the headerfiles in usr/include, but that doesn't quite help me. I know it's in stdlib/cstdlib, but where is that file?

Thank you,
Melindrea

---

### Post by stumbleUpon on 2009-03-11
on my machine,

```
locate cstdlib
```

gives

```
/usr/include/c++/4.3/cstdlib
/usr/include/c++/4.3/tr1/cstdlib
/usr/include/c++/4.3/tr1_impl/cstdlib
```

---

### Post by Melindrea on 2009-03-11
Well, that gave me header files, but still not the actual files, so I still haven't found the implementation.

Perhaps it's not in cstdlib, or the actual file is called something else?

---

### Post by Npl on 2009-03-11
if you re seeking for the C++ implementation, its in the header file "algorithm". Since its an template, implementation has to be in the headers.

The C Version is somewhere in glibc (and only in compiled form unless you DL the sources). I had to dig it up for myself sometime for a presentation, so ill attach it

---

### Post by Melindrea on 2009-03-11
Thanks. =) It was the c++ one I needed. We're supposed to compare that implementation with one we made ourselves.

---

### Post by Sinkingships7 on 2009-03-11
I'm not sure if it's what you're looking for, but you can use [www.cppreference.com](www.cppreference.com) as a reference to the standard library. It's up to date and easy to read.

---

### Post by Melindrea on 2009-03-11
That's going to be very useful, but didn't have the implementation I needed. Ah well, I've found some other references.  Thank you =)

---

