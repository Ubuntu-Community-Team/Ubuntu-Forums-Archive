---
title: "std::extent problem"
date: 2013-07-05
forum: Programming Talk
---

### Post by hvn on 2013-07-05
Hi,

Using Ubuntu 10.04 LTS, I'm trying to use std::extent. Following the diverse c++ websites, I've included <type_traits> and try to do this: 'int cols = std::extent<xr, 2>::value'. However, extent isn't recognized and the websites tell that it works from standard C++11 onwards. Helppages show that Lucid = 10.04LTS should support 'std::extent' when at least libstdc++ 6.4.4 is installed. My version is 6.4.6. So I wonder why I can't use 'extent' ?

Thanks for helping out.

---

### Post by spjackson on 2013-07-05
Which compiler version are you using? You probably need
```

g++ -std=c++0x

```
or possibly -std=c++11 if it's a newer compiler. The repository version on 10.04 is 4.4.3 and that doesn't recognize c++11, so you'd want c++0x.

---

### Post by hvn on 2013-07-05
That's what I looked at as well at first but couldn't figure out which version it was, so I assumed it was the correct version. Just tested -std=c++0X via commandline and that works. So thank you.

---

