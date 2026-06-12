---
title: "BASH: Passing result of boolean expression to a function"
date: 2010-01-10
forum: Programming Talk
---

### Post by demonGeek on 2010-01-10
I'd like to evaluate a boolean expression and pass the result as a parameter to a function.  Here's the code I have so far:  

```
dayOfMonth=$( (date +%-d) )
[ $dayOfMonth = 10 ]
MyFunction "$?"
```The code above works but I'd really like to combine the boolean expression and the function call into a single line so that it looks something like this (which doesn't work):

```
MyFunction "[ $dayOfMonth = 10 ]"
```Any help would be appreciated.

 - Adam

---

### Post by croto on 2010-01-10
How about changing the double quotes by backticks?
```

MyFunction `[ $dayOfMonth = 10 ]`

```

EDIT: My suggestion does not work, you need the exit code, not stdout.

---

### Post by slakkie on 2010-01-10
I don't think that is possible.

You could do it ala

bla=$( [ 0 -eq 0 ] ; echo $?)
your_func $bla

which would become: 

your_func $([ 0 -eq 0 ] ; echo $?)

but that's the same as doing what you are currently doing. I would keep your current version.

---

### Post by jpkotta on 2010-01-10
> **croto said:**
> How about changing the double quotes by backticks?
```

MyFunction `[ $dayOfMonth = 10 ]`

```

EDIT: My suggestion does not work, you need the exit code, not stdout.

Return status of the last command is $?.  Zero means OK/true/no error.

```

false ; echo $?
[ 0 = 0 ] ; echo $?

```

---

### Post by demonGeek on 2010-01-10
Thanks for the help everyone.

Slakkie:  Your suggestion worked out for me - it's ugly but it does the job:

```

dayOfMonth=$( (date +%-d) )
MyFunction "$([ $dayOfMonth = 10 ];echo $?)"

```

---

