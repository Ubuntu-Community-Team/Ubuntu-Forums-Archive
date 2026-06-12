---
title: "newb question on python input from file"
date: 2012-03-21
forum: Programming Talk
---

### Post by brushman on 2012-03-21
I have a file consisting of thousands of lines, where time and x represent real numbers (not integers) that looks like what follows (there are some spaces in front of each line):

```
     
     time1
     x1
     time2
     x2
     time3
     x3
     .
     .
     time4000
     x4000

```

In python I need to read these numbers in and graph x vs time using matplotlib. Does anyone have advice on the best way to read in these numbers? Thanks.

---

### Post by JDShu on 2012-03-21
Why not the standard way?

```

F = open("yourfile.txt","r")

```Every time you call F.next(), you get the next line. In fact you can use it like any other iterator in Python.

Edit: The documentation should help you specifically [http://docs.python.org/library/stdtypes.html#file-objects](http://docs.python.org/library/stdtypes.html#file-objects)

---

