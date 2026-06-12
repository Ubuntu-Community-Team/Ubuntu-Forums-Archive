---
title: "Make"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by darren8 on 2014-01-24
Hi

I am trying to install pg_repack as per these instructions "http://reorg.github.io/pg_repack/#installation", as I am trying to sort out a database problem.

However, everytime I use the make command, I get this error "Makefile:19: /usr/lib/postgresql/9.1/lib/[COLOR=#ff0000]pgxs[/COLOR]/src/makefiles/pgxs.mk: No such file or directory.

make: *** No rule to make target `/usr/lib/postgresql/9.1/lib/pgxs/src/makefiles/pgxs.mk'.  Stop."


Looking at the error, it would appear that I am missing the "pgxs" directory

Any help would be great

Thanks

---

### Post by steeldriver on 2014-01-24
Hello and welcome to the forums

Did you install the appropriate postgresql development package(s) as 

> 
pg_repack can be built with make on UNIX or Linux. The PGXS build framework is used automatically. **Before building, you might need to install the PostgreSQL development packages** (postgresql-devel, etc.) and add the directory containing pg_config to your $PATH. Then you can run:


Depending on what version of Ubuntu you are running the package may be named something slightly different e.g.

```

$ apt-file search pgxs.mk
postgresql-server-dev-8.4: /usr/lib/postgresql/8.4/lib/pgxs/src/makefiles/pgxs.mk
**[COLOR=#0000ff]postgresql-server-dev-9.1[/COLOR]: /usr/lib/postgresql/9.1/lib/pgxs/src/makefiles/pgxs.mk**

```

---

### Post by darren8 on 2014-01-28
Hi, yes I installed the postgresql development package, after searching the web on various forums. Unfortunately this made no difference.

---

### Post by darren8 on 2014-01-28
Just to make sure I tried the command you listed, I didn't get what I was expecting "The program 'apt-file' is currently not installed.  You can install it by typing:" you will have to excuse me, I am very new to Linux.

---

### Post by steeldriver on 2014-01-28
don't worry about apt-file for now, what does

```
dpkg -L postgresql-server-dev-9.1 | grep pgxs
```

say?

---

### Post by darren8 on 2014-01-30
Very strange "Package `postgresql-server-dev-9.1' is not installed"

---

### Post by steeldriver on 2014-01-30
Try to install it - and note if there are any errors

---

### Post by darren8 on 2014-01-31
I tried to follow your earlier instructions regarding the postgresql development package. I seem to be missing one of the directories "pgxs" 
**/usr/lib/postgresql/9.1/lib/pgxs/src/makefiles/pgxs.mk**

---

### Post by steeldriver on 2014-01-31
Can you run

```
sudo apt-get install --reinstall postgresql-server-dev-9.1
```

and post back any errors please

---

### Post by darren8 on 2014-01-31
Great, I just ran " dpkg -L postgresql-server-dev-9.1 | grep pgxs" and this is the result

 /usr/lib/postgresql/9.1/lib/pgxs
/usr/lib/postgresql/9.1/lib/pgxs/config
/usr/lib/postgresql/9.1/lib/pgxs/config/install-sh
/usr/lib/postgresql/9.1/lib/pgxs/src
/usr/lib/postgresql/9.1/lib/pgxs/src/Makefile.port
/usr/lib/postgresql/9.1/lib/pgxs/src/nls-global.mk
/usr/lib/postgresql/9.1/lib/pgxs/src/Makefile.shlib
/usr/lib/postgresql/9.1/lib/pgxs/src/makefiles
/usr/lib/postgresql/9.1/lib/pgxs/src/makefiles/pgxs.mk
/usr/lib/postgresql/9.1/lib/pgxs/src/test
/usr/lib/postgresql/9.1/lib/pgxs/src/test/regress
/usr/lib/postgresql/9.1/lib/pgxs/src/test/regress/pg_regress
/usr/lib/postgresql/9.1/lib/pgxs/src/Makefile.global

---

### Post by steeldriver on 2014-01-31
Ok so now you should be good to go

---

### Post by darren8 on 2014-01-31
Great, thanks for all your help :)

---

