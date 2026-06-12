---
title: "python syntax help"
date: 2012-01-07
forum: Programming Talk
---

### Post by ilikelinuxitisthebest on 2012-01-07
Hey guys. Im a beggining python programmer and i want to make a mesurment converter i. e. how many inches in a foot. but when i try to run it, it says invalid syntax. heres my code ```
from sys import argv

input, output, = argv


if input = "Feet" and output = "Inches" print "12"
```

---

### Post by epicoder on 2012-01-07
```
input, output, = argv
if input = "Feet" and output = "Inches" print "12"
```Both of these lines have incorrect syntax, and even if they were correct, I doubt they'd do what you want.

First off, the first line has an extra comma after output. Even after this is corrected, it will always fail if your program has more or less than one argument. This is because unpacking will throw an error if there are more values in the list/tuple/etc. than variables to unpack to. Also, the first value of argv is the name of the script, not an argument. To get the first and second arguments of the script, use these lines.
```

from sys import argv
try:
    arg1=argv[1]
    arg2=argv[2]
except IndexError: #Not enough arguments.
    print "You must pass in at least 2 arguments."
    exit(1)

```The second line doesn't have a colon after the if statement. This will always throw an error even if the statement to execute is on the next line and properly indented. Also, = will throw an error because it is the assignment symbol, not the comparison symbol. Use == instead.
```

if arg1=="Feet" and arg2=="Inches": print "12"

```Here is the program you are trying to write in pseudocode, handling feet, inches, and yards. I will leave translating it to python as a challenge for you.
```

try {
    arg1=arguments[1].lowercase()
    arg2=arguments[2].lowercase()
} except NotInArray {
    print "Not enough arguments."
    exit(1)
}

#These are all in terms of inches.
units=array(
    "inches" = 1,
    "feet" = 12,
    "yards" = 36
)

try {
    print units[arg2]/units[arg1]
} except NotInArray {
    print "Invalid units."
    exit(1)
}

```

---

### Post by holiday on 2012-01-07
> **ilikelinuxitisthebest said:**
> Hey guys. Im a beggining python programmer and i want to make a mesurment converter i. e. how many inches in a foot. but when i try to run it, it says invalid syntax. heres my code ```
from sys import argv

input, output, = argv


if input = "Feet" and output = "Inches" print "12"
```

Interesting strategy the assignment of the arg list to a list variable. However you have a a syntactical error from the start. 

The '=' operator is an assignment token. For evaluation you need '=='. 

Fixing that and using your strategy, I'd try this:

[input,output] = argv

Worth a shot. Please report back.

If that doesn't work then use an indexed access:

input = argv[1]
output = argv[2]

(argv[0] is the call to python) 

And then you have to go with :

if input == 'Feet' and output == 'Inches' :
..print '12'

Indentation is a token in Python. The forum software is removing spaces at first of line so replace the dots with spaces.

---

### Post by Arndt on 2012-01-07
> **holiday said:**
> Interesting strategy the assignment of the arg list to a list variable. However you have a a syntactical error from the start. 

The '=' operator is an assignment token. For evaluation you need '=='. 

Fixing that and using your strategy, I'd try this:

[input,output] = argv

Worth a shot. Please report back.

If that doesn't work then use an indexed access:

input = argv[1]
output = argv[2]

(argv[0] is the call to python) 

And then you have to go with :

if input == 'Feet' and output == 'Inches' :
..print '12'

Indentation is a token in Python. The forum software is removing spaces at first of line so replace the dots with spaces.

It doesn't if you enclose it in code tags.

---

### Post by holiday on 2012-01-07
> **Arndt said:**
> It doesn't if you enclose it in code tags.

Ah! Thanks for that, Arndt.

---

### Post by d3v1150m471c on 2012-01-07
```

from sys import argv
var,foo=argv

```

you can do this for sequential items in an array as well.

---

### Post by cgroza on 2012-01-07
> **d3v1150m471c said:**
> ```

from sys import argv
var,foo=argv

```you can do this for sequential items in an array as well.
I may have misunderstood your post, but argv is an array.

---

### Post by d3v1150m471c on 2012-01-07
> **cgroza said:**
> I may have misunderstood your post, but argv is an array.

```

>>> var=[1,2,3]
>>> a,b,c=var
>>> print(a,b,c)
(1, 2, 3)

```

:-). the problem is not his assignment, rather his bitwise operation.

---

### Post by d3v1150m471c on 2012-01-07
s/bitwise/comparison. i've been working on too much crypto lately. anyways, here is a link that will probably serve you well in the future. [http://www.tutorialspoint.com/python/python_basic_operators.htm](http://www.tutorialspoint.com/python/python_basic_operators.htm)

---

### Post by ilikelinuxitisthebest on 2012-01-08
Thanks guys. you were all very helpful in this post and i believe i will be finishing my program soon.

---

### Post by ilikelinuxitisthebest on 2012-01-09
Also it would be a lot more efficient if you used elif instead of if.

---

### Post by mssever on 2012-01-10
> **ilikelinuxitisthebest said:**
> Also it would be a lot more efficient if you used elif instead of if.
elif may be more efficient, but it isn't a lot more efficient. In most cases, the difference would be insignificant.

---

