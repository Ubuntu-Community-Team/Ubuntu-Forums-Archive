---
title: "Regular expressions"
date: 2006-08-05
forum: Programming Talk
---

### Post by mikeym on 2006-08-05
Hi,

I recall someone useing a regular expression to pick out part of a string but I can't find out how they did it. Does anyone know how this was done?

It was something like 

```


echo "qwertyuiop" | grep (or sed or somthing) "ty[[:alpha:]]" -print "%1"


```

This is complete nonsence of course but I'm trying to convay the gyst of what it was doing. In this case printing the first indefinite part of the regular expression. 

In this case it would print "u".

---

### Post by neilp85 on 2006-08-05
Check out the man pages for grep, that should answer your question  more thouroughly than any forum post.

---

### Post by mikeym on 2006-08-05
I think reading the manuals for grep, sed, and awk might be a little over kill for what I am looking for. They are not inexpansive programs. 

I have tried looking through the man page for grep and searched on line for any mention of this but I haven't been able to find any reference to this particular thing.

I thought someone might know.

---

### Post by mikeym on 2006-08-05
Ahh ha! 

Found it! 

For anyone who wants to know the way I was looking for was with 'sed' and it was of the form.


```

echo "onetwothree"| sed -e "s/\(one\)\(two\)\(three\)/\2/" 

```

where this would print 'two'.

I found a great little tutorial on regular expressions [here]("http://gnosis.cx/publish/programming/regular_expressions.html").

---

