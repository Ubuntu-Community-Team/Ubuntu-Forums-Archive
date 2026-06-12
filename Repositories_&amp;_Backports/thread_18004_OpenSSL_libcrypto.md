---
title: "OpenSSL libcrypto?"
date: 2005-03-04
forum: Repositories &amp; Backports
---

### Post by HungSquirrel on 2005-03-04
I am trying to build [OpenNTPD](http://www.openntpd.org/), but configure bails out looking for OpenSSL libcrypto.  What package has this, if any?

```
configure: error: *** Can't find recent OpenSSL libcrypto (see config.log for details) ***
```

---

### Post by kyle01 on 2005-05-25
I think I had a similar problem and was just able to solve it. I tried to compile WepAttack which needs libcrypto to include <openssl/md5.h>

By chance, I found out that this is provided by libssl-dev

strange...

---

### Post by grip2 on 2006-05-12
apt-get install libssl-dev

---

### Post by bnuytten on 2008-08-08
Great! Works for compiling openssh_4.7p1 on Hardy too :-)

---

