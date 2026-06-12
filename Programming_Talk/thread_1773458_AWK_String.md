---
title: "AWK String"
date: 2011-06-02
forum: Programming Talk
---

### Post by __Sun__ on 2011-06-02
I am at a complete loss at how to loop through a string in AWK.

Suppose I want to access the n'th character of a variable holding a string.
How may I do this?

*Update:*

I have figure out a method but I am unsure if this is the only right method of traversing through an array of characters.
Here is my current solution:
```

  str = "test"
  c = 1
  while ((ch = substr(str, c++, 1)))
    {
      print ch
    }

```

---

### Post by DaithiF on 2011-06-02
Hi, using substr.

a couple of examples:
```
$ echo "hello" | awk '{ print substr($0, 5, 1) }'
o

$ echo "hello" | awk '{ for(i=1; i<=length($0); i++) print substr($0, i, 1); }'
h
e
l
l
o
```

you could also set the field separator to empty which will cause awk to split the input into single-character fields, and then output whichever character you want:, e.g.
```
 $ echo "hello" | awk 'BEGIN {FS=""}; {print $5}'
0
```

---

### Post by __Sun__ on 2011-06-02
So, the feature is not built-in like it is in most languages (such as C).

Very well, thank you for your second solution. I deduced the first one (if you cared reading the "Update" section of my post).

I was hoping for something similar to what is provided in C (as AWK is so similar to it), not an indirect method.
Thanks anyway.

---

