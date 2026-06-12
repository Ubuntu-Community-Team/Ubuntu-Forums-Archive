---
title: "script debugging help"
date: 2006-11-15
forum: Programming Talk
---

### Post by jman623 on 2006-11-15
Hi all whenever I try to run frostwire I get this syntax error from runFrost.sh, i don't know much about shell scripting so I was wondering if one of you would be willing to help out.



```
 44: Syntax error: "(" unexpected (expecting "}")

```


here is the syntax for line 44 in the script:

```
  potential_java_dirs=(`ls -d1 "$JAVADIR"/j* | sort | tac`)
```

any help would be greatly appreciated.

thanks in advance :)

---

### Post by po0f on 2006-11-15
jman623,

Maybe the line should be:
```
potential_java_dirs=(`ls -d1 "$JAVADIR/j*" | sort | tac`)
```

---

### Post by jman623 on 2006-11-15
Nope same error but thanks anyways if you or anyone else have any other suggestions let me know:)

---

### Post by po0f on 2006-11-15
jman623,

Maybe try reinstalling it?  Brute force tends to work nicely in these kinds of situations.  :)

To diagnose the script as is, you're going to have to post more of it.  Ten lines before and after the offending line should help out more.

---

### Post by dataw0lf on 2006-11-16
Replace the first line '#!/bin/sh' or whatever to '#!/bin/bash' (or sudo vim `which frostwire` and switch 'sh runFrost.sh' to 
'bash runFrost.sh').  I believe this has been addressed previously in the forums, so in the future be sure to use the Search tool, and you'll save alot of time. :)

---

