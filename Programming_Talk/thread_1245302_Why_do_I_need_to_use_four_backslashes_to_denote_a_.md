---
title: "Why do I need to use four backslashes to denote a single backslash"
date: 2009-08-20
forum: Programming Talk
---

### Post by jamadagni on 2009-08-20
Hello. I want to know why, in escape sequences, I have to type four backslashes to denote a single backslash.

For example, if I have to convert:

A\B\C

to

A/B/C

using sed, I have to write:

echo "A\B\C" | sed "s/\\\\/\//g"

Where it is obvious that the first, second and fourth forward slashes are part of the sed s command, the third forward slash is the replacement character, and the backslash before that is to escape this forward slash. The \\\\ serving as the search character is what gets me. Why is it not enough to write \\? Why should I write \\\\?

Please explain. Thanks.

---

### Post by Lux Perpetua on 2009-08-20
Because developers of many different tools, for some reason, seem to have decided that you should write two backslashes to achieve the effect of a single backslash. That means if you chain two of those tools together and require a single backslash at the end of the chain (sed), then (1) sed needs two backslashes to get the effect of one, and (2) at the front of the chain, the shell makes you write two backslashes to get each one of those individual backslashes. Thus, you require 2*2 = 4 backslashes total. 

It could be worse: you could be writing another program to output that shell command, in which case you might need to write *eight* backslashes in a string literal to get those four backslashes, which the shell turns into two when it passes the command to sed, which sed finally treats as a single backslash!

P. S. Backslash is the most common *escape character*, which means it is typically used to begin an *escape sequence*, i. e., a sequence of two or more literal characters that are to be interpreted specially. Unfortunately, that means a single backslash doesn't actually represent a backslash character; a single backslash character actually has to be represented by an escape sequence. *Very* unfortunately, programmers everywhere seem to have decided that the right escape sequence for the backslash is two backslashes, a sequence of two characters that themselves must be represented by escape sequences. So we're stuck in a world where the number of backslashes required to represent a single backslash in a literal increases exponentially with the level of indirection.

---

### Post by slakkie on 2009-08-20
Mind the " and the ' quotes as well:

```

echo "A\B\C" | sed 's#\\#\/#g'

```

---

### Post by jamadagni on 2009-08-21
Thanks, people for explaining, especially Lux! 

@slakkie: I didn't gather what you meant by "mind the quotes". I have been using double quotes for enclosing sed commands (and using \ to escape it wherever it occurs as pure text (without meanings for the command)) -- is there a problem?

---

### Post by slakkie on 2009-08-21
Well, the way the shell works (and other programming languages) is that " expands the variable (the value holding the variable gets printed) and the ' doesn't expands it, so it will print the literal value. 


```

foo="bar"

echo "$foo" # prints bar
echo '$foo' # prints $foo

```

Also escaped values will differ a bit:

```

$ echo '\n'


$ echo '\\n'
\n
$ echo "\n"


$ echo "\\n"


$ echo "\\\n"
\n
$ echo '\\\n'
\

$

# And the example with perl
$ perl
print '\n';
\n$ perl
print "\n";

$


```

So based on using " or ' the shell will interpret escaped characters differently, just like it would with variables. I use the following rule of the thumb, if I need to expand a variable, then I use ", if I don't need to expand a variable, I use the '.

---

### Post by jamadagni on 2009-08-21
That was very clear and very useful to know - I didn't know it before. Thanks Slakkie!

---

### Post by DaithiF on 2009-08-25
I've missed the boat on this thread, but just for the record
```
echo "A\B\C" | sed "s/\\\\/\//g"
```
could be simplified as
```
echo "A\B\C" | sed 's/\\/\//g'
```
ie. no need to double-escape the slashes if your sed expression is in single quotes rather than double.  Which just reinforces slakkies suggestion to use single quotes unless you need to expand a variable, which probably isn't very often when using sed.

---

### Post by Reiger on 2009-08-25
Which can be simplified further to:

```

echo 'A\B\C' | sed 's!\\!/!g'

```

---

### Post by DaithiF on 2009-08-25
and could be even further simplified to:
```
echo 'A/B/C'
```
:P

---

