---
title: "python - checking if any of the values in the list in a string"
date: 2007-01-04
forum: Programming Talk
---

### Post by pedrotuga on 2007-01-04
I have a list of stopwords.

is there an imediate way to check if a string contains any of those or do i have to loop it and test one by one?

also, how do i lowercase a a string?

---

### Post by Steveire on 2007-01-04
```

stopwords = ["stop", "halt", "freeze"]
for word in stopwords:
    if stopword in string:
        return

```

```

string = "erDRTGrfg"
string.lower()

```

---

### Post by duff on 2007-01-04
or
```
stopwords=set('stop','halt','freeze')
stopwords.intersection(set(word.split()))
```
the resulting set will be empty if *word* doesn't contain any *stopwords*.

---

### Post by ghostdog74 on 2007-01-04
> **pedrotuga said:**
> I have a list of stopwords.

is there an imediate way to check if a string contains any of those or do i have to loop it and test one by one?

also, how do i lowercase a a string?

you can just use "in" keyword
```

stopwords = ["stop", "halt", "freeze"]
if not word in stopwords:
   print "Word is not in stopwords"

```

to change string to lowercase
```

astring = "THIS STRING IS UPPER" #note: don't use "string" as a variable name.
print astring.lowercase()

```

---

### Post by pedrotuga on 2007-01-05
thanks everybody.

python cycle syntax is kind of elegant :) so the solution i said in the beggining is actualy very simpleas steve showed. Though, i think the intersection might be faster

---

### Post by pmasiar on 2007-01-05
Why guess, it's not hard to time it yourself:

Program to time:
```
import time

loopTimes = 10000000
stoplist = ["stop", "halt", "freeze"]
stopSet = set(["stop", "halt", "freeze"])
string = 'many differnet words which may containn stop or may not'
wordsSet = set(string.split())

def using_in(text, stopwords):
    "return 1 (true) if any of the stopwords are in text -- using in"
    for word in stopwords:
        if word in text:
            return 1
    return 0

def using_set(wordsSet, stopSet):
    "return 1 (true) if any of the stopwords are in text -- using sets"
    return len( wordsSet & stopSet)

tStart = time.time()
for ii in range(loopTimes):
    pass
t_empty = time.time() - tStart # empty loop

tStart = time.time()
for ii in range(loopTimes):
    res = using_in(string, stoplist)
t_in = time.time() - tStart # using in

tStart = time.time()
for ii in range(loopTimes):
    res = using_set(wordsSet, stopSet)
t_set = time.time() - tStart # using set
    
print loopTimes , 'using in:', t_in - t_empty
print loopTimes , 'using set:', t_set - t_empty
```

results of 3 runs (increasing loop times)

```
>>> ================================ RESTART 
100 using in: 0.0
100 using set: 0.0
>>> ================================ RESTART 
10000 using in: 0.0160000324249
10000 using set: 0.0149998664856
>>> ================================ RESTART 
1000000 using in: 1.78200006485
1000000 using set: 0.983999967575
>>> ================================ RESTART 
10000000 using in: 17.8279998302
10000000 using set: 9.82899999619
```

Result: Return of invested time (learning sets) will pay off if you run the code more than   1 billion times. Less than that, and plain loop is **faster** :-)

---

### Post by pmasiar on 2007-01-05
I was not happy with my previous solution: python mantra is that most obvious solution is the best. So i looked deeper. Sets approach has a little help: target string is preparsed to words. What I will preparse it for "in" approach too?

I added into obvious places these snippets: 

```
wordlist = string.split()

def using_inlist(wordlist, stopwords):
    "using in from list"
    for word in stopwords:
        if word in wordlist:
            return 1
    return 0

tStart = time.time()
for ii in range(loopTimes):
    res = using_inlist(wordlist, stoplist)
t_inlist = time.time() - tStart # using in list

print loopTimes , 'using in list:', t_inlist - t_empty
```

**result: Obvious apprach IS the fastest!**
```
1000000 using in: 1.78099989891
1000000 using in list: 0.922000169754
1000000 using set: 0.952999830246
```

---

### Post by slavik on 2007-01-05
this problem is O(nm) complexity. you are matching all elements in one array to all elements in another array.

---

### Post by RSL on 2007-04-10
Aw... Not to be a jerk but this is one of those moments where Ruby's Enumerable#include? would be sweet, right?

```

%w{list of stop words}.include?(word)
```

Oh, crap. I just became _that_ guy. :(

---

### Post by pmasiar on 2007-04-10
```

>>> stop_words = ['a', 'b', 'c', 'd']
>>> word = 'd'
>>> word in stop_words
True

```

It is python, after all. Simple things are obvious, hard are possible. :-)

---

### Post by WW on 2007-04-10
Something like this, maybe? (If you are using Python 2.5, the 'any' function is built-in.)
```

>>> def any(seq):
...     for s in seq:
...         if s:
...             return True
...     return False
...
>>> stopwords = ['stop','end','halt','quit']
>>> sentence1 = 'Four score and seven years ago'
>>> sentence2 = 'Should I stop using python?'
>>> any([sentence1.find(word) != -1 for word in stopwords])
False
>>> any([sentence2.find(word) != -1 for word in stopwords])
True
>>>

```

---

### Post by ghostdog74 on 2007-04-11
```

>>> stopwords = ['stop','end','halt','quit']
>>> sentence = 'Should I stop using python?'
>>> for x in stopwords:
...  sentence.__contains__(x)
...
True
False
False
False


```

---

