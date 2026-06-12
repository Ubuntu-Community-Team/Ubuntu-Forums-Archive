---
title: "Why is this script working? [BASH]"
date: 2011-07-08
forum: Programming Talk
---

### Post by neur0 on 2011-07-08
I was reading a book on shell scripting and found this example:

```

#!/bin/sh
pattern="$1"
shift
echo "Matching against '$pattern':"
for string
do
case $string in
$pattern) echo "$string: Match." ;;
*) echo "$string: No match." ;;
esac
done

```

This little script works as expected and accepts multiple arguments, but how does it substitute the values of the "STRING" variable when "shift" is not inside the loop? 
I am new to shell scripting but I just hate it when I find something that works and I don't know why it works. No troubleshooting can give me an answer to this one so I thought I try the forums. Also, using "for" without some kind of a list/array is poorly documented on the internet.

---

### Post by geirha on 2011-07-08
When you omit the **in words** part, it assumes **in "$@"**. Run **help for** in an interactive bash shell to see the syntax.

Out of curiosity, which book is it?

---

### Post by gmargo on 2011-07-08
from the **dash(1)** man page:
```

     The syntax of the for command is

           for variable [ in [ word ... ] ]
           do   list
           done

     The words following in are expanded, and then the list is executed repeatedly with the variable set to each
     word in turn.  Omitting in word ... is equivalent to in "$@".

```So your 'for string' is the same as 'for string in "$@"', which expands to all the remaining command line arguments.

---

### Post by Bachstelze on 2011-07-08
From the zsh manual, I expect Bash works the same way:

>        for name ... [ in word ... ] term do list done
              where term is at least one newline or ;.  Expand the list of words, and set the parameter name
              to  each  of them in turn, executing list each time.  [b]If the in word is omitted, use the posi-
              tional parameters instead of the words.[/b]


---

### Post by neur0 on 2011-07-09
Ah,
Thanks for those answers, I understand it now.

It from the "Beginning Portable Shell Scripting: From Novice to Professional" btw

---

### Post by geirha on 2011-07-09
> **neur0 said:**
> Ah,
Thanks for those answers, I understand it now.

It from the "Beginning Portable Shell Scripting: From Novice to Professional" btw

Aha, in that case this thread's title is misleading. Based on the title on that book, it most likely teaches you to write sh scripts, not bash scripts.

---

