---
title: "Problems with bash's logical and (-a) operator"
date: 2008-04-13
forum: Programming Talk
---

### Post by AncientPC on 2008-04-13
I'm trying to test two statements within an if conditional statement, but can't get the syntax just right.

Anyway here's the code, the line in question is the long if statement:
```
#!/bin/bash

max=1000;
if [ ! -z $1 ]; then
	max=$1;	
fi

ssh-add ~/.ssh/cs-servers
machines=`cat cshosts.txt`
count=0
for m in $machines; do
	if [ [ $count -le $max ] -a [`ping -s 1 -c 1 $m >/dev/null; echo $?` -eq 0] ]; then
		if [ "$(ssh $m who)" == "" ]; then
			echo "$m"
		fi
		let "count+=1"
	fi
done

exit 0
```

On a side note, what are the bash values for true and false?  For example, I tested "if [ 0 -a 1 ]; then echo "inside if" fi" and the script would evaluate the echo statement.  Using true and false gave the same response.

On a second side note, is there anyway to test that $1 is in fact a number?

---

### Post by colo on 2008-04-13
You might want to try
```

 if ([[ ${count} -le ${max} ]] && ping -s 1 -c 1 "${m}" &>/dev/null); then
   your code
 fi
```

"true" is a return value of zero; "false" is any nonzero return value.

For testing $var being numeric or not:
```
REGEX='^[0-9]+$';
[[ ${var} =~ ${REGEX} ]] && printf '%d is numeric.\n' "${var}"

```
(beware, though: returns false on non-natural numbers.)

---

### Post by WW on 2008-04-13
I just took a look at the bash manpage, and it says that -a is a unary operator for testing whether or not a file exists:
```

      -a file
              True if file exists.

```
Your usage doesn't make sense to me (but maybe I missed something in the manpage).

EDIT: Nevermind; it's in the manpage. :oops:

---

### Post by AncientPC on 2008-04-13
From your post, I realized I could test the argument as a number by using:
```
if [[ $1 =~ [0-9] ]]; then
```

However I'm still having trouble with the syntax of combining test statements and evaluating boolean expressions.

```
#!/bin/bash
if [ 0 -a 0 ]; then
	echo "true"
else
	echo "false"
fi
exit 0
``` evaluates to true

```
#!/bin/bash
if [ 0 -a 1 ]; then
	echo "true"
else
	echo "false"
fi
exit 0
``` evaluates to true

```
#!/bin/bash
$x=1
$y=2
if [ $x -a $y ]; then
	echo "true"
else
	echo "false"
fi
exit 0
``` evaluates to true

