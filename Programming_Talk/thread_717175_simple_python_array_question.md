---
title: "simple python array question"
date: 2008-03-06
forum: Programming Talk
---

### Post by pytheas22 on 2008-03-06
This is probably extraordinarily obvious to anyone who knows what he's doing, but I'm new to python and don't.

I have a file that looks like:

```
6 2 N
6 3 T
6 4 E
```

For each line in the file, I want to create a two-dimensional array where arr[FIELD-ONE][FIELD-TWO]=[FIELD-THREE].  In other words, arr[6][2] should give N, arr[6][3] gives T and so on.  I can't figure this out, mostly because I am not sure how I can get python to recognize different fields as needed.  I could probably solve the problem by calling awk in a subshell or something, but I'm sure there's a much more efficient way to do this.  If anyone has any hints, they would be greatly appreciated.

---

### Post by pmasiar on 2008-03-06
see [two-dimensional arrays in python](http://ubuntuforums.org/showthread.php?t=716350) thread. You can use dictionary with keys - tuples. Any dimension you want :-)

---

### Post by nuggien on 2008-03-06
I'd just use a dictionary of dictionaries for your purpose.  Inserting is as simple as:

arr = {}
arr[6] = {}
arr[6][2] = 'N'

Referencing arr[6][2] will obviously give you back 'N'.

---

### Post by pmasiar on 2008-03-06
With dictionary using tuple as key, you can use arr[6,2] = 'N'

---

### Post by pytheas22 on 2008-03-06
Thanks to all for the responses.  I should have been clearer; I actually meant that I wanted to add the values to the array with a routine that would iterate through each line, not just put them in manually (that I actually know how to do).  However after the idea of dictionaries came to mind I did figure out how to do it.  Thanks to all who helped!

---

