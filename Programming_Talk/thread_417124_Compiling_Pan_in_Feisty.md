---
title: "Compiling Pan in Feisty"
date: 2007-04-21
forum: Programming Talk
---

### Post by trak87 on 2007-04-21
I'm trying to compile a newer version of Pan in my newly installed Feisty. I installed build-essential and the required libs and so ./configure runs successfully. But "make" is giving me a problem.  Here are the results:

$ make
make  all-recursive
make[1]: Entering directory `/home/mine/apps/pan-0.128/pan-0.128'
Making all in po
make[2]: Entering directory `/home/mine/apps/pan-0.128/pan-0.128/po'
file=`echo am | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file am.po
/bin/sh: -o: not found
make[2]: *** [am.gmo] Error 127
make[2]: Leaving directory `/home/mine/apps/pan-0.128/pan-0.128/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mine/apps/pan-0.128/pan-0.128'
make: *** [all] Error 2


I don't understand what "-o" is testing for.  I get the same compile problem with version .127 although it compiled fine in Edgy. What am I missing?

Pan website:  [http://pan.rebelbase.com/](http://pan.rebelbase.com/)

---

### Post by WW on 2007-04-21
I don't have solution for you--only a few clues.

I took a look at the pan-0.128 source; in particular, Makefile.in.in in the po subdirectory.  The error appears to be from this command:
```

.po.gmo:
	file=`echo $* | sed 's,.*/,,'`.gmo \
	  && rm -f $$file && $(GMSGFMT) -o $$file $<

```
For some reason, the macro GMSGFMT is not defined.

In the main directory, the file aclocal.m4 contains this line:
```

	  AC_PATH_PROG(GMSGFMT, gmsgfmt, $MSGFMT)

```
Unfortunately I don't know enough about the autotools suite to figure out what is going wrong.

---

### Post by trak87 on 2007-04-21
Thanks. That gave me a clue to search on GMSGFMT and I found this thread:

[http://forum.xfce.org/index.php?action=profile;u=3462;sa=showPosts](http://forum.xfce.org/index.php?action=profile;u=3462;sa=showPosts)

The guy says to install the gettext package. I did and it is now compiling.

---

