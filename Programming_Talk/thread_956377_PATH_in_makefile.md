---
title: "PATH in makefile"
date: 2008-10-23
forum: Programming Talk
---

### Post by ngmachado on 2008-10-23
Hi all,

I bet this one is easy... but not for me.

I want to change the current PATH variable in a makefile.

For instance:

```

$ echo $PATH
/usr/bin:/usr/sbin

$ PATH=$PATH:/my/dir
$ echo $PATH
/usr/bin:/usr/sbin:/my/dir

```

After I quit, the /my/dir will be lost but... no problem!
Now I wanna replicate this behaviour in a makefile, I tried the following code but it didn't work:

```

test:
	PATH=$(PATH):/my/dir

```

If I run it, I get:
```

$ make test
PATH=/usr/bin:/usr/sbin:/my/dir
$ echo $PATH
/usr/bin:/usr/sbin

```


Any help will be greatly appreciated. Thanks.

---

### Post by ngmachado on 2008-10-23
Well, 

After reading a bit more on this, and getting no answers here, I might conclude that it's not possible to change the PATH environment variable from a makefile.

Cheers.

---

### Post by dwhitney67 on 2008-10-23
In your Makefile, statements that appear below entry-points (e.g. test) will be executed.  I don't think that is what you want (with respect to setting the PATH).

To set the PATH variable, within the Makefile only, use something like:
```

PATH := $(PATH):/my/dir

test:
        @echo my new PATH = $(PATH)

```

P.S.  The @ symbol is used so that the echo statement itself is not shown on the terminal.

---

