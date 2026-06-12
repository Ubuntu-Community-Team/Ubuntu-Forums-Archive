---
title: "Regular expression help"
date: 2009-02-05
forum: Programming Talk
---

### Post by cdekter on 2009-02-05
I need a bit of help getting this regular expression working correctly.

I'm using the regex to split a string, for example:

"This is a string <stuff>+<stuff>+<more> asdf"

Currently my regex is: "(<.*>\+?)"

However running the string through the regex yields:

['This is a string ', '<stuff>+<stuff>+<more>', ' asdf']

and what I actually want is:

['This is a string ', '<stuff>+', '<stuff>+', '<more>', ' asdf']

That is, I want to split at any occurence of a token like <stuff> or <stuff>+

Any advice greatly appreciated.

---

### Post by jespdj on 2009-02-05
In which programming language? Many programming languages have regular expressions, but they're not the same in all programming languages.

Here's a good website with lots of information about regular expressions in many different programming languages:
[http://www.regular-expressions.info/](http://www.regular-expressions.info/)

---

### Post by cdekter on 2009-02-05
This is in Python... I have read much material on regexes but the trick is synthesizing the information to solve the actual problem I'm having. I'll keep trying but if someone out there already knows the answer it can save me a lot of time :)

Edit: I've ended up with this: "(<.+?>\+{0,1})" 

Seems to work :)

---

