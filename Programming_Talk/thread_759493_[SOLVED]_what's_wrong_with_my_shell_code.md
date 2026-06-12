---
title: "[SOLVED] what's wrong with my shell code"
date: 2008-04-19
forum: Programming Talk
---

### Post by chinayem on 2008-04-19
```
if [ $# -ne 1 ]
then
    echo error
    exit 1
fi

char=$1
numchar=$(echo "$char" |wc -c)

 if [ "$numchar" -ne 2 ]
then
    echo error
    exit1
fi

case "$char"
   in
 [0-9])echo number;;
 [a-z])echo little;;
 [A-Z])echo big;;
  *   )echo special;;
esac

```
when i enter "sh -x ./ctype A" ,terminal show "big"--it right
but if enter " ./ctype A"  ,terminal show "little"--it wrong
i want to know wheather it my ternimal's problem  or the codes'
thanks

---

### Post by ghostdog74 on 2008-04-19
I have the correct results. you can try put #!/bin/bash at the first line of the script. Also you can try 
```

bash -x ./ctype A

```
and see what happens.

---

### Post by sisco311 on 2008-04-19
[COLOR=#000000]> [COLOR=#000000]#!/bin/bash
# Testing ranges of characters.

echo; echo "Hit a key, then hit return."
read Keypress

case "$Keypress" in
  [[:lower:]]   ) echo "Lowercase letter";;
  [[:upper:]]   ) echo "Uppercase letter";;
  [0-9]         ) echo "Digit";;
  *             ) echo "Punctuation, whitespace, or other";;
esac      #  Allows ranges of characters in [square brackets],
          #+ or POSIX ranges in [[double square brackets.

[B] #  In the first version of this example,
#+ the tests for lowercase and uppercase characters were
#+ [a-z] and [A-Z].
#  This no longer works in certain locales and/or Linux distros.
#  POSIX is more portable.[/B]
** #  Thanks to Frank Wang for pointing this out.**

#  Exercise:
#  --------
#  As the script stands, it accepts a single keystroke, then terminates.
#  Change the script so it accepts repeated input,
#+ reports on each keystroke, and terminates only when "X" is hit.
#  Hint: enclose everything in a "while" loop.

exit 0[/COLOR][http://tldp.org/LDP/abs/html/testbranch.html#EX29](http://tldp.org/LDP/abs/html/testbranch.html#EX29)
[/COLOR]

---

### Post by chinayem on 2008-04-19
@ghostdog
```
 bash -x ./ctype A
+ '[' 1 -ne 1 ']'
+ char=A
+ case "$char" in
+ echo little
little
```
```
 sh -x ./ctype A
+ [ 1 -ne 1 ]
+ char=A
+ echo big
big
```
why they are different? 
to the codes the second is right

---

### Post by ghostdog74 on 2008-04-19
see sisco311's post.

---

### Post by sisco311 on 2008-04-19
> **chinayem said:**
> @ghostdog
```
 bash -x ./ctype A
+ '[' 1 -ne 1 ']'
+ char=A
+ case "$char" in
+ echo little
little
``````
 sh -x ./ctype A
+ [ 1 -ne 1 ]
+ char=A
+ echo big
big
```why they are different? 
to the codes the second is right

In your first example the scrip is interpreted by bash. In the second is interpreted by sh. In bash the [a-z] and [A-Z] doesn't work. You must use [:lower:] and [::upper:] which works in both (bash and sh)..

---

### Post by chinayem on 2008-04-19
oh.i see!
thanks very much!

---

