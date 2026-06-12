---
title: "recursive line counting."
date: 2010-06-16
forum: Programming Talk
---

### Post by leblancmeneses on 2010-06-16
I found a nice solution to this at the very bottom of this page:
[http://www.unix.com/unix-dummies-questions-answers/33319-recursive-wc-directory.html](http://www.unix.com/unix-dummies-questions-answers/33319-recursive-wc-directory.html)

```


find /topleveldirectory/ -type f -exec wc -l {} \; | awk '{total += $1} END{[print]("http://www.unix.com/#") total}'
```

the problem is I now have a new requirement to remove empty lines from the count.
I wasn't able to edit the exec switch correctly. (syntax errors)


My solution is currently: (supports spaces in directories/files)
```


#!/bin/sh

sum=0
targetdirectory='directory one'

find "${targetdirectory}" -type f -print > exportlist.txt
while read -d $'\n' FILENAME  < exportlist.txt
do
    lines=`cat exportlist.txt | wc -l`
    lines=`expr ${lines} - 1`
    tail -${lines} exportlist.txt > tmp.txt
    mv tmp.txt exportlist.txt
    
    [ ! -f "${FILENAME}" ] && continue

    sum=`expr ${sum} + 1`
    size=`cat "${FILENAME}" | sed '/^\s*$/d' | wc -l`
    sum=`expr ${sum} + ${size}`
done
echo ${sum}


```

although its very slow compared to the referenced code. on ~4 million lines of code. 

Anyone know how to get it working correctly.  At this point just as learning exercise.

---

### Post by trent.josephsen on 2010-06-16
My solution was to -exec grep -v '^$' {} \; and pipe the output to wc -l.

---

### Post by leblancmeneses on 2010-06-16
```


find "New Folder" -type f -exec sed '/^\s*$/d' {} | wc -l  \; | awk '{total += $1} END{print total}'


```

is invalid syntax.


can you show how your handling piping the output.

thanks,

---

### Post by trent.josephsen on 2010-06-16
> **leblancmeneses said:**
> 
```
find "New Folder" -type f -exec sed '/^\s*$/d' {} | wc -l  \; | awk '{total += $1} END{print total}'
```
is invalid syntax.

can you show how your handling piping the output.

You can't pipe the output of an argument to find elsewhere.  Defer the counting until later.

```
find -type f -exec sed '/^\s*$/d' {} \; | wc -l
```

---

### Post by geirha on 2010-06-17
```
find /topleveldirectory/ -type f -exec grep -c . {} \;
```

---

