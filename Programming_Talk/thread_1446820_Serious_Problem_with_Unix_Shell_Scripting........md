---
title: "Serious Problem with Unix Shell Scripting......."
date: 2010-04-04
forum: Programming Talk
---

### Post by hakermania on 2010-04-04
Hi.....:(
I made this prog:
```

#!/bin/sh
 echo "What is your age?"
 read DIKIAMOU
 if [ $DIKIAMOU -lt 0 ]; then
 echo "pff you don't say the truth!!!!"
elif [ $DIKIAMOU -ge 120 ]; then
echo "N000 you are lier"
else
echo "Your age is $DIKIAMOU. How old is your sister??"
read HLIKIADERFHS
if [ $HLIKIADERFHS -lt 0 ]; then 
echo "You are wrong or your sister is propably not born yet..."
elif [ $HLIKADERFHS -ge 120 ]; then
echo "She is too big to tell the truth.."
else
echo "Your sister is $HLIKIADERFHS years old!"
fi
fi
```
This script seems to have a problem...See the result after the execution:
```
alex@maD-pc:~/Desktop$ ./prog4
What is your age?
1
Your age is 1. How old is your sister??
1
[: 18: -ge: unexpected operator
Your sister is 1 years old!
```
I cannot understand which is the #@!%@! problem!!!! :'(

---

### Post by Cracauer on 2010-04-04
You should always quote variables like that

```

[ "$myvar" -lt 55 ] && yupp

or

[ -n "myvar" ] && yepp


```

That way an empty string stays an empty string, it doesn't disappear, in the former case causing a syntax error.

---

### Post by km0r3 on 2010-04-04
[s]Shouldn't this line:

```
elif [ $HLIKADERFHS -ge 120 ]; then
```Look like this:

```
elif [ $HLIKADERFHS -gt 120 ]; then
```?
[/s]
**@falconindy**:
OK, I was wrong.

---

### Post by falconindy on 2010-04-04
> **km0r3 said:**
> Shouldn't this line:

```
elif [ $HLIKADERFHS -ge 120 ]; then
```

Look like this:

```
elif [ $HLIKADERFHS -gt 120 ]; then
```

?
From `man 1p test`:
```
       n1 -ge  n2
              True if the integer n1 is algebraically greater than or equal to the integer n2.
```
I don't know Greek, but I can plainly see that HLIKIADERFHS is the variable read in, and HLIKADERFHS is the variable compared in the elif. Not the same spelling.

---

### Post by hakermania on 2010-04-05
Ok thx guys!

---

