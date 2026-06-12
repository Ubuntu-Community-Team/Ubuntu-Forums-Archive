---
title: "where is the libgssapi_krb5.a?"
date: 2008-05-21
forum: Programming Talk
---

### Post by kirys on 2008-05-21
It's me again ^_^
And still having more problems with static linking :) (mysql one still unsolved)
So i was trying another program that need kerberos
I seems that the libkrb5-dev doesn't contain  libgssapi_krb5.a
Which deb contains that file?
Thank you

---

### Post by pdwerryhouse on 2008-05-21
It's not there anymore; the upstream package doesn't support static linking.

See this debian bug report:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=439039](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=439039)

---

### Post by kirys on 2008-05-22
this mean that there is no way to static link curl that depends on it right?

---

### Post by pdwerryhouse on 2008-05-22
You could try recompiling the library; apparently there is an option that will let you build the .a file, but they don't support its use anymore.

---

### Post by kirys on 2008-05-22
Maybe i'll try recompile the curl without crypt/kerberos support (i don't need it).
But what is the meaning of giving the .a file of a lib (libcurl) that need the .a of another lib that doesn't exists? :)
Is there a way to avoid the krb5 lkib when static linking?
Thank you

---

