---
title: "[SOLVED] Python For-loop"
date: 2008-11-13
forum: Programming Talk
---

### Post by elmoosecapitan on 2008-11-13
I am having a little issue with for loops in python.
The functionality of my code is to take each VALUE in my list of floating decimals (FLOAT_LIST) and place it each VALUE into one of 16 bins depending on the its value.

Here is my code snippet:
[CODE]  
for value in Float_list: 
 
    for i in range(0,17): 
        if (i-j) <= value and value < (i+j):  
            Bin_i.append(value) 
            break 
[\CODE]

As you see, if VALUE falls within a range about an integer i, I put it into a corresponding list Bin_i. However, in attempting to iterate the process, I run into a problem of python recognizing Bin_i as something undefined. That is to say, if i = 5, and VALUE is within 5+/-j, then my interpreter tries putting VALUE in Bin_i and NOT Bin_5.

Help!

---

### Post by jjgomera on 2008-11-13
how does python know bin_i is bin_i when you wanted bin_5, or really b5n_5?

maybe its easier using arrays of arrays

if you use bin[i].append(value)

---

### Post by elmoosecapitan on 2008-11-13
Array of array worked, thanks!

---

