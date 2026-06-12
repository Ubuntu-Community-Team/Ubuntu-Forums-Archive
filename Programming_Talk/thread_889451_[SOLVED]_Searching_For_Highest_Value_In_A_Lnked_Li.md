---
title: "[SOLVED] Searching For Highest Value In A Lnked List"
date: 2008-08-14
forum: Programming Talk
---

### Post by lordhaworth on 2008-08-14
Hey all

The title says it all really. I need to find a way to search a linked list for the highest data value in the list (in C or Fortran90) and there seems to be a bit of a shortage of good examples of this on the internet!
I am familiar with various sorting algorithms and those are not the problem - what is more of a problem is applying them to a linked list. 
The simplest (though I would have thought not best) way would be to compare one nodes data value with that of the next node and then swap their place in the list using other pointers if they satisfy some criteria?

Thanks for any help

Tom

---

### Post by LaRoza on 2008-08-14
> **lordhaworth said:**
> 
The simplest (though I would have thought not best) way would be to compare one nodes data value with that of the next node and then swap their place in the list using other pointers if they satisfy some criteria?


A Bubble sort, and you are right, it isn't the best (but it works)

I don't understand the problem, finding the highest value shouldn't be a problem:

```

def findHighest(list):
    findHighest = 0
    for el in list:
        if el > findHighest:
            findHighest = el
    return findHighest

```

---

### Post by lordhaworth on 2008-08-14
Thanks LaRoza
Its sorted now anyway - the problem was my lack of experience using fortran and what kind of things I could do with it to get what I wanted. 
At that awkward stage with the language where I feel I dont have to pick up a book anymore, but of course any problems I encounter couldnt be because I've forgotten something :)!

---

