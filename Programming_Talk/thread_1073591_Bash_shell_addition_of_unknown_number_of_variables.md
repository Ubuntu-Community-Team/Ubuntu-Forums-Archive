---
title: "Bash shell addition of unknown number of variables"
date: 2009-02-18
forum: Programming Talk
---

### Post by forthekill on 2009-02-18
I am trying to read a set of numbers from a line of a file, and add them up. The issue is I don't know how many numbers might be on a line, only that it won't be more than a certain number, let's say 9.

```
function addUp() {
while read LINE
do
  totalUp $LINE > "/tmp/addedUp"
done
return
}

function totalUp() {
echo "$#, $1, $2, $3, $4, $5, $6, $7, $8, $9!"
sum=0
i=1
while [ $i -lt 10 ]
do
  sum=`expr $sum + **$$i**`
  echo "Sum is: $sum"
  i=`exp $i + 1`
done
echo "$sum"
return
}
```

The problem is getting the right syntax for **$$i**. I'm not sure how I can get it to be $1 in the first run, $2 the second, etc. Can I use cat or something similar?

---

### Post by s1ightcrazed on 2009-02-18
you might be able to use eval to interpret the $i correctly.

---

### Post by stylishpants on 2009-02-18
This is known as 'indirect expansion'. See the bash man page for more info.

```

bob@cob:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

bob@cob:~$ var=PATH

bob@cob:~$ echo $var
PATH

bob@cob:~$ echo ${!var}
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

bob@cob:~$
```

---

### Post by geirha on 2009-02-18
I'd use shift, which removes $1 and shifts all other arguments to the left, so that what was $2 before shift was run, becomes $1 after it's run. So, just loop until $1 is empty
```

totalUp()
{
    sum=0
    while [ -n "$1" ]; do
        sum=`expr $sum + $1`
        shift
    done
    echo "Sum is: $sum"
}

```

---

### Post by stroyan on 2009-02-18
You could do a little trick with array expansion using the first IFS character.  This reads the input numbers into an array and then formats the array with the numbers seperated by '+' characters.  It finally uses 'let' to evaluate the sum.
Be careful putting IFS back to its original value.
```

function addUp() {
 while read -a LINE
 do
  OFS=$IFS
  IFS=+
  let sum="${LINE[*]}"
  IFS=$OFS;
  echo $sum > "/tmp/addedUp"
 done
 return
}

```

---

### Post by ghostdog74 on 2009-02-18
use awk
```

 # more file
1 2 3 4 5
# awk '{for(i=1;i<=NF;i++) s+=i}END{print "sum: "s}' file
sum: 15


```

---

### Post by Yuzem on 2009-02-22
```
totalUp() {
  for i in $* ; do
    result=$((result+i))
  done

  echo "Sum is: $result"
}
```

---

### Post by unutbu on 2009-02-22
```
awk 'BEGIN{ RS=" " }{ s+=$0 }END{print "sum: "s}' file
```

---

