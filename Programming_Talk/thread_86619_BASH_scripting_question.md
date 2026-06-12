---
title: "BASH scripting question"
date: 2005-11-05
forum: Programming Talk
---

### Post by NewWithoutClue on 2005-11-05
Hey, sup?
Question, if i may:
In Visual Basic there is a statement "ON ERROR RESUME NEXT", this statement basically does what it says it does: skips an error causing line of code and continues with the current flow of logic ( for the current sub or function ).
Now, i want to know of a equivlent for BASH. Does one exist? if not, know any tricks?

Thanks,
Paul.

---

### Post by 23meg on 2005-11-05
AFAIK in bash error causing lines will be skipped by default. Errors will only be handled if you write error handlers that instruct bash to terminate the script (error_exit) or do something else.

---

### Post by NewWithoutClue on 2005-11-05
[QUOTE=23meg]AFAIK in bash error causing lines will be skipped by default. Errors will only be handled if you write error handlers that instruct bash to terminate the script (error_exit) or do something else.[/QUOTE]

```
#!/bin/bash
# error, uh huh.
iamfunction()
}

echo "look at me! all functiony"

embeddedfunctionality()
{
echo "w00t w00t"
}

}
embeddedfunctionality
# i know that after calling the second functions owning function that i would be able to call the second function
# woot.

```

Output:
```
point@cytrex:~/Desktop$ ./erroriam
./erroriam: line 14: embeddedfunctionality: command not found
point@cytrex:~/Desktop$

```

I don't like the looks of this! Is there a way to avoid seeing such nasty outputs?
like, o lets say, something equivlent to VB's "ON ERROR RESUME NEXT"?

Thanks,
Paul.

---

### Post by 23meg on 2005-11-06
I'm not familiar with VB but if you just want to suppress the error message, redirecting output to /dev/null should help.

---

### Post by NewWithoutClue on 2005-11-07
[QUOTE=23meg]I'm not familiar with VB but if you just want to suppress the error message, redirecting output to /dev/null should help.[/QUOTE]

Thanks. 
For anyone else who wants to know...you can redirect stdout only if an error occurs ( if you choose, of course ) using 
```
2>/insert/your/destination/here
```

0=stdin, 1=stdout and 2=stderr
FYI.

w00t,
Paul.

---

