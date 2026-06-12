---
title: "shell script to delete some files"
date: 2010-08-04
forum: Programming Talk
---

### Post by tapas_mishra on 2010-08-04
I am writing a shell script to delete some files but not all.
the file names are development23
if they are in home directory of user then I do not want them to be deleted.
So I am trying

find / -name development23
the logic that I want to try is 

(if [ ! `dirname $i` = "/home" ]; then ...)

but putting a for loop for above I am not clear as how will I take the reults of find for doing above in a script.

---

### Post by Some Penguin on 2010-08-04
'find' has boolean operators as well as negation.  Then use xargs.

---

### Post by tapas_mishra on 2010-08-04
My mistake what I want to ask is.
Suppose you execute a command such as ls -l
it will display some thing.
Now for each line displayed.
I would like to do some thing with that individual lines.
Is it some how possible in a shell script to take them,
in different variables.

---

### Post by ghostdog74 on 2010-08-04
```

#!/bin/bash
shopt -s nullglob
for file in *.extension
do
   echo "do something  to $file"
done

```

---

### Post by tapas_mishra on 2010-08-04
Wow!!!
:o
I learned some thing new but I looked at man page of shopt it did not exist.
Tell me what does shopt do and use of nullglob here ?

---

### Post by ghostdog74 on 2010-08-04
> **tapas_mishra said:**
> Wow!!!
:o
I learned some thing new but I looked at man page of shopt it did not exist.
Tell me what does shopt do and use of nullglob here ?

look at man bash.

---

