---
title: "Bash variable"
date: 2009-09-27
forum: Programming Talk
---

### Post by Levo on 2009-09-27
My script uses the "read" command for user input. But when I set a wine path (e.g.: "c:\") it only gets this: "c:". If I write "c:\\" it gets "c:\" (which is what I want). How can this be done (type "c:\" and get "c:\")?

---

### Post by DaithiF on 2009-09-27
use ```
read -r
```

from man bash:

              -r     Backslash  does  not  act  as an escape character.  The backslash is
                     considered to be part of the line.  In particular, a  backslash-new&#8208;
                     line pair may not be used as a line continuation.

---

### Post by Levo on 2009-09-27
> **DaithiF said:**
> use ```
read -r
```

from man bash:

              -r     Backslash  does  not  act  as an escape character.  The backslash is
                     considered to be part of the line.  In particular, a  backslash-new&#8208;
                     line pair may not be used as a line continuation.

This doesn't really work. If I type "c:\" I get "c:\". But if I type something like "c:\asd\" I get "c:sd\".

---

### Post by DaithiF on 2009-09-27
works for me:
```
read -r somevar && echo $somevar

```
c:\asd\    <-- input
c:\asd\    --> output
what shell are you executing this script with?  the above works under bash, doesn't seem to work under dash (or /bin/sh which is a symlink to dash).  
Try a shebang of #!/bin/bash on the first line of the script to make sure it executes under bash.

---

### Post by Levo on 2009-09-27
> **DaithiF said:**
> works for me:
```
read -r somevar && echo $somevar

```
c:\asd\    <-- input
c:\asd\    --> output
what shell are you executing this script with?  the above works under bash, doesn't seem to work under dash (or /bin/sh which is a symlink to dash).  
Try a shebang of #!/bin/bash on the first line of the script to make sure it executes under bash.

You are right, it works under bash. I executed it with sh. Thanks!

---

