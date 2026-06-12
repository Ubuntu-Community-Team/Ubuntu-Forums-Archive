---
title: "Two python commands...what's the difference? (simple question)"
date: 2008-07-16
forum: Programming Talk
---

### Post by s3a on 2008-07-16
The book byteofpython says:

[B]#!/usr/bin/python
# Filename: expression.py
length = 5
breadth = 2
area = length * breadth
print 'Area is', area
print 'Perimeter is', 2 * (length + breadth)[/B]

I find the following to also work:

[B]length = 5
breadth = 2
area = length * breadth
print 'Area is', area
print 'Perimeter is', 2 * (length + breadth)[/B]

Why does the author of the book do it that way? Does it matter?

---

### Post by LaRoza on 2008-07-16
> **s3a said:**
> The book byteofpython says:

[B]#!/usr/bin/python
# Filename: expression.py
length = 5
breadth = 2
area = length * breadth
print 'Area is', area
print 'Perimeter is', 2 * (length + breadth)[/B]

I find the following to also work:

[B]length = 5
breadth = 2
area = length * breadth
print 'Area is', area
print 'Perimeter is', 2 * (length + breadth)[/B]

Why does the author of the book do it that way? Does it matter?

I don't see a difference...

It could be written as:

```

#!/usr/bin/python
print "%s %d %s %d" % ("Area is ",5*2,"\nPerimeter is ", 2*(5+2)) 

```

---

### Post by ConMan318 on 2008-07-16
I assume you mean the first two lines.  Well the first line is the shebang line, which tells whatever is running the program where to look for the python interpreter.  I assume you ran your code with
```

python **filename**

```

This negates the need for the shebang by telling the shell specifically to run the program with python.  The shebang lets the program find python itself so it can be run with python.

The second line is a comment, which does absolutely nothing when the program runs; it is just there for people looking at the code.

---

### Post by LaRoza on 2008-07-16
Oh. For the OP...the shebang only works if the file is marked as execuatable (chmod +x $FILE) and if it is the first line and first character in the file. 

It is a comment and ignored otherwise (non Unix-like OS's don't use that convention, so it won't make a difference)

---

### Post by -grubby on 2008-07-16
A "#" Is a comment. Python ignores it. Another type of Comment is triple quotes (""" Comment """), that can be used over several lines. The triple quotes only work alone - I.E., you can only have something as a comment if the """ """ are alone, you could also use them for multiline strings.

---

### Post by mssever on 2008-07-17
> **nathangrubb said:**
> A "#" Is a comment. Python ignores it. Another type of Comment is triple quotes (""" Comment """), that can be used over several lines. The triple quotes only work alone - I.E., you can only have something as a comment if the """ """ are alone, you could also use them for multiline strings.
Actually, triple quotes are merely another type of string literal. [FONT=Courier New]"""foo"""[/FONT] is equivalent to [FONT=Courier New]'''foo'''[/FONT], [FONT=Courier New]"foo"[/FONT], and [FONT=Courier New]'foo'[/FONT]. I think you're confusing comments and docstrings.

---

### Post by Bodsda on 2008-07-17
s3a asked this question on #ubuntu and referred to width and breadth, i think hes just made a typo and s3a it doesnt matter what the words are (more or less) they are just variables you could do

```

OMGitsaVariable1 = 5
OMGitsaVariable2 = 2
area = OMGitsaVariable1 * OMGitsaVariable2
print 'Area is', area
print 'Perimeter is', 2 * (OMGitsaVariable1 + OMGitsaVariable2)

```

if you really wanted to, it would have the same results

> Another type of Comment is triple quotes (""" Comment """), 

Triple quotes like '''quote''' are used for spanning a single print statement across multiple lines

---

### Post by pmasiar on 2008-07-17
> **Bodsda said:**
> Triple quotes like '''quote''' are used for spanning a single print statement across multiple lines

Not exactly: to span string literals over multiple lines.

```

ml = """multiple
line"""
sl = "multiple\nline"

ml == sl # try it :-)

```

---

