---
title: "[Python] Array to Image"
date: 2008-06-04
forum: Programming Talk
---

### Post by regomodo on 2008-06-04
I'm sort of following an example i found a while back on the net (can't find the link) on messing with an image in array (image intesity) for then back to an image. However, i cannot for the life of me figure out why, when i go to repack an image, i get gobbledegook as the value changes are correct. It's easy to do it with the *im.point(lambda i: i *2)* but i want to do it this way. Any help would be great.

```
#! /usr/bin/env python
import Image, numpy
global im_m
im = Image.open("test.jpg").convert("L")

dimx = im.size[0]
dimy = im.size[1]

print dimx, dimy

im_l = numpy.array(list(im.getdata()))
im_l = numpy.resize(im_l,im.size)
print im_l[1,10]

for x in range(dimx):
	for y in range(dimy):
		im_l[x,y] = im_l[x,y] *2
		
print im_l[1,10]

img = Image.fromstring("L",im.size,im_l.tostring())
img.show()
img.save("mess.gif")
```

i've attached  original and output

---

### Post by geirha on 2008-06-04
I spot a couple of problems here.

1. you are converting a 24 bpp image to 8 bpp grayscale. That's fine. Then you put the data in a numpy.array, but a numpy.array defaults to 32 bits per value, but Image.fromstring will expect 8 bits per pixel. So you get about 3 black pixels behind each pixel. To fix, you need to specify the correct dtype for numpy.array:
```
numpy.array([255,128]).tostring()
'\xff\x00\x00\x00\x80\x00\x00\x00'        #bad
numpy.array([255,128], dtype='uint8').tostring()
'\xff\x80'                                #good

```

2. when you multiply each pixel with 2, you need to check that its value does not exceed 255, because it will wrap if it does. if the pixel-value is 128, then 128*2 will be 0 (not 256 since 255 is the highest value). So do something like: if pixel >127, then set to 255, else multiply with two.

---

### Post by regomodo on 2008-06-05
ah, cheers for making that clear. I just found a better way of creating my array```


i = Image.open('lena.jpg')
a = numpy.asarray(i) # a is readonly
i = Image.fromarray(a)
```

I managaed to read the changelog for PIL 1.1.6 as none of the guides show this. It sets the array's dtype to uint8. 
It's not a major issue but is there a way to prevent the loopback to 0 when 255 is exceeded without an if/else statement?

---

### Post by regomodo on 2008-06-05
nobody for anymore?

---

### Post by WW on 2008-06-05
```

		im_l[x,y] = min(255, im_l[x,y] *2)

```

---

### Post by regomodo on 2008-06-06
Ok, this is what i have now. It's a tentative change, just to make sure, but it keeps failing with it complaining about the ranges i'm using. Any ideas?

```
#! /usr/bin/env python
import Image, numpy
global im_m
im = Image.open("test.jpg").convert("L")

dimx = im.size[0]
dimy = im.size[1]
res = dimx * dimy

print dimx, dimy

im_l = numpy.asarray(im)
im_m = numpy.zeros( (dimx,dimy),dtype = "uint8" ))
print im_m.shape

for x in range(dimx):
	for y in range(dimy):
		im_m[x,y] = min(255, im_l[x,y] + 1)
i = Image.fromarray(im_m)
i.show()
```

The error is this
> 
Traceback (most recent call last):
  File "/home/jon/work/Image_Processing/python/image/simple_array.py", line 18, in ?
    im_m[x,y] = min(255, im_l[x,y] + 1)
IndexError: index (532) out of range (0<=index<=532) in dimension 0

[edit] this weird. I've just run it but telling it to print out the coordinates, it fails at 531,531, of a 800x532 image.

---

### Post by geirha on 2008-06-06
EDIT: Strike that, I was wrong.
EDIT2: On second thought, I wasn't after all. With an image of size 3x2, you get the following result:
```

>>> im.size
(3, 2)
>>> im_l= numpy.asarray(im)
>>> im_m= numpy.empty( (3,2) )
>>> im_l.shape, im_m.shape
((2, 3), (3, 2))

```
They are the opposite way of each other ...

---

### Post by regomodo on 2008-06-06
> **WW said:**
> ```

		im_l[x,y] = min(255, im_l[x,y] *2)

```

cheers for that. That works a treat.

---

### Post by regomodo on 2008-06-06
> **geirha said:**
> EDIT: Strike that, I was wrong.
EDIT2: On second thought, I wasn't after all. With an image of size 3x2, you get the following result:
```

>>> im.size
(3, 2)
>>> im_l= numpy.asarray(im)
>>> im_m= numpy.empty( (3,2) )
>>> im_l.shape, im_m.shape
((2, 3), (3, 2))

```
They are the opposite way of each other ...

it appears you're right

```
im_l = numpy.asarray(im)
im_m = numpy.zeros( (dimx,dimy),dtype = "uint8" )
print "original", "=",im_l.shape,"\n", "new",im_m.shape
```

gives me
> 
800 532
original = (532, 800) 
new (800, 532)

So, 
```

im_m[x,y] = min(255, im_l[x,y] * 2)
```

is now 

```
im_m[y,x] = min(255, im_l[y,x] * 2)
```
which works.

That is bloody weird how numpy skews up x and y. Is there a specific reason for the way it is?

---

### Post by Zeromaru on 2008-09-16
NumPy indexes 2-dimensional arrays as (row,column) as opposed to familiar coordinate notation of (column,row). This is because matrices written index notation use this order (ie, the element g_{ij} refers to the ith row and jth column of matrix g). So when considering an array representing a picture, one has to use the unfamiliar (y,x) format.

This is my first time using NumPy for images, but I've used it extensively for relativistic calculations where the order of indices worked naturally. I'm actually just starting some image programming, and this thread was very helpful on getting me started! Thank you!

---

