---
title: "Python - how do you output a dictionary sorted by 'value'?"
date: 2010-09-02
forum: Programming Talk
---

### Post by BioBiro on 2010-09-02
I'm new to Python, and can't seem to figure this one out. I know dictionaries can't be sorted, but how can I get the output of a dictionary sorted by values, rather than keys? If I do something like:

```
mydict = {'John': '777', 'Mike': '9944', 'Peter': '93'}

sorted(mydict.values())

(I get back)

['777', '93', '9944']
```...it returns the values, but it's in alphabetical-style ordering, not numerical-style. And also, it doesn't give me back the matching keys from the dictionary. Can anyone show me how to do this? :)

---

### Post by StephenF on 2010-09-02
```

>>> mydict = {'John': '777', 'Mike': '9944', 'Peter': '93'}
>>> sorted((int(val), key) for key, val in mydict.iteritems())
[(93, 'Peter'), (777, 'John'), (9944, 'Mike')]
>>> [(key, str(val)) for val, key in sorted((int(val), key) for key, val \
... in mydict.iteritems())]
[('Peter', '93'), ('John', '777'), ('Mike', '9944')]

```

---

### Post by Bachstelze on 2010-09-02
Probably better to store the numbers as ints in the dict to begin with. ;)

---

### Post by Dies on 2010-09-02
> **BioBiro said:**
> Can anyone show me how to do this? :)

It would help if you told us more about what exactly it is you're trying to accomplish. :wink:

For example, what format are the results supposed to be in?

---

### Post by BioBiro on 2010-09-02
> **StephenF said:**
> ```

  [(key, str(val)) for val, key in sorted((int(val), key) for key, val \
... in mydict.iteritems())]
```

That's the sort of thing i'm after! Thanks a lot. I notice Python 3 uses 'items()' instead of 'iteritems()' for some reason.

Now all I have to do is have a good long look at what it actually does :-k.

> **Bachstelze said:**
> Probably better to store the numbers as ints in the dict to begin with. ;)

Yeah...that would have been good practice on my part. I promise i'll do it in future!

> **Dies said:**
> It would help if you told us more about what exactly it is you're trying to accomplish. :wink:

For example, what format are the results supposed to be in?

What i'm trying to do is simulate the results of a competition (let's say, a running race), and have the participants displayed in a results list, and the person with the biggest number wins the race, descending downwards. The number associated with the person's name will have a load of code to alter it (in fact it doesn't even need to be seen), but I want to get the 'results simulation' working first. The format would just be the dictionary keys going down in a list based on their associated value.

---

### Post by yashar on 2010-09-02
```

mydict = {'John': '777', 'Mike': '9944', 'Peter': '93'}

list_one=mydict.values()
list_two=[]

for item in list_one:
    list_two.append(int(item))

list_two.sort()

mydict_sorted={}


for k,v in mydict.iteritems():
    mydict_sorted[int(v)]=k

for value in list_two:
    print mydict_sorted[value],value
    


```

---

### Post by BioBiro on 2010-09-02
> **yashar said:**
> ```
...
```

Yes! That's it! I changed the last line a smidgen: [I]print(mydict_sorted[value])
[/I] 
Doing the output in a 'for' loop was what I was hoping for, so thanks a ton.

I'll do that 'SOVLED' thingy with the brackets since my question has been answered 100%.

---

### Post by ssam on 2010-09-03
there is also a ordered dict datatype that is new in python 2.7 and 3.1

---

