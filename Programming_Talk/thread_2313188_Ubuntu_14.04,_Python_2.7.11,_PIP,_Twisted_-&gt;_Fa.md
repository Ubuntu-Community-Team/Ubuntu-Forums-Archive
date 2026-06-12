---
title: "Ubuntu 14.04, Python 2.7.11, PIP, Twisted -&gt; Fail"
date: 2016-02-10
forum: Programming Talk
---

### Post by Sami Lehtinen on 2016-02-10
Hi, I got strange (?) PIP issue. 

I've installed  Python 2.7.11 for Ubuntu 14.04 and it works well. But there are couple  of libraries I can't install for 2.7.11 nor 2.7.9 or 2.7.10 for unknown  reason. It says that the library can't be found. The extact error  message is:

```
No matching distribution found for Twisted'.
```

PIP isn't  completely broken, because I've installed about 20 other libraries. But  now I'm highly confused why Twisted won't work. Error messages do not  give any kind of hint what the actual problem is. With the original OS  provided python I can install Twisted, but the python 2.7.6 is too old  for some other libraries. Any pro tips? I guess this is super trivial  issue if you just know what the problem is. I've Googled and asked a few  guys and nobody seems to know what it is all about.
Edit: One more  extra detail, it's Twisted==14.0.2 if that does make any difference,  I've tried some other Twisted versions and any of those won't be found. I also got the pynacl installed just fine after compiling and installing libsodium.

Any pro tips?

**Solved: libbz2-dev wasn't installed and bzip2 library wasn't available. **

---

