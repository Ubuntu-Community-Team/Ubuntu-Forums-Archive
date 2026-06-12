---
title: "Variables in Makefile, used in several commands"
date: 2006-10-13
forum: Programming Talk
---

### Post by Arndt on 2006-10-13
Let's say I have a make rule like this (using some fictitious commands):

```
%.a: %.b
    a_compiler -i title -o $@ $<
    gen_indices -i title $< > $*.ix
    -mkdir titles/title
    mv $*.ix titles/title

```
It's not so important exactly what happens, only that there are many subcommands.

Now I need to generalize this so that "title" is not fixed, but computed from $<. Then the rule may become

```
%.a: %.b
    a_compiler -i `gen_title $<` -o $@ $<
    gen_indices -i `gen_title $<` $< > $*.ix
    -mkdir titles/`gen_title $<`
    mv $*.ix titles/`gen_title $<`

```
Imagine that the gen_title command is actually a whole line long, and perhaps also very computationally demanding. What I would like to do is this

```
%.a: %.b
    title=`gen_title $<`
    a_compiler -i $(title) -o $@ $<
    gen_indices -i $(title) $< > $*.ix
    -mkdir titles/$(title)
    mv $*.ix titles/$(title)

```
But this doesn't work, because the title= line sets a shell variable, which doesn't survive to the next line, and $(title) refers to a make variable anyway. So, my question is: how do I avoid repeating the gen_title command, without wrapping the whole thing in a shell script?

(I'd like to keep the usual make handling of the lines, them being echoed (or not), error checking after each line, etc.; otherwise putting " && \" between all the lines would work, or a shell script.)

I'm using GNU make - if there is a solution portable to other make's that would be nice, but not important.

---

### Post by duff on 2006-10-13
```
TITLE=$(shell gen_title)

target: deps
   cmd $(TITLE)

```

---

### Post by Arndt on 2006-10-16
> **duff said:**
> ```
TITLE=$(shell gen_title)

target: deps
   cmd $(TITLE)

```

Thank you. That solves the readability problem, so my Makefiles are very much improved.

The command is still executed many times unnecessarily, though. Some kind of "rule-local" make variable would have been nice.

---

