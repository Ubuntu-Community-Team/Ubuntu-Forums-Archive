---
title: "Assignment to a variable variable."
date: 2011-03-17
forum: Programming Talk
---

### Post by nikefalcon on 2011-03-17
This loop is part of a bash script which takes multiple arguments.
```

for ((i=1;i<=$number;++i)) ; do 
    offset=$(($i+5))     
    url$i=${!offset}     
    echo $url1     
done

```I get the following error-"./test2: line 6: url1=URLf1: command not found".

Note: "URLf1" is one of the arguments passed to the script.

Any ideas as to how to work around this??

Thanks

---

### Post by Arndt on 2011-03-17
> **nikefalcon said:**
> This loop is part of a bash script which takes multiple arguments.
```

for ((i=1;i<=$number;++i)) ; do 
    offset=$(($i+5))     
    url$i=${!offset}     
    echo $url1     
done

```I get the following error-"./test2: line 6: url1=URLf1: command not found".

Note: "URLf1" is one of the arguments passed to the script.

Any ideas as to how to work around this??

Thanks

I haven't looked up the order of evaluation in the bash man page, but obviously, it thinks that url$i=xxx is a command and not an assignment. You can use 'eval':

```
eval url$i=${!offset}
```

Not that in general you then need to be careful with the right-hand side of =, as it will essentially be evaluated twice.

---

### Post by nikefalcon on 2011-03-17
Thank You, eval works perfectly.
So it now reads:
```

for ((i=1;i<=$number;++i)) ; do
    offset=$(($i+5))
    eval url$i=${!offset}
    ltemp=url$i
    URL=${!ltemp}
    echo CHECK$URL    
done

```

---

