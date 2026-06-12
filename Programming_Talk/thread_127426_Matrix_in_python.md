---
title: "Matrix in python"
date: 2006-02-08
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-08
I programmed pretty much in C all my life. Now I am  learning python.

I have a very basic question. In C you define and have array like 

```

int[] a = {1,2,3,4,5}

or int[2][2] a = { {2,3},
                      {3,2},
                   } 

```
The above code show matrix like this
2 3
3 2

How do u do it in python. I understand list, but how do u use those lists to make 2D and 3D array in Python.

I think I am not able to think beyond C, which I think needs to be changed.

All your help is appreciated.

Thanks

---

### Post by cwaldbieser on 2006-02-08
[QUOTE=krypto_wizard]I programmed pretty much in C all my life. Now I am  learning python.

I have a very basic question. In C you define and have array like 

```

int[] a = {1,2,3,4,5}

or int[2][2] a = { {2,3},
                      {3,2},
                   } 

```
The above code show matrix like this
2 3
3 2

How do u do it in python. I understand list, but how do u use those lists to make 2D and 3D array in Python.

I think I am not able to think beyond C, which I think needs to be changed.

All your help is appreciated.

Thanks[/QUOTE]

A simple matrix of nested lists:
```

>>> x = [ [1,2,3],
          [4,5,6],
          [7,8,9]]
>>> x[0][0]
1
>>> x[1][1]
5

```

---

### Post by celloandy on 2006-02-09
Native Python arrays are slow for matrix operations, so if you plan to do actual matrix operations (in the linear algebra sense), take a look at [NumArray](http://www.stsci.edu/resources/software_hardware/numarray).  It's much faster for that sort of thing.

Andrew

---

### Post by krypto_wizard on 2006-02-09
thanks, I will take a look at it.


[QUOTE=celloandy]Native Python arrays are slow for matrix operations, so if you plan to do actual matrix operations (in the linear algebra sense), take a look at [NumArray](http://www.stsci.edu/resources/software_hardware/numarray).  It's much faster for that sort of thing.

Andrew[/QUOTE]

---

