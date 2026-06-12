---
title: "Creating a C library with autotools"
date: 2007-05-01
forum: Programming Talk
---

### Post by WebDrake on 2007-05-01
Hello all,

I'm creating a small C library to assist simulation of some fun models developed in the field of [econophysics](http://en.wikipedia.org/wiki/Econophysics).  I've never used GNU autotools before so I was hoping someone could advise me on a few things.  I have the tutorial at [http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/autotools.html](http://www-src.lip6.fr/homepages/Alexandre.Duret-Lutz/autotools.html) but there are some specifics not covered there.

The library is called MGa but this could be changed if for any reason it's a really bad idea.  In terms of structure I've tried to follow aspects of the design of the GNU Scientific Library (GSL).

Anyway, first off, the idea for using this library is that headers should be included by calling,
```

#include <MGa/MGa_header_name.h>

```

So the two questions are, (i) how do I ensure that the make install puts all appropriate header files in the appropriate place and (ii) how do I deal with the problem of the headers being in the right place when the library is being built?

The solution for the latter is obviously that the make process should first copy all header files to $(top_srcdir)/MGa/ but I'm not sure about how to do this nicely.

The GSL uses a comparable technique, with all header files having to be copied to $(top_srcdir)/gsl before the rest of the system is built.  Here's the Makefile.am from that subdirectory:

```

header-links: remove-links
	HEADERLIST="$(top_srcdir)/gsl*.h $(top_srcdir)/*/gsl*.h"; \
	for h in $$HEADERLIST; do \
	  BASENAME=`basename $$h`; \
	  test -r $$BASENAME || $(LN_S) $$h $$BASENAME; \
	done

remove-links: 
	rm -f gsl*.h


all: all-am header-links

clean: clean-am remove-links
distclean: distclean-am remove-links
	-rm -f Makefile

```

... but I don't understand everything that this is doing, partly because I'm not strong on shell scripting but mainly because I don't understand the options such as remove-links, all, clean and distclean.  I can see to some extent what they *do*, but are they custom-defined options or will they mix cleanly with the rest of the make process?  I don't want to just copy-and-paste, I want to understand what the code is doing! ;-)

Can anyone advise me?  I will probably be back with far more questions but these are the starters. :-)

Thanks in advance,

     -- Joe

---

