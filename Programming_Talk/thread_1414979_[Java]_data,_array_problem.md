---
title: "[Java] data, array problem"
date: 2010-02-24
forum: Programming Talk
---

### Post by SpinningAround on 2010-02-24
I have an array size 1000 and a program that after a certain time span add a new value to the array, problem is that depending on the time span will I get out of boundary exception past a certain time. Question is how to get around this problem so when the limit of the array is reached will the oldest value be disposed to make room for the newest.

---

### Post by Queue29 on 2010-02-24
Arrays can't be resized, at least not without allocating a new array of larger size and copying the contents of the old array into the new array.

It sounds like you want to use an [ArrayList]("http://java.sun.com/javase/6/docs/api/java/util/ArrayList.html"), which automates that process for you. All you have to worry about is adding and removing elements.

---

### Post by ja660k on 2010-02-24
I would suggest using an arrayList
because they are so much easier to work with

[http://java.sun.com/j2se/1.5.0/docs/api/java/util/ArrayList.html](http://java.sun.com/j2se/1.5.0/docs/api/java/util/ArrayList.html)

when deleting a value the indexes are already reset
inbetween < > tags are generics
for this example will be using array list of strings
arraylist can hold any subclass of Object 

```

arrayList<String> list = new java.util.ArrayList<String>()


if (list.size() < 1000)
    list.add(data)
else
    list.remove(0)

```
ps: i cannot remember how data is inserted whether new data is added at the start index 0 or appended to the end length +1

i have not tried this code this is only pseudo

---

