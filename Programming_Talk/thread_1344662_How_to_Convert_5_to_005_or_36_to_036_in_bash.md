---
title: "How to Convert 5 to 005 or 36 to 036 in bash"
date: 2009-12-03
forum: Programming Talk
---

### Post by 3rag0n on 2009-12-03
The title says it all, please help - I need it to make my comic donwloader script :)

---

### Post by dwhitney67 on 2009-12-03
I've used something like this when renaming JPG files; there's probably a niftier way.  Hopefully someone will weigh in with something better.
```

#!/bin/sh

FILES=`find . -name '*.jpg'`

declare -i i
i=1

for file in $FILES
do
        if [ "$i" -lt "10" ]
        then
                index="00$i"
        elif [ "$i" -lt "100" ]
        then
                index="0$i"
        else
                index="$i"
        fi

        mv $file image$index.jpg

        i=$i+1
done

```

---

### Post by Bachstelze on 2009-12-03
Just use printf. ;)

```
$ a=3; b=`printf "%03d" $a`; echo $b;
003
```

---

### Post by 3rag0n on 2009-12-03
@dwhitney67 : Thanks, but your script turns 36 to 0036 instead of 036. Although in your code, I'd like to suggest that you use the rename command, it renames specific patterns in files.

@Bachstelze: Thanks!!! This works great.

---

### Post by Arndt on 2009-12-03
> **Bachstelze said:**
> Just use printf. ;)

```
$ a=3; b=`printf "%03d" $a`; echo $b;
003
```

$ a=3; num=000$a; echo ${num:${#num}-3:3}
003

(From the man page, I thought ${num:-3:3} would work, but it doesn't.)

---

### Post by falconindy on 2009-12-03
> **Arndt said:**
> $ a=3; num=000$a; echo ${num:${#num}-3:3}
003

(From the man page, I thought ${num:-3:3} would work, but it doesn't.)
It **does** work, but you need to wrap the -3 in parenthesis.
```
[~]$ a=3; num=000$a; echo ${num:(-3):3}
003
```

---

### Post by apmcd47 on 2009-12-03
If it were ksh:
```
$ typeset -Z3 i
$ i=3
$ echo $i
003
$

```
But it's not. I'd go with the printf solution above.

Andrew

---

