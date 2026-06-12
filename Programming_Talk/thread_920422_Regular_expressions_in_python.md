---
title: "Regular expressions in python"
date: 2008-09-15
forum: Programming Talk
---

### Post by Sagekilla on 2008-09-15
Hi all, I was wondering if anyone could help me with regex in python. I can't seem to figure out how I can match a specific string. My purpose is that I'm trying to create a match for a price (this is for educational purposes only -- I don't intend on using this for any other purpose) inside of a string of characters.

So if I have (from a portion of the huger string of text) a string that says lines = 'The price for this item is <div class="price">$100.00</div>' I want to be able to grab that $100.00 portion.


If anyone can help me through this problem, I'd greatly appreciate it!

---

### Post by aloshbennett on 2008-09-15
I'm not sure about python's regex support (though i have a gut feeling it wouldnt be disappointing :-) ), here's a generic regular expression that matches any string 
starting with $ (\$)
Having more than one digits and comas ([0-9,\,]+)
May have zero or one '.', followed by more than one digit (\.?[0-9]+)
This would match string like '$100,00.99'
```
\$[0-9,\,]+\.?[0-9]+
```

You might have to tune it to your dataset.

---

### Post by pmasiar on 2008-09-15
Parsing HTML/XML via regex is sucker's game: don't! Use BeautifulSoup(messy HTML) or ElementTree (clean XML).

---

### Post by pmasiar on 2008-09-15
> **aloshbennett said:**
> I'm not sure about python's regex support (though i have a gut feeling it wouldnt be disappointing :-) )

Your gut feeling was correct: Python calls the same C regex library like anyone else. But your advice is useless: does not cover all the special cases, which proper HTML/XML parsing library does. So **my** gut feeling is you don't have as much experience solving **real world** problems **in production** as you pretend to have... Attitude is not a valid substitute for experience 8-)

Edit: sorry my first reading was that Python regex **is** disappointing.

But your advice was **still** useless: friends don't let friends to parse HTML by regex.

---

### Post by forger on 2008-09-15
> **pmasiar said:**
> So **my** gut feeling is you don't have as much experience solving **real world** problems **in production** as you pretend to have... Attitude is not a valid substitute for experience 8-)

ouch? :P

---

### Post by ghostdog74 on 2008-09-15
regular expression is the last thing on my mind
```

>>> s='The price for this item is <div class="price">$100.00</div>'
>>> s.index("$")
46
>>> s.index("</div>")
53
>>> s[46:53]
'$100.00'


```

---

### Post by aloshbennett on 2008-09-15
lol!! Thats some tough words.

I wouldnt try parse regex with html (or suggest either) if my bread and butter depend on it. But hey, thats the quickest hack if you want some dirty job done!

You tell me you never grep around with regex and I'd say, "what an idiot".
So, tell me, do you grep around with regex?

And oh, btw, educational purposes = NOT production code.

---

