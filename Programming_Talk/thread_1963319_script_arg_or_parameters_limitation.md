---
title: "script arg or parameters limitation"
date: 2012-04-22
forum: Programming Talk
---

### Post by jao_madn on 2012-04-22
Hi,

I would like to ask some info on the script arguments/parameters. Does script arguments had limitation like inside or deep inside the loop in which it will not function as it use to be.

as an example: 
$2 not working
```

command2 () {
for log in $LOG{1,2,3}
    do
    if [ -e $log ] && [ -s $log ]; then
    echo
    echo BEGIN $log
    grep -E "$DATE" $log | grep -E "$2"  2> $SCRIPT
    echo
    echo END $log
    echo
    fi
    done
}
```

$2 need to declare as another variable to work

```

par2=echo $2
command2 () {
for log in $LOG{1,2,3}
    do
    if [ -e $log ] && [ -s $log ]; then
    echo
    echo BEGIN $log
    grep -E "$DATE" $log | grep -E "$par2"  2> $SCRIPT
    echo
    echo END $log
    echo
    fi
    done
}
```

---

### Post by gmargo on 2012-04-22
Inside a shell function, the positional parameters ($1, $2, $3, etc) refer to arguments passed to the function.

It is only outside of a function body that $1, $2, $3 etc refer to command line parameters.

Prove it to yourself with a simple script like this:
```

#!/bin/sh

print_some_args()
{
    echo "f1 = $1"
    echo "f2 = $2"
    echo "f3 = $3"
}

echo "a1 = $1"
echo "a2 = $2"
echo "a3 = $3"
print_some_args alpha beta charlie

```Now suppose you called that script "foo.sh"; now run the shell script like this:
```

$ sh foo.sh a b c
a1 = a
a2 = b
a3 = c
f1 = alpha
f2 = beta
f3 = charlie

```

---

### Post by jao_madn on 2012-04-22
> **gmargo said:**
> Inside a shell function, the positional parameters ($1, $2, $3, etc) refer to arguments passed to the function.

It is only outside of a function body that $1, $2, $3 etc refer to command line parameters.

Prove it to yourself with a simple script like this:
```

#!/bin/sh

print_some_args()
{
    echo "f1 = $1"
    echo "f2 = $2"
    echo "f3 = $3"
}

echo "a1 = $1"
echo "a2 = $2"
echo "a3 = $3"
print_some_args alpha beta charlie

```Now suppose you called that script "foo.sh"; now run the shell script like this:
```

$ sh foo.sh a b c
a1 = a
a2 = b
a3 = c
f1 = alpha
f2 = beta
f3 = charlie

```

@gmargo: thanks, very much appreciated, you just save me some time digging/reading in the advance shell script guide about functions.

---

