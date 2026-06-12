---
title: "problem in bash script"
date: 2010-11-18
forum: Programming Talk
---

### Post by oren tal on 2010-11-18
I have written a script and I get error and I don't understand why.
```

neededParameters=2
numOfParameters=0
correctNum=0
while getopts "s:l:" opt
do
    case "$opt" in
    s)
        serviceName= $OPTARG #errorline 1
        numOfParameters= $numOfParameters + 1
        ;;
    l)
        fileName= $OPTARG #errorline 2
        numOfParameters= $numOfParameters + 1    
        ;;
    ?)
        echo "unknown option"
        ;;
    esac
done

```when I run:
script -s s -l l
Then I get error message on errorlines 1 and 2 that it doesn't recognize s and l.

I would be really glad for an help.
Thanks in advance.

---

### Post by jpl888 on 2010-11-18
Did you try removing the quotes from ```
"s:l:"
```?

---

### Post by gmargo on 2010-11-18
FIxed addition and removed space:

```

neededParameters=2
numOfParameters=0
correctNum=0
while getopts "s:l:" opt
do
    case "$opt" in
    s)
        serviceName=$OPTARG
        numOfParameters=$(($numOfParameters + 1))
        ;;
    l)
        fileName=$OPTARG
        numOfParameters=$(($numOfParameters + 1))
        ;;
    ?)
        echo "unknown option"
        ;;
    esac
done

```

---

### Post by oren tal on 2010-11-21
> **gmargo said:**
> FIxed addition and removed space:

```

neededParameters=2
numOfParameters=0
correctNum=0
while getopts "s:l:" opt
do
    case "$opt" in
    s)
        serviceName=$OPTARG
        numOfParameters=$(($numOfParameters + 1))
        ;;
    l)
        fileName=$OPTARG
        numOfParameters=$(($numOfParameters + 1))
        ;;
    ?)
        echo "unknown option"
        ;;
    esac
done

```
Thanks.

---

