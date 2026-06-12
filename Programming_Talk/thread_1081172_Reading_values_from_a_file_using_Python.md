---
title: "Reading values from a file using Python"
date: 2009-02-26
forum: Programming Talk
---

### Post by adamsnative on 2009-02-26
hi

Suppose i have stored an array in a file.How can i read that array in my current program and manipulate it ie if i read an integer array i manipulate it using the same method by which i manipulate a local array declared in my program , because i want to access the individual values of the array read from the file row and column wise
Please help
Thank you

---

### Post by ssam on 2009-02-26
if it is a nice neat array of numbers (each row having the same number of numbers), then the best option would be to use numpy/scipy

[http://www.scipy.org/Cookbook/InputOutput](http://www.scipy.org/Cookbook/InputOutput)

if you are working with arrays of numbers using a numpy array will be quicker and easier than using a list of lists.

---

### Post by ghostdog74 on 2009-02-26
you can use pickle/shelve/cpickle. check the documentation.

---

### Post by adamsnative on 2009-02-26
thans any further help will b of gr8 use and aapreciated it will be gr8 if you can post an example with the output also
thanks a lot

---

### Post by Paul Miller on 2009-02-27
How to get your data back into Python depends entirely on how you wrote it out.  Provide a small example showing what you did to write the array to disk in the first place, and then we can help you read it back.

---

### Post by adamsnative on 2009-02-27
i am having the values of 7 haralik parameters for 20 images and i want to store these values as and when i get in a file and then retreive the whole lot at a time in an array ie a floating point array

---

