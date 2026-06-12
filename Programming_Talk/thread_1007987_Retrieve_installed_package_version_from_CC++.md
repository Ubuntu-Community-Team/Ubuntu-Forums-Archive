---
title: "Retrieve installed package version from C/C++?"
date: 2008-12-11
forum: Programming Talk
---

### Post by bedge on 2008-12-11
I'm looking at libapt-front-dev. but I can't find any docs for it.
I hate using popen("dpkg -l bork | sed ...") to get version info.

What's the _right_ way?

Or, please point me to the libapt-front-dev docs and I'll RTFM.

Thanks, Bruce

---

### Post by nvteighen on 2008-12-11
You have two reasonable options:

0. Use some shell script to grep the result from apt-get/aptitude show. (Why not?)
1. Use the libapt-* family of libraries and have an application natively aware of the packaging system. But IMO this is senseful only if you're developing an application that needs to have that functionality among others.

---

