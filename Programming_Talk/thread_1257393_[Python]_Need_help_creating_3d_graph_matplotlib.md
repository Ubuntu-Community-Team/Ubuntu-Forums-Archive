---
title: "[Python] Need help creating 3d graph matplotlib"
date: 2009-09-03
forum: Programming Talk
---

### Post by sonicrules1234 on 2009-09-03
Hi.  I need some help creating a 3d wireframe in matplotlib in python.  Here is my code.

```

from __future__ import division
import matplotlib.pyplot as plt
from numpy import *

fig = plt.figure()
from mpl_toolkits.mplot3d import Axes3D
ax = Axes3D(fig)
xlist = []
ylist = []
zlist = []
for x in range(1, 100) :
    for y in range(1, 100) :
        xlist.append(x)
        ylist.append(y)
        zlist.append(x/y)
numpyx = array(xlist)
numpyy = array(ylist)
numpyz = array(zlist)
ax.plot_wireframe(numpyx, numpyy, numpyz)
ax.set_xlabel('X Label')
ax.set_ylabel('Y Label')
ax.set_zlabel('Z Label')
plt.show()


Traceback (most recent call last):
  File "C:\Users\Westly\Desktop\3dimage.py", line 19, in <module>
    ax.plot_wireframe(numpyx, numpyy, numpyz)
  File "C:\Python25\Lib\site-packages\mpl_toolkits\mplot3d\axes3d.py", line 684, in plot_wireframe
    rows, cols = Z.shape
ValueError: need more than 1 value to unpack
```

Thanks in advance for any help. :)

---

