---
title: "how to get first n lines of a file"
date: 2007-03-08
forum: Programming Talk
---

### Post by monkeyking on 2007-03-08
i have some huge text files.
But while I test and develop, I want some small files.

So I want a way to "cat" the first n-lines to another file.
There must be some nice linux command tools for this.

Thanks in advance

---

### Post by 23meg on 2007-03-08
Check out* head*.

---

### Post by monkeyking on 2007-03-08
YES!

thanks,
this is excatly what I needed :)

---

### Post by 23meg on 2007-03-08
You're welcome. For future reference, the *apropos* command is helpful when you know what you want to do, are sure some command does it, but aren't sure which one. Try this:

```
apropos first lines 
```

And don't forget the forum search.

---

### Post by LotsOfPhil on 2007-03-09
You could also do 

sed -n 1,Np file.txt > newfile

That will put the first N lines in newfile.

---

### Post by LotsOfPhil on 2007-03-09
head is a lot faster than sed, so... I am just babbling, I guess.

---

