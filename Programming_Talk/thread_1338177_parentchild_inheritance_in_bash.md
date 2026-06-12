---
title: "parent/child inheritance in bash"
date: 2009-11-26
forum: Programming Talk
---

### Post by mo.reina on 2009-11-26
can someone clarify this for me.

AFAIK, any variables in child processes are not passed to the parent.  this includes the value ofvariables in any *do-done* constructs (*while, for, until* loops).  

i've seen this first hand when i started scripting, the values of variables in loops weren't being passed on to the main body of the script.

however, i was writing something today and absentmindedly did this
```
while true; do

        number=$RANDOM
        if (( $number > 100 )) || (( $number == 0 )); then
                continue
        else
                break
        fi
done

**echo $number**

```
and the script actually gave me the value of $number.  what gives?

---

### Post by Arndt on 2009-11-26
> **mo.reina said:**
> can someone clarify this for me.

AFAIK, any variables in child processes are not passed to the parent.  this includes the value ofvariables in any *do-done* constructs (*while, for, until* loops).  

i've seen this first hand when i started scripting, the values of variables in loops weren't being passed on to the main body of the script.

however, i was writing something today and absentmindedly did this
```
while true; do

        number=$RANDOM
        if (( $number > 100 )) || (( $number == 0 )); then
                continue
        else
                break
        fi
done

**echo $number**

```
and the script actually gave me the value of $number.  what gives?

This seems normal. That child processes don't inherit variables is normal too - if you use 'export', they do, however.

What you write about "values of variables in loops weren't being passed on to the main body of the script" seems strange, on the other hand.

---

### Post by mo.reina on 2009-11-26
i think i confused the do-done loops with pipelines, thinking they followed the same rules.

i always close file descriptors with every pipeline and/or command, to avoid inheritance issues.  since the pipelines/commands open sub-shells, i thought that the loops followed the same rule.  don't know how that came about....

---

