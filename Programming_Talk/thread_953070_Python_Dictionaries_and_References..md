---
title: "Python: Dictionaries and References."
date: 2008-10-19
forum: Programming Talk
---

### Post by jesuisbenjamin on 2008-10-19
Hey Forum,

This [useful tutorial on python]("http://http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/More_on_Lists") has taught me the basics on lists and dictionaries.
But now i am facing a little issue:
I create a dictionary_A including a dictionary_B, which itself includes a list. I did so only to save time and computing. Now i need to change values individually in the lists and in the sub-dictionaries. But when i do so, then all values change simultaneously with the values of their twin lists and sub-dictionaries.
And because i learned my lesson, i did:
```
import copy
new_dictionary = copy.deepcopy(dictionary_A)

```
And then i hoped to be able to change data in my lists found two levels down in my new_dictionary, but lo!
The twins change again in concert.... :(

So what is the magic spell i am missing?

---

### Post by y-lee on 2008-10-19
It would help to see your code :confused:

---

### Post by WW on 2008-10-19
I agree with y-lee, it would help to see your code (or at least a simple version that doesn't work for you).  What you described works for me:
```

>>> import copy
>>> w = [0,1,2]
>>> x = {'a':{'b':w}}
>>> y = copy.deepcopy(x)
>>> x
{'a': {'b': [0, 1, 2]}}
>>> y
{'a': {'b': [0, 1, 2]}}
>>> w[2] = 99
>>> x
{'a': {'b': [0, 1, 99]}}
>>> y
{'a': {'b': [0, 1, 2]}}
>>> 

```

---

### Post by meanburrito920 on 2008-10-19
try this:

```

dict_A = dict_B[:]

```

that is the easiest way to just copy the data.

---

### Post by WW on 2008-10-20
> **meanburrito920 said:**
> try this:

```

dict_A = dict_B[:]

```

that is the easiest way to just copy the data.

Actually, that doesn't work--you'll get an error.  Slice operations don't work with dictionaries.

---

### Post by jesuisbenjamin on 2008-10-20
So cool everyone, thanks for all the help.

Here is the code:

```
#This function creates 1 list and 2 dictionaries:
# 'xy' is a list with the coordinates of regions set at x = 0 and y = 0
# 'info' includes 'xy' and other info about the region
# 'region' includes 48 regions with from 0 to 47, with 'info' set as their respective value.

def make():
    xy = [0, 0]

    info = {'xy': xy, 'terrain': 'sea', 'landlord': 'no one', 'governor': 'no one',
            'fort': False, 'general': 'no one', 'army': 0, 'wonder': False}

    region = {}
    a = 0
    while len(region) < 48:
        region[a] = info
        a = a + 1
        
#Now we cut-off references with a deepcopy:
    import copy
    world = copy.deepcopy(region)
    
#Next, regions should be getting proper coordinates:

    for r in range(len(world)):
        if 0 <= r and r <= 7:
            world[r]['xy'] = [r, 0]
        elif 8 <= r and r <= 15:
            world[r]['xy'] = [r-8, 1]
        elif 16 <= r and r <= 23:
            world[r]['xy'] = [r-16, 2]
        elif 24 <= r and r <= 31:
            world[r]['xy'] = [r-24, 3]
        elif 32 <= r and r <= 39:
            world[r]['xy'] = [r-32, 4]
        elif 40 <= r and r <= 47:
            world[r]['xy'] = [r-40, 5]
        print r + 1, '\t', "r = ", r, '\t', world[r]['xy']
        print 10, '\t', "r = ", r, '\t', world[r]['xy']

#Here is the end of make() -- RETURN VARIABLES!
            
    return world


#This function will print the menu:
def menu():
    option = 3
    if option != 0:
        print "Menu"
        print "1. New Game"
        print "0. Quit"
        option = input("Please chose an option: ")
    if option == 1:
        world = make()

    else:
        print "Thank you, good bye!"
    return world


world = menu()



```

As far as my logic goes, there is no reason it shouldn't work, but i can't get Python to agree with me, so obviously there is something i am not aware of...

Cheers :D

---

### Post by WW on 2008-10-20
Your assignment of info to region[a] also needs to be a deep copy.  As it is now, each entry in region points to the same object, info.  When you deep copy region to world, only a single copy of info is made, and each entry in world points to this single copy.

Move **import copy** to the beginning of the file, and in the while loop, change this:
```

        region[a] = info

```
to this:
```

        region[a] = copy.deepcopy(info)

```

---

### Post by jesuisbenjamin on 2008-10-20
Haaa but of course! :D This is so cool!
Cheers!

---

### Post by Lifman on 2008-10-20
if i'm not mistaken, what you do is assign the same list (xy) to the key 'xy' in all of your infos, and the same dictionary (info) to all your ranges. writing something like {xy': [0,0]} should cure the first problem, and you should probably avoid using info in the second - simply assign the {...} bit to range[a].
while you're at it, maybe change the range loop to a normal for a... like you did with the ranges...? ;-)

---

### Post by jesuisbenjamin on 2008-10-20
So actually the following may just as well be the simplest way of making my dictionary:

```

    region = {}
    a = 0
    while len(region) < 48:
        region[a] = {'xy': [0, 0], 'terrain': 'sea', 'landlord': 'no one', 'governor': 'no one',
            'fort': False, 'general': 'no one', 'army': 0, 'wonder': False}
        a = a + 1

```

And all my region[a] entries will be independent from each other as well as 'xy'?

---

