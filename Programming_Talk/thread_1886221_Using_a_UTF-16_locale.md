---
title: "Using a UTF-16 locale"
date: 2011-11-24
forum: Programming Talk
---

### Post by ehmicky on 2011-11-24
Hi there,

I'd like to know how to use a UTF-16 locale instead of the standard UTF-8 one in Ubuntu. Note that my question is not about conversion between UTF-16 and UTF-8 (iconv, etc.), but about having a terminal running natively in UTF-16.
The reason for it is that I'd like to have a Linux terminal which behaves natively as a Windows one (considering Unicode handling), in order to check that my programs can be run under both Linux and Windows.
I notice that en_US.utf-16 doesn't exist in /usr/share/i18n/SUPPORTED

Thank you very much

---

### Post by crdlb on 2011-11-25
It is not possible to use UTF-16 because it is not ASCII-compatible. Most importantly, C strings are NUL-terminated, and UTF-16 can contain embedded NULs.

---

### Post by ehmicky on 2011-11-25
Thanks for your reply,
But Windows manages to handle this issue since it uses UTF-16 natively, doesn't it ?

---

### Post by crdlb on 2011-11-25
My understanding is that Windows has two parallel APIs. One is 8-bit and uses Windows "ANSI" codepages; the other is 16-bit and uses UTF-16.

---

### Post by ehmicky on 2011-11-25
Ok thanks,
So actually, no matter why, if Linux can't run a UTF-16 terminal, then I'll have to switch to Windows (or use a VM, etc.) to make the tests, so it answers my question. Thanks !

---

