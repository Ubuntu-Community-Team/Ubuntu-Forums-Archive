---
title: "error while loading shared libraries: libwx_gtk2_aui-2.7.so.0:"
date: 2006-08-23
forum: Programming Talk
---

### Post by Hakirato on 2006-08-23
Hello

I just installed Ubuntu for programming learning reason. WxWidget (2.7.x) was my choice for coding c++ with Eclipse. Well I had lots of problems to make the compilation to get succeed. I took me almost a week :frown: . Now I have the last problem when trying to execute the the sample file from wxwidget after the compilation in Eclipse:

/home/user/workspace/WxTestCalendar/Release/WxTestCalendar: error while loading shared libraries: libwx_gtk2_aui-2.7.so.0: cannot open shared object file: No such file or directory

Anyboy could help me with this issue?

The application executes with no problem when using terminal and write:

./WxTestCalendar



Thanks..

---

### Post by mlind on 2006-08-24
> **Hakirato said:**
> Hello

I just installed Ubuntu for programming learning reason. WxWidget (2.7.x) was my choice for coding c++ with Eclipse. Well I had lots of problems to make the compilation to get succeed. I took me almost a week :frown: . Now I have the last problem when trying to execute the the sample file from wxwidget after the compilation in Eclipse:

/home/user/workspace/WxTestCalendar/Release/WxTestCalendar: error while loading shared libraries: libwx_gtk2_aui-2.7.so.0: cannot open shared object file: No such file or directory

Anyboy could help me with this issue?

The application executes with no problem when using terminal and write:

./WxTestCalendar



Thanks..

Eclipse is linking program against wrong soname, that doesn't exist in Dapper. There's probably something wrong in how you compile it?

Library that has similar files is libwxgtk2.6-0 or libwxgtk2.6-0-dev, but neither contains the file you need..

---

