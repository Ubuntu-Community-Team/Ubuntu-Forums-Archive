---
title: "Python : array problem"
date: 2011-04-01
forum: Programming Talk
---

### Post by wlourf on 2011-04-01
Hi !

I have this little script :
```
table = [["a",1],["b",2]]
table.append(table[1])
table.append(table[2])
print table
table[0].append("aa")
table[1].append("bb")
table[2].append("cc")
print table

```and its output :
```
[['a', 1], ['b', 2], ['b', 2], ['b', 2]]
[['a', 1, 'aa'], ['b', 2, 'bb', 'cc'], ['b', 2, 'bb', 'cc'], ['b', 2, 'bb', 'cc']]


```And the output I would like  :
```
[['a', 1], ['b', 2], ['b', 2], ['b', 2]]
[['a', 1, 'aa'], ['b', 2, 'bb'], ['b', 2, 'cc'], ['b', 2]]

```The first part of the script copy last element of the array for making a 4 elements array. I think the problem is here, when I copy the last element : table.append(table[1]) but I can't see what is wrong !

thanks for your help

---

### Post by MadCow108 on 2011-04-01
mutable types, like lists, are passed by reference in python.
So the first appends insert references to the list table[1] so in the end you have a list with four entries where the last two are just references to the second entry
if you modify one of them you modify all three.

to get the result you want you have to explicitly make copy the list, e.g. with the slice operator:
```

table.append(table[1][:])

```
[http://docs.python.org/library/copy.html](http://docs.python.org/library/copy.html)

immutable types like strings and tuples are always copied

---

### Post by Arndt on 2011-04-01
> **wlourf said:**
> Hi !

I have this little script :
```
table = [["a",1],["b",2]]
table.append(table[1])
table.append(table[2])
print table
table[0].append("aa")
table[1].append("bb")
table[2].append("cc")
print table

```and its output :
```
[['a', 1], ['b', 2], ['b', 2], ['b', 2]]
[['a', 1, 'aa'], ['b', 2, 'bb', 'cc'], ['b', 2, 'bb', 'cc'], ['b', 2, 'bb', 'cc']]


```And the output I would like  :
```
[['a', 1], ['b', 2], ['b', 2], ['b', 2]]
[['a', 1, 'aa'], ['b', 2, 'bb'], ['b', 2, 'cc'], ['b', 2]]

```The first part of the script copy last element of the array for making a 4 elements array. I think the problem is here, when I copy the last element : table.append(table[1]) but I can't see what is wrong !

thanks for your help

The cause of the behaviour is that you don't copy, you take the array itself, so after the append, it will be referenced in several places. Use

table.append(table[1][:])

---

### Post by wlourf on 2011-04-01
thanks to you both, I tried the copy [:] before but not in this way. That rocks !

---

### Post by StephenF on 2011-04-01
Alternatively.
```

table.append(list(table[1]))
table.append(list(table[2]))

```

There is also the 'copy' module (import copy).

---

