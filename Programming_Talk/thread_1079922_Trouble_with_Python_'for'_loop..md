---
title: "Trouble with Python 'for' loop."
date: 2009-02-24
forum: Programming Talk
---

### Post by addowannapeea on 2009-02-24
I'm trying to make a program in python that will compute a list of 4-digit numbers in which the 4 digits multiply out to 120. my attempt looks a bit like:

def num_count(a,b,c,d):
for a in range(1,10):
for b in range(1,10):
for c in range(1,10):
for d in range(1,10):
if a*b*c*d==120:
print "%d,%d,%d,%d" % (a,b,c,d)

num_count(a,b,c,d)


(ignore lack of indentation)

the error i'm getting says:

File "numbercount.py", line 11, in <module>
num_count(a,b,c,d)
NameError: name 'a' is not defined


Any help would be much appreciated.

---

### Post by cabalas on 2009-02-24
Why are you passing the loop iterators as parameters? take them out so it looks a little something like this:

[PHP]
def num_count():
	for a in range(1,10):
		for b in range(1,10):
			for c in range(1,10):
				for d in range(1,10):
					if a*b*c*d==120:
						print "%d,%d,%d,%d" % (a,b,c,d)

num_count()
[/PHP]

And it all works fine.

---

### Post by unutbu on 2009-02-24
Change
```

def num_count(a,b,c,d):
```

to
```

def num_count():
```

and change
```

num_count(a,b,c,d)

```
to
```

num_count()
```

When you define the function num_count this way "def num_count(a,b,c,d):"
it means you need to pass four arguments to num_count. Indeed you do, when 
you call it with "num_count(a,b,c,d)", but python complains that in this line (line 11) the symbol "a" is used without being defined. "a" is indeed not defined outside the scope of the function definition. "a" is just a temporary variable whose existence is confined to the scope of the function definition. At the point where num_count is called, "a" has no meaning.

---

### Post by addowannapeea on 2009-02-25
Awesome you guys. thanks for the help.

---

### Post by Can+~ on 2009-02-25
I think scipy has a module for combinatorics and permutations.

---

### Post by bostonaholic on 2009-02-25
> **Can+~ said:**
> I think scipy has a module for combinatorics and permutations.

+1.  You may want to look into the differences between *combinations* and *permutations*.

Order matters within a permutation so (10, 6, 2, 1) != (10, 2, 6, 1).  But within a combination order does not matter, therefor (10, 6, 2, 1) is the same as (10, 2, 6, 1).

You might need to find out if you want *permutations* of numbers who's multiple is 120, or do you want *combinations* of number's who's multiple is 120.

---

### Post by addowannapeea on 2009-02-25
Duly noted, but i was looking for combinations on this one.

---

### Post by simeon87 on 2009-02-25
> **bostonaholic said:**
> +1.  You may want to look into the differences between *combinations* and *permutations*.

Order matters within a combination so (10, 6, 2, 1) != (10, 2, 6, 1).  But within a permutation order does not matter, therefor (10, 6, 2, 1) is the same as (10, 2, 6, 1).

You might need to find out if you want *combinations* of numbers who's multiple is 120, or do you want *permutations* of number's who's multiple is 120.

It's the other way around: order matters in a permutation, order does not matter in a combination.

---

### Post by bostonaholic on 2009-02-25
> **simeon87 said:**
> It's the other way around: order matters in a permutation, order does not matter in a combination.

Thanks, I just reread my post and realized I had it backwards.  It's fixed now.

---

