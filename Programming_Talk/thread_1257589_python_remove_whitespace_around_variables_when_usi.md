---
title: "python: remove whitespace around variables when using print"
date: 2009-09-04
forum: Programming Talk
---

### Post by AncientPC on 2009-09-04
```
#!/usr/bin/env python

for n in range(0,10):
    print n,
print
```

Results in:
0 1 2 3 4 5 6 7 8 9

I want:
0123456789

What should I do?

---

### Post by myrtle1908 on 2009-09-04
I don't know much about python but why do you have a comma after n?  Remove it.

---

### Post by AncientPC on 2009-09-04
> **myrtle1908 said:**
> I don't know much about python but why do you have a comma after n?  Remove it.
The comma is there so a newline is not added, otherwise I would get:
0
1
2
3
4
5
6
7
8
9

---

### Post by myrtle1908 on 2009-09-04
> **AncientPC said:**
> The comma is there so a newline is not added, otherwise I would get:
0
1
2
3
4
5
6
7
8
9

Ah yes.  I just read up on that.  I really shouldn't offer advice for languages i know little about.  My apologies.

---

### Post by -grubby on 2009-09-04
Hmm... try this:

```

x = range(0, 10)
print "".join(x)

```

EDIT: I just tried it, it didn't work. Maybe we can try list comprehensions?

```

x = range(0, 10)
print "".join( [str(y) for y in x] )

```

---

### Post by AncientPC on 2009-09-04
Thanks grubby but I need it as part of the for loop because what I'm actually doing is more along the lines of:
```

for object in obj_list:
    print obj.data,
print
```

To be a little more explicit, I'm working with a 2 dimensional array of classes and need to output the data without a gap between the data:
```
#!/usr/bin/env python

x = [['.','x','.'],['x','.','x'],['.','x','.']]

for i in range(0,3):
    for j in range(0,3):
        print x[i][j],
    print
```

output:
. x .
x . x
. x .

desired output:
.x.
x.x
.x.

Whereas I'm working with objects, I cannot join them using list comprehension.

---

### Post by -grubby on 2009-09-04
Try building a string:

```

x = something
string = ""

for i in x:
    string += i.attr

print string

```

---

### Post by AncientPC on 2009-09-04
Yeah, I already have something similar in the form of:
```
#!/usr/bin/env python

x = [['.','x','.'],['x','.','x'],['.','x','.']]

for i in range(0,3):
    s = ''
    for j in range(0,3):
        s += x[i][j]
    print s
```

Am I being stubborn about doing this without having to build strings and waste memory?

In C/C++/Java I can use printf/cout/System.out.print() without adding trailing white space, but for some reason is python not able to do something that I find basic?

---

### Post by ghostdog74 on 2009-09-04
> **AncientPC said:**
> ```
#!/usr/bin/env python

for n in range(0,10):
    print n,
print
```

Results in:
0 1 2 3 4 5 6 7 8 9

I want:
0123456789

What should I do?

```

>>> import sys
>>> for i in range(10):
...  sys.stdout.write(str(i))
...
0123456789

```

---

### Post by ghostdog74 on 2009-09-04
> **myrtle1908 said:**
> I don't know much about python but why do you have a comma after n?  Remove it.
i suggest you know more about Python before suggesting something like that.

---

### Post by myrtle1908 on 2009-09-04
> **ghostdog74 said:**
> i suggest you know more about Python before suggesting something like that.

Yes.  And you'll see I corrected my mistake in a subsequent post.

---

### Post by AncientPC on 2009-09-04
> **ghostdog74 said:**
> ```

>>> import sys
>>> for i in range(10):
...  sys.stdout.write(str(i))
...
0123456789

```
Awesome, that works!  Thanks ghostdog.

---

### Post by Bodsda on 2009-09-04
> **AncientPC said:**
> ```
#!/usr/bin/env python

for n in range(0,10):
    print n,
print
```

Results in:
0 1 2 3 4 5 6 7 8 9

I want:
0123456789

What should I do?

I am surprised by the complexity of some of the suggestions, especially as this is not a complex problem. Here is my solution.
```

string = ""
for n in range(10):
    string += str(n)
print string, "\n"

```

---

### Post by ghostdog74 on 2009-09-04
> **Bodsda said:**
> I am surprised by the complexity of some of the suggestions, especially as this is not a complex problem. Here is my solution.
```

string = ""
for n in range(10):
    string += str(n)
print string, "\n"

```
concatenating like that is "inefficient". if OP simply wants to print out the range without the spaces, this will suffice
```

>>> print ''.join(map(str,range(10)))
0123456789


```
or just use sys.stdout.write()

---

### Post by AncientPC on 2009-09-04
> **ghostdog74 said:**
> concatenating like that is "inefficient". if OP simply wants to print out the range without the spaces, this will suffice
```

>>> print ''.join(map(str,range(10)))
0123456789


```
or just use sys.stdout.write()
Actually I can't get this to work properly because sys.stdout.write() will add a newline that I can't seem to get rid of. :(

Edit: Nevermind, I found my problem (source had new lines in the data).

---

