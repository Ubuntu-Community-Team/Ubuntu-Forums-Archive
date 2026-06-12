---
title: "Bash conditionals"
date: 2008-03-11
forum: Programming Talk
---

### Post by Mevsthevoices on 2008-03-11
I was wondering if bash has some way of comparing 1 string to many others using logical OR
Say like
if [ "$readvar" = 'y' || 'Y' ];then
     echo 'Yay'
fi

Would it be ok to use square brackets? say
if [ "$readvar" = [yY] ];then
     echo 'Yay
fi

---

### Post by mssever on 2008-03-11
You can use limited regex functionality, but if you do this, you must use #!/bin/bash, not #!/bin/sh.
```
if [[ "$somevar" =~ [yY] ]]; then
  #do stuff
fi
```I'm not 100% positive of the syntax, but it's similar.

EDIT: You could also keep it basic and so something like
```
if [ "$somevar" = y -o "$somevar" = Y ]; then
  #do stuff
fi
```
-o means or. -a means and. ! means not

---

### Post by ghostdog74 on 2008-03-11
use case, more neat, IMO
```

case $variable in 
y|Y ) echo "yes ";;
esac

```

---

### Post by Mevsthevoices on 2008-05-05
Thanks that worked perfect

---

