---
title: "`expr` shell script problem"
date: 2009-08-17
forum: Programming Talk
---

### Post by colau on 2009-08-17
```

#!/bin/bash
a=8
b=7

if [ $b -ge $a ] ; then
	echo "b is greater= $b"
else
	echo "a is greater= $a"
fi

`expr $b=$b+1`
echo $b

```
./script.sh
```

./script.sh: line 11: 7=7+1: command not found

```

---

### Post by Arndt on 2009-08-17
> **colau said:**
> ```

#!/bin/bash
a=8
b=7

if [ $b -ge $a ] ; then
	echo "b is greater= $b"
else
	echo "a is greater= $a"
fi

`expr $b=$b+1`
echo $b

```
./script.sh
```

./script.sh: line 11: 7=7+1: command not found

```

```
b=`expr $b + 1`
```

does what you want. Run "expr $b=$b+1" by hand to see what's wrong with it.

---

### Post by hyperAura on 2009-08-17
if ur shell is Bourne-compatible then try this

b=`expr $b + 1`

---

### Post by colau on 2009-08-17
> **Arndt said:**
> ```
b=`expr $b + 1`
```

does what you want. Run "expr $b=$b+1" by hand to see what's wrong with it.
Still not working.
[php]
#!/bin/bash
a=8
b=7

if [ $b -ge $a ] ; then
	echo "b is greater= $b"
else
	echo "a is greater= $a"
fi

b=`expr $b+1`

echo $b
[/php]

Output:
```

a is greater= 8
7+1

```
I want to print 
```

a is greater= 8
8

```

---

### Post by abhilashm86 on 2009-08-17
try this, you'll get the result.......
```
#!/bin/bash
a=8
b=7

if [ $b -ge $a ] ; then
    echo "b is greater= $b"
else
    echo "a is greater= $a"
fi

echo ` expr  $b + 1 `

```
output
```


abhilash@abhilash:~$ sh a.sh
a is greater= 8
8

```

---

### Post by colau on 2009-08-17
> **abhilashm86 said:**
> try this, you'll get the result.......
```
#!/bin/bash
a=8
b=7

if [ $b -ge $a ] ; then
    echo "b is greater= $b"
else
    echo "a is greater= $a"
fi

echo ` expr  $b + 1 `

```
output
```


abhilash@abhilash:~$ sh a.sh
a is greater= 8
8

```

Is there any way to save the result of **`expr $b + 1`** to a variable(saving with that expr command)?

---

### Post by Tibuda on 2009-08-17
> **colau said:**
> Is there any way to save the result of **`expr $b + 1`** to a variable(saving with that expr command)?

variablename=`expr $b + 1`

---

### Post by colau on 2009-08-17
> **danielrmt said:**
> variablename=`expr $b + 1`
After ./script.sh
```

a is greater= 8
./script.sh: line 11: 8: command not found

```
```

#!/bin/bash
a=8
b=7

if [ $b -ge $a ] ; then
    echo "b is greater= $b"
else
    echo "a is greater= $a"
fi

var= `expr $b + 1`
echo $var

```

---

### Post by stroyan on 2009-08-17
In bash you can use

let b=$b+1
or
let b+=1
or
b=$(($b+1))
or
((b+=1))

to increment b.

---

### Post by colau on 2009-08-17
> **danielrmt said:**
> variablename=`expr $b + 1`
The problem is here[COLOR="Red"]**(extra space)**[/COLOR]:
```

#!/bin/bash
a=8
b=7

if [ $b -ge $a ] ; then
    echo "b is greater= $b"
else
    echo "a is greater= $a"
fi

var[COLOR="Red"]**= `e**[/COLOR]xpr $b + 1`
echo $var

```

Correct code:
[php]
#!/bin/bash
a=8
b=7

if [ $b -ge $a ] ; then
    echo "b is greater= $b"
else
    echo "a is greater= $a"
fi

var=`expr $b + 1`
echo $var
[/php]

---

### Post by colau on 2009-08-17
> **stroyan said:**
> In bash you can use

let b=$b+1
or
let b+=1
or
b=$(($b+1))
or
((b+=1))

to increment b.
Or
b=$[$b+1]

---

### Post by stroyan on 2009-08-17
> **colau said:**
> Or
b=$[$b+1]

"man bash" does warn that-
"The old format $[expression] is deprecated and will be removed in upcoming versions of bash."

---

### Post by colau on 2009-08-17
> **stroyan said:**
> "man bash" does warn that-
"The old format $[expression] is deprecated and will be removed in upcoming versions of bash."
Difficult to find here:
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
Can you reference the particular area to search?

---

### Post by stroyan on 2009-08-17
> **colau said:**
> Difficult to find here:
[http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)
Can you reference the particular area to search?
Have a look at [http://manpages.ubuntu.com/manpages/hardy/man1/bash.1.html#toptoc11](http://manpages.ubuntu.com/manpages/hardy/man1/bash.1.html#toptoc11) under Arithmetic Expansion.

---

### Post by colau on 2009-08-17
> **stroyan said:**
> Have a look at [http://manpages.ubuntu.com/manpages/hardy/man1/bash.1.html#toptoc11](http://manpages.ubuntu.com/manpages/hardy/man1/bash.1.html#toptoc11) under Arithmetic Expansion.
Thank you.
Got this.
> 
Arithmetic Expansion

        Arithmetic  expansion allows the evaluation of an arithmetic expression and the substitution of the result.  The format for  arithmetic  expansion is:
 
$((expression))
 
The  old  format  $[expression]  is  deprecated  and will be removed in upcoming versions of bash.


---

