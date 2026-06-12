---
title: "Bash Abuse"
date: 2009-11-05
forum: Programming Talk
---

### Post by Freelance Physicist on 2009-11-05
So, occasionally, I like to write programs in inefficient ways just to watch the computer thrash around (especially if the code becomes rather obfuscated in the process (I don't know what's wrong with me)).  Anyway, I decided to write a recursive Fibonacci number calculator in BASH like so:

```
#!/bin/bash

# Takes one integer argument ($1) and returns "$1"th Fibonacci number

if [ $1 -lt 1 ] # return zero for arguments less than one
then
	echo 0
	exit
fi

if [ $1 -lt 3 ] # the first and second Fibonacci numbers are 1
then 
	echo 1
	exit
fi

a=$1 # store argument in $a
echo $(( $($0 $((--a))) + $($0 $((--a))) ))
##          ^      ^          ^     ^
##          fib.sh ^         fib.sh ^
##                 ^ decrement $a   ^ decrement $a (again)
exit
```

This is saved as fib.sh.  As you can see, for each level of recursion, two new process of fib.sh is run (in other words, don't try to find the 40th Fibonacci number with this program), the first with $a-1, the second with $a-2--or, so I thought.  I thought that $((--a)) decrements the value of a before returning its value.  It ends up that both of the $((--a)) return the same number.  For example, if I run this as $ ./fib 4, the final command translates to 
```
echo $(( $(./fib.sh 3) + $(./fib.sh 3) ))
```

instead of

```
echo $(( $(./fib.sh 3) + $(./fib.sh 2) ))
```

and I end up having to use

```
echo $(( $($0 $((--a))) + $($0 $((--a-1))) ))
```

instead (mush less elegant).

However, if I run the following commands on the command line:

```
$ a=5
$ echo $((--a)) $((--a))
```
"4 3" is returned as expected.

Am I missing something, or could this be a bug in bash?

---

### Post by falconindy on 2009-11-05
Why not use --a and a-- ?

---

### Post by jpkotta on 2009-11-06
The $() is creating a subshell, and the $a in that shell is local to it.  Thus the script's shell can't see the changes.

```

$ echo $BASH_SUBSHELL
0
$ echo $(echo $BASH_SUBSHELL)
1
$ echo $(($BASH_SUBSHELL))
0

```

---

### Post by Freelance Physicist on 2009-11-06
Thanks, jpkotta.  That makes sense.  Too bad, using $((--a)) twice would have been sneakier than $((a-1)) and $((a-2)).  Ah, well.

@falconindy: It's like the c++ operators.  $((--foo)) decrements foo then returns its value.  $((foo--)) returns the value of foo then decrements it.

```
foo=5
echo $((--foo)) $((foo--))
```

The returns "4 4" and leaves the value of $foo at 3.  I need the decremented value in both cases.

---

### Post by Sockerdrickan on 2009-11-06
> **Freelance Physicist said:**
> So, occasionally, I like to write programs in inefficient ways just to watch the computer thrash around

I LoL'd irl.

---

