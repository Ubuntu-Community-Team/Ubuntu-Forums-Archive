---
title: "BASH Builtin: No -t Option Available for read in 12.04?"
date: 2014-03-12
forum: Programming Talk
---

### Post by BuntuSeriously on 2014-03-12
Good day, folks.

Here's a "quirk" which seems to be 'buntu-specific':

From a terminal instance in 12.04, "read" will accept option "-t" -- the timeout call -- without issue.  Within any tested script context, however, we get "illegal option -t" when execution reaches "read", _*and that's it*_.  Verified on two completely different machines, two different point releases.

FWIW, during script testing this problem was not in evidence on Parted Magic...

So what's going on here?  Is there a way of getting "read" to accept the -t option in 12.04???


Thanks!

---

### Post by steeldriver on 2014-03-12
Are you sure your script is executing with bash (not, for example, dash)? 

```

$ cat timeout.sh
#!/bin/sh
read -t 2 -p "Enter some text: "
$
$ ./timeout.sh
./timeout.sh: 3: read: Illegal option -t

```

```

$ cat timeout.sh
#!/bin/bash
read -t 2 -p "Enter some text: "
$
$ ./timeout.sh
Enter some text: 

```

---

### Post by BuntuSeriously on 2014-03-13
@steeldriver:

Old habits die hard.  /bin/sh: *"Just say no..."*

FWIW, I was given to understand bash would automagically "step in" when  situations such as this came up, hence the ingrained /sh bang usage.  If known, what's the difference in mechanism between Ubuntu & Parted Magic in this regard?

Thanks; and have a great day :)

---

### Post by steeldriver on 2014-03-13
AFAIK it's just a matter of a symlink - the default for Ubuntu is

```

$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 Jun  1  2013 /bin/sh -> dash

```

but not all distros follow that (for example I've come across source builds that fail because their Makefile assumes /bin/sh is bash). If your Parted Magic is a live CD it will likely follow whatever convention is used in the base distribution.

---

