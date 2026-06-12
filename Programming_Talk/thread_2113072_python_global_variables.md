---
title: "python global variables"
date: 2013-02-06
forum: Programming Talk
---

### Post by wingnut2626 on 2013-02-06
Hi yet again guys!  Here is the issue today with Python (or more realistically, me)

Here is the code:

```
def break_words(stuff):
    """This function will break up words for us."""
    words = stuff.split(' ')
    return words
    
def sort_words(words):
    """Sorts the words."""
    return sorted(words)
    
def print_first_word(words):
    """Prints the first word after popping it off."""
    words = words.pop(0)
    print word
    
def print_last_word(words):
    """Prints the last word after popping it off."""
    word = words.pop(-1)
    print word
    
def sort_sentence(sentence):
    """Takes in a full sentence and returns the sorted words."""
    words = break_words(sentence)
    return sort_words(words)
    
def print_first_and_last(sentence):
    """Prints the first and last words of the sentence."""
    words = break_words(sentence)
    print_first_word(words)
    print_last_word(words)
    
def print_first_and_last_sorted(sentence):
    """Sorts the words then prints the first and last one."""
    words = sort_sentence(sentence)
    print_first_word(words)
    print_last_word(words)
```
    

And here is the output:

```
Python 2.7.3 (default, Sep 26 2012, 21:53:58) 
[GCC 4.7.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import python11
>>> sentence = "All good things come to those who wait."
>>> words = python11.break_words(sentence)
>>> words
['All', 'good', 'things', 'come', 'to', 'those', 'who', 'wait.']
>>> sorted_words = python11.sort_words(words)
>>> sorted_words
['All', 'come', 'good', 'things', 'those', 'to', 'wait.', 'who']
[COLOR=Green]>>> python11.print_first_word(words)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "python11.py", line 13, in print_first_word
    print word
NameError: global name 'word' is not defined[/COLOR]
>>> 
```

In the tutorial im using there is a valid output of All.  Why is it not working for me?  I have it typed exactly the way the tutorial shows.

---

### Post by r-senior on 2013-02-06
> **wingnut2626 said:**
> 
```

def print_first_word(words):
    """Prints the first word after popping it off."""
    word[COLOR="Red"]s[/COLOR] = words.pop(0)
    print word

```
Do you have an extra 's' that shouldn't be there?

---

### Post by MG&amp;TL on 2013-02-06
Don't follow tutorials blindly. 
 
```
def print_first_word(words):
    """Prints the first word after popping it off."""
    words = words.pop(0)
    print word

```
 
You're using the *words* array to store things. That's fine, but then you try and assign the result of *words.pop(0) *into *words. *I'm pretty sure that's not what you meant to do, right? *word* isn't even defined.
 
For instance, this would work better:
 
```

def print_first_word(words):
    word = words.pop(0)
    print word
```

---

### Post by wingnut2626 on 2013-02-06
Thanks guys.  Like i said the problem was with me, and a simple typo.  Thank you again!  Im learning more from ubuntu forums than I have from years of school!

---

