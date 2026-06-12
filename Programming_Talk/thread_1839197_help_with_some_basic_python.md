---
title: "help with some basic python"
date: 2011-09-05
forum: Programming Talk
---

### Post by Beauxesprits13 on 2011-09-05
i'm relatively new to python and haven't fully got the hang of it yet. below is a function from some code that I have been writing. however I am snagged on a problem that Ii can't fathom a remedy for and was hoping someone could guide me as to how i might negate the issue.
the context of this code is a calculator of % frequency of some values. "distro" is a large dictionary of integers and their frequencies.  

However the output insists that the "data" object i created was a NoneType.
what is a noneType? why is there one here? can i get around them?

[PHP]def print_stats(distro):
    L = distro['total']
    del distro['total']
    data = [(v, k) for k, v in distro.items()]
    data = sorted(data)
    data = data.reverse()
    data = data[:10] # This returns nonetype is not subscriptable

    names=[]; numbers=[]
    for k, v in data:  # This returns nonetype is not iterable
        names.append(str(int(v)).center(8))
        numbers.append(k)

    for x in range(len(numbers)):
        z = (numbers[x]/L)*100    
        z = str(round(z, 2))
        z = z +"%"
        numbers[x] = z.center(7)[/PHP]thankyou for any help :P

---

### Post by nvteighen on 2011-09-05
> **Beauxesprits13 said:**
> 
[PHP]def print_stats(distro):
    L = distro['total']
    del distro['total']
    data = [(v, k) for k, v in distro.items()]
    data = sorted(data)
    data = data.reverse()
    data = data[:10] # This returns nonetype is not subscriptable

    names=[]; numbers=[]
    for k, v in data:  # This returns nonetype is not iterable
        names.append(str(int(v)).center(8))
        numbers.append(k)

    for x in range(len(numbers)):
        z = (numbers[x]/L)*100    
        z = str(round(z, 2))
        z = z +"%"
        numbers[x] = z.center(7)[/PHP]


The problem is this line:
```

data = data.reverse()

```

The reverse method works "in place" or "destructively", meaning that it actually modifies the original list forever. This makes it unnecessary to return the reversed list, because data itself is the reversed list.

<rant>
Yes, for someone like me, who [s]comes from Lisp[/s] is used to Lisp and functional programming, only having a destructive list reversal function makes me really mad. There should be a functional, non-destructive version which worked like you wanted.
</rant>

Where does the NoneType come from? Well, data.reverse doesn't return anything, so data becomes None... None is Python's way to say that something has no value nor type and it's what you get when you get a value from a function that returns nothing.

So, don't reassign data at that line. Just do data.reverse() and that's it.

EDIT: For some reason, I wrote that I came from Lisp. No, that's not true: I learned Lisp after learning Python. Corrected, for factual accuracy :)

---

### Post by StephenF on 2011-09-05
> **nvteighen said:**
> The problem is this line:
```

data = data.reverse()

```

<rant>
Yes, for someone like me, who [s]comes from Lisp[/s] is used to Lisp and functional programming, only having a destructive list reversal function makes me really mad. There should be a functional, non-destructive version which worked like you wanted.
</rant>
Since reversed() works on any iterable the provision of a non in-place method for list in particular is unnecessary.
```

newlist = list(reversed(oldlist))

```

---

### Post by Beauxesprits13 on 2011-09-05
I ended up swapping that line for [PHP]data = data[::-1][/PHP]

Thanks for the explanation though for a while I thought i'd never use reversed().

---

### Post by nvteighen on 2011-09-05
> **StephenF said:**
> Since reversed() works on any iterable the provision of a non in-place method for list in particular is unnecessary.
```

newlist = list(reversed(oldlist))

```

Oh, didn't know that one, though it's a bit cumbersome... I'd prefer something more direct, but well it's better than nothing :)

---

