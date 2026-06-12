---
title: "Raw strings in Python"
date: 2012-08-17
forum: Programming Talk
---

### Post by kcode on 2012-08-17
So I am having this wierd thing as I am playing around with python regular expressions.

I write:
```
pat = r'href="http://\S+"'
```
and *pat* gets transformed to ```
'href="http://\\S+"'
```

in spite of the fact that I make the pattern string raw!

This is not expected. I am using python 2.7

---

### Post by trent.josephsen on 2012-08-17
What did you expect?

What do you mean it gets "transformed"? That output is exactly what you asked for.

(Try displaying it with 'print' instead of using the auto-echo feature to examine it)

---

### Post by kcode on 2012-08-17
I expect the string not to be manipulated/processed.

I don't want escaping to be done. Raw means : Do not do any processing with back slashes. Let it be there as it is. But the inner back slash gets escaped.

P.S : Watching Nick Parlante's (Google) tutorial on Python RE. He mentions this around 12:30

---

### Post by Vaphell on 2012-08-17
```
>>> a=r'abc\s+'
>>> a
'abc\\s+'
>>> print a, len(a)
abc\s+ 6
```
the string has the right number of characters, in other words everything is fine.

---

### Post by kcode on 2012-08-21
So what is extra \ doing there?

---

### Post by trent.josephsen on 2012-08-21
What are the single quotes doing there? They're not a part of the string either.

---

### Post by kcode on 2012-08-21
> **trent.josephsen said:**
> What are the single quotes doing there? They're not a part of the string either.

Single quotes define a string. I do understand that.

But if I define a string to be raw, then it should be as it is. And it actually *is* as it is, as we see that len(a) == 6 is True.

But when I print, why that extra \? What is its purpose?

---

### Post by snip3r8 on 2012-08-21
> **kcode said:**
> Single quotes define a string. I do understand that.

But if I define a string to be raw, then it should be as it is. And it actually *is* as it is, as we see that len(a) == 6 is True.

But when I print, why that extra \? What is its purpose?
because \ is an escape character and it is printing the string representation that it is pulling from memory. if you weren't  defining the string as raw , you would have had to define that escape character manually anyway. At least thats what i think its doing.

---

### Post by trent.josephsen on 2012-08-21
You don't get an extra \ when you print. Look at Vaphell's example again.

---

### Post by snip3r8 on 2012-08-21
Oh I see thats just output when typing it line by line into the console. I dont see what the fuss is then. I still think my escape character logic applies though

---

### Post by Vaphell on 2012-08-21
developers standarized string 'preview' on non-raw form, where is the problem?
r'\' <=> '\\'

i'll add to my example:
```
>>> list(a)
['a', 'b', 'c', **'\\'**, 's', '+']
```
and don't think for a minute all of these are not characters.

---

### Post by kcode on 2012-08-23
> **snip3r8 said:**
> Oh I see thats just output when typing it line by line into the console. I dont see what the fuss is then. I still think my escape character logic applies though

Thanks, I am convinced. :)

---

