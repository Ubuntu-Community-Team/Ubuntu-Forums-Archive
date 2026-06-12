---
title: "Is there anything in Python which is equivalent to &quot;$$&quot; in PHP"
date: 2007-02-06
forum: Programming Talk
---

### Post by 3togo on 2007-02-06
I am very new to python and would like to ask whether there is anything equivalent in python that could work like "$$" in PHP.

Many thanks.

3togo


<?php
error_reporting(E_ALL);

$name = "Christine_Nothdurfter";
// not Christine Nothdurfter
// you are not allowed to leave a space inside a variable name ;)
$$name = "'s students of Tyrolean language ";

print " $name{$$name}<br>";
print  "$name$Christine_Nothdurfter";
// same
?>

---

### Post by duff on 2007-02-06
for those of us that know python, but not php, what does the $$ do?

**edit:**
are you dereferencing a variable to get the name of another variable?  if so, ```
>>> s='x'
>>> exec s+"=3"
>>> print x
3

```

---

### Post by clouserw on 2007-02-07
No, the $$ is creating a variable from the value of another.  Meaning:

```

<?php
$var = "testo";

$$var = "I like pudding.";

echo $testo; // Prints "I like pudding" to the screen
?>

```

I don't know python, but to the OP:  Please don't do this unless you have a very good reason and you document it well.  Supporting code like that is a nightmare.

---

### Post by gpolo on 2007-02-07
Hmm.. I don't know if I'm doing good posting an answer to this, there are ways to avoid what you want. But..

```

var = "testo"
exec("%s = '%s'" % (var, "I like pudding"))
print testo

```

Somewhat trickie, but does what you want

---

### Post by ssam on 2007-02-07
thats probably not a great style to code in.can you trust that $var is not the name of a variable you are already using?

see if you can solve the problem using dictionaries.

```

var = "testo"
my_dict = {} # make an empty dictionary
my_dict[var] = "I like pudding"
print my_dict["testo"]

```

---

