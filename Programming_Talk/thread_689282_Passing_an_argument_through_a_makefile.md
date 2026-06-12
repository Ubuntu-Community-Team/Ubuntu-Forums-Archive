---
title: "Passing an argument through a makefile?"
date: 2008-02-06
forum: Programming Talk
---

### Post by earobinson on 2008-02-06
I'm working on a C program that takes arguments is there anyway I can set up the makefile so that I can pass the arguments to the program through the make file

I have it set up now so that ```
make run
``` runs the program I want ```
make run aaa
``` to run the program with arguments aaa

Thanks

---

### Post by stroyan on 2008-02-06
If you just add 'aaa' then it will be treated as a makefile target.
But you can add an assignment to a make command to set a variable.
Here is an example-
```
$ cat Makefile
OVERRIDING=default
run:
        echo running with $(ARG) and $(OVERRIDING)
$ make run
echo running with  and default
running with and default
$ make run ARG=a
echo running with a and default
running with a and default
$ make run ARG=a OVERRIDING="a little more"
echo running with a and a little more
running with a and a little more
$
```

---

### Post by earobinson on 2008-02-06
Thanks

---

### Post by dbw on 2012-09-27
You could also try using $(MAKECMDGOALS), which contains the arguments used on the command line.

---

