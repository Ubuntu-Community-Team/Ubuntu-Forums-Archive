---
title: "Wondering How To Do This In Python..."
date: 2009-09-23
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-09-23
I am wondering how I would do the following, but have the list of indicies stretch arbitrarily for however long the indicies list is. Here is the code:
```

if checkList(argv,[i,1],':'):
    print "ok"
#------function------

def checkList(l,indicies,char):
    try:
        if l[indicies[0]][indicies[1]] == char:
            return True
        else:
            return False
    except:
        return False

```

I have basically just put a bandaid on the problem at the moment by doing:
```

l[indicies[0]][indicies[1]]

```
But I would like to have it so that based on the length of indicies it will treat it as another index to an array. I am thinking I would have to use some sort of lamda expression, but get stuck when thinking about how to make it so that another dimension of the array is added(another [] is added to l[] making it l[][]).

Any ideas or suggestions? Is this even possible? Thanks in advance.

---

### Post by Arndt on 2009-09-23
> **StunnerAlpha said:**
> I am wondering how I would do the following, but have the list of indicies stretch arbitrarily for however long the indicies list is. Here is the code:
```

if checkList(argv,[i,1],':'):
    print "ok"
#------function------

def checkList(l,indicies,char):
    try:
        if l[indicies[0]][indicies[1]] == char:
            return True
        else:
            return False
    except:
        return False

```

I have basically just put a bandaid on the problem at the moment by doing:
```

l[indicies[0]][indicies[1]]

```
But I would like to have it so that based on the length of indicies it will treat it as another index to an array. I am thinking I would have to use some sort of lamda expression, but get stuck when thinking about how to make it so that another dimension of the array is added(another [] is added to l[] making it l[][]).

Any ideas or suggestions? Is this even possible? Thanks in advance.

Maybe I'm dense today, but I don't grasp what you want. Can you give an example call and the result you want?

(This is not important, of course, and you can name your variables what you want, but the word is 'indices'.)

---

### Post by StunnerAlpha on 2009-09-23
> **Arndt said:**
> Maybe I'm dense today, but I don't grasp what you want. Can you give an example call and the result you want?

(This is not important, of course, and you can name your variables what you want, but the word is 'indices'.)

Ah thanks for the spelling correction, I appreciate it. What I would like to have in the function is something like:
```

def checkList(l,indicies,char):
    try:
        if l[X] == char:
            return True
        else:
            return False
    except:
        return False

```
Where "X" is the bit of code that will make it so that all dimensions of the array are specified. For example the way I have it in the function now would cause me to do this:
```

def checkList(l,indicies,char):
    try:
        if len(indicies) == 1:
            if l[indicies[0]] == char:
                return True
            else:
                return False
        elif len(indicies) == 2:
            if l[indicies[0]][indicies[1]] == char:
                return True
            else:
                return False
        elif len(indicies) == 3:
            if l[indicies[0]][indicies[1]][indicies[2]] == char:
                return True
            else:
                return False
#and so on and so forth...
    except:
        return False

```

I am just wondering if there is any concise way to keep on expanding the array dimensions. Thanks.

---

### Post by Occasionally Correct on 2009-09-23
You can reduce the list down to the innermost child that you want to grab with a loop:
```
def check_list(lst, indices, char):
    j = list(lst)
    for i in indices:
        j = j[i]
    return j == char

some_list = ['a', ['b', 'c', ['d', 'e'], 'f'], 'g']
print check_list(some_list, [1, 2, 0], 'd')
```
With a few more *print*s in there, the progression of the loop is easy to follow:

j = ['a', ['b', 'c', ['d', 'e'], 'f'], 'g']
j = ['b', 'c', ['d', 'e'], 'f']
j = ['d', 'e']
j = 'd'

Hope that helps. :)

---

