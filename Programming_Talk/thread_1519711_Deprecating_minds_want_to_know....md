---
title: "Deprecating minds want to know..."
date: 2010-06-28
forum: Programming Talk
---

### Post by starfyredragon on 2010-06-28
Hey all,
I'm currently writing an open-source program in Python for one of my University's labs...

As part of the program, I'm taking old (and very large) fortran Arrays and reading them into a python program so they can later be displayed in tables, graphs, etc.

Anyway, I've been using scipy.io.fopen, but python keeps bugging me and saying that I should switch from using fopen to npfile since fopen is being deprecated. Since I'm having to read single-precision binary fortran files, I've been trying to use fopen. However, for the sake of future code compatibility and updatability... how do I do the equivalent using npfile?  I don't see any fortran binary options in npfile. 

Thanks!

---

### Post by Linteg on 2010-06-28
Try [numpy.fromfile]("http://docs.scipy.org/doc/numpy/reference/generated/numpy.fromfile.html"). Since you are converting fortran arrays you might also need to use the "order" parameter of numpy.reshape/ndarray.reshape (if/when you need to do that)

---

### Post by starfyredragon on 2010-06-28
Any clue what I'd need to put in the order parameter?

---

### Post by Linteg on 2010-06-28
order='F', reshape doesn't have [too many options]("http://docs.scipy.org/doc/numpy/reference/generated/numpy.reshape.html").

---

### Post by starfyredragon on 2010-06-28
Thanks! You're a huge help!

So, if I'm understanding this correctly, if I'm using a two-dimensional array, what I should likely do is something like this:

myFile=numpy.reshape( a=numpy.fromfile("filename", count=-1, sep=''), 2, order = F)

(apologies if I'm making some bad assumptions... it's been awhile since I've written programs in python, and I'm still getting back into the groove.)

---

### Post by Linteg on 2010-06-29
Close, you do not need the count=-1 and sep='' unless you want to change the default value. The second parameter in reshape should also be different, you need to know the actual size of the array for this to work. The command should look something like: [php]myArray = numpy.fromfile("filename").reshape((sizex, sizey), order='F')[/php]
Unless the array is saved as a number of doubles you might also need to change the dtype parameter in fromfile in order to parse the data as the proper type, i.e. [php]myArray = numpy.fromfile("filename", dtype=numpy.uint16).reshape((sizex, sizey), order='F')[/php]
A list of numpy's data types is available [here]("http://docs.scipy.org/doc/numpy/user/basics.types.html")

---

### Post by starfyredragon on 2010-06-30
> **Linteg said:**
> Unless the array is saved as a number of doubles you might also need to change the dtype parameter in fromfile It's actually a multi-dimensional array with some parts as integers, some parts as doubles, and some parts as set characters.

---

### Post by starfyredragon on 2010-06-30
Oh, here's the info I have to go off:
[http://www.ks.uiuc.edu/Research/vmd/plugins/molfile/dcdplugin.html](http://www.ks.uiuc.edu/Research/vmd/plugins/molfile/dcdplugin.html)

---

