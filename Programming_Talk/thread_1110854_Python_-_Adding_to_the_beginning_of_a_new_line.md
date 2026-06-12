---
title: "Python - Adding to the beginning of a new line"
date: 2009-03-30
forum: Programming Talk
---

### Post by dodle on 2009-03-30
I am trying to add a "- " to the beginning of each new line in a string.  Here is my code:[PHP]#! /usr/bin/env python
#
text = "First Line\nSecond Line\nThird Line"
print text
print

text_group = text.split("\n")

for nl in text_group:
	spaced = "- %s" % nl
	print spaced

print
print spaced[/PHP]The output is:```
First Line
Second Line
Third Line

- First Line
- Second Line
- Third Line

- Third Line

```When I print from inside the "for" loop, each line is printed.  But if I print outside the loop, only the last line is printed.  How can I get all lines to print outside the loop?

---

### Post by Sprut1 on 2009-03-30
> **dodle said:**
> I am trying to add a "- " to the beginning of each new line in a string.  Here is my code:[PHP]#! /usr/bin/env python
#
text = "First Line\nSecond Line\nThird Line"
print text
print

text_group = text.split("\n")

for nl in text_group:
	spaced = "- %s" % nl
	print spaced

print
print spaced[/PHP]The output is:```
First Line
Second Line
Third Line

- First Line
- Second Line
- Third Line

- Third Line

```When I print from inside the "for" loop, each line is printed.  But if I print outside the loop, only the last line is printed.  How can I get all lines to print outside the loop?

Look at what you are doing with "spaced" in the for loop. When the for loop is done "spaced" will contain the last line.

```
var = "some string"
var += " some other string"
print var
> "some string some other string"
```

---

### Post by dodle on 2009-03-30
Thanks Sprut1.  I've found a solution:[PHP]#! /usr/bin/env python
#
text = "First Line\nSecond Line\nThird Line"
print text
print

new_group = []
text_group = text.split("\n")

for nl in text_group:
	spaced = "- %s" % nl
	new_group.append(spaced)

joined_group = "\n".join(new_group)
print joined_group[/PHP]Output:```
First Line
Second Line
Third Line

- First Line
- Second Line
- Third Line

```

---

### Post by imdano on 2009-03-30
This kind of operation is a good place to use a list comprehension:
[php]
text = "First Line\nSecond Line\nThird Line"
joined_group = '\n'.join(["- %s" % line for line in text.split('\n')])[/php]

---

### Post by Sprut1 on 2009-03-30
> **imdano said:**
> This kind of operation is a good place to use a list comprehension:
[php]
text = "First Line\nSecond Line\nThird Line"
joined_group = '\n'.join(["- %s" % line for line in text.split('\n')])[/php]

This is exactly why I love Python.

---

### Post by dodle on 2009-03-30
> **imdano said:**
> This kind of operation is a good place to use a list comprehension:
[php]
text = "First Line\nSecond Line\nThird Line"
joined_group = '\n'.join(["- %s" % line for line in text.split('\n')])[/php]

Wow, that's a lot less code.  I'll give it a shot.  Thanks.

---

### Post by Can+~ on 2009-03-30
> **imdano said:**
> This kind of operation is a good place to use a list comprehension:
[php]
text = "First Line\nSecond Line\nThird Line"
joined_group = '\n'.join(["- %s" % line for line in text.split('\n')])[/php]

It's not limited to lists, but tuples also:

[php]text = "First Line\nSecond Line\nThird Line"
joined_group = '\n'.join(("- %s" % line for line in text.split('\n')))[/php]

I remember reading that with tuples it uses less memory or something, not sure where I read it.

---

### Post by ghostdog74 on 2009-03-30
```

>>> text = "First Line\nSecond Line\nThird Line"
>>> print "-" + text.replace("\n","\n- ")

```

---

