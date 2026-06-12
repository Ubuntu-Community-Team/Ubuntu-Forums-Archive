---
title: "Python quick questions"
date: 2006-01-25
forum: Programming Talk
---

### Post by krypto_wizard on 2006-01-25
Hi,

I am a python newbie. I started reading "ByteofPython" and was also looking at "dive into python".

I couldn't find these things

1. How to use 2 dimensional Array(or higher dimensional) in Python....nobody mentioned that.
2. How to pass an array as a function argument ? I was kinda confused and didn't get much really.


Thanks

---

### Post by ubuntumaneh on 2006-01-25
1) 
a=[1,2]
b=[2,2]
a+b

This simple example show you you don't have to declare the variable before use it. Also, have a look at the type "list" in your books.

2)
def soma_vec(a,b):
     c=a+b
     return c

a=[1,2]
b=[2,3]
print soma_vec(a,b)

x=1
y=2
print soma_vec(x,y)

---

### Post by diffuser78 on 2006-01-25
How to pass 3d array ? Is there anything like poiners

---

### Post by ubuntumaneh on 2006-01-25
It was a very nice experience. I just got a book, like you. And I had the luck to have some problems to solve (mainly physics and math ones). That's the most important. I learned in a day the most common commands. Then I was able to make well structured programs. I started to write oo programs a month later. Since then I have being playing with it. It is fast and easier.
I read from time to time things from:
[http://python.org/doc/current/modindex.html](http://python.org/doc/current/modindex.html)
to get acquainted with some modules.
My suggestion is: set some problems, and work on it with python. That is the best way. Examples are:
1) email server and client
2) sysadmin scripts, like a script to add new user with all configurations set by you, a program to rename multiple files
3) some mathematical and physics problems

have fun

---

### Post by ubuntumaneh on 2006-01-25
Ther is no pointers. Consider the function built before. Just use:

a=[1,2,3]
b=[3,2,1]
print soma_vec(a,b)

x=[1,2,3,4,5,6,7]
y=[7,6,5,4,3,2,1]
print soma_vec(x,y)

---

### Post by krypto_wizard on 2006-01-25
Thanks ubuntumaneh, I really appreciate your help.

[QUOTE=ubuntumaneh]Ther is no pointers. Consider the function built before. Just use:

a=[1,2,3]
b=[3,2,1]
print soma_vec(a,b)

x=[1,2,3,4,5,6,7]
y=[7,6,5,4,3,2,1]
print soma_vec(x,y)[/QUOTE]

---

### Post by Van_Gogh on 2006-01-26
multidimensional array are typically implemented in Python as lists of lists, e.g.
```
2_dim_array = [[1,2,3], [4,5,6]]  #2x3 matrix

elem_2_3 = 2_dim_array[1][2] #accesing element 2,3
```

Alternatively, if you need to do math and the array handling to be faster(the built-in lists are quite slow for math stuff), you could take a look at the modules Numeric or SciPy. For matrix manipulation etc. these are an order of magnitude faster than simple lists of lists.

---

### Post by krypto_wizard on 2006-01-26
Thanks dude, this is the answer I was looking for. I wanted to write a class for matrix operations just for practice. This quite helps.

[QUOTE=Van_Gogh]multidimensional array are typically implemented in Python as lists of lists, e.g.
```
2_dim_array = [[1,2,3], [4,5,6]]  #2x3 matrix

elem_2_3 = 2_dim_array[1][2] #accesing element 2,3
```

Alternatively, if you need to do math and the array handling to be faster(the built-in lists are quite slow for math stuff), you could take a look at the modules Numeric or SciPy. For matrix manipulation etc. these are an order of magnitude faster than simple lists of lists.[/QUOTE]

---

### Post by krypto_wizard on 2006-01-26
Thanks as I said earlier.

I am writing Matrix Program (manipulation) just to get some practice.
Can you give any starters on that. 



[QUOTE=Van_Gogh]multidimensional array are typically implemented in Python as lists of lists, e.g.
```
2_dim_array = [[1,2,3], [4,5,6]]  #2x3 matrix

elem_2_3 = 2_dim_array[1][2] #accesing element 2,3
```

Alternatively, if you need to do math and the array handling to be faster(the built-in lists are quite slow for math stuff), you could take a look at the modules Numeric or SciPy. For matrix manipulation etc. these are an order of magnitude faster than simple lists of lists.[/QUOTE]

---

