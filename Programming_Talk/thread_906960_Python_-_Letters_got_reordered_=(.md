---
title: "Python - Letters got reordered =("
date: 2008-09-01
forum: Programming Talk
---

### Post by dmitrijledkov on 2008-09-01
I have started to learn python by doing python challenge.

For level two, there is huge input and you need to find rare characters in it.

This is my solution:

```

from text import *
import string

result = {}

for letter in set(s):
    result[letter] = s.count(letter)
    
for letter, count in result.items():
    if letter.isalpha():
        print letter, count
print "--"

# small test to ask question about above
for letter in s:
    if letter.isalpha():
        print letter

```

text.py has: s=''' HUGE INPUT ''', [pastebin]("http://pastebin.com/m73011d50")

The output of this program is:
```

a 1
e 1
i 1
l 1
q 1
u 1
t 1
y 1
--
e
q
u
a
l
i
t
y

```

I don't understand why set(s) reordered letters in s, since correct answer is equality for next challenge.

Can you please explain it to me?

---

### Post by WW on 2008-09-01
As explained in the first few sentences of [Section 3.7](http://docs.python.org/lib/types-set.html) of the [Python Library Reference](http://docs.python.org/lib/lib.html), a set is an "unordered collection of distinct hashable objects", and "Being an unordered collection, sets do not record element position or order of insertion."

You also use the set elements as keys in a dict; this can also change the order.  According to [Section 3.8](http://docs.python.org/lib/typesmapping.html), "Keys and values are listed in an arbitrary order which is non-random, varies across Python implementations, and depends on the dictionary's history of insertions and deletions."

For example:
```

>>> result = {}
>>> result['a'] = 1
>>> result['z'] = 2
>>> result['b'] = 3
>>> result['x'] = 4
>>> result
{'a': 1, 'x': 4, 'z': 2, 'b': 3}
>>> result.items()
[('a', 1), ('x', 4), ('z', 2), ('b', 3)]
>>> 

```

---

### Post by rikxik on 2008-09-01
I thought set by definition is an un-ordered collection of objects?

---

### Post by dmitrijledkov on 2008-09-01
Thank you very much. Is there an ordered list? Cause in this task I should have gotten in the end "equality" the ordered word.

---

### Post by nvteighen on 2008-09-01
What is exactly the challenge? If you just want to catch any letter in the text, in order, you just could do:

[PHP]
s = "2123153abs12ww3?)("
result = []

for letter in s:
   if letter.isalpha():
       result += [letter]

print result
[/PHP]

If you need to count how many times a letter occurs... well, change result to a dictionary and use the method you used before...

---

### Post by Wybiral on 2008-09-01
> **dmitrijledkov said:**
> Thank you very much. Is there an ordered list? Cause in this task I should have gotten in the end "equality" the ordered word.

When you use set in "for letter in set(s):" you're reducing the collection to a unique set. If you're wondering why it's unordered... How else should it be? The first occurrence? The last? If so, then you will need to come up with an algorithm on your own (probably just store the first occurrence of every item as you iterate). But, I don't think that's what you need... I've solved quite a few of the Python challenges, without anything like this.

---

### Post by dmitrijledkov on 2008-09-01
> **nvteighen said:**
> What is exactly the challenge? If you just want to catch any letter in the text, in order, you just could do:

If you need to count how many times a letter occurs... well, change result to a dictionary and use the method you used before...

[URL="http://www.pythonchallenge.com/pc/def/ocr.html"]
http://www.pythonchallenge.com/pc/def/ocr.html[/URL]
```

<!--
find rare characters in the mess below:
-->

<!--
%%$@_$^__#)^)&!_+]!*@&^}@[@%]()%+$&[(_@%+%$*^@$^!+]!&_#)_*}{}}!}_]$[%}@[{_@#_^{*
@##&{#&{&)*%(]{{([*}@[@&]+!!*{)!}{%+{))])[!^})+)$]#{*+^((@^@}$[**$&^{$!@#$%)!@(&
+^!{%_$&@^!}$_${)$_#)!({@!)(^}!*^&!$%_&&}&_#&@{)]{+)%*{&*%*&@%$+]!*__(#!*){%&@++
!_)^$&&%#+)}!@!)&^}**#!_$([$!$}#*^}$+&#[{*{}{((#$]{[$[$$()_#}!@}^@_&%^*!){*^^_$^
]@}#%[%!^[^_})+@&}{@*!(@$%$^)}[_!}(*}#}#___}!](@_{{(*#%!%%+*)^+#%}$+_]#}%!**#!^_
)@)$%%^{_%!@(&{!}$_$[)*!^&{}*#{!)@})!*{^&[&$#@)*@#@_@^_#*!@_#})+[^&!@*}^){%%{&#@
@{%(&{+(#^{@{)%_$[+}]$]^{^#(*}%)@$@}(#{_&]#%#]{_*({(])$%[!}#@@&_)([*]}$}&${^}@(%
(%[@%!}%*$}(*@)}){+@(%@*$&]*^*}*]&$[}*]%]+*}^!}*$^^_()#$^]++@__){&&+((#%+(&+){)$

+ 1200 lines


```

I didn't know upfront what characters will be rare. Most of characters have count >1000 and only letters had count 1.

The answer to proceed to next challenge are those letters in the order they appeared in the the challenge.

How would you count character instances without loosing their order in a pythonic way?

---

### Post by mssever on 2008-09-01
Try using a list instead of a set.

---

### Post by DaymItzJack on 2008-09-01
[http://wiki.pythonchallenge.com/index.php?title=Level2:Main_Page](http://wiki.pythonchallenge.com/index.php?title=Level2:Main_Page)

---

### Post by bvmou on 2008-09-02
Here is a fairly straightforward way of doing the basic ordering, if I understand the problem (this probably doesn't address the full scope, but I have sometimes used things like it, for example, with calls to get information about files that is then stored in a dictionary, and reordered based on dates, etc.):

[PHP]>>> a = 'c aaaaa l bbbb u ddddd e'
>>> resultDict = {}
>>> b = [letter for letter in a]
>>> b
['c', ' ', 'a', 'a', 'a', 'a', 'a', ' ', 'l', ' ', 'b', 'b', 'b', 'b', ' ', 'u', ' ', 'd', 'd', 'd', 'd', 'd', ' ', 'e']
>>> for item in b:
	try:
		resultDict[item] += 1
	except KeyError:
		resultDict[item] = 1

		
>>> resultDict
{'a': 5, ' ': 6, 'c': 1, 'b': 4, 'e': 1, 'd': 5, 'l': 1, 'u': 1}
>>> resultList = []
>>> for item in b:
	if resultDict[item] < 2:
		resultList.append(item)

		
>>> resultList
['c', 'l', 'u', 'e']
>>> [/PHP]

This avoids the problem you encountered with the hash table (python 'dict' type), which reorders and stores values so that they can be quickly looked up and would give you something like:

[PHP]>>> for item in resultDict:
	if resultDict[item] < 2:
			print item

			
c
e
l
u[/PHP]

Your sample string (the s variable posted to pastebin) happens to have only those letters in that order.  If it had more extraneous letters, you would want something that rechecks the order in the original, for that you might try something like the list comprehension (a cool python thing) that is used to define b above.

---

### Post by nvteighen on 2008-09-02
You don't need anything but a string. I mean: use the very same code you posted at the first post and change set(s) by s and it will work.

A list can also be used, but why bother if strings are also iterable?

A question: is that "import string" really needed?

---

### Post by WW on 2008-09-02
> **nvteighen said:**
> You don't need anything but a string. I mean: use the very same code you posted at the first post and change set(s) by s and it will work.
No it won't, because the dict "result" will not necessarily preserve the order of the keys.  (It will also be very inefficient!)

If I understand the challenge correctly, it is to find all the characters that occur just once (these are the "rare" characters), and print them *in the order in which they occurred in the string*.  At least, that is what the original poster is trying to accomplish.

---

### Post by ghostdog74 on 2008-09-02
> **dmitrijledkov said:**
> 

How would you count character instances without loosing their order in a pythonic way?

Hint: you do not need to count anything. Just replace those unwanted characters with blanks, or just use a loop to go over them and print only wanted characters.

---

### Post by pmasiar on 2008-09-02
OP: why you don't use hints from Python Challenge Forum?

"Forums: Python Challenge Forums, read before you post. "

Do you understand hints there? 

Maybe you are not ready yet to tackle this challenge website, maybe you should solve more trivial homework problems first? Learn about basic data structures (list, dictionary) and how to use them?

Python challenge is not aimed to teach you trivial basics from your guide book, but to have fun while getting past basics.

---

