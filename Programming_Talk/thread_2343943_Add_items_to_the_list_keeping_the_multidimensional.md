---
title: "Add items to the list keeping the multidimensionality"
date: 2016-11-21
forum: Programming Talk
---

### Post by iacoposk8 on 2016-11-21
Hi to all, In the code below I take a picture and convert it into a 3d array numpy  (cordinates x, y of each pixel and color rgb) Then skim this array and sequentially extract of the matrices 5 x 5 x 3  (then arrays of 5 x 5 px most the rgb values 3) and insert them in an  array

```
from PIL import Image  
import numpy as np  

img = Image.open("img.jpg")  
arr = np.array(img)  

x = []  
h,w,rgb = arr.shape  
size = 5  

for i in range(0,h):  
    for j in range(0,w):  
        part = arr[i:i+size,j:j+size]  
        if len(part)==size and len(part[0])==size:  
            x.append(part)
```

The result is something like:

```
...  
[[129, 166, 175],  
[129, 166, 175],  
[130, 167, 175],  
[128, 166, 175],  
[128, 166, 175]],  

...  

[[129, 166, 174],  
[129, 166, 174],  
[129, 166, 175],  
[129, 166, 175],  
[128, 166, 175]]], dtype=uint8), 129, 166, 175, array([[[129, 166, 175],  
[128, 166, 175],  
[128, 166, 175],  
[128, 166, 175],  
[128, 168, 176]],  

...  

[[129, 166, 174],  
[129, 166, 175],  
[129, 166, 175],  
[128, 166, 175],  
[129, 167, 176]]], dtype=uint8), 129, 166, 175, array([[[128, 166, 175],  
[128, 166, 175],  
[128, 166, 175],  
[128, 168, 176],  
[128, 168, 178]],  

...  

[[129, 166, 175],  
[129, 166, 175],  
[128, 166, 175],  
[129, 167, 176],  
[128, 168, 176]]], dtype=uint8), 128, 166, 175]  
```

While I would expect something like

```
...  
[[129, 166, 175],  
[129, 166, 175],  
[130, 167, 175],  
[128, 166, 175],  
[128, 166, 175]],  

...  

[[129, 166, 174],  
[129, 166, 174],  
[129, 166, 175],  
[129, 166, 175],  
[128, 166, 175]]], dtype=uint8), array([[[129, 166, 175],  
[128, 166, 175],  
[128, 166, 175],  
[128, 166, 175],  
[128, 168, 176]],  

...  

[[129, 166, 174],  
[129, 166, 175],  
[129, 166, 175],  
[128, 166, 175],  
[129, 167, 176]]], dtype=uint8), array([[[128, 166, 175],  
[128, 166, 175],  
[128, 166, 175],  
[128, 168, 176],  
[128, 168, 178]],  

...  

[[129, 166, 175],  
[129, 166, 175],  
[128, 166, 175],  
[129, 167, 176],  
[128, 168, 176]]], dtype=uint8)]  
```

So a matrix that is always 5 x 5 x 3 not in some one-dimensional  points after the fact ", dtype=uint8)," I would expect a, array([[[128,  166, 175], and not a 128, 166, 175
  thank you.

---

