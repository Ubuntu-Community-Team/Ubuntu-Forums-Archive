---
title: "Python: .split vs. .join"
date: 2009-09-05
forum: Programming Talk
---

### Post by filifunk on 2009-09-05
I don't understand why .split() and .join() can't be used in the same way.  For instance, this works:

```


grocery_list: "Milk  2\nEggs  12"

grocery_list.split()


```

but this doesn't

```


grocery_list.join()


```

in fact I have to do this:

```


"".join(grocery_list)


```

why do most functions work like split() but join() works differently?

Just curious, maybe they're different types of functions?

---

### Post by ghostdog74 on 2009-09-05
> **filifunk said:**
> 

```


grocery_list.join()


```


if you do that , the interpreter will give you errors. join() needs an argument.

---

### Post by slavik on 2009-09-05
because in python, object.join(args) will join args together with object between them.

---

### Post by tjwilli on 2009-09-05
> **filifunk said:**
> I don't understand why .split() and .join() can't be used in the same way.  For instance, this works:

```


grocery_list: "Milk  2\nEggs  12"

grocery_list.split()


```

but this doesn't

```


grocery_list.join()


```

in fact I have to do this:

```


"".join(grocery_list)


```

why do most functions work like split() but join() works differently?

Just curious, maybe they're different types of functions?

Maybe because they are basically opposites? split() breaks up a string into a sequence, join() concatenates a sequence into a string.

```

>>> grocery_list="Milk  2\nEggs  12"
>>> grocery_list.split()
['Milk', '2', 'Eggs', '12']
>>> ' '.join(grocery_list.split())
'Milk 2 Eggs 12'

```

---

