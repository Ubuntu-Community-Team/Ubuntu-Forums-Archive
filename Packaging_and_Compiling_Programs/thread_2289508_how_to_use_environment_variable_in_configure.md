---
title: "how to use environment variable in configure"
date: 2015-08-04
forum: Packaging and Compiling Programs
---

### Post by newcfd on 2015-08-04
export APP_HOME = /something/ 
is it possible to use it in configure --prefix=$APP_HOME?

I also want to use it in ccmake . settings. It seems that I can not do it.

Any help?  Thanks.

---

### Post by newcfd on 2015-08-04
configure --prefix=$APP_HOME works. But in the Makefile absolute path is used. I would prefer to have $APP_HOME in the Makefile.

---

### Post by newcfd on 2015-08-04
I tried configure --prefix=${$APP_HOME}. configure does not like it

---

### Post by steeldriver on 2015-08-04
try
```

--prefix='$(APP_HOME)'

```

the single quotes should prevent shell expansion

---

### Post by newcfd on 2015-08-05
Thanks for your reply. the quotes do prevent shell expansion.
But configure adds the source dir in front of $(APP_HOME)
For example, if the source is in /home/src, install dir becomes /home/src/$APP_HOME

> **steeldriver said:**
> try
```

--prefix='$(APP_HOME)'

```

the single quotes should prevent shell expansion

---

