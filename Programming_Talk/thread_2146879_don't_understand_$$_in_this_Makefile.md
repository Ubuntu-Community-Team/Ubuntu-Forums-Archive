---
title: "don't understand $$ in this Makefile"
date: 2013-05-20
forum: Programming Talk
---

### Post by IAMTubby on 2013-05-20
Hello,
I have a small question regarding a Makefile. I was able to understand most of the important aspects, but still haven't been able to figure out the meaning of **-o $$a $$a.o** below.

```

SRCS = sourceOne.c sourceTwo.c
SOBJ = $(patsubst %.c,%.o,$(SRCS)) **#I understand this will translate to sourceOne.o and sourceTwo.o**
APP = $(patsubst %.c,%,$(SRCS)) **#I understand this will translate to sourceOne and sourceTwo, which will be the names of the eventual executables **


$(APP): $(SOBJ) $(LIBSHARED)
        @set -e ; \
                for a in $(APP) ; do \
                        $(CC) $(CFLAGS) $(CPPFLAGS) **-o $$a $$a.o** $(PRJLIB) $(LINKMAP) $(DEPLIBS) ; \
                done
**#Again, here I understand that basically it generates executables called sourceOne and sourceTwo from sourceOne.o and sourceTwo.o, but what I don't understand is the $$ part.**
 
```
What exactly does **-o $$a $$a.o** mean ?


I read that ***"[COLOR=#000000][FONT=Times New Roman]If you need a literal dollar sign, put in a double dollar sign ([/FONT][/COLOR]$$[COLOR=#000000][FONT=Times New Roman])[/FONT][/COLOR]"***. But hmm, still can't relate to this.

Please advise.
Thanks.

---

### Post by MG&amp;TL on 2013-05-20
> **IAMTubby said:**
> 
```

                for a in $(APP) ; do \
                        $(CC) $(CFLAGS) $(CPPFLAGS) **-o $$a $$a.o** $(PRJLIB) $(LINKMAP) $(DEPLIBS) ; \
                done
 
```
What exactly does **-o $$a $$a.o** mean ?


I read that ***"[COLOR=#000000][FONT=Times New Roman]If you need a literal dollar sign, put in a double dollar sign ([/FONT][/COLOR]$$[COLOR=#000000][FONT=Times New Roman])[/FONT][/COLOR]"***. But hmm, still can't relate to this.


You probably know that *make* uses a '$' character to reference variables. Unfortunately, so do most system shells. In the for-loop I hightlighted, it builds a binary for every entry in the $(APP) variable.
To do this, it uses a shell variable, 'a' in order to keep track. However, you can't just use '$a' to use the variable, as *make* would try and find a *make* variable called 'a', when in fact it is a shell variable. So in order to get '$a' passed to the shell, rather than a blank, a double-dollar '$$a' is used. *Make* evaluates this as '$a', so everyone is happy.

---

### Post by IAMTubby on 2013-05-20
> **MG&TL said:**
> So in order to get '$a' passed to the shell, rather than a blank, a double-dollar '$$a' is used. *Make* evaluates this as '$a', so everyone is happy.
Thanks a lot for the reply MG&TL. Your explanation is very clear :)

---

