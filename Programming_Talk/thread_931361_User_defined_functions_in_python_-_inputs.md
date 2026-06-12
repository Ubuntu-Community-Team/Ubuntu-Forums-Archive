---
title: "User defined functions in python - inputs"
date: 2008-09-27
forum: Programming Talk
---

### Post by elbarto_87 on 2008-09-27
Hi,
I have recently started experimenting with python and have liked what I have seen so far. I have a few questions regarding user defined functions. 

In MATLAB, you can have a UDF with a certain number of inputs, and using the "nargin" function you can determine how many inputs the user has specified, and set some defualt values if there is less inputs then expected.

In the example below, I would like to set defualt values as shown in the comments. Any suggestions on how to do this would be appreciated. I have scipy and numpy libraries also if that makes a difference?

```
def pnt(x,y,z):

    #point(x,y) sets z = 0 by default. {1 dimensional}
    #point(x) sets y =0, z = 0 by default. {2 dimensional}
    
    
    global pmatrix
    pmatrix = [x , y, z]
    print "Point defined @ x = ", x, " y = ", y, " z = ", z, " ..."
```

Also, I am useing IDLE as my IDE at the moment. Is there any way to clear the python shell and also a way to clear all Global / Local variables in the namespace. 

Thank You

Elbarto

---

### Post by yotam on 2008-09-27
Defining default values for parameters can be done as in:
```
def pnt(x,y=0,z=0):
```

---

### Post by elbarto_87 on 2008-09-27
Thanks yotam,
That was easier then I thought.

Much appreciated,

Elbarto

---

