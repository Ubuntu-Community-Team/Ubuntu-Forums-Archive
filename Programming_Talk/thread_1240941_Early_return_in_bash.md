---
title: "Early return in bash"
date: 2009-08-15
forum: Programming Talk
---

### Post by matemargo on 2009-08-15
Hi, I'm trying to make a bash script that checks the arguments at the beginning. If they are invalid, it would return with an "exit 1".

This is what I wrote:

```

#!/bin/bash

DIR=$1

[ "$DIR" = "" ] && (echo You have to specify at least one argument; exit 1)
[ -e "$DIR" ] && (echo The given directory does not exist; exit 1)
[ -f "$DIR" ] && (echo You must specify a directory; exit 1)

echo Rest of the script

```

I took the "one line if" examples from this site: [Introduction to if]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_07_01.html")
But even this script doesn't run as expected:
```

[ "$(whoami)" != 'root' ] && ( echo you are using a non-privileged account; exit 1 )

```
When I try it, it shows the error message, but it continues running the rest.

Any ideas?

btw: I'm using 64bits Jaunty

---

### Post by matemargo on 2009-08-15
I've found the answer:

Instead of:
```

[ "$DIR" = "" ] && (echo You have to specify at least one argument; exit 1)

```

It should be:
```

[ "$DIR" = "" ] && { echo You have to specify at least one argument; exit 1; }

```

Besides I've noticed that the second check I should use || instead of &&

---

### Post by geirha on 2009-08-15
You can also check the number of arguments with $#

```

# POSIX
[ $# -gt 0 ] || { echo...

# bash
((!$#)) || { echo...

```

---

