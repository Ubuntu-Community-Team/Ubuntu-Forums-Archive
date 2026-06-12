---
title: "pickle in python"
date: 2011-02-08
forum: Programming Talk
---

### Post by Bigmon on 2011-02-08
Could anyone suggest why even though I am constantly adding items to the"weekly turnover" list - when unpickling the list I can only always print out the first item in the list ?

def yearly_turnover(week):
            import pickle, shelve
            weekly_turnover = []
            weekly_turnover.append(week)
            f = open("pickles1.dat","ab")
            pickle.dump(weekly_turnover,f)
            f.close()
            f = open("pickles1.dat","rb")
            turnover = pickle.load(f)
            print (turnover)
            f.close()

Any clues ???

---

### Post by gmargo on 2011-02-08
You have the **weekly_turnover** list as local to the **yearly_turnover** function.  It needs to be outside the scope of the function.  Every time you call the function you write out a list with a single element, which is why only one prints.

And please wrap your code in [ CODE ] tags to preserve indentation (especially important for python!)

Update: You are appending multiple dumps to the same file.  Pickle loads the first only.

Rewritten without all the appending to the dump file, this works:

```

#!/usr/bin/python

import pickle, shelve
weekly_turnover = []

def yearly_turnover(week):
        weekly_turnover.append(week)

yearly_turnover("Howdy1")
yearly_turnover( [ "Howdy2", "Howdy3" ] )
yearly_turnover("Howdy4")

f = open("pickles1.dat","wb")
pickle.dump(weekly_turnover,f)
f.close()

f = open("pickles1.dat","rb")
turnover = pickle.load(f)
print (turnover)
f.close()

```

---

### Post by Bigmon on 2011-02-08
Many thanks. That seems to work. You have been a great help.:p

---

### Post by unknownPoster on 2011-02-08
Just an fyi. I've found pickling to be relatively slow. 

I'm not sure if that's a problem or even worth worrying about in your situation. However, if you see any degradation of performance, I would check to see how many times you are performing pickle operations.

---