```
if [ 0 && 0 ]; then
	echo "true"
else
	echo "false"
fi
exit 0
``` gives me a syntax error: line 6: [: missing `]'

---

### Post by AncientPC on 2008-04-13
> **WW said:**
> I just took a look at the bash manpage, and it says that -a is a unary operator for testing whether or not a file exists:
```

      -a file
              True if file exists.

```
Your usage doesn't make sense to me (but maybe I missed something in the manpage).

From: [http://tille.garrels.be/training/bash/ch07.html](http://tille.garrels.be/training/bash/ch07.html)

[ -a FILE ]	True if FILE exists.
[ EXPR1 -a EXPR2 ]	True if both EXPR1 and EXPR2 are true.

---

### Post by nanotube on 2008-04-13
if you are using actual booleans, rather than conducting a test, don't use [], which is a test operator:

```
#!/bin/bash
if false -a false ; then
	echo "true"
else
	echo "false"
fi
exit 0
```

will give you false, as expected.

to conduct a test:
```
if [ 1 == 1  -a  1 == 0 ]; then echo "true"; else echo "false"; fi
```
will give you a false, again, as expected (of course replace the dummy 1==1 tests with stuff you actually want to test

---

### Post by ghostdog74 on 2008-04-13
> **WW said:**
> I just took a look at the bash manpage, and it says that -a is a unary operator for testing whether or not a file exists:
```

      -a file
              True if file exists.

```
Your usage doesn't make sense to me (but maybe I missed something in the manpage).

which version of bash? -e is supposed to check for file existence and  -a is deprecated. -a is used in an "if/else" statement or "test" to specifiy "and". See[ compound comparison.]("http://tldp.org/LDP/abs/html/comparison-ops.html")
eg
```

if [ -e file -a -z $string ] ; then
...
fi

```

---

### Post by ghostdog74 on 2008-04-13
> **AncientPC said:**
> 
	if [ [ $count -le $max ] -a [`ping -s 1 -c 1 $m >/dev/null; echo $?` -eq 0] ];  

why don't you do it step by step.
```

if count less than max then
   ping 
   check status
   if status equal 0 then
    do something.

```

---

### Post by AncientPC on 2008-04-13
> **ghostdog74 said:**
> why don't you do it step by step.
```

if count less than max then
   ping 
   check status
   if status equal 0 then
    do something.

```

Technically you could break up all and / or statements into nested if / else's, but that kinda defeats the purpose of using and / or to begin with.

---

### Post by WW on 2008-04-13
Instead of this:
[php]
        if [ [ $count -le $max ] -a [`ping -s 1 -c 1 $m >/dev/null; echo $?` -eq 0] ]; then
[/php]
try this:
[php]
        ping -s 1 -c 1 $m >/dev/null
        if [ $count -le $max -a $? == 0 ]; then
[/php]

---

### Post by AncientPC on 2008-04-13
The final working script:
```
#!/bin/bash

max=1000
if [[ -n "$1" && $1 =~ [0-9] ]]; then
	max=$1
else
	echo "Invalid arguments"
	exit 1
fi

ssh-add ~/.ssh/cs-servers
machines=`cat cshosts.txt`
count=0
for m in $machines; do
	if [[ $count -le $max && `ping -s 1 -c 1 $m>/dev/null; echo $?` -eq 0 ]]; then
		if [ "$(ssh $m who)" == "" ]; then
			echo "$m"
			let "count+=1"
		fi
	fi
done

exit 0
```

---

### Post by pfalcon on 2010-12-02
> **nanotube said:**
> if you are using actual booleans, rather than conducting a test, don't use [], which is a test operator:

```
#!/bin/bash
if false -a false ; then
    echo "true"
else
    echo "false"
fi
exit 0
```will give you false, as expected.



Well, I find it worrying that author's original question is ignored, and instead suit-once example are given. Suit-once, because


```
#!/bin/bash
if true -a false ; then
    echo "true"
else
    echo "false"
fi
exit 0
```will give you true, as **UN**expected.



It gives a feeling that few people actually know how bash does things. My try, not necessarily fully correct, is here:
[http://pfalcon-oe.blogspot.com/2010/12/bash-braindeadness-logical-connectives.html](http://pfalcon-oe.blogspot.com/2010/12/bash-braindeadness-logical-connectives.html)


And I post it here because this thread is what google gives on trying to search on the matter, with few other relevant links. So hopefully, people could find additional info in such case.

---

### Post by DaithiF on 2010-12-03
if true -a false

runs the true command, passing in the (redundant) parameters **-a false**  
-a is not special to the shell, its just an argument like any other and gets passed to the preceding command as an argument.  It **only **has significance as a logical and chaining expression for the **test** aka **[** commands (as you correctly point out in your post).  

Your post is incorrect when it says: **"Usage of -a, -o in any other context silently produces undefined result."** -- it would only be undefined if you expected -a / -o to behave as logical operators.  They don't, except (again) for one particular command (**test**).

Consider the command ls -a ... if -a was the logical and operator there would be a problem because there is no second expression, but of course it is not the logical and operator and so ls -a just means that ls gets the parameter -a and modifies its behaviour accordingly (shows all files)

maybe the fact that true and false accept redundant command line arguments without complaining is a legitimate complaint, but to be fair their manpages are explicit about it:

```
NAME
       true - do nothing, successfully

SYNOPSIS
       true **[ignored command line arguments]**

```

```
NAME
       false - do nothing, unsuccessfully

SYNOPSIS
       false **[ignored command line arguments]**

```

Finally, if you wanted to chain two commands with logical and/or in an if statement, then you would do:
[B]if true && false
[/B]and
**if true || false**

---

### Post by pfalcon on 2010-12-04
> **DaithiF said:**
> if true -a false

runs the true command, passing in the (redundant) parameters **-a false**  


Makes sense. Actually, quite obvious ;-). Thanks for clarification!

---

