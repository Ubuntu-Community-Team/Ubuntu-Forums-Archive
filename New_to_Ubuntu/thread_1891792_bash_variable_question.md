---
title: "bash variable question"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by Diametric on 2011-12-06
Hello,

What is the difference between setting a variable without {}

```
var=123

echo $var

123
```

and with curly braces?  I can't seem to figure out how this could be interpreted differently in a script.

Thanks!

---

### Post by papibe on 2011-12-07
Hi Diametric.

Could you post an example where the curly braces make no difference?

Where the curly braces be would be?

It is something like this?
```
var=123

echo $var456


echo ${var}456
123456
```
Regards.

---

### Post by Diametric on 2011-12-07
I guess what I'm trying to determine is what is the difference in how bash could operate on how a variable is called

```
var=123

echo var

123
```

or if the variable is called like this:

```
echo ${var}

123
```

Does that make sense?  

Thanks!

---

### Post by mcduck on 2011-12-07
As far as I know, it makes no difference in your example. But that's mainly because the only thing you have in the brackets is the variable itself. However the syntax with brackets can be used for changing and extending the variables, which you wouldn't be able to do as easily without them.

For example:
```
echo ${username-`whoami`}
```
this will check if the variable *$username* is set, and if it isn't sets set it to the result of *whoami*

Read here for more:
[http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion]("http://www.gnu.org/software/bash/manual/bashref.html#Shell-Parameter-Expansion")
[http://www.dcc.fc.up.pt/~nam/aulas/0102/ic/material/abs-guide/parameter-substitution.html#PARAMSUBREF]("http://www.dcc.fc.up.pt/~nam/aulas/0102/ic/material/abs-guide/parameter-substitution.html#PARAMSUBREF")

edit: It actually seems that the brackets are optional, but recommended for keeping the parameter from mixing with any following characters. "The parameter name or symbol to be expanded may be enclosed in braces, which are optional but serve to protect the variable to be expanded from characters immediately following it which could be interpreted as part of the name. "

---

### Post by papibe on 2011-12-07
> **Diametric said:**
> 
Does that make sense?  

Not really.

I think you meant the difference between something like:
```
echo $var
echo ${var}
```
Both with using the $, right?

In that example there won't be difference, but I know a couple of cases in which does.

First is the case that I used on my previous example. If you want to print the variable and add a suffix string, you can use the braces to assure bash recognize the variable name. Example:
```
var=123
echo $var456
# prints a black line because the variable var456 does not exist.

echo ${var}456
# prints 123456
# in this case bash knows you are substituting the value of var,
# and then pasting the trailing '456' 
```
The other case is very similar but related to positional parameters. Let's say you have an script than is called with at least 10 parameters:
```
#!/bin/bash
echo $10
```
If you call it like this:
```
./caca a b c d e f g h i j

```
It will print a0 since bash assumes just one digit for positional parameters. You can solve that by using braces:
```
#!/bin/bash
echo ${10}
```
That will print the 10th parameter: j

Does that help?
Regards.

---

### Post by Diametric on 2011-12-08
Papibe,

That absolutely gets at what I was asking about - thank you!  And yes, there was a typo in my previous post where I forgot to include the $, so I can see how it didn't make sense.  

Thank you for taking the time to explain that for me, it was very helpful.

Cheers!

---

