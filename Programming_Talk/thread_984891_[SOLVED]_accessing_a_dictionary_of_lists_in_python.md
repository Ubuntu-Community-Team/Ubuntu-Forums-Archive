---
title: "[SOLVED] accessing a dictionary of lists in python"
date: 2008-11-17
forum: Programming Talk
---

### Post by glok_twen on 2008-11-17
hi - i am using the rpy python library and trying to access the data is sends back. the result is in a variable called dum1 in the following code bit. i think it's a dictionary of lists but am not quite sure. anyhow, see the shell statements at the end where i am trying to access specific numbers within this result. i can get to the 'coefficients' piece, but don't know how to dereference any deeper than that.

can you explain and or put in an example or two of how to dereference some of this data?

thanks,
gt


```
print dum1
{'terms': <Robj object at 0x8192270>, 'fstatistic': {'dendf': 1.0, 'value': 20.986335569171622, 'numdf': 2.0}, 'aliased': {'x2': False, 'x1': False, '(Intercept)': False}, 'df': [3, 1, 3], 'call': <Robj object at 0x8192260>, 'residuals': {'1': -2.6991151550361319, '3': 2.0065931586311789, '2': 1.3073982844227885, '4': -0.61487628801783556}, 'adj.r.squared': 0.93018818889935884, 'cov.unscaled': array([[ 2.18057535, -0.44896157,  0.0256508 ],
       [-0.44896157,  0.10707525, -0.01169993],
       [ 0.0256508 , -0.01169993,  0.01266843]]), 'r.squared': 0.97672939629978628, 'sigma': 3.6604647038442288, 'coefficients': array([[-12.60488519,   5.40532452,  -2.33193865,   0.25789996],
       [  3.71675747,   1.19779026,   3.10301194,   0.19847162],
       [  1.81562486,   0.41200043,   4.4068519 ,   0.14205569]])}

print dum1['coefficients']
[[-12.60488519   5.40532452  -2.33193865   0.25789996]
 [  3.71675747   1.19779026   3.10301194   0.19847162]
 [  1.81562486   0.41200043   4.4068519    0.14205569]]

print dum1['coefficients'[0][0]]
Traceback (most recent call last):
  File "<input>", line 1, in <module>
KeyError: 'c'

print dum1['coefficients':[0][0]]
Traceback (most recent call last):
  File "<input>", line 1, in <module>
TypeError: unhashable type
```

---

### Post by Tony Flury on 2008-11-17
I think you just have your [] is the wrong places 

I think you need
```

print dum1['coefficients'][0][0]

```
```

print dum1['coefficients'] 

```
will produce your list of lists, as you have proved
```

print dum1['coefficients'][0] 

```
will produce your first sub list : 
```

[-12.60488519   5.40532452  -2.33193865   0.25789996]

```
so
```

print dum1['coefficients'][0][0] 

```
should produce 
```

-12.60488519

```

---

