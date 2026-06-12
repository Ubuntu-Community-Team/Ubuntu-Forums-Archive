---
title: "libiconv"
date: 2007-10-24
forum: Programming Talk
---

### Post by Neil_Wilson on 2007-10-24
I've just updated to 7.10, and now when I build my one of my apps I get the following errors, 

../common/StringUtilities.cpp:699: undefined reference to `libiconv_open'
../common/StringUtilities.cpp:716: undefined reference to `libiconv'


 can get around this error by building and installing my own version of libiconv, but I would like to know why, after the upgrade I have to do this.

Any ideas would be appreciated.

Thanks

Neil

---

### Post by Neil_Wilson on 2007-10-24
Problems solved - there was a conflict with two versions iconv.h.....

---

