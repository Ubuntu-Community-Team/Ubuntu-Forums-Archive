---
title: "python list.del[0]"
date: 2010-02-07
forum: Programming Talk
---

### Post by Raemian on 2010-02-07
This is my first post so please bear with me....

I am new to programming. Python is my first language and I am playing around with code creating simple guessing games, hangman, and such.

My problem is that i want to have a list of words that once a word is used it won't be used again. I have read that strings cannot be deleted or removed (plus I get an error when i try run the program - must use integer)

example:

listOne = ['strawberries', 'chicken', 'spam', 'steak and eggs', 'a basket of fruit']
i = listOne[0]

def question(i):
          answer = (raw_input ('Would you like ' + i + '?'))
                if answer in ('no') :
           del.listOne[0]
                                  return [asking(i)]    
            else:
          ...............................


  I have been reading tutorials and forums for  a week... Does anyone have any suggestions so i can get some sleep?

---

### Post by croto on 2010-02-07
Hi Raemian, could you express in words what your example is supposed to do? I'm having trouble understanding it.

---

### Post by Raemian on 2010-02-07
I am trying to go through the list one by one in order without repeating. I actually have no need for this (yet), i was just curious if it's possible. ;)
 

output would look something like:

Would you like strawberries?


If the user responds 'no'  the program would choose next word in list:

Would you like chicken?



And so on until the list runs out or the user responds differently.
I know this can be done with numbers, but I can't get it to work with words.

Am I making any sense yet?

---

### Post by croto on 2010-02-07
In that case, I don't think you need to delete from the list. You can do something like:
```

#!/usr/bin/python

choices = ['strawberries', 'chicken', 'spam', 'steak and eggs', 'a basket of fruit']

userchoice = None

for choice in choices:
        answer = (raw_input ('Would you like ' + choice + '?'))
        if answer.lower() in set(['y', 'yes']):
                userchoice = choice
                break

if userchoice is not None:
        print "User would like " + userchoice
else:
        print "User is not in the mood for anything"

```

---

### Post by Raemian on 2010-02-07
Thanks! :D

---

### Post by wmcbrine on 2010-02-07
If you *did* want to delete from a list, "del listname[index]" or "listname.pop(index)" are both valid (but not "listname.del[index]", nor "del.listname[index]"). But note that you'll confuse Python if you delete items from a list while iterating over it.

What you read about strings is probably that they're "immutable". That means that they can't be *changed*, not that they can't be deleted. And for the most part, you can ignore this aspect of strings -- it just means you can't do something like this:

```
>>> a = 'pan'
>>> a[1] = 'i'  # WRONG, CAUSES EXCEPTION
>>> print a
pin # DOES NOT HAPPEN
```

However, there's no reason you can't do this:

```
>>> a = 'pan'
>>> a = 'pin'
>>> print a
pin # WORKS
```

So, aren't you changing the string? From Python's point of view, no -- you're just attaching the label "a" to a completely *new* string object. The original string object will then be garbage collected if there are no other labels referring to it.

---

### Post by lavinog on 2010-02-07
I think i= i = listOne.pop(0) is what you are wanting.  It will grab the first item from the list and delete it at the same time.

---

