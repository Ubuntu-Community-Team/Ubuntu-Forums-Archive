---
title: "Help with SED and variables containing &amp;"
date: 2014-09-23
forum: Programming Talk
---

### Post by cbillson on 2014-09-23
I hope someone can help as this one is driving me up the wall and i'm not sure how to fix it.

myfile:-[INDENT]
----
agent-name
------[/INDENT]
 
```


myvar=test&test

sed -i "s/agent-name/$myvar/g" /mydir/myfile
[INDENT] [/INDENT]

```

results in:

[INDENT]testagent-nametest
[/INDENT]
I expected:

[INDENT]test&test[/INDENT]

I've tried single quotes - resulted in $myvar

I also tried both \ and \\ in front of $myvar

Can anyone help me with how to format a sed statement if the variable contains & ?

Thanks
Chris

---

### Post by cbillson on 2014-09-23
I've found a way via experimentation, though appreciate thoughts if this is a good way or if there are better

```


VAR1="$(echo "$myvar" | sed 's/&/\\&/g')"

sed -i "s/agent-name/$VAR1/g" /mydir/myfile


```

---

### Post by Lars Noodén on 2014-09-23
That's one way.  Another way is like this:

First, you'll want the value of $mytest in quotes to avoid the shell processing & as it is a control operator and will put the preceding sequence of commands into the background.  In your example, there just happens to be a program in the system called "test"  If you had used another value the error would have been obvious.  

```

myvar='test&test'

```

Second, you'll want to escape any symbols that sed might act upon.  Again, & is one of them.  So what you really want when assigning a value to $myvar would be this:

```

myvar='test\&test'

```

---

### Post by cbillson on 2014-09-23
Thanks for this, i'm sorry, I should have expanded on what i'm doing, i'm using a for loop and $myvar is coming from a text file

---

### Post by Vaphell on 2014-09-23
care to show the code? for loops and files in general should not be used together.

btw you don't have to use pipe to sed to do simple substitutions on a variable, bash can do that
```
sed -i "s//${var//&/\\&}/g"
```

---

