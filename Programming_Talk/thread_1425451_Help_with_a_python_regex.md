---
title: "Help with a python regex"
date: 2010-03-09
forum: Programming Talk
---

### Post by aquavitae on 2010-03-09
I am trying to write a regular expression (in python) which will match a certain string once, or twice with an underscore between. E.g.:
'a2' or 'a2_b4', but not 'a2_' or 'a2b4'. 
The simplest I've managed so far is ```
'[a-z]\d_[a-z]\d|[a-z]\d'
``` but I'm sure there's got to be a tidier way of doing this. Also, the string I'm matching is more complicated than 'a2', so I really don't want to have it appearing 3 times in the full expression. Any suggestions?

---

### Post by Some Penguin on 2010-03-09
Presumably you mean to match a *pattern* twice if separated by an underscore, because 'a2' and 'b4' are not the same string.

You could make it *slightly* terser as

'pattern(_pattern)?'

but you're still going to need repetition.

---

### Post by DaithiF on 2010-03-09
i guess you could construct the re using a variable for the pattern which is repeated:
```
>>> tests
['a2', 'a2_b4', 'a2_', 'a2b4']
>>> pattern='[a-z]\d'
>>> r = re.compile(r'\b%s(_%s)?$' % (pattern, pattern))
>>> [ t for t in tests if r.match(t) ]
['a2', 'a2_b4']
```

---

### Post by __init__ on 2010-03-09
> **DaithiF said:**
> i guess you could construct the re using a variable for the pattern which is repeated.

It's a bad taste, you can sometimes format regexp when some parts of it is unknown at the time of coding, for example, if you want to inject a person's name or site address in the search pattern. But in this case it's just unnecessary obfuscation, [a-z]\d(_[a-z]\d)? is a completely normal regexp, there is nothing bad about it.

---

### Post by DaithiF on 2010-03-09
> **__init__ said:**
> But in this case it's just unnecessary obfuscation, [a-z]\d(_[a-z]\d)? is a completely normal regexp, there is nothing bad about it.
The OP did say "Also, the string I'm matching is more complicated than 'a2', so I really don't want to have it appearing 3 times in the full expression. Any suggestions?"

---

### Post by __init__ on 2010-03-09
> **DaithiF said:**
> The OP did say "Also, the string I'm matching is more complicated than 'a2', so I really don't want to have it appearing 3 times in the full expression. Any suggestions?"

Ok, if pattern is *really* complex, this would look better, I presume.
```
re.compile(r'{0}(_{0})?'.format(r'[a-z]\d'))
```

I just wanted to say that regexps is always completely unreadable and there are no any means to change this situation. Hopefully, there usually no need to "read" regexp, you write and debug it once, and then attach comment to it describing in plain words which strings it is meant to match.

---

### Post by aquavitae on 2010-03-09
Thanks for all the advice. The only problem is that I get this (python 2.5):
```

>>> pattern='[a-z]\d'
>>> re.findall(r'%s(_%s)?' % (pattern, pattern), 'a2_')
['']
>>> re.findall(r'%s(_%s)?' % (pattern, pattern), 'a2_b4')
['_b4']

```

Also, which I probably should have said earlier, I'm searching for the pattern within a longer string, so \b and $ won't give the right results. So in fact, it should also match 'gga2' -> 'a2' and 'a2_b4_f' -> 'a2_b4'

---

### Post by __init__ on 2010-03-09
> **aquavitae said:**
> Thanks for all the advice. The only problem is that I get this (python 2.5):
```

>>> pattern='[a-z]\d'
>>> re.findall(r'%s(_%s)?' % (pattern, pattern), 'a2_')
['']
>>> re.findall(r'%s(_%s)?' % (pattern, pattern), 'a2_b4')
['_b4']

```

If regexp contains at least one group, findall returns a list of groups matched, and parenthesis is actually a grouping operator. (?: ... ) is a non-grouping kind. Try this:
```
[a-z]\d(?:_[a-z]\d)?
```

---

### Post by DaithiF on 2010-03-09
at the risk of dismaying anyone who may need to look at your code in the future :)
```
>>> tests
['a2', 'a2_b4', 'a2_', 'a2b4', 'gga2', 'a2_b4_f']
>>> r = re.compile(r'(?<!%s)%s(?:_%s)?(?!%s|(?<!_%s)_)' % ( pattern, pattern, pattern, pattern, pattern))
>>> for t in tests:
...   print "%s => %s" % ( t, r.findall(t))
... 
a2 => ['a2']
a2_b4 => ['a2_b4']
a2_ => []
a2b4 => []
gga2 => ['a2']
a2_b4_f => ['a2_b4']

```

---

### Post by aquavitae on 2010-03-09
> **DaithiF said:**
> at the risk of dismaying anyone who may need to look at your code in the future :)
```
>>> tests
['a2', 'a2_b4', 'a2_', 'a2b4', 'gga2', 'a2_b4_f']
>>> r = re.compile(r'(?<!%s)%s(?:_%s)?(?!%s|(?<!_%s)_)' % ( pattern, pattern, pattern, pattern, pattern))
>>> for t in tests:
...   print "%s => %s" % ( t, r.findall(t))
... 
a2 => ['a2']
a2_b4 => ['a2_b4']
a2_ => []
a2b4 => []
gga2 => ['a2']
a2_b4_f => ['a2_b4']

```
Scary stuff...

I've got to rush off now, but I'll give the ?: suggestion a try tomorrow.  I've just discovered that my requirements are a lot more complicated than I previously thought so I'll post back with the full problem once I've thought it through.

---

### Post by diesch on 2010-03-09
A little bit shorter (and with some additional test cases):
```

>>> tests = ['a2', 'a2_b4', 'a2_', 'a2b4', 'gga2', 'a2_b4_f', 'a2_b4gg', 'a2gg', 'a2_gg', 'gga2_']
>>> pattern=r'[a-z]\d'
>>> r = re.compile(r'((?<!%s)%s(?:_%s|(?!%s|_)))' % (pattern, pattern, pattern, pattern))
>>> for t in tests:
...   print "%s => %s" % ( t, r.findall(t))
... 
a2 => ['a2']
a2_b4 => ['a2_b4']
a2_ => []
a2b4 => []
gga2 => ['a2']
a2_b4_f => ['a2_b4']
a2_b4gg => ['a2_b4']
a2gg => ['a2']
a2_gg => []
gga2_ => []

```

---

### Post by aquavitae on 2010-03-10
Thanks. using ?: worked. And it turns out the extra complication wasn't so complicated after all, I just had to find a few more matches further on in the string, just digits so the regex was easy.  Thanks for all the help!

---

