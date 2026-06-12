---
title: "Question about regular expression with Python"
date: 2007-08-22
forum: Programming Talk
---

### Post by triptoe on 2007-08-22
hey

I am trying to take a number like "192368"

and divide it up into numbers 3 digits long with every possible sequence. for instance

192, 923,236, 368         ... etc

when i try

pattern = "[0-9]{3}"

it finds 192 and 368 instead... it doesn't overlap witht he 923. how do i get it to do that?

---

### Post by Soybean on 2007-08-22
I'm a bit of a regular expression noob, but my sense of regular expressions suggests that this might not be possible. Do you have any particular reason to believe that it can be done?

A trivial example of why I think it won't work:
Say I have the string "superman", and I want to match both "sup" and "uper" in a single regex. The only way I can picture doing that is like so:
```
[COLOR="Red"]([/COLOR]s[COLOR="Blue"]([/COLOR]up[COLOR="Red"])[/COLOR]er[COLOR="Blue"])[/COLOR]man
```
But, of course, the parser isn't going to see my color coding, and it's going to return "super" and "up". Parentheses can be nested, but can't really overlap. In your case you aren't explicitly specifying parentheses, but I think the situation is analogous.

There may still be a way with a single expression, but I would think you might have more luck with some sort of loop. For example, find the *first* set of 3 consecutive digits, then start from one character past the beginning of the match, and do the same expression again.

So with "192368" you would find "192", then do the same regex on "92368" and get "923", then use "2368", etc. I believe that cutting down a string like that is pretty easy in Python, and if I recall correctly, a match from a Python regular expression can even tell you where in the string it was found. Although, if your input is always going to be a number, with no non-numerical characters, you can just drop one character from the beginning each time.

---

### Post by AZzKikR on 2007-08-22
> **triptoe said:**
> it finds 192 and 368 instead... it doesn't overlap witht he 923. how do i get it to do that?

Interesting question. This is the first time I am wondering about it myself. As of your problem, I guess it can be solved pretty easily. Something like:

```
num = 19232155678
strnum = str(num)

idx = 0 
for zoit in strnum:
    if idx < len(strnum) - 3: 
        print strnum[idx:idx+3]
        idx += 1

```

Should do the trick.

---

### Post by ghostdog74 on 2007-08-22
```

>>> import re
>>> a="1923684"
>>> re.findall("\d{,3}", a)
['192', '368', '4', '']

```

---

### Post by AZzKikR on 2007-08-22
Read the OP's question again dude, the result of your regex is not what he requested.

---

### Post by ghostdog74 on 2007-08-22
> **AZzKikR said:**
> Read the OP's question again dude, the result of your regex is not what he requested.

```

>>> a = "192368"
>>> re.findall("(?=(\d{3}))",a)
['192', '923', '236', '368']

```

---

### Post by triptoe on 2007-08-22
Hey sweet... both nice solutions... thanks!

---

