---
title: "BASH - Need help.  Can't script a command w/ space in filename correctly"
date: 2010-05-10
forum: Programming Talk
---

### Post by mjwalfredo on 2010-05-10
I am not able to get this darn command to execute correctly.  I can rename the path for the command to not include spaces but I would rather get this working with the space. Can someone help?

Here are the relevant snippets from my script:

```

#!/bin/bash

DBNAME=PIJC18

CREATEDBPATH='/home/mark/workspace/db2/CreateDB/Solaris\ x86'

"$CREATEDBPATH"/dbcreate -a $DBNAME $DBNAME

```

This errors with:

: line 51: /home/mark/workspace/db2/CreateDB/Solaris\ x86/dbcreate -a PIJC18 PIJC18: No such file or directory

However, if I copy/paste that exact string and execute it from an interactive bash shell, it works.  What am I doing wrong?

---

### Post by mjwalfredo on 2010-05-10
Well, I got the command to work by using the eval command to execute the text.  I still don't understand why my command was not working. I'd still appreciate an explanation.  Thanks.

---

### Post by DaithiF on 2010-05-10
Hi, either enclose in quotes, or use \ to escape the space, but not both.  So:
```
CREATEDBPATH='/home/mark/workspace/db2/CreateDB/Solaris x86'

```or
```
CREATEDBPATH=/home/mark/workspace/db2/CreateDB/Solaris\ x86

```

---

