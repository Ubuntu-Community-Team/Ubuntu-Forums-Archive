---
title: "[BASH] little confuse"
date: 2009-10-06
forum: Programming Talk
---

### Post by play05 on 2009-10-06
Hai guys! 
I confuse with my on bash script.Getting error with it :confused:
Taking hour try to fix it but still cant see which one is the problem.
What the script should do is taking 10 user input and then search which one is the biggest'
After that print out the biggest one.

#! /bin/bash

count=0
biggest=0
value=10

while [$count -lt $value];
do
echo "Enter number"
read INTG
if [$INTG -gt $biggest];
then
 biggest=$INTG
fi
$count++
done
echo "The biggest number is: $biggest"

So can i use $count++ in bash.I know in C we can use it. :(

---

### Post by scragar on 2009-10-06
Doesn't work in bash because $count is evaluated first. Instead you have to manually specify the addition:
```
count=$(( $count + 1 ))
```

---

### Post by kaibob on 2009-10-06
Also, I believe you have to have a space after [ and before ]. For example

```
if [ $INTG -gt $biggest ]
```

With the above change, and the change suggested by scragar, the script works for me.

---

### Post by scragar on 2009-10-06
> **kaibob said:**
> Also, I believe you have to have a space after [ and before ].

Ooh, yes, it's also a nice idea to double up
```
while [[ $count < $value ]];
```
And make the code a bit easier to read.

---

### Post by play05 on 2009-10-06
Thanks guy for quick reply :lolflag:
Really helping me and it work 

So this is the code after i fix it as you all told me.

#! /bin/bash

count=0
biggest=0
value=10

while [ $count -lt $value ];
do
echo "Enter number"
read INTG
if [ $INTG -gt $biggest ];
then
 biggest=$INTG
fi
count=$(( $count + 1 ))
done
echo "The biggest number is: $biggest"

---

### Post by scragar on 2009-10-06
> **play05 said:**
> Thanks guy for quick reply :lolflag:
Really helping me and it work 

So this is the code after i fix it as you all told me.

```
#! /bin/bash

count=0
biggest=0
value=10

while [ $count -lt $value ];
do
echo "Enter number"
read INTG
if [ $INTG -gt $biggest ];
then
 biggest=$INTG
fi
count=$(( $count + 1 ))
done
echo "The biggest number is: $biggest"
```

Can I please post my minimised version now? Please?
```
#!/bin/bash

MAX=0 ## obviously we set the max
for x in {1..10}; do ## we set up a foreach loop since it's easier to write :p
  echo "Enter a number:"
  read INTG
  [[ $INTG > $MAX ]] && MAX=$INTG ## if the numbers higher we update our count
done
echo "The biggest number is: $MAX"

```:p

---

### Post by play05 on 2009-10-06
Wow!
Haha..i guess your want much more better than me,Scragar :)
Simple,short and easy to read.

But i still wondering why u put :
[[ INTG > MAX ]] **&&** MAX=$INTG

For my understanding,&& means AND right.
Can u please explain little bit about tour code there. :confused:


I'm a newbie in bash and want gains more knowledge about it :KS

---

### Post by scragar on 2009-10-06
Think of every line as a command to run, each command can return 3 kinds of output, it's return status(success or failure), STDOUT(standard output) and STDERR(standard error).
When evaluating the return status of the line it's quite simple, bash is smart, think of it like this:
A || B
Bash knows that if A is true it never needs to work out B, the line will return true anyway, so it doesn't work it out. The same logic is applied to and:
A && B
if A is false there's no way the line can return true, so it never even looks at B.

Taking advantage of that you can throw multiple parts on the same line and chain them together depending on each other:
[[ $INTG > $MAX ]] &&
if it's true so far then we check if the next part is true(which involves running it), otherwise we ignore it(so it's not run at all).

Don't abuse this functionality btw, for the most part you want an IF condition, it's easier to read and easier to expand on.

---

