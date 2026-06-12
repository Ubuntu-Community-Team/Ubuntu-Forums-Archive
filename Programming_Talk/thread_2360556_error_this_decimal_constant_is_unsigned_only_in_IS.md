---
title: "error: this decimal constant is unsigned only in ISO C90 [-Werror]"
date: 2017-05-05
forum: Programming Talk
---

### Post by rafelarote on 2017-05-05
hello ):P,
I  tried to install Cryptdb ([https://whitehatty.com/2012/09/30/cryptdb-howto-compile-on-ubuntu-linux-12-04/#comment-5410](https://whitehatty.com/2012/09/30/cryptdb-howto-compile-on-ubuntu-linux-12-04/#comment-5410) -> see here for more info).

And i have error in the end of install :

 **error: this decimal constant is unsigned only in ISO C90 [-Werror]**
[B]cc1plus: all warnings being treated as errors
make: *** [obj/parser/mysql_type_metadata.o] Error 1[/B]
./scripts/install.rb:176:in `pretty_execute': `make` failed (RuntimeError)
    from ./scripts/install.rb:169:in `>'
    from ./scripts/install.rb:147:in `fn'
    from ./scripts/install.rb:281

**I have 12.04 ubuntu and 32bits**.
Any suggestion how to fix it?? thanks

---

### Post by TheFu on 2017-05-05
[https://www.ubuntu.com/info/release-end-of-life](https://www.ubuntu.com/info/release-end-of-life) 
Support for 12.04 ended last month.  

I moved services from my last 12.04 box a few weeks ago and shut it down. No more patches coming for it and getting help really isn't possible anymore.

---

