---
title: "can makefile targets be variables?"
date: 2009-11-28
forum: Programming Talk
---

### Post by SIGTERMer on 2009-11-28
i've searched alot for this one. can makefile targets be variables? as in
```

$var: some.c source.c files.c
   cc ...

```
If not, is there anyway to make a target variable?

thanks

---

### Post by dwhitney67 on 2009-11-28
> **SIGTERMer said:**
> i've searched alot for this one. can makefile targets be variables? as in
```

$var: some.c source.c files.c
   cc ...

```
If not, is there anyway to make a target variable?

thanks

Never heard of this possibility.  What specifically are you trying to accomplish (sigh!)???


Actually, there are 'wildcard' types of targets one can define, but not using the shell-script style you presented.

---

### Post by apmcd47 on 2009-11-28
> **SIGTERMer said:**
> i've searched alot for this one. can makefile targets be variables? as in
```

$var: some.c source.c files.c
   cc ...

```
If not, is there anyway to make a target variable?

thanks

The following is a paste from a makefile that I maintain (but did not write):

```
$(RGF): $(OBJRGF)
        $(LINK) -D $(PUBLIC) $(OBJRGF) 
        $(ALLOW)

```
So the answer is yes! And it works. I don't think I would have written it that way, but if it ain't broke...

Andrew

---

### Post by nvteighen on 2009-11-28
Er... I'm surprised... There's a very common usage of this when people place the executable's name into a variable (usually called APP or APP_NAME) so they can change it if necessary more easily by having that variable declared at the top. Of course the $(var) syntax is needed to expand its contents.

---

### Post by SIGTERMer on 2009-11-29
> **apmcd47 said:**
> The following is a paste from a makefile that I maintain (but did not write):

```
$(RGF): $(OBJRGF)
        $(LINK) -D $(PUBLIC) $(OBJRGF) 
        $(ALLOW)

```
So the answer is yes! And it works. I don't think I would have written it that way, but if it ain't broke...

Andrew

Andrew, you're a life saver! thanks :)

---

