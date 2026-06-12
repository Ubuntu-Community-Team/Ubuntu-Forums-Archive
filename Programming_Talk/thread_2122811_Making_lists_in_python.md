---
title: "Making lists in python"
date: 2013-03-06
forum: Programming Talk
---

### Post by wingnut2626 on 2013-03-06
Isn't there a way to split items in a list into text separated by spaces? Like turn

[4, 6, 9]
INTO
4 6 9

---

### Post by MG&amp;TL on 2013-03-06
I'm confident that there's a much more efficient way, but for now (while I research it):

```

#any list here
some_list = [1, 2, 3]

#blank storage string
some_list_string = ''

#iterate over every item in the list
for num in some_list:
     #append the number and a space
     some_list_string += str(num) + ' '

print some_list_string

```

After some research, it turns out that it's quite easy to just convert the list into a string (as python's print does), then remove extraneous characters. E.g.

```

#Any list here.
some_list = [1, 2, 3]

#Convert to string, remove '[' and ']', and remove commas.
some_list_string = str(some_list).strip('[]').replace(',', '')

print some_list_string

```

EDIT 2: Python's join is even better, see the people below.

---

### Post by r-senior on 2013-03-06
I think the Python way would be:

```
' '.join(some_list)
```

EDIT: Or, if it's a list of integers:

```
' '.join([str(n) for n in some_list])
```

---

### Post by Vaphell on 2013-03-06
integers need to be converted to strings with str()
```
$ python
Python 2.7.2+ (default, Jul 20 2012, 22:15:08) 
[GCC 4.6.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> l=[4,6,9]
>>> ' '.join(str(x) for x in l)
'4 6 9'
```

---

### Post by wingnut2626 on 2013-03-06
Thanks guys for the help

---

### Post by schragge on 2013-03-06
```
' '.join(map(str, list))
```should work, too.

---

