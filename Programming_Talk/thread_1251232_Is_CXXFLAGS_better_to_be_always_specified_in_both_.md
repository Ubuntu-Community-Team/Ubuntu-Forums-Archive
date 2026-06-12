---
title: "Is CXXFLAGS better to be always specified in both link and compile stages?"
date: 2009-08-27
forum: Programming Talk
---

### Post by flylehe on 2009-08-27
Hi,
I learned that you specify in CXXFLAGS the debugging options and/or optimization options among others, whereas LDFLAGS is not to do so. 

In most Makefiles I have seen, CXXFLAGS is used in the compile rule, either implicit or explicit. A few days ago, however I saw a Makefile that uses CXXFLAGS in link stage. Its compile rule is implicit which I suppose to use CXXFLAGS as well. Its CXXFLAGS is defined as
```

ifeq ($(DEBUG),yes)
  OPTIMIZE_FLAG = -ggdb3 -DDEBUG
else
  OPTIMIZE_FLAG = -ggdb3 -O3
endif

ifeq ($(PROFILE),yes)
  PROFILE_FLAG = -pg
endif

CXXFLAGS = -Wall $(OPTIMIZE_FLAG) $(PROFILE_FLAG) $(CXXGLPK)

```
Does it mean that the optimization or/and debug options are necessary in both compile and link stages? So is it better to use CXXFLAGS in link stage too?

Thanks and regards!

---

### Post by nvteighen on 2009-08-27
> **flylehe said:**
> Hi,
I learned that you specify in CXXFLAGS the debugging options and/or optimization options among others, whereas LDFLAGS is not to do so. 

In most Makefiles I have seen, CXXFLAGS is used in the compile rule, either implicit or explicit. A few days ago, however I saw a Makefile that uses CXXFLAGS in link stage. Its compile rule is implicit which I suppose to use CXXFLAGS as well. Its CXXFLAGS is defined as
```

ifeq ($(DEBUG),yes)
  OPTIMIZE_FLAG = -ggdb3 -DDEBUG
else
  OPTIMIZE_FLAG = -ggdb3 -O3
endif

ifeq ($(PROFILE),yes)
  PROFILE_FLAG = -pg
endif

CXXFLAGS = -Wall $(OPTIMIZE_FLAG) $(PROFILE_FLAG) $(CXXGLPK)

```
Does it mean that the optimization or/and debug options are necessary in both compile and link stages? So is it better to use CXXFLAGS in link stage too?

Thanks and regards!
The CXXFLAGS should be used at compiling, because its effects are relevant there.

But, gcc/g++ will ignore them safely if you put them in any other stage, so, don't worry... Of course, the ideal is to put them where they're relevant, but at least it won't fail if you confuse the place as long as they're present at compiling stage.

---

