---
title: "Python Code Question..."
date: 2009-02-13
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-13
Example-1:>>> '"Yes," he said.'
'"Yes," he said.'

Example-2:>>> "\"Yes,\" he said."
'"Yes," he said.'

I just started using Python and above is an example they give. I was just wondering Why would you use the slashes in example 2 because it adds 2 more characters to type and you get the same result as in example 1? So why would you use the longer method? 

Thanx for the answers in advance...

P.S. I have read that in programing you should learn proper spelling. I understand this but does that mean I should not use abbreviations or slang at all so I can break that habit if I want to become a serious coder?

LOL ROFLMAO Thx Thanx...etc.

---

### Post by Wybiral on 2009-02-13
Example:
```

'"That\'s why," he said.'

```

---

### Post by Leo Dragonheart on 2009-02-13
>>> 'str' [COLOR="Red"].strip() +[/COLOR] 'ing'       # <- This is ok
'string'

In this statement why is the ".strip() +" used? It just seams like pointless extra steps...

---

### Post by Wybiral on 2009-02-13
In that example, it is pointless. But in situations like this, it's not:

```

x = 'this could    '

print x.strip() + ' have come from anywhere'

```

There are situations where you'll parse data from some file or website, or maybe getting user input from a terminal or textbox and you don't want whitespace on the ends.

---

### Post by WW on 2009-02-13
> **Wybiral said:**
> Example:
```

'"That\'s why," he said.'

```
Alternatively,
```

""""That's why," he said."""

```

---

### Post by Wybiral on 2009-02-13
> **WW said:**
> Alternatively,
```

""""That's why," he said."""

```

Definitely. In fact, considering triple-quotes, you really only need to escape a quote when it gets this out of hand:

```

print '''
print """"
print '"That\'s why," he said.'
"""
'''

```

And hopefully... It never gets that far :)

But I would probably just escape it instead of triple quoting if it's just one or two quotes I need to print.

---

### Post by Leo Dragonheart on 2009-02-14
```
x = 'this could    '

print x.strip() + ' have come from anywhere'
```




Thank you for the info. I see from your example how it would be used and that the one they show is kind of lame they should use something like your example so noobs like myself don't get all messed up... Thank you again for the insight....

---

