---
title: "Help with Python IRC bot :/"
date: 2011-06-12
forum: Programming Talk
---

### Post by Horseboy on 2011-06-12
Here's my source: [http://github.com/FionnK/fIRC-bot](http://github.com/FionnK/fIRC-bot)

I have a few questions.


[LIST=1]
[*]Using the hard-coded "modules" in /core/connect.py, how would I make it get specific data? For example, if I wanted to incorporate a "!say" command followed by some text, how would I get it to say the text after !say?
[*]How do I make it so that !about" (or whatever command) HAS to be executed first? Example: It'd successfully do "!about" but not "sjksbl omg !about diujhbsd".
[/LIST]
After that, I can get to work on a small library ;).

Thanks

---

### Post by TwoEars on 2011-06-12
I want to help, but I'm sorry, I'm not sure what you mean.
Regardless, here's my answers from what I interpreted it as -

1) In order to do both of these, you want to use the re pattern matching module. 
A quick example here - 
```

>>> import re
>>> matches = re.search('(?<=!say ).*','ghhe !say dkk')
>>> matches.group(0)
'dkk'

```

In order to do 2, use match instead of search.

[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

---

### Post by Horseboy on 2011-06-12
> **TwoEars said:**
> I want to help, but I'm sorry, I'm not sure what you mean.
Regardless, here's my answers from what I interpreted it as -

1) In order to do both of these, you want to use the re pattern matching module. 
A quick example here - 
```

>>> import re
>>> matches = re.search('(?<=!say ).*','ghhe !say dkk')
>>> matches.group(0)
'dkk'

```In order to do 2, use match instead of search.

[http://docs.python.org/library/re.html](http://docs.python.org/library/re.html)

Ah thanks, I'll take a look at those docs and recode my bot accordingly. I think that answers both my questions :D

Kudos

---

