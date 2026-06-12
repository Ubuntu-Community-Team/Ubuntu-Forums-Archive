---
title: "bash scripting options double semicolon"
date: 2017-02-26
forum: Programming Talk
---

### Post by macnux on 2017-02-26
Hi
I have a small question about bash scripting
this is the snippet I'm asking about

```
#!/bin/bash
echo
while [ -n "$1" ]
do
case "$1" in
-a) echo "Found the -a option" ;;
-b) echo "Found the -b option" ;;
-c) echo "Found the -c option" ;;
*) echo "$1 is not an option" ;;
esac
shift
done
```
I got this from a tutorial [https://likegeeks.com/linux-bash-scr...e-guide-part3/](https://likegeeks.com/linux-bash-scr...e-guide-part3/)

Why do we need double semicolon after each option 
I tried to remove the semicolon it gives me this error

```
syntax error near unexpected token `)'
```
thanks in advance.

---

### Post by steeldriver on 2017-02-26
That usage is specific to the case ... esac construct AFAIK - it's equivalent to the `break` statement in a C switch ... case expression

From `man bash`:

```

                         If the ;; operator is used, no subsequent matches are
              attempted after the first pattern match.

```

Without it, bash probably tried to execute the following `-b)` as part of the expression list belonging to case `-a)`

---

### Post by macnux on 2017-02-26
thank you for help

---

