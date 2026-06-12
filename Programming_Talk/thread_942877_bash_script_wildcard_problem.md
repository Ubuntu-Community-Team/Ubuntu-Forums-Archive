---
title: "bash script wildcard problem"
date: 2008-10-09
forum: Programming Talk
---

### Post by lwnexgen2 on 2008-10-09
Hey Guys-

I am trying to write a bash script that'll check a file for a line of code specified in a different file, and add the specified line of code if it doesn't exist.


The specified line is:

1)
```

*  *    * * *   root    ./usr/bin/mg_backup.sh

```

Since that is all that's in the file, I am running
```

check_line=$(cat filename)

```
to fill check_line with the values, but for some reason, even though "cat filename" works fine and outputs 1), the the value of check_line is a list of all the files in my home directory for some reason. 

I assume this is because there are wildcard characters in my line, so does anyone know how I can get around this?

Thanks!

---

### Post by drubin on 2008-10-09
> **lwnexgen2 said:**
> 
```

*  *    * * *   root    ./usr/bin/mg_backup.sh

```

Since that is all that's in the file, I am running
```

check_line=$(cat filename)

```

I assume this is because there are wildcard characters in my line, so does anyone know how I can get around this?

I dont think the wildcard chars will make a diff in this context.

try this
NOTE: those ` is not a quote but a back tick belove the title char ~
```

check_line=`cat filename`

```

---

### Post by ghostdog74 on 2008-10-09
what do you want to do with the line?

---

### Post by unutbu on 2008-10-09
[PHP]#!/bin/bash
check_line=$(cat filename)
echo "$check_line"
[/PHP]
I think you need quotations marks around the variable.
See [http://newsgroups.derkeiler.com/Archive/Uk/uk.comp.os.linux/2005-08/msg00458.html](http://newsgroups.derkeiler.com/Archive/Uk/uk.comp.os.linux/2005-08/msg00458.html)

---

