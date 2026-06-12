---
title: "Conditionally setting FLAGS variable in makefile"
date: 2010-04-09
forum: Programming Talk
---

### Post by GeoMX on 2010-04-09
I have my program version saved to a version.h file and would like to set the value of a FLAGS variable according to the content of this file.

I'm trying to do something like this:

```
VERSION=`cat version.h`
ifneq (,$(findstring "beta", $(VERSION)))
	@echo "nothing"
else
	@echo "it's beta"
	FLAGS=-g
endif
```

But it does not work. First, I get messages expressing I can't place operations before targets, if I place a dummy target before this, the FLAGS variable never sets.

Thanks in advance for all of your help

---

### Post by GeoMX on 2010-04-09
More information :).

The contents of version.h can be one of these:

```
#define VERSION "0.1 beta"
```
```
#define VERSION "0.1"
```

The makefile:
```
VERSIONH=`cat version.h`
VERSION=$(findstring beta, $(VERSIONH))
ifeq ($(VERSION),)
	FLAGS = 
else
	FLAGS = -g
endif

version: version.c
  cc -o version version.c $(FLAGS)
  @echo "VERSIONH: $(VERSIONH)"
  @echo "VERSION: $(VERSION)"
  @echo "FLAGS: $(FLAGS)"
```

Output of make command when version.h contains the beta word:
```
cc -o version version.c -g
version.h: #define VERSION "0.1 beta"
version: 
flags:

```
And when beta is not present:
```
version.h: #define VERSION "0.1"
version: 
flags:
```
It seems findstring is the problem, do you have any advice on how to get it working?

---

### Post by gmargo on 2010-04-09
I think I've got it working; see if you can adapt this.  I've got two version files so both can be tested at once:

```

$ cat version1.h
#define VERSION "0.1"

$ cat version2.h
#define VERSION "0.1 beta"

$ cat version.makefile
VERSION1 := $(shell cat version1.h)
VERSION2 := $(shell cat version2.h)
FLAGS1=
FLAGS2=

ifneq (,$(findstring beta, $(VERSION1)))
        FLAGS1=-g
endif
ifneq (,$(findstring beta, $(VERSION2)))
        FLAGS2=-g
endif

all:
        @echo "VERSION1 = \"$(VERSION1)\""
        @echo "VERSION2 = \"$(VERSION2)\""
        @echo "FLAGS1   = \"$(FLAGS1)\""
        @echo "FLAGS2   = \"$(FLAGS2)\""

$ make -f version.makefile
VERSION1 = "#define VERSION 0.1"
VERSION2 = "#define VERSION 0.1 beta"
FLAGS1   = ""
FLAGS2   = "-g"

```

---

### Post by diesch on 2010-04-09
Why not just

```
FLAGS=$(shell grep -q beta version.h && echo -- '-g')
```

---

### Post by GeoMX on 2010-04-10
> **gmargo said:**
> I think I've got it working; see if you can adapt this.  I've got two version files so both can be tested at once:

```

VERSION1 := $(shell cat version1.h)

```

Thank you, using shell and := everything works correctly :).

> **diesch said:**
> Why not just

```
FLAGS=$(shell grep -q beta version.h && echo -- '-g')
```
It seems a nicer way, I just had to remove the two dashes after the echo.
```
FLAGS=$(shell grep -q beta version.h && echo '-g')
```
Just one more question, how would I set an alternative value as in the else clause for the ieq/ineq?

THANK YOU so much for your help.

---

