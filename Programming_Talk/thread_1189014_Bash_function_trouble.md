---
title: "Bash function trouble"
date: 2009-06-16
forum: Programming Talk
---

### Post by neugen on 2009-06-16
Hello all! Given the following code:

```

#!/bin/bash

function foo()
{
 if [ "$1" -gt 5 ];then
    #this is considered an error
    exit 192
 else
    echo "OK"
 fi
}

declare -i NUMBER=$(($RANDOM % 10))

#first call of foo
#prints OK only if $NUMBER is less than 5
foo "$NUMBER"


#the following is executed only if $NUMBER is less than 5
NUMBER=6
#second call of foo
OUTPUT=`foo "$NUMBER"`

#the following is executed every time
echo "Why is this executed every time??"

```

Can someone please explain to me what happens at the second call of foo? Why the execution of the script continues after the second call ??

---

### Post by geirha on 2009-06-16
Because when you do
```
OUTPUT=`foo "$NUMBER"`
```
foo is run in a subshell, and when foo calls exit, it exits the subshell instead of the "main" shell.

---

### Post by neugen on 2009-06-16
Thanks for your answer! Is there any way this can be avoided ( to force the exit from the "main" shell as well )... besides the obvious solution when you check the output:
```

if [ -z "$OUTPUT" ];then
   #some  error occured
   exit 192
else
   #do something here
   :
fi

```

---

### Post by geirha on 2009-06-16
Yes, you can check the return value ($?).
```

OUTPUT=`foo 6`
if [ $? -eq 192 ]; then
    exit 192
then

```

Alternatively, it can be done a bit shorter, by exiting with the same value as the function (unless the return value is 0).

```

for i in {1..10}; do
    OUTPUT=`foo $i` || exit $?
    echo "$i: $OUTPUT"
done

```

---

### Post by neugen on 2009-06-16
Thanks a lot for your support! This was really helpful for me!

---

