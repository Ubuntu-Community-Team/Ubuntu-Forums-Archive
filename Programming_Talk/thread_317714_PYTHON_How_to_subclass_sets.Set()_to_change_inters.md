---
title: "PYTHON: How to subclass sets.Set() to change intersection() behavior?"
date: 2006-12-12
forum: Programming Talk
---

### Post by mkppk on 2006-12-12
I have kind of strange change I'd like to make to the sets.Set() intersection() method..

Normally, intersection would return items in both s1 and s2 like with something like this:  s1.intersection(s2)

I want the item matching to be a bit "looser".. that is, items in s2 that match to just the beginning of items in s1 would be included in the result of intersection().

I do not know how intersection() is implemented, so I just kinda guessed it might have something to do with how it compares set elements, probably using __eq__ or __cmp__. SO, I though if I override these methods, maybe magically that would affect the way intersection works.. so far, no luck =(

Please take a look at the little example script to try to illustrate what I would like to happen when using my subclass.. Is my approach totally wrong, or is there a better way to accomplish this? I am trying to avoid running through nested loops of lists (see final example).

P.S.
- the lists I am working with are small, like 1-10 items each
- actually, not so concerned witht the items in the resulting set, just want to know that the two sets have at least one item "in common"
- would welcome any other suggestions that would be FAST



My example script:
```
import sets

# the way set intersection normally works
s1=sets.Set(['macys','installment','oil','beans'])
s2=sets.Set(['macy','oil','inst','coffee'])

# prints Set(['oil']), as expected..
print s1.intersection(s2)


# my subclass, mySet - I don't know how to effect the .intersection() method
# my best guess was to change the __eq__ or maybe the __cmp__ methods??
# for now, mySet does nothing special at all but call the functions from sets.Set
class mySet(sets.Set):
	
	def __init__(self,iterable=None):
		
		sets.Set.__init__(self,iterable)
	
	def __eq__(self,other):
		
		# maybe something here?
		return sets.Set.__eq__(self,other)
	
	def __cmp__(self,other):
		
		# or maybe something here?
		return sets.Set.__cmp__(self,other)
	
	
	
# the same sets used in previous example
s3=mySet(['macys','installment','oil','beans'])
s4=mySet(['macy','oil','inst','coffee'])

# and, the same result: mySet(['oil'])
print s3.intersection(s4)

#****************************************************************************
# THE RESULT I WOULD LIKE TO GET WOULD LOOK LIKE THIS
# because I want items of s4 to match to the beginning of items in s3
# actually I am not so concerned with the result of intersection, just want to know there there was
# at least one item in common between the two sets..
#
# mySet(['macy','inst','oil'])
#****************************************************************************



# this is the list implementation I am trying to avoid because I am under the impression using set  would be faster..(??)
# please let me know if I am wrong about that assumption

L1=['macys','installment','oil','beans']
L2=['macy','oil','inst','coffee']

L3=[]
for x in L1:
	for y in L2:
		if x.startswith(y):
			L3.append(y)
		
# prints ['macy', 'inst', 'oil']
print L3
```
		

And the output:
```
/usr/bin/python -u  "/home/mkp/pytest/settest.py"
Set(['oil'])
mySet(['oil'])
['macy', 'inst', 'oil']

```

---

### Post by duff on 2006-12-12
Here's a bit of a hack, but it works.

First, you're overridding __cmp__ and __eq__ in Set, but it's actually the 'str' class that needs changing.  With a bit of testing, I found out first '__hash__' is called, if there is a collision then '__eq__' is called.  So, instead of subclassing Set, I subclassed str.  __hash__ is overridden to always return 0, and __eq__ is overridden to first see if the strings are close-enough, but falls back to the original __eq__ if the aren't. ```
class CloseEnoughString(str):
   def __hash__(self):
      return 0
   def __eq__(self, other):
      if self.startswith(other) or other.startswith(self):
         return True
      return str.__eq__(self,other)

_=CloseEnoughString
s3 = set([_('macys'),_('installment'),_('oil'),_('beans')])
s4 = set([_('macy'),_('oil'),_('inst'),_('coffee')])
print s3.intersection(s4)
```

With output: ```
set(['macy', 'oil', 'inst'])
```

Btw, "set" is a built-in class now.

---

### Post by pmasiar on 2006-12-12
Warning: I am *not* OO guru. Others may have better advice, but here it goes:

> **mkppk said:**
> I do not know how intersection() is implemented 

Use the source, Luke! :-) see file /usr/lib/python2.4/sets.py and be impressed as you will inherit from Guido and Alex! :-)

You don't need to define methods you want to inherit without change - define only changed methods.

---

### Post by mkppk on 2006-12-12
duff - ah, of course.. custom str types

pmasiar - k, didnt know it was a builtin type now.. i did import sets print sets and it pointed to a .pyc file so I assumed the code was unavailable without looking for a .py file.. 



Still would like to see a less "hacky" solution, but appriciated duff. I will try it and see how performance compares to my nested for loop w/ lists solution.

---

