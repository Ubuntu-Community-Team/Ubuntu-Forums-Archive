---
title: "retrieve called target name in Makefile?"
date: 2010-05-17
forum: Programming Talk
---

### Post by biogerm on 2010-05-17
when writing a Makefile, how do we get the name of the target which is called by make? for example, in a makefile we have

```

test1: clean
     do something
test2: clean
     do something
clean:
     depending on which "test" is called

```

---

### Post by r-senior on 2010-05-17
Try "$@", e.g.

```

hello_world: 
	echo $@

```

$ make -s hello_world
hello_world

---

### Post by biogerm on 2010-05-17
> **r-senior said:**
> Try "$@", e.g.

```

hello_world: 
	echo $@

```

$ make -s hello_world
hello_world

thanks for the reply. but it doesn't work actually because:
```

test1: clean
      do something
test2: clean
      do something
clean:
      echo $@

```
and if you "make test1"
here it echoes "clean", not "test1" that i want.

---

### Post by dwhitney67 on 2010-05-17
> **biogerm said:**
> 
and if you "make test1"
here it echoes "clean", not "test1" that i want.

I'm very skeptical of your claims; either you have a malformed Makefile or you did not issue the command "make test1".

Btw, you can also use the built-in make variable MAKECMDGOALS to determine which, if any, argument was passed to the make command.
```

foo1:
        @echo "$(MAKECMDGOALS)"

foo2:
        @echo $@

clean:
        @echo $@

```

---

### Post by biogerm on 2010-05-17
> **dwhitney67 said:**
> I'm very skeptical of your claims; either you have a malformed Makefile or you did not issue the command "make test1".

Btw, you can also use the built-in make variable MAKECMDGOALS to determine which, if any, argument was passed to the make command.
```

foo1:
        @echo "$(MAKECMDGOALS)"

foo2:
        @echo $@

clean:
        @echo $@

```
Thank you dwhitney67! Problem solved!

$(MAKECMDGOALS) gives me the string I want uniquely anywhere in the Makefile.

---

### Post by nvteighen on 2010-05-18
> **biogerm said:**
> Thank you dwhitney67! Problem solved!

$(MAKECMDGOALS) gives me the string I want uniquely anywhere in the Makefile.

Another approach is to use variables in your script.

```

APP_NAME = yay!

$(APP_NAME):
	@echo $@

```

---

