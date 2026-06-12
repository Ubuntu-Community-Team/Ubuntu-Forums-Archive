---
title: "How do I get the full path of a shell script?"
date: 2007-07-30
forum: Programming Talk
---

### Post by piers on 2007-07-30
I've built a script which needs to work on files that are in the same directory as it, for example

**running**
*~$ /var/myscripts/thisscript.sh*

**would return**
*Path to thisscript.sh is /var/myscripts/thisscript.sh*

How can I get the script to output its own path?

I've been googling and have found the solution for PHP, Ruby, Python, Applescript, VBScript and ColdFusion but not for shell script!!!

---

### Post by jyba on 2007-07-30
```
#! /bin/bash

echo "Path to $(basename $0) is $(readlink -f $0)"
```

---

### Post by piers on 2007-07-30
Thanks jyba!! You saved my bacon.

Its nice to see another Cornish Ubuntu user aswell!

---

### Post by vanyatka on 2011-04-22
> **jyba said:**
> ```
#! /bin/bash

echo "Path to $(basename $0) is $(readlink -f $0)"
```

Not available on MacOS

```
barcelona:mem-cs2-wrapper xman$ readlink -f ./lp.out

readlink: illegal option -- f

usage: readlink [-n] [file ...]
```

---

### Post by stchman on 2011-04-22
This has worked for me.

```

#!/bin/bash

SCRIPT=$(readlink -f "$0")
SCRIPTPATH=`dirname "$SCRIPT"`

echo $SCRIPTPATH

```

The quotes around the $0 and $SCRIPT help it deal gracefully with directory names with white space.

---

