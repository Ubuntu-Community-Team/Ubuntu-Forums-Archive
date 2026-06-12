---
title: "[SOLVED] Sed removeing new lines"
date: 2008-09-12
forum: Programming Talk
---

### Post by WitchCraft on 2008-09-12
Hi, question about sed:

I have a list of mail addresses.
I want to add a ; at the end of each line, and remove the new line character.

I got it working, but I have a question:

When you remove new line characters, I would have supposed you can do it with at least one of these:
```

sed 's/\n//'
or
sed 's/\n//g'
or
sed 's/\r//'
or
sed 's/\r//g'

```

But this doesn't work.
Doing a tr -d '\012' works with the same effect...

Now I searched the internet and found
```

sed ':a;N;$!ba;s/\n//g'

```
which works

Now i seee the ":a;N;$!ba" added. 
What is the meaning of these commands?
Why does it not just work with 's/\n//g' ?

---

### Post by ghostdog74 on 2008-09-12
> **WitchCraft said:**
> 
Why does it not just work with 's/\n//g' ?
sed works on one line at a time and ignores the newline, therefore you can't match the newline. you need to add the new line to the buffer so that \n can be matched.

---

### Post by WitchCraft on 2008-09-13
> **ghostdog74 said:**
> 
sed works on one line at a time and ignores the newline, therefore you can't match the newline. you need to add the new line to the buffer so that \n can be matched.

Ah, interesting, thanks.

So, typically sed operates on one line at the time,
:a is a label for a location in the sed script, like in BASIC you hava goto a, in sed you have ba, i.e. branch to a if some condition is satisfied
N means append the contents of the next line to the current one (including the \n newline)
$!ba means branch to location in the sed script labelled with label a, while or untill the last line has not been reached.

---

