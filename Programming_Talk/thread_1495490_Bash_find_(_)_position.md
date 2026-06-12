---
title: "Bash find \( \) position"
date: 2010-05-28
forum: Programming Talk
---

### Post by dragos2 on 2010-05-28
How can I position the exclude \( $e \) for the script to work ?

```

#!/bin/bash

# I exclude 3 directories from search
e="! -name one_ ! -name another* ! -name third*"

cd /some/path || exit
for dir in *; do
 find /some/path \( $e \) -type d -name $dir  -mindepth 2 -maxdepth 3
done

```The error is:
```

find: warning: you have specified the -maxdepth option after a non-option argument (, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

```

---

### Post by trent.josephsen on 2010-05-28
This is what we have manpages for.

```
$ man find
```

(Hint:  It has nothing to do with the apparently superfluous parentheses.)

---

### Post by dragos2 on 2010-05-28
> **trent.josephsen said:**
> This is what we have manpages for.

```
$ man find
```(Hint:  It has nothing to do with the apparently superfluous parentheses.)

I changed the order of the parameters and there are no errors but I can still see the folders
I want to exclude as output. Why ?

---

### Post by trent.josephsen on 2010-05-28
> **dragos2 said:**
> I changed the order of the parameters and there are no errors but I can still see the folders
I want to exclude as output. Why ?

Can you post the exact command line?

Bang characters (!) *usually* have special meaning to bash, and I just realized that your script isn't escaping them.  I've never seen it in this exact context before, though, so it may be correct -- my bash isn't what it should be.

---

### Post by geirha on 2010-05-28
What are you actually trying to do with that script?

---

### Post by gmargo on 2010-05-28
> **dragos2 said:**
> 
```

find: warning: you have specified the -maxdepth option after a non-option argument (, but options are not positional (-maxdepth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.

```

The warning message told you exactly what to do.  Move the "-mindepth 2 -maxdepth 3" to just after /some/path, and before any -name arguments. (If you just move the -maxdepth, then you get the same warning for -mindepth, so move both.)

---

