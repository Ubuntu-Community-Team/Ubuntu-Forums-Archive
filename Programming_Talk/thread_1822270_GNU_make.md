---
title: "GNU make"
date: 2011-08-10
forum: Programming Talk
---

### Post by cybo on 2011-08-10
i used GNU Make before but only for small projects and never really wrote my own Makefile before. we are using makefiles at my work and there is a small piece of code i don't understand:

```
$(ASMSRCS:.src=.obj)
```

i'm not even sure where to look for an explanation of this in the documentation for GNU. i would really appreciate if someone could explain what this piece of code does.

thanks.

---

### Post by dwhitney67 on 2011-08-10
Surely in the Makefile there is an assignment made to ASMSRCS of one or more files that end with the .src extension.

The entry of which you inquired about is converting the .src extension to the .obj extension, for each file in ASMSRCS, perhaps as a means to identify the names of the object file(s) that will be created when the source file(s) are compiled.  However, I would have expected to see that line appear as something like:
```

ASMOBJS = $(ASMSRCS:.src=.obj)

```

P.S.  You can play with this Makefile to get a better grasp of the concept:
```

ASMSRCS = file_1.src file_2.src

ASMOBJS = $(ASMSRCS:.src=.obj)

test:
   @echo $(ASMSRCS)
   @echo $(ASMOBJS)

```

---

### Post by cybo on 2011-08-10
> **dwhitney67 said:**
> 
```

ASMOBJS = $(ASMSRCS:.src=.obj)

```


does this command work only on file extensions? 

say in the example you gave
```
ASMSRCS = file_1.src file_11.src file_111.src
ASMOBJS = $(ASMSRC:1=2)

```
will ASMOBJS now be equal to 
```
ASMSOBJS = file_2.src file_22.src file_222.src
```

i realize it is unusual use of this functionality, but i just want to understand it fully.

thanks

---

### Post by dwhitney67 on 2011-08-10
To make a change from a 1 in the string to instead be 2, you would use subst (substitute string).

For example:
```

WITH_ONE = file_1.src
WITH_TWO = $(subst 1,2,$(WITH_ONE))

foo:
   @ echo $(WITH_TWO)

```
To change the file extension, patsubst (which is short for pattern substitute string) can be used.  Google for more information on these topics, for there is more detailed information out there than I could ever offer.

---

### Post by Arndt on 2011-08-10
> **cybo said:**
> i used GNU Make before but only for small projects and never really wrote my own Makefile before. we are using makefiles at my work and there is a small piece of code i don't understand:

```
$(ASMSRCS:.src=.obj)
```

i'm not even sure where to look for an explanation of this in the documentation for GNU. i would really appreciate if someone could explain what this piece of code does.

thanks.

[http://www.gnu.org/software/make/manual/make.html#Substitution-Refs](http://www.gnu.org/software/make/manual/make.html#Substitution-Refs)

---

### Post by cybo on 2011-08-10
> **Arndt said:**
> [http://www.gnu.org/software/make/manual/make.html#Substitution-Refs](http://www.gnu.org/software/make/manual/make.html#Substitution-Refs)

thanks. it really helped

---

