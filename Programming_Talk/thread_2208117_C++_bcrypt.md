---
title: "C++ bcrypt"
date: 2014-02-26
forum: Programming Talk
---

### Post by jnewing on 2014-02-26
I'm doing a quick little C++ app on Ubuntu and was wondering if crypt or something like that is around that supports blowfish hashing method like bcrypt? If someone could point me to lib, docs etc... something would be helpful.

Thanks.

---

### Post by spjackson on 2014-02-26
I use [http://www.cryptopp.com/](http://www.cryptopp.com/) in some projects.

---

### Post by jnewing on 2014-02-26
> **spjackson said:**
> I use [http://www.cryptopp.com/](http://www.cryptopp.com/) in some projects.

Just checking that out, while I do see blowfish under block ciphers, it doesn't look like it supports bcrypt hashing?

---

### Post by jnewing on 2014-02-26
To be honest I though I could do this with crypt so I tried something like this:

```
crypt(argv[1], "$2a$10$randomgensalthere$")
``` 

however it never seems to error but never gives any output at all :/ where as all the other key derivations seem to work just fine :/

---

