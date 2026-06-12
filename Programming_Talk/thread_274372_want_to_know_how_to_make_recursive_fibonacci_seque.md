---
title: "want to know how to make recursive fibonacci sequence program"
date: 2006-10-09
forum: Programming Talk
---

### Post by baldy1324 on 2006-10-09
hi i would like to make a program that does the fibonacci sequence by calling the function (recursion) 1000 times. each times it does this 1 time, the program prints the number so using code like this - 
```
#!/usr/bin/python
def fibiterative():
        n = 1000
        first = 0
        second = 1
        third = 0
        print first
        print "    "
        print second

        while n>0:
                third = first+second
                first = second
                second = third
                print third
                print "    "
                n=n-1

fibiterative()
```

but using recursion instead of while loops

---

### Post by eeGhoong0ais on 2006-10-09
Er ... forgive me if I'm jumping to conclusions here, but this looks very much like a homework assignment.

---

### Post by jpkotta on 2006-10-09
Just look it up in Google or Wikipedia.  There are so many examples that it's not even funny.

---

### Post by Note360 on 2006-10-09
Usually one uses lisp, haskell, or nemerle for recursion (functional programming). However, the same concept apply to python as far as recursion go.

---

### Post by meng on 2006-10-10
Word of warning: Using python to calculate fibonacci sequence to 1000 by recursion could take a LOT of processor time (think hours) unless you intend to use a dictionary to look-up previously calculated values.

Perhaps you could use this exercise to learn about generators rather than recursion!?

Also, I agree that you should take advantage of websearching to get instant answers to these fairly straightforward questions. Most Python texts (including online ones) cover this as a routine exercise.

Finally, if one of your aims is to litter the forums with several threads on essentially the same topic, then you're doing a great job! :p

---

### Post by skeeterbug on 2006-10-10
I was looking for the ignore button next to his name. Looks like this forum doesn't have it :(

---

### Post by meng on 2006-10-10
Oh be nice! You can set your mental filters if you need to.

---

### Post by skeeterbug on 2006-10-10
Sorry, I took the bait. It's been two or three days now and every day there seems to be one or two fibonacci posts from this guy. I wonder if he has ever been to google.com

:twisted: 


OK OK, on a serious note. Check out this url.

[http://www.google.com/codesearch/advanced_code_search](http://www.google.com/codesearch/advanced_code_search)

It might help more than this forum, who knows!

---

### Post by meng on 2006-10-10
True, some folks need more encouragement to learn how to help themselves.

---

### Post by johnnymac on 2006-10-10
IMHO google'n it is the easy way out.  Do it like the rest of us had to before google (hmm - perhaps I show my age) and READ...you'd be amazed at just how much your "I wann learn to program" book will show you about recursion.  

Funny though....school says this is how recursion works....industry says...AHHHHH Don't use recursion!!

---

### Post by Note360 on 2006-10-10
If you really want to use recursion you wont want to use python. You need a functional programming language. I would suggest Nemerle or LISP. If you want to do functional programming in python you should read up on functional programming first (because python is mainly imperative). Then you can implement functional programming in any language. (You should look into python lambada, and tuples. Also you will need a class for everything). I will admit that I like functional programming alot, but it has its places.

---

